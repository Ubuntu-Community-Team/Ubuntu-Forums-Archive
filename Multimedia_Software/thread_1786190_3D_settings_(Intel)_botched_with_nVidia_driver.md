---
title: "3D settings (Intel) botched with nVidia driver"
date: 2011-06-19
forum: Multimedia Software
---

### Post by Seb1982 on 2011-06-19
Hey Guys,

Yesterday I played a little with a Bitcoin miner and discovered today that I must have scambled my 3D settings. My Intel graphics card doesn't seem to work, instead I must have added a nVidia Settings Manager to my menu.

I already removed the package I mistakenly installed (something concerning OpenCL) but nothing happens. The xorg.conf file seems to be okay.

Gnome now only starts in 2D mode and Unity refuses to work at all.

Do you have an idea how I might get my Intel card back working?

Thanks for your help!

Sebastian

---

### Post by smokes2345 on 2011-07-18
the included opencl package depends on the nvidia driver.  

run ```
sudo apt-get remove nvidia-common
``` to remove the nvidia driver

---

