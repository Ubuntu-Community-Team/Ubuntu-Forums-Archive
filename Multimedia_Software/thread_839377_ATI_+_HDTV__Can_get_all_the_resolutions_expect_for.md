---
title: "ATI + HDTV:  Can get all the resolutions expect for 1360x768"
date: 2008-06-24
forum: Multimedia Software
---

### Post by whatever69 on 2008-06-24
I installed the proprietary driver (as noted by restricted driver messsage) but all I could get was 1600x1200, 1280x1024, 1024x768, etc...

My card is ATI Radeon 9500 Pro (275Mhz clock) and I have it attached through a VGA cable to a Samsung HDTV LN40A530.  In the TV manual, it has 1360x768 as a supported resolution through VGA, all the way to 1920x1080RB (no idea what RB means).

> $ glxinfo | grep vendor
server glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: ATI Technologies Inc.

My TV's manual states the following constraints:
Hor:  30-60
Ver:  60-75

and it also has a table for resolutions for the D-Sub (VGA) connections in Vesa Mode:

1360x768  H=47.712 V=60.015 PixelClock=85.500 +/+

From the command line, I get the following Modelines. Note how the H/V sync is never the same as the TV manual:

> $ cvt 1360 768 60.015
# 1360x768 59.80 Hz (CVT) hsync: 47.72 kHz; pclk: 84.75 MHz
Modeline "1360x768_60.01"   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync

$ gtf 1360 768 60.015

# 1360x768 @ 60.01 Hz (GTF) hsync: 47.71 kHz; pclk: 84.74 MHz
Modeline "1360x768_60.01"  84.74  1360 1424 1568 1776  768 769 772 795  -HSync +Vsync

When I click "Screens and Graphics", I can't find anything close to my TV.  It simply Says "Plug and Play" as the model for the TV.  I've tried some modelines but none have worked.  There's CVT, GTF, Online Modeline generators.  I'm quite confused why there are so many and which to use.

How to I go about "adding" this TV as monitor?  I've spent hours trying but can't seem to get anywhere past this point :( Please help!  Let me know if you need me to post anything.

xorg.conf:

> Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"fglrx"
	Option		"VideoOverlay"	"on"
	Option		"OpenGLOverlay"	"off"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc101"
	Option		"XkbLayout"	"us"
	Option		"XkbVariant"	"us"
	Option		"XkbOptions"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
EndSection

Section "Module"
	Load		"glx"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Extensions"
	Option		"Composite"	"Enable"
EndSection


---

### Post by whatever69 on 2008-06-25
Should I just give up trying to get my TV on 1360x768?  Anyone?

---

### Post by batty on 2008-06-25
Not sure if it will help in your case,but is it possible a setting on your TV
On my Hitachi in the setup menu I have to turn on WXGA and set it to 1024x768 or 1360x768
I have to be on the RGB2 channel to get this setup option in the Tv's menu.

Dave

---

### Post by whatever69 on 2008-06-25
Hi,

I've tried looking, and for the VGA port, there's no such setting.  I know for a fact for my TV, there's no DVI port.  Only 3 HDMI inputs, and only HDMI-2 is the one that can receive a mixed DVI/HDMI signal.  However, I have 2 computers, so I need to use the VGA on the Ubuntu one.

Thanks for the help.

---

### Post by danb0087 on 2008-07-18
> **whatever69 said:**
> Should I just give up trying to get my TV on 1360x768?  Anyone?


I finally got the correct resolution running Catalyst 8.6 proprietary driver (fglrx) on my Vizio L37 hdtv (primary display)

Background:
I used Method two from 
[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)
-after the first reboot, the black screen low resolution box popped up -> rebooted and the login displayed at 1024x768

To get 1366x768:
#this fixes the login screen resolution
$sudo aticonfig --hsync=0,<LOW-HIGH> #i.e. 30-60
$sudo aticonfig --vrefresh=0,<LOW-HIGH> #i.e. 60-75

#and this keeps the resolution at 1366x768 after login
$sudo aticonfig --resolution=0,1280x768

for whatever reason, 1366x768 and 1360x768 aren't recognized as valid displays, but 1280x768 is recognized - and just "looks" right

changes don't take effect unitl you restart X
ctrl-alt-backspace

So, my TV menu says that it's displaying 1024x768, however the picture looks the same as when I was using the xserver-xorg-video-ati open source driver, and the TV menu displayed 1366x768 when running the open source driver.

You can also configure multiple displays using aticonfig, see 
[http://wiki.cchtml.com/index.php/Aticonfighelp](http://wiki.cchtml.com/index.php/Aticonfighelp)
or 
$sudo aticonfig --help | more

hope this helps

---

