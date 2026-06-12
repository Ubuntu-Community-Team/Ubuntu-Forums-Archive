---
title: "ATI driver installer?"
date: 2006-01-09
forum: Multimedia &amp; Video
---

### Post by Dark Damo on 2006-01-09
What's a "super user" It wants you to be in? 

Anyway i'm reading through the readme tutorial thing and after i install i have to do some "flgrxconfig" command. and thats some really advanced stuff. Anyhoo do i have to play in any config files to set it up properly after the installer has done it?

Note: 	You must be logged in with super user privileges in order to successfully install the ATI Proprietary Linux driver.

Thanks in advance :)

---

### Post by Dark Damo on 2006-01-09
Anyone i need to know what a super user is?

---

### Post by ZarathustraDK on 2006-01-09
You simply need to write "sudo" (without the comments) in front of your commands in the terminal (means SuperUser DO).

example : sudo apt-get upgrade

---

### Post by Dark Damo on 2006-01-10
When i type sudo it gives me

> damo@OMG:~$ sudo /home/damo/Desktop/ATI drivers/ati-driver-installer-8.20.8-i386.run
Password:
sudo: /home/damo/Desktop/ATI: command not found
 

:confused:

---

### Post by Nrvnqsr on 2006-01-10
try to read from this thread:
[http://ubuntuforums.org/showpost.php?p=423584](http://ubuntuforums.org/showpost.php?p=423584)

if you gonna install any proprietary drivers,
first try to remove the drivers that came included with Ubuntu if any

> 
sudo apt-get remove xorg-driver-fglrx
sudo apt-get remove fglrx-control
sudo apt-get remove linux-restricted-modules-$(uname -r)
sudo dpkg-reconfigure xserver-xorg *#Select the ATI driver*


and in terminal, install these packages to compile the drivers, and the reason that your having command not found is that you forgot to have *sh* command bolded below. 
Also add the *--buildpkg Ubuntu/breezy* so that the installer can create packages only your OS.

> 
sudo apt-get install gcc-3.4 module-assistant build-essential fakeroot dh-make debconf libstdc++5 gcc-3.3-base
sudo **sh** ./ati-driver-installer-8.20.8-i386.run **--buildpkg Ubuntu/breezy**


and its should create 3 deb packages. and from there on follow the instructions and that should be all for the installation steps

---

### Post by Dark Damo on 2006-01-10
Thankyou i think the problem is solved ;)

---

