---
title: "Netgear WNA 3100 disappeared"
date: 2012-08-22
forum: Networking &amp; Wireless
---

### Post by Zammael on 2012-08-22
After following the instructions I installed the proper drivers and ndiswrapper program, etc., a month ago. 

But last night I updated to the latest distro and this broke my system: it can no longer detect my wireless USB adapter. 

The blue light works but there's no connexion between the system and the USB adapter. I've tried several different workin USB ports to no avail. When I type sudo ndiswrapper I get a fatal module. When I check the ndiswrapper program it says. I hardware is detected. I use the driver from  netgear - bcmwlhigh5.inf

Since this is a month old USB it can't be the adapter. Is there something I'm missing? Should I revert to older kernels and leave the more recent ones alone?  3.2.0-29-generic is the latest I have. 

I use Ubuntu 12.04 LTS
Netgear N600 wireless dual band USB adapter 
(WNDA3100)
Thanks in advance.

---

### Post by Zammael on 2012-08-22
More bad news: after trying to install windows drivers in the ndiswrapper, both the bcmn43xx32 that originally worked, and the bcmwlhigh5 driver that's originally from the Netgear zip file for USB WNDA3100, they both are now marked with a giant red X as "invalid driver!" 

Ay Caramba.

---

### Post by Zammael on 2012-08-22
Update: I removed both .inf files and reinstalled the bcmwlhigh5.inf. 
The good news? Ndiswrapper says hardware is present. 
So I ran the terminal to confirm this with lsusb:```

Bus 008 Device 003: ID 0846:9011 NetGear, Inc. WNDA3100v2 802.11abgn [Broadcom BCM4323]

```

But that didn't solve the problem. Help?

---

### Post by Zammael on 2012-08-22
I connected my desktop PC with an Ethernet cable for the nonce. Typing in the usual suspects spits out the following:

```

gendo@gendo-desktop:~$ iwconfig
lo        no wireless extensions.

eth2      no wireless extensions.

gendo@gendo-desktop:~$ lsusb
Bus 004 Device 002: ID 1532:0001 Razer USA, Ltd RZ01-020300 Optical Mouse [Diamondback]
Bus 008 Device 003: ID 0846:9011 NetGear, Inc. WNDA3100v2 802.11abgn [Broadcom BCM4323]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
gendo@gendo-desktop:~$ lsusb
Bus 004 Device 002: ID 1532:0001 Razer USA, Ltd RZ01-020300 Optical Mouse [Diamondback]
Bus 008 Device 003: ID 0846:9011 NetGear, Inc. WNDA3100v2 802.11abgn [Broadcom BCM4323]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
gendo@gendo-desktop:~$ sudo modprobe ndiswrapper
[sudo] password for gendo: 
FATAL: Module ndiswrapper not found.
gendo@gendo-desktop:~$ cd Desktop/wna3100-drivers
gendo@gendo-desktop:~/Desktop/wna3100-drivers$ sudo modprobe -r ndiswrapper
FATAL: Module ndiswrapper not found.

```

Thanks in advance! ):P

---

### Post by chili555 on 2012-08-22
> [sudo] password for gendo: 
FATAL: Module ndiswrapper not found.Please try:```
sudo apt-get install ndiswrapper-dkms
sudo modprobe ndiswrapper
```Any improvement?

---

### Post by Zammael on 2012-08-22
> **chili555 said:**
> Please try:```
sudo apt-get install ndiswrapper-dkms
sudo modprobe ndiswrapper
```Any improvement?

Hello Chili555 :)

I tried your suggestions and here are the results:

```
gendo@gendo-desktop:~$ sudo apt-get install ndiswrapper-dkms
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ndiswrapper-dkms is already the newest version.
The following packages were automatically installed and are no longer required:
  nvidia-settings-updates libllvm3.0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
gendo@gendo-desktop:~$ sudo modprobe ndiswrapper
FATAL: Module ndiswrapper not found.

```
:confused:

---

### Post by chili555 on 2012-08-22
Please try:```
sudo apt-get install --reinstall ndiswrapper-common
sudo apt-get install --reinstall ndiswrapper-utils-1.9
sudo modprobe ndiswrapper
```I hope we don't have to go to sudo apt-get install big hammer.

---

### Post by Zammael on 2012-08-22
Reinstalled both common & utils 1.9.... 

Alas, the results are the same, even including Big Hammer ;) 

```
gendo@gendo-desktop:~$ sudo modprobe ndiswrapper
FATAL: Module ndiswrapper not found.
gendo@gendo-desktop:~$ sudo apt-get install big hammer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package big
E: Unable to locate package hammer
gendo@gendo-desktop:~$ 

```:(

---

### Post by Zammael on 2012-08-22
Update: I have both drivers installed in the ndiswrapper application - bcmn43xx64 and bcmwlhigh5 - and they both say "hardware present: yes" 

Where do I go from here?
](*,)

---

### Post by chili555 on 2012-08-22
](*,) Indeed! I am getting low on skill/mojo/ideas and, especially, patience with this long-standing bug. [/RANT]

