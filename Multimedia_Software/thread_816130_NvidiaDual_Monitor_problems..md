---
title: "Nvidia/Dual Monitor problems."
date: 2008-06-02
forum: Multimedia Software
---

### Post by phreakoe on 2008-06-02
I've just started playing around with Ubuntu again recently, and I have two monitors that I've been trying to get working. I can get both monitors functioning if I install the driver, then configure it to use TwinView, but it;
A) is very slow, the windows load slowly, dragging windows slows the system  down, X starts to use 80-90% of CPU when firefox is being dragged around the desktop.
B) when I reboot the system, it does not display the nvidia logo as it should when it loads X, and goes to "simple graphics mode".

The card is a Quadro NVS 280. I don't know what information you guys will need as I am still fairly new to this, but let me know if you need me to paste anything from logs or config files and I will do so.

Thanks!

---

### Post by phreakoe on 2008-06-02
Alright, so I reinstalled everything with 64 bit, and edited /etc/default/linux-restricted-modules-common which fixed the problem on reboot, but I'm still experiencing all of the slowdown. Any ideas?

---

### Post by phreakoe on 2008-06-02
Solved! Had to install the compiz settings manager and change the VSync and refresh rate settings.

---

