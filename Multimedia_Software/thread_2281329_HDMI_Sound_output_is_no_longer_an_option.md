---
title: "HDMI Sound output is no longer an option"
date: 2015-06-06
forum: Multimedia Software
---

### Post by kbuntu1 on 2015-06-06
I am using Xubuntu viivid. Up until recently, whenever I plugged my television into the HDMI output of my laptop, applications like the Parole media player would automatically use HDMI output.

Now, when I plug in the television, HDMI sound output is no longer an option. The display manager still recognises the video output, though.

How do I get the system to recognise HDMI audio as an option again?

---

### Post by TheFu on 2015-06-06
Did a new kernel get installed?
Have you tried reinstalling the GPU drivers?  A few yrs ago, I had to manually reinstall the ATI drivers after every new kernel to get HDMI video+audio working again.

Also, if the kernel is an LTS HW compat kernel, there are some other issues which may be important. So ... is the system running that kernel? If you didn't go out of your way to install it, then you are not - unless the install was from a 14.04.2 ISO.

---

