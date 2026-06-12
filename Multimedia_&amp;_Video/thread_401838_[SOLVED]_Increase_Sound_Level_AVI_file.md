---
title: "[SOLVED] Increase Sound Level AVI file"
date: 2007-04-05
forum: Multimedia &amp; Video
---

### Post by prince_niceguy on 2007-04-05
I am having an avi file which I ripped from a personal DVD. The video format is xvid, audio is mp3 128 kbps. However, the sound level is very low, I have to put the volume to maximum to make it barely audible.

Is there a way a increase the sound level now. I no longer have the DVD with me.


thanks

---

### Post by tbroderick on 2007-04-05
Add this line to /home/username/.mplayer/config
```
af=volnorm
```

That will normalize the audio like mp3gain. I'm not sure if VLC or Xine has a similar option.

---

### Post by prince_niceguy on 2007-04-18
well i used transcode and did it. do not have the command with me currently but i did a pass through for video (-P 1) and ensured that the gain is 10 (-s option i believe).

---

### Post by prince_niceguy on 2007-04-18
command transcode -i <input file> -P 1 -s <desired gain> -N <desired format i used 0x55(mp3)> -o <output file>

---

