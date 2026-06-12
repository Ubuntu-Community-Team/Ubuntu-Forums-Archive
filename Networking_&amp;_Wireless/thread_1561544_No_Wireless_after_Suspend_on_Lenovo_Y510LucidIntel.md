---
title: "No Wireless after Suspend on Lenovo Y510/Lucid/Intel 4965"
date: 2010-08-26
forum: Networking &amp; Wireless
---

### Post by Clippy on 2010-08-26
Hi,

A few months back, my Lenovo IdeaPad Y510 stopped connecting to my wireless network after coming out of Suspend (it had worked fine previously).  Wireless networking is simply disabled, and I have to reboot in order to get it back.  I tried upgrading my OS from Intrepid all the way to Lucid, but the problem persisted.  I also tried changing my 00sleep_module as suggested in [this thread]("http://ubuntuforums.org/showthread.php?t=1017306&highlight=wireless+suspend&page=2"), but to no avail.

Here are my specs:

```
 *-network               
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 61
       serial: 00:1f:3b:c9:3f:17
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn ip=192.168.0.103 latency=0 mul
```

I have researched this problem quite a bit, but so far haven't had any luck.  Any help (preferably in beginner-friendly terms) would be greatly appreciated!

---

### Post by salmonsm on 2010-12-15
I'm having the same problem with my Dell D400 (Intel 855GM) with built-in Broadcom wireless.

---

### Post by vyellapa on 2010-12-22
My wireless(Atheros A8131 on Lenovo V560) ain't working after waking up from hibernate.what to do?

---

### Post by kivantsov on 2011-03-09
I had the same problem. And solution was simple. When wi-fi dropped, it just need to reload the module of your wi-fi card:
```

sudo rmmod -f iwlagn
sudo modprobe iwlagn

```

---

### Post by nicco on 2011-04-16
I have the exact same problem on my Dell Latitude D630. I can confirm that the above rmmod/modprobe solution works. So thanks!

I actually had this problem a few years ago, then it went away after an upgrade (don't remember which Ubuntu release.) Now it seems to be back. I am guessing this is basically a crash bug in the iwlagn driver. It doesn't seem to crash everytime after suspend though, just sometimes. And after heavy use it can stop working even when not suspending, but the modprobe solution solves it.

---

