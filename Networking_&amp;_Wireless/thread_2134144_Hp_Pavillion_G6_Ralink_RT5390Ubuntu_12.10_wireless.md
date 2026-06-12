---
title: "Hp Pavillion G6/ Ralink RT5390/Ubuntu 12.10 wireless card disabled"
date: 2013-04-10
forum: Networking &amp; Wireless
---

### Post by creynol4 on 2013-04-10
[COLOR=#333333][FONT=Ubuntu]Hello all,

I did a fresh install of Ubuntu 12.10 and opted to delete windows 7. Since then my wireless has been disable and I have not come across an answer that has fixed the problem.
Ive tried "sudo rfkill unblock all" and other inputs that have not helped.

Here's my computer Information.

chris@chris-HP-Pavilion-g6-Notebook-PC:~$ ip link set
Not enough information: "dev" argument is required.
chris@chris-HP-Pavilion-g6-Notebook-PC:~$ sudo apt-get update; sudo apt-get install hwinfo grep rfkill; sudo lshw -C network; rfkill list; sudo iwlist scan | egrep -i 'chan|ssid'; cat /etc/network/interfaces; cat /etc/lsb-release; lspci -nnk | grep -iA2 net; lsusb; nmcli nm status; sudo lshw -short; uname -a; dmesg | egrep '02:00|80211|acx|at76|ath|b43|bcm|brcm|CX|eth|ipw|ireless|irmware|isl|lbtf|orinoco|ndiswrapper|NPE|ound|p54|prism|rror|rtl|rt2|rt3|rt5|rt6|rt7|usb|witch|wl';sudo dmidecode|egrep 'anufact|roduct|erial|elease'; iwconfig; cat /etc/modprobe.d/* | egrep '80211|acx|at76|ath|b43|bcm|brcm|CX|eth|ipw|irmware|isl|lbtf|orinoco|ndiswrapper|NPE|p54|prism|rtl|rt2|rt3|rt6|rt7|wmi|witch|wl'; cat /var/lib/NetworkManager/NetworkManager.state; sudo hwinfo --netcard ; ps -aux|egrep 'wpa|icd|etwork'; netstat -rn ; cat /etc/resolv.conf; sudo lsmod
[sudo] password for chris:
Get:1 [http://security.ubuntu.com]("http://security.ubuntu.com/") quantal-security Release.gpg [933 B]
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") quantal Release.gpg
Get:2 [http://security.ubuntu.com]("http://security.ubuntu.com/") quantal-security Release [49.6 kB]
Get:3 [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") quantal-updates Release.gpg [933 B]
Hit [http://extras.ubuntu.com]("http://extras.ubuntu.com/") quantal Release.gpg
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") quantal-backports Release.gpg
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") quantal Release
Hit [http://extras.ubuntu.com]("http://extras.ubuntu.com/") quantal Release
Get:4 [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") quantal-updates Release [49.6 kB]
Get:5 [http://security.ubuntu.com]("http://security.ubuntu.com/") quantal-security/main Sources [38.2 kB]
Hit [http://extras.ubuntu.com]("http://extras.ubuntu.com/") quantal/main Sources
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") quantal-backports Release
Get:6 [http://security.ubuntu.com]("http://security.ubuntu.com/") quantal-security/restricted Sources [14 B]
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") quantal/main Sources
Hit [http://extras.ubuntu.com]("http://extras.ubuntu.com/") quantal/main amd64 Packages
Get:7 [http://security.ubuntu.com]("http://security.ubuntu.com/") quantal-security/universe Sources [16.0 kB]
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") quantal/restricted Sources
Get:8 [http://security.ubuntu.com]("http://security.ubuntu.com/") quantal-security/multiverse Sources [692 B]
Hit [http://extras.ubuntu.com]("http://extras.ubuntu.com/") quantal/main i386 Packages
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") quantal/universe Sources
Get:9 [http://security.ubuntu.com]("http://security.ubuntu.com/") quantal-security/main amd64 Packages [103 kB]
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") quantal/multiverse Sources
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") quantal/main amd64 Packages
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") quantal/restricted amd64 Packages
Get:10 [http://security.ubuntu.com]("http://security.ubuntu.com/") quantal-security/restricted amd64 Packages [14 B]
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") quantal/universe amd64 Packages
Get:11 [http://security.ubuntu.com]("http://security.ubuntu.com/") quantal-security/universe amd64 Packages [44.9 kB]
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") quantal/multiverse amd64 Packages
Get:12 [http://security.ubuntu.com]("http://security.ubuntu.com/") quantal-security/multiverse amd64 Packages [1,150 B]
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") quantal/main i386 Packages
Get:13 [http://security.ubuntu.com]("http://security.ubuntu.com/") quantal-security/main i386 Packages [103 kB]
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") quantal/restricted i386 Packages
Get:14 [http://security.ubuntu.com]("http://security.ubuntu.com/") quantal-security/restricted i386 Packages [14 B]
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") quantal/universe i386 Packages
Get:15 [http://security.ubuntu.com]("http://security.ubuntu.com/") quantal-security/universe i386 Packages [45.5 kB]
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") quantal/multiverse i386 Packages
Get:16 [http://security.ubuntu.com]("http://security.ubuntu.com/") quantal-security/multiverse i386 Packages [1,396 B]
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") quantal/main Translation-en
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") quantal-security/main Translation-en
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") quantal/multiverse Translation-en
Ign [http://extras.ubuntu.com]("http://extras.ubuntu.com/") quantal/main Translation-en_US
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") quantal-security/multiverse Translation-en
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") quantal/restricted Translation-en
Ign [http://extras.ubuntu.com]("http://extras.ubuntu.com/") quantal/main Translation-en
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") quantal-security/restricted Translation-en
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") quantal/universe Translation-en
Get:17 [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") quantal-updates/main Sources [86.9 kB]
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") quantal-security/universe Translation-en
Get:18 [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") quantal-updates/restricted Sources [1,302 B]
Get:19 [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") quantal-updates/universe Sources [81.5 kB]
Get:20 [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") quantal-updates/multiverse Sources [2,933 B]
Get:21 [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") quantal-updates/main amd64 Packages [224 kB]
Get:22 [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") quantal-updates/restricted amd64 Packages [3,048 B]
Get:23 [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") quantal-updates/universe amd64 Packages [177 kB]
Ign [http://security.ubuntu.com]("http://security.ubuntu.com/") quantal-security/main Translation-en_US
Ign [http://security.ubuntu.com]("http://security.ubuntu.com/") quantal-security/multiverse Translation-en_US
Get:24 [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") quantal-updates/multiverse amd64 Packages [7,946 B]
Ign [http://security.ubuntu.com]("http://security.ubuntu.com/") quantal-security/restricted Translation-en_US
Ign [http://security.ubuntu.com]("http://security.ubuntu.com/") quantal-security/universe Translation-en_US
Get:25 [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") quantal-updates/main i386 Packages [223 kB]
Get:26 [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") quantal-updates/restricted i386 Packages [3,067 B]
Get:27 [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") quantal-updates/universe i386 Packages [178 kB]
Get:28 [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") quantal-updates/multiverse i386 Packages [8,097 B]
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") quantal-updates/main Translation-en
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") quantal-updates/multiverse Translation-en
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") quantal-updates/restricted Translation-en
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") quantal-updates/universe Translation-en
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") quantal-backports/main Sources
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") quantal-backports/restricted Sources
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") quantal-backports/universe Sources
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") quantal-backports/multiverse Sources
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") quantal-backports/main amd64 Packages
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") quantal-backports/restricted amd64 Packages
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") quantal-backports/universe amd64 Packages
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") quantal-backports/multiverse amd64 Packages
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") quantal-backports/main i386 Packages
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") quantal-backports/restricted i386 Packages
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") quantal-backports/universe i386 Packages
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") quantal-backports/multiverse i386 Packages
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") quantal-backports/main Translation-en
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") quantal-backports/multiverse Translation-en
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") quantal-backports/restricted Translation-en
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") quantal-backports/universe Translation-en
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") quantal/main Translation-en_US
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") quantal/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") quantal/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") quantal/universe Translation-en_US
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") quantal-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") quantal-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") quantal-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") quantal-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") quantal-backports/main Translation-en_US
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") quantal-backports/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") quantal-backports/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") quantal-backports/universe Translation-en_US
Fetched 1,452 kB in 11s (125 kB/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree
Reading state information... Done
grep is already the newest version.
rfkill is already the newest version.
hwinfo is already the newest version.
The following package was automatically installed and is no longer required:
  linux-headers-3.5.0-17
Use 'apt-get autoremove' to remove it.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 05
       serial: 78:e3:b5:58:f8:04
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8105e-1.fw ip=192.168.1.70 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:41 ioport:3000(size=256) memory:b0404000-b0404fff memory:b0400000-b0403fff
  *-network DISABLED
       description: Wireless interface
       product: RT5390 Wireless 802.11n 1T/1R PCIe
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 00
       serial: cc:af:78:7f:ab:80
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci driverversion=3.5.0-26-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:18 memory:b4400000-b440ffff
  *-network
       description: Wireless interface
       physical id: 2
       bus info: usb@1:1.2
       logical name: wlan1
       serial: 00:1a:ef:17:1e:73
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8187 driverversion=3.5.0-26-generic firmware=N/A ip=10.0.1.38 link=yes multicast=yes wireless=IEEE 802.11bg
0: phy0: Wireless LAN
 Soft blocked: no
 Hard blocked: no
1: phy1: Wireless LAN
 Soft blocked: no
 Hard blocked: yes
2: hp-wifi: Wireless LAN
 Soft blocked: yes
 Hard blocked: no
eth0 Interface doesn't support scanning.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]lo Interface doesn't support scanning.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]wlan0 Interface doesn't support scanning : Network is down[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    ESSID:"sadgood"
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    ESSID:"ATT720"
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.10
DISTRIB_CODENAME=quantal
DISTRIB_DESCRIPTION="Ubuntu 12.10"
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
 Subsystem: Hewlett-Packard Company Device [103c:1693]
 Kernel driver in use: r8169
--
02:00.0 Network controller [0280]: Ralink corp. RT5390 Wireless 802.11n 1T/1R PCIe [1814:5390]
 Subsystem: Hewlett-Packard Company U98Z077.00 Half-size Mini PCIe Card [103c:1636]
 Kernel driver in use: rt2800pci
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0bda:8187 Realtek Semiconductor Corp. RTL8187 Wireless Adapter
Bus 002 Device 003: ID 045e:007d Microsoft Corp. Notebook Optical Mouse
Bus 002 Device 004: ID 04f2:b249 Chicony Electronics Co., Ltd
RUNNING STATE WIFI-HARDWARE WIFI WWAN-HARDWARE WWAN
running connected enabled disabled enabled disabled
H/W path Device Class Description
======================================================
                            system HP Pavilion g6 Notebook PC (LW259UA#A
/0 bus 1693
/0/0 memory 1MiB BIOS
/0/13 memory 4GiB System Memory
/0/13/0 memory DIMM DDR3 Synchronous 1067 MHz (0.9 n
/0/13/1 memory 4GiB SODIMM DDR3 Synchronous 1067 MHz
/0/1b processor Intel(R) Core(TM) i3 CPU M 370
/0/1b/1c memory 3MiB L3 cache
/0/1b/1e memory 256KiB L2 cache
/0/1b/1f memory 32KiB L1 cache
/0/1d memory 32KiB L1 cache
/0/100 bridge Core Processor DRAM Controller
/0/100/2 display Core Processor Integrated Graphics Co
/0/100/16 communication 5 Series/3400 Series Chipset HECI Con
/0/100/1a bus 5 Series/3400 Series Chipset USB2 Enh
/0/100/1b multimedia 5 Series/3400 Series Chipset High Def
/0/100/1c bridge 5 Series/3400 Series Chipset PCI Expr
/0/100/1c/0 eth0 network RTL8101E/RTL8102E PCI Express Fast Et
/0/100/1c.2 bridge 5 Series/3400 Series Chipset PCI Expr
/0/100/1c.2/0 wlan0 network RT5390 Wireless 802.11n 1T/1R PCIe
/0/100/1c.4 bridge 5 Series/3400 Series Chipset PCI Expr
/0/100/1c.4/0 generic RTS5209 PCI Express Card Reader
/0/100/1d bus 5 Series/3400 Series Chipset USB2 Enh
/0/100/1e bridge 82801 Mobile PCI Bridge
/0/100/1f bridge Mobile 5 Series Chipset LPC Interface
/0/100/1f.2 storage 5 Series/3400 Series Chipset 4 port S
/0/100/1f.3 bus 5 Series/3400 Series Chipset SMBus Co
/0/100/1f.6 generic 5 Series/3400 Series Chipset Thermal
/0/101 bridge Core Processor QuickPath Architecture
/0/102 bridge Core Processor QuickPath Architecture
/0/103 bridge Core Processor QPI Link 0
/0/104 bridge Core Processor QPI Physical 0
/0/105 bridge Core Processor Reserved
/0/106 bridge Core Processor Reserved
/0/1 scsi0 storage
/0/1/0.0.0 /dev/sda disk 500GB WDC WD5000BPVT-6
/0/1/0.0.0/1 /dev/sda1 volume 461GiB EXT4 volume
/0/1/0.0.0/2 /dev/sda2 volume 3893MiB Extended partition
/0/1/0.0.0/2/5 /dev/sda5 volume 3893MiB Linux swap / Solaris partitio
/0/2 scsi1 storage
/0/2/0.0.0 /dev/cdrom disk CDDVDW TS-L633R
/1 power MU06047
/2 wlan1 network Wireless interface
Linux chris-HP-Pavilion-g6-Notebook-PC 3.5.0-26-generic #42-Ubuntu SMP Fri Mar 8 23:18:20 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
[ 0.000000] DMI: Hewlett-Packard HP Pavilion g6 Notebook PC/1693, BIOS F.32 12/01/2011
[ 0.000000] No AGP bridge found
[ 0.000000] No NUMA configuration found
[ 0.000000] No AGP bridge found
[ 0.326860] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[ 1.842326] ACPI: No dock devices found.
[ 1.857685] pci 0000:02:00.0: [1814:5390] type 00 class 0x028000
[ 1.857710] pci 0000:02:00.0: reg 10: [mem 0xb4400000-0xb440ffff]
[ 1.873530] pci 0000:00:1c.4: bridge window [mem 0xb3400000-0xb43fffff]
[ 1.879632] ACPI: bus type usb registered
[ 1.879650] usbcore: registered new interface driver usbfs
[ 1.879659] usbcore: registered new interface driver hub
[ 1.879680] usbcore: registered new device driver usb
[ 1.891945] Switching to clocksource hpet
[ 1.899526] pnp: PnP ACPI: found 11 devices
[ 1.906068] pci 0000:00:1c.4: bridge window [mem 0xb3400000-0xb43fffff]
[ 1.906159] pci_bus 0000:03: resource 1 [mem 0xb3400000-0xb43fffff]
[ 1.965521] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[ 1.965544] ACPI: Lid Switch [LID0]
[ 1.976924] [Firmware Bug]: battery: (dis)charge rate invalid.
[ 1.991739] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[ 1.991745] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[ 1.991750] usb usb1: Product: EHCI Host Controller
[ 1.991755] usb usb1: Manufacturer: Linux 3.5.0-26-generic ehci_hcd
[ 1.991759] usb usb1: SerialNumber: 0000:00:1a.0
[ 1.991872] hub 1-0:1.0: USB hub found
[ 2.007703] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[ 2.007709] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[ 2.007713] usb usb2: Product: EHCI Host Controller
[ 2.007718] usb usb2: Manufacturer: Linux 3.5.0-26-generic ehci_hcd
[ 2.007723] usb usb2: SerialNumber: 0000:00:1d.0
[ 2.007830] hub 2-0:1.0: USB hub found
[ 2.007933] usbcore: registered new interface driver libusual
[ 2.026609] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[ 2.082380] r8169 0000:01:00.0: eth0: RTL8105e at 0xffffc9000066a000, 78:e3:b5:58:f8:04, XID 00a00000 IRQ 41
[ 2.303256] usb 1-1: new high-speed USB device number 2 using ehci_hcd
[ 2.435592] usb 1-1: New USB device found, idVendor=8087, idProduct=0020
[ 2.435597] usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[ 2.436114] hub 1-1:1.0: USB hub found
[ 2.546847] usb 2-1: new high-speed USB device number 2 using ehci_hcd
[ 2.679162] usb 2-1: New USB device found, idVendor=8087, idProduct=0020
[ 2.679168] usb 2-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[ 2.679537] hub 2-1:1.0: USB hub found
[ 2.750670] usb 1-1.2: new high-speed USB device number 3 using ehci_hcd
[ 2.850212] usb 1-1.2: New USB device found, idVendor=0bda, idProduct=8187
[ 2.850220] usb 1-1.2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 2.850226] usb 1-1.2: Product: RTL8187_Wireless_LAN_Adapter
[ 2.850231] usb 1-1.2: Manufacturer: Manufacturer_Realtek_RTL8187_
[ 2.850235] usb 1-1.2: SerialNumber: 001AEF171E73
[ 2.938131] Switching to clocksource tsc
[ 2.950139] usb 2-1.2: new low-speed USB device number 3 using ehci_hcd
[ 3.050469] usb 2-1.2: New USB device found, idVendor=045e, idProduct=007d
[ 3.050478] usb 2-1.2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[ 3.050484] usb 2-1.2: Product: Microsoft Notebook/Mobile Optical Mouse 2.0
[ 3.050488] usb 2-1.2: Manufacturer: Microsoft
[ 3.056302] usbcore: registered new interface driver usbhid
[ 3.056304] usbhid: USB HID core driver
[ 3.058304] input: Microsoft Microsoft Notebook/Mobile Optical Mouse 2.0 as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.0/input/input4
[ 3.058437] hid-generic 0003:045E:007D.0001: input,hidraw0: USB HID v1.10 Mouse [Microsoft Microsoft Notebook/Mobile Optical Mouse 2.0] on usb-0000:00:1d.0-1.2/input0
[ 3.121855] usb 2-1.6: new high-speed USB device number 4 using ehci_hcd
[ 3.265356] usb 2-1.6: New USB device found, idVendor=04f2, idProduct=b249
[ 3.265364] usb 2-1.6: New USB device strings: Mfr=2, Product=1, SerialNumber=3
[ 3.265370] usb 2-1.6: Product: HP Webcam-101
[ 3.265375] usb 2-1.6: Manufacturer: Chicony Electronics Co., Ltd.
[ 3.265380] usb 2-1.6: SerialNumber: SN0001
[ 15.040839] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 15.652078] intel ips 0000:00:1f.6: CPU TDP doesn't match expected value (found 25, expected 29)
[ 15.680412] lpc_ich: Resource conflict(s) found affecting iTCO_wdt
[ 15.680438] lpc_ich: Resource conflict(s) found affecting gpio_ich
[ 15.920703] cfg80211: Calling CRDA to update world regulatory domain
[ 15.925419] cfg80211: World regulatory domain updated:
[ 15.925424] cfg80211: (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 15.925426] cfg80211: (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 15.925427] cfg80211: (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 15.925429] cfg80211: (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 15.925430] cfg80211: (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 15.925432] cfg80211: (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 16.267962] uvcvideo: Found UVC 1.00 device HP Webcam-101 (04f2:b249)
[ 16.283329] input: HP Webcam-101 as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.0/input/input5
[ 16.283425] usbcore: registered new interface driver uvcvideo
[ 16.404544] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[ 16.404548] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 16.404550] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[ 16.404552] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 16.404553] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[ 16.404555] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 16.404556] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[ 16.404557] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 16.404559] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[ 16.404560] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 16.404562] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[ 16.404563] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 16.404564] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[ 16.404566] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 16.404567] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[ 16.404569] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 16.404570] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[ 16.404572] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 16.404573] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[ 16.404575] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 16.404576] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[ 16.404577] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 16.404579] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[ 16.404580] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 16.404582] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[ 16.404583] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 16.404585] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[ 16.404586] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 16.479760] lp: driver loaded but no devices found
[ 16.505332] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[ 16.505526] ieee80211 phy0: hwaddr 00:1a:ef:17:1e:73, RTL8187vB (default) V1 + rtl8225z2, rfkill mask 2
[ 16.526128] rtl8187: Customer ID is 0xFF
[ 16.526171] Registered led device: rtl8187-phy0::radio
[ 16.526212] Registered led device: rtl8187-phy0::tx
[ 16.526239] Registered led device: rtl8187-phy0::rx
[ 16.527142] rtl8187: wireless switch is on
[ 16.527179] usbcore: registered new interface driver rtl8187
[ 16.528884] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[ 16.528888] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 16.528891] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[ 16.528893] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 16.528895] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[ 16.528897] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 16.528899] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[ 16.528902] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 16.528904] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[ 16.528906] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 16.528907] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[ 16.528908] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 16.528910] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[ 16.528911] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 16.528913] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[ 16.528914] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 16.528916] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[ 16.528917] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 16.528918] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[ 16.528920] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 16.528921] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[ 16.528923] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 16.528924] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[ 16.528926] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 16.528927] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[ 16.528929] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 16.528930] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[ 16.528932] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 16.529088] ieee80211 phy1: Selected rate control algorithm 'minstrel_ht'
[ 16.529460] Registered led device: rt2800pci-phy1::radio
[ 16.529484] Registered led device: rt2800pci-phy1::assoc
[ 16.529508] Registered led device: rt2800pci-phy1::quality
[ 16.772357] Console: switching to colour frame buffer device 170x48
[ 17.062285] input: HDA Intel HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[ 17.062397] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[ 17.062501] input: HDA Intel Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[ 17.077645] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[ 17.430096] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 17.627178] r8169 0000:01:00.0: eth0: link down
[ 17.627199] r8169 0000:01:00.0: eth0: link down
[ 17.627630] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 17.628015] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 17.629621] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 19.372296] r8169 0000:01:00.0: eth0: link up
[ 19.372759] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 296.923265] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 301.004456] wlan1: authenticate with 20:c9:d0:1b:c3:95
[ 301.126531] wlan1: send auth to 20:c9:d0:1b:c3:95 (try 1/3)
[ 301.128172] wlan1: authenticated
[ 301.187348] wlan1: associate with 20:c9:d0:1b:c3:95 (try 1/3)
[ 301.190018] wlan1: RX AssocResp from 20:c9:d0:1b:c3:95 (capab=0x431 status=0 aid=1)
[ 301.191202] wlan1: associated
[ 301.192367] IPv6: ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[ 301.192542] cfg80211: Calling CRDA for country: US
[ 301.201146] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[ 301.201159] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 301.201164] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[ 301.201170] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 301.201174] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[ 301.201180] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 301.201184] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[ 301.201189] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 301.201193] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[ 301.201198] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 301.201203] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[ 301.201208] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 301.201212] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[ 301.201216] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 301.201220] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[ 301.201226] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 301.201230] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[ 301.201235] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 301.201240] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[ 301.201246] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 301.201250] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[ 301.201256] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 301.201260] cfg80211: Disabling freq 2467 MHz
[ 301.201264] cfg80211: Disabling freq 2472 MHz
[ 301.201267] cfg80211: Disabling freq 2484 MHz
[ 301.201274] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[ 301.201280] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 301.201284] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[ 301.201290] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 301.201294] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[ 301.201299] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 301.201303] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[ 301.201308] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 301.201313] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[ 301.201319] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 301.201325] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[ 301.201330] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 301.201335] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[ 301.201340] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 301.201345] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[ 301.201350] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 301.201354] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[ 301.201358] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 301.201363] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[ 301.201368] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 301.201373] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[ 301.201378] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 301.201382] cfg80211: Disabling freq 2467 MHz
[ 301.201385] cfg80211: Disabling freq 2472 MHz
[ 301.201389] cfg80211: Disabling freq 2484 MHz
[ 301.201395] cfg80211: Regulatory domain changed to country: US
[ 301.201399] cfg80211: (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 301.201405] cfg80211: (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 301.201411] cfg80211: (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[ 301.201417] cfg80211: (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 301.201423] cfg80211: (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 301.201429] cfg80211: (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 301.201435] cfg80211: (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
 Release Date: 12/01/2011
 Manufacturer: Hewlett-Packard
 Product Name: HP Pavilion g6 Notebook PC
 Serial Number: 5CG1311XDK
 Manufacturer: Hewlett-Packard
 Product Name: 1693
 Serial Number: PCEVF00WB1CMDA
 Manufacturer: Hewlett-Packard
 Serial Number: Chassis Serial Number
 Manufacturer: 13-54
 SBDS Serial Number: 4BA1
 SBDS Manufacture Date: 2011-06-26
 Manufacturer: Not Specified
 Serial Number: 00000000
 Manufacturer: Micron Technology
 Serial Number: 37520C42
 Manufacturer: Intel(R) Corporation
 Serial Number: Not Specified
wlan1 IEEE 802.11bg ESSID:"sadgood"
          Mode:Managed Frequency:2.432 GHz Access Point: 20:C9:D0:1B:C3:95
          Bit Rate=54 Mb/s Tx-Power=27 dBm
          Retry long limit:7 RTS thr:off Fragment thr:off
          Power Management:off
          Link Quality=60/70 Signal level=-50 dBm
          Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
          Tx excessive retries:7 Invalid misc:42 Missed beacon:0[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]eth0 no wireless extensions.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]lo no wireless extensions.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]wlan0 IEEE 802.11bgn ESSID:off/any
          Mode:Managed Access Point: Not-Associated Tx-Power=off
          Retry long limit:7 RTS thr:off Fragment thr:off
          Power Management:off[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# which ath5k cannot recover. To prevent this condition, stop
blacklist ath_pci
blacklist eth1394
# replaced by p54pci
blacklist prism54
# replaced by b43 and ssb.
blacklist bcm43xx
blacklist uart6850
blacklist twl4030_wdt
# /etc/modprobe.d/iwlwifi.conf
# iwlwifi will dyamically load either iwldvm or iwlmvm depending on the
# microcode file installed on the system. When removing iwlwifi, first
# remove the iwl?vm module and then iwlwifi.
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true
> hal.1: read hal dataprocess 2706: arguments to dbus_move_error() were incorrect, assertion "(dest) == NULL || !dbus_error_is_set ((dest))" failed in file ../../dbus/dbus-errors.c line 282.
This is normally a bug in some application using the D-Bus library.
libhal.c 3483 : Error unsubscribing to signals, error=The name org.freedesktop.Hal was not provided by any .service files
22: PCI 100.0: 0200 Ethernet controller
  [Created at pci.318]
  Unique ID: rBUF.BNDG+UKwNaF
  Parent ID: z8Q3.pouUn3JbaHC
  SysFS ID: /devices/pci0000:00/0000:00:1c.0/0000:01:00.0
  SysFS BusID: 0000:01:00.0
  Hardware Class: network
  Model: "Realtek RTL8101E/RTL8102E PCI Express Fast Ethernet controller"
  Vendor: pci 0x10ec "Realtek Semiconductor Co., Ltd."
  Device: pci 0x8136 "RTL8101E/RTL8102E PCI Express Fast Ethernet controller"
  SubVendor: pci 0x103c "Hewlett-Packard Company"
  SubDevice: pci 0x1693
  Revision: 0x05
  Driver: "r8169"
  Driver Modules: "r8169"
  Device File: eth0
  I/O Ports: 0x3000-0x3fff (rw)
  Memory Range: 0xb0404000-0xb0404fff (ro,non-prefetchable)
  Memory Range: 0xb0400000-0xb0403fff (ro,non-prefetchable)
  IRQ: 41 (8037 events)
  HW Address: 78:e3:b5:58:f8:04
  Link detected: yes
  Module Alias: "pci:v000010ECd00008136sv0000103Csd00001693bc02sc00i00"
  Driver Info #0:
    Driver Status: r8169 is active
    Driver Activation Cmd: "modprobe r8169"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #13 (PCI bridge)[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]23: PCI 200.0: 0282 WLAN controller
  [Created at pci.318]
  Unique ID: y9sn.NrxSart5bs1
  Parent ID: hoOk.tSgUiLnPhpD
  SysFS ID: /devices/pci0000:00/0000:00:1c.2/0000:02:00.0
  SysFS BusID: 0000:02:00.0
  Hardware Class: network
  Model: "RaLink WLAN controller"
  Vendor: pci 0x1814 "RaLink"
  Device: pci 0x5390
  SubVendor: pci 0x103c "Hewlett-Packard Company"
  SubDevice: pci 0x1636
  Driver: "rt2800pci"
  Driver Modules: "rt2800pci"
  Device File: wlan0
  Features: WLAN
  Memory Range: 0xb4400000-0xb440ffff (rw,non-prefetchable)
  IRQ: 18 (no events)
  HW Address: cc:af:78:7f:ab:80
  Link detected: no
  WLAN channels: 1 2 3 4 5 6 7 8 9 10 11
  WLAN frequencies: 2.412 2.417 2.422 2.427 2.432 2.437 2.442 2.447 2.452 2.457 2.462
  WLAN encryption modes: WEP40 WEP104 TKIP CCMP
  WLAN authentication modes: open sharedkey wpa-psk wpa-eap
  Module Alias: "pci:v00001814d00005390sv0000103Csd00001636bc02sc80i00"
  Driver Info #0:
    Driver Status: rt2800pci is active
    Driver Activation Cmd: "modprobe rt2800pci"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #14 (PCI bridge)[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]31: USB 00.0: 0282 WLAN controller
  [Created at usb.122]
  Unique ID: BobO.ife4UMEq4P5
  Parent ID: ADDn.0j9+vWlqL56
  SysFS ID: /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2/1-1.2:1.0
  SysFS BusID: 1-1.2:1.0
  Hardware Class: network
  Model: "Realtek RTL8187_Wireless_LAN_Adapter"
  Hotplug: USB
  Vendor: usb 0x0bda "Realtek Semiconductor Corp."
  Device: usb 0x8187 "RTL8187_Wireless_LAN_Adapter"
  Revision: "1.00"
  Serial ID: "001AEF171E73"
  Driver: "rtl8187"
  Driver Modules: "rtl8187"
  Device File: wlan1
  Features: WLAN
  Speed: 480 Mbps
  HW Address: 00:1a:ef:17:1e:73
  Link detected: yes
  WLAN channels: 1 2 3 4 5 6 7 8 9 10 11
  WLAN frequencies: 2.412 2.417 2.422 2.427 2.432 2.437 2.442 2.447 2.452 2.457 2.462
  WLAN encryption modes: WEP40 WEP104 TKIP CCMP
  WLAN authentication modes: open sharedkey wpa-psk wpa-eap
  Module Alias: "usb:v0BDAp8187d0100dc00dsc00dp00ic00isc00ip00"
  Driver Info #0:
    Driver Status: rtl8187 is active
    Driver Activation Cmd: "modprobe rtl8187"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #36 (Hub)
warning: bad ps syntax, perhaps a bogus '-'?
See [http://gitorious.org/procps/procps/blobs/master/Documentation/FAQ](http://gitorious.org/procps/procps/blobs/master/Documentation/FAQ)
root 889 0.0 0.1 246356 6100 ? Ssl 10:27 0:00 NetworkManager
root 1622 0.0 0.0 10192 3712 ? S 10:27 0:00 /sbin/dhclient -d -4 -sf /usr/lib/NetworkManager/nm-dhcp-client.action -pf /var/run/sendsigs.omit.d/network-manager.dhclient-eth0.pid -lf /var/lib/dhcp/dhclient-a5bf7094-6b9f-4a19-bc91-1f8fe2f12944-eth0.lease -cf /var/run/nm-dhclient-eth0.conf eth0
nobody 1660 0.0 0.0 33072 1556 ? S 10:27 0:00 /usr/sbin/dnsmasq --no-resolv --keep-in-foreground --no-hosts --bind-interfaces --pid-file=/var/run/sendsigs.omit.d/network-manager.dnsmasq.pid --listen-address=127.0.1.1 --conf-file=/var/run/nm-dns-dnsmasq.conf --cache-size=0 --proxy-dnssec --enable-dbus=org.freedesktop.NetworkManager.dnsmasq --conf-dir=/etc/NetworkManager/dnsmasq.d
root 2347 0.0 0.0 31868 2416 ? Ss 10:31 0:00 /sbin/wpa_supplicant -B -P /run/sendsigs.omit.d/wpasupplicant.pid -u -s -O /var/run/wpa_supplicant
root 2368 0.0 0.0 10192 3728 ? S 10:31 0:00 /sbin/dhclient -d -4 -sf /usr/lib/NetworkManager/nm-dhcp-client.action -pf /var/run/sendsigs.omit.d/network-manager.dhclient-wlan1.pid -lf /var/lib/dhcp/dhclient-c8c550b7-b10f-42d9-b92e-28c57d3fa4c2-wlan1.lease -cf /var/run/nm-dhclient-wlan1.conf wlan1
chris 2726 0.0 0.0 13584 912 pts/0 S+ 10:41 0:00 egrep --color=auto wpa|icd|etwork
Kernel IP routing table
Destination Gateway Genmask Flags MSS Window irtt Iface
0.0.0.0 192.168.1.254 0.0.0.0 UG 0 0 0 eth0
10.0.1.0 0.0.0.0 255.255.255.0 U 0 0 0 wlan1
169.254.0.0 0.0.0.0 255.255.0.0 U 0 0 0 eth0
192.168.1.0 0.0.0.0 255.255.255.0 U 0 0 0 eth0
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
# DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1
search gateway.2wire.net
Module Size Used by
joydev 17458 0
rfcomm 46620 4
bnep 18141 2
bluetooth 209249 10 rfcomm,bnep
parport_pc 32689 0
ppdev 17074 0
snd_hda_codec_hdmi 32049 1
snd_hda_codec_idt 70210 1
snd_hda_intel 33492 3
snd_hda_codec 134213 3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep 17699 1 snd_hda_codec
snd_pcm 96668 3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi 13325 0
snd_rawmidi 30513 1 snd_seq_midi
snd_seq_midi_event 14900 1 snd_seq_midi
snd_seq 61555 2 snd_seq_midi,snd_seq_midi_event
psmouse 95595 0
rt2800pci 18529 0
snd_timer 29426 2 snd_pcm,snd_seq
arc4 12530 4
rt2800lib 58731 1 rt2800pci
lp 17760 0
snd_seq_device 14498 3 snd_seq_midi,snd_rawmidi,snd_seq
parport 46346 3 parport_pc,ppdev,lp
snd 78921 16 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
crc_ccitt 12708 1 rt2800lib
uvcvideo 76750 0
rt2x00pci 14519 1 rt2800pci
videobuf2_core 32852 1 uvcvideo
rt2x00lib 54939 3 rt2800pci,rt2800lib,rt2x00pci
videodev 120310 2 uvcvideo,videobuf2_core
rtl8187 56913 0
coretemp 13401 0
soundcore 15048 1 snd
i915 520615 8
mac80211 540032 4 rt2800lib,rt2x00pci,rt2x00lib,rtl8187
videobuf2_vmalloc 12861 1 uvcvideo
hp_wmi 18049 0
kvm 414071 0
drm_kms_helper 49113 1 i915
cfg80211 206797 3 rt2x00lib,rtl8187,mac80211
drm 288721 4 i915,drm_kms_helper
videobuf2_memops 13405 1 videobuf2_vmalloc
sparse_keymap 13891 1 hp_wmi
wmi 19071 1 hp_wmi
serio_raw 13216 0
mac_hid 13206 0
snd_page_alloc 18485 2 snd_hda_intel,snd_pcm
i2c_algo_bit 13414 1 i915
rtsx_pci_ms 13012 0
mei 40691 0
eeprom_93cx6 13345 2 rt2800pci,rtl8187
lpc_ich 17062 0
memstick 16555 1 rtsx_pci_ms
intel_ips 18244 0
video 19391 1 i915
microcode 22804 0
hid_generic 12541 0
usbhid 46987 0
hid 100411 2 hid_generic,usbhid
rtsx_pci_sdmmc 17476 0
rtsx_pci 28325 2 rtsx_pci_ms,rtsx_pci_sdmmc
ahci 25721 2
libahci 31192 1 ahci
r8169 61651 0
chris@chris-HP-Pavilion-g6-Notebook-PC:~$[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]Thank you for your time.[/FONT][/COLOR]

---

### Post by chili555 on 2013-04-10
What is the position of the wireless key? Please see attached. Is there any change if you press the key and run again?```
rfkill list all
```You have two, possibly conflicting, wireless devices. I assume the rtl8187 is a USB. After we solve the rfkill issue, remove the USB to continue troubleshooting.

---

### Post by creynol4 on 2013-04-10
My F12 is the toggle key. It does work. I pressed it once.
chris@chris-HP-Pavilion-g6-Notebook-PC:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
2: hp-wifi: Wireless LAN
	Soft blocked: yes
	Hard blocked: yes
3: phy2: Wireless LAN
	Soft blocked: no
	Hard blocked: no
Pressed it again.

chris@chris-HP-Pavilion-g6-Notebook-PC:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
2: hp-wifi: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
3: phy2: Wireless LAN
	Soft blocked: no
	Hard blocked: no
chris@chris-HP-Pavilion-g6-Notebook-PC:~$

---

### Post by creynol4 on 2013-04-10
chris@chris-HP-Pavilion-g6-Notebook-PC:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
2: hp-wifi: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
3: phy2: Wireless LAN
	Soft blocked: no
	Hard blocked: no
Although I see this, the network manager now says that Wireless is disabled by hardware switch....


Also, for some reason the manager likes to auto toggle to airplane mode whenever I open up the manager...

---

### Post by chili555 on 2013-04-10
So neither keypress unblocks Hard blocked: yes. This technique may have some other consequences but the only way to find out is to try it. There is a module loaded called hp-wmi that is supposed to accurately translate key presses, F12 for example, into action; in this case, turn on the wireless, please! It's evidently not doing so correctly. Let's remove it temporarily:```
sudo modprobe -rf hp-wmi
```Now check:```
sudo rfkill unblock all
rfkill list all
```Any improvement?

---

### Post by creynol4 on 2013-04-10
chris@chris-HP-Pavilion-g6-Notebook-PC:~$ sudo modprobe -rf hp-wmi
[sudo] password for chris: 
chris@chris-HP-Pavilion-g6-Notebook-PC:~$ sudo rfkill unblock all
chris@chris-HP-Pavilion-g6-Notebook-PC:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
3: phy2: Wireless LAN
	Soft blocked: no
	Hard blocked: no

No improvement. To me it looks like it just deleted my wireless card all together...

---

### Post by chili555 on 2013-04-10
> To me it looks like it just deleted my wireless card all together... Not at all:> chris@chris-HP-Pavilion-g6-Notebook-PC:~$ rfkill list all
0: phy0: Wireless LAN  [COLOR="#FF0000"]<--built-in[/COLOR]
Soft blocked: no
Hard blocked: yes
3: phy2: Wireless LAN  [COLOR="#FF0000"]<--USB[/COLOR]
Soft blocked: no
Hard blocked: noI'm not sure I know another answer. You could:

* Blacklist the driver for the built-in and enjoy the USB.

* Fully update the system to the latest kernel, now 3.5.0-27-generic and see if there is any improvement.

* Try the live DVD for 13.04 and see if there is any improvement.

There may be some hardware way to block off the appropriate pin on the built-in card, like this: [http://www.notebookforums.com/t/225429/broken-wireless-hardware-switch-fix](http://www.notebookforums.com/t/225429/broken-wireless-hardware-switch-fix)

In terms of the operating system and the driver, I don't believe there are any further options.

---

### Post by creynol4 on 2013-04-10
Thank you for all your help and time spent. It is much appreciated!

---

