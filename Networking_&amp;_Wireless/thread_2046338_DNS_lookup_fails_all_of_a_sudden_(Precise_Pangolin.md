---
title: "DNS lookup fails all of a sudden (Precise Pangolin)"
date: 2012-08-22
forum: Networking &amp; Wireless
---

### Post by ChadHerman on 2012-08-22
I own an HP Pavillion p6520y with Ubuntu 12.04 installed. This morning, I was unable to access the internet. Chromium tells me "The server at [www.google.com]("http://www.google.com") can't be found, because the DNS lookup failed." Firefox says "Server not found". Because I have had issues with Ubuntu and networking in the past, I initially thought this was a driver issue, but it didn't match the symptoms I had encountered previously. I contacted my ISP and they ran some diagnostics. The cable modem was running fine and they could see my computer. I narrowed down the cause to be something on my system. I ran a few live CDs (Crunchbang, Mint, etc.) to see if it was the installed OS. Unfortunately, none of them could access the internet either. I was able to connect from an ancient laptop running Debian Squeeze. I downloaded the driver (RealTek r616808.032.00), copied it to my desktop and installed it to no avail.

Here are some of my system specifics:

```
dmesg | tail
```> 
[   21.661675] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   21.835451] r8168: eth0: link down
[   21.836408] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   21.837469] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   22.033587] vboxpci: IOMMU not found (not registered)
[   23.090082] radeon 0000:01:05.0: texture bo too small (1600 900 26 0 -> 5785600 have 5763072)
[   23.090086] radeon 0000:01:05.0: alignments 1600 64 8 256
[   23.090088] [drm:radeon_cs_ioctl] *ERROR* Invalid command stream !
[   23.450313] r8168: eth0: link up
[   23.450984] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   23.832029] r8168: eth0: link up
[   24.201765] init: plymouth-stop pre-start process (1555) terminated with status 1
[   34.176032] eth0: no IPv6 routers present```
lfconfig
```> 
eth0      Link encap:Ethernet  HWaddr 78:e7:d1:ca:3d:ae  
          inet addr:68.199.112.124  Bcast:68.199.115.255  Mask:255.255.252.0
          inet6 addr: fe80::7ae7:d1ff:feca:3dae/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:750 errors:0 dropped:0 overruns:0 frame:0
          TX packets:121 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:45564 (45.5 KB)  TX bytes:14235 (14.2 KB)
          Interrupt:42 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:36 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2174 (2.1 KB)  TX bytes:2174 (2.1 KB)```
lsmod | grep r8168
```> r8168                 244911  0 ```
lspci
```> 00:00.0 Host bridge: Advanced Micro Devices [AMD] RS880 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (int gfx)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 1)
00:0a.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 5)
00:11.0 RAID bus controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 SATA Controller [Non-RAID5 mode]
00:12.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.1 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0 USB OHCI1 Controller
00:12.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.1 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0 USB OHCI1 Controller
00:13.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: Advanced Micro Devices [AMD] nee ATI SBx00 SMBus Controller (rev 3c)
00:14.2 Audio device: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 LPC host controller
00:14.4 PCI bridge: Advanced Micro Devices [AMD] nee ATI SBx00 PCI to PCI Bridge
00:14.5 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:05.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RS880 [Radeon HD 4200]
02:00.0 Network controller: Ralink corp. RT3090 Wireless 802.11n 1T/1R PCIe
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
04:06.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev c0)```
uname -a
```> Linux ubuntu 3.2.0-29-generic #46-Ubuntu SMP Fri Jul 27 17:03:23 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by papibe on 2012-08-22
Hi ChadHerman. Welcome to the forums ):P

Could you post the result of these commands?
```
lspci -nnk | grep -iA2 eth

sudo lshw -C network

cat /etc/network/interfaces
```
Regards.

---

### Post by ChadHerman on 2012-08-22
> **papibe said:**
> Hi ChadHerman. Welcome to the forums ):P

Could you post the result of these commands?
```
lspci -nnk | grep -iA2 eth

sudo lshw -C network

cat /etc/network/interfaces
```Regards.

Hi papibe. Thanks for your response. Here's the output:
```
lspci -nnk | grep -iA2 eth
```> 03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 03)
    Subsystem: Hewlett-Packard Company Device [103c:2a92]
    Kernel driver in use: r8168```
sudo lshw -C network
```> 
  *-network DISABLED
       description: Wireless interface
       product: RT3090 Wireless 802.11n 1T/1R PCIe
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 00
       serial: 70:f1:a1:8f:8c:6b
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci driverversion=3.2.0-29-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:fe9f0000-fe9fffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 03
       serial: 78:e7:d1:ca:3d:ae
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8168 driverversion=8.032.00-NAPI duplex=full ip=68.199.112.124 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:42 ioport:d800(size=256) memory:feaff000-feafffff memory:fdffc000-fdffffff memory:feac0000-feadffff```
cat /etc/network/interfaces
```> 
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
#NetworkManager
#iface eth0 inet dhcp

