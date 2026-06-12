---
title: "having problems with snort"
date: 2010-11-02
forum: Networking &amp; Wireless
---

### Post by acidblue on 2010-11-02
Using Ubuntu 10.04 with snort-mysql 2.8.5.2 and Base.

I'm getting this error when I run sudo snort -c /etc/snort/snort.conf:

Warning: /etc/snort/rules/community-dos.rules(16) => threshold (in rule) is deprecated; use detection_filter instead.
ERROR: /etc/snort/rules/community-virus.rules(19) => !any is not allowed
Fatal Error, Quitting..

I'm following this guide, although it's kinda old.
[http://ubuntuforums.org/showthread.php?t=145641](http://ubuntuforums.org/showthread.php?t=145641)

I have MYSQL and Base set up and working, but snort doesn't log anything to base probably because of the above error.

Any help would be greatly appreciated.

---

