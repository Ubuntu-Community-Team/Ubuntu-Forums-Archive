---
title: "startup sounds but no audio"
date: 2010-01-23
forum: Multimedia Software
---

### Post by viingot on 2010-01-23
I have startup sounds but no audio once I've logged in.  I can see the volume meter in the pulseaudio volume control panel moving when I play music but no sounds.  I tried searching through the forums but I couldn't find a solution and it seems like this should be an easy fix.  Thanks in advance.

---

### Post by mörgæs on 2010-01-24
[https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats](https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats)

---

### Post by viingot on 2010-01-24
Thanks for replying!  Unfortunately, I don't have any of the issues in the debugging guide so I still have no sound.

---

### Post by Enigmapond on 2010-01-24
I had terrible audio issues after I upgraded and that was one of them...I just totally purged pulseaudio from my system and went back to pure alsa and the sound now works well again...I suggest you do this...pulse is too quirky and I have no idea why the devs are sticking with it. Maybe in the next LTS it will have worked out but pulse is the pits now..

---

### Post by viingot on 2010-01-24
I purged pulseaudio but it didn't fix the audio.  I ended up switching from ubuntu to xubuntu because I heard xubuntu doesn't use pulseaudio and now I have sound.  So solved! (kind of)

---

