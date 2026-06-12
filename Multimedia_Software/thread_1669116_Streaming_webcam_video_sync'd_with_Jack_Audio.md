---
title: "Streaming webcam video sync'd with Jack Audio"
date: 2011-01-17
forum: Multimedia Software
---

### Post by chicle2en1 on 2011-01-17
Hi all,

I come from XP and I used to stream occasionally through Justin.tv. Now I switched to Ubuntu Studio 10.10 and have not found a way to do so. My main goal is to be able to simultaneously broadcast audio from my firewire audio interface (through Jack) and video from my webcam. Also, I would like to be able to stream video with audio from PulseAudio, to use my Zoom H2, but this is secondary.

I tried VLC for streaming, but it cannot seem to find my integrated webcam (I have a Lenovo T400 laptop). The webcam does work with Skype, and worked great for broadcast on Justin.tv under XP.

Any solutions? Thanks for your help!

---

### Post by chicle2en1 on 2011-01-30
Well, it's been a week and no replies... So, I figured it out myself. 
 For the video, just go to:
 [http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager06.html](http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager06.html)
 and under the tab with an eye allow justin.tv to show video.
 
 Audio just works out of the box, even with the Zoom H2, through Pulse Audio. In addition, I am using Jack through Pulse Audio, with:
pactl load-module module-jack-source
This has allowed me to play electric guitar plugged to my firewire audio interface.

By the way, I have since re-installed Ubuntu Studio, this time 10.04 with  the rt kernel, and it has been a much smoother experience than 10.10.  However, I must recognize that I have learned from all the mistakes I  made while on 10.10.

I hope this helps somebody. If so, please let me know!

---

### Post by Jason92 on 2011-02-28
hey chicle2en1, realy thanks for the informations you provide here, it was exactly what I needed!

good work.

---

