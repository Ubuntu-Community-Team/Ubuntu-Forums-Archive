---
title: "How to fix pixellated video?"
date: 2011-09-20
forum: Multimedia Software
---

### Post by t0p on 2011-09-20
Most of the time, my computer (running Ubuntu 10.04) plays video files nice and smoothly.  But some videos won't.  Case in point: I've got a video file, Doctor_Who_Series_6_-_11._The_God_Complex_b014vy02_default.mp4, which doesn't want to play nicely at all.  If I try using vlc, the picture is all broken up and pixellated.  If I try totem or banshee, it plays as a series of stills.  Audio is okay, but the video is messed up.

I figure that some parameter or something of the file is too big for my old Pentium 4 PC to handle.  So I think maybe I can use ffmpeg or something to convert the file so it'll be playable.  But I don't know how.

ffmpeg says of the file:

> 
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'Doctor_Who_Series_6_-_11._The_God_Complex_b014vy02_default.mp4':
  Duration: 00:47:58.98, start: 0.000000, bitrate: 798 kb/s
    Stream #0.0(und): Video: h264, yuv420p, 640x360, 25 tbr, 50 tbn, 100 tbc
    Stream #0.1(und): Audio: aac, 24000 Hz, stereo, s16


(I've got ffmpeg to tell me that, but I don't know how to make ffmpeg fix it for me.)

Can anyone please help me?  Cheers.

---

### Post by t0p on 2011-09-20
I *think* I've found a solution to my problem.  In vlc, go to Tools > Preferences > Video, then go to the Output drop-down menu and choose "GNU/Linux framebuffer video output".  I did that, then restarted vlc and it seems that my pixellation problems have gone.

I have marked this as [SOLVED] on a provisional basis, but I may revise that if the problem rears its ugly head again with different video files.

---

### Post by t0p on 2011-09-21
Well, I'm revoking this thread's [SOLVED] status as the "fix" I described worked only very temporarily.  Other video files are suffering the described problem.

Note: the videos suffering this pixellation are all BBC iplayer files that I've downloaded via the **get_iplayer** utility.  Most of my other video files seem to run legibly.  So, the BBC is putting something in their iplayer files that won't play nicely with my computer.  Any ideas what that might be, and how I may fix it?

---

### Post by t0p on 2011-09-21
Incidentally, I find it pretty lousy that no one has responded to my pleas for help.  I would have thought *someone* frequenting the Multimedia & Video forum would have at least some sort of idea what's up.  Isn't this where the video wizards hang out?  Makes me wonder if I would have got a better response if I'd posted this in General Help.  C'mon, multimedia gurus - help out a video and multimedia n00b, *pleeeeze*!!  :(

---

### Post by jhonan on 2011-09-21
> **t0p said:**
> Incidentally, I find it pretty lousy that no one has responded to my pleas for help.
You should get a refund :p

I can't help with your issue, but what I will say is that I thought the previous week's episode; 'The Girl Who Waited' was excellent - classic Dr Who, and a great plot idea.

I was a bit disappointed with the God Complex - It lacked suspense.

---

### Post by BicyclerBoy on 2011-09-21
Similar bitrate H264 media files playback okay on dual core atom 330. (Not tried with VLC)

The BBC material is likely to be higher bit-rate or using higher compression. Both put more demands on the (your) CPU for decode & then decoded video data bus-bandwidth. Uncompressed video is huge.

The stock 10.04 VLC has played (CPU decode core2duo) any H246/L4 HD media I have tried.

Mediainfo is the best tool to inspect media files.

You still need to have reasonable video h/w with CPU decode.

With weak CPUs (P4, atoms etc) you need to be using video decode h/w acceleration of VDPAU VAAPI XvBA via VA-API support in VLC.
This has (2) effects: lower bus demands (compressed data) & allows CPU to do other stuff.

With P4 chipset you likely have almost no options..
There is one nVidia PCI video card with basic VDPAU.
The chipset GMA4500MHD or GMA500 can be made/massaged to work..

What is the video h/w ?
What driver ?
Can you get VLC from ppa with VA-API support ? Can you make any use of it?

---

### Post by t0p on 2011-09-22
> **BicyclerBoy said:**
> 
What is the video h/w ?
What driver ?
Can you get VLC from ppa with VA-API support ? Can you make any use of it?

I've got a very old nvidia video chip - can't recall the name, and I don't know how to look it up, but it is very old. 

System > Administration > Hardware Drivers says I'm not using any proprietary drivers, so I guess I'm using Ubuntu/Linux's own, Free driver for ancient nvidia hardware.

I have not yet investigated if I can get vlc from ppa with VA-API support, as I have never heard of VA-API support before and have no clear idea what it is.  I shall check it out later (as will I try to discover the name of my nvidia video hardware).

Thanks for the response, BicyclerBoy.  I hope I can make use of it!

---

### Post by BicyclerBoy on 2011-09-22
Be aware that the real old nvidia cards have a separate legacy driver (96?).
And it might have to be a re-built "old driver" because of ABI changes in 11.04 Xorg.
These Xorg changes will end up in 10.10 & 10.04 now/soon. 

You will not get much of a lift with VA-API on old h/w.
Do you have a spare PCI slot ?

---

