---
title: "apt-cache multiple computer updating"
date: 2011-01-20
forum: Networking &amp; Wireless
---

### Post by tejas.deshpande on 2011-01-20
Hi,
I have 3 computers in my house running ubuntu, and I wanted to get them to update from just 1 download from the main server. so using the apt-cache application, I tried doing it, but when I do sudo apt-get update, it stops on 98% .

I followed this guide [here]("http://www.debuntu.org/how-to-set-up-a-repository-cache-with-apt-cacher") .

my sources.list from the client is (192.168.1.11 is the static ip I have assigned to the host)

> 
# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://192.168.1.11:3142/unsupported](http://192.168.1.11:3142/unsupported) maverick main restricted
deb-src [http://192.168.1.11:3142/unsupported](http://192.168.1.11:3142/unsupported) maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://192.168.1.11:3142/unsupported](http://192.168.1.11:3142/unsupported) maverick universe
deb-src [http://192.168.1.11:3142/unsupported](http://192.168.1.11:3142/unsupported) maverick universe
deb [http://192.168.1.11:3142/unsupported](http://192.168.1.11:3142/unsupported) maverick-updates universe
deb-src [http://192.168.1.11:3142/unsupported](http://192.168.1.11:3142/unsupported) maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://192.168.1.11:3142/unsupported](http://192.168.1.11:3142/unsupported) maverick multiverse
deb-src [http://192.168.1.11:3142/unsupported](http://192.168.1.11:3142/unsupported) maverick multiverse
deb [http://192.168.1.11:3142/unsupported](http://192.168.1.11:3142/unsupported) maverick-updates multiverse
deb-src [http://192.168.1.11:3142/unsupported](http://192.168.1.11:3142/unsupported) maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://192.168.1.11:3142/archive](http://192.168.1.11:3142/archive) maverick partner
deb-src [http://192.168.1.11:3142/archive](http://192.168.1.11:3142/archive) maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://192.168.1.11:3142/extras](http://192.168.1.11:3142/extras) maverick main
deb-src [http://192.168.1.11:3142/extras](http://192.168.1.11:3142/extras) maverick main

deb [http://192.168.1.11:3142/security](http://192.168.1.11:3142/security) maverick-security main restricted
deb-src [http://192.168.1.11:3142/security](http://192.168.1.11:3142/security) maverick-security main restricted
deb [http://192.168.1.11:3142/security](http://192.168.1.11:3142/security) maverick-security universe
deb-src [http://192.168.1.11:3142/security](http://192.168.1.11:3142/security) maverick-security universe
deb [http://192.168.1.11:3142/security](http://192.168.1.11:3142/security) maverick-security multiverse
deb-src [http://192.168.1.11:3142/security](http://192.168.1.11:3142/security) maverick-security multiverse

and the apt-cacher config from the host is 

> 
#################################################################
# This is the config file for apt-cacher. On most Debian systems
# you can safely leave the defaults alone.
#################################################################

# cache_dir is used to set the location of the local cache. This can
# become quite large, so make sure it is somewhere with plenty of space.
cache_dir=/var/cache/apt-cacher

# The email address of the administrator is displayed in the info page
# and traffic reports.
admin_email=root@localhost

# For the daemon startup settings please edit the file /etc/default/apt-cacher.

# Daemon port setting, only useful in stand-alone mode. You need to run the
# daemon as root to use privileged ports (<1024).
daemon_port=3142

# optional settings, user and group to run the daemon as. Make sure they have
# sufficient permissions on the cache and log directories. Comment the settings
# to run apt-cacher as the native user.
group=www-data
user=www-data

# optional setting, binds the listening daemon to specified IP(s). Use IP
# ranges for more advanced configuration, see below.
# daemon_addr=localhost

# If your apt-cacher machine is directly exposed to the Internet and you are
# worried about unauthorised machines fetching packages through it, you can
# specify a list of IPv4 addresses which are allowed to use it and another
# list of IPv4 addresses which aren't.
# Localhost (127.0.0.1) is always allowed. Other addresses must be matched
# by allowed_hosts and not by denied_hosts to be permitted to use the cache.
# Setting allowed_hosts to "*" means "allow all".
# Otherwise the format is a comma-separated list containing addresses,
# optionally with masks (like 10.0.0.0/22), or ranges of addresses (two
# addresses separated by a hyphen, no masks, like '192.168.0.3-192.168.0.56').
allowed_hosts=*
denied_hosts=

# And similarly for IPv6 with allowed_hosts_6 and denied_hosts_6.
# Note that IPv4-mapped IPv6 addresses (::ffff:w.x.y.z) are truncated to
# w.x.y.z and are handled as IPv4.
allowed_hosts_6=fec0::/16
denied_hosts_6=

# This thing can be done by Apache but is much simpler here - limit access to
# Debian mirrors based on server names in the URLs
#allowed_locations=ftp.uni-kl.de,ftp.nerim.net,debian.tu-bs.de

# Apt-cacher can generate usage reports every 24 hours if you set this
# directive to 1. You can view the reports in a web browser by pointing
# to your cache machine with '/apt-cacher/report' on the end, like this:
#      [http://yourcache.example.com/apt-cacher/report](http://yourcache.example.com/apt-cacher/report)
# Generating reports is very fast even with many thousands of logfile
# lines, so you can safely turn this on without creating much 
# additional system load.
generate_reports=1

# Apt-cacher can clean up its cache directory every 24 hours if you set
# this directive to 1. Cleaning the cache can take some time to run
# (generally in the order of a few minutes) and removes all package
# files that are not mentioned in any existing 'Packages' lists. This
# has the effect of deleting packages that have been superseded by an
# updated 'Packages' list.
clean_cache=1

# Apt-cacher can be used in offline mode which just uses files already cached,
# but doesn't make any new outgoing connections by setting this to 1.
offline_mode=0

# The directory to use for apt-cacher access and error logs.
# The access log records every request in the format:
# date-time|client ip address|HIT/MISS/EXPIRED|object size|object name
# The error log is slightly more free-form, and is also used for debug
# messages if debug mode is turned on.
# Note that the old 'logfile' and 'errorfile' directives are
# deprecated: if you set them explicitly they will be honoured, but it's
# better to just get rid of them from old config files.
logdir=/var/log/apt-cacher

# apt-cacher can use different methods to decide whether package lists need to
# be updated,
# A) looking at the age of the cached files
# B) getting HTTP header from server and comparing that with cached data. This
# method is more reliable and avoids desynchronisation of data and index files
# but needs to transfer few bytes from the server every time somebody requests
# the files ("apt-get update")
# Set the following value to the maximum age (in hours) for method A or to 0
# for method B
expire_hours=0

# Apt-cacher can pass all its requests to an external http proxy like
# Squid, which could be very useful if you are using an ISP that blocks
# port 80 and requires all web traffic to go through its proxy. The
# format is 'hostname:port', eg: 'proxy.example.com:8080'.
#http_proxy=proxy.example.com:8080

# Use of an external proxy can be turned on or off with this flag.
# Value should be either 0 (off) or 1 (on).
use_proxy=0

# External http proxy sometimes need authentication to get full access. The
# format is 'username:password'.
#http_proxy_auth=proxyuser:proxypass

# Use of external proxy authentication can be turned on or off with this flag.
# Value should be either 0 (off) or 1 (on).
use_proxy_auth=0

# This sets the interface to use for the upstream connection.
# Specify an interface name, an IP address or a host name.
# If unset, the default route is used.
#interface=

# Rate limiting sets the maximum bandwidth in bytes per second to use
# for fetching packages. Syntax is fully defined in 'man wget'.
# Use 'k' or 'm' to use kilobytes or megabytes / second: eg, 'limit=25k'.
# Use 0 or a negative value for no rate limiting.
limit=0

# Debug mode makes apt-cacher spew a lot of extra debug junk to the
# error log (whose location is defined with the 'logdir' directive).
# Leave this off unless you need it, or your error log will get very
# big. Acceptable values are 0 or 1.
debug=0

# To enable data checksumming, install libberkeleydb-perl and set this option
# to 1. Then wait until the Packages/Sources files have been refreshed once
# (and so the database has been built up). You can also nuke them in the cache
# to trigger the update.  
# checksum=1

# Print a 410 (Gone) HTTP message with the specified text when accessed via
# CGI. Useful to tell users to adapt their sources.list files when the
# apt-cacher server is being relocated (via apt-get's error messages while
# running "update")
#cgi_advise_to_use = Please use [http://cacheserver:3142/](http://cacheserver:3142/) as apt-cacher access URL
#cgi_advise_to_use = Server relocated. To change sources.list, run perl -pe "s,/apt-cacher\??,:3142," -i /etc/apt/sources.list

# Server mapping - this allows to hide real server names behind virtual paths
# that appear in the access URL. This method is known from apt-proxy. This is
# also the only method to use FTP access to the target hosts. The syntax is
# simple, the part of the beginning to replace, followed by a list of mirror
# urls, all space separated. Multiple profile are separated by semicolons
# Note that you need to specify all target servers in the allowed_locations
# options if you make use of it. Also note that the paths should not overlap
# each other. FTP access method not supported yet, maybe in the future.
#path_map = debian ftp.uni-kl.de/pub/linux/debian ftp2.de.debian.org/debian ; ubuntu archive.ubuntu.com/ubuntu ; security security.debian.org/debian-security ftp2.de.debian.org/debian-security

path_map = mavericksec security.ubuntu.com/ubuntu ; extras extras.ubuntu.com/ubuntu ; archive archive.canonical.com/ubuntu ; unsupported us.archive.ubuntu.com/ubuntu/

# Permitted package files - this is a perl regular expression which matches all
# package-type files (files that are uniquely identified by their filename). 
# The default is: 
#package_files_regexp = (?:\.deb|\.rpm|\.dsc|\.tar\.gz|\.diff\.gz|\.udeb|index\.db-.+\.gz|\.jigdo|\.template)$

# Permitted Index files - this is the perl regular expression which matches all
# index-type files (files that are uniquely identified by their full path and
# need to be checked for freshness). 
#The default is:
#index_files_regexp = (?:Index|Packages\.gz|Packages\.bz2|Release|Release\.gpg|Sources\.gz|Sources\.bz2|Contents-.+\.gz|pkglist.*\.bz2|release|release\..*|srclist.*\.bz2|Translation-.+\.bz2)$



can you help me identify the problem??

In the apt-cacher config file, the only changes made to the default is the path names.


Thanks!

---

