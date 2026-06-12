---
title: "[Wireless] I'm connected to wireless but browser(s) doesn't load pages."
date: 2011-12-13
forum: Networking &amp; Wireless
---

### Post by Exenis on 2011-12-13
Hi all.  

I have a problem for several weeks. I can not connect to my home network without using a Belkin usb wireless which I usually use on my desktop computer. This fact make me think that my PCI is broken but this one WORKS with all the rest of Wireless Networks.

When I say that PCI doesn't work properly I mean that the PCI recognizes the network "Linksys", it connects to it but Firefox/Chromium and software-center don't load pages and download packages.

What I can tell you is that I also installed WICD, but nothing, the Wifi does not go to unless I attack the usual Belkin memory stick; ipv4 and ipv6 settings are set, respectively Automatic (DHCP) and Ignore (I tried all combinations but nothing works); I formatted the pc several times also changing the Ubuntu distro, but nothing worked for me. My home network is composed of a tiscali modem connected to a Cisco access point via Ethernet.

Here there are:


iwconfig


```


lo * * * *no wireless extensions.

eth0 * * *no wireless extensions.

wlan0 * * IEEE 802.11bgn *ESSID:off/any *
 * * * * *Mode:Managed *Access Point: Not-Associated * Tx-Power=14 dBm * 
 * * * * *Retry *long limit:7 * RTS thr:off * Fragment thr:off
 * * * * *Power Management:off
 * * * * *
wlan1 * * IEEE 802.11bgn *ESSID:"linksys" *
 * * * * *Mode:Managed *Frequency:2.422 GHz *Access Point: 00:25:9C:8F:28:C2 * 
 * * * * *Bit Rate=39 Mb/s * Tx-Power=20 dBm * 
 * * * * *Retry *long limit:7 * RTS thr:off * Fragment thr:off
 * * * * *Power Management:on
 * * * * *Link Quality=51/70 *Signal level=-59 dBm *
 * * * * *Rx invalid nwid:0 *Rx invalid crypt:0 *Rx invalid frag:0
 * * * * *Tx excessive retries:669 *Invalid misc:89 * Missed beacon:0

```


ifconfig


```


eth0 * * *Link encap:Ethernet *HWaddr 60:eb:69:38:5b:41 *
 * * * * *UP BROADCAST MULTICAST *MTU:1500 *Metric:1
 * * * * *RX packets:0 errors:0 dropped:0 overruns:0 frame:0
 * * * * *TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
 * * * * *collisions:0 txqueuelen:1000 
 * * * * *RX bytes:0 (0.0 B) *TX bytes:0 (0.0 B)
 * * * * *Interrupt:42 Base address:0x4000 

lo * * * *Link encap:Local Loopback *
 * * * * *inet addr:127.0.0.1 *Mask:255.0.0.0
 * * * * *inet6 addr: ::1/128 Scope:Host
 * * * * *UP LOOPBACK RUNNING *MTU:16436 *Metric:1
 * * * * *RX packets:239 errors:0 dropped:0 overruns:0 frame:0
 * * * * *TX packets:239 errors:0 dropped:0 overruns:0 carrier:0
 * * * * *collisions:0 txqueuelen:0 
 * * * * *RX bytes:20124 (20.1 KB) *TX bytes:20124 (20.1 KB)

wlan0 * * Link encap:Ethernet *HWaddr 4c:0f:6e:1b:08:ee *
 * * * * *inet6 addr: fe80::4e0f:6eff:fe1b:8ee/64 Scope:Link
 * * * * *UP BROADCAST MULTICAST *MTU:1500 *Metric:1
 * * * * *RX packets:361 errors:0 dropped:0 overruns:0 frame:0
 * * * * *TX packets:522 errors:0 dropped:0 overruns:0 carrier:0
 * * * * *collisions:0 txqueuelen:1000 
 * * * * *RX bytes:66392 (66.3 KB) *TX bytes:80478 (80.4 KB)

wlan1 * * Link encap:Ethernet *HWaddr 00:22:75:40:cd:ef *
 * * * * *inet addr:192.168.1.105 *Bcast:192.168.1.255 *Mask:255.255.255.0
 * * * * *inet6 addr: fe80::222:75ff:fe40:cdef/64 Scope:Link
 * * * * *UP BROADCAST RUNNING MULTICAST *MTU:1500 *Metric:1
 * * * * *RX packets:26812 errors:0 dropped:0 overruns:0 frame:0
 * * * * *TX packets:19295 errors:0 dropped:0 overruns:0 carrier:0
 * * * * *collisions:0 txqueuelen:1000 
 * * * * *RX bytes:31845846 (31.8 MB) *TX bytes:3196751 (3.1 MB)


```


and lspci

```


00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
01:00.0 VGA compatible controller: ATI Technologies Inc Manhattan [Mobility Radeon HD 5400 Series]
01:00.1 Audio device: ATI Technologies Inc Manhattan HDMI Audio [Mobility Radeon HD 5000 Series]
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
7f:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
7f:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
7f:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
7f:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
7f:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
7f:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)


```

.. as you can see I am now connected to linksys with the famous Belkin key, that Ubuntu (11.10) called "Ralink 802.11 n WLAN".

Thanks for the support.


ps: Sorry for my BAAAAAD english. I tried to do my best!


nis

---

### Post by Exenis on 2012-01-24
Uhm, any help?

---

