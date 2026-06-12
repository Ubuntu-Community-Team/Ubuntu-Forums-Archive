---
title: "Can't tether Blackberry Curve to Ubuntu 11.04"
date: 2011-08-30
forum: Networking &amp; Wireless
---

### Post by emilward on 2011-08-30
I'm not sure if anyone will be able to help me but here it goes anyways:
 
I'm trying to tether my Sprint Blackberry Curve 8530 to my Dell Latitude D630 which is running Ubuntu 11.04. 
 
I've had no luck with berry4all, blueman, easy tether, Blue tooth, or other random script solutions. 
 
Is there anyone who can help me?

---

### Post by northd_tech on 2011-08-30
I don't have any experience with Blackberries, but post #174 on this thread says that "Barry" works fairly well:

[http://ubuntuforums.org/showthread.php?t=190938&page=18](http://ubuntuforums.org/showthread.php?t=190938&page=18)

Barry
[http://www.netdirect.ca/software/packages/barry](http://www.netdirect.ca/software/packages/barry)

(You will need to get the correct .DEB package for your machine architecture- usually i386, ia64, or amd64 for most "PC" architecures)
[http://packages.debian.org/sid/libbarry0](http://packages.debian.org/sid/libbarry0)
[http://packages.debian.org/unstable/main/barry-util](http://packages.debian.org/unstable/main/barry-util)

Alternately Ubuntugeek tells us this (for Ubuntu's through 10.10):

> **Install barry in ubuntu 10.10/10.04/9.10**
 Open terminal and run the following commands
```
sudo add-apt-repository ppa:doctormo/barry-snapshot
sudo apt-get update
sudo apt-get install barry-util opensync-plugin-barry-4x
```


[http://www.ubuntugeek.com/syncing-your-blackberry-on-ubuntu.html](http://www.ubuntugeek.com/syncing-your-blackberry-on-ubuntu.html)

Good luck with it.

---

