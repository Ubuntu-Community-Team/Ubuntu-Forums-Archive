---
title: "modem connection  problems"
date: 2011-07-31
forum: Networking &amp; Wireless
---

### Post by marijke on 2011-07-31
I've got 2 laptops with ubuntu on it. One communicates with the modem, the other refuses to. For as far as I can see, all settings are the same. Modem and internet works, this one laptop is just being a donkey.

Working laptop: Lenovo 3000 N100
Donkey laptop: Acer Aspire 9300
Modem: Netcomm NB6plus4

we are using ADSL+

I have no idea what other information to give, internet connections are not my field. I can only see connection information on the working laptop, on the donkey, this link shows in grey and is unclickable.

Hope someone can help me, we need the other laptop to work.

---

### Post by dandnsmith on 2011-07-31
I can see no mention of wireless in the modem details I've found by googling, so, have you tried swapping over the ports the machines used, or even using other ports of the 4 you have?
Other things being equal, I'd be wondering whether you have some MAC filtering set up which blocks the non-working machine.

---

### Post by marijke on 2011-08-01
Thanks,

its a wired modem and I've tried all the ports. 

I'll look up this MAC filter, see if that does anything.

---

### Post by marijke on 2011-08-01
So the mac is for wireless, that is not the problem here.

I called the internet provider and they said it is probably something to do with the network adapter. I have no idea.

---

### Post by marijke on 2011-08-02
Isn't there anyone who can help me with this?

---

### Post by thefasterblueone on 2011-08-02
Post the results of:

```
rfkill list
```

---

### Post by dineshs on 2011-08-03
Please post the result (both machines) of ```
sudo lshw -C network
```

---

### Post by dandnsmith on 2011-08-03
Sorry about the lack of response - I've had other worries the last couple of days.
If the ISP says it could be the network adapter, then that is worth taking seriously. Assuming you use wire to connect to the modem, then there isn't a lot that can go wrong except failure or drivers which don't work.

If it's failed, then the only recourse is probably to plug in some sort of adapter.
If it's drivers, then there is a bit of research to be done involving the release of Ubuntu you're using (on the failing machine) and the port details (I think that last command suggested will give that to you)

HTH

---

### Post by marijke on 2011-08-08
The results of rfkill list is:

> 0: phy0: wireless LAN 
soft blocked: no
hard blocked: no
1: acer-wireless: wireless LAN
soft blocked: no
hard blocked: no

note, we haven't got wireless connection.

---

### Post by marijke on 2011-08-08
results for the sudo lshw:
working laptop:
>  *-network DISABLED      
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 02
       serial: 00:19:d2:98:25:00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:26 memory:d0000000-d0000fff
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:05:01.0
       logical name: eth0
       version: 10
       serial: 00:0f:b0:d3:48:48
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.2 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: irq:21 ioport:2000(size=256) memory:d0100000-d01000ff


and for donkey:
>  *-network      
       description: network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list 
       configuration: driver=b43-pci-bridge  latency=0 
       resources: irq:19 memory:c3000000-c3003fff
  *-network DISABLED
       description: wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:19:7e:d2:42:b4
       size: 100MB/s
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg


---

### Post by dineshs on 2011-08-09
From the output of sudo lshw -C network I think your ethernet card is not detected.What does ```
lspci -nn 
```say

---

