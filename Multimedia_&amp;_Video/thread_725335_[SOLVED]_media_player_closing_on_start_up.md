---
title: "[SOLVED] media player closing on start up"
date: 2008-03-15
forum: Multimedia &amp; Video
---

### Post by treymul on 2008-03-15
I have tried mplayer,vlc, and gxine.  I have downloaded all of the codex and restricted stuff. but each media player closes as soon as i try to open the dvd.  I dont know what to do.  any suggestions?

---

### Post by xc3RnbFO8P on 2008-03-15
In terminal:

> vlc

Return and show the output.

---

### Post by treymul on 2008-03-15
thats not what i mean, all of the media players open up, but when you press play to play the dvd, the players close on their own.

---

### Post by xc3RnbFO8P on 2008-03-15
If you start the player in terminal you can see what happened when you try to play a video.

---

### Post by treymul on 2008-03-15
here is the output:

  VLC media player 0.8.6c Janus
[00000298] a52 decoder: A/52 channels:6 samplerate:48000 bitrate:448000
No accelerated IMDCT transform found
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  140 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  84
  Current serial number in output stream:  85


what does this mean?

---

### Post by xc3RnbFO8P on 2008-03-15
Problem:

[http://ubuntuforums.org/showthread.php?t=725034]("http://ubuntuforums.org/showthread.php?t=725034")

---

### Post by treymul on 2008-03-15
Thanks man, rolled it back and now it works fine.  You don/t know how much crap I have installed trying to get this fixed.  How did you find that so quick?

---

### Post by treymul on 2008-03-15
by the way, only one player is working.  gxine works while vlc and mplayer do not(not that I care, i only need one).  Thanks again.

---

### Post by xc3RnbFO8P on 2008-03-15
You could try to reinstall, start with one player.

---

