---
title: "Microphone not detected 11.04"
date: 2011-04-20
forum: Multimedia Software
---

### Post by Nalfeshnee on 2011-04-20
I'm having trouble getting 11.04 to recognize my microphone. I have no connector option in sound preferences under input and I have turned the playback volume down for my mic all the way in alsa mixer as well as made sure that the capture volume is all the way up.

Any ideas would be much appreciated. 

[http://www.alsa-project.org/db/?f=ae459ad21a96f96a5a778cf9ffb2e845a5dc9709](http://www.alsa-project.org/db/?f=ae459ad21a96f96a5a778cf9ffb2e845a5dc9709)

---

### Post by lidex on 2011-04-20
It looks like you tried to update alsa in one way or another. It doesn't look good. First re-install alsa:

Using a Terminal="Applications->Accessories->Terminal"
```
sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2
```
**Reboot.**

For a 'command not found' error simply install aptitude:
```
sudo apt-get install aptitude
```

---

### Post by JeffreyBlanchard on 2011-06-28
This worked for me.  Thanks!

---

