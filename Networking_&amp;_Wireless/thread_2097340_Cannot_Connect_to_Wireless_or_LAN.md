---
title: "Cannot Connect to Wireless or LAN"
date: 2012-12-22
forum: Networking &amp; Wireless
---

### Post by jradicle11 on 2012-12-22
I just installed Ubuntu alongside Windows 7. I had installed it once before on an old desktop and had no problem connected to the internet through Ethernet. My wireless adapter is a Broadcom 4322AG and I believe my NIC is a Realtek RTL8102E. I've read through the sticky pertaining to the Broadcom issues but still haven't been able to get it working. I definitely need more help.

My laptop is an HP Pavillion DV4

$ lspci | grep Broadcom
```
03:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)
```

$ lspci -n | grep '14e4:43'
```
03:00.0 0280: 14e4:432b (rev 01)
```

$ lsb_release -d
```
Description:	Ubuntu 12.10
```

$ uname -mr
```
3.5.0-17-generic x86_64
```

---

### Post by TOMBSTONEV2 on 2012-12-23
Refer to this: [http://ubuntuforums.org/showthread.php?t=2097033](http://ubuntuforums.org/showthread.php?t=2097033) I believe this will solve your problem. :) I have a Realtek RTL8188CE wireless network card, it would be great to have someone else to try what I'm saying. (I do not want to mess with my working internet) 

If it doesn't help at least we will have another mind on the subject. I don't think people should be robbed of the ubuntu experience just because they have a broadcom wireless network adapter.

---

### Post by jradicle11 on 2012-12-23
I tried your solution but it wouldn't work during the second part 

> Next move the file broadcom-wl-5.10.56.27.3_mipsel.tar.bz2 (download at " [http://mirror2.openwrt.org/sources/b...mipsel.tar.bz2](http://mirror2.openwrt.org/sources/b...mipsel.tar.bz2) ") to your home folder. Right click it and select extract. (Pretty much the same process as the last file)

In terminal type:
Code:
cd /home/your user name/broadcom-wl-5.10.56.27.3/driver
Type:
sudo make
Then

The link to the broadcom file is wrong because of all the "...'s" in there. I googled the file and downloaded what seems to be the exact same thing, but I guess that could be the error. When I type sudo make, nothing happens, just some error. Sudo make worked for the fwcutter file but not for this one.

Thank you for the response.

---

### Post by Pjotr123 on 2012-12-23
Try this roadmap:
[https://sites.google.com/site/easylinuxtipsproject/internet](https://sites.google.com/site/easylinuxtipsproject/internet)

---

### Post by TOMBSTONEV2 on 2012-12-23
Man, don't know how that happened I'll correct it.

[http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2](http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2) 

There's the link

Now, if you refer to: [http://ubuntuforums.org/showthread.php?t=2097033](http://ubuntuforums.org/showthread.php?t=2097033) in theory you may be able to get it working. Let me know the turn out. =)

---

### Post by Hadaka on 2012-12-23
Hi, here ya go.

```
sudo apt-get install linux-headers-generic
sudo apt-get install --reinstall bcmwl-kernel-source
sudo modprobe wl 
```

---

### Post by Open and Sourced on 2012-12-23
Maybe there is something more detrimental with your LAN settings. make sure to diagnose the problem with LAN or WiFi config. 

I wish you luck.  :popcorn:

---

### Post by jradicle11 on 2012-12-24
> **TOMBSTONEV2 said:**
> Man, don't know how that happened I'll correct it.

[http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2](http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2) 

There's the link

Now, if you refer to: [http://ubuntuforums.org/showthread.php?t=2097033](http://ubuntuforums.org/showthread.php?t=2097033) in theory you may be able to get it working. Let me know the turn out. =)

Same issue as before, unfortunately. Still no success.

> **Hadaka said:**
> Hi, here ya go.

```
sudo apt-get install linux-headers-generic
sudo apt-get install --reinstall bcmwl-kernel-source
sudo modprobe wl 
```

Not successful either. I copied the code for it:

```
jared@jared-HP-Pavilion-dv4-Notebook-PC:~/broadcom-wl-4.150.10.5/driver$ sudo apt-get install linux-headers-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package linux-headers-generic is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'linux-headers-generic' has no installation candidate
jared@jared-HP-Pavilion-dv4-Notebook-PC:~/broadcom-wl-4.150.10.5/driver$ sudo apt-get install --reinstall bcmwl-kernel-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package bcmwl-kernel-source:i386 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'bcmwl-kernel-source:i386' has no installation candidate
jared@jared-HP-Pavilion-dv4-Notebook-PC:~/broadcom-wl-4.150.10.5/driver$ sudo modprobe wl
FATAL: Module wl not found.

```

Looking back, maybe its because I wasn't in my home directory?

When I rebooted to switch back to Windows 7 so I could use the internet, chkdsk started. I notice that it "deleting index file in........" and listed broadcom and b43 drivers.

---

### Post by TOMBSTONEV2 on 2012-12-24
Well on the thread I referred you to, I solved tastypants same issue.

```
http://ubuntuforums.org/showthread.php?t=2097033
```

Follow directions in post 8, everything has been revised, proper files for proper terminal commands.

---

### Post by jradicle11 on 2012-12-24
> **TOMBSTONEV2 said:**
> Well on the thread I referred you to, I solved tastypants same issue.

```
http://ubuntuforums.org/showthread.php?t=2097033
```Follow directions in post 8, everything has been revised, proper files for proper terminal commands.

Got it working! Thank you! Now I just need to figure out how to install google chrome since what I tried didn't work... but that's for another topic.

---

### Post by TOMBSTONEV2 on 2012-12-24
I'm very glad to hear this, it makes it worth the effort when we get results.

---

