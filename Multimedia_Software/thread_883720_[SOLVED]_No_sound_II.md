---
title: "[SOLVED] No sound II"
date: 2008-08-08
forum: Multimedia Software
---

### Post by Ghoztrider on 2008-08-08
Here's my predicament for all those willing to listen ](*,)

I recently set up my machine for dual boot with Hardy and XP. For some reason I cannot get the Hardy side to make any sound whatsoever. I know all the peripherals work like the speakers and the actual jack itself(sound works in xp). I have a Dell Dimension 5100 with Sigmatel HD onboard sound controller. I am really newbish when it comes to some parts of linux, so I really don't know where to start. I ran a hardware test from the administrative menu and it looked like it saw my hardware. Any help would be appreciated. Thank You!!

---

### Post by brujoand on 2008-08-08
Try playing around in System --> Preferences --> Sound, and run the tests with different settings.. These settings control what soundcard/mixer is used for web media and system sounds.

---

### Post by Ghoztrider on 2008-08-08
I did try that...choosing the correct driver in the sound menu, however I didn't try all the options.

---

### Post by Ghoztrider on 2008-08-09
Well, I tried every option under the Sound menu in preferences. The "alsa" option and "PulseAudio" option gave me a faint steady beeping noise when doing the sound test. Nothing else worked. Is there anything else I could try?

---

### Post by Yellow Pasque on 2008-08-09
Try upgrading ALSA [http://ubuntuforums.org/showthread.php?t=820959](http://ubuntuforums.org/showthread.php?t=820959)
You can also try OSS4 (link in sig).

---

### Post by Armen818 on 2008-08-10
ty GrimmVarg,  that solved my problems with the sound

---

