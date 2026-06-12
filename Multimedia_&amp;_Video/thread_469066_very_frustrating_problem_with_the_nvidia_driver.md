---
title: "very frustrating problem with the nvidia driver"
date: 2007-06-09
forum: Multimedia &amp; Video
---

### Post by fakie_flip on 2007-06-09
I've looked on various websites and guides on how to do this. im trying to uninstall ubuntu's packages of the nvidia driver, and use the driver that I downloaded from nvidia.com.  Well, I must have never got it removed completely before installing the one from nvidia.com because when my computer reboots, x wont start. I can get x to start by removing the nvidia module (rmmod) and then loading it again with modprobe. Then x will start. This is a crummy thing to do every time my computer reboots, and I would like to have the problem fixed. From the directions here.

[https://help.ubuntu.com/community/Latest_Nvidia_Dapper](https://help.ubuntu.com/community/Latest_Nvidia_Dapper)

It says this for removing the nvidia module in ubuntu's packages:

```
HOW TO UNINSTALL THE DRIVER (from Method 1)

Restore your old xorg.conf

sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf

NOTE: if the backup of your old xorg.conf doesn't work or you lost it try this command (so as to regenerate a clean xorg.conf): sudo dpkg -reconfigure -phigh xserver-xorg

If you used the nvidia driver 8178 (not the legacy one)

sudo apt-get --purge remove nvidia-glx linux-restricted-modules-`uname -r` linux-restricted-modules-common

OR (If you need Legacy drivers, i.e. your graphic card is in the list at the end of the page or you need driver 7174)

sudo apt-get --purge remove nvidia-glx-legacy nvidia-xconfig nvidia-settings linux-restricted-modules-`uname -r` linux-restricted-modules-common

Log out and press CTRL+ALT+BACKSPACE (so as to restart the xserver).
```

However, when I do that, apt says its going to remove the linux kernel and a bunch of other packages.

```
chris@ubuntu:~$ sudo apt-get --purge remove nvidia-glx linux-restricted-modules-`uname -r` linux-restricted-modules-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package nvidia-glx is not installed, so not removed
The following packages were automatically installed and are no longer required:
  binutils-static
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  linux-generic* linux-restricted-modules-2.6.20-15-generic*
  linux-restricted-modules-2.6.20-16-generic* linux-restricted-modules-common*
  linux-restricted-modules-generic*
0 upgraded, 0 newly installed, 5 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 97.5MB disk space will be freed.
Do you want to continue [Y/n]? 
```

Attempting to remove nvidia-kernel-common will result in the same thing.

```
chris@ubuntu:~$ sudo apt-get --purge remove nvidia-kernel-common 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-generic* linux-restricted-modules-2.6.20-15-generic*
  linux-restricted-modules-2.6.20-16-generic*
  linux-restricted-modules-generic* nvidia-kernel-common*
0 upgraded, 0 newly installed, 5 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 97.5MB disk space will be freed.
Do you want to continue [Y/n]? 
```

---

### Post by fakie_flip on 2007-06-11
bump

---

### Post by logos34 on 2007-06-11
You shoud be using the newer guide for feisty (it's slighly different)[B]
[http://www.albertomilone.com/latest_nvidia_udsf_feisty.html](http://www.albertomilone.com/latest_nvidia_udsf_feisty.html)[/B]

Unless I'm mistaken, you shoudl be looking at Method 2 since you installed the proprietary driver from the nvidia website

---

### Post by fakie_flip on 2007-06-11
Yes, I've seen it, so what are you suggesting?

---

### Post by logos34 on 2007-06-11
well according to the feisty guide you didn't need to remove 
linux-restricted-modules-`uname -r` linux-restricted-modules-common

---

### Post by fakie_flip on 2007-06-14
linux-generic was only a meta package, so I removed it. everything worked fine with my new 8800 gts graphics adapter except my psu couldn't handle it and quit working. do you have any advice on choosing another one? i know what the wattage should be, but what about the other specs?

---

### Post by logos34 on 2007-06-14
> **fakie_flip said:**
> linux-generic was only a meta package, so I removed it. everything worked fine with my new 8800 gts graphics adapter except my psu couldn't handle it and quit working. do you have any advice on choosing another one? i know what the wattage should be, but what about the other specs?

Get ATX12V v2.2 compliant.

Most that you see nowadays will come with the 24-pin main connector plus 6-pin PCI-x16 connector.  And some may even come with two and be SLI certified.

Make sure it has dual +12v/dual rail, 20+4 pin main connector, and high efficiency under typical to high loads (say 75-80% or better).  Active PFC too.

Dual fans (in push-pull arrangement) are nice in that they cut down noise. I have an Antec SmartPower 400W with 2 fans and it's very quiet when not virtually silent, which is more than I can say for my TruePower 430W with a single larger fan under similar loads. 

Modular cabling nice too...you plug in only the cables you need.

I've heard nothing but good things about Seasonic and PC Power & Supply.  Google around and read the reviews.

---

### Post by dabl on 2007-06-14
> **fakie_flip said:**
> i know what the wattage should be  Yep, that's what I thought, too -- go up another 100 watts from what you think it should be, if you want to avoid an unhappy surprise.  The PSU makers wear rosy glasses when they rate their power supplies.  Two cents' worth ....  ;)

---

