---
title: "Broadcom BCM4318 Wireless on ubuntu 8.04 HPzv6000 notebook"
date: 2010-08-21
forum: Networking &amp; Wireless
---

### Post by JoshDN on 2010-08-21
HP ZV6000 Notebook running ubuntu 8.04. WUBI. Wired connection works good. Cannot connect with wireless. Wireless networks don't even show up. I tried to enable the Broadcom B43 wireless driver. When i click on it I get the dialog box:

 "While this driver itself is free software, it relies on proprietary firmware which cannot be legally shipped with the operating system. Your hardware will not work without the firmware.

After clicking on "enable" status is still "not in use" even after reboot.

Here is the output of "lspci" "ifconfig" "iwconfig" "sudo lshw -C network":
```
josh@josh-laptop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 10)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 01)
00:14.6 Modem: ATI Technologies Inc SB400 AC'97 Modem Controller (rev 01)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)
03:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
03:04.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
03:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
josh@josh-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0f:b0:77:39:a3  
          inet addr:192.168.1.105  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:b0ff:fe77:39a3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10400 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9006 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:12071470 (11.5 MB)  TX bytes:1241447 (1.1 MB)
          Interrupt:22 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1946 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1946 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:97300 (95.0 KB)  TX bytes:97300 (95.0 KB)

josh@josh-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

josh@josh-laptop:~$ sudo lshw -C network
[sudo] password for joshneymeiyer: 
  *-network:0             
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:03:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@0000:03:06.0
       logical name: eth0
       version: 10
       serial: 00:0f:b0:77:39:a3
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.105 latency=128 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:14:a5:15:7e:93
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

```I've read several posts that are similar to this issue, none of which were easily solved. So any help is very much appreciated. Thanks in advance to the community who has been very helpful to noobs like me.

---

### Post by ieee488 on 2010-08-22
You should seriously consider upgrading to 9.10

---

### Post by JoshDN on 2010-08-22
Sure, i'll give that a go. What are your thoughts on 10.04? It seems like there is even more wireless problems in that release. I'm not experiencing these setbacks because i'm running WUBI am I?

---

### Post by ieee488 on 2010-08-22
Sorry, I don't have any experience using Wubi.

I always install Ubuntu as a pure dual-boot.

I am running 10.04, but frankly, I am not impressed.  There was an issue with the video driver which someone posted a solution for. But for a LTS I wasn't expecting that. From reading the boards, upgrading to 10.04 from 9.10 caused many people's wireeless not to work.

Fortunately for me, the wired ethernet works on my home laptop and my T-mobile mobile broadband USB device works on the laptop I keep at work.

---

### Post by JoshDN on 2010-08-22
Excellent suggestion!

I did the upgrade and wireless as well as the rest of my hardware works perfect.

Many many thanks!!!

---

### Post by ieee488 on 2010-08-22
great!

---

