---
title: "X fails to start after install nvidia-glx"
date: 2006-08-22
forum: Multimedia &amp; Video
---

### Post by Lorian on 2006-08-22
Ubuntu was working fine for quite a while, then I had to reinstall,just need to change some partitions around. Anyway, after installing and enabling the NVIDIA drivers according to the wiki, X fails to start. The output says:

No matching Device section for instance (BusID PCI:5:0:0) found
[...]
Fatal server error:
no screen found

I tried restoring the backup and it still gives the same error. Also, it named the card ATI Radeon..., instead of the usualy NVIDIA Default...

Please help, I don't like having to use Windows :(

---

### Post by rpalyvoda on 2006-08-22
hm... strange!!!

What video card do you have?

I've got a similar problem usine Nvidia GeForce 4 420, the solution was to edit some configuration files (search forums in this case)

---

### Post by rpalyvoda on 2006-08-22
btw, did you install linux-restricted-modules for your kernel version?

---

### Post by rpalyvoda on 2006-08-22
I've forgotten:

to return to a working version of Ubuntu, reboot you computer in recovery mode, then type this:

> sudo dpkg-reconfigure xserver-xorg

you'll have to answer a couple of questions (use default if you don't know), and when it asks for video driver, just use nv instead of nvidia (make choice with space bar)

good luck

---

### Post by Lorian on 2006-08-22
Thanks to [this](http://www.ubuntuforums.org/showthread.php?t=186219) topic, with these instructions:```
sudo /etc/init.d/gdm stop
sudo dpkg-reconfigure xserver-xorg 
sudo dpkg-reconfigure gdm
sudo /etc/init.d/gdm start
```I managed to fix it. Thanks to all :).

---

### Post by RuarriS on 2006-08-22
also if you:

sudo gedit /etc/X11/xorg.conf

and edit the drivers line from "nvidia" to "nv" I find that works for me

---

### Post by kelcey_s on 2006-08-22
Yeah, this is the update to Xserver.

[http://www.ubuntuforums.org/showthread.php?t=241254]("http://www.ubuntuforums.org/showthread.php?t=241254") for all the answers.

I fixed it with

```
sudo apt-get install xserver-xorg-core=1:1.0.2-0ubuntu10
```

---

