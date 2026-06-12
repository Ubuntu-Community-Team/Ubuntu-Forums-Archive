---
title: "AspireOne, Atheros chipset not found, madwifi/ndiswrapper no worky"
date: 2009-09-08
forum: Networking &amp; Wireless
---

### Post by mailman1175 on 2009-09-08
I just installed Ubuntu 8.04 on my sister's AspireOne ZG5 (160GB HDD; 1GB RAM), using the same process (almost; see below) I used to install it on my wife's AspireOne ZG5 (8GB SSD; 512MB RAM). My wife's machine is functioning perfectly, and has been for the 3 months or so since I did the install. I can't get the wifi working on little sister's machine.

I went through the [instructions]("https://help.ubuntu.com/community/AspireOne") for madwifi AND ndiswrapper (concurrently, not at the same time). I did change madwifi-hal-0.10.5.6-r3879-20081204 to whatever unzipped with the package, but other than that, I followed step-by-step. For that matter, I used the linked wiki for the whole install on both machines. I know just enough to be dangerous, in other words. The only difference between the two is that I allowed my sister's machine to upgrade a few things that I have not allowed yet with my wife's.

That is, I figured out (the hard way on my wife's machine, before I read the note in the wiki) that a kernel upgrade to 2.6.24-23 would break the install. So, I've never allowed that upgrade. However, I noticed today that there seemed to be a newer kernel available for upgrade, 2.6.24-24. So, I installed the following on my sister's machine *before* I compiled the madwifi drivers, and - later - the ndiswrapper set:

[LIST]
[*]linux-generic
[*]linux-headers-2.6.24-24
[*]linux-headers-2.6.24-24-generic
[*]linux-headers-generic
[*]linux-image-generic
[*]linux-restricted-modules-2.6.24-24-generic
[*]linux-restricted-modules-common
[*]linux-restricted-modules-generic
[*]linux-ubuntu-modules-2.6.24-24-generic
[/LIST]
What I left *out* were the linux-headers and linux-*-modules that referred to the 2.6.24-23 kernel, as that's the one that breaks the install.

At any rate, in both cases, with madwifi and ndiswrapper, there appears no wireless network. After a bit of searching, I found some people who had similar problems, but their problems seemed to solve themselves after a reboot. Mine did not, so I'll post below the results of a few commands asked-for in those similar threads:

```
iwconfig
lo        no wireless extensions
eth0    no wireless extensions
``````
lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GME Express Memory Controller Hub [8086:27ac] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GME Express Integrated Graphics Controller [8086:27ae] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 [8086:27d0] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 [8086:27d2] (rev 02)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 [8086:27d6] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 [8086:27c8] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 [8086:27c9] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 [8086:27ca] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 [8086:27cb] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 02)
00:1f.2 IDE interface [0101]: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller [8086:27c4] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801G (ICH7 Family) SMBus Controller [8086:27da] (rev 02)
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)

```See? It doesn't even show the Atheros chipset. It's like it's not there. It was working (one of the few things that was...) in XP, so something's b0rked it.

Are the kernel updates 23-24 and 24-24 dependent on one another? Is it possible that, for some reason, madwifi's not working with that latest kernel? Something else I'm not thinking of? How do I boot to the older kernel to see if ndiswrapper (which is what's presently installed) works with it so I can remove that possibility? I remember I can do that... I just can't remember how.

Thanks in advance, people.

---

### Post by mailman1175 on 2009-09-08
I don't know why, or how, but the last hard shutdown/reboot cycle seems to have fixed it. Weird. Thanks, anyway.

---

