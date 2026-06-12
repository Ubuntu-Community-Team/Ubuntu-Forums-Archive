---
title: "Atheros 928"
date: 2009-03-25
forum: Networking &amp; Wireless
---

### Post by bluestreek on 2009-03-25
nabling ath9k

To enable ath9k, you must first enable mac80211:

Networking --->
Wireless --->
<M> Improved wireless configuration API
<M> Generic IEEE 802.11 Networking Stack (mac80211)

You can then enable ath9k in the kernel configuration under

Device Drivers --->[*] Network device support --->
Wireless LAN --->
<M> Atheros 802.11n wireless cards support

I have no idea what this means or where these "Networking" or "Wireless" menu's are. Also I am trying to setup Kismet and it says I have to set capture sources but im not sure how what to put in the format thing.

# Sources are defined as:
# source=sourcetype,interface,name[,initialchannel]
source=none,none,addme

Any help would be great. I have Atheros card 928x In my laptop (At least thats what its called in device manager in windows) Its wireless n. I have Ubuntu 8.10 and ath9x is meant to be included in the kernel I think.

---

### Post by pytheas22 on 2009-03-25
The instructions that you found look like they're for compiling a Linux kernel.  That's not what you want to do.  The Ubuntu kernel already has wireless drivers built-in.

Does your wireless card work on Ubuntu in normal mode?  If so, there's not much more you need to do to make it work with kismet (you just need to specify the interface name, which should be 'wlan0' it's being driven by ath9k, in the configuration file).

---

### Post by bluestreek on 2009-03-25
name@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

ppp0      no wireless extensions.

I don't exactly know what that means but my wireless isn't working lets put it that way.

---

### Post by pytheas22 on 2009-03-25
What is the output of these commands:
```

lspci -nn
lshw -C Network
```

---

### Post by bluestreek on 2009-03-25
**[SIZE="4"]root@ubuntu:~# lspci -nn[/SIZE]**
00:00.0 Host bridge [0600]: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub [8086:2a40] (rev 07)
00:01.0 PCI bridge [0604]: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port [8086:2a41] (rev 07)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 03)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 [8086:2938] (rev 03)
00:1a.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 [8086:2939] (rev 03)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 [8086:2940] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 [8086:2942] (rev 03)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 [8086:2944] (rev 03)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 [8086:2946] (rev 03)
00:1c.4 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 [8086:2948] (rev 03)
00:1c.5 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 [8086:294a] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 93)
00:1f.0 ISA bridge [0601]: Intel Corporation ICH9M LPC Interface Controller [8086:2919] (rev 03)
00:1f.2 SATA controller [0106]: Intel Corporation ICH9M/M-E SATA AHCI Controller [8086:2929] (rev 03)
01:00.0 VGA compatible controller [0300]: nVidia Corporation GeForce 9600M GS [10de:0648] (rev a1)
03:00.0 Network controller [0280]: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) [168c:002a] (rev 01)
08:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 02)
09:01.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 05)
09:01.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 22)
09:01.2 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 12)
09:01.3 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev 12)
**[SIZE="4"]root@ubuntu:~# lshw -c Network[/SIZE]**
  *-network UNCLAIMED     
       description: Network controller
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 02
       serial: 00:22:15:2a:f2:4f
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no module=r8169 multicast=yes port=twisted pair
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 52:7a:00:bd:60:1c
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

---

### Post by pytheas22 on 2009-03-25
Please try running these commands:
```

sudo apt-get install linux-backports-modules-intrepid
echo ath9k | sudo tee -a /etc/modules
echo ath5k | sudo tee -a /etc/modules
```

Then reboot, and post the output of:
```

lshw -C Network
dmesg | grep -e ath -e wlan
lsmod | grep ath
uname -rm
```

---

### Post by bluestreek on 2009-03-26
dmesg | grep -e ath -e wlan
[   13.583753] ath9k: 0.1
[   13.583983] ath9k 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   13.583994] ath9k 0000:03:00.0: setting latency timer to 64
[   14.031401] phy0: Selected rate control algorithm 'ath9k_rate_control'
[   14.179805] Registered led device: ath9k-phy0:radio
[   14.179820] Registered led device: ath9k-phy0:assoc
[   14.179836] Registered led device: ath9k-phy0:tx
[   14.179850] Registered led device: ath9k-phy0:rx
[   38.971101] ADDRCONF(NETDEV_UP): wlan0: link is not ready


root@ubuntu:~# lshw -C Network
  *-network               
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 01
       serial: 00:15:af:ce:b6:db
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath9k latency=0 module=ath9k multicast=yes wireless=IEEE 802.11bgn
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 02
       serial: 00:22:15:2a:f2:4f
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.0.11 latency=0 link=yes module=r8169 multicast=yes port=MII speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 2a:9a:10:cb:2c:36
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
root@ubuntu:~# 


iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.


 lsmod | grep ath
ath5k                 116612  0 
ath9k                 250416  0 
rfkill                 17176  2 ath9k
lbm_cw_mac80211       215856  2 ath5k,ath9k
lbm_cw_cfg80211        46744  2 ath5k,lbm_cw_mac80211
led_class              12164  3 ath5k,ath9k,asus_laptop


uname -rm
2.6.27-11-generic i686

---

### Post by pytheas22 on 2009-03-26
The device is recognized now.  Can you connect?

---

