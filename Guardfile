cucumber_options = {
  :all_on_start   => false,
  :all_after_pass => false,
  :bundler        => false,
  :notification   => true,
  :command_prefix => 'zeus',
  :change_format => 'pretty'
}

rspec_options = {
  :cmd            => 'zeus rspec',
  :zeus           => true,
  :bundler        => false,
  :all_on_start   => false,
  :all_after_pass => false,
  :notification   => false
}

guard 'cucumber', cucumber_options do
  watch(%r{^features/.+\.feature$})
end

guard :rspec, rspec_options do
  watch(%r{^spec/.+_spec\.rb$})
  watch(%r{^lib/(.+)\.rb$})     { |m| "spec/lib/#{m[1]}_spec.rb" }
  # watch('spec/spec_helper.rb')  { "spec" }

  # Rails example
  watch(%r{^app/(.+)\.rb$})                                  { |m| "spec/#{m[1]}_spec.rb" }
  watch(%r{^app/(.*)(\.erb|\.haml)$})                        { |m| "spec/#{m[1]}#{m[2]}_spec.rb" }
  watch(%r{^app/controllers/api/v1/(.+)\.rb$})               { |m| "spec/api/v1/#{m[1]}_spec.rb" }
  watch(%r{^app/controllers/(.+)_(controller)\.rb$})         { |m| ["spec/api/v1/#{m[1]}_routing_spec.rb", "spec/#{m[2]}s/#{m[1]}_#{m[2]}_spec.rb", "spec/acceptance/#{m[1]}_spec.rb"] }
  watch(%r{^spec/support/(.+)\.rb$})                         { "spec" }
  watch('config/routes.rb')                                  { "spec/routing" }
  watch('app/controllers/application_controller.rb')         { "spec/controllers" }

  # Capybara features specs
  watch(%r{^app/views/(.+)/.*\.(erb|haml)$})          { |m| "spec/features/#{m[1]}_spec.rb" }

  # Turnip features and steps
  watch(%r{^spec/acceptance/(.+)\.feature$})
  watch(%r{^spec/acceptance/steps/(.+)_steps\.rb$})   { |m| Dir[File.join("**/#{m[1]}.feature")][0] || 'spec/acceptance' }
end

#livereload_options = {
#  port: '3000'
#}

#guard 'livereload' do
#  watch(%r{app/views/.+\.(erb|haml|slim)$})
#  watch(%r{app/helpers/.+\.rb})
#  watch(%r{public/.+\.(css|js|html)})
#  watch(%r{config/locales/.+\.yml})
#  # Rails Assets Pipeline
#  watch(%r{(app|vendor)(/assets/\w+/(.+\.(css|js|html|coffee))).*}) { |m| "/assets/#{m[3]}" }
#end