---
title: "Why is in Synaptic package &quot;nvidia-glx-71&quot; if Ubuntu 8.10 not suport RIVA TNT2 card?"
date: 2008-11-07
forum: Multimedia Software
---

### Post by alikas on 2008-11-07
Why is in Synaptic package "nvidia-glx-71" if on Ubuntu 8.10 this package driver not suport "RIVA TNT2/TNT2 Pro" video card?


If say simple: I have "NVIDIA RIVA TNT2 Model 64/Model 64 Pro" video card and want install driver, who can adjust brightness and contrast display.
But then I install "nvidia-glx-71" package and write in /etc/X11/xorg.conf **Driver		"nvidia"**, then then start computer something write, that can not load "nvidia" driver.


More simple: How I can make smallest brightness and contrast on Ubuntu 8.10?

---

### Post by bathala on 2009-01-12
I have exactly the same problem.

My server is using the same video card:
```

lspci | grep VGA
01:00.0 VGA compatible controller: nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro] (rev 15)

```

First I tried using envyNG then manually using aptitute and apt-get for nvidia-glx-71 to no avail. It kept failing at boot when it tried to run the nvidia kernel.

---

### Post by agharbeia on 2009-05-06
Here too with Jaunty and the exact same card as bathala.

---

### Post by douham on 2009-05-19
Same here, trying out jaunty on my low-spec machine and want to be able to enable Nvidia"s leagacy driver.

---

### Post by _B00 on 2009-09-02
me too! sucks bum!

---

