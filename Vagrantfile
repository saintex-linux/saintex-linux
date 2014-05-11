# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = '2'
VAGRANT_ROOT = File.dirname(File.expand_path(__FILE__))

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = 'arch'
  config.vm.hostname = 'bootstrap.saintexlinux.com'
  config.vm.network :private_network, ip: '192.168.40.40'

  config.vm.provider 'virtualbox' do |vb|
    vb.customize ['modifyvm', :id, '--memory', '2048']
    vb.customize ['modifyvm', :id, '--ioapic', 'on', '--cpus', '4']

    file_to_disk = File.join(VAGRANT_ROOT, 'saintex-linux.vdi')
    unless File.exist?(file_to_disk)
      vb.customize ['createhd', '--filename', file_to_disk, '--size', 8 * 1024]
    end
    vb.customize ['storageattach', :id, '--storagectl', 'SATA Controller', '--port', 1, '--device', 0, '--type', 'hdd', '--medium', file_to_disk]
  end
end
