---
title: "Getting flash hardware acceleration for nVidia"
date: 2011-10-31
forum: Multimedia Software
---

### Post by ticket on 2011-10-31
Adobe Flash version 11 (& maybe earlier) claim hardware acceleration under Linux is available for modern nVidia cards. This is apparently achieved by Adobe's 'stage' video architecture and the VDPAU interface.

But I'm not sure I've got this working properly.

I'm on Ubuntu 11.10 (upgraded from 11.04) and using a GT250 card on an Intel i3 PC.

I have created the file /etc/adobe/mms.cfg with contents:
```
OverrideGPUValidation=true
EnableLinuxHWVideoDecode=1
```

I'm using this video for testing:
[http://www.youtube.com/watch?v=XSGBVzeBUbk](http://www.youtube.com/watch?v=XSGBVzeBUbk)

Right click the video and choose the 'Show video info' menu option.  You typically get a popup showing something like:

```
10 stage fps, 23 video fps
Software video rendering, accelerated video decoding
```

If I play the video at 1080p, all four cores of the i3 go to about 30% to 40% and the 'top' command shows about CPU = 65%.
My graphics card has a loud fan, and this does increase in noise showing the GPU is indeed doing something.

If I play a downloaded 1080p video using totem (no gpu acceleration) I get 
the cores going between 20% to 40% and top shows 55% CPU.

If I play the same downloaded movie using gnome-mplayer with vdpau enabled, the cores show 10% to 20%, and top shows 12% (and the gpu fan noise increases).

To me, it doesn't look like the flash video is being accelerated to any significant extant.

I have tried the following advice, but made no difference:
[http://forums.adobe.com/thread/858201](http://forums.adobe.com/thread/858201)
The advice applied to 11.10 I believe should be modified to:
```
sudo ln -s /usr/lib/nvidia-current/vdpau/libvdpau_nvidia.so  /usr/lib32/libvdpau.so
```
I note that my /usr/lib32 directory contains no files - just empty folders (maybe a left over from an upgrade?).

I tend to conclude that while there may be some flash video acceleration going one, it isn't doing the whole job.  

I wonder if anyone using a low end CPU with a VDPAU capable card has had success in playing HD flash videos under Linux?

---

### Post by ilcapo09 on 2011-11-02
bump

---

### Post by papibe on 2011-11-02
Your results are consistent with recent tests. There is, without a doubt, acceleration going on, but not as good as older flash plugins versions.

My processor used to go around 15-20% on previous versions, now is around 70%. Nevertheless, the experience sitting on the couch is still smooth 1080p play.

[Here]("http://ubuntuforums.org/showthread.php?t=1856830&highlight=flash+vdpau")'s a previous discussion about the same topic.

Kind Regards.

---

### Post by ticket on 2011-11-05
Thanks for confirming.  Is there any need to set up a symbolic link like I did?

---

### Post by beew on 2011-11-05
At least for 32 bit, flash 11 stable build only works partially with vdpau (accelerated rendering but no accelerated decoding) However, the newest beta build does do accelerated decoding as well.

To install the beta version, install the flash-aid Firefox addon and run the script. It works well with full vdpau support in 11.04 32 bit. With 11.10 there seems to be some problems, but I am not sure if they are specifically flash related because overall graphic performance is not as smooth in  11.10 and FF appears to be very sluggish and choppy in general (not just in flash sites like Youtube),-- at least for my test installation.

---

### Post by papibe on 2011-11-05
> **ticket said:**
> Is there any need to set up a symbolic link like I did?

Not that I know of. Both my desktop (10.04) and laptop (11.04) were set just using the mms.cfg file.

Regards.

---

### Post by madjr on 2012-03-30
unreal engine flash working well for anyone ?

[http://www.unrealengine.com/flash/](http://www.unrealengine.com/flash/)

works for me on windows, not on linux (but havent tried to enable 3d yet if its possible)

---

### Post by pootan on 2012-03-30
It loads for me but the ground textures don't render. I'm on my old pc atm with a 9800gt, latest drivers on 11.10 64 bit.

---

