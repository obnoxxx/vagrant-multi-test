# -*- mode: ruby -*-
# vi: set ft=ruby et ts=2 sts=2 sw=2 :

# Example of a multi-machine Vagrantfile that will
# only work correctly if the machines are brought
# up in parallel: If a machine brought up can not
# reach the other machine within 60 pings,
# provisioning will fail.
#
# Michael Adam <obnox@samba.org>

Vagrant.configure(2) do |config|
  config.vm.box = "humaton/fedora-21-cloud"
  config.vm.synced_folder ".", "/vagrant", disabled: true

  config.vm.define "node1" do |node1|
    node1.vm.box = "humaton/fedora-21-cloud"
    node1.vm.network "private_network", ip: "172.20.10.51"
    node1.vm.provision "shell", inline: "ping -c 60 172.20.10.52"
  end

  config.vm.define "node2" do |node2|
    node2.vm.box = "humaton/fedora-21-cloud"
    node2.vm.network "private_network", ip: "172.20.10.52"
    node2.vm.provision "shell", inline: "ping -c 60 172.20.10.51"
  end
end
