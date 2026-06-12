---
title: "Random Graphics Problems"
date: 2010-11-20
forum: Multimedia Software
---

### Post by ice2921 on 2010-11-20
Hello Everyone,

For the last few weeks I have been having some strange video card problems. Basically whats happening is that every now and then my screen will go squirrelly. It flickers a few funky colors almost like you would have a vga cable half way on. Now my monitor is less than a year old and I have tested it on windows and have not had any issues whatsoever. When the graphics issue happens I am not doing anything in particular like playing a game or watching a movie. It happens completely at random, and has worked great for the longest time. Here are some spec about my system:


Ubuntu 10.04 x64
EVGA nforce 780i SLI mainboard 
Geforce 9500 GT x 2

```
cat /proc/driver/nvidia/version
NVRM version: NVIDIA UNIX x86_64 Kernel Module  260.19.21  Thu Nov  4 21:16:27 PDT 2010
GCC version:  gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5)
```

I have installed the nvidia drivers via the nvidia website using the latest nvidia drivers for my cards. If you need any more just ask.Any help would be appreciated. thanks

---

### Post by ice2921 on 2010-11-21
Anyone?

---

### Post by sikander3786 on 2010-11-21
You can try reconfiguring your graphics.

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

If that doesn't help, you can try purging the existing drivers and re-install them.

Some more troubleshooting options are listed here.

[https://wiki.ubuntu.com/X/Troubleshooting/Freeze](https://wiki.ubuntu.com/X/Troubleshooting/Freeze)

Or it might be compiz as well. Disable it if you've enabled.

Good Luck!

---

