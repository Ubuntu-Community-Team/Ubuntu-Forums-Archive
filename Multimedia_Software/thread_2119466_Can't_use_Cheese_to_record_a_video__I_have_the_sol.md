---
title: "Can't use Cheese to record a video?  I have the solution"
date: 2013-02-23
forum: Multimedia Software
---

### Post by jimmy the saint on 2013-02-23
Cheese's latest bug seems to be that attempting to record a video locks up the program, or at the very least results in a video that won't save.

The solution is to install gstreamer1.0-pulseaudio

```
sudo apt-get install gstreamer1.0-pulseaudio
```

The bug to fix the dependencies is reported.  In the meantime, if you want to use cheese to record your webcam, install that package and you should be good to go.

---

