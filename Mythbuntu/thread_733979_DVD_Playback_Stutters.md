---
title: "DVD Playback Stutters"
date: 2008-03-24
forum: Mythbuntu
---

### Post by ed3120 on 2008-03-24
I'm using 8.04 A4 and all video playback (including 1080i and 720 HD)  works flawlessly, except for DVD playback.  It works, but the video stutters.  The audio is perfect.  

Are there any settings that I can play around with to fix this?  DVD playback is obviously much less CPU intensive than HD playback, so I'm wondering what is happening.

---

### Post by pdragon04 on 2008-03-24
I noticed that my DVD player speed was set to x2 in the Video Settings menu. My DVD-ROM is x16 read, but the max it can be set to is x12. I bumped it up to x12 and haven't been having anymore stutter problems myself. Give that a try and see if it works for you.

---

### Post by ed3120 on 2008-04-10
I tried changing it to 12x and I still have the video stutters.  Is anyone else having this issue?

---

### Post by slyhne on 2008-04-11
Hi

Have you tried enabling DMA for your DVD drive?

You can do it in /etc/hdparm

There are examples in the file.

Good luck

slyhne

---

### Post by adderx99 on 2009-01-18
try following the instructions on 
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

it just worked for me. i had very similar symptoms before trying this. DVD playback worked, but was unwatchable as it stuttered too much. both audio and video. vlc was previously reporting that "decoder is leaking pictures".
however after flowing the instructions above everything is fine. i hope that helps.

---

