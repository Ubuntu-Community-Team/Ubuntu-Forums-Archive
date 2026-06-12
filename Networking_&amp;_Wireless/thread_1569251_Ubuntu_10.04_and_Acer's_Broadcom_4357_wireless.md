---
title: "Ubuntu 10.04 and Acer's Broadcom 4357 wireless"
date: 2010-09-06
forum: Networking &amp; Wireless
---

### Post by Dittie on 2010-09-06
I went nuts trying to figure out why I couldn't get my wireless working for my new acer aspire laptop. I have an Aspire 7551G-5407 with the Broadcom 4357 wireless and Broadcom ethernet.

I tried all of the things I could find here and through searching google with no luck. I installed ndiswrapper via .deb packages and compiled source. Ndiswrapper would load fine, and it would show that there was a card, but the driver wouldn't accept it, no matter what I did. I even tried wicd. Nothing worked. I was about to give up.

'lshw -C network' would display: 
>  
*-network UNCLAIMED       
description: Network controller       
product: Broadcom Corporation       
vendor: Broadcom Corporation       
physical id: 0       
bus info: pci@0000:06:00.0       
version: 01      
width: 64 bits       
clock: 33MHz       
capabilities: bus_master cap_list      
configuration: latency=0       
resources: memory:d0200000-d0203fff

Even after checking to make sure the driver was installed:
> 
ndiswrapper -l
bcmwl6 : driver installed	
device (14E4:4357) present

After installing wicd, no wireless would show up, still. It just wasn't accepting the driver. You basically have to have the STL proprietary driver for this to work.

I connected via wired network, installed the proprietary driver, uninstalled ndiswrapper and kept wicd. Rebooted and then set up the wireless. It was that simple, and after banging my head off the keyboard for a day and a half, it finally clicked that I did have the wired eth0 working :P

Hope this saves time for anyone else trying to fix their 4357 wireless.

---

### Post by wyt168 on 2011-06-17
> **Dittie said:**
> 

After installing wicd, no wireless would show up, still. It just wasn't accepting the driver. You basically have to have the STL proprietary driver for this to work.

I connected via wired network, installed the proprietary driver, uninstalled ndiswrapper and kept wicd. Rebooted and then set up the wireless. It was that simple, and after banging my head off the keyboard for a day and a half, it finally clicked that I did have the wired eth0 working :P



I have the exact same problem. So the only thing to do is to get and install "wicd" driver? I presume that "wicd" is the "STL proprietary driver" for the Broadcom 4357 wireless chip? Where can you get the driver?
Thanks!

---

### Post by blackmail on 2011-06-17
You will need the brcm80211 driver.
A good guide can be found [here]("http://ubuntuforums.org/showthread.php?t=1617380")


Hope this helps.

Regards

---

### Post by wyt168 on 2011-06-17
> **wyt168 said:**
> I presume that "wicd" is the "STL proprietary driver" for the Broadcom 4357 wireless chip? Where can you get the driver?
Thanks!

Just figured out that "wicd" is a network utility that manages both wireless and wired network interfaces on Linux. So the next question still follows--is there a pre-compiled driver for Ubuntu 10.04? If so does it come with the distro or do I have to download it from somewhere?

Thanks!
[]("http://en.wikipedia.org/wiki/Linux")

---

### Post by wyt168 on 2011-06-17
> **blackmail said:**
> You will need the brcm80211 driver.
A good guide can be found [here]("http://ubuntuforums.org/showthread.php?t=1617380")

Regards

Thanks for the link. Will follow the instructions to build the driver. 
Just to be sure--will this source work if built on 10.04?
Regards.

---

### Post by superduperlinuxperson on 2011-06-17
bcm4313 is supported and can get working like this:
step 1: download these two things from here:[http://downloads.openwrt.org/sources...a-3.130.20.0.o](http://downloads.openwrt.org/sources...a-3.130.20.0.o) and [http://mirror2.openwrt.org/sources/b...0.10.5.tar.bz2](http://mirror2.openwrt.org/sources/b...0.10.5.tar.bz2)
step 2: extract the second one to your home folder, and copy the other one their too
step 3: download b43-fwcutter from the software center
step 4: execute these steps in terminal too get it working:

~$ sudo b43-fwcutter -w /lib/firmware wl_apsta-3.130.20.0.o
~$ sudo b43-fwcutter --unsupported -w /lib/firmware broadcom-wl-4.150.10.5/driver/wl_apsta_mimo.o

---

### Post by blackmail on 2011-07-22
So did this work for you?

---

### Post by wyt168 on 2011-07-22
> **blackmail said:**
> So did this work for you?
Well, no, if you are asking about the brcm80211 driver. I was having trouble building it 
(see my post at the thread for building the brcm80211:
[http://ubuntuforums.org/showpost.php?p=10966375&postcount=145](http://ubuntuforums.org/showpost.php?p=10966375&postcount=145))

So I went back and tried to load and config the wl driver. And it worked for me somehow this time! Forgot what I did but that was the end of my dilemma.

---

### Post by blackmail on 2011-07-24
So... does it work fine now?

Sorry if I am stupid or if I make stupid questions, but i am very tired, and i have red through your post very quickly.

Regards

---

### Post by wildmanne39 on 2011-07-24
> **blackmail said:**
> So... does it work fine now?

Sorry if I am stupid or if I make stupid questions, but i am very tired, and i have red through your post very quickly.

RegardsHi, if you need help please run these commands in a terminal
```
lspci -nn | grep 0280
```
```
iwconfig
```
```
rfkill list All
```
```
lsmod
```
and post the outcome  here by clicking on new reply and click # and paste the information between the brackets.

---

