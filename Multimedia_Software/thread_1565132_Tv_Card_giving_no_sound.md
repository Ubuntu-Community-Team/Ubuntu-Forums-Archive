---
title: "Tv Card giving no sound"
date: 2010-08-31
forum: Multimedia Software
---

### Post by m2rt on 2010-08-31
Hey,

I am running a fresh install of latest Ubuntu and trying to get my TV Card to work. I have tried mythtv and tvtime but nothing with them.

Normal audio works. Set everything to max level with alsa.

Device info:
$ hwinfo --tv card
05: PCI 0a.0: 11200 TV Card                                     
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_1131_7133
  Unique ID: bSAa.asSYQMshbxE
  SysFS ID: /devices/pci0000:00/0000:00:0a.0
  SysFS BusID: 0000:00:0a.0
  Hardware Class: tv card
  Model: "Avermedia AVerTV GO 007 FM"
  Vendor: pci 0x1131 "Philips Semiconductors"
  Device: pci 0x7133 "SAA7131/SAA7133/SAA7135 Video Broadcast Decoder"
  SubVendor: pci 0x1461 "Avermedia Technologies Inc"
  SubDevice: pci 0xf31f "Avermedia AVerTV GO 007 FM"
  Revision: 0xd0
  Driver: "saa7134"
  Driver Modules: "saa7134"
  Memory Range: 0xe0002000-0xe00027ff (rw,non-prefetchable)
  IRQ: 18 (no events)
  Module Alias: "pci:v00001131d00007133sv00001461sd0000F31Fbc04sc80i00"
  Driver Info #0:
    Driver Status: saa7134 is active
    Driver Activation Cmd: "modprobe saa7134"
  Config Status: cfg=new, avail=yes, need=no, active=unknown


Anything else you need to know to help me?
Thanks!

---

### Post by lidex on 2010-09-03
Go to your sound preferences and select your tv card on the hardware tab. On the input tab make sure the device is not muted.

---

### Post by mike4ubuntu on 2010-09-23
I have a similar problem with my tv card.  I have a bt878 card.  It has a jumper for sound into the line-in of the sound card.  I look at the pulse audio sound preferences and I can select the sound card line-in for input and I can see that the sound in coming in from the input level meter on the input tab.  However, I still don't hear anything with tvtime or xawtv, even though the picture is fine and I can change channels.  I get sound from other sources such as rythmbox or just clicking on the sound effects, but no sound from the tvtime and xawtv.  Any ideas?

---

### Post by mike4ubuntu on 2010-09-27
I needed to install the gnome-alsamixer app to be able to unmute the line-in source.  Apparently, the pulse audio sound preferences dialog didn't make that available.  Now I get sound when playing TVTime just fine and a decent volume levels, but using ffmpeg or streamer to record produces only low volume playback.  Not sure why the difference between record and live volume levels.

---

