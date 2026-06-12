---
title: "Ubuntu is running in low graphics mode"
date: 2009-04-19
forum: Multimedia Software
---

### Post by necronwarrior on 2009-04-19
Today when I started my laptop I got the following error message on the screen on boot:
```

Ubuntu is running in low graphics mode.
The following error occurred. You may need to update your configuration to solve this problem.
(EE)GARTinit : Unable to open /dev/agpart (No such file or directory)
(EE)[drm] drm Open failed
(EE) intel(0) : [dri]DRI Screeninit failed.Disabling DRI
(EE) intel(0):Couldn't Allocate video memory.

```

It appears in a dialogue box which freezes and all I can do is directly power off the laptop.

---

### Post by inobe on 2009-04-19
you may need to allocate more vram in the system bios.

example

[IMG]http://www.hackernotcracker.com/wordpress/wp-content/uploads/2007/06/vram_bios.jpg[/IMG]

please include if you've done any updates prior to shutting down.

---

### Post by necronwarrior on 2009-04-22
> **inobe said:**
> you may need to allocate more vram in the system bios.
please include if you've done any updates prior to shutting down.
I went through all my bios options but found no option to increase the vram.
I have a lenovo thinkpad R61 (2Gb ram core 2 duo 1.80Ghz) . It has a integrated video card and shared video memory.
I triple boot Ubuntu 8.10--Fedora 10--Vista.
Before this problem started I had done a partial upgrade(no idea what that is but it came up in the update manager)
The error message says 
"Update your configuration to solve this problem"-->What conf. is it talking about??
Will upgrading to 9.04 help in solving this problem??
Please help as I don't want to reinstall ubuntu in any case.(already have put too much time into customizing it..)

---

### Post by VMC on 2009-04-22
It might be the xorg.conf file found here /etc/X11.

Post the output of that file here. Also post output of  ```
lspci -nn | grep VGA
```

---

### Post by necronwarrior on 2009-04-23
[PHP][/PHP]In case you didnt get me , I cannot boot into ubuntu at all .
The system boots( I get no graphical boot progress bar ) at the end the screen flashes a few times and then the error comes up.
Will running the same command in fedora work??
I get the following output in fedora:
```

$ lspci -nn | grep VGA
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a02] (rev 0c)

```
Here is my Xorg.0.log file from the folder //var/etc.The error that I get is listed at the very end of the file.
I have also included the xorg.conf file.

---

