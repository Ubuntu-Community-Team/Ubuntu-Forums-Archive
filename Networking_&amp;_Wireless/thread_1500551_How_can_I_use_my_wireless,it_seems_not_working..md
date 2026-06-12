---
title: "How can I use my wireless,it seems not working."
date: 2010-06-03
forum: Networking &amp; Wireless
---

### Post by hayphen on 2010-06-03
Hi.
This is my second day I am using my netbook remix ubuntu 10.04 on a 8gb flash disc with persistance ability.

My netbook is LG x130.

I have no idea how can I use or configure my wirelees it seems not working.I search forums and I learned a little bit "terminal" and I have an information like this about my netbook's configuration:

Thanks anyway but please don't forget I am realy a newbee!



ubuntu@ubuntu:~$ sudo lshw -C network; sudo iwlist scanning; cat etcnetworkinterfaces; cat etclsb-release; lspci -nn; lsusb; sudo lshw -short; uname -a; dmesg  grep ound; dmesg  grep b43; dmesg  grep wl; dmesg  grep witch; iwconfig; grep b43 etcmodprobe.d; grep wl etcmodprobe.d; sudo etcinit.dnetworking restart
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 02
       serial: 00:26:9e:7d:fb:33
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:27 ioport:3000(size=256) memory:50010000-50010fff(prefetchable) memory:50000000-5000ffff(prefetchable) memory:50020000-5002ffff(prefetchable)
  *-network DISABLED
       description: Wireless interface
       product: RT3090 Wireless 802.11n 1T/1R PCIe
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt3090 latency=0 multicast=yes wireless=RT2860 Wireless
       resources: irq:17 memory:54000000-5400ffff
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results

cat: etcnetworkinterfaces: No such file or directory
cat: etclsb-release: No such file or directory
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GME Express Memory Controller Hub [8086:27ac] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GME Express Integrated Graphics Controller [8086:27ae] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 2 [8086:27d2] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 [8086:27c8] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801G (ICH7 Family) IDE Controller [8086:27df] (rev 02)
00:1f.2 SATA controller [0106]: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller [8086:27c5] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation N10/ICH 7 Family SMBus Controller [8086:27da] (rev 02)
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
02:00.0 Network controller [0280]: RaLink RT3090 Wireless 802.11n 1T/1R PCIe [1814:3090]
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c52f Logitech, Inc. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 5986:0241 Acer, Inc 
Bus 001 Device 003: ID 0951:1607 Kingston Technology DataTraveler 100
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
H/W path             Device     Class       Description
=======================================================
                                system      X130-L.A7B6T
/0                              bus         UL1
/0/0                            memory      1MiB BIOS
/0/15                           memory      1GiB System Memory
/0/15/0                         memory      1GiB DIMM DDR2 Synchronous 533 MHz (1.9 ns)
/0/1a                           processor   Intel(R) Atom(TM) CPU N270   @ 1.60GHz
/0/1a/1b                        memory      512KiB L2 cache
/0/1a/1c                        memory      32KiB L1 cache
/0/1a/0.1                       processor   Logical CPU
/0/1a/0.2                       processor   Logical CPU
/0/100                          bridge      Mobile 945GME Express Memory Controller Hub
/0/100/2                        display     Mobile 945GME Express Integrated Graphics Controller
/0/100/2.1                      display     Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller
/0/100/1b                       multimedia  N10/ICH 7 Family High Definition Audio Controller
/0/100/1c                       bridge      N10/ICH 7 Family PCI Express Port 1
/0/100/1c/0          eth0       network     RTL8101E/RTL8102E PCI Express Fast Ethernet controller
/0/100/1c.1                     bridge      N10/ICH 7 Family PCI Express Port 2
/0/100/1c.1/0        wlan0      network     RT3090 Wireless 802.11n 1T/1R PCIe
/0/100/1d                       bus         N10/ICH7 Family USB UHCI Controller #1
/0/100/1d.1                     bus         N10/ICH 7 Family USB UHCI Controller #2
/0/100/1d.2                     bus         N10/ICH 7 Family USB UHCI Controller #3
/0/100/1d.3                     bus         N10/ICH 7 Family USB UHCI Controller #4
/0/100/1d.7                     bus         N10/ICH 7 Family USB2 EHCI Controller
/0/100/1e                       bridge      82801 Mobile PCI Bridge
/0/100/1f                       bridge      82801GBM (ICH7-M) LPC Interface Bridge
/0/100/1f.1                     storage     82801G (ICH7 Family) IDE Controller
/0/100/1f.2          scsi2      storage     82801GBM/GHM (ICH7 Family) SATA AHCI Controller
/0/100/1f.2/0.0.0    /dev/sda   disk        160GB FUJITSU MJA2160B
/0/100/1f.2/0.0.0/1  /dev/sda1  volume      4GiB Windows NTFS volume
/0/100/1f.2/0.0.0/2  /dev/sda2  volume      50GiB Windows NTFS volume
/0/100/1f.2/0.0.0/3  /dev/sda3  volume      95GiB Windows NTFS volume
/0/100/1f.3                     bus         N10/ICH 7 Family SMBus Controller
/0/1                 scsi6      storage     
/0/1/0.0.0           /dev/sdb   disk        8088MB SCSI Disk
/0/1/0.0.0/1         /dev/sdb1  volume      7713MiB Windows FAT volume
Linux ubuntu 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686 GNU/Linux
Usage: dmesg [-c] [-n level] [-r] [-s bufsize]
Usage: dmesg [-c] [-n level] [-r] [-s bufsize]
Usage: dmesg [-c] [-n level] [-r] [-s bufsize]
Usage: dmesg [-c] [-n level] [-r] [-s bufsize]
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     RT2860 Wireless  ESSID:""  Nickname:"RT2860STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:-87 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

grep: etcmodprobe.d: No such file or directory
grep: etcmodprobe.d: No such file or directory
sudo: etcinit.dnetworking: command not found
ubuntu@ubuntu:~$

---

### Post by chili555 on 2010-06-03
First of all, your commands are missing a few parts:> $ sudo lshw -C network; sudo iwlist scanning; cat etcnetworkinterfaces; cat etclsb-release; lspci -nn; lsusb; sudo lshw -short; uname -a; dmesg grep ound; dmesg grep b43; dmesg grep wl; dmesg grep witch; iwconfig; grep b43 etcmodprobe.d; grep wl etcmodprobe.d; sudo etcinit.dnetworking restartThese are commands that are intended to be issued one at a time. Second, it is not cat etcnetworkinterfaces it is, instead:```
cat /etc/network/interfaces
```Those slashes are important and needed. 

It is not dmesg grep b43 it is instead:```
dmesg | grep b43
```The pipe symbol, which is on the right side of my US keyboard along with \ is important and needed.

As a matter of fact, b43, nor wl have anything to do with your Realtek wireless. We would like to see:```
dmesg | grep -i RT2
dmesg | grep -i RT3
rfkill list all
```Thanks.

---

### Post by hayphen on 2010-06-03
Thanks for your help,I just updated my system and everything is OK now.Including my wireless.I will go on testing my new system ubuntu.

---

### Post by hakansamil on 2010-06-20
Solved;
just install the driver in an accurate way and it works.

---

### Post by hakansamil on 2010-06-20
Solved;
just install the driver in an accurate way and it works.

---

