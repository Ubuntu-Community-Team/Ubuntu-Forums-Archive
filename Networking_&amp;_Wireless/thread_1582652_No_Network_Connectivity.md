---
title: "No Network Connectivity"
date: 2010-09-26
forum: Networking &amp; Wireless
---

### Post by marm26 on 2010-09-26
Hallo Everybody.

I just installed the latest version of Ubuntu Desktop. The installation was fast and easy and I got Ubuntu running now. Only problem: I dont get any network connectivity at all. I guess its a driver issue. If I check my system within Windows I see the following network adapters:

Atheros AR8152 PCI-E Fast Ethernet Controller
Broadcom 802.11n Network Adapter

I tried searching the internet for linux drivers for both of the above mentioned but couldnt get anything to work. If anybody could help me out with this issue I would greatly apppreciate. 

Thanks in advance...

Maybe I should mention that I am not very linux literate....

---

### Post by walt.smith1960 on 2010-09-26
I am far from knowledgeable but that never stopped me before :tongue:.  Does your wired ethernet connection not work either?  My EeePC has an Atheros 81**3**2 ethernet chip which has been plug & play since 9.10.  It seems common to have to use a wired connection to download the Broadcom software.  If you don't have a wired connection there are other ways to get the Broadcom proprietary drivers  but I can't help with it, sorry. There are lots of knowledgeable helpful people here. Your problem should soon be solved.

---

### Post by Iowan on 2010-09-26
Wireless isn't my forte either, but...
From a terminal (Applications>Accessories>Terminal) check (post if possible) **sudo lshw -C network**

---

### Post by marm26 on 2010-09-27
Hi guys. Thanks for helping me out with this. 

I might have been a little missleading in my post above. Actually I am trying to get the wired connection to work for now. I guess the wireless drivers will be an easy install once I got a wired connection setup.

So Walt to answer your question, no I got a LAN cable plugged but I cant connect to the internet for some reason.

Iowan, here is the output of  **sudo lshw -C network. **Hope it helps...

*-network UNCLAIMED     
       description: Network controller
       product: Broadcom Corporation
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:94000000-94003fff
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR8152 v1.1 Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:04:00.0
       version: c1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list
       configuration: latency=0
       resources: memory:93000000-9303ffff ioport:2000(size=128)

---

### Post by marm26 on 2010-09-27
guys i just got it to work. i did something like this:
[http://www.linuxforums.org/forum/suse-linux/135926-how-do-i-manually-install-driver.html](http://www.linuxforums.org/forum/suse-linux/135926-how-do-i-manually-install-driver.html)

it didnt really work the way it was supposed to but after messing around with command line for a couple of hours i finally managed to get the missing driver installed. after the cable connection started working the wireless driver was updated automatically.

thanks for helping out again and good luck with your future linux endeavors...

---

### Post by Iowan on 2010-09-27
If the problem stays fixed, consider marking the thread [[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads"). :)

---

### Post by walt.smith1960 on 2010-09-27
If you downloaded and compiled driver software,  a kernel update might break it again and you'll have to recompile and reinstall. (as I understand it)  I wonder why vendors can't release .deb & .rpm packages for their more popular hardware.  Too many different configurations?

---

