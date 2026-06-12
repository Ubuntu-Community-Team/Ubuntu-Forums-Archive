---
title: "Surround sound issues"
date: 2008-01-14
forum: Multimedia &amp; Video
---

### Post by piratebill on 2008-01-14
Ok, I am new here, so if this is posted in the wrong place please let me know. I dual boot gutsy 64 bit and xp home. my motherboard has a chip set 6 channel sound card (gutsy tells me its a hda nvida). in xp the surround sound works great. In gutsy, only the front channels work. I have looked at the audio settings in volume control, and the surround option is unmuted and turned up. Running this code:
speaker-test -Dplug:surround40 -c6 -twav
I have discovered that my rear left speaker is playing when the center should and the right rear plays when the LFE is supposed to play. I am very confused. I have even tried moving the black jack (for the rear speakers channel) to the orange jack, but then the left rear is labeled correctly, but the right rear doesn't work at all.

Do I need some special driver? is there a way to reassign what speaker is what? Thanks in advance. this has been driving me crazy for the last few days.

also I am using alsa and have esound installed if that changes anything.

---

### Post by Spartan.II.117 on 2008-01-16
You might try the suggestions at this link.
[http://www.arsgeek.com/?p=971](http://www.arsgeek.com/?p=971)

Spartan

---

### Post by piratebill on 2008-01-17
no change.

---

