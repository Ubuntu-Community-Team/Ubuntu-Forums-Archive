---
title: "Terrible video quality"
date: 2008-01-23
forum: Multimedia &amp; Video
---

### Post by Patogen on 2008-01-23
Divx/xvid playback: [http://81.235.216.106/test/2008-01-22-223323_1280x1024_scrot.png](http://81.235.216.106/test/2008-01-22-223323_1280x1024_scrot.png)
Dvd playback: [http://81.235.216.106/test/2008-01-22-223839_1280x1024_scrot.png](http://81.235.216.106/test/2008-01-22-223839_1280x1024_scrot.png)

How come my videos look like this? As you can see the quality is not what it's supposed to be (the xvid file IS a high quality file and the dvd is not supposed to look like this!). I'm running Gutsy x64 version on a C2D, it doesn't matter if I have w64codecs and non-free-codecs installed -- the playback still looks like this. 

I do have the ATI drivers installed and I do have dvd support. All xvid/divx/mpeg/dvd videos look like this, they look normal on windows xp / mac os x. It doesn't matter if I install vlc before I install the codecs or the other way round. 

Different players doesn't work aswell, totem, mplayer and vlc all look the same. I'm not 100% sure what specs somebody needs to try to help me with this, but I will give all the information you need ;)

---

### Post by jeffus_il on 2008-01-23
Xvid, is not a quality, it's a form of compression, you can make a good quality Xvid or a bad one, you choose. The are lots of  parameters to set when making an Xvid,  in short, there is always a trade off between size and quality, videos are often compressed very much to send over the internet, resulting in lower quality.

---

### Post by Patogen on 2008-01-23
> **jeffus_il said:**
> Xvid, is not a quality, it's a form of compression, you can make a good quality Xvid or a bad one, you choose. The are lots of  parameters to set when making an Xvid,  in short, there is always a trade off between size and quality, videos are often compressed very much to send over the internet, resulting in lower quality.

Oh yes, I know this -- but this file isn't a low quality file. It is a significant difference compared to windows. it simply doesn't look this bad in windows xp or mac os x.

Edit: Likewise dvd doesn't mean quality. You can have ugly looking dvd files as well, however this is rare from commercial DVD's. But you could put something with really awful quality on a dvd ... but these aren't low quality dvd or low quality divx/xvid! All look this way!

---

### Post by jeffus_il on 2008-01-23
How is the quality of a commercial DVD played on your system,using the same player as for the Xvid?

---

### Post by kinkyHelenMandarin on 2008-01-23
> **Patogen said:**
> I do have the ATI drivers installed and I do have dvd support. All xvid/divx/mpeg/dvd videos look like this, they look normal on windows xp / mac os x. It doesn't matter if I install vlc before I install the codecs or the other way round. 

I had the same problem, I just stopped using the ATI drivers -let ubuntu do whatever they feel like with the VGA-, and all's k.

---

### Post by eye208 on 2008-01-23
> **Patogen said:**
> I do have the ATI drivers installed and I do have dvd support.
But you forgot to enable XVideo. That's why the video output looks pixelated.

I have no idea why the ATI drivers come with XVideo disabled by default, but they do. You have to enable it by running this command:

sudo aticonfig --ovt Xv

The new setting will be written to the X.org configuration file. After you restart your computer or the X server, XVideo will be available.

XVideo will NOT work with Compiz. There is no way to warp or rotate a hardware-controlled video overlay, sorry. If you use Compiz, you will have to cope with ugly video. But at least you can rotate it on a cube. :mrgreen:

---

### Post by Patogen on 2008-01-23
> **jeffus_il said:**
> How is the quality of a commercial DVD played on your system,using the same player as for the Xvid?

You have a screenshot in my first post:
[http://81.235.216.106/test/2008-01-22-223839_1280x1024_scrot.png](http://81.235.216.106/test/2008-01-22-223839_1280x1024_scrot.png)

So it doesn't look alright aswell. It's from the dvd "Depeche Mode - Videos 86>98". 

> **kinkyHelenMandarin said:**
> I had the same problem, I just stopped using the ATI drivers -let ubuntu do whatever they feel like with the VGA-, and all's k.

I could try that, however then I won't be able to play games I suppose ... I'm not much for gaming but it's not fun if you have to give up things for playing movies on your computer.

> **eye208 said:**
> But you forgot to enable XVideo. That's why the video output looks pixelated.

I have no idea why the ATI drivers come with XVideo disabled by default, but they do. You have to enable it by running this command:

sudo aticonfig --ovt Xv


This didn't work. Getting Compiz to work is nothing that I do need or wish, I like to keep it simple.

---

### Post by jeffus_il on 2008-01-23
So it seems you have a general video problem, not just Xvid. You should be able to solve the problem with the ATI driver, if you are patient ...

---

### Post by jeffus_il on 2008-01-23
Found this in google, try it.
> Try different video outputs. For example: install xine-ui and set the video output to xv in the preferences.There are also other options, you'll see in the listbox.

---

### Post by Patogen on 2008-01-23
> **jeffus_il said:**
> So it seems you have a general video problem, not just Xvid. You should be able to solve the problem with the ATI driver, if you are patient ...

I don't follow this sort of stuff all that much, installed the newest drivers a couple of days ago. Are there new drivers coming that fixes this?

> **jeffus_il said:**
> Found this in google, try it.
There are also other options, you'll see in the listbox.

xine starts ... and shuts down right after I've started the program. Trying differen options with VLC I've tried and they all look the same ... (except for those ASCII outputs ;))

---

### Post by jeffus_il on 2008-01-23
xine should be fine (excuse the poetry)

run xine in a terminal and see what's making him unhappy.

It may be connected to your problem, if not, you'll have another player running.

---

### Post by Patogen on 2008-01-23
hedlund@shiva:/media/exwin/Toy$ xine
This is xine (X11 gui) - a free video player v0.99.5.
(c) 2000-2007 The xine Team.

And you see it start for a second and then shuts down. If I try this instead:

hedlund@shiva:/media/exwin/Toy$ xine Torkel\ I\ Knipa.mpg 
This is xine (X11 gui) - a free video player v0.99.5.
(c) 2000-2007 The xine Team.

And it does the same thing. I got the advice to try with xfmedia and it crashed my entire X. If this helps, this is my xorg.conf

```

# Fallback X.org config file
# FIXME: include the wacom devices (would only add noise at the current
#        development stage)

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"se"
EndSection

Section "InputDevice"
       Identifier "Configured Mouse"
       Driver "mouse"
       Option "CorePointer"
       Option "Device" "/dev/input/mice"
       Option "Protocol" "ExplorerPS/2"
       Option "ZAxisMapping" "4 5"
       Option "Emulate3Buttons" "true"
       Option "Buttons" "7"
       Option "ButtonMapping" "1 2 3 6 7"
EndSection


Section "ServerLayout"
	Identifier	"Default Layout"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
  screen 0 "screen1" 0 0
EndSection
Section "Module"
	Load		"GLcore"
	Load		"glx"
	Load		"dbe"
	Load		"v4l"
EndSection
Section "device" # 
	Identifier	"device1"
	Boardname	"VESA driver (generic)"
	Busid		"PCI:1:0:0"
	Driver		"fglrx"
	Screen	0
EndSection
Section "screen" # 
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
	SubSection "Display"
		Depth	24
		Modes		"1280x1024@75"	"1280x960@60"	"1152x864@75"	"1280x1024@60"	"1024x768@60"	"1280x960@75"	"1024x768@70"	"1400x1050@60"	"1024x768@75"	"1600x1200@65"	"832x624@75"	"1600x1200@60"	"800x600@60"	"800x600@75"	"800x600@72"	"800x600@56"	"640x480@75"	"640x480@72"	"640x480@60"
	EndSubSection
EndSection
Section "monitor" # 
	Identifier	"monitor1"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
  modeline  "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@75" 129.86 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
  modeline  "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
	Gamma	1.0
EndSection
Section "device" # 
	Identifier	"device2"
	Boardname	"VESA driver (generic)"
	Busid		"PCI:1:0:1"
	Driver		"fglrx"
	Screen	0
EndSection
Section "screen" # 
	Identifier	"screen2"
	Device		"device2"
	Defaultdepth	24
	Monitor		"monitor2"
EndSection
Section "monitor" # 
	Identifier	"monitor2"
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection

```

---

### Post by jeffus_il on 2008-01-23
xine is a stable program and should be running well on your system, and X shouldn't crash.

---

### Post by jeffus_il on 2008-01-23
[SIZE=2][COLOR=Black]Maybe you should reconfigure X with 
[/COLOR][/SIZE]**[SIZE=2][COLOR=Black]```
sudo dpkg-reconfigure xserver-xorg
```[/COLOR][/SIZE]**

---

### Post by sanraj83 on 2008-01-23
> **Patogen said:**
> I don't follow this sort of stuff all that much, installed the newest drivers a couple of days ago. Are there new drivers coming that fixes this?



xine starts ... and shuts down right after I've started the program. Trying differen options with VLC I've tried and they all look the same ... (except for those ASCII outputs ;))


