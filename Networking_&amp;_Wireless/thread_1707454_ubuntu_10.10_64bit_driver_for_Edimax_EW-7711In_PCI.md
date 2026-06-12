---
title: "ubuntu 10.10 64bit driver for Edimax EW-7711In PCI card"
date: 2011-03-15
forum: Networking &amp; Wireless
---

### Post by eldadz on 2011-03-15
Hi
I can't find a working driver for this card. Notice that I use 64bit ubuntu.

Some data that can help:
1. desktop

2. lspci -nn
03:07.0 Network controller [0280]: RaLink Device [1814:3060]

3. iwconfig wlan0
wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

4. lsmod | grep -e rt2 -e rt3
rt2800pci              10233  0 
rt2800lib              31970  1 rt2800pci
rt2x00usb              11316  1 rt2800lib
rt2x00pci               6993  1 rt2800pci
crc_ccitt               1699  1 rt2800pci
rt2x00lib              31575  4 rt2800pci,rt2800lib,rt2x00usb,rt2x00pci
led_class               3393  1 rt2x00lib
mac80211              266657  3 rt2x00usb,rt2x00pci,rt2x00lib
cfg80211              170293  2 rt2x00lib,mac80211
eeprom_93cx6            1789  1 rt2800pci

5. dmesg | grep -e rt2 -e rt3
[    9.150551] rt2800pci 0000:03:07.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    9.157970] Registered led device: rt2800pci-phy0::radio
[    9.157987] Registered led device: rt2800pci-phy0::assoc
[    9.157999] Registered led device: rt2800pci-phy0::quality

6. sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 03
       serial: 1c:6f:65:4c:4e:e4
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:41 ioport:de00(size=256) memory:fdaff000-fdafffff memory:fdaf8000-fdafbfff memory:fda00000-fda1ffff
  *-network
       description: Wireless interface
       product: RaLink
       vendor: RaLink
       physical id: 7
       bus info: pci@0000:03:07.0
       logical name: wlan0
       version: 00
       serial: 00:1f:1f:a6:0e:c0
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci driverversion=2.6.35-22-generic firmware=N/A latency=32 link=no maxlatency=4 mingnt=2 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:21 memory:fdce0000-fdceffff

7. iwlist wlan0 scanning
wlan0     No scan results

8. lsb_release -d
Description:    Ubuntu 10.10

9. uname -mr
2.6.35-22-generic x86_64

10. sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...       [ OK ]


Thanks,
Eldad

---

### Post by eldadz on 2011-03-16
can someone please help? any idea?

---

