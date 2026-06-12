---
title: "Using a talk talk router to share files between computers"
date: 2010-11-02
forum: Networking &amp; Wireless
---

### Post by electric-wildflower on 2010-11-02
Hey guys i have recently become interested in networking easier way of sharing files than using a usb pen drive. here is the situation my gf has a tower system in the spare room which i wanna use as a server basicly a place for her to store audio, video etc and a xbox in the living room also her laptop and i wanted to find a cheap router that would let me share stuff between the three.

I have recently got my hands on a talk talk router free from a friend and was wondering would it be enough to just plug in and use the wireless + ethernet to connect all 3 devices or would it be better to buy another router i am try to save as much hassle as i can.

not interested in using it to share internet as she uses mobile broadband just a cheap way of sharing files.

will this be enough thanks in advance. :guitar:

---

### Post by Boondoklife on 2010-11-02
This would depend on the router, if the wireless and wired clients are all bridged then yes it should (this also assumes your router does not have some crazy firewall going on). I would just try to plug in two devices and try to ping each other. If it works then try to share files.

---

### Post by drdos2006 on 2010-11-02
The shared directory is “/media/sdb1/sdb1-shared” on the server.
It is easier to set the server IP address to a fixed IP, the server can also be Ubuntu desktop version.
For Ubuntu 10.10 64bit.

NFSv4 server

Install the required packages... 
# apt-get install nfs-kernel-server nfs-common
Modify /etc/defaults/nfs-kernel-server with:
NEED_SVCGSSD=no # no is default
Modify /etc/defaults/nfs-common with:
NEED_IDMAPD=yes
NEED_GSSD=no # no is default

To export our directories to a local network 192.168.0.0/24 
we add the following line to /etc/exports 
/media/sdb1/sdb1-shared 192.168.0.0/24(rw,fsid=0,insecure,no_subtree_check,async) */ all on the one line of course */
and restart the service with:
sudo  /etc/init.d/nfs-kernel-server restart or reboot the server to allow NFS to change the permissions of the shared directory.

Change the permissions of /media/sdb1/sdb1-shared to allow read/write.

NFSv4 client
Install the required packages... 
# apt-get install nfs-common 
The client needs the same changes to /etc/default/nfs-common to connect to an NFSv4 server. 
In /etc/default/nfs-common we set: 
NEED_IDMAPD=yes
NEED_GSSD=no # no is default
From a terminal, create a new directory with:
sudo mkdir /media/sdb1-shared
Mount the shared directory with:
sudo mount <server-IP-address>:/media/sdb1/sdb1-shared  /media/sdb1-shared


regards

---

