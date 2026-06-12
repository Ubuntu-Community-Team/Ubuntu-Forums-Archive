---
title: "Amarok-firefox problem"
date: 2011-03-31
forum: Multimedia Software
---

### Post by Anacleto85 on 2011-03-31
Hi, 

I have installed Amarok on my pc with all codec and it play all without problem.
However, I have opened firefox and video (for instance from youtube) were without audio. Hence, I've tried to close amarok and video on internet became listenable. But now amork is not listenable.

someone can help me?

---

### Post by Yellow Pasque on 2011-03-31
You need to be using Pulseaudio in the Multimedia section of KDE SystemSettings. Also, you need to make sure ALSA apps are routed through Pulseaudio, which should be the default in fresh installs of Ubuntu 10.04 and later.

---

### Post by Anacleto85 on 2011-04-01
Well, I don't know were is KDE SystemSettings. I have searched it on system->preference but nothing. I've searched something similar also in system->preference->sound, nothing also there. Howere I've checked that PulseSection package are present in my library. Now?

---

### Post by Yellow Pasque on 2011-04-01
```
sudo apt-get install systemsettings
systemsettings
```

---

