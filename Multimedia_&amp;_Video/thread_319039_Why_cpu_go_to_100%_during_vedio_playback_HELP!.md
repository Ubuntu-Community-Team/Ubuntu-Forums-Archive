---
title: "Why cpu go to 100% during vedio playback HELP!"
date: 2006-12-15
forum: Multimedia &amp; Video
---

### Post by rpradeep on 2006-12-15
When I try to playback a video in gxine, totem xine.. my cpu usage jumped to 100%. Why is this happen. Because of this I am not able to playback DVD's in my UB (Ubuntu Box).

Spec;
1GHz with 512MB HP Visualize.
TSST DVD ROM with or without (U)DMA
nVIDIA Quadro 64MB with nVIDIA or nv Drivers

in W*****s W**DVD playback the same movie flawlessly.

Please help me to get rid of W*****s

---

### Post by tommcd on 2006-12-15
Having DMA off could be your problem. Does your DVD ROM drive support dma? If so, you can turn it on this way:
"sudo hdparm -d1 /dev/hdc" (assuming /hdc is your drive, check "cat /etc/fstab" to find out).
Then to enable hdparm on bootup:
gksudo gedit /etc/hdparm.conf
then add this at the end:
/dev/hdc {
dma = on
}

Hope this helps.

---

### Post by flotsaminthecosmicsea on 2006-12-15
I am experiencing the same problems, only with .avi playback. Also screensavers are choppy. I don't think this has anything to do with the dvd drive. Any ideas?

Spec:
2 GHZ AMD 64 with 1GB RAM
ATI x800 Pro with latest drivers from ati

---

### Post by tommcd on 2006-12-16
To check if DMA is on:
for cdrom:
hdparm /dev/hdc
for hard drive:
hdparm /dev/hda
This assumes that hard drive is /dev/hda and cdrom is /dev/hdc. I don't believe dma is needed or required for sata hard drives.

---

### Post by flotsaminthecosmicsea on 2006-12-16
I think the hdparm thing might actually be part of the problem, since all my .avi's are saved to a windows drive. I checked whether it was on or not using...

> sam@sam-desktop:~$ sudo hdparm /dev/sdb1

and got...

> /dev/sdb1:
 IO_support   =  0 (default 16-bit)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 36483/255/63, sectors = 586099332, start = 63

I don't know which one of these needs to be on (I assume read only since it is a NFTS and cannot write to it anyways), but I tried turning it on by...

> sam@sam-desktop:~$ sudo hdparm -d1 /dev/sdb1

and got...

> /dev/sdb1:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device

Got any suggestions?

---

### Post by tommcd on 2006-12-16
/dev/sdb would indicate it is a SATA drive. SATA drives are listed as /dev/sdx, IDE drives are listed as /dev/hdx (where "x" is the letter of the drive) in /etc/fstab. I'm pretty sure dma is not necessary for SATA drives. I get the same thing on my SATA drive and performance is ok. Check if dma is on for the CDROM drive. I don't think the screensaver issue is related to the CDROM though. Your specs are good enough that screensavers should work fine. Is your video driver installed properly? I don't have any experience with ATI drivers. 
As for the .avi problem, are you reading them from a windows partition? If so, try copying some of them to your ubuntu partition and see if they run better.

---

### Post by flotsaminthecosmicsea on 2006-12-17
> **tommcd said:**
> As for the .avi problem, are you reading them from a windows partition? If so, try copying some of them to your ubuntu partition and see if they run better.

Great idea! Why didn't I think of that? Well, its still choppy after I tried that, so it must not be the hard drive.

> **tommcd said:**
> Your specs are good enough that screensavers should work fine. Is your video driver installed properly?

I thought I installed it correctly. (See attachment)

Is there any way (possibly using the device manager) to see if this is the driver my card is actually using?

---

### Post by tommcd on 2006-12-17
Well, I know with nvidia drivers you type "glxinfo" to see if direct rendering is enabled. There is a similar command for ATI, "fglrxinfo" I think it is. This should tell you if direct rendering is enabled.

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-c966b2cb7c82944d6883f27a2896725db3b90a3a](https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-c966b2cb7c82944d6883f27a2896725db3b90a3a)

---

