---
title: "Atheros 5k Series with Wubi, Intrepid, Ubuntu"
date: 2009-01-08
forum: Networking &amp; Wireless
---

### Post by Ratattuta on 2009-01-08
Hello. I hope this topic is in the right place. And I am sorry if I sound like an annoying noob or the topic was already addressed. I did search the forum and could not find anything. My question is this. I have a Toshiba satellite A215-24757 Laptop and I have installed Ubuntu 8.10 Intrepid Ibex on it with Wubi. Now from browsing the forums it seems I have an Atheros 5k card (5006 or 5007) and I need the ath5k module from linux-backports-modules-intrepid. Problem is I cannot find that package. I also tried
```
$ sudo -i
$ echo "blacklist ath_pci" >> /etc/modprobe.d/blacklist
$ rmmod ath_pci
$ apt-get install ndiswrapper-utils-1.9 ndiswrapper-common
$ ndiswrapper -i net5211.inf
$ ndiswrapper -l
look for something like this:
net5211 : driver installed
device (168C:001C) present (alternate driver: ath_pci)
$ modprobe ndiswrapper
$ echo "ndiswrapper" >> /etc/modules
```
from [here]("http://knol.google.com/k/drew-withers/ubuntu-linux-810-on-toshiba-satellite/36kyj1id6r02z/5#") but when I got to rmmod ath_pci it said it could not find ath_pci. Can someone please help me or redirect me to a source of help? Thank you.

---

### Post by Ratattuta on 2009-01-08
Okay I tried to manually install linux-backports-modules-intrepid-generic but no avail. This is what it says:
```

:~/Desktop$ sudo dpkg -i linux-backports-modules-intrepid-generic_2.6.27.9.13_amd64.deb
(Reading database ... 99182 files and directories currently installed.)
Preparing to replace linux-backports-modules-intrepid-generic 2.6.27.9.13 (using linux-backports-modules-intrepid-generic_2.6.27.9.13_amd64.deb) ...
Unpacking replacement linux-backports-modules-intrepid-generic ...
dpkg: dependency problems prevent configuration of linux-backports-modules-intrepid-generic:
 linux-backports-modules-intrepid-generic depends on linux-backports-modules-2.6.27-9-generic; 
however:
Package linux-backports-modules-2.6.27-9-generic is not installed.
dpkg: error processing linux-backports-modules-intrepid-generic (--install): dependency problems - leaving unconfigured
Errors were encountered while processing: linux-backports-modules-intrepid-generic
:~/Desktop$
```
But apparently it partially install so I tried this:
```
:~$ sudo apt-get install linux-backports-modules-intrepid
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-backports-modules-intrepid
:~$ 
```
Does anybody know what's wrong?

---

### Post by moveright on 2009-02-04
I am a noob and juts conquered this problem last night.

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

If that doesn't work, ask someone who knows what they are talking about :)

---

### Post by Philo1 on 2009-02-15
Hey "moveright" thanks for the input on how you got your wifi to work. I purchased a CQ60 Presario (32-bit) around a week ago. I had quite a few issues with just installing 8.10 by itself. Today I resolved to doing a dual boot with Vista. This is working out quite well. Either way, after I ran "sudo aptitude install linux-backports-modules-intrepid-generic" command it all panned out. After I rebooted, I had a gui to work with, not bad at all. As you mentioned though, I was not prompted to reboot, just a heads up for anyone else who reads this thread.

---

