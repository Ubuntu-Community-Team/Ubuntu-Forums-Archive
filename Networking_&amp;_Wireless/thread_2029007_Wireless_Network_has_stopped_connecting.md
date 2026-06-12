---
title: "Wireless Network has stopped connecting"
date: 2012-07-19
forum: Networking &amp; Wireless
---

### Post by Vetinarisdog on 2012-07-19
Installed Ubuntu 12.04 on Acer Aspire One with no problems, wireless network found and connected to with no issues but has since stopped working without warning.  I have altered no settings whatsoever and installed nothing aside from the updates.  

Now it just loops round to "Authentication requited by wireless network".

Help please?:(

---

### Post by austinap on 2012-07-19
I've been having what sounds like the exact same issue, starting two evenings ago.  Didn't install any updates or alter any settings that I'm aware of, but now my wireless gets stuck at authentication and just keeps asking for my password ever 2 minutes or so.  My original thread is [here]("http://ubuntuforums.org/showthread.php?p=12113680#post12113680").  The network and connection works fine if I boot into Windows.  Any help at all would be fantastic, as this is extremely frustrating.

---

### Post by Vetinarisdog on 2012-07-19
Some further information.  It will connect to the Open BT Network so it seems to be a specific problem with secure networks.

---

### Post by steeldriver on 2012-07-19
please open a terminal and run the same diagnostic commands that austinap used so that we can see whether you have the same card / driver

```
lspci -nn
iwconfig
lshw -C network
```

---

### Post by Vetinarisdog on 2012-07-19
These are the results

> dave@dave-AOA150:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GSE Express Memory Controller Hub [8086:27ac] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GSE Express Integrated Graphics Controller [8086:27ae] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 2 [8086:27d2] (rev 02)
00:1c.2 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 3 [8086:27d4] (rev 02)
00:1c.3 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 4 [8086:27d6] (rev 02)
00:1d.0 USB controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 [8086:27c8] (rev 02)
00:1d.1 USB controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 02)
00:1d.2 USB controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 02)
00:1d.3 USB controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 02)
00:1d.7 USB controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 02)
00:1f.2 IDE interface [0101]: Intel Corporation 82801GBM/GHM (ICH7-M Family) SATA Controller [IDE mode] [8086:27c4] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation N10/ICH 7 Family SMBus Controller [8086:27da] (rev 02)
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
03:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR242x / AR542x Wireless Network Adapter (PCI-Express) [168c:001c] (rev 01)
04:00.0 System peripheral [0880]: JMicron Technology Corp. SD/MMC Host Controller [197b:2382]
04:00.2 SD Host controller [0805]: JMicron Technology Corp. Standard SD Host Controller [197b:2381]
04:00.3 System peripheral [0880]: JMicron Technology Corp. MS Host Controller [197b:2383]
04:00.4 System peripheral [0880]: JMicron Technology Corp. xD Host Controller [197b:2384]

> lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"BTFON"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 12:01:3B:9A:D8:62   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=56/70  Signal level=-54 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:10   Missed beacon:0

eth0      no wireless extensions.

> PCI (sysfs)


  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:68:f2:61:d6
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=N/A latency=0 multicast=yes port=MII speed=10Mbit/s
       resources: irq:44 ioport:3000(size=256) memory:31010000-31010fff memory:31000000-3100ffff memory:31020000-3103ffff
  *-network
       description: Wireless interface
       product: AR242x / AR542x Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 00:23:4d:4f:1e:df
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k driverversion=3.2.0-23-generic-pae firmware=N/A ip=10.36.11.90 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:18 memory:35200000-3520ffff
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.

  

---

