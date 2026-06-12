---
title: "Wired Networking failure - hardware or software?"
date: 2010-03-09
forum: Networking &amp; Wireless
---

### Post by djuke04 on 2010-03-09
The basics:

Ubuntu froze, restart and fsck etc - now there's no ethernet connection.
Booted in XP and it says - Device cannot start (code 10).
Syslog says: deactivating device (reason 2)
ifconfig says:

lo   Link encap: local loopback
     inet addr:127.0.0.1  Mask:255.0.0.0
     inet6 addr: ::1/128 Scope:Host
     UP LOOPBACK RUNNING MTU:16436  Metric:1
     RX packets: 0 errors:0 dropped:0 overruns:0 frame:0
     tx packets: 0  errors:0 dropped:0 overruns:0 carrier:0
     collisions:0 txqueuelen:0
     RX: bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

What now?



The longer story, with more details that may or may not be pertinent:

I was vacuuming the floor the other night and watching a tv show via my htpc.  It was running Linux at the time, but randomly froze while I was vacuuming.  After vacuuming, linux still worked kinda, but none of the menus worked and when I tried to restart it, the normal box that counts down to shutdown popped up with a bunch of squares instead of text and then didn't do anything.  After a forced restart, FSCK, and another couple restarts and strange startup behavior such as not recognizing the keyboard and mouse etc, it seemed to be back up and working like normal.  

Then I noticed it didn't have an internet connection.  This has happened before but I could just fiddle with the connection properties and it would eventually restart.  This time however it wouldn't do anything.  Also, when I left click on the network icon, all the options (eth0) and (eth1) are grayed out, not an option.  

So I restarted and booted into XP.  It doesn't work either now, where there weren't any problems before.  Device manager in windows says "Device Cannot Start - Code 10". Leopard doesn't work either... crap.  

So then I check syslog in Ubuntu.  It says a lot of crap about device changing state, citing "reason 2" and "reason 37" here and there, but at the end says "deactivating device (reason 2).  

I did and ifconfig at terminal and posted the output above.  

I'm not sure what the problem is, but did I somehow fry my ethernet card?

---

### Post by Iowan on 2010-03-09
Just my opinion - sounds like maybe more than the network card - although a corrupted hard drive could really play havoc with the OS(es).

---

