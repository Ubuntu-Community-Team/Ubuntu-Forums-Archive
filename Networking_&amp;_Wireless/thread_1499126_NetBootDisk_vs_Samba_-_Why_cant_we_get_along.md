---
title: "NetBootDisk vs Samba - Why cant we get along?"
date: 2010-06-01
forum: Networking &amp; Wireless
---

### Post by cdusseau on 2010-06-01
Howdy all, I'm new to this site, but I'm hoping I can find what I need here. 

Recently at my job we have been trying to replace our windows server with an Ubuntu server. The main function of that server is to host images for ghosting machines over the network. Currently we use the Universal TCP/IP Network BootDisk to boot into a windows share on the server which has the ghost.exe and images.

So far I have been able to setup the Ubuntu machine to allow for pxe and the loading of NetBootDisk over pxe. The problem I am running into is setting up a samba share that I can put ghost and the images onto. While I have set one up and can successfully access it from windows, I cannot logon onto it via the netbootdisk. I am able to logon using net logon with the appropriate username and password, but when I run:

net use g: //south-server/share

I consistently get a prompt saying i have an invalid password and to enter the correct password. I have tried every password i use on the system but I am denied no matter what.

I will be posting my config files later when I have a chance to access them.

So basically what I need to know is how to setup samba/netbootdisk to work together or if someone has an alternative method for booting via pxe to load ghost and its images please let me know.

Thanks!

---

### Post by pricetech on 2010-06-01
This may not be relevant to your case, but have you run smbpasswd on the server yet ??

Some kind of bug in Samba.  May or may not apply in your case, but easy enough to do.

---

### Post by hansdg1 on 2010-06-23
I have the exact same problem, and was wondering if you ever found a solution.  Basically I have an old Cent OS 2 box which has hosted our images, but the hardware is dying.  I want to replace it with the latest Ubuntu, however I can't get it to access the samba share.  It keeps asking me for a password, but none of the passwords on the machine work.  I even ran the smbpasswd and set it to the same password, but it doesn't work.

---

### Post by pauldeveth on 2011-03-08
Hi

 this one may be same problem as the following thread
[http://ubuntuforums.org/showthread.php?t=815382&highlight=samba+netbootdisk](http://ubuntuforums.org/showthread.php?t=815382&highlight=samba+netbootdisk)

---

