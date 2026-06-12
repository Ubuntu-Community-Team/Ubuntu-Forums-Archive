---
title: "Won't connect to some wifi networks; connects to most"
date: 2010-07-17
forum: Networking &amp; Wireless
---

### Post by unclejames on 2010-07-17
I'm the proud owner of a BENQ Joybook Lite (which you probably won't have heard of, since it's only available in some parts of Asia, where I bought it: less than 200 quid, with a decent keyboard and a sensible amount of memory).

Inside is a:
```
01:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)
```

This connects to almost all wifi networks. It doesn't, however, connect to two ones I've tried so far: my Android phone does, however, so I suspect a problem with the driver I'm using: the Broadcom STA proprietary driver.

The first network was an encrypted wifi point, a "BT Fusion" one in a coffee shop in central London, with a long alphanumeric password that was given to me on a scrappy piece of paper. After a long attempt to connect (the wifi indicator going in two distinct patterns), the machine comes back and asks me for the password again.

The second network is the one in this Fullers pub, which is an open network (with a redirect to a login).Here, there's a long pause while the machine attempts to connect (the wifi indicator going in two distinct patterns), followed by the machine giving up.

I'm lucky that my Android phone is running the latest version of Android, with a portable hotspot connection: so I'm not without wifi - but it's a nuisance to discover these don't work well.

Decent wifi is one of the most frustrating things for newbies to cope with when moving over to Ubuntu; I've used Ubuntu for quite some time, so knew how to get it working in the first place, but in order to help debug this, what information would be worthwhile capturing about these wifi points?

---

### Post by georgie on 2010-07-17
Hi James

sudo tail -f /var/log/syslog is a start - it should give you some chatter and hints about what's going wrong

George

---

### Post by nickpiggott on 2010-07-17
I wonder if it's closely related to [this problem]("http://ubuntuforums.org/showthread.php?t=1476007"), which affects Ralink rt2860 chipset?

Failing that, you could try recompiling the drivers from manufacturer's stock, as described [here]("http://linuxwireless.org/en/users/Drivers/b43")

I just have a hunch that it's related to ota encryption (AES or TKIP) which can still be present even in apparently unsecured networks. (I have had trouble getting onto a work "open" network provided by a CISCO AP which provides multiple SSIDs, some of which are fully secured).

---

