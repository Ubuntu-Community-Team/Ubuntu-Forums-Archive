---
title: "Cannot play Flv. files"
date: 2009-02-05
forum: Multimedia Software
---

### Post by BlackAce on 2009-02-05
I am trying to play flv files with VLC player which is my player of choice. I was using to Ubunutu and then switched to Mandriva and back to Ubunutu. I didn't have any problems playing them in Mandriva. I downloaded all the GStreamer and abode flash but just get a blue screen for not having the proper codec. Audio is fine. What am I missing???

---

### Post by BlackAce on 2009-02-05
I also follows these instruction for mediunbuntu still no luck.

[http://ubuntuforums.org/showthread.php?t=943506](http://ubuntuforums.org/showthread.php?t=943506)

I also tried playing them in Totem and Swfdec flash player with no luck either.

---

### Post by wolfen69 on 2009-02-05
completely remove flash using synaptic package manager. then:
```
sudo apt-get clean && sudo apt-get autoremove
```
then go [here]("http://get.adobe.com/flashplayer/") and download the .deb for ubuntu 8.04+

click to install.

---

### Post by BlackAce on 2009-02-05
Thanks but that didn't work. Still getting a blue when playing downloadeded flv files.

---

### Post by gandaran on 2009-02-05
change the video output/driver in vlc preferences to x11 or xv
you don't need to install codecs for vlc, vlc has it's own codecs!
for .flv files try totem

---

### Post by BlackAce on 2009-02-06
Thats did it THANKS!!!!

---

