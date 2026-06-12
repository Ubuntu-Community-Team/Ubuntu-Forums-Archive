---
title: "Ubuntu 10.04 not recognizing wireless networks"
date: 2010-05-04
forum: Networking &amp; Wireless
---

### Post by ajd79 on 2010-05-04
Hello, I am using a Toshiba Laptop model P205D-S7802 with an atheros wireless card. Since I upgraded to 10.04 I am unable to connect to the internet unless I use an ethernet cable.  I have been surfing the threads for a fix and have tried what has been posted but to no avail.

[HTML]eth0      Link encap:Ethernet  HWaddr 00:1b:38:b6:cb:98  
          inet addr:192.168.1.6  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:38ff:feb6:cb98/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:771 errors:0 dropped:0 overruns:0 frame:0
          TX packets:755 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:894077 (894.0 KB)  TX bytes:110035 (110.0 KB)
          Interrupt:27 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:806 errors:0 dropped:0 overruns:0 frame:0
          TX packets:806 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:117696 (117.6 KB)  TX bytes:117696 (117.6 KB)
[/HTML][HTML]00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:05.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1)
00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2)
00:07.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
11:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)
17:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
1d:04.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
1d:04.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
1d:04.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
1d:04.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller[/HTML]I have figured out that there are no installed drivers for the atheros 802.11b/g wireless-LAN. Is there any way that I can either fix this issue or get restored to 9.10?
I had a connection previous to the upgrade.

---

### Post by GSF1200S on 2010-05-05
Looks like its a known issue with Lucid for your particular wireless chipset. Take a look at this link- it provides a patched kernel that is supposed to work, although that did not help some of the posters in the thread:

[http://ubuntuforums.org/showthread.php?t=1466201]("http://ubuntuforums.org/showthread.php?t=1466201")

---

### Post by udippel on 2010-05-05
> **ajd79 said:**
> Hello, I am using a Toshiba Laptop model P205D-S7802 with an atheros wireless card. Since I upgraded to 10.04 I am unable to connect to the internet unless I use an ethernet cable.  I have been surfing the threads for a fix and have tried what has been posted but to no avail.

I had a connection previous to the upgrade.

Was your output 'ifconfig' or 'ifconfig -a'? We need the latter.

Uwe

---

### Post by ajd79 on 2010-05-05
> **udippel said:**
> Was your output 'ifconfig' or 'ifconfig -a'? We need the latter.

Uwe
here is the ifconfig -a [HTML]Link encap:Ethernet  HWaddr 00:1b:38:b6:cb:98  
          inet addr:192.168.1.6  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:38ff:feb6:cb98/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:26767 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15727 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:38784397 (38.7 MB)  TX bytes:1433913 (1.4 MB)
          Interrupt:27 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1500 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1500 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:181584 (181.5 KB)  TX bytes:181584 (181.5 KB)[/HTML]
forgive the recovering windows user for his ineptitudes :)

---

### Post by ajd79 on 2010-05-05
> **GSF1200S said:**
> Looks like its a known issue with Lucid for your particular wireless chipset. Take a look at this link- it provides a patched kernel that is supposed to work, although that did not help some of the posters in the thread:

[http://ubuntuforums.org/showthread.php?t=1466201](http://ubuntuforums.org/showthread.php?t=1466201)
tried that as well, it didn't work.
I did try to add the drivers via ndiswrapper and that failed me as well

---

### Post by udippel on 2010-05-05
> **ajd79 said:**
> here is the ifconfig -a
forgive the recovering windows user for his ineptitudes :)

No need to worry. This is just to show if the interface is there at all, maybe just 'DOWN'. But it isn't. Since the kernel recognises it, it is physically there. The driver is probably borked. I suggest to file a bug report for this specific chipset, if it doesn't exist already.

Uwe

---

### Post by ajd79 on 2010-05-05
where do I go to file a bug report or see what has been posted already?  Also, what do I need to include in the report? Also, since 9.10 recognized the drivers automatically, is there a wayto revert to the earlier release?

---

### Post by eltonw on 2010-05-05
> **ajd79 said:**
> where do I go to file a bug report or see what has been posted already?  Also, what do I need to include in the report? Also, since 9.10 recognized the drivers automatically, is there a wayto revert to the earlier release?

There are many issues with the kernel in LUCID LTS. You could try reverting to the kernel from Karmic, or install the 2.6.33 kernel,as mentioned in my posting:[http://ubuntuforums.org/showthread.php?t=1473629]("http://ubuntuforums.org/showthread.php?t=1473629")

HTH...):P

---

### Post by udippel on 2010-05-05
> **ajd79 said:**
> where do I go to file a bug report or see what has been posted already?  Also, what do I need to include in the report? Also, since 9.10 recognized the drivers automatically, is there a way to revert to the earlier release?

Since your problem is different from most of ours (your wireless card isn't recognized), you should file the report. Simply run 'ubuntu-bug' from a terminal, answer some questions, check if it is there. (You need to create an account in launchpad, if you don't have any yet. It will ask you to do so during the process.)

There are different philosophies about reverting to an earlier release. At least, it isn't *that* straightforward. I'd start by modifying /etc/apt/sources.list, and replace all 'lucid' with 'karmic', and try 'update' 'dist-upgrade'. You'll probably need some 'force'.

Uwe

---

