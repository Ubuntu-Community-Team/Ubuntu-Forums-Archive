---
title: "Audio stuttering (fast play) Ubuntu 12.04"
date: 2013-11-04
forum: Multimedia Software
---

### Post by stefbeukers on 2013-11-04
Hi guys,

I'm using Ubuntu 12.04 with the 'famous' poulsbo gma500 driver. After a lot of updating and upgrading I've managed to get the most of Ubuntu working. Although when I play a video on Youtube or play music in Rythmbox/VLC, my audio and video seem to stutter. The audio plays at higher speed than normal and only once in a few times it really plays a sound. For video it's the same. 

Does any of you have an idea? 

Thnx!

---

### Post by olli-sylvanne on 2013-11-07
have ASUS eeePc with gma500. All problems vanished when I deleted Rhythmbox. Also installed Xfce desktop which has more capabilities to set up HW. Cannot run Full HD but HD Ready (1300*700) works rather good in a window. Have SMPlayer + Mplayer2. Cannot get VLC working.

Anyway difficult to understand this mess with sound/video where several applications are intertwined and have an effect on what comes out.

Am a beginner and not very versed with this issue at hand.

---

### Post by stefbeukers on 2013-11-08
Thnx! Going to give it a shot and delete Rhythmbox. I'll keep you posted!

---

### Post by stefbeukers on 2013-11-12
Removed Rhythmbox, but no progress. Audio and video still stuttering.

---

### Post by olli-sylvanne on 2013-11-15
My humble advice would be: check what audio driver you are using, ALSA or pulse. Try changing that.

My case was very much like yours and after weeks of this and that it (probing here and there) it suddenly started working ok. And  sound and video in sync. But not full HD which is beyond the GMA500.

---

### Post by Yellow Pasque on 2013-11-15
At least one Poulsbo user said this fixed it: [https://wiki.ubuntu.com/Audio/PositionReporting](https://wiki.ubuntu.com/Audio/PositionReporting)

---

### Post by stefbeukers on 2013-11-17
Hmm, thnx for the link. I'm going to give it a shot! I'll let you know ;-)

---

### Post by stefbeukers on 2013-11-17
Done! Fixing the PulseAudio option worked for me! So make it two Poulsbo users said this fixed it ;-)

Thnx all!

---

### Post by btherio on 2014-04-26
Setting  "[COLOR=#333333]options snd-hda-intel position_fix=1" also fixed my stuttering audio problems with my GMA500. Thanks!

[/COLOR]

---

