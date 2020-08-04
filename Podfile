install! 'cocoapods', :deterministic_uuids => false

platform :ios, '10.0'
use_frameworks!

# ignore all warnings from all pods
inhibit_all_warnings!

def import_test_pods
  pod 'Quick', '~> 1.0'
  pod 'Nimble', '~> 7.0'
end

target "ExSwiftTests" do
  import_test_pods
end

post_install do |installer|
  installer.pods_project.targets.each do |target|
    target.build_configurations.each do |config|
      config.build_settings['SWIFT_VERSION'] = '4.2'
      config.build_settings['CLANG_ENABLE_MODULES'] = 'YES'
      if config.build_settings['IPHONEOS_DEPLOYMENT_TARGET'].to_f < 10.0
      	config.build_settings['IPHONEOS_DEPLOYMENT_TARGET'] = '10.0'
      end
    end
  end
end
