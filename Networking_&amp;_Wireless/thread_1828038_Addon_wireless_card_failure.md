---
title: "Addon wireless card failure"
date: 2011-08-18
forum: Networking &amp; Wireless
---

### Post by pgtipz on 2011-08-18
Hi, I'd be grateful for any help to get online.

I'm trying to get my install of Ubuntu 11.04 to recognize and connect wirelessly, but the network applet does not even see my Addon wireless pci card.

My PC is a custom built system from dinopc: AMD Phenom II X2 555, Windows 7 Home Premium 64-bit/Ubuntu 11.04, Motherboard:  Asus M4N68T-M, 8GB DDR3 1333mhz, 1TB HDD, ATI Radeon HD 5770 1GB, PSU: 500W Xigmatek, Addon Wireless 802.11N 300Mbps MIMO PCI card, Peak Hardware PCI Digital TV Tuner Card,

Additionally, I have a micro USB mini wifi adapter available which is purportedly Linux friendly, as another option.

Following, ‘How to post a wireless issue', [http://ubuntuforums.org/showthread.php?t=885847](http://ubuntuforums.org/showthread.php?t=885847) here are the results:

peter@ubuntu:~$ uname -m
x86_64
peter@ubuntu:~$ lspci –nn
00:00.0 RAM memory [0500]: nVidia Corporation MCP61 LPC Bridge [10de:03e2] (rev a1)
00:01.0 ISA bridge [0601]: nVidia Corporation MCP61 LPC Bridge [10de:03e1] (rev a2)
00:01.1 SMBus [0c05]: nVidia Corporation MCP61 SMBus [10de:03eb] (rev a2)
00:01.2 RAM memory [0500]: nVidia Corporation MCP61 Memory Controller [10de:03f5] (rev a2)
00:02.0 USB Controller [0c03]: nVidia Corporation MCP61 USB Controller [10de:03f1] (rev a3)
00:02.1 USB Controller [0c03]: nVidia Corporation MCP61 USB Controller [10de:03f2] (rev a3)
00:04.0 PCI bridge [0604]: nVidia Corporation MCP61 PCI bridge [10de:03f3] (rev a1)
00:05.0 Audio device [0403]: nVidia Corporation MCP61 High Definition Audio [10de:03f0] (rev a2)
00:06.0 IDE interface [0101]: nVidia Corporation MCP61 IDE [10de:03ec] (rev a2)
00:07.0 Bridge [0680]: nVidia Corporation MCP61 Ethernet [10de:03ef] (rev a2)
00:08.0 IDE interface [0101]: nVidia Corporation MCP61 SATA Controller [10de:03f6] (rev a2)
00:08.1 IDE interface [0101]: nVidia Corporation MCP61 SATA Controller [10de:03f6] (rev a2)
00:09.0 PCI bridge [0604]: nVidia Corporation MCP61 PCI Express bridge [10de:03e8] (rev a2)
00:0b.0 PCI bridge [0604]: nVidia Corporation MCP61 PCI Express bridge [10de:03e9] (rev a2)
00:0c.0 PCI bridge [0604]: nVidia Corporation MCP61 PCI Express bridge [10de:03e9] (rev a2)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration [1022:1200]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor Address Map [1022:1201]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller [1022:1202]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control [1022:1203]
00:18.4 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor Link Control [1022:1204]
01:06.0 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 62)
01:06.2 USB Controller [0c03]: VIA Technologies, Inc. USB 2.0 [1106:3104] (rev 65)
01:07.0 Network controller [0280]: Ralink corp. Device [1814:3062]
02:00.0 VGA compatible controller [0300]: ATI Technologies Inc Juniper [Radeon HD 5700 Series] [1002:68b8]
02:00.1 Audio device [0403]: ATI Technologies Inc Juniper HDMI Audio [Radeon HD 5700 Series] [1002:aa58]

peter@ubuntu:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: Ralink corp.
       vendor: Ralink corp.
       physical id: 7
       bus info: pci@0000:01:07.0
       logical name: wlan0
       version: 00
       serial: c8:3a:35:ce:59:ab
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci driverversion=2.6.38-8-generic firmware=0.11 latency=64 maxlatency=4 mingnt=2 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:16 memory:dfee0000-dfeeffff
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.

peter@ubuntu:~$ sudo lshw -C Network
  *-network               
       description: Wireless interface                                                                    
       product: Ralink corp.                                                                              
       vendor: Ralink corp.
       physical id: 7
       bus info: pci@0000:01:07.0
       logical name: wlan0
       version: 00
       serial: c8:3a:35:ce:59:ab
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci driverversion=2.6.38-8-generic firmware=0.11 latency=64 link=no maxlatency=4 mingnt=2 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:16 memory:dfee0000-dfeeffff

Many thanks for any help. 

Cheers!
pgtipz

---

### Post by pgtipz on 2011-09-20
I'm still hoping that a kind soul will respond to my post above. 

I have wiped out the previous install (with Wubi), and can safely dual boot from winblows 7 or into Ubuntu 11.04, having tried Wubi again. 

I am really keen to get Ubuntu up and running, but I still need help to get my wireless working for it to be productive. 

I believe the Addon pci card is supposed to be Linux compatible, but I'm having no joy getting any networks to appear. 

Thanks for your help in advance!

---

### Post by wildmanne39 on 2011-09-20
Hi, here is a link with directions.
[http://ubuntuforums.org/showthread.php?t=1780136&page=3](http://ubuntuforums.org/showthread.php?t=1780136&page=3)
Start with post 20 all you need is in that post, where it says the 3562 driver put yours the 3062.
Thank you

---

### Post by praseodym on 2011-09-20
Or try this prepared driver:

[http://forum.ubuntuusers.de/topic/doppelseitiges-problem-wlan-kabel/#post-2739482](http://forum.ubuntuusers.de/topic/doppelseitiges-problem-wlan-kabel/#post-2739482)

Just copy/paste the commands, the driver will be downloaded with "wget"

---

### Post by pgtipz on 2011-09-21
Many thanks, chums!
I'll give it a whirl and let you know how it goes.

Cheers!
Pete

---

### Post by wildmanne39 on 2011-09-21
Hi, your welcome! good luck.

---

### Post by pgtipz on 2011-09-29
It worked!! 

I downloaded and installed the driver and edited the files as directed above. I was not sure it was going to succeed when the modprobe did not work at first (i.e. find the new module), but on reboot the network icon now displays local wireless networks for the first time. Relief! Superabundance of jollity to follow! :)

My sincere thanks to wildmanne39 and praseodym for your help. That's what is so good about the Linux community - helping one another.

I suppose this will be fine until the next distro upgrade?

Best wishes from England!

Pete

---

### Post by wildmanne39 on 2011-09-29
Hi, your welcome! I am glad your wireless is working, when you upgrade your kernel you will have to do this to make it work again.

Change into the directory of the driver then run:
```
sudo su
make clean
make
make install
modprobe drivername
exit
```
If I was helpful would you please click on the red link in my signature and support me becoming an ubuntu member? also would you please go to the top of the page and mark this thread solved by clicking on thread tools. Thank you so much.

---

