---
title: "Sound mixer"
date: 2007-11-18
forum: Multimedia &amp; Video
---

### Post by I Tvivl on 2007-11-18
I've just updated my ALSA-driver, but now I haven't got a sound mixer. I've tried to install an OSS-mixer, but it said something about libraries. Then I installed the library from alsa-project.org and it said something like nothing to do with 'all'. And it keeps giving me messages like that whenever I try to install the library OR the OSS-mixer.

I tried installing by:
'filename'
sudo make
sudo make install


- Rasmus

---

### Post by Yellow Pasque on 2007-11-18
Try removing ALSA and installing OSS (see my sig). Once you get the OSS DEB installed, you can use ossmix in the terminal or ossxmix in the GUI.

---

