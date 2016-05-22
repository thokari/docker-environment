# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|

  config.vm.provider "virtualbox" do |vb|
    vb.memory = "1024"
  end

  config.vm.define "hub" do |hub|

    hub.vm.provider "virtualbox" do |vb_hub|
      vb_hub.memory = "512"
    end
    
    hub.vm.box = "ubuntu/trusty64"
    hub.vm.hostname = "hub"
    hub.vm.network :private_network, ip: "192.168.50.11"

    hub.vm.network "forwarded_port", guest: 4444, host: 4444

  end

  config.vm.define "chrome-node-1" do |cn1|
    cn1.vm.box = "ubuntu/trusty64"
    cn1.vm.hostname = "cn1"
    cn1.vm.network :private_network, ip: "192.168.50.12"

  end

  config.vm.define "chrome-node-2" do |cn2|
    cn2.vm.box = "ubuntu/trusty64"
    cn2.vm.hostname = "cn2"
    cn2.vm.network :private_network, ip: "192.168.50.13"

  end

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "setup-docker-host.yml"
  end

  # Create a private network, which allows host-only access to the machine
  # using a specific IP.
  # config.vm.network "private_network", ip: "192.168.33.10"

  # Create a public network, which generally matched to bridged network.
  # Bridged networks make the machine appear as another physical device on
  # your network.
  # config.vm.network "public_network"

  # Share an additional folder to the guest VM. The first argument is
  # the path on the host to the actual folder. The second argument is
  # the path on the guest to mount the folder. And the optional third
  # argument is a set of non-required options.
  # config.vm.synced_folder "../data", "/vagrant_data"

  #
  # View the documentation for the provider you are using for more
  # information on available options.

  # Define a Vagrant Push strategy for pushing to Atlas. Other push strategies
  # such as FTP and Heroku are also available. See the documentation at
  # https://docs.vagrantup.com/v2/push/atlas.html for more information.
  # config.push.define "atlas" do |push|
  #   push.app = "YOUR_ATLAS_USERNAME/YOUR_APPLICATION_NAME"
  # end

  # Enable provisioning with a shell script. Additional provisioners such as
  # Puppet, Chef, Ansible, Salt, and Docker are also available. Please see the
  # documentation for more information about their specific syntax and use.
  # config.vm.provision "shell", inline: <<-SHELL
  #   sudo apt-get update
  #   sudo apt-get install -y apache2
  # SHELL
end
