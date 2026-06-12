---
title: "Another wireless thread [Intel PRO/Wireless 5300 AGN] please help!"
date: 2009-11-04
forum: Networking &amp; Wireless
---

### Post by Nottaken on 2009-11-04
I am completely new to ubuntu so all help would be appreciated.
I read about a dozen threads and know people will want me to post the following:

ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 00:24:21:61:30:60  
          inet addr:192.168.1.130  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::224:21ff:fe61:3060/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10828 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8425 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:12909259 (12.9 MB)  TX bytes:1326399 (1.3 MB)
          Interrupt:29 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 RX bytes:960 (960.0 B)  TX bytes:960 (960.0 B)
```iwconfig:
```
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```sudo lshw -C network:
```
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 02
       serial: 00:24:21:61:30:60
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.130 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:29 ioport:e800(size=256) memory:feaff000-feafffff memory:fcff0000-fcffffff(prefetchable) memory:feac0000-feadffff(prefetchable)
  *-network DISABLED
       description: Wireless interface
       product: PRO/Wireless 5300 AGN [Shiloh] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wmaster0
       version: 00
       serial: 00:16:ea:e5:0b:be
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:30 memory:febfe000-febfffff
```lspci -vv -d 8086:4235:
```

05:00.0 Network controller: Intel Corporation PRO/Wireless 5300 AGN [Shiloh] Network Connection
    Subsystem: Intel Corporation Device 1101
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 32 bytes
    Interrupt: pin A routed to IRQ 30
    Region 0: Memory at febfe000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: <access denied>
    Kernel driver in use: iwlagn
    Kernel modules: iwlagn
```The lshw appears to state that my wireless is disabled , how do I go about toggling it? 
sudo ifconfig wlan0 up:
```
SIOCSIFFLAGS: Unknown error 132
```There is no physical switch for my wireless nor can it be disabled through the BIOS.

Additionally the enable wireless radio button in the network applet is grayed out and can not be toggled.

EDIT:
Turns out there was a physical switch I sure do feel dumb

---

