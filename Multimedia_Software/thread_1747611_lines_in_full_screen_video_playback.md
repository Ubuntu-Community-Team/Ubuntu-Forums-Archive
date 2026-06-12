---
title: "lines in full screen video playback"
date: 2011-05-02
forum: Multimedia Software
---

### Post by mcduo on 2011-05-02
Hi

I really don't know where I should ask this question. When I'm watching a video in full screen (ex, avi or h264 file) I am seeing random horizontal bars where there is action on the video like where a head is turning.

When the motion is slow I am less likely to see these lines. Faster the motion, lots of lines or shaky motion. I was using my onboard Geforce 6150 GPU but thought it was because it was underpowered. I then bought a GT220 thinking that it was the problem. It is still but less frequent. 
Using the built in player, VLC... 

I don't know where to look, what to search for...


There is my setup:

AMD Athlon II x2 255
4GB DDR3
nvidia GT220 512mb
24" 1080p BenQ monitor connected with HDMI
latest nvidia drivers
Ubuntu 11.04 64 bits

---

### Post by afriseun on 2011-09-06
bump

Ubuntu 11.04 32bit
Nvidia GT220 1G
nvidia-driver 270.41.06
Samsung PDP tv at 848x480
2G memory
Some Intel Dual Core processor :)

I've already tried switching on all sync to V-Blank options as described in other places as well as setting manual refresh rate to 60 Hz. Any other suggestions out there?

Regards,
Carel

---

### Post by BicyclerBoy on 2011-09-07
It could be tearing vsync or de-interlacing.

Does it look like horizontal combing on high motion video ?
Turn on yadifx2 filter (VLC).

The GT220 is very capable HTPC GPU & has excellent VA de-interlacing via VDPAU.
Has very good scaling (down in your case)..

The built-in gnome mplayer ? could have some VDPAU support.
VLC does not. VLC uses VAAPI.
There is a vdpau-va library to allow VAAPI on VDPAU h/w.

VLC should have no problem s/w decoding 1080i H264 & yadifx2 on 50% CPU of a core2duo.

But it is better to use VDPAU directly with MythTV XBMC mplayer etc.

There is no tearing/combing with VDPAU.
The Xv & openGL vsync settings have no effect on VDPAU.

The player should be able set the refresh rate/video mode if you have a mix of 50 & 60Hz material etc.

---

