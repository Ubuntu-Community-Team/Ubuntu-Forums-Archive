---
title: "Interesting Wireless Problem"
date: 2009-05-22
forum: Networking &amp; Wireless
---

### Post by version7x on 2009-05-22
In the last couple of weeks, I've noticed my wireless connection start to drop in and out on my home network.  It's to the point now where I'll connect for about 30 seconds, the connection will drop, and then it will attempt to connect for about 5 minutes (asking for my passcode two or three times) and then connect for another 30 seconds.  Other computers will stay connected as will hard booting the windows partition.

When I go to work,  I can bounce off any of the access points and stay connected all day (WPA2 Enterprise)

Laptop - Dell E6500
Card - Intel Wifi Link 5100
Kernel 2.6.28-11-generic  in Jaunty/9.04
Router - linksys wrt150n

The only thing I see in /var/log/messages is
```
iwlagn 0000:c:00.0:firmware: requesting iwlwifi-5000-1.ucode
```
and
```
Registered led device: iwl-phy0:RX
```
followed by
```
ADDRCONF(NETDEV_UP): wlan0: link is not ready
```

I'll get the exact output from syslog a bit later, but wanted to know what else I can do to troubleshoot this or if anyone knew of a fix for this.  I hadn't been able to find anything exatly like this in the forums.

Thanks in advance!

---

### Post by superprash2003 on 2009-05-23
could be related to this [http://ubuntuforums.org/showthread.php?t=1146367](http://ubuntuforums.org/showthread.php?t=1146367)

---

### Post by version7x on 2009-06-03
Thanks for the tip!  I had done some searching, but couldnt find concise information.

I've now updated my kernel, installed backports, and turned off ipv6.  I'll give it a shot when I get home an see if that does the trick!

Thanks!

---

### Post by version7x on 2009-06-03
I've installed the 2.6.29 kernel and I've now been connected for 20 minutes straight!  Thats beats my last record by about 19 minutes, 30 seconds.


I do have a lot lower signal strenght that's going in and out, but a definite stable connection.

Thanks for the help!

-M

---

