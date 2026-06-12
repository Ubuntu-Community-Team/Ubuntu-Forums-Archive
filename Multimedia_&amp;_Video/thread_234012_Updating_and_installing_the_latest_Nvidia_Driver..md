---
title: "Updating and installing the latest Nvidia Driver."
date: 2006-08-10
forum: Multimedia &amp; Video
---

### Post by Betta on 2006-08-10
How can I check my nvidia driver version and update it if needed? I have an nvidia Geforce 6800XT if that helps. I am new to Ubuntu so don't expect too much, but I'm fairly competent.

-Betta

---

### Post by visik7 on 2006-08-10
right now ubuntu 6.06 contain the latest nvidia driver
btw you need to check it by hand but be happy ubuntu devs updates this drivers when a new version will come out

---

### Post by Betta on 2006-08-10
Under System Settings > Display > Hardware, it says the following:

Graphics card: nv
Driver: nvidia

Is this how it should be?

I have it all sorted out, thanks for the help though ^_^

---

### Post by Mooie on 2006-08-11
you can check the driver version to see if its the latest if you open synaptic and search for nvidia-glx, off to the side it should say "installed version" and if that matches the latest one on the nvidia site, then you have the latest one.

if you haven't installed the nvidia driver yet, then type
```
sudo apt-get install nvidia-glx
```
in a command line, when that is finnished you need to type
```
sudo gedit /etc/X11/xorg.conf
```
this opens a text document. scroll down to the section labled devices, and you need to change where it says nv to nvidia

if you just used synaptic or did an apt-get install nvidia-glx, you still need to edit the xorg.conf document if you haven't yet, or your computer just wont use the driver.

I hope this answered your questions :D

---

### Post by Mooie on 2006-08-11
oops, I just read your last post again, you have everything working, it says driver: nvidia, which is the good one. that is the latest driver. :D

---

### Post by tseliot on 2006-08-11
```
dmesg | grep NVIDIA
```

---

