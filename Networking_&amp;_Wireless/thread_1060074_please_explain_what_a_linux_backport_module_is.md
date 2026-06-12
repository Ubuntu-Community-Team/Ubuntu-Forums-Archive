---
title: "please explain what a linux backport module is"
date: 2009-02-04
forum: Networking &amp; Wireless
---

### Post by moveright on 2009-02-04
I could not get my atheros card working and seeing as how I am a noob and totally could not figure out how to install "madwifi" I found this in another thread:
Here are the steps:

1- Disable the "Support for Atheros 802.11 wireless LAN cards" on Hardware Drivers, and reboot your box.
2- Once it is back on, open a Terminal, and type:
Code:

sudo aptitude install linux-backports-modules-intrepid-generic

It will ask your password, this is what it prints on screen, that is, what it will do:
Code:

esteban@tango:~/Desktop$ sudo aptitude install linux-backports-modules-intrepid-generic
[sudo] password for esteban: 
Reading package lists... Done
Building dependency tree 
Reading state information... Done
Reading extended state information 
Initializing package states... Done
The following NEW packages will be installed:
linux-backports-modules-2.6.27-7-generic{a} 
linux-backports-modules-intrepid-generic 
0 packages upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 1173kB of archives. After unpacking 3772kB will be used.
Do you want to continue? [Y/n/?]

When that is over (you'll get your prompt back), reboot, and enjoy the WiFi connection.

Can someone please explain to me what backport modules are, what they do, why I needed them and if possible, how to integrate that into my ISO so that the next time I install ubuntu I don't have to search the internet for that syntax to type in again to make my wifi card work.  

Also, it wouldn't hurt if someone explained to me how madwifi works, if it is the same thing that I did with the above command and if not, a way to install it or something so that if I ever install ubuntu again this will be easier for me.

thanks so much for the patience of all.

---

### Post by OrangeCrate on 2009-02-04
> **moveright said:**
> I could not get my atheros card working and seeing as how I am a noob and totally could not figure out how to install "madwifi" I found this in another thread:
Here are the steps:

1- Disable the "Support for Atheros 802.11 wireless LAN cards" on Hardware Drivers, and reboot your box.
2- Once it is back on, open a Terminal, and type:
Code:

sudo aptitude install linux-backports-modules-intrepid-generic

It will ask your password, this is what it prints on screen, that is, what it will do:
Code:

esteban@tango:~/Desktop$ sudo aptitude install linux-backports-modules-intrepid-generic
[sudo] password for esteban: 
Reading package lists... Done
Building dependency tree 
Reading state information... Done
Reading extended state information 
Initializing package states... Done
The following NEW packages will be installed:
linux-backports-modules-2.6.27-7-generic{a} 
linux-backports-modules-intrepid-generic 
0 packages upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 1173kB of archives. After unpacking 3772kB will be used.
Do you want to continue? [Y/n/?]

When that is over (you'll get your prompt back), reboot, and enjoy the WiFi connection.

**Can someone please explain to me what backport modules are, what they do, why I needed them** and if possible, how to integrate that into my ISO so that the next time I install ubuntu I don't have to search the internet for that syntax to type in again to make my wifi card work.  

Also, it wouldn't hurt if someone explained to me how madwifi works, if it is the same thing that I did with the above command and if not, a way to install it or something so that if I ever install ubuntu again this will be easier for me.

thanks so much for the patience of all.

[https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)

---

### Post by moveright on 2009-02-04
> **OrangeCrate said:**
> [https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)

yeah, I found that site right after I posted this...  anyhow, I read it and don't understand what how it all works.  so I guess I'd just like to know out of ALL those modules listed on the site for 8.10, which ones did my system install and what exactly was it that allowed my atheros 5k to work?  I guess what I am wondering is the fact that a fresh install of ubuntu leaves me only needing two drivers, the atheros and the nvidia so is there a way now that it all works to just copy the necessary data into the ISO image for super easy installation in the future?

---

### Post by stchman on 2009-02-04
Backport modules are simply stated additional kernel modules.  They did no make their way into the production kernel but can be backported in via a new repository.

---

### Post by moveright on 2009-02-04
> **stchman said:**
> Backport modules are simply stated additional kernel modules.  They did no make their way into the production kernel but can be backported in via a new repository.

so why does that have to be entered in at a shell prompt?  should that be included in the updates section of ubuntu?  I found that last night and it downloaded about 250 files.

oh, and I may have already asked this, can't remember but can I just separately download these modules and add them to the .iso?  effectively making it a more current install cd?

---

