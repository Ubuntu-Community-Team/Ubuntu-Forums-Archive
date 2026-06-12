---
title: "Gutsy: ATi X1250 on board TV Out not working"
date: 2007-11-11
forum: Multimedia &amp; Video
---

### Post by MrHyde on 2007-11-11
Hi,

I have just recently installed Ubuntu Gutsy on a new AMD64 machine and then installed MythTV.  I would now like to output the video through the TV-Out onto my old TV.  It only has Composite input, so I need to use the Composite out connection that is provided.

However, I have not been able to get this to work.  I have followed the instructions to install the ATi restricted drivers, but can't get it to work.

Below are the output of some of the files and commands I have run to try to get this to work.

lspci to confirm my chipset
[PHP]
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon X1200 Series
[/PHP]

lsmod does not show fglrx as being loaded

output of fglrxinfo
[PHP]
Xlib:  extension "XFree86-DRI" missing on display "localhost:10.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)
[/PHP]

When trying to load it manually, I get:
[PHP]
sudo modprobe fglrx
Not loading fglrx module; not used in /etc/X11/xorg.conf
[/PHP]

When I ran sudo aticonfig --initial during installation, it outputted lots of lines and then at the end it said Aborted.  It also had the side result that I no longer had an xorg.conf as it had renamed it to xorg.conf.Original-0

I have added the following lines to /etc/X11/xorg.conf
[PHP]
Section "Module"
        Load "vnc"
        Load "dri"
EndSection

Section "Extensions"
        Option  "Composite"     "0"
EndSection
[/PHP]

Not sure about disabling Composite as that is what I want to use to input into my TV.

Looking at the Xorg logs, I see this line.  Not sure if it is related.
[PHP]
(EE) AIGLX: Screen 0 is not DRI capable
[/PHP]

Any suggestions on what I should look at next to proceed further.

Regards,
Vivek

---

### Post by birdySi on 2007-11-21
I have exactly the same problem. Is there someone who could help us find a solution.

---

### Post by birdySi on 2007-11-28
I have found really good instructions how to install ati driver and enable TvOut. You can find it at [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

This guide is fo Ubuntu Gutsy, but provides many other guides for different distros.

---

### Post by subspawn on 2008-02-21
Although DRI & GL acceleration worked out of the box with fglrx (on mythbuntu), 
I get the following when starting Xorg with a TV attached:

> 
(WW) fglrx(0): More than one displays are connected,so clone mode is enabled
(WW) fglrx(0): DALEnableDriverInstance on secondary failed: 9
(EE) fglrx(0): PreInitDAL failed
(EE) fglrx(0): PreInit failed


Poses a big problem on a mythbox :(

---

