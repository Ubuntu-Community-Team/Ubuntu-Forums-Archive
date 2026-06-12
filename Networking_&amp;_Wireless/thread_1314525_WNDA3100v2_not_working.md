---
title: "WNDA3100v2 not working"
date: 2009-11-04
forum: Networking &amp; Wireless
---

### Post by SKITTLES_momma on 2009-11-04
Hello everyone. I'm tired of windows and I've previously used ubuntu back in the 7.0 days. Now I've installed Ubuntu 9.10 and I've tried Ubuntu Netbook Remix (I have and Acer Aspire One D150). Everything went great except trying to install my Netgear Wnda3100v2 wireless adapter. I have followed all steps in this how to thread:[[ubuntu] HOWTO: Netgear RangeMax Dual Band Wireless-N 300 USB Adapter (WNDA3100) - Ubuntu Forums]("http://swiss.ubuntuforums.org/showthread.php?p=7940291"). After I click on Windows Wireless Devices it says the driver is installed but the hardware is not present. When I run the lsusb command in the terminal it doesn't show up. I have noticed in Windows that it has a Broadcom chipset the driver I have installed is the bcmwlhigh. I've tried googling this sys file in order to find the inf for ndiswrapper but that didn't return much. I have the .exe is there a way I can get the inf from that? Or has anyone had this problem with this version of the adapter?

---

### Post by Darquelf on 2009-11-05
As much as I hate to piggyback on someone elses' thread, I seem to be having the same issue, only mine does say Netgear, Inc in lsusb...but it still tells me device not ready under Wireless Networks...

---

### Post by AndEvo on 2010-05-10
Hi

I'm having the same problem, I can connect using ndiswrapper but as soon as I do any scrolling etc the connection crashes, I really need this to work

Cheers
Andy

---

### Post by 65 mustang on 2010-05-21
Bump having same problem NETGEAR WNDA3100-100NAS on 10.04 64 bit.  Can someone give me the steps to get the ndiswrapper to install?

---

### Post by 65 mustang on 2010-05-21
Found this:
[http://ubuntuforums.org/showthread.php?t=1383708](http://ubuntuforums.org/showthread.php?t=1383708)

---

### Post by sambo625 on 2010-06-05
anyone find a solution for WNDA3100v2 on ubuntu 10.04.

---

### Post by jwferk on 2010-08-27
I just finished trying for a week to get a WNDA3100v2 working on Ubuntu 10.04.  After reading buku threads, advice, etc I could never get the device to function.  I ran into most of the problems already described in these threads and on other forums.

1 - definitely does not work out of the box;
2 - does not work with any known linux driver;
3 - does not work with ndiswrapper; in fact,ndiswrapper would go into an infinite loop on many occasions once I tried to install the Windows driver.  I'd need to either blacklist ndis or remove the package altogether.
4 - wine doesn't correctly unpack/install the Windows driver.  I went so far as to purchase Crossover Professional and that still fails to unpack the drivers correct.y
5 - the most recent driver bcmlwhigh6 is not valid for ndiswrapper.
6 - when I did get the older driver (bcmlwhigh5) to install, "ndiswrapper -l" would tell me the driver and device were present but not a thing would happen.
7 - the ndiswrapper issues are probably a bug in 10.04 as I've seen other reports of similar behavior on LaunchPad.

I could go on.

Solution for me, I returned the Netgear product to NewEgg and went out and purchased a Linksys WMP600N PCI card at Microcenter for a few dollars less.  It worked out of the box in about 5 min most of which was devoted to opening up the box to put the card in.  The Linksys card has all the dual band and bandwidth capabilities as the Netgear unit.

---

### Post by CeilingRepairman6872 on 2010-09-18
> **jwferk said:**
> 
1 - definitely does not work out of the box;
2 - does not work with any known linux driver;
3 - does not work with ndiswrapper; in fact,ndiswrapper would go into an infinite loop on many occasions once I tried to install the Windows driver.  I'd need to either blacklist ndis or remove the package altogether.
4 - wine doesn't correctly unpack/install the Windows driver.  I went so far as to purchase Crossover Professional and that still fails to unpack the drivers correct.y
5 - the most recent driver bcmlwhigh6 is not valid for ndiswrapper.
6 - when I did get the older driver (bcmlwhigh5) to install, "ndiswrapper -l" would tell me the driver and device were present but not a thing would happen.
7 - the ndiswrapper issues are probably a bug in 10.04 as I've seen other reports of similar behavior on LaunchPad.


You are right on counts (1) and (2). You are partially correct on the other points. But rather than make the solution be to go out and buy something else, I'd like to focus on the actual issue. Mankind would not progress if we all approached problem solving in this way :)

I've gotten the Netgear WPN111 USB stick to work with Ubuntu 10.4, but not well. It is an exceptionally bad connection when used on either linux or windows. Download speeds are relatively high, but connection losses and inability to make connections make the device nearly unusable.

The Netgear WNDA3100v2 is very good under windows. I can get the bcmlwhigh5 driver to work, but there is bug that prevents the use of WPA security. 

This thread continues the problem and someone at the end claims to have solved it: [http://ubuntuforums.org/showthread.php?t=1553807](http://ubuntuforums.org/showthread.php?t=1553807)

Here is the link to the potential fix, which looks scary to me at first, but as I read through it might be fairly simple: [http://polach.cc/howto-fix-broadcom-wifi-adapter-wpa-network-access-on-ubuntu-10-04-lucid-lynx](http://polach.cc/howto-fix-broadcom-wifi-adapter-wpa-network-access-on-ubuntu-10-04-lucid-lynx)

---

### Post by frankmoss on 2010-11-07
Its not working on ubuntu 10.04. 
The error I found in messages

loadndisdriver:  couldn't load driver bcmwlhigh6.

Also tried bcmlhigh5. In this case the modprobe just hangs. Have to restart the PC.

---

### Post by frankmoss on 2010-11-08
Anyone tried this [http://ubuntuforums.org/showthread.php?t=1383708](http://ubuntuforums.org/showthread.php?t=1383708) on Ubuntu 10.04?

---

### Post by Sega dude on 2011-05-08
> **frankmoss said:**
> Anyone tried this [http://ubuntuforums.org/showthread.php?t=1383708](http://ubuntuforums.org/showthread.php?t=1383708) on Ubuntu 10.04?

I have and it does'nt work. It screwed up my wireless all together and now I can only use wired.

---

