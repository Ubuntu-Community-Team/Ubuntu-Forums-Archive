---
title: "Flickering in openGL applications with fglrx driver"
date: 2008-07-27
forum: Multimedia Software
---

### Post by nv22nv on 2008-07-27
Hello,

I'm also one of those who's experiencing a problem with (PowerColor) ATI Radeon HD 3870 and would like to use OpenGL screensavers and watch videos on Kubuntu 8.04. Both is currently not possible without some kind of flickering which I can't get rid of. The flickering is especially present when large objects move over the screen fast. 

This is what I did so far:
[list]
[*] Compiz is not installed - when I had it activated things were a lot worse. Since uninstalling it's a lot better, but still far from acceptable.
[*] At first, I tried to use the proprietory ATI fglrx driver and executed the installation program. That also gave me the problem that I couldn't log out or shutdown my computer without having it crash. Adding *TerminateServer=true* into the sections of */etc/kde3/kdm/kdmrc* didn't help here, although some users say this did it for them.
[*] After being unable to get rid of the flickering, I tried installing the fglrx driver with EnvyNG (AFAIK, this installs the fglrx driver from the repository automatically and does all the condiguration stuff for you). Unfortunately, this didn't solve the flickering problem, but at least I could now log out of my account without having my computer crash.
[*] Then I tried the open source driver radeonhd. When I was finally done, I noticed that it doesn't have and 2D / 3D accelleration implemented, so this is of no use for me since it's not even possible to watch a video with it smoothly *sigh*. So back to EnvyNG. After various attempts to alter */etc/X11/xorg.conf* by hand with things that had helped other users, I'm still stuck with my problem and don't know what I could try.
[/list]
Here's my */etc/X11/xorg.conf*, perhaps someone's got a clue what I could try?
```
Section "Screen"
        Identifier      "aticonfig-Screen[0]"
        Device          "atiradeon"
        Monitor         "aticonfig-Monitor[0]"
        SubSection "Display"
                Depth   24
                Virtual 1400    1050
                Modes           "1280x1024@60"  "1400x1050@60"  "1280x960@60"   "1152x864@75"   "1024x768@60"   "1024x768@70"   "1024x768@75"   "832x624@75"    "800x600@60"    "8
00x600@75"      "800x600@72"    "800x600@56"    "640x480@75"    "640x480@72"    "640x480@60"
        EndSubSection
        Defaultdepth    24
EndSection

Section "Device"
        Identifier      "atiradeon"
        Busid           "PCI:1:0:0"
        Driver          "fglrx"
        Option          "TexturedVideo" "on"
        Option          "VideoOverlay"  "on"
        Option          "OpenGLOverlay" "off"
        Screen  0
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "de"
        Option          "XkbOptions"    "lv3:ralt_switch"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
  screen 0 "aticonfig-Screen[0]" 0 0
EndSection

Section "Module"
        Load            "glx"
        Load            "GLcore"
        Load            "v4l"
EndSection

Section "Monitor"
        Identifier      "aticonfig-Monitor[0]"
        Vendorname      "LG Electronics Inc."
        Modelname       "LG L1960TR (Digital)"
        Horizsync       30.0-71.0
        Vertrefresh     56.0-75.0
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
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
        Gamma   1.0
EndSection

Section "ServerFlags"
        Option          "AIGLX" "off"
EndSection

Section "Extensions"
        Option          "Composite"     "Enable"
EndSection

```

and here's the output of *hwinfo -gfxcard*
```
15: PCI 100.0: 0300 VGA compatible controller (VGA)
  [Created at pci.296]
  UDI: /org/freedesktop/Hal/devices/pci_1002_9501
  Unique ID: VCu0.ZNdfaaWhm72
  Parent ID: vSkL.695oDIffHYA
  SysFS ID: /devices/pci0000:00/0000:00:01.0/0000:01:00.0
  SysFS BusID: 0000:01:00.0
  Hardware Class: graphics card
  Model: "Hightech Information VGA compatible controller"
  Vendor: pci 0x1002 "ATI Technologies Inc"
  Device: pci 0x9501
  SubVendor: pci 0x1787 "Hightech Information System Ltd."
  SubDevice: pci 0x2244
  Driver: "fglrx_pci"
  Driver Modules: "fglrx"
  Memory Range: 0xd0000000-0xdfffffff (rw,prefetchable)
  Memory Range: 0xfe8e0000-0xfe8effff (rw,non-prefetchable)
  I/O Ports: 0xc000-0xcfff (rw)
  Memory Range: 0xfe8c0000-0xfe8dffff (ro,prefetchable,disabled)
  IRQ: 16 (158898 events)
  I/O Ports: 0x3c0-0x3df (rw)
  Module Alias: "pci:v00001002d00009501sv00001787sd00002244bc03sc00i00"
  Driver Info #0:
    Driver Status: fglrx is active
    Driver Activation Cmd: "modprobe fglrx"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #33 (PCI bridge)

Primary display adapter: #15

```

