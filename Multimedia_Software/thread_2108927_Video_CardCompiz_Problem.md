---
title: "Video Card/Compiz Problem"
date: 2013-01-26
forum: Multimedia Software
---

### Post by smtaylor on 2013-01-26
Hi. 
I have had Ubuntu 12.10 running on a custom system for about 3 months now and it has been working flawlessly. However, I recently installed a new video card (nVIDIA GEFORCE GT 610 DDR3 1GB PCIe 2.0), and now Compiz has been using between 40-90% of my CPU all the time. It never used to be this way and I am really not sure what to do.

I have tweaked a few settings in Compiz to see if that would lessen the load, but it really hasen't done much. It has been causing system sluggishness. My CPU is a Pentium(R) Dual-Core CPU E5500 @ 2.80GHz × 2,

The machine is only about 2-3 years old and is in great condition with 4GB of RAM. 

Anyone have any thoughts or tips?
Thanks!!

---

### Post by Yellow Pasque on 2013-01-26
Did you install the nvidia driver?
```
sudo apt-get install nvidia-current
```

---

### Post by smtaylor on 2013-01-26
Thanks man that did it. I wasn't able to find a driver before but that installed it and now it is working fine. Thanks!!

---