### Post by sivnik on 2006-12-18
> **tommcd said:**
> with nvidia drivers you type "glxinfo" to see if direct rendering is enabled. 
i am sure the problem is in direct rendering, not in the dma
i have the same problem with the videos, i have nvidia, 
i do the glxinfo and says direct rendering: no
what should i do? i have installed drivers though

---

### Post by pormogo on 2006-12-18
After you install your drivers with apt or synaptic etc you're most likely going to need to choose the driver X is using in /etc/X11/xorg.conf. There should be a device section for your video card, what driver is it using there. 

direct rendering shouldn't really effect your video performance, the color space of the X server could cause an issue with some videos. (I think it was color space or maybe video overlay).

xine-check is an awesome tool for troubleshooting video issues. Make sure you have xine installed and then open a terminal and type in 

*xine-check*

---

### Post by sivnik on 2006-12-18
yeh, in the xorg.conf the driver it is using is nvidia, not nv
and i believe it is about direct rendering because the problem started after installing xgl-beryl

---

### Post by pormogo on 2006-12-18
well Xgl will "steal" direct rendering from your box making it appear as if your video card does not have direct rendering (this is the whole reason behind the AIGLX project using glx and hardware acceleration). Did you try running a xine-check in order to troubleshoot general video issues? 

What video player are you using and what output mode are you using? A common mistake I have seen is people trying to use openGL video output under XGL often this causes a performance decrease.

---

### Post by sivnik on 2006-12-18
i don't use xine, i use mplayer but the problem is with all the media players ofcourse
i use xv (X11/Xv) driver from the driver's list...

and from the xine-check:

> [ good ] you're using Linux, doing specific tests
[ good ] looks like you have a /proc filesystem mounted.
[ good ] You seem to have a reasonable kernel version (2.6.17-10-386)
[ good ] intel compatible processor, checking MTRR support
[ good ] you have MTRR support and there are some ranges set.
[ hint ] multiple xine executables found
         I have found multiple xine executables on your machine:
         /usr/bin/xine
         /usr/X11R6/bin/xine
         xine is the main player as installed by the xine-ui package.
         You should probably uninstall the instances you don't use...
         press <enter> to continue...

[ hint ] multiple xine executables found in your PATH
         I have found more than one occurance of 'xine' in your PATH:
         /usr/bin/X11/xine
         /usr/bin/xine
         You have probably installed xine-ui more than once, or the directory
         where you have installed xine occurs more than once in your PATH.
         Technically, this is not really a problem, but it's probably
         somewhat confusing, as it's not obvious, which xine you're using.
         You should probably uninstall the copies that you don't use...
         Further tests assume, you're using /usr/bin/X11/xine
         press <enter> to continue...

[OUCH!!] no xine-config on this machine.
         This means that xine-lib is either not installed
         or it is installed in a very unusual place.
         So you should probably install xine-lib before running xine-check...
         press <enter> to continue...

[ hint ] unable to determine plugin directory
         I could not determine your plugin directory. That would be much easier
         if you had xine-config installed (see message above)...
         Note that I could not check your xine plugins.
         press <enter> to continue...

[ good ] /dev/cdrom points to /dev/hdb
[ good ] /dev/dvd points to /dev/hdb
[ good ] DMA is enabled for your DVD drive
[ good ] found xvinfo: X-Video Extension version 2.2
[ good ] your Xv extension supports YV12 overlays (improves MPEG performance)
[ good ] your Xv extension supports YUY2 overlays
[ good ] Xv ports:  YUY2 YV12


---

### Post by tommcd on 2006-12-19
pormogo,
what are we to make of xine-check? I get the same output from xine-check as Sivnik, and my videos play fine in vlc, totem, mplayer, and xine. I do not experience 100% CPU load either. How do we interpret the output of xine-ckeck?
Sivnik,
have you tried disabling or uninstalling xgl-beryl to see if the problem goes away? I have read about so many problems with beryl that I won't touch it just for some eye candy.
BTW, I hear xgl-beryl will be included by default in ubuntu-feisty. I hope there is an easy way to disable or remove it.

---

### Post by sivnik on 2006-12-19
actually i don't know how to remove it, but for sure it has to do with it. Because before the installation of beryl i didn't have that problem with the videos.
But i like this and i don't want to remove it, i want to fix it :p

---