### Post by marijke on 2011-08-18
> 00:00.0 RAM memory [0500]: nVidia Corporation C51 Host Bridge [10de:02f3] (rev a2)
00:00.1 RAM memory [0500]: nVidia Corporation C51 Memory Controller 0 [10de:02fa] (rev a2)
00:00.2 RAM memory [0500]: nVidia Corporation C51 Memory Controller 1 [10de:02fe] (rev a2)
00:00.3 RAM memory [0500]: nVidia Corporation C51 Memory Controller 5 [10de:02f8] (rev a2)
00:00.4 RAM memory [0500]: nVidia Corporation C51 Memory Controller 4 [10de:02f9] (rev a2)
00:00.5 RAM memory [0500]: nVidia Corporation C51 Host Bridge [10de:02ff] (rev a2)
00:00.6 RAM memory [0500]: nVidia Corporation C51 Memory Controller 3 [10de:027f] (rev a2)
00:00.7 RAM memory [0500]: nVidia Corporation C51 Memory Controller 2 [10de:027e] (rev a2)
00:02.0 PCI bridge [0604]: nVidia Corporation C51 PCI Express Bridge [10de:02fc] (rev a1)
00:03.0 PCI bridge [0604]: nVidia Corporation C51 PCI Express Bridge [10de:02fd] (rev a1)
00:04.0 PCI bridge [0604]: nVidia Corporation C51 PCI Express Bridge [10de:02fb] (rev a1)
00:05.0 VGA compatible controller [0300]: nVidia Corporation C51 [GeForce Go 6100] [10de:0247] (rev a2)
00:09.0 RAM memory [0500]: nVidia Corporation MCP51 Host Bridge [10de:0270] (rev a2)
00:0a.0 ISA bridge [0601]: nVidia Corporation MCP51 LPC Bridge [10de:0260] (rev a3)
00:0a.1 SMBus [0c05]: nVidia Corporation MCP51 SMBus [10de:0264] (rev a3)
00:0a.3 Co-processor [0b40]: nVidia Corporation MCP51 PMU [10de:0271] (rev a3)
00:0b.0 USB Controller [0c03]: nVidia Corporation MCP51 USB Controller [10de:026d] (rev a3)
00:0b.1 USB Controller [0c03]: nVidia Corporation MCP51 USB Controller [10de:026e] (rev a3)
00:0d.0 IDE interface [0101]: nVidia Corporation MCP51 IDE [10de:0265] (rev f1)
00:0e.0 IDE interface [0101]: nVidia Corporation MCP51 Serial ATA Controller [10de:0266] (rev f1)
00:10.0 PCI bridge [0604]: nVidia Corporation MCP51 PCI Bridge [10de:026f] (rev a2)
00:10.1 Audio device [0403]: nVidia Corporation MCP51 High Definition Audio [10de:026c] (rev a2)
00:14.0 Bridge [0680]: nVidia Corporation MCP51 Ethernet Controller [10de:0269] (rev a3)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
04:06.0 CardBus bridge [0607]: Texas Instruments PCIxx12 Cardbus Controller [104c:8039]
04:06.2 Mass storage controller [0180]: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD) [104c:803b]


I have no idea what this means.

---

### Post by dineshs on 2011-08-18
lspci lists all PCI devices
-nn also shows device and vendor ids.
to get details of what a command does,run *man* followed by the command.eg: *man lspci*
Now on to the problem.The list only shows this
> 01:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01
which is a wifi card.I dont see a wired ethernet
> Its a wired modem and I've tried all the ports. Your ethernet port I think is faulty.

---

### Post by marijke on 2011-08-18
why would the port be suddenly faulty? It worked fine until a few weeks ago, when the internet provider changed stuff from their end. 

if it is faulty, what does one do about that?

---

### Post by dineshs on 2011-08-18
> why would the port be suddenly faulty?As I told I am not sure.Is it disabled in BIOS? Is your machine dual boot?Is the connection OK on windows?
> if it is faulty, what does one do about that?If it is a hardware problem for sure contact service person.

---

### Post by marijke on 2011-08-18
no windows in my house, except the ones you look through.

I'll check the BIOS and if that fails, ask the cute computer guy at work tomorrow if he can help me out.

---

### Post by marijke on 2011-08-18
I checked the BIOS and see no such thing as port being enabled or disabled. There is "network boot: enabled"

---

### Post by dineshs on 2011-08-18
which ubuntu version are you using ?Have you tried a live cd?Is the lspci output same for live cd?

---

### Post by marijke on 2011-08-18
we've got 10.04

not sure if we have a live cd here, we just moved and probably threw them out. I'll check though or find/burn one. I'll update once I found it.

---

### Post by marijke on 2011-08-18
I found an old 8.04 version and it shows exactly the same details for the lscpi.

Internet works though! so the port is not broken yay.

---

### Post by marijke on 2011-08-18
for the sudo lshw -C network I got the same results with the difference that the physical id is 0 and 1, instead of 1 and 2.

rfkill didn't work, no such command

---

### Post by dineshs on 2011-08-19
> I found an old 8.04 version and it shows exactly the same details for the lscpi.
Internet works though! so the port is not broken yay.Just to make sure , are you using wired (or wireless)? What is the result of ```
ifconfig -a
``` [COLOR="Red"] on live CD when the connection is working[/COLOR]?

---

### Post by marijke on 2011-08-19
> ubuntu@ubuntu:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:16:d3:e0:3e:db  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:d3ff:fee0:3edb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:303 errors:0 dropped:0 overruns:0 frame:0
          TX packets:295 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:309488 (302.2 KB)  TX bytes:38326 (37.4 KB)
          Interrupt:22 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:868 errors:0 dropped:0 overruns:0 frame:0
          TX packets:868 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:43400 (42.3 KB)  TX bytes:43400 (42.3 KB)

wlan0     Link encap:Ethernet  HWaddr 00:19:7e:d2:42:b4  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-19-7E-D2-42-B4-00-00-00-00-00-00-00-00-00-00  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


this is what came up with the ifconfig -a
It is wired internet.

---

