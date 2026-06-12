---
title: "SharedData Partition Between OSX, Ubuntu, and XP"
date: 2008-12-30
forum: Mac OSX
---

### Post by RookieUbuntuUser58 on 2008-12-30
I decided to triple boot and still have about 25GB's left. So I thought why not use it as a SharedData Partition between the 3 OS's. I tried to configure this using the Disk Utility in OSX but it doesn't recognize the free space; only the 3 OS partitions. I then tried to format the free space as FAT32 and then format it in OSX Disk Utility but that also didn't work. It was recognized but the formatting didn't work it just erased the data on partition. Any ideas on how to get this to work?


Also since I installed Ubuntu last I have grub bootloader to handle the triple boot. But heres the problem. I go into OSX and Darwin bootloader runs giving me the option to load OSX or XP. I set the timeout to "0" but that didn't work. I just want when I click on OSX from grub bootloader it loads OSX and not options. 

Thanks in advance for any help.

---

### Post by handy on 2009-01-01
Here is a link to an Arch wiki article I wrote regarding installing Arch on an iMac:

***_[http://wiki.archlinux.org/index.php/IMac_Aluminium](http://wiki.archlinux.org/index.php/IMac_Aluminium)_***

I went into a lot of detail regarding Apple's use of the GPT partitioning scheme, you should find the sections up to *1.4 Installing Arch* relevant to your situation 

It explains all. :)

---

