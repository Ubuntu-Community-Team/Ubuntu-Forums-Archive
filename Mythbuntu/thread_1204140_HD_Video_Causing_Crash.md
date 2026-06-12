---
title: "HD Video Causing Crash"
date: 2009-07-04
forum: Mythbuntu
---

### Post by Macus on 2009-07-04
Hi all, 

Iv got a very odd issue with my mythbuntu box
when ever I attempt to watch HD tv it immediately crashes to the login screen.
it does the same if I play a recorded HD tv show

background:
I have this Compaq evo which i installed mythbuntu on and got both my tuner cards working
however 1.6ghz isn't quite enough to run all the things I want, so i built a new computer

the new comp:
CPU: Intel celeron dual core 2.0ghz
motherboard: Gigabyte GA-EG41M-S2H
graphics (onbord): intel G41 graphics chipset

the Evo can play HDTV fine (a bit laggy but it can do it) but if I pull the HDD out and put it in the new comp it still crashes on HDTV

and heres whare it gets stranger,
if I exit myth and open a random video file (dosnt have to be HD) and play it
it will play just fine in vlc, but if I drag another window so much as one pixel over the video window, it crahses to the login box

Im no linux pro (most of my knolage is windows xp) but id say its somthing to do with the video driver

Thanks in advance.

---

### Post by klc5555 on 2009-07-04
> **Macus said:**
> Hi all, 

Iv got a very odd issue with my mythbuntu box
when ever I attempt to watch HD tv it immediately crashes to the login screen.
it does the same if I play a recorded HD tv show

background:
I have this Compaq evo which i installed mythbuntu on and got both my tuner cards working
however 1.6ghz isn't quite enough to run all the things I want, so i built a new computer

the new comp:
CPU: Intel celeron dual core 2.0ghz
motherboard: Gigabyte GA-EG41M-S2H
graphics (onbord): intel G41 graphics chipset

the Evo can play HDTV fine (a bit laggy but it can do it) but if I pull the HDD out and put it in the new comp it still crashes on HDTV

and heres whare it gets stranger,
if I exit myth and open a random video file (dosnt have to be HD) and play it
it will play just fine in vlc, but if I drag another window so much as one pixel over the video window, it crahses to the login box

Im no linux pro (most of my knolage is windows xp) but id say its somthing to do with the video driver

Thanks in advance.

First and logical guess is that the onboard graphics chip on the new machine simply can't handle the HD content. You're going to need a high-octane video card for that, preferably a reasonably current NVidia GeForce card since their proprietary driver support is by far the best.

---

### Post by Macus on 2009-07-04
thanks for the reply

but I think it can do HD it seems a little stupid to have a motherboard with DVI and HDMI on it and not be able to play HD content

I can play counter strike source (in windows) on it without issues

Edit: More info:

I put a PCI graphics card in (puled it out of my server) 
its a Radeon RV100 QY [Radeon 7000/VE]
(according to lshw)

