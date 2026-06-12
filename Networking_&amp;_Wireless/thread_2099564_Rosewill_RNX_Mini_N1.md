---
title: "Rosewill RNX Mini N1"
date: 2012-12-29
forum: Networking &amp; Wireless
---

### Post by andrude27 on 2012-12-29
I am trying to connect to my wifi using the rnx mini n1 dongle.  I downloaded the driver from rosewill and installed it.  The wireless(USB) finds my network but won't connect to it.  When I use my wep key (Iknow not very secure) it tries but keeps asking for the key. I am using the correct key (same as in other wireless devices and is listed in my modem setup screen.  I read the manual and this device uses the realtek rtl8188cus chip set.  The module installed is the rlt8192x.  When I turn off my security on my modem I still can't connect.  I went to realtek and downloaded a driver 8188cus.  I tried to install but it won't.  I tried to blacklist the rtl8192x module but it seems modules are handled differently than with prior Ubuntu versions I have used.  I tried the live disk and the rtl8192 module is loaded by default.  I can't see any modules with cat/etc/modules.  Nor can I see any modules blacklisted, even though I blacklisted the rtl8192x module.  I am not a total noob, but I'm beginning to feel like one.  When I installed the new driver I used the install.sh file by making it executable.  Do I have to compile it manually?  I have read several simaler threads and tried what they tried with no luck.  Could my device be defective?  Could the tiny device be able to see my network but not strong enough to talk to it?  Please someone more well versed than I help!

---

### Post by ahallubuntu on 2012-12-29
First of all, you have to build the correct driver - there are several unfortunate similarities in names of Realtek modules.  And Realtek considers the 8188/8192CU to be the same thing, somehow.  I'm not sure I can explain it.

In any case: download the correct driver from Realtek's website.  (You want "RTL8192CU" .) I have the same dongle (a generic version but same chipset) and have built it many times in Ubuntu 12.04 and 12.10.  I downloaded the latest from Realtek again this afternoon and built it in 12.04 and it worked perfectly.  But you have to blacklist the correct driver names (then reboot).

I've detailed it pretty well here:

[http://ubuntuforums.org/showthread.php?p=12318056#poststop](http://ubuntuforums.org/showthread.php?p=12318056#poststop)

FYI, the /etc/modules file is for ADDING modules to be loaded at boot time.  It is not of all modules in use or available.  You do need to add the new name ("8192cu") to this file to get the module to load each time.  Also, if you install a new kernel as an update, you'll have to re-build this module one more time.

---

### Post by andrude27 on 2012-12-29
thank you for your reply.  I have the rtl8192 loaded but it doesn't work.

---

### Post by andrude27 on 2012-12-29
I'm sorry I have the rtl8192cu module loaded

---

### Post by ahallubuntu on 2012-12-29
Can you give the output of the following commands please:

```
lsmod
```

and

```
lsusb
```

and

```
sudo lshw -C network
```

---

### Post by ahallubuntu on 2012-12-29
> **andrude27 said:**
> I'm sorry I have the rtl8192cu module loaded

Did you blacklist it so the new module, called "8192cu" gets loaded instead?

---

### Post by andrude27 on 2012-12-29
I need help blacklisting as the method I tried didn't work

---

### Post by ahallubuntu on 2012-12-29
You could add the three  module names I list in my link to the blacklist file, add 8192cu to /etc/modules, and reboot, or try this:

```
sudo modprobe -r rtl8192cu
sudo modprobe 8192cu
```

to see if it will work now.

---

### Post by ahallubuntu on 2012-12-29
> **andrude27 said:**
> I need help blacklisting as the method I tried didn't work

Please try to follow the instructions in the link I gave you:

[http://ubuntuforums.org/showthread.php?p=12318056#poststop](http://ubuntuforums.org/showthread.php?p=12318056#poststop)

To edit the blacklist file, try

sudo gedit /etc/modprobe.d/blacklist.conf

also

sudo gedit /etc/modules

---

### Post by andrude27 on 2012-12-29
I'm sorry but the computer in question is not connected to the internet.  I can tell you that , lsmod shows the rtl8192cu module loaded, and ls usb sees my dongle. And lshw _C network shows the dongle and the logical name wlan0 and the rtl8192cu driver and my kernal version 3.2.0.-35-generic-pae

---

### Post by ahallubuntu on 2012-12-29
> **andrude27 said:**
> I'm sorry but the computer in question is not connected to the internet.  I can tell you that , lsmod shows the rtl8192cu module loaded, and ls usb sees my dongle. And lshw _C network shows the dongle and the logical name wlan0 and the rtl8192cu driver and my kernal version 3.2.0.-35-generic-pae

As I said, you need to remove the rtl8192cu module (old one that doesn't work).  There are three modules you should blacklist as I indicate in the other post.  The new module is called simply "8192cu" .  If "rtl8192cu" is loaded, it's not going to work.

---

### Post by andrude27 on 2012-12-29
mo luck with the modprobe commands, I have already unzipped the folder so I can't unzip it again.  I'm missing something, please bear with me.

---

### Post by andrude27 on 2012-12-29
sorry I blacklisted per your instuctions with no success.

---

### Post by andrude27 on 2012-12-29
went to realtek to download the drivers but for some reason they won't download. I'll try again tomorrow going to bed, thanks for the help.

---

### Post by andrude27 on 2012-12-30
thank you ahallubuntu!  THe driver I had didn't work(from realtek).  I ended up downloading from an archlinux site and that driver works!  I 'm now connected. thanks again.:D

---

