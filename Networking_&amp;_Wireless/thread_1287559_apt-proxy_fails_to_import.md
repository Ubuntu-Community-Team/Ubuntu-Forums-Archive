---
title: "apt-proxy fails to import"
date: 2009-10-10
forum: Networking &amp; Wireless
---

### Post by cong06 on 2009-10-10
I have apt-proxy set up on the local machine.

Running "sudo aptitude update" updates the apt-proxy import repository, so that any files that can be downloaded with "apt-get install" are now listed in the import repository also... right?

So when I have a version of "gpaint" for example, that is the latest version, directly downloaded from the repository on another (fully updated) computer, it should import.

But it doesn't, it gives the standard "no backend found"

I found the bug post: [https://launchpad.net/ubuntu/+source/apt-proxy/+bug/4844](https://launchpad.net/ubuntu/+source/apt-proxy/+bug/4844)
and the standard reply: [https://launchpad.net/ubuntu/+source/apt-proxy/+bug/4844/comments/8](https://launchpad.net/ubuntu/+source/apt-proxy/+bug/4844/comments/8)
which I tried... but it didn't solve the problem. (actually it seems sudo find, isn't finding any "Packages.bz2"... or any *.bz2 files for that matter)

apt-proxy-v2.conf:
```

[DEFAULT]
;; All times are in seconds, but you can add a suffix
;; for minutes(m), hours(h) or days(d)

;; Server IP to listen on
;address = 127.0.0.1

;; Server port to listen on
port = 9999

;; Control files (Packages/Sources/Contents) refresh rate
;;
;; Minimum age of a file before it is refreshed
min_refresh_delay = 1h

;; Minimum age of a file before attempting an update (NOT YET IMPLEMENTED)
;min_age = 23h

;; Uncomment to make apt-proxy continue downloading even if all
;; clients disconnect.  This is probably not a good idea on a
;; dial up line.
;; complete_clientless_downloads = 1

;; Debugging settings.
;; for all debug information use this:
;; debug = all:9
debug = all:4 db:0

;; Debugging remote python console
;; Do not enable in an untrusted environment
;telnet_port = 9998
;telnet_user = apt-proxy
;telnet_password = secret

;; Network timeout when retrieving from backend servers
timeout = 30

;; Cache directory for apt-proxy
cache_dir = /var/cache/apt-proxy

;; Use passive FTP? (default=on)
;passive_ftp = on

;; Use HTTP proxy?
http_proxy = 127.0.0.1:3128

;; Limit download rate from backend servers (http and rsync only), in bytes/sec
;bandwidth_limit = 100000

;;--------------------------------------------------------------
;; Cache housekeeping

;; Time to perform periodic housekeeping:
;;  - delete files that have not been accessed in max_age
;;  - scan cache directories and update internal tables
cleanup_freq = 1d

;; Maximum age of files before deletion from the cache (seconds)
max_age = 120d

;; Maximum number of versions of a .deb to keep per distribution
max_versions = 3

;; Add HTTP backends dynamicaly if not already defined? (default=on)
;dynamic_backends = on

;;---------------------------------------------------------------
;;---------------------------------------------------------------
;; Backend servers
;;
;; Place each server in its own [section]

[ubuntu]
;; Ubuntu archive
backends = 
    http://ke.archive.ubuntu.com/ubuntu
    http://archive.ubuntu.com/ubuntu
min_refresh_delay = 15m

[ubuntu-security]
;; Ubuntu security updates
backends = http://security.ubuntu.com/ubuntu
min_refresh_delay = 1m
```
sources.list:
```
deb http://localhost:9999/ubuntu/ jaunty main universe restricted multiverse
deb http://localhost:9999/ubuntu/ jaunty-updates universe main multiverse restricted
deb http://localhost:9999/ubuntu-security/ jaunty-security universe main multiverse restricted
```

---

### Post by cong06 on 2009-10-13
It seems after a few days of running "sudo aptitude update" a few more debs have been installed, but still not all of them.

In an attempt to fully update my apt-proxy cache, I deleted all of the /var/lib/apt/lists/ files and ran an update again.

It helped, but there's still a whole slew of packages that should be importable...

---

### Post by cong06 on 2009-10-15
is "skipped - no suitable backend found" synonymous with "skipped - already imported" ?

I know some of these files were imported already. But now its not pointing out that they're imported.

---

### Post by cong06 on 2009-12-14
I think that running this (a few times) on the computer with apt-proxy helps...

```

rm /var/lib/apt/lists/*
aptitude update
find /var/cache/apt-proxy/ -name *.bz2 -exec bunzip2 -f {} \;
/etc/init.d/apt-proxy restart

```

and then doing the import

---

