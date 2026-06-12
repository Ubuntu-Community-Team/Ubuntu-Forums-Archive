---
title: "frontend 0/0 timed out while tuning to channel"
date: 2011-12-04
forum: Multimedia Software
---

### Post by fobos.deimos on 2011-12-04
Hello all,

Recently I bought Technisat Skystar HD2 card for my new HTPC. I've installed mantis drivers and v4l-dvb-dkms.

This is what I get with dmesg|grep -i dvb is:
```
box:~$ dmesg|grep -i dvb
[   13.946153] DVB: registering new adapter (Mantis DVB adapter)
[   14.856455] DVB: registering adapter 0 frontend 0 (STB0899 Multistandard)...

```b```
ox:~$ dmesg|grep -i mantis
[   13.945121] Mantis 0000:05:01.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   13.946153] DVB: registering new adapter (Mantis DVB adapter)

```I use 1.7.20-8yavdr1 version of VDR on ubuntu 10.04 x86 OS.

I'm a newbie in ubuntu and have very little experience with it. 

I'm having a problem that sometimes for no known to me reason, the card just stops working with message:
```
box vdr: [1283] frontend 0/0 timed out while tuning to channel 365, tp 212051
```Sometimes, it starts to work after a while, but most of the times i need to reboot.
I was looking everywhere for a solution to this problem, but can't find anything. Can someone please help me with this, as it is very annoying and i can't use my system as i would like to.

Sorry, but I'm not sure which kind of logs/data would need such troubleshooting, otherwise i would provide it. :(

---

