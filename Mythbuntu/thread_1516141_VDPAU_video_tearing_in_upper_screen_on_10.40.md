---
title: "VDPAU video tearing in upper screen on 10.40"
date: 2010-06-23
forum: Mythbuntu
---

### Post by dibuntux on 2010-06-23
I mean 10.04, of course...

VDPAU was working perfectly in SD in 9.10 AMD64 but had problems with artifacts in H.264 HD, all using DVB-T. The Nvidia driver was 185.-latest.

Now that I'm on 10.04 AMD64, mythtv .23 with PPA latest, I'm experiencing video tearing in the upper portion of the screen, like if the GPU cannot keep pace with fast moving scenes - in fact on normal slow panning or quite still scenes the video is perfect. The effect is not very visible, you have to watch it for a while to get it, but it is there and annoying.
The strange thing is that it happens on SD and HD (1080i - now works!) channels.


One thing: the Nvidia driver is the 195.something (believe is the latest) - but I cannot start Nvidia X server setting application from the System menu in XFCE. In Mythbuntu control center, if I launch restricted drivers manager it says that Nvidia accelerated graphics driver (version current) (recommanded) is installed - also Firmware for DVB cards is installed.

My settings for VDPAU are: VDPAU Normal;


Any Ideas? TIA, Dave

Mythbuntu 9.10 AMD64
Gigabyte GA-M720
Athlon X2 4800+
Nvidia 9400GT 1GB
WD Sata2 CaviarGreen
Skystar 2 DVB-s
Nova T-500 dual DVB-T
Denon AVR 1610 connected with SPDIF
Optoma HD700x on DVI

---

### Post by LowSky on 2010-06-23
Are you using Mplayer or mythtv's internal player to playback content?

To open Nivida-settings in a terminal, type:

```
gksu nvidia-settings
```

---

### Post by novellahub on 2010-06-24
I have this in my /etc/X11/xorg.conf file to prevent tearing:

```

   Section "Extensions"
       Option "Composite" "Disable"
   EndSection

```

---

### Post by dibuntux on 2010-06-27
Thanks novellahub, now I recall that I had this in my x.conf:

Section "Extensions"
       Option "Composite" "Disable"
   EndSection

...and now it works like it should!

But I also noticed that some of my .mkv files in 720p X.264 present some bad artifacts, and thta was not the case before...
This is using internal player. Any ideas? TIA

Oh, BTW, LowSky, I tried your solution for nvidia settings:

gksu nvidia-settings

but nothing happens...

---

### Post by novellahub on 2010-06-28
Try playing one of your mkv files in mplayer or VLC and see if the artifacts are still there.  Are you sure it is a condition of tearing or a line of static at the top of the video's?  The line of static in some programs I believe carry the closed captioning part of the broadcast.  I had to use nvidia-settings to adjust the overscan to eliminate that issue.

---

### Post by dibuntux on 2010-06-28
No, no static, it is a DLP cinema system...
And yes, it does not show with VLC or not usinf vdpau with internal. 
Thanks for helping

---

