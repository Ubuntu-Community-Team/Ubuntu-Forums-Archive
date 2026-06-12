---
title: "Unable to connect to wifi-device not ready(firmware missing)"
date: 2011-06-17
forum: Networking &amp; Wireless
---

### Post by collegian on 2011-06-17
Hello All,

I tried to implement the solution given at: [http://ubuntuforums.org/showthread.php?t=1780744](http://ubuntuforums.org/showthread.php?t=1780744) on a Dell Inspiron 1525 laptop, running Ubuntu 11.04. However, I still can't connect to wifi.

I can see that the files were extracted inside /lib/firmware/ (I see a b43 and a b43 legacy folder). 

The lspci -vnn | grep 14e4 returns:


```
0b:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01) 
```Please give your suggestions. Thanks!

---

### Post by Toz on 2011-06-17
How about trying these instructions? [http://ubuntuforums.org/archive/index.php/t-1742147.html]("http://ubuntuforums.org/archive/index.php/t-1742147.html")

---

### Post by collegian on 2011-06-17
> **Toz said:**
> How about trying these instructions? [http://ubuntuforums.org/archive/index.php/t-1742147.html]("http://ubuntuforums.org/archive/index.php/t-1742147.html")

Thanks for the reply. Do I need to create a live CD for this or is there a folder named Ubuntu 11.04 i386? I installed Ubuntu via Windows 7 using the Ubuntu Windows Installer.

---

### Post by Toz on 2011-06-17
Do you have a live wired network connection in Ubuntu? If so, you should be able to run these commands:
```
sudo apt-get install dkms
sudo apt-get install bcmwl-kernel-source
```
Then restart your computer.

If not, you'll have to get those files somehow (extract from iso file in Windows), copy them to a usb key, startup ubuntu and get them from the key.

EDIT: In the link, he lists the second file as **bc,wl-kernel-source_5.100.82.38+bdcom-0ubuntu3_i386.deb** when it is really called **bcmwl-kernel-source_5.100.82.38+bdcom-0ubuntu3_i386.deb** (m not ,)

---

### Post by superduperlinuxperson on 2011-06-17
my own driver is bcm4312, and i have got it working by doing these steps:
step 1: download these two things from here:[http://downloads.openwrt.org/sources...a-3.130.20.0.o](http://downloads.openwrt.org/sources...a-3.130.20.0.o) and [http://mirror2.openwrt.org/sources/b...0.10.5.tar.bz2](http://mirror2.openwrt.org/sources/b...0.10.5.tar.bz2)
step 2: extract the second one to your home folder, and copy the other one their too
step 3: download b43-fwcutter from the software center
step 4: execute these steps in terminal too get it working:

~$ sudo b43-fwcutter -w /lib/firmware wl_apsta-3.130.20.0.o
~$ sudo b43-fwcutter --unsupported -w /lib/firmware broadcom-wl-4.150.10.5/driver/wl_apsta_mimo.o

---

### Post by superduperlinuxperson on 2011-06-17
oh and here is the link: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

### Post by collegian on 2011-06-17
> **superduperlinuxperson said:**
> my own driver is bcm4312, and i have got it working by doing these steps:
step 1: download these two things from here:[http://downloads.openwrt.org/sources...a-3.130.20.0.o](http://downloads.openwrt.org/sources...a-3.130.20.0.o) and [http://mirror2.openwrt.org/sources/b...0.10.5.tar.bz2](http://mirror2.openwrt.org/sources/b...0.10.5.tar.bz2)
step 2: extract the second one to your home folder, and copy the other one their too
step 3: download b43-fwcutter from the software center
step 4: execute these steps in terminal too get it working:

~$ sudo b43-fwcutter -w /lib/firmware wl_apsta-3.130.20.0.o
~$ sudo b43-fwcutter --unsupported -w /lib/firmware broadcom-wl-4.150.10.5/driver/wl_apsta_mimo.o

Thanks for the reply.However, those 2 links are not working(give 404 error). Also, I am unable to connect to wired internet so probably can't continue till I figure that out.

---

### Post by superduperlinuxperson on 2011-06-17
horribly sorry, iam trying to find the link now

---

### Post by superduperlinuxperson on 2011-06-17
new instructions:
download from here:   [http://www.omattos.com/sites/default...all-fw.tar_.gz]("http://www.omattos.com/sites/default/files/b43-all-fw.tar_.gz")
now, take the two folders in the link and extract them into lib/firmware/

---

### Post by collegian on 2011-06-17
> **superduperlinuxperson said:**
> new instructions:
download from here:   [http://www.omattos.com/sites/default...all-fw.tar_.gz]("http://www.omattos.com/sites/default/files/b43-all-fw.tar_.gz")
now, take the two folders in the link and extract them into lib/firmware/

Is that it or I still need to run any more commands? Also, it seems like the same file which I already extracted in first place :(

---

### Post by collegian on 2011-06-18
> **Toz said:**
> Do you have a live wired network connection in Ubuntu? If so, you should be able to run these commands:
```
sudo apt-get install dkms
sudo apt-get install bcmwl-kernel-source
```Then restart your computer.

If not, you'll have to get those files somehow (extract from iso file in Windows), copy them to a usb key, startup ubuntu and get them from the key.

EDIT: In the link, he lists the second file as **bc,wl-kernel-source_5.100.82.38+bdcom-0ubuntu3_i386.deb** when it is really called **bcmwl-kernel-source_5.100.82.38+bdcom-0ubuntu3_i386.deb** (m not ,)


Thanks,that worked! :)

---

