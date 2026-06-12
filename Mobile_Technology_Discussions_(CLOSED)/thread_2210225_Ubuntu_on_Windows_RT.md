---
title: "Ubuntu on Windows RT?"
date: 2014-03-09
forum: Mobile Technology Discussions (CLOSED)
---

### Post by flyfishingphil on 2014-03-09
I've used Ubuntu for several years now but am just about as close to knowing what I am doing as politicians are to answering questions honestly so thought I'd post here and get moved to proper area if needed. OK as long as I get notification of any responses.

What I am trying to find out is if it is possible to change a Surface RT, with 64 GB, from the worthless Win 8.1 to Ubuntu. Unfortunately a "tech" at what is supposed to be one of the best buy places for electronics convinced me that the RT system would plug right in to my Win 7 and Ubuntu with no problem and I would be able to share files and do just about anything between the laptop and the tablet. (I'll try to avoid purchasing there in the future. I didn't know that doing that is kind of like trying to get the engine and transmission from an 18-wheeler to fit on your Honda 90 motorcycle and work properly.)

Has anybody figured out how to format the Surface RT and have an Ubuntu OS that could be installed in the Surface RT? If not, how about installing it in an android tablet? Android is better than ARM Win 8.1 but I'd really like to have the Ubuntu so I can share between my laptop and my tablet.

Any assist is greatly appreciated.

ffp

---

### Post by kurt18947 on 2014-03-10
Here is my understanding - I'm no expert.  My impression is that Windows RT devices are locked and alternative OSs can't be installed.  Secure Boot can be disabled on X86 systems like Surface Pro but not on ARM devices.  Aren't Windows RT devices (surface) ARM powered?  Even on Surface Pro devices I've read hardware support for Linux is pretty bad.

---

### Post by Lars Noodén on 2014-03-10
Anything with Windows on ARM is going to be locked that way.  [WindowsRT devices lock out Linux](http://www.dailytech.com/Microsoft+Bans+LinuxAndroid+DualBooting+on+Windows+8+ARM+Devices/article23785.htm) by design.  So if you can't return the device to the shop for money back or a credit against a useful purchase, the only place the device belongs would be the recycling center and steer clear of that chain of stores in the future.   They're still trying their mischief but [that attempt did not work out well](http://www.computerworld.com/s/article/9240899/Microsoft_writes_off_nearly_1B_to_account_for_Surface_RT_bomb).  There are many other ARM devices to choose from, none of which are tainted in a way that prevents you from using them.  Just avoid Windows pre-installed next time.  

However, about [Ubuntu on ARM](https://wiki.ubuntu.com/ARM), I have not followed it closely but get the impression that only the server edition is available for ARM.  Debian might be your best option for an ARM notebook or tablet.

---

### Post by grahammechanical on 2014-03-10
Ubuntu has had a Linux kernel that meets the Microsoft secure boot criteria since the release of Ubuntu 12.10. So, the inability to disable secure boot cannot be why Linux cannot be installed on a surface RT device.

> [COLOR=#333333][FONT=Ubuntu]"[/FONT][/COLOR][Secure Boot]("http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface#Secure_boot")[COLOR=#333333][FONT=Ubuntu]" is a new UEFI feature that appeared in 2012, with Windows8 preinstalled computers. [/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu][/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]All current Ubuntu 64bit ([/FONT][/COLOR][not 32bit]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1025555")[COLOR=#333333][FONT=Ubuntu]) versions now support this feature, [/FONT][/COLOR]

[https://help.ubuntu.com/community/UEFI#SecureBoot](https://help.ubuntu.com/community/UEFI#SecureBoot)

The reason could possibly be the fact that the RT has a CPU architecture that Ubuntu does not run on. The ARM company designs the CPU and they can tailor the design to meet the specification of the customer.

Regards.

---

### Post by flyfishingphil on 2014-03-10
Kind of what I figured would be the Micro practices. If it won't make us money don't allow it.

Anyone have the specifications on an Android device that might allow the use of Ubuntu?

ffp

---

### Post by kurt18947 on 2014-03-10
No experience but Chromebooks can be convinced to run Ubuntu, I think.  The problem with Chromebooks is small SSD drives if you wanted to dual boot Chrome & a linux distro.  I believe some Chromebooks use standard SSDs that can be upgrade though.  HP might be one.   Some manufacturers make maintenance and service manuals available online so you assess hardware prior to purchase.  The question would be if the Chromebook's BIOS recognizes other SSDs if you wanted to go bigger.   Here's one of the first things that popped up via a Google search:


[URL="http://www.howtogeek.com/162120/how-to-install-ubuntu-linux-on-your-chromebook-with-crouton/"]http://www.howtogeek.com/162120/how-to-install-ubuntu-linux-on-your-chromebook-with-crouton/





[/URL]

---

### Post by 3rdalbum on 2014-03-10
The 2013 Nexus 7 is an Android tablet that communicates with Ubuntu for sharing of files. It can also be convinced to run Ubuntu Touch. Not Ubuntu Desktop, though.

---

### Post by 2ndbase on 2015-03-07
I guess it depends of if you can find an ARM version of GRUB 2 that is signed with by Microsoft? If you know of one then please reply with a link.

---