---

### Post by papibe on 2012-08-22
Comment the line 'auto eth0' on your interfaces, so it looks like this:
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
**[COLOR="Red"]#[/COLOR]**auto eth0
#NetworkManager
#iface eth0 inet dhcp 
```

Then restart your network:
```
sudo service network-manager stop

sudo service network-manager start
```
Let us know how it goes.
Regards.

---

### Post by ChadHerman on 2012-08-22
> **papibe said:**
> Comment the line 'auto eth0' on your interfaces, so it looks like this:
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
**[COLOR=Red]#[/COLOR]**auto eth0
#NetworkManager
#iface eth0 inet dhcp 
```Then restart your network:
```
sudo service network-manager stop

sudo service network-manager start
```Let us know how it goes.
Regards.

papibe,

I tried it, but the DNS lookup still fails.

---

### Post by papibe on 2012-08-22
Try this:
```
sudo ifconfig eth0 up
```
and then again:
```
sudo service networking-manager restart
```
Tell us how it goes.
Regards.

---

### Post by ChadHerman on 2012-08-22
> **papibe said:**
> Try this:
```
sudo ifconfig eth0 up
```and then again:
```
sudo service networking-manager restart
```Tell us how it goes.
Regards.

It still doesn't work.

---

### Post by papibe on 2012-08-22
Did any of the other settings change?

Could you post the result of these commands?
```
ifconfig

route -n

cat /etc/resolv.conf

cat /var/run/nm-dns-dnsmasq.conf
```
Regards.

---

### Post by ChadHerman on 2012-08-22
> **papibe said:**
> Did any of the other settings change?

Could you post the result of these commands?
```
ifconfig

route -n

cat /etc/resolv.conf

cat /var/run/nm-dns-dnsmasq.conf
```Regards.

```
ifconfig
```> eth0      Link encap:Ethernet  HWaddr 78:e7:d1:ca:3d:ae  
          inet addr:68.199.112.124  Bcast:68.199.115.255  Mask:255.255.252.0
          inet6 addr: fe80::7ae7:d1ff:feca:3dae/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3877 errors:0 dropped:0 overruns:0 frame:0
          TX packets:909 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:236004 (236.0 KB)  TX bytes:116119 (116.1 KB)
          Interrupt:42 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1950 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1950 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:127601 (127.6 KB)  TX bytes:127601 (127.6 KB)
```
route -n
```> Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         68.199.112.1    0.0.0.0         UG    0      0        0 eth0
68.199.112.0    0.0.0.0         255.255.252.0   U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0```
 cat /etc/resolv.conf
```> # Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.0.1```
cat /var/run/nm-dns-dnsmasq.conf
```> server=167.206.245.129
server=167.206.245.130

---

### Post by papibe on 2012-08-22
Looks OK.

Could you test some addresses?
```
nslookup ubuntu.com

dig yahoo.com
```
Regards.

---

### Post by ChadHerman on 2012-08-23
> **papibe said:**
> Looks OK.

Could you test some addresses?
```
nslookup ubuntu.com

dig yahoo.com
```Regards.

It failed. It said:
> ;; connection timed out; no servers could be reached

---

### Post by papibe on 2012-08-23
Try disabling the Network Manager's dnsmasq plugin. Read [here]("http://ubuntuforums.org/showpost.php?p=11923702&postcount=40").

Let us know how it goes.
Regards.

---

### Post by ChadHerman on 2012-08-23
> **papibe said:**
> Try disabling the Network Manager's dnsmasq plugin. Read [here]("http://ubuntuforums.org/showpost.php?p=11923702&postcount=40").

Let us know how it goes.
Regards.

After making the changes to the conf file, I still can't get a connection.

---

### Post by ChadHerman on 2012-08-23
I'm able to get back online. I don't know what fixed it. After trying papibe's advice, nothing worked and I called it a night. I connected the Ethernet cable to my desktop this afternoon and I had a slow connection. Google's homepage showed up, but the logo couldn't load. I figured that one of the changes I had made the night before was responsible for the slow connection (and for the fact that I was online to begin with). I uncommented the line "#dns=dnsmasq" in NetworkManager.conf and ran sudo service network-manager restart and now my connection is back at 100%.

I would like to thank papibe for his assistance. I'm going to reboot to make sure I haven't celebrated too soon.

---

