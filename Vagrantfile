Vagrant::Config.run do |config|
  config.vm.box = "neatline"
  config.vm.box_url = "http://files.vagrantup.com/lucid32.box"

  config.vm.network "33.33.33.11"
  config.vm.provision :chef_solo do |chef|
    chef.cookbooks_path = [
      'cookbooks/opscode',
      'cookbooks/slab',
    ]

    chef.add_recipe 'omeka'

    chef.add_recipe 'tmux'
    chef.add_recipe 'vim'

    chef.json.merge!({
      :omeka => {
        :username            => 'neatline',
        :password            => 'neatline',
        :super_email         => 'erochest@virginia.edu',
        :administrator_email => 'erochest@virginia.edu',
        :site_title          => 'Neatline Playground',
        :description         => 'This is a small Omeka site to play with Neatline.',
        :copyright           => 'Rector and Visitors of the University of Virginia',
        :author              => 'Eric Rochester',
        :path_to_convert     => '/usr/bin',
        :version             => 'stable-1.4',
        :plugins             => [
          {:name => 'Neatline',     :url => 'git@github.com:scholarslab/Neatline.git'},
          {:name => 'NeatlineMaps', :url => 'git@github.com:scholarslab/NeatlineMaps.git'},
          {:name => 'NeatlineTime', :url => 'git@github.com:scholarslab/NeatlineTime.git'},
        ],
      },
      :vim => {
        :extra_packages => %w{vim-scripts exuberant-ctags ack-grep htop}
      },
      :domain => [],
      :openldap => {}
    })
  end

end
