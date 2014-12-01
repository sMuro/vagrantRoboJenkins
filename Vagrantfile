# -*- mode: ruby -*-

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  config.vm.box = "debian73"
  config.vm.box_url = "http://puppet-vagrant-boxes.puppetlabs.com/debian-73-x64-virtualbox-nocm.box"

  config.vm.network :forwarded_port, guest: 80, host: 8888
  config.vm.network :forwarded_port, guest:8080, host: 8880

  config.ssh.private_key_path = ["~/.vagrant.d/insecure_private_key", "~/.ssh/vagrantKey"]
  config.ssh.forward_agent = true

  config.vm.provider :virtualbox do |vb|
     vb.customize ["modifyvm", :id, "--memory", 1024]
  end

  config.vm.provision :ansible do |ansible|
     ansible.playbook = "provisioning/playbook.yml"

     ansible.host_key_checking = false
  end
end