The reason is that your xv overlay is not existent. 

do this,

sudo aticonfig --ovt=Xv

( I think someone else suggested the same thing. )

not restart the system,

check if 

glxinfo | grep render

gives yes for direct erendering. If so run xine and things should fall in place. For some reason, gusty is bad w/ ati drivers. Try Feisty instead.

-- R

---

### Post by Patogen on 2008-01-23
> **sanraj83 said:**
> The reason is that your xv overlay is not existent. 

do this,

sudo aticonfig --ovt=Xv

( I think someone else suggested the same thing. )

not restart the system,

check if 

glxinfo | grep render

gives yes for direct erendering. If so run xine and things should fall in place. For some reason, gusty is bad w/ ati drivers. Try Feisty instead.

-- R

```

hedlund@shiva:/etc/X11$ sudo aticonfig --ovt=Xv
Warning: Option 'VideoOverlay' doesn't affect running session.
Warning: Option 'OpenGLOverlay' doesn't affect running session.
Using xorg.conf
Saved back-up to xorg.conf.fglrx-2
*** glibc detected *** aticonfig: munmap_chunk(): invalid pointer: 0x00007fff5757d9f2 ***
======= Backtrace: =========
/lib/libc.so.6(cfree+0x1b6)[0x2b9154373826]
aticonfig[0x4148ed]
aticonfig[0x414849]
aticonfig[0x40c6e5]
aticonfig(XOpenDisplay+0x2bd)[0x402485]
aticonfig(XOpenDisplay+0x141)[0x402309]
/lib/libc.so.6(__libc_start_main+0xf4)[0x2b915431bb44]
aticonfig(XOpenDisplay+0x62)[0x40222a]
======= Memory map: ========
00400000-00420000 r-xp 00000000 08:02 83064                              /usr/bin/aticonfig
00520000-00526000 rw-p 00020000 08:02 83064                              /usr/bin/aticonfig
00526000-00547000 rw-p 00526000 00:00 0                                  [heap]
2b915352c000-2b9153549000 r-xp 00000000 08:02 651532                     /lib/ld-2.6.1.so
2b9153549000-2b915354d000 rw-p 2b9153549000 00:00 0 
2b9153748000-2b915374a000 rw-p 0001c000 08:02 651532                     /lib/ld-2.6.1.so
2b915374a000-2b9153751000 r-xp 00000000 08:02 82791                      /usr/lib/libXrandr.so.2.1.0
2b9153751000-2b9153950000 ---p 00007000 08:02 82791                      /usr/lib/libXrandr.so.2.1.0
2b9153950000-2b9153951000 rw-p 00006000 08:02 82791                      /usr/lib/libXrandr.so.2.1.0
2b9153951000-2b915395a000 r-xp 00000000 08:02 82793                      /usr/lib/libXrender.so.1.3.0
2b915395a000-2b9153b59000 ---p 00009000 08:02 82793                      /usr/lib/libXrender.so.1.3.0
2b9153b59000-2b9153b5a000 rw-p 00008000 08:02 82793                      /usr/lib/libXrender.so.1.3.0
2b9153b5a000-2b9153b6b000 r-xp 00000000 08:02 82771                      /usr/lib/libXext.so.6.4.0
2b9153b6b000-2b9153d6a000 ---p 00011000 08:02 82771                      /usr/lib/libXext.so.6.4.0
2b9153d6a000-2b9153d6b000 rw-p 00010000 08:02 82771                      /usr/lib/libXext.so.6.4.0
2b9153d6b000-2b9153e75000 r-xp 00000000 08:02 82750                      /usr/lib/libX11.so.6.2.0
2b9153e75000-2b9154075000 ---p 0010a000 08:02 82750                      /usr/lib/libX11.so.6.2.0
2b9154075000-2b915407c000 rw-p 0010a000 08:02 82750                      /usr/lib/libX11.so.6.2.0
2b915407c000-2b915407d000 rw-p 2b915407c000 00:00 0 
2b915407d000-2b91540fd000 r-xp 00000000 08:02 652109                     /lib/libm-2.6.1.so
2b91540fd000-2b91542fc000 ---p 00080000 08:02 652109                     /lib/libm-2.6.1.so
2b91542fc000-2b91542fe000 rw-p 0007f000 08:02 652109                     /lib/libm-2.6.1.so
2b91542fe000-2b9154450000 r-xp 00000000 08:02 652032                     /lib/libc-2.6.1.so
2b9154450000-2b915464f000 ---p 00152000 08:02 652032                     /lib/libc-2.6.1.so
2b915464f000-2b9154652000 r--p 00151000 08:02 652032                     /lib/libc-2.6.1.so
2b9154652000-2b9154654000 rw-p 00154000 08:02 652032                     /lib/libc-2.6.1.so
2b9154654000-2b9154659000 rw-p 2b9154654000 00:00 0 
2b9154659000-2b915465b000 r-xp 00000000 08:02 82756                      /usr/lib/libXau.so.6.0.0
2b915465b000-2b915485a000 ---p 00002000 08:02 82756                      /usr/lib/libXau.so.6.0.0
2b915485a000-2b915485b000 rw-p 00001000 08:02 82756                      /usr/lib/libXau.so.6.0.0
2b915485b000-2b915485c000 rw-p 2b915485b000 00:00 0 
2b915485c000-2b9154861000 r-xp 00000000 08:02 82767                      /usr/lib/libXdmcp.so.6.0.0
2b9154861000-2b9154a60000 ---p 00005000 08:02 82767                      /usr/lib/libXdmcp.so.6.0.0
2b9154a60000-2b9154a61000 rw-p 00004000 08:02 82767                      /usr/lib/libXdmcp.so.6.0.0
2b9154a61000-2b9154a63000 r-xp 00000000 08:02 652035                     /lib/libdl-2.6.1.so
2b9154a63000-2b9154c63000 ---p 00002000 08:02 652035                     /lib/libdl-2.6.1.so
2b9154c63000-2b9154c65000 rw-p 00002000 08:02 652035                     /lib/libdl-2.6.1.so
2b9154c65000-2b9154c67000 rw-p 2b9154c65000 00:00 0 
2b9154c67000-2b9154c74000 r-xp 00000000 08:02 651586                     /lib/libgcc_s.so.1
2b9154c74000-2b9154e74000 ---p 0000d000 08:02 651586                     /lib/libgcc_s.so.1
2b9154e74000-2b9154e75000 rw-p 0000d000 08:02 651586                     /lib/libgcc_s.so.1
7fff57569000-7fff5757e000 rw-p 7fff57569000 00:00 0                      [stack]
ffffffffff600000-ffffffffff601000 r-xp 00000000 00:00 0                  [vdso]
Aborted (core dumped)

```

