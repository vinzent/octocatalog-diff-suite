# octocatalog-diff suite

Differerent Puppet versions and octocatalog-diff bundled

For use on EL7

## Prequisites

On EL7:

```
yum install -y -q centos-release-scl-rh 
yum install -y -q rh-ruby24-rubygem-bundler rh-ruby24-ruby-devel 
yum install -y -q git openssl-devel make gcc cmake libgit2-devel redhat-rpm-config
yum install -y -q rpm-build
. /opt/rh/rh-ruby24/enable
gem install fpm
```

## Build


```
. /opt/rh/rh-ruby24/enable
(cd octocatalog-diff; bundle install)
(cd puppet4; bundle install)
(cd puppet5; bundle install)
(cd puppet-dev; bundle install)

fpm -s dir -t rpm \
  --name octocatalog-diff-suite \
  --version 0.1.0 \
  --iteration 1 \
  --exclude "*.rpm" \
  --description "octocatalog-diff and different Puppet versions bundled for EL7" \
  --url https://github.com/vinzent/octocatalog-diff-suite \
  --depends rh-ruby24-ruby \
  --depends git  \
  ./=/opt/octocatalog-diff-suite
```