the vlc overlap thing was immediately fixed, but when myth boots I get the same error as described in [http://ubuntuforums.org/showthread.php?t=1094371](http://ubuntuforums.org/showthread.php?t=1094371)

the tread says to launch myth with the command:

XLIB_SKIP_ARGB_VISUALS="1" mythfrontend
this fixes the issue but is more a work around than a solution, and iv paid for a motherboard that has HDMI so id like to use it

I found the drivers for the Intel at [http://lists.freedesktop.org/archives/xorg/2009-April/045117.html](http://lists.freedesktop.org/archives/xorg/2009-April/045117.html)
but i have no clue how to install them

---

### Post by klc5555 on 2009-07-05
> **Macus said:**
> thanks for the reply

but I think it can do HD it seems a little stupid to have a motherboard with DVI and HDMI on it and not be able to play HD content

I can play counter strike source (in windows) on it without issues

Edit: More info:

I put a PCI graphics card in (puled it out of my server) 
its a Radeon RV100 QY [Radeon 7000/VE]
(according to lshw)

the vlc overlap thing was immediately fixed, but when myth boots I get the same error as described in [http://ubuntuforums.org/showthread.php?t=1094371](http://ubuntuforums.org/showthread.php?t=1094371)

the tread says to launch myth with the command:

XLIB_SKIP_ARGB_VISUALS="1" mythfrontend
this fixes the issue but is more a work around than a solution, and iv paid for a motherboard that has HDMI so id like to use it

I found the drivers for the Intel at [http://lists.freedesktop.org/archives/xorg/2009-April/045117.html](http://lists.freedesktop.org/archives/xorg/2009-April/045117.html)
but i have no clue how to install them

Don't waste your time.

In order to do HDTV, both for NVidia or ATI, you generally need to use the company's much faster proprietary Linux drivers, not the open-source ones. No such proprietary drivers exist for Intel, so far as I'm aware, and, according to the Mythbuntu 8.10 installation manual (almost unchanged for 9.04), ATI does not support cards earlier than Radeon 8500 on Linux. Further, Mythbuntu docs specifically state that the default Mythbuntu open-source driver installed at system installation is the best available choice for a Radeon 7000: [https://help.ubuntu.com/community/RestrictedDrivers/ATI](https://help.ubuntu.com/community/RestrictedDrivers/ATI)


Unfortunately, the issue is not what you can do with the machine in Windows; rather it's what components are supported and to what extent under Linux and Mythtv that will determine whether you get HD out of Mythtv on the machine or not. I'm not aware of adequate driver support existing for the Intel onboard chipset; I'm pretty sure it doesn't exist for a Radeon 7000. Your best option (and I welcome someone correcting me if I happen to be wrong) will be to pitch the old ATI card and invest in a recent NVidia GeForce 8xxx or above, one chosen from the matrix where VDPAU is supported with the proprietary drivers in Mythtv here: [http://www.mythtv.org/wiki/Vdpau#Supported_Cards](http://www.mythtv.org/wiki/Vdpau#Supported_Cards) 

Cheers! :)

---

### Post by ian dobson on 2009-07-05
Hi,

There are no proprietary drivers for intel graphic cards as intel releases the source code for them. So what you usually mean with proprietary (manufacturer) drivers are the open source drivers.

Regards
Ian Dobson

---

### Post by klc5555 on 2009-07-05
> **ian dobson said:**
> Hi,

There are no proprietary drivers for intel graphic cards as intel releases the source code for them. So what you usually mean with proprietary (manufacturer) drivers are the open source drivers.

Regards
Ian Dobson

Ah! I didn't know that.

Well, that's good in that Ubuntu likely incorporates the best Linux driver available for this chipset. But it's bad in that the current state of the driver does not appear to be able to handle HD content, in the original poster's experience with it.

---

### Post by Macus on 2009-07-05
Thank you all for the replys

I have managed to fix the crash issues by dooing a:
sudo apt-get install xserver-xorg-video-intel

so it no longer crashes when playing HD or overlapping video windows

but i took the comp up to the TV I plan to use it with (40" LCD, about 1300x720)
and now the standard definition is choppy/laggy

Im sure its something driver related or myth itself because I booted into windows 
installed the PVR software from leadtek, and plugged it up to my 1680x1050 screen
and it plays HDTV with ease

---

### Post by rtrevor on 2009-07-06
You may find that following the "safe" configuration from the following thread improves your video performance if you're using the intel driver. It worked for me:

[http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)

---

### Post by Macus on 2009-07-07
Hey WOW,

that fix it, thanks

however I got the HDMI cable to got th the LDC, oh and I looks up its specs, its 1920x1080
I got the HDMI because the VGA is limited to 1360x768

but when I connect the HDMI, it cuts off the edges of the screen, I believe this is call overscan

Il investigate this today

Thank you all for the helpful replys

---

