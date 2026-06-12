---
title: "What am I doin wrong? Dual Head setup"
date: 2005-10-13
forum: Multimedia &amp; Video
---

### Post by jadacyrus on 2005-10-13
Okay, I've got a Nvidia GEForce 6800GT on AGP and an ATI Radeon 7200 on PCI. Both cards worked by themselves when I switched primary video device from PCI to AGP and so forth in the bios. However when I try to have both cards running a multi-screen display I get the following error:

> (WW) RADEON: No matching Device section for instance (BusID PCI:2:3:0) found
(--) Chipset ATI Radeon QD (AGP) found


However running an X :1 -scanpci shows that the device is there..

> root@nanofiber:/home/alex#  X :1 -scanpci
Probing for PCI devices (Bus:Device:Function)

(0:0:0) unknown card (0x8086/0x2570) using a Intel Corp. 82865G/PE/P Processor to I/O Controller
(0:1:0) Intel Corp. 82865G/PE/P Processor to AGP Controller
(0:29:0) unknown card (0x8086/0x524c) using a Intel Corp. 82801EB USB
(0:29:1) unknown card (0x8086/0x524c) using a Intel Corp. 82801EB USB
(0:29:2) unknown card (0x8086/0x524c) using a Intel Corp. 82801EB USB
(0:29:3) unknown card (0x8086/0x524c) using a Intel Corp. 82801EB USB
(0:29:7) unknown card (0x8086/0x524c) using a Intel Corp. 82801EB USB2
(0:30:0) Intel Corp. 82801BA/CA/DB/EB PCI Bridge
(0:31:0) Intel Corp. 82801EB LPC Interface Controller
(0:31:1) unknown card (0x8086/0x524c) using a Intel Corp. 82801EB Ultra ATA Storage Controller
(0:31:2) unknown card (0x8086/0x524c) using a Intel Corp. 82801EB Ultra ATA Storage Controller
(0:31:3) unknown card (0x8086/0x524c) using a Intel Corp. 82801EB SMBus Controller
(0:31:5) unknown card (0x8086/0xe000) using a Intel Corp. 82801EB AC'97 Audio Controller
(1:0:0) unknown card (0x1043/0x81a3) using an unknown chip (DeviceId 0x0045) from nVidia Corporation
(2:1:0) unknown card (0x1102/0x0051) using a Creative Labs SB Audigy
(2:1:1) unknown card (0x1102/0x0040) using a Creative Labs SB Audigy MIDI/Game port
(2:1:2) unknown card (0x1102/0x0010) using a Creative Labs SB Audigy FireWire Port
(2:2:0) unknown card (0x1317/0x0570) using a Linksys Network Everywhere Fast Ethernet 10/100 model NC100
(2:3:0) unknown card (0x1002/0x0039) using a ATI Technologies Inc Radeon R100 QD [Radeon 7200]

This leads me to beleive it has somethign to do with my xorg.conf file, so here it is. is there something I am missing here? I've been trying to get this to work forever, this should be a simple thing.
Here is a snippet of the relevant stuff from /etc/X11/xorg.conf:
> 

Section "Device"
	Identifier	"NVIDIA Corporation NV40 [GeForce 6800 GT]"
	Driver		"nv"
	BusID		"PCI:1:0:0"
	Screen		0
EndSection

Section	"Device"
	Identifier	"ATI Radeon 7200"
	Driver		"radeon"
	BusID		"PCI:2:3:0"
	Screen		1
EndSection

Section "Monitor"
	Identifier	"Generic Monitor 2"
	Option		"DPMS"
	HorizSYnc	28-64
	VertRefresh	43-60
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"NvidiaScreen"
	Device		"NVIDIA Corporation NV40 [GeForce 6800 GT]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "Screen"
        Identifier      "ATIScreen"
        Device          "ATI Radeon 7200"
        Monitor         "Generic Monitor 2"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
EndSection

Section "ServerFlags"
	Option	"Xinerama"	"ON"
EndSection

Section "ServerLayout"
	Identifier	"Dual Head Layout"
	Screen		0 "NvidiaScreen" 0 0
	Screen		1 "ATIScreen" LeftOf "NvidiaScreen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection


Please help me!

---

### Post by MetalMusicAddict on 2005-10-13
Sorry man. I dont think Ive ever seen this question. "Dual Head" is a little inaccurate. It should be "Dual Card". I hope you get this workin. Would be good info to know. ;)

---

### Post by jadacyrus on 2005-10-13
Actually it is commonly referred to as running a Dual Head system when you have two monitors and two video cards.. EIther that or multi-screen but I Dont think i've ever heard it referred to as Dual-Card...

---

### Post by starscalling on 2005-12-12
well first off make sure the drivers for the second // non nvidia card work ok
ive heard of conflits when nvidia and teh 'other' drivers are in the same system... the xorg itself looks ok from a glance...

---

### Post by MyKal on 2006-12-24
> **jadacyrus said:**
> Actually it is commonly referred to as running a Dual Head system when you have two monitors and two video cards.. EIther that or multi-screen but I Dont think i've ever heard it referred to as Dual-Card...

actually unless im mistaken metalmusicaddict is correct as "dual head" actually refers to running two monitors off of a single video card with dual outs 

as you are using two induvidual cards dual head would not be the propper term but then i may be completely mistaken so dont take my word for it

---

### Post by majoridiot on 2006-12-24
dual head is any box with two displays... although a more correct description of this one would be "dual-card, dual-head".

in any event, try adding the following to the radeon device section:

```
    Option      "UseInt10Module" "1"
```

is this doesn't fix it, post a copy of your entire /var/log/Xorg.0.log after it fails and we'll see 
what it has to say.

---

### Post by Mike'sHardLinux on 2006-12-25
I agree with MyKal and MetalMusicAddict. Dual Head refers SPECIFICALLY to a video card with 2 outputs. Here is a link that supports this arguement. [http://www.webopedia.com/TERM/D/dual_head_card.html]("http://www.webopedia.com/TERM/D/dual_head_card.html")

A dual display system is just that, dual display.

---

### Post by n1gke on 2006-12-25
I have sent an attachment named xorg.conf.txt for you to look at.

It took awhile for me to locate the correct driver software and then finger out where the files were supposed to go as the original installer was wanting another OS, like Fedora Red Hat and didn't like the idea that I am using Ubuntu v.606 LTS.

Patience and work. It only took me a few days of effort to make it all work.

I am happy with the Matrox G400/G450 dual-head video card, even with only 16 Megs of video memory, it works all okay.

I hope you get the attachment and it is helpful. I will work with you on this as best as possible as that is what two other folks did for me to make it work.

I found a lot of assistance on the irc.freenode.net #ubuntu channel as well.

---

