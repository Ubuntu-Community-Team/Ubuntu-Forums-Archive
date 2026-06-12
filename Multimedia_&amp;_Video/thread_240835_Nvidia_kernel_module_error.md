---
title: "Nvidia kernel module error"
date: 2006-08-21
forum: Multimedia &amp; Video
---

### Post by cornish on 2006-08-21
I´m seem to have broken something

After installing the NVIDIA drivers and re-editing xorg.conf
X fails to load, it says that I have the NVIDIA 8762 driver installed, but the version of my NVIDIA Kernel module is 7174

How do I remove this module.

Many thanks

---

### Post by tseliot on 2006-08-21
Set the driver to "vesa" in the Section Device of your xorg.conf

Then install Envy and follow the instructions (it will solve the problem for you):
[http://www.albertomilone.eu/europeo/nvidia_scripts1.html](http://www.albertomilone.eu/europeo/nvidia_scripts1.html)

---

