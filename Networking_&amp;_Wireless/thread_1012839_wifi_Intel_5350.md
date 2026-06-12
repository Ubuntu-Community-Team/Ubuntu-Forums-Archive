---
title: "wifi Intel 5350"
date: 2008-12-16
forum: Networking &amp; Wireless
---

### Post by mikhmv on 2008-12-16
Hi, 
Does exist possibility to use intel 5350 wifi card in linux?

Thanks advance.

---

### Post by mikhmv on 2008-12-16
I have bought lenovo T500 notebook with Intel 5350 wifi/wimax card. And WiFi didn't work on kubuntu 8.1. 
Device recognized like: 
03:00.0 Intel Corporation Device 423b


Please help me to make it work.

---

### Post by Martey on 2008-12-17
I also have a T500 with a wireless card with the same PCI ID. I created a bug to track this issue at [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/308848](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/308848)

---

### Post by mikhmv on 2008-12-17
Thanks Martey. 
Look like I have to install kernel 2.6.28.
How can I install it?

---

### Post by Martey on 2008-12-17
First, 2.6.28 does not seem to actually have been released yet - all of the information I can find suggests that it is still in release candidate mode. However, it or 2.6.29 should appear in the next version of Ubuntu (9.04/Jaunty Jackalope) - packages for 2.6.28 already exist for that version.

On another thread, [http://ubuntuforums.org/showthread.php?t=969340](http://ubuntuforums.org/showthread.php?t=969340) , someone suggested using the KernelCheck program to build a custom 2.6.28 kernel. I have never used that program before, so I can speak to neither its capabilities nor its ease of use.

---

### Post by Martey on 2008-12-19
If anyone is interested, I was able to use the instructions at [https://wiki.ubuntu.com/KernelTeam/GitKernelBuild](https://wiki.ubuntu.com/KernelTeam/GitKernelBuild) to build a custom 2.6.28 kernel while still using Ubuntu 8.10. I did not have to make any configuration changes (the instructions include copying over the standard Ubuntu kernel config file), and wireless now works!

---

### Post by mikhmv on 2008-12-21
thanks.
I installed ubuntu 9.04 and wifi now working

---

### Post by dzuchowski on 2009-09-03
> **mikhmv said:**
> thanks.
I installed ubuntu 9.04 and wifi now working

the intel 5350 works with opensuse 11.1 and with the livecd of 9.1 beta should work with 9.04 as well.  atleast the wifi works i live in indianapolis and as far as i know we do not have wimax yet

---

