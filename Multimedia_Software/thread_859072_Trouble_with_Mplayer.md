---
title: "Trouble with Mplayer"
date: 2008-07-14
forum: Multimedia Software
---

### Post by _sAm_ on 2008-07-14
Hi I need some help with playing video using mplayer. 

I want to try to use Mplayer for some *.mkv(h.264) movies that VLC and Totem cant play with enough fps. But Mplayer fails to play any movies on my pc. 

Using Ubuntu8.04 with nVidia drivers enabled, I have installed codec from Mediabuntu.

When I open Mplayer I get an error(se picture). 

I started Mplayer from the terminal and then started to play a normal avi movie, I get no video only sound – and this is true for all movies I start with Mplayer(I get picture if I try with VLC or Totem Media player on the same videos). 

This is the info from the terminal:

Playing /home/sam/Server/Disk_1/video/Citizen.Kane.1941.Xvid/ck-cd1-bw.avi.
AVI file format detected.
[aviheader] Video stream found, -vid 0
[aviheader] Audio stream found, -aid 1
[aviheader] Audio stream found, -aid 2
VIDEO:  [DIV3]  608x448  24bpp  23.976 fps  1424.4 kbps (173.9 kbyte/s)
Clip info:
 Software: Nandub v1.0rc2
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
[VO_XV] It seems there is no Xvideo support for your video card available.
[VO_XV] Run 'xvinfo' to verify its Xv support and read
[VO_XV] DOCS/HTML/en/video.html#xv!
[VO_XV] See 'mplayer -vo help' for other (non-xv) video out drivers.
[VO_XV] Try -vo x11.
Error opening/initializing the selected video_out (-vo) device.
==========================================================================
Forced audio codec: mad
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 48000 Hz, 2 ch, s16le, 32.0 kbit/2.08% (ratio: 4000->192000)
Selected audio codec: [mad] afm: libmad (libMAD MPEG layer 1-2-3)
==========================================================================
AO: [pulse] 48000Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...

---

### Post by unoodles on 2008-07-14
Ok, had this problem when I first installed Mplayer too first you could (like it says in the output) use the switch -vo x11.
Also, you could (if you have the GUI frontend) click on preferences->video, and go through the list changing the driver until you find one that works for you.

---

