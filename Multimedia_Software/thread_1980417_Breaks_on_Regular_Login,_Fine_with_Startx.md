---
title: "Breaks on Regular Login, Fine with Startx"
date: 2012-05-15
forum: Multimedia Software
---

### Post by handheld-penguin on 2012-05-15
I'm running precise kubuntu with 3.2.0-24-generic and NVIDIA driver 3.295.49.  Recently, whenever I login the X11 server has trouble setting up my display correctly. It will either not correctly load the NVIDA kernel module or the Intel-x11 kernel module that I have for the monitor using the integrated graphics.

What does work however is that if I kill the kdm and then drop into a shell and run startx, it all works fine. What does it do differently other than a simple startx upon login that is causing it to not load my modules correctly?

Everytime I reboot atm I have to kill the kdm and run a startx manually - not ideal.

Cheers,

Jam

---

