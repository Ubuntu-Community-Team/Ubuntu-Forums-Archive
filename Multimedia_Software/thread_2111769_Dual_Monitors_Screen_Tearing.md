---
title: "Dual Monitors Screen Tearing?"
date: 2013-02-02
forum: Multimedia Software
---

### Post by croash on 2013-02-02
I am running Ubuntu 12.04 LTS (64-bit) and an EVGA GTX 560 gpu. I have had this issue on Linux Mint Cinnamon, Gnome-Classic Shell, and Ubuntu Unity. Basically, whenever I try to watch a video or play a game I get horrible screen tearing. My monitors are 1024x768 and 1680x1050 with a ~75 and ~60 refresh rate, respectively. 

I have tried enabling sync to vblank in compiz and nvidia settings and setting my refresh rate to 60 and 75 in compiz settings. I have also tried experimenting with which monitor to sync to in the nvidia settings and nothing has worked. I have been trying to find the solution to this on various forums and websites for weeks now.

Has anyone else had a similar issue and managed to fix it? This issue is keeping me on windows because it makes Ubuntu completely unusable to me. :(

Edit: I forgot to mention that I am using the proprietary 313 driver. I have tried using the Nouveau one but it is really slow, won't recognize my second monitor, and has a really low resolution.

---

### Post by BicyclerBoy on 2013-02-02
Tearing in video playback is most likely composite effects redirection.
Unity (compiz) is particularly troubled by nVidia twinview meta-modes.
(you are not using twinview if you have 2 diff refresh rates)

Have you tried (in unity & old gnome)
"ccsm"
& set un-redirect full screen.
Sometimes the refresh rate auto detect works, it can only sync to one monitor..It would be better to run both monitors at same rate.

This setting also allows VDPAU to use overlay instead of blitter.

---

### Post by croash on 2013-02-03
> **BicyclerBoy said:**
> Tearing in video playback is most likely composite effects redirection.
Unity (compiz) is particularly troubled by nVidia twinview meta-modes.
(you are not using twinview if you have 2 diff refresh rates)

Have you tried (in unity & old gnome)
"ccsm"
& set un-redirect full screen.
Sometimes the refresh rate auto detect works, it can only sync to one monitor..It would be better to run both monitors at same rate.

This setting also allows VDPAU to use overlay instead of blitter.


Unredirect Fullscreen Windows was already enabled. How can I set the refresh rate to be the same on both monitors?

---

### Post by croash on 2013-02-04
:/

---

### Post by sjwblkfly on 2013-02-04
I'm having the same problem. I have a gtx 560 and i get tearing on the desktop and in videos. Both of my monitors are the exact same to. I've been searching for days for a solution. Tried every suggestion nothing seems to work. Thing is i really like Ubuntu but this screen tearing breaks it for me. Back to Windows i guess.:sad:

---

### Post by TOMBSTONEV2 on 2013-02-04
Thing is i really like Ubuntu but this screen tearing breaks it for me. Back to Windows i guess.

^^ That has to be one of the saddest things I've heard. I feel for you. This problem happens only with dual monitors? This is actually the first I have heard of this. I will keep an eye out for any help on this.

---

### Post by croash on 2013-02-10
Well, I changed both the monitors to have the same refresh rate (it was locked before in the nvidia settings and I didn't even notice it) and the issue is a lot better. On my smaller monitor there is no tearing whatsoever. On my larger one, there is now one line of tearing rather than 3-5. Anyone else have any ideas?

---

### Post by BicyclerBoy on 2013-02-10
Try to find the exact real refresh rate (from the monitor's builtin OSD).

Check this refresh rate is exactly same as in compiz settings.
Some people with fast GPUs can use double real refresh rate.

Note that nVidia twinview creates metamodes with fake refresh rates in an attempt to make unique mode names.
Note that (historically) number_monitors >=2 causes nVidia driver leave GPU at max performance level.

---

### Post by croash on 2013-02-10
> **BicyclerBoy said:**
> Try to find the exact real refresh rate (from the monitor's builtin OSD).

Check this refresh rate is exactly same as in compiz settings.
Some people with fast GPUs can use double real refresh rate.

Note that nVidia twinview creates metamodes with fake refresh rates in an attempt to make unique mode names.
Note that (historically) number_monitors >=2 causes nVidia driver leave GPU at max performance level.

Which of the monitors should I find the exact real refresh rate on?

---

### Post by BicyclerBoy on 2013-02-12
Check both /all ..the monitors OSD info can reveal H&V frequencies..

Twinview should be forcing the vertical freq to be the same but your report of improvement after manually setting the vert rate suggests that fact is incorrect...

The nVidia-settings reported refreshrate may be fake but version 310 & later driver was meant to have corrected this behaviour (according to the release notes).

You can read thru /var/log/Xorg.0.log to find the actual video modes used for each monitor..

---

### Post by croash on 2013-02-16
> **BicyclerBoy said:**
> Check both /all ..the monitors OSD info can reveal H&V frequencies..

Twinview should be forcing the vertical freq to be the same but your report of improvement after manually setting the vert rate suggests that fact is incorrect...

The nVidia-settings reported refreshrate may be fake but version 310 & later driver was meant to have corrected this behaviour (according to the release notes).

You can read thru /var/log/Xorg.0.log to find the actual video modes used for each monitor..

I'm using the 313.18 beta drivers.

---

### Post by croash on 2013-02-20
Anyone found a fix yet?

---

### Post by webgoddess on 2013-05-06
I have this same issue with nVidia GTX 660 using triple monitor set up (2x 4:3 1280x1024 DVI monitors, 1x 16:9 1920x1080 HDMI monitor) with nVidia proprietary 313.30 driver on Xubuntu 13.04.

I don't really notice any tearing on the desktop with or without compositing, but when i try to watch video on VLC I do get noticeable tearing.  It really sucks to have to either live with the tearing or reboot into windows 7, which doesn't have any tearing problems.  

I just noticed that I only have x.org 1.12.4, so I'm thinking of trying to upgrade to 1.13 and the nVidia 319 drivers to see if that helps.  I think I might have downgraded to 1.12 when I was using an ATI card before I upgraded, because it was having issues with the multi-monitor support.

What's weird is when I first got this video card I didn't have any trouble with tearing, but something was broken where the direct rendering was disabled and it was using openGL 1.4 instead of 4.3.  This caused one of the video games I wanted to play to not work, so I did some sort of fix to get 4.3 working, and I believe that the fix somehow caused the video tearing.

I'm running all the monitors at 60Hz even though the 4:3 ones work at 75Hz as well.  For some reason the nVidia settings say that the 4:3 monitors are running at 60.02, so i'm wondering if that .02 is somehow causing the tearing.

---

### Post by Octagonal on 2013-05-08
I have 2 monitors.  I've noticed the tearing that you're describing.
I'm using nvidia driver version 310.44 (313 causes issues w/ my browsers for some reason and I wasn't able to get 319 working at all--though I didn't give it much effort)

At any rate... I've noticed that after ensuring that the sync to vblank in the nvidia-settings -> opengl settings is checked, I only see tearing on one of my monitors.  
The first monitor is listed as 0 and the second is listed as 1.  I only see tearing on '1'.  I've seen some solutions to video tearing but all seem to involve Compiz or just don't work...

I should also mention the tearing is only noticeable when watching movies on monitor '1'.  I've used vlc, mplayer, smlayer and tried setting different video output drivers for each (gl, gl2, xv, vdpau etc. all w/ the same tearing problem)

Anyone have any ideas?

Using Xubuntu 13.04

---

### Post by Octagonal on 2013-05-08
I guess I didn't google hard enough.
Adding the lines below to my xorg.conf resolved it for me...

Section "Extensions"
    Option "Composite" "Disable"
EndSection

---

