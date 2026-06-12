---
title: "Graphics Issues on MX3215 with Ibex"
date: 2009-01-24
forum: Multimedia Software
---

### Post by /sys/null on 2009-01-24
Hey everyone,

I hope you'll be able to help me out. Just a few days ago I unearthed this old Gateway MX3215 laptop from the depths of the closet and decided that it could be a formidable host for Ubuntu. It had Windows XP installed before I ran the Ubuntu installer, and was working OK -- albeit slow and undesirably non-unix.

When first installing, the graphical CD I burned subsequently did not run on the laptop, and I attributed this to graphics card problems -- when it came time to run the LiveCD or begin installation graphically, the system would hang until forcibly shut down. The MX3215 has an integrated graphics chip, the S3 Graphics UniChrome Pro IGP, as stated on the box. It had worked flawlessly on Windows, and after doing some digging I realized that there were some issues with getting these brand of IGPs to work with Ubuntu, but it had been done before. So I decided to go for it and burned the text-only install CD.

It installed without a hitch, and when booting up into the login screen, I noticed that the Ubuntu logo was actually in the lower-left of the screen, as well as the login box pushed into that corner. It's a little hard to explain, but it seemed to me that the screen resolution was set incorrectly, and that somehow a resolution larger than 1280x800 was being used with the graphics card. As I logged in to the system, it was obvious -- the mouse could get lost on the left and bottom sides of the screen, and the panel at the bottom with the window manager was out of reach. Also, the time element on the top panel was not visible, as it was set to reach the top right edge of the screen. After opening the display manager, it showed that the screen was running at 1600x1200. And that... is obviously not the resolution. After running xrandr, it stated that the system was indeed running at 1600x1200, and that the maximum resolution by the graphics card was 1600x1200.

But here's the kicker: when I switched to 1280x800 with xrandr or in the display settings, the display outputted this horrible garbly mess that seemed to stretch pixels across the screen, offset a little bit but ultimately unreadable. Here's what I mean...

[[IMG]http://img164.imageshack.us/img164/4889/photoxe4.th.jpg[/IMG]](http://img164.imageshack.us/my.php?image=photoxe4.jpg)

I had to exit to command line and login/logout. When I did, the system restored the screen to 1600x1200 automatically.

Once there, I installed all the system updates over Ethernet, got the Broadcom Wireless drivers to work, the sound to work, the trackpad and battery to work, but I can't fix this screen resolution problem.

I've tried following the installation instructions to install the OpenChrome drivers, but when I do there is no change. Occasionally, I'll mess around with /etc/X11/xorg.conf so much that Ubuntu will reboot into low-graphics mode. After I allow Ubuntu to reconfigure, the file is replaced with generic settings and the system returns to how it was.

Here is my current xorg.conf file, in which I added the "Driver" line to the Device section:
```

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"openchrome"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

```

PS -- Running sudo dpkg-reconfigure -phigh xserver-xorg in a console returns nothing, and I suspect it just replaces the current xorg.conf with a generically-configured one.

MX3215 system specifications:
> Intel Celeron M Processor 360
Operates at 1.40 GHz, 1 MB L2 Cache
and 400 MHz FSB

14" Widescreen Ultrabright WXGA TFT (that runs at 1280x800 in Windows)

256 MB DDR2 Dual Channel Memory

S3 Graphics UniChrome Pro IGP
64 MB shared VRAM

60 GB HDD, 4200 RPM

Any help would be much appreciated. Thank you!

---

### Post by Awolsmith on 2009-01-24
I have run into very simaliar problems with my Gateway 3215. I have successfully installed 7.04 and got the video resolution 1024x768 with audio but still no wireless card. I knew that 8.10 had wireless card and audio fixed but the resolution was to high for screen but looked clear. So this last time I tried to incrementally upgrade from 7.04 to 8.10. But once I got to 8.10 the screen resolution did not stay at 1024x768 but went to the higher one that is bigger than the monitor. So I am at a loss also. I may just have to try and find a wireless driver for the 8.04 version since that was the last video resolution that looked decent enough to live with. That is my 2 cents but I did find a link that was very helpful for the audio and video resolution for 7.04. I am wondering if that user had any success upgrading to a newer OS version?

---

### Post by rtomek on 2009-01-29
1280x800 gave you junk because the monitor's resolution is 1280x768.

I'm installing ubuntu on this little guy right now (albeit I upgraded the memory and processor to a Pentium M 745A) so perhaps I'll be able to give you some help.  I had mandriva on it before and everything was working great.  A few years ago I sold this laptop and I just got it back when they upgraded.  :)

---

### Post by arkindal on 2009-09-07
I received this from a friend as a gift, I followed many guides and I'm kinda disperate now, asked for help in italian forums, tried with arch too, frustrated I reinstalled arch, the only thing working fine for me was x, so well... if someone have this laptop, with any linux distro working fine on it and want to give me a BIG help... it would be nice if he/she can make a .iso file for me to download, because after guides and suggestions I think I just cant make it work :(

EDIT: By the way...

```
Section "InputDevice"
Identifier "Generic Keyboard"
Driver "kbd"
Option "XkbRules" "xorg"
Option "XkbModel" "pc105"
Option "XkbLayout" "us"
Option "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "Emulate3Buttons" "true"
EndSection


Section "InputDevice"
Identifier "Synaptics Touchpad"
Driver "synaptics"
Option "SendCoreEvents" "true"
Option "Device" "/dev/psaux"
Option "Protocol" "auto-dev"
Option "HorizEdgeScroll" "0"
EndSection
Section "Device"
Identifier "Configured Video Device"
Boardname "vesa"
Busid "PCI:1:0:0"
Driver "openchrome"
Screen 0
Option "SWcursor" "true"
Option "EnableAGPDMA" "True"
EndSection

Section "Monitor"
Identifier "Configured Monitor"
Vendorname "Generic LCD Display"
Modelname "LCD Panel 1280x800"
Horizsync 31.5-50.0
Vertrefresh 56.0 - 65.0
modeline "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
modeline "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
modeline "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
modeline "1280x800@60" 83.46 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
Gamma 1.0
EndSection

Section "Screen"
Identifier "Default Screen"
Device "Configured Video Device"
Monitor "Configured Monitor"
Defaultdepth 24
SubSection "Display"
Depth 24
Modes "1280x768@60" "1280x720@60" "800x600@60" "1280x800@60" "800x600@56"
Virtual 1280 768
EndSubSection
EndSection

Section "ServerLayout"
Identifier "Default Layout"
screen 0 "Default Screen" 0 0
Inputdevice "Synaptics Touchpad"
EndSection
Section "Module"
Load "glx"
Load "GLcore"
Load "dri"
Load "v4l"
EndSection
Section "device" #
Identifier "device1"
Boardname "vesa"
Busid "PCI:1:0:0"
Driver "openchrome"
Screen 1
EndSection
Section "screen" #
Identifier "screen1"
Device "device1"
Defaultdepth 24
Monitor "monitor1"
EndSection
Section "monitor" #
Identifier "monitor1"
Gamma 1.0
EndSection
Section "ServerFlags"
EndSection
```

---

### Post by hitjim on 2009-09-14
I had this same laptop (upgraded to 1gig ram) running at 1280x768 just fine for quite a while on 7x.  I tried to upgrade to 8.04 when 9.04 came out.  Then things went all wonky as you have described.  I tried a new 9.04 install as well.  I can get the liveCD to play nice, but no dice after installing, which is cruelly ironic.  

If I ever find a resolution, I'll post it here.

---

