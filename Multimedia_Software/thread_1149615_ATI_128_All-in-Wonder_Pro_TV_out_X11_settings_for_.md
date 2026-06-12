---
title: "ATI 128 All-in-Wonder Pro TV out X11 settings for Jaunty"
date: 2009-05-05
forum: Multimedia Software
---

### Post by schruthensis on 2009-05-05
Hello,

I'm posting to help others out with their old ATI TV out capable cards.  

Some time ago I posted my X11 settings 
[http://ubuntuforums.org/showthread.php?p=3535099](http://ubuntuforums.org/showthread.php?p=3535099)
that worked with Gutsy and continued to work (in "low graphics mode") with Intrepid.

This last weekend, however, I upgraded to Jaunty (9.04) and my screen started freezing during boot up... right when the login screen is supposed to appear I instead got a blurred version of the Ubuntu logo with no response from the keyboard our mouse.


I followed steps 1 & 2 here:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/285603](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/285603)

```

sudo apt-get remove --purge fglrx*
sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon  

```

...and loaded a variant of the X11 settings from the post linked above... (with a change from 'Driver "ATI Rage 128"' to 'Driver "vesa"')
to get things to work again.  

```

Section "Device"
 Identifier "Card0"
 Driver "vesa"       
 Option "AGP" "1"
 Option "ConnectedMonitor" "TV"
 Option "TVStandard" "NTSC-M"
EndSection
 
Section "Monitor"
 Identifier "Monitor0"
 HorizSync 30.0 - 50.0
 VertRefresh 60 
EndSection 
 
Section "Screen"
 Identifier "Screen0"
 Device "Card0"
 Monitor "Monitor0"
 DefaultDepth 24
 SubSection "Display"
  Depth 24
  Modes "800x600"
 EndSubSection
EndSection

```
Now things run better than before!  No prompts about low graphics mode or anything!

---

### Post by ugm6hr on 2009-05-24
Thanks for the post.  Got my X1200 card working after me trying for about 12 hours!

[http://ubuntuforums.org/showthread.php?t=1168176](http://ubuntuforums.org/showthread.php?t=1168176)

---

