---
title: "[SOLVED] copy audio from video file"
date: 2008-03-01
forum: Multimedia &amp; Video
---

### Post by panguin on 2008-03-01
Is there any *moderately* easy way to take a video file and copy the audio from it?

I ask because I have a lot comedy standup videos that i would love to make into comedy standup cds.

any ideas? i tried to do it by myself vlc, but fuggit dude. shenanigans on that. i need someone smarter and more well equipped than myself.

---

### Post by yabbadabbadont on 2008-03-01
```
mplayer -vc null -vo null -ao pcm:fast:waveheader:file=mynewwavfile.wav nameofvideofilesource
```
That will create a standard wav file which can be burned to a standard audio CD.

---