So has anyone got an idea what I could do to get rid of the flickering? Any help is appreciated!

---

### Post by markbuntu on 2008-07-27
Try VideoOverlay "off"

There are some other things you can try here:

[http://forum.compiz-fusion.org/showthread.php?t=6794](http://forum.compiz-fusion.org/showthread.php?t=6794)

You can also try fooling around with the settings in the Catalyst Control Center.

---

### Post by nv22nv on 2008-07-27
markbuntu, thanks for your reply!
> Try VideoOverlay "off"
Unfortunately, that didn't do it. If I only change this, I can't see any video at all. If I change everything the way it is shown in the first post of the topic you linked me to, I do see video but it's still flickering. Too bad. I'll try to read myself through this lengthy topic, but that doesn't seem promising to me.

I already tried everything I could in the ATI Catalyst tool, without any positive effect.

Yet, thanks again for your help!

---

### Post by Melcar on 2008-07-27
What kind of "flickering"?  Flickering as in screen tearing/distortion across the screen, or flickering as in rapid flashes of black over the video output?  The latter usually happens when you have Compiz on (or any form of transparency really) and trying to use Xv/openGL acceleration in movies and games; you can't really fix it since it's a problem with the current DRI framework (not fault of the driver), although the recent fglrx releases allow accelerated video playback (and games) without flickering as long as they're played in fullscreen.  The former looks more as if Vsync were off; this also happens on accelerated video playback and games and is a common issue of the driver (everyone seems to suffer from it to some degree of severity and there is no real fix for it yet).

---

### Post by nv22nv on 2008-07-27
> **Melcar said:**
> What kind of "flickering"?  Flickering as in screen tearing/distortion across the screen, or flickering as in rapid flashes of black over the video output? Good question, I should have explained that in more detail. What I'm talking about is the first effect you mention, videos tend to separate into blocks which are moved out of place horizontally.

If everyone has these effects and there is no solution for this kind of problem, that is also helpful for me, because I don't need to waste more days in front of my computer trying to fix a problem which can't be fixed. It has already cost me two full days :mad:. In this case, I will return the crappy ATI product and get an nvidia card instead.

Thanks for your support!

---

### Post by markbuntu on 2008-07-28
Did you try the other adjustments in that thread I listed above? 
They really make a difference.

I have no problems with video tearing, only a little flickering in windowed playback when compiz is on and Textured Video is on with my HD3650. xine does not play so nice with this driver but vlc and miro and mplayer are fine.

Envy will only give you the 8.5 driver. The 8.6 and 8.7 drivers are far superior. If you want to get the 8.7 driver, folow the directions here, use Method 2 and follow it very carefully:

[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

Release notes for 8.7

[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_87_linux.html](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_87_linux.html)

Release Notes for 8.6

[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_86_linux.html](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_86_linux.html)

Release notes for 8.5

[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_85_linux.html](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_85_linux.html)

---

### Post by nv22nv on 2009-04-24
I'm sorry for not answering any earlier. Although it may not really help others who are reading this topic with the same problem I had, I'll bring this to a conclusion now.

I tried everything I could, but without success. I didn't lose too much time and sent back the video card as long as I could and excanged it for one from nvidia. With the nvidia driver, I don't have these problems anymore with any video player except for flash video embedded into websites. Therefore, I prefer to download streams instead and play them in my local video player (which is more convenient anyway, IMO).

A late "thank you" to everyone for their help.

---

