---
title: "Help!  Soooo close!  8400GS/S-Video out"
date: 2010-08-03
forum: Multimedia Software
---

### Post by Ubun00btu on 2010-08-03
I've searched the forums and have got things working except my Ubuntu 10.04 32 bit now locks up on load.  I get the load screen with the 4 dots, but nothing's happening, no dots are changing colors.

I have been trying to build a PC to watch TV shows on a plain old CRT TV with S-Video input.  I got Ubuntu installed and running no problem using a standard LCD monitor, it would install just fine while using S-video, but as soon as the OS loaded it would shut off the S-video and use the DVI output.

So I added this to my xorg.conf:

Section "Device"
        Option          "TVStandard" "NTSC-M"  
        Option          "MetaModes" "1024x768" 
        Option          "UseDisplayDevice" "TV-0"  Display
        Option          "TVOutFormat" "S-video" 
EndSection

Now it starts out using the TV just fine, except that it locks up.

I'm using a cheap Galaxy 8400GS card, I installed the restricted drivers during installation while using the LCD, rebooted, made the change to Xorg, rebooted and here I am.  Other than that, the Xorg.conf is completely un-messed with.

I've been working on getting this system together for days now and would really like to get it working.  Please help!  Thanks!!!

---

### Post by Ubun00btu on 2010-08-03
BTW it works fine in booting system restore > safe graphics mode.

---

### Post by endotherm on 2010-08-03
in the TVOutputFormat, I believe it should be all uppercase, without the dash, so try it like this:

```
Option        "TVOutputFormat" "SVIDEO"
```

ultimately though, this may not do it. the 8300-8600 cards have a history of minor incompatibilities with the linux drivers (both the restricted version, and the proprietary from nvidia themselves). it wasn't until lucid for instance that my 8400 and 8500 cards gained overscan/underscan control. I was always able to get svideo to work, so there may be hope yet, but I found that in the end, replacing the card was my best bet. 

[FONT=Arial, Helvetica, sans-serif][SIZE=2]
[/SIZE][/FONT]

---

### Post by Ubun00btu on 2010-08-04
Unfortunately that did not work.

---

### Post by endotherm on 2010-08-04
> **Ubun00btu said:**
> Unfortunately that did not work.
is that your entire device section? there are some key elements missing like the driver, the busID etc. can you post your entire xorg? It's been a few years since i had to muck with one, but we can look it over.

is there any particular reason you are not using nvidia-settings for configuring the vidcard? if you do, besure to launch it with gksu when setting outputs and resolution.

in the long run, lockups are not likely an xorg.conf setting, but an issue with the driver, the kernel or with your specific hardware. 
how bad does it lock? when it locks, does the mouse still move? can you alt+tab to another open application? if not, hold Alt + Prntscrn (keep holding them) and SLOWLY enter
```
r e i s u b
```. when you get to 's' your hard drive access light may come on. don't enter 'u' until it goes off. this is the best procedure for safely shutting down a box when you can;t tell it to shutdown gracefully. it will tell us how "locked" the system really is (a locked system or a locked application).

---

### Post by Ubun00btu on 2010-08-14
Yes to the device section.

Nvidia settings cannot be set in recovery mode.  Nvidia settings not in recovery mode does not recognize the S-Video monitor as it defaults to VGA/DVI.

Will try your suggestion and post the results.

---

