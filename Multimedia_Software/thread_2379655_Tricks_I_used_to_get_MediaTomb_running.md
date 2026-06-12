---
title: "Tricks I used to get MediaTomb running"
date: 2017-12-07
forum: Multimedia Software
---

### Post by ub-newbie on 2017-12-07
Posting this mainly for myself, but I hope it might help others.

OS: 16.04 LTS 

Installed MediaTomb, but my UPnP player (PS3) would not see it, and I could only access its web page locally.

Solution:  There are multiple configuration files to be changed
```
/etc/default/mediatomb
/etc/mediatomb/config.xml
~/home/.mediatomb/config.xml
```
If I understand correctly, the "home" config.xml is used when you run Mediatomb from the command line.
"etc" config.xml is used when Mediatomb is ran as a daemon

"/etc/default/mediatomb", well that is where my problem was.  It defaults to only presenting Mediatomb on the "lo" (loopback) interface.
So, I had to go in and replace "lo" with my interface name. I got my interface name  from ```
ifconfig
```  
On my system it is "enp0s31f6"?? (guess ETH0 would have been to easy).

So, once I set ```
MT_INTERFACE="enp0s31f6"
``` Mediatomb became visible to my UPnP player.

Also, /etc/default/mediatomb is where the Port is set, and the Logfile, and the location of the config.xml file to use.

---

