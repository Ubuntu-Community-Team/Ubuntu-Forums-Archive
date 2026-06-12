---
title: "Laggy HD Video, many details"
date: 2012-04-16
forum: Multimedia Software
---

### Post by fishbutt2 on 2012-04-16
Codec: ubuntu-restricted-extras non-free-codecs 
GPU: 8800 GTS 512 (G92) nVidia
Player: VLC
Ubuntu 11.10 32b
 
I installed all these items from the software app on the stock gui. They do work for dvd. i tried increasing the buffer size in vlc and adjusting the x264 block settings to all. Teh block setting did work but is no longer hd :P
 
May also need the accelerated drivers for nvidia 8 series, fml. not sure what nvidia drivers i need. I miss ATI for sure with ubuntu
 
Any ideas?
 
BTW can you make my netflix work!?!? I was looking at the XBMC but not at the computer atm.
 
EDIT:: Adding: will try list
- VDPAU with nvidia works with mplayer \ smplayer
- Increasing video ram, playing flc file from temps
- Nvidia's official driver \ 8 series of ubuntu's distro driver
  [http://ubuntuforums.org/showthread.php?t=1771806](http://ubuntuforums.org/showthread.php?t=1771806)  that should be the fix I will check back later
-

---

### Post by fishbutt2 on 2012-04-18
Update:  Seems like those nvidia drivers are all inclusive.  reinstall did not help.  Going to try a new cpu though the current is on a stable OC

---

### Post by BicyclerBoy on 2012-04-18
You need the nVidia proprietary driver for GPU decode etc using VDPAU.
The 8800 GTS 512 is feature set A (the std 8800 GTS has no video decode).

By default VLC uses CPU for decoding/post-processing.

VLC can play 10Mbps H264 1080i (yadifx1) on 50% core2duo.
It has no problem with BD 24p (easier in some ways).

VLC does not directly support VDPAU but it can use VA-API (GPU acceleration).
There is a VDPAU backend for VA-API (vdpau-va-driver).

VLC has a problem with pulseaudio setup in some ubuntu versions..there is a simple mod to change pulseaudio timing method.

What's x264 block setting got to do with this ?
x264 is a H264 encoder..

---

