---
title: "Default Sound Card In Ubuntu"
date: 2009-10-06
forum: Multimedia Software
---

### Post by VertexPusher on 2009-10-06
Use "aplay -l" to find out the name of the soundcard you want to use. For onboard audio controllers on Intel boards it's usually just "Intel" (even if the controller is actually a RealTek one).

Create a text file with the following content:
```
defaults.ctl.!card "Intel"
defaults.pcm.!card "Intel"
```
Save the file as ".asoundrc" in your home directory, then log out and log in again. Now the Intel card should remain the default one for all applications.

---

