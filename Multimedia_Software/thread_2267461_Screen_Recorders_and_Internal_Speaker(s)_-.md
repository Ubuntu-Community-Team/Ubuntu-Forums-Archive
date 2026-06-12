---
title: "Screen Recorders and Internal Speaker(s) - ?"
date: 2015-03-01
forum: Multimedia Software
---

### Post by michael-piziak on 2015-03-01
Ubuntu 12.04 LTS on HP Compaq dc5800 small form factor computer.

Before I put in and took out an Nvidia graphic card, I could get Kazam to record video and audio.  Now it only records video.

I installed SimpleScreenRecorder and can only record video with it also.

Can someone help me trouble shoot my system and figure out why I can't record audio (even though I can hear it).

---

### Post by mc4man on 2015-03-01
Don't have 12.04 but have just spent some time regarding screen cap with audio. I actually found simplescreen... to be the best as far as audio. No set up or anything.
So for ssr open it up & see what the setting is for Audio input > source. Typically should be "Monitor of Built-in Audio Analog Stereo" or similar.  If set to one that says (HDMI) in it then try changing to other one (built-in whatever

I also use FFmpeg but that needs to be set up one time  in pavucontrol > recording (when something is recording), here I choose the above also.

---

### Post by michael-piziak on 2015-03-01
Solved problem with a program called PulseAudio Volume Control in the Ubuntu Software Center.

Source of solution:  [https://www.youtube.com/watch?v=jeATRDE7LzI](https://www.youtube.com/watch?v=jeATRDE7LzI)

---

