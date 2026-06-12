---
title: "Wireless Intel Ultimate n 6300 problems."
date: 2011-02-10
forum: Networking &amp; Wireless
---

### Post by yuri nator on 2011-02-10
I can't find or connect to wireless.
I'm using Kubuntu 10.10
Please excuse my newbiness. 

Wireless light on the computer is not on, I can't turn it on.
Wireless is enabled on network interface.
Wireless and Mobile Broadband are not lit up/clickable  on network connections add new interface.

No additional drivers can be found other than Nvidia drivers. 

This thread  in the Absolute Beginner forum is what's been tried  [http://ubuntuforums.org/showthread.php?t=1683934](http://ubuntuforums.org/showthread.php?t=1683934)

Keep in mind I'm a complete noob and know how to do almost nothing in linux, so anything will need to be explained in almost perfect detail. :redface:

---

### Post by chili555 on 2011-02-10
I always try to give my instructions perfectly; if I am ever unclear, post back and ask for clarification. Let's get some diagnostic information first. What is the make and model of your laptop? Next, please open Applications > Accessories > Terminal and run and then post:```
rfkill list all
dmesg | grep iwl
```The pipe symbol | is on the right side of my US keyboard on the same key with \.

When we have this information, we will have a better idea how to proceed.

---

### Post by yuri nator on 2011-02-10
```

:~$ rfkill list all
$ dmesg | grep iwl
[   11.930003] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   11.930007] iwlagn: Copyright(c) 2003-2010 Intel Corporation
[   11.930093] iwlagn 0000:09:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   11.930107] iwlagn 0000:09:00.0: setting latency timer to 64
[   11.930203] iwlagn 0000:09:00.0: Detected Intel(R) Centrino(R) Ultimate-N 6300 AGN, REV=0x70
[   11.964107] iwlagn 0000:09:00.0: Unsupported (too old) EEPROM VER=0x21e < 0x434 CALIB=0x4 < 0x4
[   11.964268] iwlagn 0000:09:00.0: PCI INT A disabled
[   11.964276] iwlagn: probe of 0000:09:00.0 failed with error -22
:~$ 


