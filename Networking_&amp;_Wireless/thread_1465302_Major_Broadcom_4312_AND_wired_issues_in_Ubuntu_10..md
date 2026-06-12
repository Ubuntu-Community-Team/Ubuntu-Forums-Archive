---
title: "Major Broadcom 4312 AND wired issues in Ubuntu 10.04"
date: 2010-04-29
forum: Networking &amp; Wireless
---

### Post by zoolove on 2010-04-29
I installed Ubuntu 10.04 on my HP dv4-1225dx today, and of course thanks to my broadcom card I have no wireless.  In addition to that, I have no wired.  Also, no drivers are showing up in my proprietary drivers.  I live on a college campus that requires you to install Bradford Persistent Agent before you can go online, and I'm not able to do this with even a wired connection.  I had these same problems with 9.10, which is why I had to leave Linux for Windows Vista...very sad.  I would like to get this fixed if possible since Vista is just painful to work with.  With lspci my card is Broadcom Corporation BCM4312 802.11b/g (rev 01).

Any help will be majorly appreciated!

---

### Post by snowpine on 2010-04-29
Welcome to the forums! It is not a "problem" with Ubuntu; Broadcom does not release their driver as open-source, and so Ubuntu cannot legally include it. 

It's really easy to install, though, check it out: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

### Post by zoolove on 2010-04-29
Most of those commands do not work unless you have some other internet connection going such as ethernet.  I tried installing the package from the install CD and got an error message that said Error: Dependency is not satisfiable: dkms.

---

### Post by zoolove on 2010-04-29
Bump?

---

### Post by snowpine on 2010-04-29
> **zoolove said:**
> Most of those commands do not work unless you have some other internet connection going such as ethernet.  I tried installing the package from the install CD and got an error message that said Error: Dependency is not satisfiable: dkms.

Can you try booting from a live CD and seeing if this works?

```
sudo modprobe -r b43 ssb wl
sudo modprobe wl
```

Does that get your wireless working in Live mode?

If you read a little further down the page I linked to, you'll see there are several options for installing without internet access: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#No%20internet%20access](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#No%20internet%20access)

It is possible that the instructions might not quite be up to date for the 10.04 release, which, as you know, just came out today. If you find the documentation is lacking, you may need to wait a couple of days for it to be updated. :(

---

### Post by ublintu on 2010-04-29
Hi,
This was working for me in 9.10 :
[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)
[http://ubuntuforums.org/showthread.php?t=1288865](http://ubuntuforums.org/showthread.php?t=1288865)
Maybe is still ok in 10.04... I don't know, because I'm still in 9.10.

---

### Post by powerslave12r on 2010-04-29
I tried most of the stuff mentioned for 9.10 regarding this for 10.04, to no avail.

Had to connect through ethernet and one command fixed it:

```
sudo apt-get install b43-fwcutter
```

---

### Post by RebeccaWebDiva on 2010-05-06
I'm running Ubuntu 10.04 with a Broadcom 4312.  This is what I did to get it working:
 

 	Code:
 	sudo apt-get install ndisgtk 
 

Reboot, then:

 	Code:
 	sudo apt-get install b43-fwcutter 
Reboot again.  Worked like a charm.  Wireless light came on for the first time and automatically connected to my wireless network.  I hope this helps.

---

### Post by musketballdan on 2010-11-11
I've come across a different problem, the B4312 LP-PHY card I have is also on the Ethernet port. When you attach an Ethernet cable, the network does not automatically connect. It's dead!

Wireless works great, but where the hell has the cable connection gone?

This is on 10:10 Maverick and as to broadcom not releasing the drivers, they made those drivers open source ages ago! :P

---

### Post by jchw on 2011-01-24
I just tried to fix this problem by reinstalling b43-fwcutter without succes. It came up with the following errors and still no wifi!


ohn@john-eMachines-E525:~$ sudo apt-get install b43-fwcutter
[sudo] password for john: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
b43-fwcutter is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 13 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up firmware-b43-installer (4.150.10.5-4) ...
Not supported low-power chip with PCI id 14e4:4315!
Aborting.
dpkg: error processing firmware-b43-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 firmware-b43-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)
john@john-eMachines-E525:~$ 

I am not sure what to try after this.

---

