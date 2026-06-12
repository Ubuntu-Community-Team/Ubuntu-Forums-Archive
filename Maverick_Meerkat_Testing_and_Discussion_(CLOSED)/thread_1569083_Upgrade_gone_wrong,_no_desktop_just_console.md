---
title: "Upgrade gone wrong, no desktop just console"
date: 2010-09-06
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Arla on 2010-09-06
Ha! Silly me thought that since my lovely USB drive worked just fine, so would the upgrade, that'll teach me!

Anyway, I don't appear to get a net-connection if I just let it boot to the console, so I booted into the live-CD and then used the mount (dev, proc and sys) commands and chroot'd into my partition. When I try apt-get update I get a lot of messages about "something wicked happened resolving" and well, I'm a bit clueless from here, do I just bite the bullet and try a fresh install, or is there something else I can do?

---

### Post by Arla on 2010-09-06
Not sure if it matters, but I've discovered that resolving any name doesn't appear to work, from the live CD I can ping say [www.google.com](www.google.com) just fine, however from my chroot'd terminal I get the message "unknown host www.google.com" but if I ping the actual IP address it works fine, so... I guess I could update sources to have the IP addresses and see if that works? (just thinking out-loud)

---

### Post by DemonBob on 2010-09-06
Chck your logs in /var/logs/ to look for errors. 


Xorg.0.log
messages
syslog
dmesg

Post any errors here.

---

### Post by Arla on 2010-09-06
Xorg.0.log has one error

> 
(EE) Screen(s) found, but none have a usable configuration.
Fatal server error:
[    26.371] no screens found


messages and dmesg both appear to have none (as far as I can tell)

syslog has

> 
GdmLocalDisplayFactory: maximum number of X display failures reached: check X server log for errors


but that appears to be it

---

### Post by ronacc on 2010-09-06
using the live cd  mount your install and using gedit as root ( sudo gedit ) edit /etc/X11/xorg.conf  so that the line that now reads 

```
driver     "nvidia"
```

reads

```
driver      "nv"
```  

or you could just delete xorg.conf and it will default to the vesa driver 

this should let you get to desktop and install the nvidia driver using
system>administration>aditional drivers .

---

### Post by Arla on 2010-09-06
> **ronacc said:**
> using the live cd  mount your install and using gedit as root ( sudo gedit ) edit /etc/X11/xorg.conf  so that the line that now reads 

```
driver     "nvidia"
```

reads

```
driver      "nv"
```  

or you could just delete xorg.conf and it will default to the vesa driver 

this should let you get to desktop and install the nvidia driver using
system>administration>aditional drivers .

Couple of issues there, one is that I don't have a file called etc/X11/xorg.conf, other is I'm not using an nvidia chipset (intel 950 here)

Doing a search for xorg.conf I found this file (other than a manual and a sample file)

usr/share/X11/xorg.conf.d

---

### Post by k4341 on 2010-09-06
after update maverick I can't go to mygnome, n I solved with [http://ubuntuforums.org/showthread.php?t=1116636](http://ubuntuforums.org/showthread.php?t=1116636)

---

### Post by Arla on 2010-09-06
> **k4341 said:**
> after update maverick I can't go to mygnome, n I solved with [http://ubuntuforums.org/showthread.php?t=1116636](http://ubuntuforums.org/showthread.php?t=1116636)

I moved that file, didn't seem to change anything.

---

### Post by ronacc on 2010-09-06
> **Arla said:**
> Couple of issues there, one is that I don't have a file called etc/X11/xorg.conf, other is I'm not using an nvidia chipset (intel 950 here)

Doing a search for xorg.conf I found this file (other than a manual and a sample file)

usr/share/X11/xorg.conf.d

sorry I thought you were nvidia , I've seen that error message when an update nuked the nvidia driver.

can you boot into recovery mode ?

---

### Post by Arla on 2010-09-06
> **ronacc said:**
> sorry I thought you were nvidia , I've seen that error message when an update nuked the nvidia driver.

can you boot into recovery mode ?

Just got into recovery mode properly, and managed to get it to boot to low-graphics mode, so getting somewhere!

Still not sure what's actually wrong, will keep looking.

---

### Post by ronacc on 2010-09-06
try running sudo apt-get update then sudo apt-get upgrade then sudo apt-get dist-upgrade in that order , that should bring anything that got missed in the original upgrade .

---

### Post by Arla on 2010-09-06
> **ronacc said:**
> try running sudo apt-get update then sudo apt-get upgrade then sudo apt-get dist-upgrade in that order , that should bring anything that got missed in the original upgrade .

Done all that, and unfortunately still no dice, it still just dies to console if I try to run my main boot (in anything but recovery mode), obviously some config file is screwing it up (since it works in live-cd and works fine for low-graphics boot) just to figure which one!

---

### Post by Arla on 2010-09-06
> **Arla said:**
> Done all that, and unfortunately still no dice, it still just dies to console if I try to run my main boot (in anything but recovery mode), obviously some config file is screwing it up (since it works in live-cd and works fine for low-graphics boot) just to figure which one!

Okay mostly solved, seemed to be the problem of having "nomodeset" on the GRUB_CMDLINE_LINUX, removing that and it all boots fine, so something must not quite like that option. I lost the option to do backlight changes again, but that seems to happen every single update.

One concern on this, I know a lot of people had been using that option under Lucid, not sure if it's just me that that is an issue on, or for others too?

---

