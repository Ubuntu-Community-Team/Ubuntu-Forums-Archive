---
title: "BCM43224 wireless max speed"
date: 2011-08-16
forum: Networking &amp; Wireless
---

### Post by robalrr on 2011-08-16
Hi I have a wireless card BCM43224, I have a problem I can't achieve the max speed I have contracted. From speedtest.net I got a speed of 20M using ubuntu and 50M (the speed I contracted) from windows, in both I tried with firefox and chrome. I think there is a problem with the driver. 

I was participating in this bug [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/774496]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/774496") because I had the problem of freezing.

Somebody have info about the limitations of the drivers. Thanks

This is the info of my system:

```
uname -a

Linux katara 2.6.39-0-generic #5~20110427-Ubuntu SMP Wed Apr 27 15:27:41 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

lspci -vvnn | grep Network

12:00.0 Network controller [0280]: Broadcom Corporation BCM43224 802.11a/b/g/n [14e4:4353] (rev 01)

lspci -k | grep Network --after-context 3

12:00.0 Network controller: Broadcom Corporation BCM43224 802.11a/b/g/n (rev 01)
	Subsystem: Dell Device 000e
	Kernel driver in use: brcmsmac
	Kernel modules: wl, brcmsmac
```

---

