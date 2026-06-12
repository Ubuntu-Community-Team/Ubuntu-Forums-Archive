---
title: "ATI mobility Radeon 7500 drivers"
date: 2009-02-26
forum: Multimedia Software
---

### Post by RyanHall85 on 2009-02-26
I have the ATI mobility radeon drivers that Ubuntu installed originally with 8.1o, and it works fine for typical use, such as web browsing, but when I play videos especially using S-video, it looks kinda crappy. I get colors, but it looks choppy, the screen size isn't right, etc. Can someone tell me how to find the right drivers for this so I can go back to watching divx stuff on my TV via S-video as I did in Windows XP? I un-installed Windows because I wanted to get away from it, and started to fall in love with Ubuntu. So far the only thing I miss is my easy to install Omega drivers, and excellent video performance.

---

### Post by smani on 2009-02-26
Are you using compiz (desktop effects)? It would not be the first ATI card that had serious problems with compositing enabled...

---

### Post by RyanHall85 on 2009-02-27
no I turned that off after I realized the effects it was having on my video performance.

---

### Post by Mark Nielsen on 2009-02-27
HI, I've got the same video card in my Compaq EVO 800c laptop and everything works fine until I plug in my external monitor; not so good after that LOL.  I'm pretty sure the drivers the issue and I wanted to find out if you've found any solution?  Strangly enough, I started having the issue after the last set of Unbuntu patches, so I think I may have done this to myself (normaly the case).
Thanks,
Mark

---

### Post by chinamusic on 2009-02-27
Had the same problem with my Radeon Mobility 1600.  Disabled compiz and it got much better.  I still get occasional "tearing" when playing back mpeg2/4 video.  It seemed to work fine after a fresh install so I'm assuming that some "update" stepped on the video driver or altered some setting that's hosing video playback.  :(

This is on an Asus W3J laptop with 2ghz coreduo, 2gb RAM, ATI Radeon Mobility 1600, 100gb 7200rpm disk, etc.  That should be well in excess of the requirements to play smooth mpeg video.

Sigh....

---

### Post by emeraldgirl08 on 2009-04-23
I'm new here and to Ubuntu. I have the Radeon 7500 card in my Laptop. I am loving Ubuntu so far but the performance of my card stinks. Is there some kind of path I'm supposed to take to take full advantage of my card?

I have my HD dual-booted with XP pro and Ibex. The performance is great in XP so I want the same for my Ibex. Anyone have any success stories with this???

I did find a thread that people seemed to like that enabled the 3d acceleration etc. If I could only find it but I'm gettin' sleepy. If anyone has any advice I'd appreciate it.

---

### Post by killabee44 on 2009-06-06
I just installed kubuntu in someone's Thinkpad T42 and am trying to get better drivers so we can run warcraft 3 on it. 

It has a Mobility ATI Radeon 7500 video card inside. If anyone has any luck, please post. Thanks.

---

### Post by deadmonkey01 on 2009-06-17
bump!

I am also having issues!  I have been searching around and don't seem to have a straight answer.  Most of what I see is threads on performance upgrades.  I think I have a completely different problem.  I have an IBM Thinkpad T40 with Mobility Radeon 7500 (M7 chip)

I have tried to install the Xorg drivers, but when I do this, at bootup, the screen flashes with half of the screen showing my desktop background.  The other 1/2 is garbled... like somebody dropped the screen or something.  It flashes again, with less of the picture visible, then a 3rd time with nothing but scrunched, garbled lines at the bottom.  I can include pictures if needed.

I have been looking and the settings are supposed to be in the  xorg.conf file from what I gather.  I don't think I even have anything in there.  I don't have xorg installed right now because if I do, I have no more Ubuntu.  So I reinstalled (for the 3rd time now) so I can have the generic install back and at least have functionality.

I noticed that the graphics for minimizing have been impeded a bunch.  It is a simple task the the computer should be able to handle, but fails miserably.

I also have issues playing DVD's, it does play, but very poorly, if at all.  I can barely get usable frame rates out of stuff like youtube videos for example.  It looks more like a web cam then video.

I Installed Wine and have Warcraft III up and running, it works but the options menu has an animated background that barely is animated... maybe 1 frame/second at best.

Something is very wrong here.
======

I am new to ubuntu, but I had this same laptop working fine with XP and working farely well in PClinux... at least with Beryl I had no issues with the graphics.... or at least not this bad.

Here is what my xorg.conf file looks like regardless of before or after install/crash

> 
Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

Thanks in advanced.  I' really like to leave XP behind.  But it is stuff like this that keeps me going with linux based aps  Please help me leave my XP in its package... I really don't wanna re-install it again.

---

