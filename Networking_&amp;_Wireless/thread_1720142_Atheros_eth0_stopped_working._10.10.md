---
title: "Atheros eth0 stopped working. 10.10"
date: 2011-04-02
forum: Networking &amp; Wireless
---

### Post by Rkn4roll4life on 2011-04-02
Hey all,

I installed 10.10 about a week or two ago, everything was fine until I restarted my computer today.

After the reboot my eth0 stopped working.  I'm not a very network savvy user, so I would appreciate some help.

I've had the ethernet working before, and I've booted/rebooted before, this is the first time it's stopped working.

It's for sure a good connection, I unplugged it from the desktop and tried it out on my mac with no connections problems. 

Additionally, I thought I might be able to reinstall to fix the issue, but trying to install from flashdrive it didn't recognize the eth0 connection. 

I'm not sure exactly what diagnostic information you'll need, but I know the following: 

I've got an Atheros (built into the board)
```
03:00.0  Ethernet Controller:  Atheros Communications AR8313 Gigabit Ethernet
```running ifconfig...
```
eth0      Link encap:Ethernet  HWaddr 6c:62:6d:54:60:1c  
          inet6 addr: fe80::6e62:6dff:fe54:601c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4303 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:449085 (449.0 KB)  TX bytes:4821 (4.8 KB)
          Interrupt:43 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:82 errors:0 dropped:0 overruns:0 frame:0
          TX packets:82 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:20441 (20.4 KB)  TX bytes:20441 (20.4 KB)

```Any help, tips, suggestions would be appreciated.


Thanks,
Jack

---

### Post by maximmai on 2011-04-04
Hello, I have exactly the same problem today, 2011-04-04.

It was working fine before, and it stopped working today after I rebooted my computer (I had it running for all day, so I decided to reboot...)


here is some of my info:

Machine Model: HP HPE371F

```
ifmaxim@maximmai-hpe371f:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 78:e7:d1:ca:13:1d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:43 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:47 errors:0 dropped:0 overruns:0 frame:0
          TX packets:47 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4602 (4.6 KB)  TX bytes:4602 (4.6 KB)

vboxnet0  Link encap:Ethernet  HWaddr 0a:00:27:00:00:00  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 70:f1:a1:62:98:ac  
          inet addr:192.168.0.198  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::72f1:a1ff:fe62:98ac/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12141 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9538 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:12751999 (12.7 MB)  TX bytes:1617978 (1.6 MB)

maxim@maximmai-hpe371f:~$ uname -a
Linux maximmai-hpe371f 2.6.35-28-generic-pae #49-Ubuntu SMP Tue Mar 1 14:58:06 UTC 2011 i686 GNU/Linux

maxim@maximmai-hpe371f:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge Alternate
00:02.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (ext gfx port 0)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:0a.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 5)
00:11.0 RAID bus controller: ATI Technologies Inc SB700/SB800 SATA Controller [Non-RAID5 mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3c)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:00.0 VGA compatible controller: ATI Technologies Inc Juniper [Radeon HD 5700 Series]
01:00.1 Audio device: ATI Technologies Inc Juniper HDMI Audio [Radeon HD 5700 Series]
02:00.0 Network controller: RaLink RT3090 Wireless 802.11n 1T/1R PCIe
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)


```

Any idea??

Thanks,

Regards,

Maxim Mai

---

### Post by drdanielfc on 2011-04-20
I am also having the same issue. Was running Ubuntu 10.10 Atheros AR8131 and it just stopped working (i know for a fact it was working, but it may have been a reboot that triggered the fail don't recall). Upgraded to Natty Beta 2 to no avail. I have not yet tried installing windows just to see if it's a driver issue, and I really would rather not. Have you guys made any headway? It's quite painful tethering from my phone when I could be connected gigabit...

---

