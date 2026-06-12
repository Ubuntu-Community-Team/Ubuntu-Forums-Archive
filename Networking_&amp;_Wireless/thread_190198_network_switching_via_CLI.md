---
title: "network switching via CLI"
date: 2006-06-06
forum: Networking &amp; Wireless
---

### Post by chacon on 2006-06-06
Hello all is there a way to swtich networks via the CLI?  I found this post:
[http://ubuntuforums.org/showthread.php?t=164516](http://ubuntuforums.org/showthread.php?t=164516)

which comes close.  Basically I wanted to take avantage of the "profiles" Ex.

work = Ethernet active, Wifi off
work wfi = ethernet off, wifi on essid=workwifi
home wifi =ethernet off, wifi on essid=homewifi

Basically i wanted to do something like:

hostname$ if-up work-wifi up

then when i go home, this:

hostname$ if-up home-wifi

I know the command are not the correct ones, but something to that effect. I have normally used Redhat and there are network profiles under /etc/sysconfig/network-profiles..i think.  I cannot find anything like this under ubuntu.

I would rather use the CLI instead of network-admin or network-manager.  TIA :D

---

