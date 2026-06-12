---
title: "FGLRX - ati x1650 - am I wasting my time?"
date: 2007-05-18
forum: Multimedia &amp; Video
---

### Post by glenndavy on 2007-05-18
Hi 
Just wanting to know if should stop trying to get this card working correctly.ith

I'm using 7.04 wth 2.6.20-15-lowlatency kernel

Here's what I can do... 
Get the x1650 working on a benq fp731 17" lcd monitor in its native resolution (1280x1024 IRC) with fglrx - I can do this using either the standard restricted drivers, or download and instlal the latest, or even using tselliots evny2 - all with no problem.

Here's what I cant do:
I cannot get the same card working with an AcerAL2016W 1680x1050 monitor.
Using the fglrx driver, installed by anymeans, not talking bigscreen, xinerama, or dual head - just single screen. As soon as X is run, the screen comes up black with a no signal OSD message. X doesnt crash - its running somewhere in the background, just not on this screen. This is at any resolution.
Apart from the standard watcom errors, the only erros in  /var/log/Xorg.0.log are that AIGLX has an issue and that  we're reverting to software rendering.

I can get the screen working with the VESA driver, but it doesnt support 1680x1050, so I cant get goiing for all useful purposes.

The ati / radeon open source drivers dont work with this generation card

I havent looked into fbdev yet, but IRC isnt cabable of acceleration, so havent bothered.

Without asking 'how' (yet) - I just want to at least know if its possible to use this monitor (preferably with fglrx, but any driver at this point) on this card with 7.04/2.6.20-15-lowlatency - and if not - what do i need to do to use this hardware?


thanks
Glenn

---

### Post by Herman on 2007-05-18
Hello glenndavy, 
I just brought home a nice new Acer AL2016W LCD monitor and I love it!

I too had a little trouble getting it set up at first though. I have an ATI Radeon 9200 (RV280) video card. As soon as I plugged in my new 20" monitor to replace my Acer 17" AC713 CRT monitor and booted, it worked, but not at the resolution I wanted.
So I ran [sudo dpkg-reconfigure xserver-xorg]("http://users.bigpond.net.au/hermanzone/p7.html") hoping that would improve things. It didn't. The opposite happened, I got "input out of range" or something like that.
 I re-ran sudo dpkg-reconfigure xserver-xorg several times trying to find out what I was doing wrong. The problem I had was I was unable to change the default suggested resolutions at all. I could not find a key or key combination on my keyboard that has any effect on the little 
[*] marks to select or deselect the resolutions.

I gave up running sudo dpkg-reconfigure xserver-xorg, and booted up my Feisty Fawn LiveCD. I mounted my hard disk installed Ubuntu filesystem and opened my /etc/X11/xorg.conf file and edited it with the resolutions I wanted. 
See the details in my other post in the following linked thread,                                                                                                              [LCD Monitor Out Of Range Problem]("http://ubuntuforums.org/showthread.php?t=447483").
That should get your AL2016W monitor working for you! I love mine, I have lots of room in my screen now, it's like having two monitors in one, only better! I can have two windows side by side now and see all of them both and copy and paste from one to the other. I'm extremely happy with mine, I hope you can do that same.
I'm just using the standard default Ubuntu ATI drivers, they are all I need. I had no problems with 1920x1200 resolution, except some print is too just a little too small to read at that res, so I changed it back to 1680X1050.

Regards, Herman :)

---

### Post by glenndavy on 2007-05-18
hey there hermen - thanks for the link - lot of interesting links come off of it - been trying different things but to no avail however.. 
couple of questions for you...
 - did you end up using the fglrx driver?
-  what did you use as a modeline for the monitor, esp at 1680x1050 and 1900x1200?

I cant help wondering if its something else entirely - something in the card/driver combination  - the only reason is that while you got an 'out of range' type error, I get a  'no signal' error - its like the card just turns off the monitor port , but keeps running the xserver

thanks
Glenn

---

