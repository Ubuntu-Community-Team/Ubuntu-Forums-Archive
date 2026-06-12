---
title: "Wireless help please"
date: 2009-07-20
forum: Networking &amp; Wireless
---

### Post by HutchKC on 2009-07-20
Hi, I am a relative newbie to ubuntu and linux in general. I was fluent 10 years ago, and still have some chops, but have been in a windows world since.

At any rate, I put 9.4 on an old i386 laptop. Installation and operation is fine. It has an internal wireless card, but neither windows nor ubuntu detect it. I plug in an old Linksys WUSB11 usb card, which ubuntu detects. It also detects my wireless network. 

So, the problem is that even though I can detect my network, I cannot connect. I have WPA personal security set up on it. But the only encryption connections I am given to select from are:

> WEP 40/128-bit Key
WEP 128-bit Passphrase
LEAP
Dynamic WEP (802.1x)I've attached some output in hopes that it helps you help me. 

> tom@linux:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:d4:42:b3:c4  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:22 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan1     Link encap:Ethernet  HWaddr 00:06:25:0d:62:11  
          inet6 addr: fe80::206:25ff:fe0d:6211/64 Scope:Link
          UP BROADCAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:53 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:320 (320.0 B)

tom@linux:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
00:14.6 Modem: ATI Technologies Inc SB400 AC'97 Modem Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)
06:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

tom@linux:~$ lshw -class network
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@0000:06:06.0
       logical name: eth0
       version: 10
       serial: 00:16:d4:42:b3:c4
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=128 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network:0 DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 96:de:27:b3:62:97
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
  *-network:1
       description: Wireless interface
       physical id: 2
       logical name: wlan1
       serial: 00:06:25:0d:62:11
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=at76_usb driverversion=0.17 firmware=1.101.2-84 wireless=IEEE 802.11b
Any thoughts as to how I can add WPA personal as an option? Is it possible my network card is just too old?

TIA.

Tom

---

### Post by chili555 on 2009-07-20
> Is it possible my network card is just too old?It could be. I know of no way to add WPA capabilities to a card that was built before WPA standards were developed and finalized. You can see if your card does WPA with:```
sudo iwlist wlan1 auth
```Do you see, among other things, this?> Authentication capabilities :
		WPA
		WPA2
		CIPHER-TKIP
		CIPHER-CCMP


---

### Post by HutchKC on 2009-07-20
> **chili555 said:**
> Do you see, among other things, this?

The only output I get is "wlan1    unknown authentication information"

---

