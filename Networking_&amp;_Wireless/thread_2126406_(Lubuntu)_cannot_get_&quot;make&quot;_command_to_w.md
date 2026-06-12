---
title: "(Lubuntu) cannot get &quot;make&quot; command to work (missing headers and more)"
date: 2013-03-17
forum: Networking &amp; Wireless
---

### Post by maymarie on 2013-03-17
Allrighty here's what I've got: A old dell dimension 2400 2.7Ghz intel centron and 746meg of ram.... yeah it's old.... Ok not problem. Here's my issue. I have the machine currently setup to boot ubuntu 12.04 and after a little digging I figured out how to install ndiswrapper and get it online. However ubuntu seems a little "heavy" for this old machine. so I look around for a lighter weight OS. I download Lubuntu 12.10 install to dual boot with the current os and here my problems begin. I dont have access at home to anything but wireless (unless I drag my comp to my neighbors and hook up there) and aperently one of the ways lubuntu is lighter is that some files are not installed. correct me of I'm wrong. I've looked around many forum posts and I'm hearing "ethernet cable" and sudo apt-get these files so far what I found I'm missing are as follows: the "make" file ( think I fixed that but...) I also need the build-essential files and the co-dependants and linux generic headers and also its dependants. I'm new to this and feel like I'm missing a resorce here... Like the install disk may have some of the "missing parts" on it and I simply need to be pointed in the right direction. Btw the way I tried Installing the above mentioned files (downloaded earlier and stored on usb) but without the dependant files they can't install. and help or more info anyone needs to help solve this and to teach me more about this OS will be provided ASAP.
Thanks Mayu

---

### Post by oldos2er on 2013-03-17
Moved to Networking & Wireless.

Check the sticky [here]("http://ubuntuforums.org/showthread.php?t=885847"). It would help to know the make/model of your wireless device.

---

### Post by maymarie on 2013-03-17
Thanks Ann. the wireless USB adaptor I'm using is a netgear wna3000 it has a broadcom chipset (43XX series) i do have drivers for it. however I cannot excute any sort of commands in the lubuntu 12.10 terminal to install ndiswrapper or the drivers. that has been the way Ive installed it on unbuntu 12.04 and now as we speak I'm running a xubuntu 12.04 live cd and it works from there.

---

### Post by maymarie on 2013-04-02
Ok so I figured out my problem. :D I was looking at this issue with a bit of a windows troubleshooting mind I guess.... I needed to simply read the error codes on screen a bit more closely. Here was my solution if anyone else (newbie like me) has issues installing ndiswrapper. Solution works for K and L ubuntu variants. Pull up terminal. "sudo apt-get install make" let this run "sudo apt-get install gcc" then for me I installed ndiswrapper and my wifi adapter driverfrom my usb drive. (no errors now)!!!! add a "modprobe ndiswrapper" line and pick your wifi router from list connect from there. add a ndiswrapper -m command and it will stick after reboots. grins I feel stupid. and smart. thanks for that.

---

