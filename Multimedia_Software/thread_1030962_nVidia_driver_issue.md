---
title: "nVidia driver issue"
date: 2009-01-04
forum: Multimedia Software
---

### Post by hexagondun on 2009-01-04
hey everyone
I'm trying to install video drivers for an nVidia 8M series card on ubuntu.  I downloaded the driver and it gives me this command to type into terminal:    

sh NVIDIA-Linux-x86-180.17-pkg1.run

when I type that in and press enter it tells me:

 sh: Can't open NVIDIA-Linux-x86-180.17-pkg1.run

any ideas?  thanks in advance.

---

### Post by cph05a on 2009-01-05
I had a similar problem. These are the steps I used to get everything up and running. I'm using a dell M1330 with nVidia GeForce 8400M GS.

press ctrl + alt + F1 and log into the terminal there

disable  gdm using ```
sudo /etc/init.d/gdm stop
```

switch to the directory where you saved your run file

type ```
sudo sh NVIDIA-Linux-x86-180.17-pkg1.run
```
and use nvidia's installer to get your driver set up

type ```
sudo /etc/init.d/gdm restart
``` and you should see gnome pop up with the log in screen

---

### Post by hexagondun on 2009-01-06
thanks much, the drivers are installed!

---

