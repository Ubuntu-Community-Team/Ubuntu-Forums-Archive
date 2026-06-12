---
title: "Intrepid + ndiswrapper + TEW-643PI + wicd  (cannot get Trendnet drivers working)"
date: 2009-02-10
forum: Networking &amp; Wireless
---

### Post by monikersupreme on 2009-02-10
Ignore my sig, those are the specs for my laptop. I am currently trying to get my workstation (dual boot, Intrepid and XP) working with my Trendnet TEW-643PI wireless card (PCI). 

I am running an MSI K9MM-V with an AM2 5200+ processor...

Thus far I have installed the net8190p (Vista 64bit driver) using ndiswrapper (System->Administration->Windows Wireless Drivers) and have installed Wicd (uninstalling the default Gnome Network Manager in the process)...

...

jet@hh:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

jet@hh:~$ ndiswrapper -l
net8190p : driver installed
	device (10EC:8190) present

jet@hh:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1d:92:26:48:b8  
          inet addr:10.86.192.2  Bcast:10.86.192.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:92ff:fe26:48b8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1452 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1461 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1610286 (1.6 MB)  TX bytes:302038 (302.0 KB)
          Interrupt:23 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 B)  TX bytes:100 (100.0 B)

...

ndiswrapper seems to load both the XP 64bit and Vista (have tried both, currently working with Vista) drivers but when I attempt to "Configure Network" ndiswrapper throw and error "Could not find a network configuration tool".

Meanwhile, Wicd does not detect any wireless networks and as you can see above neither iwlan nor ifconfig seem to detect any sort of wireless connection... however ndiswrapper -l seems to recognize that the "device is present"...

(I currently have a wired connection running to the box so as to provide connectivity whilst I troubleshoot this issue...)

Any advice would be much appreciated!

---

### Post by monikersupreme on 2009-02-12
anyone... anyone?

If I can't get this network card I'm probably going to blow away my Ubuntu partition and make this a straight up XP box... I'd really like to stick w/ Linux but without network access it's a no-go...

---

### Post by fibo112358 on 2009-02-13
Hi, 

I never got this card to work using the above tools. I had it working briefly when I changed to WPA encryption, but it never connected afterwards so now I can only use the card in XP. I contacted Trendnet and asked about a Linux driver for this card, but they didn't reply.

Maybe this guide will help: [http://ubuntuforums.org/printthread.php?t=684495](http://ubuntuforums.org/printthread.php?t=684495)

It may be the case that wlan0 just needs to be enabled. Then in WICD, you will be able to select wlan0. I think the problem is mainly with the encryption, since I was able to connect fine after I disabled encryption and it only worked briefly with wpa. I wish I knew more about this stuff so I could be of more help.

---

### Post by jccextermin on 2009-05-02
Hi there:
I bought that same Wireless N PCI Adapter (TEW-643PI) from Trendnet and use the ndiswrapper via the Terminal Console but when I put the command iwconfig my Ubuntu 64 bit freeze.  I am really, but really newbie at this Linux/Ubuntu stuff and I would like to learn more, I find it exiting, if you fix the problem  or have a tutorial guide, let me know  I will appreciate.  Good Luck!!:guitar:

---

### Post by berserkpi on 2011-05-17
Same problem here I'm on Ubuntu 11.04. The TEW-643PI is by no means working.

```

00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation 2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series Chipset Family MEI Controller #1 (rev 04)
00:19.0 Ethernet controller: Intel Corporation 82579V Gigabit Network Connection (rev 05)
00:1a.0 USB Controller: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.3 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 4 (rev b5)
00:1d.0 USB Controller: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation H67 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series Chipset Family 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series Chipset Family SMBus Controller (rev 05)
01:00.0 VGA compatible controller: ATI Technologies Inc Juniper [Radeon HD 5700 Series]
01:00.1 Audio device: ATI Technologies Inc Juniper HDMI Audio [Radeon HD 5700 Series]
02:00.0 PCI bridge: Integrated Technology Express, Inc. Device 8892 (rev 10)
03:02.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8190
04:00.0 USB Controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 03)

```

ndiswrapper says everything is ok...

```
net819xp : driver installed
	device (10EC:8190) present
```

ifconfig doesn't show a wlan:


```
eth0      Link encap:Ethernet  HWaddr e0:69:95:58:1f:b7  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Memory:fe700000-fe720000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:912 errors:0 dropped:0 overruns:0 frame:0
          TX packets:912 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:92497 (92.4 KB)  TX bytes:92497 (92.4 KB)
```

Thanks for your help.

---