Ok, now that I have re-composed myself, let's try to reinstall dkms:```
sudo apt-get install --reinstall ndiswrapper-dkms
sudo apt-get install --reinstall dkms
sudo modprobe ndiswrapper
```**sigh**

---

### Post by Zammael on 2012-08-22
Chili555, thanks for the help. Here are the results:

```
DKMS: uninstall completed.

------------------------------
Deleting module version: 1.57
completely from the DKMS tree.
------------------------------
Done.
Unpacking replacement ndiswrapper-dkms ...
Setting up ndiswrapper-dkms (1.57-1ubuntu1) ...
Loading new ndiswrapper-1.57 DKMS files...
Building only for 3.5.0-10-generic
Building initial module for 3.5.0-10-generic
ERROR (dkms apport): kernel package linux-headers-3.5.0-10-generic is not supported
Error! Bad return status for module build on kernel: 3.5.0-10-generic (i686)
Consult /var/lib/dkms/ndiswrapper/1.57/build/make.log for more information.
gendo@gendo-desktop:~$ sudo apt-get install --reinstall dkms
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  nvidia-settings-updates libllvm3.0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 73.1 kB of archives.
After this operation, 0 B of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu/ precise/main dkms all 2.2.0.3-1ubuntu3 [73.1 kB]
Fetched 73.1 kB in 0s (132 kB/s)
(Reading database ... 398788 files and directories currently installed.)
Preparing to replace dkms 2.2.0.3-1ubuntu3 (using .../dkms_2.2.0.3-1ubuntu3_all.deb) ...
Unpacking replacement dkms ...
Processing triggers for man-db ...
Setting up dkms (2.2.0.3-1ubuntu3) ...
gendo@gendo-desktop:~$ sudo modprobe ndiswrapper
FATAL: Module ndiswrapper not found.

```

---

### Post by Zammael on 2012-08-22
From the code, it seems to me that there's a "bad return status" for the module build on kernel 3.5.0-10-generic. That might be the fly in the soup. 

The second sudo apt-get install --reinstall dkms works fine, but the modprobe doesn't work. 

Is the module build of kernel 3.5.0-10-generic the culprit? :evil:

---

### Post by chili555 on 2012-08-22
> **Zammael said:**
> From the code, it seems to me that there's a "bad return status" for the module build on kernel 3.5.0-10-generic. That might be the fly in the soup. 

The second sudo apt-get install --reinstall dkms works fine, but the modprobe doesn't work. 

Is the module build of kernel [COLOR="Red"]3.5.0-10-generic[/COLOR] the culprit? :evil:Yes, indeedy! I'm quite certain that if you fall back to 3.2.xx you'll be working fine. I suspect that the ndiswrapper suite built for Ubuntu is not quite yet fine-tuned for 3.5.xx kernels.

You (read: we) could try to compile the tarball if you're feeling lucky.

[http://sourceforge.net/projects/ndiswrapper/files/stable/](http://sourceforge.net/projects/ndiswrapper/files/stable/)

---

### Post by Zammael on 2012-08-22
I'm going to try that new version before I revert to an earlier kernel (how do you do that without screwing up?) 

Thanks!

---

### Post by Zammael on 2012-08-22
That new ndiswrapper 1.58rc1 did the trick. :)

I followed the steps here:

[http://bbs.archbang.org/viewtopic.php?pid=17440#p17440](http://bbs.archbang.org/viewtopic.php?pid=17440#p17440)

Please share this post with others whose Ndiswrapper may be broken in the new update/kernel. 
:guitar:

Thanks for your patience, Chilli555!

---

### Post by Zammael on 2012-09-02
I've bad news, everyone. 

Each time I update the Ubuntu software, it breaks the ndiswrapper module. 

I have to go back to the instructions in the link in my previous post to re-install the ndiswrapper and re-compile the module. 

So my only solution from now on is to keep a copy of those instructions handy and the ndiswrapper files nearby. 

Ay Caramba! ](*,)

---

### Post by chili555 on 2012-09-03
That's the way compiled from source modules work; they are compiled against your running kernel version only. When Update Manager installs a later kernel, you must recompile. The preferred method is:```
cd Desktop/ndiswrapper-1.58rc1 [COLOR="Red"]<--or wherever you extracted the files[/COLOR]
[COLOR="Red"]make clean[/COLOR]
make
sudo make install
sudo modprobe ndiswrapper
```

---

### Post by Zammael on 2012-09-03
Thanks, Chilli555. 

When will Ndiswrapper release a version that won't break with each update? 

My options are:

*Recompile the module after each update.*
or...
*Don't update. *
](*,)

---

### Post by chili555 on 2012-09-03
> When will Ndiswrapper release a version that won't break with each update? Uhhh, never. That's how compiled from source tarballs work; they build a module for your running kernel version.

It doesn't break with every update, it needs to be recompiled for each updated *kernel*. If that's not your experience, something else is wrong and please post back.

It is quite likely that Ubuntu will release a .deb package that works automagically; when that will be is unknown to me. You do know, however, that the current built-in version 1.57 doesn't work properly with your kernel.

Is it really so hard to run a few commands after an updated kernel and a reboot? I always thought compiling from source was like shaving. A gentleman does so carefully at least once a day.

---

