---
title: "Ubuntu 10.10 - vdpau VLC or mplayer"
date: 2010-10-15
forum: Multimedia Software
---

### Post by mdalacu on 2010-10-15
Hi, is there an way to use vdpau in Maverick amd64? In Lucid was working very fine. 
Note: i've already installed vdpau-va-driver and no effect. In lucid there was a packet named vdpau-video which in Maverik conflicts with vdpau-va-driver and is not working.
:(

---

### Post by SeijiSensei on 2010-10-15
I just run the application to install the Advanced Drivers and let Ubuntu do the rest. It will install the NVIDIA driver and the associated libraries including libvdpau.  I suggest installing smplayer, a terrific GUI interface for mplayer.  ("sudo apt-get install smplayer" will install smplayer and mplayer as well.)

---

### Post by mdalacu on 2010-10-15
I am using Ubuntu x64 with activated drivers, Smplayer with vdpau enabled, does not work: video is displayed but it's not hw aided.
The same goes for vlc.

I have installed libvdpau1 and vdpau-va-driver. OpenGl applications, games are working great.
In Lucid with libvdpau1 and vdpau-video VA was working great but not in Maverick! :-(

---

### Post by Stolly on 2011-01-09
I believe i have the same problem....any solution ?

---