I have no idea what this means, I just know that it means something went wrong :lolflag:

---

### Post by Patogen on 2008-01-23
> **jeffus_il said:**
> [SIZE=2][COLOR=Black]Maybe you should reconfigure X with 
[/COLOR][/SIZE]**[SIZE=2][COLOR=Black]```
sudo dpkg-reconfigure xserver-xorg
```[/COLOR][/SIZE]**

This didn't work ...

---

### Post by eye208 on 2008-01-24
> **Patogen said:**
> *** glibc detected *** aticonfig: munmap_chunk(): invalid pointer: 0x00007fff5757d9f2 ***
This should not happen. It seems your system is seriously FUBAR. Backup your data and do a fresh install. Use Ubuntu's "Restricted Drivers Manager" to install fglrx. Then try running "sudo aticonfig --ovt Xv". If it crashes again, run memtest.

---

### Post by kinkyHelenMandarin on 2008-01-24
> **Patogen said:**
> 
[QUOTE=eye208;4189956]But you forgot to enable XVideo. That's why the video output looks pixelated.

I have no idea why the ATI drivers come with XVideo disabled by default, but they do. You have to enable it by running this command:

sudo aticonfig --ovt Xv

The new setting will be written to the X.org configuration file. After you restart your computer or the X server, XVideo will be available.

