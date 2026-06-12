---
title: "[SOLVED] Samsung Monitor Woes"
date: 2008-07-17
forum: Multimedia Software
---

### Post by elkade on 2008-07-17
I have 2 desktop top pc's with Hardy Heron installed.  My monitor is a Samsung SyncMaster 226bw.  The pc's access the monitor through an IOGear 4 port KVM.

One pc has Linux 2.6.24-19 generic, MB is ASRock AM2NF6G-VSTA with NVIDIA NF-6100-405 Single Chip, AMD 64x2 dual core 4200, 1 gig RAM

I am able to see approx. 12 different screen resolution settings, am currently using 1152 x 864 55 Hz.

All is well with this PC

Now with #2 PC I have issues with screen resolutions, only 2 are available 320 x 240 & 640 x 480

I installed Ubuntu on this one at a friends, and a standard 15" CRT was connected to the pc.  I was able to choose from approx. 12 resolution settings.  When I got home and connected through the KVM my headaches started.

PC #2 has Linux 2.6.24-19 generic, MB is a PC Chips A13G with NVIDIA MCP61 single chip, AMD 64x2 dual core 5400, 3 gig RAM

I unhooked from the KVM switch and hooked to a 15" crt.  All screen resolution settings are available, go figure.

Both PC's have NVIDIA accelerated graphic drivers(latest cards) enabled and in use.  For some reason PC #2 with the MCP61 chip set isn't recognizing the Samsung monitor. 

Wondering if any one may have a suggestion or solution to my little problem?  Any help would be greatly appreciated.

Thanks,

Larry ](*,)

---

### Post by xc3RnbFO8P on 2008-07-17
For #2
ALT+F2
> gksudo displayconfig-gtk
Choose **Generic **
and resolution that your monitor supports.

---

### Post by elkade on 2008-07-22
Ringi,

I followed your instructions, and all is well.  Thank you very much for your assistance.

I bought a Sanyo TV/Monitor and display was perfect.  Even had several resolutions to choose from.  But now that I have this fix applied to my Samsung 22" monitor, I can save a few bucks.  I put your instructions in Tomboy.

Thanks again,

Larry :D  ):P

---

