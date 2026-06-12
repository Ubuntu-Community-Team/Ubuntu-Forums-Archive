---
title: "Looking for Audio fix from reciever to speaker output"
date: 2015-01-19
forum: Multimedia Software
---

### Post by LoLaccount.01 on 2015-01-19
Hi im running Ubuntu 14.04 LTS  with AsRock H81M-ITX and i3 4150. The speaker sound test works but online browser sound  don't have any sound. I tried youtube and soundcloud. I Also  tried installing and reinstalling pulseaudio, doesn't seem to fix it.

Im runing my rig through HDMI cable to the Pioneer vsx-822 reciever. 


~~Thanks in advance

---

### Post by tom_rafalovitch on 2015-01-29
I have the same problem, if I connect the PC with Hdmi direct to the tv the sound works, but I want to use my reciver. Did you find a solution ?? Thanks

---

### Post by Rob Sayer on 2015-01-31
Need a lot more info.  The MB and cpu doesn't help.  Read the stickies.

Paste into terminal:

lspci

and

sudo aplay -l

and post results here embedded in [code] tags.

BTW there are a number of crappy blogs etc that suggest purging pulseaudio.

This is a BAD idea.  It has a shedload of dependencies and purging it will cause problems.  Even if pulse was the problem you don't have to purge it to disable it.

And since the test works, and since you don't mention sound problems with media playback, I'm going too assume it's the browser that's causing the problems.  Which browser?

Myself I'd try searching "ubuntu [release version] [browser] hdmi".

The release version is important.  What works for a previous or later versions often won't work for yours.  I won't do something if it doesn't say it's for the right version, or if they don't tell you how  to undo changes and I don't know how myself.

---

### Post by LoLaccount.01 on 2015-06-22
Bump, Hi sorry took long 
```
00:00.0 Host bridge: Intel Corporation 4th Gen Core Processor DRAM Controller (rev 06)00:02.0 VGA compatible controller: Intel Corporation Device 041e (rev 06)
00:03.0 Audio device: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller (rev 06)
00:14.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB xHCI (rev 05)
00:16.0 Communication controller: Intel Corporation 8 Series/C220 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #1 (rev d5)
00:1c.2 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #3 (rev d5)
00:1d.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation C220 Series Chipset Family H81 Express LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode] (rev 05)
00:1f.3 SMBus: Intel Corporation 8 Series/C220 Series Chipset Family SMBus Controller (rev 05)
02:00.0 Ethernet controller: Qualcomm Atheros QCA8171 Gigabit Ethernet (rev 10)
gigi@Ubuntu-User:~$ sudo aplay -l
[sudo] password for gigi: 
**** List of PLAYBACK Hardware Devices ****
card 0: HDMI [HDA Intel HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: HDMI [HDA Intel HDMI], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: HDMI [HDA Intel HDMI], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: PCH [HDA Intel PCH], device 0: ALC892 Analog [ALC892 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: PCH [HDA Intel PCH], device 1: ALC892 Digital [ALC892 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

---

