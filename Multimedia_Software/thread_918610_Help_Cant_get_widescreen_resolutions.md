---
title: "Help Cant get widescreen resolutions"
date: 2008-09-13
forum: Multimedia Software
---

### Post by mixersoft on 2008-09-13
I'm trying to get widescreen resolutions to display on my TV connected via RGB to my KPC K45 (Intel GMA950, Ubuntu 8.04.1). My default xorg.conf lets me see as high as 1024x768, but I cannot choose any widescreen resolutions. My TV says it can go as high as 1280x768 or 1368x768 in RGB mode.

xorg.conf (default):
[INDENT]Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection[/INDENT]


I looked at this page: 
[INDENT][https://help.ubuntu.com/community/FixVideoResolutionHowto#Undetected%20Monitor%20Specs](https://help.ubuntu.com/community/FixVideoResolutionHowto#Undetected%20Monitor%20Specs)[/INDENT]
and have manually edited the xorg.conf file after checking/trying the following:
[LIST]
[*] sudo ddcprobe | grep monitorrange
[*] sudo dpkg-reconfigure xserver-xorg
[/LIST]
but after a ctl-alt-backspace restart, I only get 800x600 in the Preferences>Screen Resolutions applet

xorg.conf (edited):
[INDENT]Section "Device"
        Identifier      "Configured Video Device"
        Boardname       "Intel 945"
        Busid           "PCI:0:2:0"
        Driver          "intel"  # also tried "i810"
        Screen  0
        Vendorname      "Intel"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
        Vendorname      "Hitachi"
        Modelname       "7800PDP Plasma"
        Horizsync       28-107
        Vertrefresh     50-85

# from: gtf 1280 768 60 -x
# 1280x768 @ 60.00 Hz (GTF) hsync: 47.70 kHz; pclk: 80.14 MHz
  Modeline "1280x768@60"  80.14  1280 1344 1480 1680  768 769 772 795  -$
# 1368x768 @ 60.00 Hz (GTF) hsync: 47.70 kHz; pclk: 85.86 MHz
  Modeline "1368x768@60"  85.86  1368 1440 1584 1800  768 769 772 795  -HSync +Vsync
                
        Gamma   1.0
EndSection
[/INDENT]

What am I doing wrong? It doesn't seem like the Screen Resolutions applet gives a rats a-- what's in the xorg.conf file.

TIA

---

### Post by Thomaseov on 2008-09-15
I'm in the same boat...anyone?  Same chipset, different widescreen monitor.  Can't get to 800x480 native, only 800x600.

---

### Post by Markor on 2008-10-07
I am also looking for 800x480 solution .

I want just to point out that there is Ubuntueee distribution
of Ubuntu Hardy that have 800x480 resolution problem solved
(i think they were using 915 chipset settings).

I just need solution for custom resolution on Any machine
(Per instance for machine inside QEMU/KVM for testing) etc.

Just a sec:.. Maybe this would help..
I just found videogen package in synaptic:
 sudo apt-get install videogen
=====
Create arbitrary-res modelines using hardware parameters
Videogen is a small but nice utility to create modelines you can
insert into your XF86Config(-4) and fb.modes files.

Modeline is created by telling the program the resolution you want
and your video hardware parameters (maximum video adapter
bandwidth, maximum HCF and VCF of the monitor etc).

The tool 'some_modes' may help you to create some common modes fast.
=====

---

