---
title: "Minimum ATI card for tear-free @ 1080p?"
date: 2012-01-03
forum: Multimedia Software
---

### Post by imrazor on 2012-01-03
I recently tried to install Ubuntu on an older box (see specs below) to try and use it as a file/media server. However, I've run into what I've found to be a common problem with Linux. HD video (and sometimes SD video) tear pretty badly when played back on my NVidia 8800GT + 1920x1080 monitor. Thus, I'm looking at low-end ATI cards to use with the "Tear Free" feature in recent Catalyst versions that has worked for me well, at least with a Radeon 5750. My question is what is the bare minimum ATI card I should get for tear-free playback at 1080p? 5450's are available pretty cheaply (starting at ~US$35) but I'm not sure if they have enough memory or GPU power to handle 1080p.
 
System specs:
Intel Pentium E5500 @ 2.8GHz
MSI G31TM-P21
3GB DDR2 667MHz
XFX NVidia 8800GT 256MB
Acer E211H Monitor
WD SATA 500GB "Green" drive
Seagate SATA 500GB 7200 RPM drive
WD SATA 320GB 7200RPM drive

---

### Post by inobe on 2012-01-03
i don't think it has anything to do with linux, more to do with the applications, video formats and setup!

you can mention that you've had the latest driver, that's only the start.

i have had nvidia cards, and haven't had a problem.

edit: here are my system specs.

[B]Intel Media Series motherboard (DP35DP)
Intel Core Duo e6850
6 gigs DDR2 800
LG bluray player/burner
Nvidia EVGA GTX 460
OpenSuse 11.4 x86 _64bit
Kubuntu 11.10 x86 _64bit[/B]

---

### Post by WienerWuerstel on 2012-01-03
Tearing is a common Problem on Linux? With Nvidia? Nope.

Just make sure to have the latest Nvidia Driver installed and use a good Media Player like XBMC that supports VDPAU. And even with OpenGL or XV Video Output you shouldn't see tearing at ALL.

---

### Post by inobe on 2012-01-03
> **WienerWuerstel said:**
> Tearing is a common Problem on Linux? With Nvidia? Nope.

Just make sure to have the latest Nvidia Driver installed and use a good Media Player like XBMC that supports VDPAU. And even with OpenGL or XV Video Output you shouldn't see tearing at ALL.

with mplayer2 and smplayer front end using output driver vdpau, i literally sat there for hours looking for a tare, and i didn't see "NOTHING" but a superb crystal clear 1080p movie :D

---

### Post by imrazor on 2012-01-04
I'm using the most recent nvidia driver in the repositories. I'm also using Totem for playback. It seemed logical to use the default media player. When I've used mplayer in the past, I've found playlist management to be severely lacking, though that may have changed. A playlist is a necessity when dealing with hundreds of videos.

---

### Post by inobe on 2012-01-04
do you have a component, vga, digital connection between the box and tv?

nice front end to mplayer2 [http://smplayer.sourceforge.net/](http://smplayer.sourceforge.net/)

---

### Post by imrazor on 2012-01-05
OK, I fixed this by doing the following 4 things:

1) Disabling compositing (add the following lines to /etc/X11/xorg.conf as root, then reboot:

```
Section "Extensions"
    Option "Composite" "Disabled"
EndSection
```2) Using the Ubuntu 2D desktop (available from login screen - click on the gear)
3) Using mplayer (or smplayer)
4) Selecting vdpau as the output video driver.

No one step by itself was sufficient, but video at 720p appears to be playing properly now. Haven't checked 1080p yet, but it'll probably work. Once I installed the beta Flash 64-bit plugin, I could even watch stutter free Youtube. Thanks to all who posted...

It really shouldn't be that much work, though. That's one reason I was interested in the ATI proprietary driver, since it seems to work with compositing and any video player.

---

### Post by inobe on 2012-01-05
> **imrazor said:**
> That's one reason I was interested in the ATI proprietary driver, since it seems to work with compositing and any video player.

ati/ amd make exceptional hardware, though there drivers are terrible.

from my experience, it's a cross platform problem and has absolutely nothing to do with linux.

---

