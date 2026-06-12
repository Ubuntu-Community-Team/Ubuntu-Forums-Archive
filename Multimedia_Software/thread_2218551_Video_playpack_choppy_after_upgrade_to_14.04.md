---
title: "Video playpack choppy after upgrade to 14.04"
date: 2014-04-21
forum: Multimedia Software
---

### Post by dalekky on 2014-04-21
Ok, this one has me stumped.

Playback of video files in totem movie player was perfect under Ubuntu 13.04. As soon as I upgrade to 14.04 I get choppy video.

I've installed the ubuntu-restricted-extras packages and have main,universe and multiverse repositories enabled... what am I missing?

The videos which previously played ok in totem, but are now giving me trouble are using mpeg-4 video codec.
The video is choppy and slow. Audio seems fine.

I have no issues with choppy playback if I use VLC. Why is totem now giving me grief after upgrade?

---

### Post by slyson on 2014-04-22
> **dalekky said:**
> Ok, this one has me stumped.

Playback of video files in totem movie player was perfect under Ubuntu 13.04. As soon as I upgrade to 14.04 I get choppy video.

I've installed the ubuntu-restricted-extras packages and have main,universe and multiverse repositories enabled... what am I missing?

The videos which previously played ok in totem, but are now giving me trouble are using mpeg-4 video codec.
The video is choppy and slow. Audio seems fine.

I have no issues with choppy playback if I use VLC. Why is totem now giving me grief after upgrade?

I have the same issue with mpeg-4 and totem on fresh 14.04 install. Likewise, vlc works fine. Running totem through console does not give any errors. My laptop has i7-2620m, Intel HD 3000 and nVidia NVS4200M with optimus.

---

### Post by dalekky on 2014-07-27
is there a solution yet to fix this choppy video which started with 14.04?

---

### Post by cetag on 2014-08-12
I have just upgraded Ubuntu Studio from 12.04.12b to 14.04. 
You are right, choppy video playback in 14.04 playing with mplayer from the command line. 

Parole media player is choppy playing mp4 video, similar to mplayer. 
Totem (3.10.1) continues to be just terrible. Audacious (3.4.3) continues to work very well for audio files. 

In my earlier Studio 12.04,  mplayer would play video perfectly.   
I will keep browsing for reports and recommendations on Studio 14.04 video, totem, Firefox, and will get back here if any news.


PS:  This following seems to suggest the driver for the system's graphics card is critical,  
[ askubuntu.com/questions/455515/ubuntu-14-04-just-update-and-very-slow ]("http://askubuntu.com/questions/455515/ubuntu-14-04-just-update-and-very-slow")

Presently I believe my system is sane, as the nouveau driver is in use. Will check against :( nVidia drivers.  

$ lspci -vnn | grep -i VGA -A 12
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation NV5 [Riva TNT2 Model 64 / Model 64 Pro] [10de:002d] (rev 15) (prog-if 00 [VGA controller])
    Subsystem: ASUSTeK Computer Inc. Device [1043:0221]
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 16
    Memory at de000000 (32-bit, non-prefetchable) [size=16M]
    Memory at da000000 (32-bit, prefetchable) [size=32M]
    Expansion ROM at df6f0000 [disabled] [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: nouveau

---

### Post by cetag on 2014-08-12
I replaced the nouveau graphics driver with NVIDIA-Linux-x86-71.86.15-pkg1.run. 
As a result, the choppy video is gone, but the video plays slow whereas the audio plays 
at normal speed, when using mplayer. 

Parole Media Player doesn't run, it says "GStreamer backend error. Could not initialize Xv output".
XIne plays video slow and audio at normal speed same as mplayer, but Xine controls are unusable.

---

