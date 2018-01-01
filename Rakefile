require 'rubygems'
require 'tmpdir'

require 'bundler/setup'
require 'jekyll'

TARGET_DIR = '../otaviof.github.io'.freeze

namespace :site do
  desc "Generate blog files on '#{TARGET_DIR}'"
  task :generate do
    config = Jekyll.configuration('source' => '.', 'destination' => TARGET_DIR)
    Jekyll::Site.new(config).process
  end

  desc 'Publish generated blog files'
  task publish: %i(generate) do
    sh <<-EOS
    cd #{TARGET_DIR} && \
      git add . && \
      git commit -m 'Update at #{Time.now}' && \
      git push origin master && \
      cd -
    EOS
  end
end
