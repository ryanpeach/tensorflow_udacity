# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure(2) do |config|

  # do not update configured box
  config.vm.box_check_update = true

  # Every Vagrant development environment requires a box. You can search for
  # boxes at https://atlas.hashicorp.com/search.
  config.vm.box = "ubuntu/trusty64"

  config.vm.provider "virtualbox" do |vb|
    # Display the VirtualBox GUI when booting the machine
    #vb.gui = true
  
    # Customize the amount of memory on the VM:
    vb.memory = "4000"
  end
  
  config.vm.network "forwarded_port", guest: 8888, host: 8888

  config.vm.provision "shell", inline: <<-SHELL
    sudo apt-get update
    sudo apt-get install -y python3-dev python3-pip python3-numpy python3-scipy python3-pandas
    export TF_BINARY_URL=https://storage.googleapis.com/tensorflow/linux/cpu/tensorflow-0.11.0rc0-cp34-cp34m-linux_x86_64.whl
    sudo pip3 install jupyter $TF_BINARY_URL
  SHELL

  config.vm.provision "shell", run: "always", inline: <<-SHELL
    ipython notebook --ip=0.0.0.0 --no-browser
  SHELL
end