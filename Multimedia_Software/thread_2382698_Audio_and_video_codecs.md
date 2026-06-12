---
title: "Audio and video codecs"
date: 2018-01-16
forum: Multimedia Software
---

### Post by espectro2 on 2018-01-16
Hi, I have a question which option do I have about audio and video codecs gstreamer is better? I  would not like to install ubuntu-restricted-extras as I will not use  either openjdk or flash would you like to install only audio and video  codecs which best option for ubuntu 16.04.2?
Thanks for listening.

---

### Post by speartip on 2018-01-16
If I was you I would just install ubuntu-restricted-extras, & then uninstall flash. I'm not even sure that openjdk comes with the restricted package anymore.
Alternatively, open a terminal, as if you were going to install the restricted-extras package, & see what it installs before you accept it. Then make a note of what you need & install them separately.

---

### Post by mc4man on 2018-01-16
gstreamer1.0-libav  covers the bulk of decoding
gstreamer1.0-plugins-bad & gstreamer1.0-plugins-ugly fill out some format coverage, dvds, ect.
So this is all you'd likely need
```
sudo apt install gstreamer1.0-libav gstreamer1.0-plugins-bad gstreamer1.0-plugins-ugly
```

---

### Post by espectro2 on 2018-01-16
Thanks for the attention I'm going to install the gstreamer as recommended 

sudo apt install gstreamer1.0-libav gstreamer1.0-plugins-bad gstreamer1.0-plugins-ugly

---

