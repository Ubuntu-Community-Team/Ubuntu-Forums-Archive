---
title: "Audio has lots of static with MSI K9N2GM-FIH"
date: 2009-03-24
forum: Multimedia Software
---

### Post by daveisfera on 2009-03-24
I just installed Mythbuntu 8.10 and I was able to get sounds working over the HDMI cable by updating to the latest packages in the repository and then [upgrading to ALSA 1.0.19]("http://ubuntuforums.org/showthread.php?p=6589810").

But the problem is that now all of the sound that I play is full of static. I have tried muting everything in alsamixer but the HDMI output and it still didn't help.

Does anyone have any suggestions on what I can do to get rid of the static?

Thanks,
Dave

---

### Post by daveisfera on 2009-04-13
> **daveisfera said:**
> I just installed Mythbuntu 8.10 and I was able to get sounds working over the HDMI cable by updating to the latest packages in the repository and then [upgrading to ALSA 1.0.19]("http://ubuntuforums.org/showthread.php?p=6589810").

But the problem is that now all of the sound that I play is full of static. I have tried muting everything in alsamixer but the HDMI output and it still didn't help.

Does anyone have any suggestions on what I can do to get rid of the static?

This turned out to be a data problem (corrupted .wav files), and once I tried playing valid sound files, it worked fine.

---

