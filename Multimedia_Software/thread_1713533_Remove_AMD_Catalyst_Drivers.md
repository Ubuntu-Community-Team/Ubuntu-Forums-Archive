---
title: "Remove AMD Catalyst Drivers"
date: 2011-03-24
forum: Multimedia Software
---

### Post by a_z1_9scores on 2011-03-24
Alright, so a series of events led me to install the AMD 11.2 Catalyst program from the website. Suddenly, I reboot and my desktop effects won't even turn on. So I go into the control panel and try to turn them back on but no such luck. Then, I find the configuration for the drivers but because I have no drivers installed, it pretty much gives me the middle finger and doesn't cut on, so I went to the administrative version, which requires a password that I didn't even set and so now I want the program gone and my display back to normal but the uninstall program that the PDF directions refer to doesn't exist. 

But long story short, I actually read the manual, found instructions on how to uninstall the program, and it tells me to run:

```
sh ./fglrx-uninstall.sh
```

but the problem is that the above doesn't exist, so I'll need to uninstall it manually, but I have no idea how to go about doing this. If someone could provide a newbie-friendly guide on how to go about doing this, I'd really appreciate it.

Thanks in advance :)

edit: Actually, I realized that the script was written wrong, so I modified it to:

```
sudo sh fglrx-uninstall.sh
```

and still had no luck.

---

### Post by realzippy on 2011-03-24
run line by line:
```
sudo apt-get remove --purge xorg-driver-fglrx fglrx*
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri fglrx-modaliases
sudo dpkg-reconfigure xserver-xorg
sudo apt-get install --reinstall xserver-xorg-core

```
from:
[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch)

---

### Post by a_z1_9scores on 2011-03-25
Awesome sauce! It worked perfectly. Thanks!

---