```

---

### Post by chili555 on 2011-02-11
> iwlagn 0000:09:00.0: Unsupported (too old) EEPROM VER=0x21e < 0x434 CALIB=0x4 < 0x4Please see: [http://bugzilla.intellinuxwireless.org/show_bug.cgi?id=1997](http://bugzilla.intellinuxwireless.org/show_bug.cgi?id=1997)

Please don't be confused that the bug report is for a different card, the 5300. The issue is the driver iwlagn which checks for an authorized EEPROM version. This driver is what your card uses, as well as the 5300 and several other cards. 

You might try the updated driver available in Synaptic, linux-backports-modules-compat-wireless-2.6.37-maverick-generic. 

I am searching for a solution that does not require recompiling the kernel. I suggest you google as well: "unsupported too old eeprom iwlagn"

---

### Post by yuri nator on 2011-02-21
> **chili555 said:**
> Please see: [http://bugzilla.intellinuxwireless.org/show_bug.cgi?id=1997](http://bugzilla.intellinuxwireless.org/show_bug.cgi?id=1997)

Please don't be confused that the bug report is for a different card, the 5300. The issue is the driver iwlagn which checks for an authorized EEPROM version. This driver is what your card uses, as well as the 5300 and several other cards. 

You might try the updated driver available in Synaptic, linux-backports-modules-compat-wireless-2.6.37-maverick-generic. 

I am searching for a solution that does not require recompiling the kernel. I suggest you google as well: &quot;unsupported too old eeprom iwlagn&quot;

Sorry for the late reply and question, but is there any chance of a newbie such as myself recompiling the kernel, or is that far too advanced?    

I tried 10.04 and I at least can open the wireless interface, but of course no wireless is picked up.  But, instead of getting an unclaimed result, I get a disabled result. I can't remember if I got an eeprom too old result though.   

 My searching for an answer for the 10.10 eeprom problem didn't return any favorable results. :(

---

### Post by chili555 on 2011-02-21
> is there any chance of a newbie such as myself recompiling the kernel, or is that far too advanced?It's fairly advanced. I've never tried it. There are instructions on the web but, since I've never tried it, I can't vouch for it's effectiveness.

The nice thing is that you probably have several kernels installed on your system; you can boot into a previous one at the GRUB menu and reinstall a fresh linux-image over a botched recompile. Post back if you need guidance about how to do this.> But, instead of getting an unclaimed result, I get a disabled result. I can't remember if I got an eeprom too old result though. Well, that seems like a step forward. Let's see what the error is. Please post:```
sudo modprobe iwlagn
dmesg | grep iwl
```

[http://linuxtweaking.blogspot.com/2010/05/how-to-compile-kernel-on-ubuntu-1004.html](http://linuxtweaking.blogspot.com/2010/05/how-to-compile-kernel-on-ubuntu-1004.html)

DISCLAIMER: I haven't tried it. I can't vouch for it.> You might try the updated driver available in Synaptic, linux-backports-modules-compat-wireless-2.6.37-maverick-genericDid you try this?

---

### Post by yuri nator on 2011-02-24
> **chili555 said:**
> It's fairly advanced. I've never tried it. There are instructions on the web but, since I've never tried it, I can't vouch for it's effectiveness.

The nice thing is that you probably have several kernels installed on your system; you can boot into a previous one at the GRUB menu and reinstall a fresh linux-image over a botched recompile. Post back if you need guidance about how to do this.Well, that seems like a step forward. Let's see what the error is. Please post:```
sudo modprobe iwlagn
dmesg | grep iwl
```[http://linuxtweaking.blogspot.com/2010/05/how-to-compile-kernel-on-ubuntu-1004.html](http://linuxtweaking.blogspot.com/2010/05/how-to-compile-kernel-on-ubuntu-1004.html)

DISCLAIMER: I haven't tried it. I can't vouch for it.Did you try this?
Well, after trying another backport module, I've been ported back to the same eeprom error from 10.10.:mad:
I guess that wasn't a clever thing on my part.


Before I installed the backport module, I was getting an SW microcode error x8200000. 
I had a look at a few bug reports, but it's all like reading another language to me. 
Supposedly someone got theirs working from an experimental ucode, but I couldn't even follow that, plus I'm not sure I should be installing anything experimental at this stage. :confused:

I did try that backport module for 10.10 that you recommended, but it didn't seem to have any positive effect. :(


I'm a little perplexed by all of this, as Intel are such a large company in the computing industry with so many common devices, yet here these problems are.

---

### Post by chili555 on 2011-02-24
> **Alvasin said:**
> **Features and benefits**

 			 			   				**Performance** 				Delivers up to 450 Mbps and 2X2 greater range with 3 antennas for faster, more reliable wireless connectivity in more places. 			   			   				**Dual band** 				Allows connectivity at 2.4 GHz to access older 802.11b/g networks and 5 GHz for higher speeds and greater network capacity. 			   			   				**Low power**3 				Enables long battery life for greater mobility. 			   			   				**Business-class** 				Supports [Intel® vPro™ technology]("http://www.intel.com/technology/vpro/index.htm"), [Intel® Active Management Technology (Intel® AMT)]("http://www.intel.com/technology/platform-technology/intel-amt/"), and [Intel® PROSet/Wireless Enterprise Software]("http://www.intel.com/products/wireless/proset/proset_software.htm") for enterprise Wi-Fi client manageability, improved security, and streamlined deployment. 			   			     				[**Intel® Wireless Display**]("http://www.intel.com/products/wireless/adapters/6300/index.htm")4 				Share PC and online content wirelessly on an HDTV. 			   			   				[**Intel® My WiFi Technology**]("http://www.intel.com/products/wireless/mywifi.htm")5 				Creates a Wi-Fi Personal Area Network (PAN) solution for your laptop for direct connectivity to other Wi-Fi devices.What, exactly, does this do to help us solve the problem?

---

### Post by chili555 on 2011-02-24
> **yuri nator said:**
> Well, after trying another backport module, I've been ported back to the same eeprom error from 10.10.:mad:
I guess that wasn't a clever thing on my part.


Before I installed the backport module, I was getting an SW microcode error x8200000. 
I had a look at a few bug reports, but it's all like reading another language to me. 
Supposedly someone got theirs working from an experimental ucode, but I couldn't even follow that, plus I'm not sure I should be installing anything experimental at this stage. :confused:

I did try that backport module for 10.10 that you recommended, but it didn't seem to have any positive effect. :(


I'm a little perplexed by all of this, as Intel are such a large company in the computing industry with so many common devices, yet here these problems are.You can certainly remove the backport module as easily as you installed it. Afterwards, a reboot will be required.

Is this the original wireless card that came with the laptop or some pre-production sample or, even worse, defective reject pawned off as working sourced from Ebay?

You might contact the folks here: [http://www.intellinuxwireless.org/](http://www.intellinuxwireless.org/)
The site seems to be down or slow loading right now. I'm sure it will be back soon.

---

### Post by yuri nator on 2011-02-25
> **chili555 said:**
> You can certainly remove the backport module as easily as you installed it. Afterwards, a reboot will be required.

Is this the original wireless card that came with the laptop or some pre-production sample or, even worse, defective reject pawned off as working sourced from Ebay?

You might contact the folks here: [http://www.intellinuxwireless.org/](http://www.intellinuxwireless.org/)
The site seems to be down or slow loading right now. I'm sure it will be back soon.

 It came with the computer. I had a look at the card itself but there were no obvious signs it was used or an engineering sample, but I wasn't exactly sure what to look for and I didn't remove any stickers/labels.    

 I'll give that site a go, thanks.

---

