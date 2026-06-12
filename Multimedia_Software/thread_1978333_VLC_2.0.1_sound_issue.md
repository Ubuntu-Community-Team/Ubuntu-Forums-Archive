---
title: "VLC 2.0.1 sound issue"
date: 2012-05-11
forum: Multimedia Software
---

### Post by eulu on 2012-05-11
Not sure if this is the place to report this.. 

VLC with Ubuntu 12.04 x64 sound distortion happens intermittently when playing audio/video files.

Has been an issue since I first installed Ubuntu 12.04 and VLC back in March. Doesn't happen with other players like Kaffeine.. 

Apparently the same as this closed thread: [http://ubuntuforums.org/showthread.php?t=1962648](http://ubuntuforums.org/showthread.php?t=1962648)

I have an SB X-Fi sound card installed. I can make a change to the output selection to another mode in the system sound settings and switch it back and this resets to normal sound in VLC for a short period of time bu then it starts fuzzing out again (sometimes within a minute, and always within a few minutes)...

---

### Post by Exeleration-G on 2012-05-14
Happens to me too.

---

### Post by carl4926 on 2012-05-14
Look for

phonon-backend-vlc and vlc-aout-pulse

---

### Post by revacuate on 2012-07-01
> **carl4926 said:**
> Look for

phonon-backend-vlc and vlc-aout-pulse


installing the package phonon-backend-vlc fixed it for me. thanks for the hint carl4926!

---

### Post by carl4926 on 2012-07-02
> **revacuate said:**
> installing the package phonon-backend-vlc fixed it for me. thanks for the hint carl4926!
Good to know, thanks

---

### Post by eulu on 2012-07-02
seems to have done the trick here too! Thanks

---

