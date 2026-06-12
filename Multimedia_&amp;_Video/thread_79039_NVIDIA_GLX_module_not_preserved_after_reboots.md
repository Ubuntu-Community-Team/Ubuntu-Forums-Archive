---
title: "NVIDIA GLX module not preserved after reboots"
date: 2005-10-19
forum: Multimedia &amp; Video
---

### Post by YetZero on 2005-10-19
Hi all, I have an nVidia Geforce MX 4000, that worked perfectly in Hoary. I did a fresh install of Breezy and the nv driver just threw me at a 640x480 resolution with no options. So I tried to install the nvidia driver from Synaptic, and that didn't work either, because the kernel module was in conflict with xorg module number (7767 vs 7776 I think).
So I installed the latest nvidia driver from nvidia.com, fine. All 3D apps working and TV-OUT working too. And when I reboot, it starts xorg Ok, but no 3d apps would work, all of them give me a segfault error, as if the glx module was not present. Even tough the glx extension .so file is in place all the time, it just doesn't find it. So I have to reinstall the nvidia-driver everytime I boot my computer, and that's a bit annoying... I think it's a linking problem, tried with sudo ldconfig but nothing works. Can anyone point me on this?

---

### Post by marx1984 on 2005-10-30
remove nvidia-glx  with apt-get remove nvidia-glx. then check /etc/init.d/ for a script called nvidia-glx if it's there than this was your problem. remove it's execution rights be doing chmod -x nvidia-glx. then reinstall the nvidia driver you got from nvidia.com and reboot and everything should work. I had this problem also until reinstalling nvidia's drivers gave me clues that something else was altering my driver. It turns out nvidia-glx was loading ubuntu's nvidia package which messed with X. try that and if it doesn't work try searching google but this should work.

---

