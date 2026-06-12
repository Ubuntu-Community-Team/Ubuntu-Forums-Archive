---
title: "Dell Wireless 1540 not found"
date: 2013-02-24
forum: Networking &amp; Wireless
---

### Post by whippetboy on 2013-02-24
G'day.

First, sorry if this has been posted elsewhere. I have a Dell E5530 that I have installed Ubuntu 12.04 on. I cannot connect to wireless networks. It seems it does not register the wireless card (Dell Wireless 1540 (802.11 a/b/g/n) Half Mini). Is anyone able to please tell me how to fix this if you know? Thanks so much for your time!

Dan

---

### Post by Hadaka on 2013-02-24
Hi,please post the output of..

```
lspci -nn | egrep '0200|0280' 
```

thanks

---

### Post by whippetboy on 2013-02-26
G'day.

The output was:
0:200.0 Network controller [0280]: Broadcom Corporation BCM43228 802.11a/b/g/n [14e4:4359]
0c:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5761 Gigabit Ethernet PCIe [14e4:1681] (rev 10)

I guess that means it CAN register them but can't make them work?? I'm a bit out of touch with this stuff sorry... I hope that's what you needed. Thanks for your help!

Dan

---

### Post by Hadaka on 2013-02-26
Hi, sorry i am so late getting back to you
please do...

```
sudo apt-get install linux-headers-generic
sudo apt-get install --reinstall bcmwl-kernel-source
sudo modprobe wl
 
```

thanks

---

### Post by whippetboy on 2013-02-26
Hi again, Hadaka.

No need for apologies! I'm in no rush really :)..

I did what you said and all was ok until the final command line:

 dgraham@dgraham-Latitude-E5530-non-vPro:~$ sudo apt-get install linux-headers-generic
  [sudo] password for dgraham: 
  Reading package lists... Done
  Building dependency tree       
  Reading state information... Done
  E: Unable to locate package linux-headers-generic
  dgraham@dgraham-Latitude-E5530-non-vPro:~$ sudo apt-get install --reinstall bcmwl-kernel-source
  Reading package lists... Done
  Building dependency tree       
  Reading state information... Done
  E: Unable to locate package bcmwl-kernel-source
  dgraham@dgraham-Latitude-E5530-non-vPro:~$ sudo modprobe wl
  FATAL: Module wl not found.
  dgraham@dgraham-Latitude-E5530-non-vPro:~$ 
  

Dan

---

### Post by praseodym on 2013-02-26
Hi,

you need a cable connection for these commands. Alternatively, the packages are located on the cd in **~/pool/main/**, sorted alphabetically. You need
[LIST]
[*]dkms
[*]linux-headers-generic
[*]bcmwl-kernel-source
[*]patch
[*]fakeroot
[/LIST]
plus the kernel header files suitable for your kernel. Check with
```

uname -r
```
Save them in "Downloads" and install them via
```

sudo dpkg -i ~/Downloads/*.deb
```

---

### Post by Hadaka on 2013-02-26
Hi, yes that is correct, you need to load connected
to the internet.

---

### Post by whippetboy on 2013-02-26
Hi, guys.

I did have the network cable plugged in and it does recognise a network but doesn't pick up any internet or file access through it (??). I can't actually do the command while connected tot he internet as connecting to the internet is the issue I'm trying to resolve. Thanks and sorry for my ignorance - I'm just getting started after some long years away using Windows...

Dan

---

### Post by whippetboy on 2013-02-26
So praseodym, I can get those files from the bootable USB I created to install ubuntu? Is that what you mean? If so, where do I put them on the main drive so they register? Thanks!
Dan

---

### Post by Hadaka on 2013-02-26
Hi Dan, you could also click the cog wheel...system settings...then additional drivers
your driver "may" be there. Also be sure to get all the updates since you have a
new install.
to get them.. please do...

```
sudo apt-get update
sudo apt-get upgrade 
```

thanks

---

