---
title: "Realtek 8185 Wireless PCI not being recognized"
date: 2011-05-30
forum: Networking &amp; Wireless
---

### Post by srikesh on 2011-05-30
Hello,

I recently upgraded to Ubuntu 11.04 (natty-64 bit) and my wireless PCI card is not being recognised by default.  Previously, when I upgraded to 10.10 I had to go to the Realtek website, download the driver for RTL8185 and install it (following instructions in the readme file) to get my wireless card recognised and working properly.

This time around, that approach doesn't seem to work.  When I try to install it using "make" I get the following error:

make: *** /lib/modules/2.6.38-8-generic-pae/build: No such file or directory.  Stop.
make: *** [all] Error 2

Can someone please help me understand what is going on and what I can do to resolve this issue.  Thanks.

Srikesh

Output for 'lshw -C network':
  *-network UNCLAIMED
       description: Ethernet controller
       product: RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@0000:03:02.0
       version: 20
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=64 maxlatency=64 mingnt=32
       resources: ioport:e800(size=256) memory:febffc00-febffdff

Output for 'lspci'
03:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)

---

### Post by imnotrich on 2011-06-08
Solved - delete 11.04 and reinstall Ubuntu 9.04, it recognizes and works flawlessly with this (forgive the editorial comment) very common wireless card. 

In the past I've had some success (when there are hardware issues with the current Ubuntu release) is to install a previous release that actually did support the hardware and then run the "upgrades" until I reached the version I wanted. Most of the time, somehow, the Ubuntu upgrade realizes that hey I need to keep support for this hardware. But today I noticed that between 9.04 and 9.10 Ubuntu broke just about everything else (touch pad, video, and sound) on my less than 5 year old laptop so the crazy bald headed guy from Mexico's upgrade method does not always work. Just an idea.

---

