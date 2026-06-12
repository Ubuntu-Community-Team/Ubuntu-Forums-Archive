---
title: "Karmic Mythtv Analog Channel Scan Failure (ok in  Jaunty)?"
date: 2009-11-03
forum: Multimedia Software
---

### Post by dealcorn on 2009-11-03
In Jaunty, Mythtv recognizes and successfully scans analog channels on my Hauppauge 1600.  In Karmic, Mythtv will recognize and scan my Hauppauge 1600 but has no success.  During scan, signal strength is shown as none and "no lock".  

I do have an analog video source set up that indicates no listing grabber.  The same failure results if I specify "EIT" as my listing source.  Any suggestions would be appreciated and specifically whether others have experienced success with the Hauppauge 1600 in Karmic.  I have no digital source for this card so I am looking only at the analog side.

---

### Post by masux594 on 2009-11-03
First of all, have u seen if the TvCard il loaded correctly? You should check if the tuner and the card chipset is loaded .. Maybe with the karmic the tvcard modules doesen't load and then it doesen't recognize your tvcard in the right way..

Sysc, A

---

### Post by dealcorn on 2009-11-03
lspci -v indicates:

03:04.0 Multimedia video controller: Conexant Systems, Inc. CX23418 Single-Chip MPEG-2 Encoder with Integrated Analog Video/Broadcast Audio Decoder
	Subsystem: Hauppauge computer works Inc. Device 7444
	Flags: bus master, medium devsel, latency 64, IRQ 16
	Memory at f8000000 (32-bit, non-prefetchable) [size=64M]
	Capabilities: <access denied>
	Kernel driver in use: cx18
	Kernel modules: cx18

Does this mean the tuner and card chipset are loaded?

---

### Post by GrugFromAus on 2009-11-03
I have what appears to be exactly the same problem. MythTV 0.21-fixes under Hoary could do an analog scan fine, but a fresh install of Karmic fails to move above 0.

Yes, I have tested the card works. DVB is happy under MythTV and analog scan and viewing is fine under TVTime.

Also, manually entering the channels from TVTime into Myth doesn't work, nor does using the channel data from Hoary. Interestingly, the channel freqs from the Hoary database don't match those of TVTime. My thoughts are that there might be something screwy with the channel tables (Australia is selected in all cases).

This problem is the only reason I'm doing a scan, and it shouldn't affect the scan anyways.

I've got a Compro VideoMate DVB-T300 (hybrid card) with freshly compiled v4l modules. The init stage of boot is identical to that under Hoary, with the exception that the v4l2 driver is 0.2.15 rather than .14 and there is a warning about IRQ sharing (which shouldn't be related to this as it works under TVTime).

There is an interesting thing in the Trac about the analog scan button being disabled, but I'm assuming that was after .22 was released. Basically, still looking.

---

### Post by deankovell on 2009-11-07
having the same problem, so I thought I'd give it a bump.

---

### Post by masux594 on 2009-11-07
Oki, this is the "general rule"..
A tv card have two components for work as well
>The tuner
>The chipset
So, I don't have specifically your card, but i've followed these steps..
1> Found the tvcard tuner name and card name [for example mine is a gigabyte card, but it has a Philiphs chipset, so search for these two params]..
2> Find the "tuner number" and "card number" for insert it into modprobe.d [that load the tuner and card chipset modules at startup]
3> Check if the tuner and card modules are included in your kernel
4> If they are included, see in the modprobe.d[/etc/modprobe.d/] if you have a "conf" that loads these modules 
5> If everything works, see if in the dmesg if the tuner module and the card module
6> if ALL these steps are ok, so, the card drivers that u need is installed, and so, mythtv may work as well

Sysc, A

P.s. I know that looks hard, but every step is very quick...

---

