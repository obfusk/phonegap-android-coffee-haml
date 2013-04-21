require 'coffee-script'
require 'haml'

hc = %w{ haml coffee }

desc 'phonegap run'
task run: hc do
  sh './cordova/run'
end

desc 'phonegap build'
task build: hc do
  sh './cordova/build'
end

desc 'phonegap release'
task release: hc do
  sh './cordova/release'
end

desc 'phonegap log'
task :log do
  sh './cordova/log'
end

desc 'phonegap clean'
task :clean do
  sh './cordova/clean'
end

desc 'watch haml and coffee'
task watch: %w{ haml coffee } do
  sh 'watchr Watchfile'
end

desc 'haml/*.haml -> assets/www/haml/*.html'
task :haml do
  Dir['haml/*.haml'].each do |x|
    y = "assets/www/haml/#{ File.basename x, '.haml' }.html"
    puts "#{x} -> #{y}"
    File.open(y, 'w') do |f|
      f.write Haml::Engine.new(File.read(x)).render
    end
  end
end

desc 'coffee/*.coffee -> assets/www/coffee/*.js'
task :coffee do
  Dir['coffee/*.coffee'].each do |x|
    y = "assets/www/coffee/#{ File.basename x, '.coffee' }.js"
    puts "#{x} -> #{y}"
    File.open(y, 'w') do |f|
      f.write CoffeeScript.compile(File.read(x))
    end
  end
end
