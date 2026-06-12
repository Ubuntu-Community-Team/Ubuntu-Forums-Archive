---
title: "Screen Resolution: Stuck at 1024x768 w/10.04"
date: 2010-05-21
forum: Multimedia Software
---

### Post by katiad on 2010-05-21
I installed 10.04 on my former windows box last night, and I seem to be stuck at a screen resolution of 1024x768. I have a Geforce 7600 GT graphics card, and I installed current drivers via the hardware drivers option. I can't go above this resolution in the nvidia x-server settings, and even xrandr says the highest resolution I can use is 1024x768. What is up with that, and how can I change it?

---

### Post by alterpinguin on 2010-05-21
search in the forum how to provide the monitor settings. It may necessary for your hardware to enter some "modeline" entries into xorg.conf in /etc/X11 directory.
But - if you used the nvidia-settings program
check the installation of it with synaptic
and try to start it from an xterm-terminal with:
nvidia-settings (this program is only for nvidia-gra-cards and the appropriate drivers)
maybe you can use this to override with options in this gui-program.
-
Background: since some time(years?) x11-driver trys to query the monitor about the possible settings and if the monitor dont answers -or! the x11-setting is setup to ignore it(that is possible), then it might be stuck at an vesa-like-resolution and a 50Hz refresh-setting.
-
like told, using the search function for the forum will come up with a lot of ways to help x11 to use special monitor-resolution-settings with modeline s.

---

