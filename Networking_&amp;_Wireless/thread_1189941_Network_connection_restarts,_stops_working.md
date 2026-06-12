---
title: "Network connection restarts, stops working"
date: 2009-06-17
forum: Networking &amp; Wireless
---

### Post by mikeljnola on 2009-06-17
This is a problem that has started on or around the upgrade to 9.04.  My desktop has run perfectly for at least a year on Ubuntu, now all of a sudden, after being up for anywhere from a week to a couple days, the internet stops working.  It started with the main DNS going down and only being able to access previously cached hosts.  I thought maybe it was pdnsd, so I uninstalled that.  After a few reboots it worked just from thrashing around.  Now this morning, I noticed nothing is working.  I scour the logs and see this

```

Jun 16 22:49:00 fenster kernel: [875996.740945] r8169: eth0: link down
Jun 16 22:49:00 fenster NetworkManager: <info>  (eth0): carrier now OFF (device state 8) 
Jun 16 22:49:00 fenster NetworkManager: <info>  (eth0): device state change: 8 -> 2 
Jun 16 22:49:00 fenster NetworkManager: <info>  (eth0): deactivating device (reason: 40). 
Jun 16 22:49:00 fenster NetworkManager: <info>  eth0: canceled DHCP transaction, dhcp client pid 5876 
Jun 16 22:49:00 fenster NetworkManager: <info>  (eth0): removing resolv.conf from /sbin/resolvconf 
Jun 16 22:49:01 fenster named[9211]: connection refused resolving 'local/SOA/IN': 192.5.5.241#53

```Then there are thousands and thousands of iterations of the last line.  I have a sneaking suspicion it is NetworkManager's fault, but that could just be because I'm suspicious of it for having capitalized names like a Java class.

Seriously, though, I'm completely perplexed.  I am used to a static resolv.conf that I can troubleshoot, but this has been quite the thorn in my side becuase it's hard for me to figure out exactly where the configuration files are.  

Any advice would be much appreciated.

---

### Post by redmk2 on 2009-06-17
See [***here***]("http://ubuntuforums.org/showthread.php?t=1185704")

---

### Post by mikeljnola on 2009-06-26
> **redmk2 said:**
> See [***here***]("http://ubuntuforums.org/showthread.php?t=1185704")

Excellent.  I just got a chance to do this.  I just threw away NetworkManager and set up resolv.conf like it should be, and everything works.  Imagine that.

Thanks.

---

