---
title: "firefox/opera timing out"
date: 2010-08-08
forum: Networking &amp; Wireless
---

### Post by ubuntu-user on 2010-08-08
I am facing problem with firefox and opera. Even google page request ends up in time out error. But google chrome works absolutely fine.

Any suggestions ?

I use 10.04

---

### Post by claracc on 2010-08-08
Perhaps you have to disable ipv6 in firefox:

    In the Location bar, type about:config and press Enter
    The about:config "This might void your warranty!" warning page may appear. Click I'll be careful, I promise!
   In the Filter field, type network.dns.disableIPv6.
   In the list of preferences, double-click network.dns.disableIPv6 to set its value to true. 

Or you can try some of the advices in this link (for firefox):
[http://support.mozilla.com/en-US/kb/Firefox+cannot+load+websites+but+other+programs+can](http://support.mozilla.com/en-US/kb/Firefox+cannot+load+websites+but+other+programs+can)

---

