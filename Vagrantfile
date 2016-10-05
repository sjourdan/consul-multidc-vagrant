ENV['VAGRANT_DEFAULT_PROVIDER'] = 'virtualbox'

vm_memory = 512
vm_cpus = 1

Vagrant.configure("2") do |config|

  config.vm.box = "bento/centos-7.2"
  config.vm.box_check_update = false

  config.vm.provider :virtualbox do |vb|
    vb.memory = vm_memory
    vb.cpus = vm_cpus
    vb.linked_clone = true
  end

  (1..3).each do |n|
    lan_ip = "10.30.0.#{n+100}"
    config.vm.define "dc1-#{n}" do |config|
      config.vm.hostname = "dc1-#{n}"
      config.vm.network "private_network", ip: lan_ip
    end
  end

  (1..3).each do |n|
    lan_ip = "10.40.0.#{n+100}"
    config.vm.define "dc2-#{n}" do |config|
      config.vm.hostname = "dc2-#{n}"
      config.vm.network "private_network", ip: lan_ip
    end
  end

end