XVideo will NOT work with Compiz. There is no way to warp or rotate a hardware-controlled video overlay, sorry. If you use Compiz, you will have to cope with ugly video. But at least you can rotate it on a cube. :mrgreen:
This didn't work.[/QUOTE]

I don't know what goes on with Compiz but through eye208's proposition I can use the ATI drivers & have non-pixelated movies play for me.

And as he also says on the previous post, I used the Restricted Drivers Manager. I didn't do anything manually, except the aticonfig --... .

---

### Post by Patogen on 2008-01-25
> **eye208 said:**
> This should not happen. It seems your system is seriously FUBAR. Backup your data and do a fresh install. Use Ubuntu's "Restricted Drivers Manager" to install fglrx. Then try running "sudo aticonfig --ovt Xv". If it crashes again, run memtest.

Well I did this ... and this is why the screenshot link doesn't work anymore. I forgot to backup my www catalog ;) 

However -- it worked fine and since I had my /home on a separate partition I didn't need to reconfigure my apps.

---

### Post by Jay Jay on 2008-02-08
I've been having this same problem from the summer of 2007 and posted everywhere trying to get help to resolve it but no-one really understood the full extent. I hoped that now direct rendering is finally working on my laptop this issue would've disappeared. :(

My laptop also uses an ATI chipset, the Mobility P/M AGP 2x 8MB. I've tried using some of the commands listed in this thread to troubleshoot and correct but I always hit a brick wall. Can you help me too please? This is one of the few remaining obstacles preventing me from no longer requiring my Win2K partition.

---

