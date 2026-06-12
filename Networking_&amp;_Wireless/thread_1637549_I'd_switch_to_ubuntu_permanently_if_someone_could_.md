---
title: "I'd switch to ubuntu permanently if someone could help me get my wireless to work.."
date: 2010-12-04
forum: Networking &amp; Wireless
---

### Post by djackson75 on 2010-12-04
I love ubuntu, but I don't know how to use a command line to save my life. I'd just as soon never use a terminal ever. My big issue is I cannot get my wireless adapter to work. It is a keebox w150nu, which is based off the Ralink RT3070 chip. I am willing to use command line to get this thing to work because I love ubuntu to death, but everything I have tried has failed, and I need help.

Okay, I have gone to the Ralink website and downloaded the Tar.bz file from there, the file I grabbed is the third one down from the top:

[http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)

I have absolutely no idea what to do from there with the file however. Please understand that I have zero idea how to use command line in a terminal. Could someone PLEASE guide me through what I have to do to make this work?

If nobody can... Is there a usb wireless N  adapter that works straight away with ubuntu 10.10, as in I plug it in before the install, and it is immediately recognized and works immediately?

Thank you for any and all help.

---

### Post by northd_tech on 2010-12-04
We should probably make sure that you have Ralink 3070 hardware first.  Can you open a terminal (Applications > Accessories > Terminal) and post(copy&paste) the results of the following terminal commands:

```
lspci
lsusb
lsmod
lshw -C network
ifconfig
iwconfig
ndiswrapper -l
```For the Ralink 3070, chili555 posted a fix on this thread:
[http://ubuntuforums.org/showthread.php?t=1378782](http://ubuntuforums.org/showthread.php?t=1378782)

Here are some more that came up in a search here for Ralink 3070 (but chili's fix is probably the way to go):
[http://ubuntuforums.org/showthread.php?t=1353044&highlight=Ralink+RT3070](http://ubuntuforums.org/showthread.php?t=1353044&highlight=Ralink+RT3070)

[http://ubuntuforums.org/showthread.php?t=1598873](http://ubuntuforums.org/showthread.php?t=1598873)

---

### Post by walt.smith1960 on 2010-12-04
I can sympathize with your plight.  I have a Ralink 3572 adapter that has frustrated me big time.  I've found 2 USB WiFi N adapters that work.  The Netgear WNA1100 is single frequency/150Mbit device, the Trendet TEW-649UB is dual frequency/300Mbit.  Neither works out of the box but both can be made to function with minimal frustration.  The  NetGear WNA1100 doesn't work out of the box but I found a .deb file at sourceforge that works beautifully.  [http://sourceforge.net/projects/ath9k-htc/](http://sourceforge.net/projects/ath9k-htc/)  It's pretty simple to install--just download the .deb file, right click it and install with either Gdebi installer or through the Ubuntu Software Center then follow the instructions--it's a 2 step process.  The Netgear WNA1100 looks like it will work out of box with Ubuntu 11.04, it works now in the alpha1 release.

The second adapter I have that works with minimal frustration is a TrendNet TEW-649UB.  There's a bug report and fix here: [http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2620217.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2620217.html).  Be sure to download the correct firmware file.  You just have to download a file, extract it, create a new folder and copy or move the extracted file to the new folder and reboot.   If you don't want to use the command line to copy the firmware file.  you can use the command 'gsku nautilus' to open nautilus with sudo/root powers. Use with care!!!! but with superuser authorization you can create new folders and copy files with unrestricted permissions.  Good luck and I wouldn't be in too big a hurry to nuke Windows unless you can restore it if necessary.  I don't boot Windows often but sometimes it can be useful to verify whether hardware works etc.

---