### Post by Herman on 2007-05-18
G'day glenndavy,
>   - did you end up using the fglrx driver? I have tried out the fglrx driver a while ago (with my old monitor), by following the instructions in this link: [B][Ubuntu ATI proprietary display driver installation]("http://wiki.serios.net/wiki/Ubuntu_ATI_proprietary_display_driver_installation")
[/B]I guess for what I use my computer for it isn't really needed, unless I did something wrong. I didn't notice a lot of difference. Ubuntu's default ati driver works well enough for me. I could try the grlfx one again now with the new monitor and see what happens. I'll ask my wife to help me and see if she can tell the difference. I'm a bit color blind anyway, maybe that's why I can't tell. I'm happy enough with the 'ati' driver.
>  -  what did you use as a modeline for the monitor, esp at 1680x1050 and 1900x1200? What's a 'modeline'? Sorry for my lack of knowledge in this department. Maybe it's your turn to teach me some things.  Here is my current xorg.conf file, maybe that will help you.
```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
    FontPath    "/usr/share/fonts/X11/misc"
    FontPath    "/usr/share/fonts/X11/cyrillic"
    FontPath    "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath    "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath    "/usr/share/fonts/X11/Type1"
    FontPath    "/usr/share/fonts/X11/100dpi"
    FontPath    "/usr/share/fonts/X11/75dpi"
    # path to defoma fonts
    FontPath    "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load    "bitmap"
    Load    "ddc"
    Load    "dri"
    Load    "extmod"
    Load    "freetype"
    Load    "glx"
    Load    "int10"
    Load    "vbe"
EndSection

Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "CoreKeyboard"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc104"
    Option        "XkbLayout"    "us"
EndSection

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
    Option        "Device"        "/dev/input/mice"
    Option        "Protocol"        "ExplorerPS/2"
    Option        "ZAxisMapping"        "4 5"
    Option        "Emulate3Buttons"    "true"
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "stylus"
    Option        "Device"    "/dev/input/wacom"
    Option        "Type"        "stylus"
    Option        "ForceDevice"    "ISDV4"        # Tablet PC ONLY
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "eraser"
    Option        "Device"    "/dev/input/wacom"
    Option        "Type"        "eraser"
    Option        "ForceDevice"    "ISDV4"        # Tablet PC ONLY
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "cursor"
    Option        "Device"    "/dev/input/wacom"
    Option        "Type"        "cursor"
    Option        "ForceDevice"    "ISDV4"        # Tablet PC ONLY
EndSection

Section "Device"
    Identifier    "ATI Technologies Inc RV280 [Radeon 9200 SE]"
    Driver        "ati"
    BusID        "PCI:1:0:0"
EndSection

Section "Monitor"
    Identifier    "AL2016W"
    Option        "DPMS"
    HorizSync    31-84
    VertRefresh    56-75
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "ATI Technologies Inc RV280 [Radeon 9200 SE]"
    Monitor        "AL2016W"
    DefaultDepth    24
    SubSection "Display"
        Depth        1
        Modes        "1920x1200" "1680x1050" "1280x800" "1152x720" "800x500"
    EndSubSection
    SubSection "Display"
        Depth        4
        Modes        "1920x1200" "1680x1050" "1280x800" "1152x720" "800x500" 
    EndSubSection
    SubSection "Display"
        Depth        8
        Modes        "1920x1200" "1680x1050" "1280x800" "1152x720" "800x500"
    EndSubSection
    SubSection "Display"
        Depth        15
        Modes        "1920x1200" "1680x1050" "1280x800" "1152x720" "800x500"
    EndSubSection
    SubSection "Display"
        Depth        16
        Modes        "1920x1200" "1680x1050" "1280x800" "1152x720" "800x500"
    EndSubSection
    SubSection "Display"
        Depth        24
        Modes        "1920x1200" "1680x1050" "1280x800" "1152x720" "800x500"
    EndSubSection
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
    Screen        "Default Screen"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice     "stylus"    "SendCoreEvents"
    InputDevice     "cursor"    "SendCoreEvents"
    InputDevice     "eraser"    "SendCoreEvents"
EndSection

Section "DRI"
    Mode    0666
EndSection
```You should be able to copy certain parts of that and paste it into your own and see if that will help. Mine's working great! 
I'll try the fglrx driver and let you know how I get along.
Regards, Herman :)

EDIT: > I cant help wondering if its something else entirely - something in the card/driver combination - the only reason is that while you got an 'out of range' type error, I get a 'no signal' error - its like the card just turns off the monitor port , but keeps running the xserver Well one of the things I did was try plugging my old monitor back in for a while to check that it would still work on that one again. Maybe you should try that too, just to prove your card is still okay. (I'm sure it will be). Your old xorg.conf file would still be there. It would be automatically backed up and renamed something like: xorg.conf.20070518161026 in case you want to restore it or just copy something from it. Maybe by comparing your old and new xorg.conf files you'll see where you might be going wrong.
I should up date that old [Xserver Page]("http://users.bigpond.net.au/hermanzone/p7.html") of mine too, it's overdue for an update. I think it's still 'Dapper' vintage. Not a lot has changed in it though. I wish I knew how to use my keyboard for adding and removing the 
[*]'s to select or deselect the resolutions. That's something that would be good to have on that web page. I'll have to look into that.

SECOND EDIT: Here's an interesting link:[ http://en.wikipedia.org/wiki/Radeon_R200]("http://en.wikipedia.org/wiki/Radeon_R200")

UPDATE: I tried switching to the fglrx driver according to the intructions in this link, **[Ubuntu ATI proprietary display driver installation]("http://wiki.serios.net/wiki/Ubuntu_ATI_proprietary_display_driver_installation")**
   and I have not been successful so far. I had to restore my backup xorg.conf file with the ati driver in it.
I'm giving it a rest for a while now, maybe try again later when I have some new ideas. :)

---

### Post by glenndavy on 2007-05-20
hey herman - just wanted to say  thanks again for all your effort
Glenn

---

### Post by Herman on 2007-05-21
Okay, sorry if that didn't fix it for you. I'm still interested in this but there are others around here who are more expert in this field than I am.
I found a few links that seem interesting, here they are,
[Envy]("http://albertomilone.com/nvidia_scripts1.html")

 [Installing ATI Drivers on Ubuntu 7.04 guide]("http://ubuntuforums.org/showthread.php?t=438008")

I'm looking forward to getting time to try that out myself sometime soon,
Maybe Envy will do the trick for you.

Regards, Herman

---

### Post by glenndavy on 2007-05-21
nah... envy doesnt do anything that  doesnt get done manually - i used it and its good but it seems at end of day it just saves you the effort of going through the process manually - my issue occurs with or with out envy, old or new drivers

---

