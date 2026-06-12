---
title: "How to activate wireless drivers with no ethenet connection?"
date: 2010-09-26
forum: Networking &amp; Wireless
---

### Post by silt on 2010-09-26
Hi. I'm been wanting to try Ubuntu for a while now, and when my mom's netbook started to get insanely slow with WinXP, I tried the Netbook Remix on a USB stick. I LOVE it, except I am unable to get the wireless working, which is the only thing stopping me right now from a full install. 

I believe my problem is that I need to activate the two drivers "Broadcom B43 wireless driver" and "Broadcom STA wireless driver" which appear as unactivated when I go into the hardware drivers admin tools. Unfortunately this netbook (HP Mini Netbook FW376UA) does not have an Ethernet port, so I can't just temporarily hard wire it to activate these drivers.  

So my main questions are:  1) How can I activate those drivers without an internet connection?, and  2) Do you think that activating these drivers is indeed the answer to getting the wireless working?  

The details: 
Machine: HP Mini Netbook FW376UA 
Network Controller: Broadcom Corporation BCM4312 802.11b/g 
Ubuntu version: Ubuntu 10.04 Netbook 

Thanks very much in advance for your help. Have a nice day.

---

### Post by tenwiseman on 2010-09-26
See [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

### Post by Chris1274 on 2010-09-26
You only need one or the other, not both. I think the STA driver should work, but I don't know how to install it without a wired connection.

---

### Post by silt on 2010-09-26
> **tenwiseman said:**
> See [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

Thanks! I was able to get the wireless working after using the Synaptic Package Manager and installing the bcmwl-kernel-source package (even though there were some errors during that process).

When I restart, I have to do all of this again though. Is this because I am booting from a USB stick? 

If I go ahead and actually install Ubuntu onto the computer, do you think I will have to keep installing that package every time I reboot? Or should everything be ok once I do it once?

Again, thank you very much for your help.

---

### Post by walt.smith1960 on 2010-09-26
Do you have an external DVD-RW or hard drive? Or HP system restore CDs/DVDs? Either way, I would get a reliable disk imaging program.  Clonezilla (Clonezilla.org) is an open source option that seems to produce reliable images. If you can create an image (I'd probably do at least two, in case one doesn't restore properly), you can create an image of the existing XP partition.  You can then create another partition if there's room on the netbook hard drive and install Ubuntu.  If there's not room, you can delete the XP partition, install Ubuntu then restore what's there now if necessary.  

I use a couple shareware programs-yes I paid for them-to handle partition management and booting multiple operating systems.  I use BootItNG for partition and boot management and Image for Linux for partition imaging.  BootItNG takes some patience but once you figure it out it seems pretty reliable. Most disks are limited to 4 primary partitions. BootItNG will create over 100 primary partitions by using an extended master boot record. You can then choose which other partitions are visible to that operating system.  I've restored several images with Image for Linux and if the image will verify, it will restore reliably.  I don't work for or have any relationship with Terabyteunlimited, I just appreciate software that does what I expect it to do.  One thing to be careful of if you do use BootItNG.  When installing Ubuntu, be sure to install GRUB in the partition, not in the MBR.  GRUB will overwrite BootItNG's extended MBR and you'll lose the ability to boot any other OSs.  There's ways to recover but I'd recommend not having to try them.

[http://www.terabyteunlimited.com/index.htm](http://www.terabyteunlimited.com/index.htm)

---

