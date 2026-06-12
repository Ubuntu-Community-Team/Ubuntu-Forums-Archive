---
title: "Radeon X300SE 128 PCI Express Driver"
date: 2005-12-04
forum: Multimedia &amp; Video
---

### Post by masingerz on 2005-12-04
Dear Forum:

I see a black frame around Ubuntu which indicates that there is aproblem with the driver, the current display is: 1024x768 85hz, I have a 17'' tube monitor:

I found this generic driver over at the ATI web
[https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=300](https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=300)

There are different versions: which one should I use?

XFree86 4.1
XFree86 4.2
XFree86 4.3
x.org 6.8

Please advice

Regards Masingerz

---

### Post by masingerz on 2005-12-04
Irc.freenode.org #ubuntu 

<bimberi> masingerz: on ubuntu breezy - x.org 6.8

It downloads an RPM file

---

### Post by WildTangent on 2005-12-04
You shouldn't use the ATI driver from their site, I heard it will break Ubuntu. Use the fglrx drivers. The easiest way to install them is from EasyUbuntu. Just search for it on the forum here, you should find the thread for it pretty easily.

-Wild

---

### Post by masingerz on 2005-12-05
when I tried to use fglrx I found myself with no gui, (luckyly fglrx made a backup), and an error message that gdm was not configured appropriatly, so i had to "sudo killall gdm" and "sudo mv xorg.conf.bak xorg.conf" and then "sudo gdm" and it worked: I have a gui now, I still want to have good display, but i do not want to suffer so much.

(the actual backup was called xorg.conf.2005101021213, but i put xorg.conf.bak for illustration purpose)

the thing that broke it:
[http://ubuntuforums.org/showthread.php?p=408111](http://ubuntuforums.org/showthread.php?p=408111)

sudo apt-get remove xorg-driver-fglrx
sudo apt-get remove linux-restricted-modules-$(uname -r)
sudo dpkg-reconfigure xserver-xorg #Select the ATI driver
I must have typed something wrong when configuring x server
---o---

the original problem was that I had a black square around the screen and I assumed that the resolution was bad, so i wanted a new driver, I had to go through all this hardship to then look at the existent config in winXP for display and I compared to ubuntu.

Ubuntu: 85hz
WinXP: 75hz

When I put ubuntu in 75hz the black frame went away...hahaha

thanks again "brunellus" #ubuntuforums irc.freenet.net for getting me out of no-gui situation in irssi

hahaha

-So 85hz is nicer than 75hz so i just put it back to 85hz and used the buttons in the screen to fill the black borders. no black borders anymore.

problem solved

ps: ill try 85hz in winxp too

---

