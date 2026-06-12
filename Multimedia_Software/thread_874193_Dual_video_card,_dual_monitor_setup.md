---
title: "Dual video card, dual monitor setup"
date: 2008-07-29
forum: Multimedia Software
---

### Post by mpentney on 2008-07-29
I'm trying to get dual monitors configured on Ubuntu 8.04. My PC is an HP Pavilion desktop with on-board Intel Extreme graphics chipset feeding a VGA output. I've added an ATI Radeon RV100 graphics card, which has both VGA and DVI outputs. I've two HP L2045w widescreen LCD monitors with 1680 x 1050 pixels each.

My first attempt to run both monitors was with Xinerama. I listed both graphics cards and both monitors in my xorg.conf file, with the "intel" driver for the on-board graphics card and the "ati" driver for the Radeon PCI card. I was able to get two independent desktops running, but whenever I tried to  turn on Xinerama, X would only run in low resolution mode.

I've now switched to using xrandr, and I've got an extended desktop working by running both monitors from the twin outputs of the Radeon card. But I don't have any Visual Effects, and (more annoyingly) I don't see the output of the power-on self tests and the GRUB loader menu - they are routed to the VGA output of the on-board graphics chips, even though I've deleted this from my xorg.conf.

All of the examples I've seen online using xrandr seem to use multiple outputs from a single graphics card. I'd really like to have one screen connected to the on-board chipset, and the other connected to the Radeon card. I'd expect this to give me access to the visual effects (as each card has 64MB of video memory), and I would see the POST messages and GRUB menu.

Thanks in advance if anyone can help...

---

### Post by markbuntu on 2008-07-29
If you want to see those things, you need to disable the on board graphics in the bios. There is a thread around in the hardware forum where some guy is using 4 video cards. Its title is

How many video cards can I use or something like that. Try a search and ask that guy, he seems to hang around there.

---

### Post by mpentney on 2008-07-30
Markbuntu:

Thanks for your reply. I've swapped my PCI video card with a similar spec AGP card, which automatically disables the on-board graphics chipset. So now I see the GRUB menu. I still don't get any visual effects, which I assume is something to do with OpenGL support. The video card has 64MB of RAM, which I guess is not quite enough to support a total display resolution of 3360x1050 (=33,768,000 pixels). I'll try playing around with the video driver options a bit and see what happens before I buy a new video card.

I see from this page:

[http://wiki.debian.org/XStrikeForce/HowToRandR12](http://wiki.debian.org/XStrikeForce/HowToRandR12)

that xrandr v1.2 does not support multiple graphics boards, so I've given up trying to use the on-board graphics and the PCI video card at the same time. (I don't know if there is a recipe to get this working with Xinerama - whenever I turned it on in my xorg.conf it crashed the X Server.)

Thanks again.

---

### Post by markbuntu on 2008-07-30
Anyway, the thread is here, if you haven't found it yet:

[http://ubuntuforums.org/showthread.php?t=854719](http://ubuntuforums.org/showthread.php?t=854719)

---

### Post by Cygoku on 2008-07-30
You cannot have dual mon + opengl at the same time yet.

Cygoku

---

### Post by executedisaster on 2008-08-25
> **Cygoku said:**
> You cannot have dual mon + opengl at the same time yet.

Cygoku

I'm not sure where you are getting this one from... I have 2 monitors running right now with hardware acceleration going. Everything is running smooth. They are on 2 separate X screens off the same card.

Cheers.

---

### Post by markbuntu on 2008-08-25
Well, some cards will support separate x sessions in a dual monitor configuration but many won't.

---

### Post by plnnightsky on 2008-08-25
I am also trying to get dual monitors working.  Being new ti Ubuntu, I can't figure out where to start.  I have search the groups and the web and have managed to mess my display up quite well.  Fortunately I did have a back up and have been able to recover after each attempt.  I have confirmed both monitors and outputs work from the the Nvida card.  I did this by disconnecting each of the displays are reboot.  The xorg.conf file seems to be the same for both displays. 
Where may I find information, I can understand.

Below is the xorg.conf:
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
EndSection
Section "Module"
	Load		"glx"
EndSection


Here is the out put of lspci:
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:01.0 Ethernet controller: VIA Technologies, Inc. VT6105 [Rhine-III] (rev 86)
02:00.0 Ethernet controller: Attansic Technology Corp. L2 100 Mbit Ethernet Adapter (rev a0)
04:00.0 VGA compatible controller: nVidia Corporation Unknown device 06e4 (rev a1)

---

### Post by Wolfexin on 2008-10-19
](*,)
This is my secound try on the linux os.It has been a big struggle for me.One of the problems is I have searched all over  for information on getting a dual monitor setup. I do not understand how to change the xorg.conf settings. I do not know how to get to where the forums I have been to, show. As in the  forums here.I have tried what I have read in all the forums I have been to.I do not understand how to change the setting for use of two monitors, for indepenent monitors.I  am a windows user and am trying to  learn linux. I like it. Please help me to solve at least this one problem. As of now, i installed  Twinview restarted and have both monitors on but i need them to be independent, to play on one and browse the internet on the other.One is a lcd and the other is a crt.My vidio card is Geforce 8500 pcie x16 dual.

---

