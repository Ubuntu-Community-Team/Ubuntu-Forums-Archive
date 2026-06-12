---
title: "No Alsa output on HH"
date: 2008-05-08
forum: Multimedia Software
---

### Post by kmand on 2008-05-08
I upgraded from GG to HH on a laptop, and now I get no sound from ALSA.

aplay gives no sound, and the test button in gnome-sound-properties is also silent. The test button for OSS does give sound.

---

### Post by jocko on 2008-05-08
Let's see the output of these commands:```

aplay -l
asoundconf list
alsamixer
```

---

