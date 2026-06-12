---
title: "ATI + opensource drivers problem"
date: 2011-02-09
forum: Multimedia Software
---

### Post by zamolxis on 2011-02-09
I installed Kubuntu 10.10 on a Shuttle computer with AMD64 3200+, 2GB RAM, ATI AIW 9600XT video. It's not bad, except that it seems impossible to setup dual monitors using the opensource (default) drivers with an old, regular CRT monitor on VGA1 and a landscape LCD on VGA2.

At first, I was able to get it to work (after numerous freezes) by going into Settings then adjusting in Size & Orientation for Monitor 2 "Position" from "Clone" to "Above". That worked, except that adjusting also the size to 1350 x 768 caused the image to have a discoloration band somewhere close to middle. The settings were not save and on each reboot I would have to do it again. The results varied from freezes, to "monitor 2 disconnected" but at one point everything worked perfectly - too bad it did not last.

This being a multiboot machine that works just the way I want it to I don't have the luxury of installing / uninstalling the OS. In a [previous thread]("http://ubuntuforums.org/showpost.php?p=10413423&postcount=26"), Krytarik suggested I install a [different kind of Open Source drivers]("http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Installing_Open_Source_Edge_Drivers"), and then [play with xorg.conf]("https://wiki.archlinux.org/index.php/Xorg#Multiple_monitors.2FDual_screen") after first installing a [ppa]("https://launchpad.net/~xorg-edgers/+archive/ppa"):```
sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get upgrade
```

In the past, the combination of ATI drivers + play with xorg.conf rendered my system unusable. Installing proprietary drivers does not seem to be an option either as ATI dropped support for this card and the old drivers don't work with the current X servers.

The main reason why I would like to get this to work as such is that I have a projector I would like to swap every now and then for VGA2. 
Has anybody gotten a similar ATI + open source drivers setup to work?

---

### Post by inobe on 2011-02-09
the time it would take to get it working you could simply grab a cheap nvidia add on card.

does this shuttle have an agp slot?

if yes, all can be fixed rite now.

any one of these would outperform your current ati card in it's infancy.

[http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=100007709%20600007850%20600030348&IsNodeId=1&name=NVIDIA](http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=100007709%20600007850%20600030348&IsNodeId=1&name=NVIDIA)

the only other way is to edit or xorg.conf [http://www.x.org/archive/X11R6.8.1/doc/xorg.conf.5.html](http://www.x.org/archive/X11R6.8.1/doc/xorg.conf.5.html)

that would require you know everything xorg.conf and your monitors, how to backup and restore xorg.conf so you can start fresh after every mistake quickly.

if you provide enough information including your current xorg.conf file maybe someone will take the time to write one for you.

---

### Post by Krytarik on 2011-02-09
What a coincidence! As a matter of fact my mum has exactly the same setup like you, also an ATI 9600XT, with an 17'' CRT and a new 24'' LCD (TV).

And I got those working, even with desktop effects, using the mentioned OSED and a similar xorg.conf like the example in the guide I posted. Although you could also use the default open source driver, the OSED should provide a better performance.

See this earlier thread on how to get the correct values for your xorg.conf:
[http://ubuntuforums.org/showthread.php?t=1675670](http://ubuntuforums.org/showthread.php?t=1675670)

---

### Post by zamolxis on 2011-02-09
@Krytarik: would you be able to post a copy of that xorg.conf?
@inobe: it seems that xorg.conf went the way of the dodo (or menu.lst in Grub2), segmented into multiple files that I don't know how to manage:
```
$ locate xorg.conf
/usr/share/X11/xorg.conf.d
/usr/share/X11/xorg.conf.d/10-evdev.conf
/usr/share/X11/xorg.conf.d/50-synaptics.conf
/usr/share/X11/xorg.conf.d/50-vmmouse.conf
/usr/share/X11/xorg.conf.d/50-wacom.conf
/usr/share/X11/xorg.conf.d/51-synaptics-quirks.conf
/usr/share/X11/xorg.conf.d/60-magictrackpad.conf
/usr/share/doc/xserver-xorg-video-nouveau/examples/xorg.conf
/usr/share/man/man5/xorg.conf.5.gz
```
I did not have much luck before with xorg.conf, now I can't even find it..

---

### Post by Krytarik on 2011-02-09
Sh*t, I was afraid you would ask that.;-) I'd really love to be able to provide it, but I have it not here, I will try to get my mom tomorrow in order to "aquire" it per remote access.

Nowadays there is no xorg.conf by default, but you can place one as usual in /etc/X11 and it will be processed as usual.

---

### Post by zamolxis on 2011-02-09
That would be great!
I'll be waiting for it.. :)

---

### Post by Krytarik on 2011-02-09
In the meantime try to get the correct specs of your monitors and the modelines you want to use, following my posts in the mentioned thread.

---

### Post by zamolxis on 2011-02-09
will do!

---

### Post by inobe on 2011-02-09
i knew it would turn out good.

---

### Post by Krytarik on 2011-02-10
Here it is:
```
Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" 1152 0
EndSection

Section "Monitor"
    #DisplaySize      310   230    # mm
    Identifier   "Monitor0"
    VendorName   "SAM"
    ModelName    "SyncMaster"
    Modeline     "1152x864_85.00"  119.75  1152 1232 1352 1552  864 867 871 910 -hsync +vsync
    Option       "PreferredMode" "1152x864_85.00"
    HorizSync    30.0 - 85.0
    VertRefresh  50.0 - 160.0
    Option         "DPMS"
EndSection

Section "Monitor"
    #DisplaySize      310   230    # mm
    Identifier   "Monitor1"
    VendorName   "LG"
    ModelName    "LG M2380D"
    Modeline     "1280x720_60.00"   74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync
    Modeline     "1920x1080_50.00"  141.50  1920 2032 2232 2544  1080 1083 1088 1114 -hsync +vsync
    Option       "PreferredMode" "1920x1080_50.00"
    HorizSync    30.0 - 83.0
    VertRefresh  56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier  "Card0"
    Driver      "radeon"
    VendorName  "ATI Technologies Inc"
    BoardName   "RV350 AR [Radeon 9600]"
    BusID       "PCI:1:0:0"
    Screen      0
EndSection

Section "Device"
    Identifier  "Card1"
    Driver      "radeon"
    VendorName  "ATI Technologies Inc"
    BoardName   "RV350 AR [Radeon 9600]"
    BusID       "PCI:1:0:0"
    Screen      1
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
    DefaultDepth    24
    SubSection "Display"
        Depth     24
        Modes   "1152x864" "1024x768"
    EndSubSection
EndSection

Section "Screen"
    Identifier "Screen1"
    Device     "Card1"
    Monitor    "Monitor1"
    DefaultDepth    24
    SubSection "Display"
        Depth     24
        Modes   "1920x1080" "1280x720"
    EndSubSection
EndSection
```

---

### Post by zamolxis on 2011-02-15
I'm having a problem with the big fan at the back of the computer - it stopped spinning & massive overheat. I'll have to look into it and see if I can get it working, because it's also connected to the CPU via a heat pipe, so I cannot do a simple replace.

Thank you for providing the Xorg but I cannot do anything until I fix the fan; it starts, works for a minute, then shuts off b/c of overheating.

I'll report back when I get it to work but that will be in a while, as I'm swamped in work.

---

### Post by Krytarik on 2011-02-16
Poor you! I understand, and thanks for the info!

---

