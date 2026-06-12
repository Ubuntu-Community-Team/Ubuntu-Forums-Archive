---
title: "Video quality problems"
date: 2007-12-11
forum: Multimedia &amp; Video
---

### Post by jobyjoe on 2007-12-11
Hi guys, 
   I'm new to Linux, but I have been able to solve all my problems till now, and I'm really happy with Ubuntu (7.10). However, I got a problem with my video quality. I am using VLC player, and I set my preferences for X11 video output. I have nVidia GeForce 7950GT. When ever I play a video, the quality is very poor. I'm dual booting XP pro with Linux, and the video quality in XP is great. In Linux though, the video is distorted and grainy. I'm thinking it is a driver issue, but I'm not sure. Any help would be appreciated.


JobyJoe

---

### Post by rsambuca on 2007-12-11
What driver are you using?  I recommend the nVidia binary driver for that card.  It will make a huge difference if you aren't using it.  Also, X11 is one of the worst output modules.  Try XVideo.  (XGL should be better, but it is currently borked in VLC).

---

### Post by jobyjoe on 2007-12-11
Thanks for the reply. I switched to XVideo, and there is an improvement. I really don't know what driver I am using. I am using the restricted drivers manager, and am using the "Nvidia accelerated graphics driver". I mean, I didn't install any specific driver. When I installed Ubuntu, it asked me if I wanted to enable it, so I did.  

So I don't think this is the nVidia binary driver. ON the nVidia site, there is a Linux 64 driver for this card. It is 100.14.19. Is this what I need?

---

### Post by rsambuca on 2007-12-11
Open your Synaptic Package Manager (System - Administration - Synaptic Package Manager).  Scroll down and see if you have the nvidia-glx-new package installed.  If so, that is the same one as you have seen on the nvidia site.

---

### Post by jobyjoe on 2007-12-11
Yeah, it is marked as installed. 

Is it enabled? Or do I have to run something like "sudo nvidia-glx-config enable"???

---

### Post by rsambuca on 2007-12-11
If you used the Restricted Drivers Manager and it is marked as in use, then you are good to go.  There have been some memory leak issues under certain cases with this driver though.

---

### Post by jobyjoe on 2007-12-11
thanks for all your help. 
I'm not sure if it is enabled. In the Restricted Drivers Manager, the only one present says "NVIDIA accelerated graphics driver" and it is enabled. Is this nvidia-glx-new driver? I typed "sudo nvidia-glx-config enable" into the terminal, and this came back:

Error: your X configuration has been altered.
This script cannot proceed automatically. If you believe that this
not correct, you can update the md5sum entry executing the following
command:
md5sum /etc/X11/xorg.conf | sudo tee /var/lib/x11/xorg.conf.md5sum
otherwise edit manually /etc/X11/xorg.conf to change the Driver section
from nv to nvidia."

I don't know if this means anything or not. Any help would be appreciated

---

### Post by rsambuca on 2007-12-11
Uh, you didn't need to run that command.  I doubt it hurt you though.   Restart X by pressing control-alt-backspace.

---

### Post by jobyjoe on 2007-12-11
Yeah, nothing got hurt. Changing the video output did help, still the videos aren't clear. Any other ideas??


Thanks,

---

### Post by rsambuca on 2007-12-11
> **jobyjoe said:**
> Yeah, nothing got hurt. Changing the video output did help, still the videos aren't clear. Any other ideas??


Thanks,

Can you elaborate on "not clear" for your video?  What types of files are these?  mpegs? avi? DVD?

On my rig, the video quality is pretty much the same between XP, Vista, and Ubuntu.

---

### Post by jobyjoe on 2007-12-12
So far it's been on .avi and .mgegs. The picture just really looks grainy an pixilated. Are there any settings I could fool with?

---

