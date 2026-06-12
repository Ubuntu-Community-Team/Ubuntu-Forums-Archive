---
title: "Ubuntu to run an HTPC? (Hardware acceleration of Video Files)"
date: 2008-07-09
forum: Multimedia Software
---

### Post by Zurtex on 2008-07-09
Hi, I was hoping to make a media centre / HTPC in the next few months.

I'm most excited about using a Linux variant to run it, where I can spend a lot of time tweaking it. So if anyone has any advice on this please point me in the right direction.

But most importantly, is there anyway to hardware accelerate video playback on Ubuntu (or any Linux)? So I could get a chipset where the majority of the video decoding was done off the CPU.

---

### Post by steefjeqv on 2008-07-09
Hi,

Hardware accelerated mpeg2 is possible with :

- nvidia xvmc
- some of the via epia boards
- drx3-like pci cards
- So called full featured TV cards : Hauppauge PVR for analog TV and all the Fujitsu-Siemens clones for Digital TV

I'm using VDR which initially was developed around the Fujitsu-Siemens DVB cards (also known as Hauppauge Nexus, TechnoTrend 2300, ....)
By know it also supports xvmc (nvidia), via epia, drx3, PVR-350.
Software mpeg2 (and mpeg4-h.264) is possible too.

[http://www.linuxtv.org/vdrwiki/index.php/Main_Page]("http://www.linuxtv.org/vdrwiki/index.php/Main_Page")

There's also MythTV and LinuxMCE :

[http://www.mythbuntu.org/]("http://www.mythbuntu.org/")

[http://www.linuxmce.org/]("http://www.linuxmce.org/")


Sadly, there's no mpeg4-h.264 hardware acceleration available at the moment for linux. 

Greetings,
Steven

---

### Post by Zurtex on 2008-07-17
Thanks for your reply. h.264 is, alas, the most important hardware acceleration I was looking for, which means for now that Linux just doesn't seem suitable for my HTPC :(

---

### Post by Jean__ on 2008-07-17
This is so sad. I really hope this changes sometime shortly.

---

