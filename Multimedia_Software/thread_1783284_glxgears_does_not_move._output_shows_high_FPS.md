---
title: "glxgears does not move. output shows high FPS"
date: 2011-06-15
forum: Multimedia Software
---

### Post by holcepl on 2011-06-15
In the terminal, I type glxgears and get a frozen window of the colored gears. My terminal window spits out this until I close the gears window.

```
john@linuxcompy:~$ glxgears
59684 frames in 5.0 seconds = 11936.646 FPS
62038 frames in 5.0 seconds = 12407.523 FPS
62352 frames in 5.0 seconds = 12470.210 FPS
61269 frames in 5.0 seconds = 12253.732 FPS
61047 frames in 5.0 seconds = 12209.273 FPS
60873 frames in 5.0 seconds = 12174.468 FPS
58891 frames in 5.0 seconds = 11778.107 FPS
57960 frames in 5.0 seconds = 11591.902 FPS
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0"
      after 50 requests (50 known processed) with 0 events remaining.
john@linuxcompy:~$ lspci | grep VGA
01:00.0 VGA compatible controller: nVidia Corporation GF106 [GeForce 450 GTS] (rev a1)
john@linuxcompy:~$
```

---

### Post by Mr. Moustache on 2011-06-15
Same here, using compiz!

---

