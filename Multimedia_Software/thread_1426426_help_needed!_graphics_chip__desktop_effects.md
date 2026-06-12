---
title: "help needed! graphics chip / desktop effects"
date: 2010-03-10
forum: Multimedia Software
---

### Post by Beowulf.1000 on 2010-03-10
*** **[COLOR="Red"]SOLVED[/COLOR]** *** : See my reply to my own posting.

I need help getting my laptop display graphics working so I can use advanced desktop effects (Compiz). And what is odd is that just yesterday I had this automagically working, then had to reinstall Ubuntu and now do not have the graphics driver that worked yesterday, so I know it is possible to get this working.

I think the solution could be simple, maybe just need some help knowing what parameter to add to my GRUB2 boot options, because I believe when I installed Ubuntu I chose the low graphics option for the install-- and maybe that low graphics option stuck and was written to GRUB2?

Toshiba satellite U405 laptop. 
Ubuntu 9.10 x86 64bit desktop. 
Laptop graphics chip is: Intel Graphics Media, Mobile Intel (R) 965 Express Chipset Family. 

I checked in synaptic package manager looking for "intel" and the following is intalled (automagically by Ubuntu): xserver-xorg-video-intel which states it supplies the X driver for the intel 965 chipset, which my laptop has, so that is why I am mystified.

I had Ubuntu as the only OS on my laptop yesterday, then wiped it off, repartitioned the drive to put Windows Vista back on /sda1, then put Ubuntu on /sda2. One thing different, is that I believe to get the install to work this second time around I had to use the install option  "noapic", so not sure if that stuck and is interfering with graphics?

Like I said, when I had Ubuntu installed on the entire drive, I was able to choose advanced desktop effects, activate Compiz, have funky effects. Now all I can get for desktop effects (by right clicking on wallpaper and chosing change background, etc) is "Normal", if I click anything else Ubuntu looks for a driver to do advanced effects but nothing is found.

I really want to get back advanced desktop effects. Can anybody help me brainstorm through solving this? Thank you.
 Beowulf

---

### Post by Beowulf.1000 on 2010-03-10
Solved my own problem, very simply solution, but took a bit of digging on other threads here to find that solution. 
  [http://ubuntuforums.org/showthread.php?t=1114093](http://ubuntuforums.org/showthread.php?t=1114093)

The origin of the problem, I am certain, was in my installing ubuntu in low graphics mode during the options at the initial install process, and that low graphics mode ("vesa") stuck and was written into the xorg.conf file located in /etc/X11/xorg.conf

Here is the solution. And btw now I have advanced desktop graphics.

Open a terminal and go to /etc/X11 the make a backup copy of xorg.conf
$ cd /etc/X11
$ sudo cp xorg.conf xorg.conf.original
so that if something goes wrong you can restore the original config file.

Now edit xorg.conf
$ sudo gedit xorg.conf

And look for the Display section. My original Display section is seen below where I have pasted in my entire original xorg.conf file. Notce the lousy generic vesa driver that X boots into, giving me the lousy generic graphics! That Device section is the problem and what needs editing.


[B]Section "Device"
	Identifier	"Configured Video Device"
	[COLOR="Red"]Driver		"vesa"[/COLOR]
EndSection[/B]

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection



Here is my edited xorg.conf that solves this issue. Notice the driver is now set to the intel graphics chip, that of course was detected during the install but its driver just sits around somewhere unused until xorg.conf tells ubuntu, or rather X, to use it! I also specified the bus for the graphics chip, and found this by looking at the hardware devices (there are utilities for that which can be installed, I forget which package I installed for that).

[B]Section "Device"
	Identifier	"Configured Video Device"
	[COLOR="Red"]Driver		"intel"[/COLOR]
        BusId           "PCI:0:2:0"
EndSection[/B]

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection


So, edit the xorg.conf file Devices section, save the edited file. Reboot. Right click on the desktop and choose Desktop effects and you should be good.

:)

---

