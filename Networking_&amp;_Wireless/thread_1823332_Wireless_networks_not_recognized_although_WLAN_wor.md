---
title: "Wireless networks not recognized although WLAN works"
date: 2011-08-11
forum: Networking &amp; Wireless
---

### Post by linuxfriendly on 2011-08-11
Hi all,

Perhaps somebody can help here.
I have a Dell Laptop which worked very well also with the wireless card.  In fact the wireless card was never an issue and worked straight out of  the box.
However it has lost the ability to detect the wireless networks. I have  plenty of networks in my area and my little netbook shows them nicely.  So did my Dell laptop in the past.
- But now the Dell laptop shows no scan results at all although the card seems to be up and running (see terminal output below)
- I have to add that I had to compile a module for the WIRED network card which works excellent
- I always use and used a wired network and cannot say when the wireless card stopped to work PLUS
- I had a faulty harddisk which was replaced by Dell recently so there  could be also a hardware fault since then because the laptop was opened  by the service people.
- And yes the wireless is switched on in the BIOS
- If I create a wireless network with the laptop the netbook can see it, so the wireless card is broadcasting

Thanks in advance

Here comes the long terminal output

sudo lshw -C network; rfkill list; sudo iwlist scanning; cat  /etc/network/interfaces; cat /etc/lsb-release; lspci -nn; lsusb; sudo  lshw -short; uname -a; dmesg | grep ound; dmesg | grep irmware ; dmesg |  grep ipw; dmesg | grep eth; dmesg | grep ath; dmesg | grep b43; dmesg |  grep witch; iwconfig; grep b43 /etc/modprobe.d/*; grep wl  /etc/modprobe.d/*; sudo hwinfo --netcard ; sudo /etc/init.d/networking  restart
  *-network               
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wlan0
       version: 01
       serial: 00:1b:b1:44:a3:44
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k latency=0 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:f69f0000-f69fffff
  *-network
       description: Ethernet interface
       product: AR8152 v2.0 Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: c1
       serial: f0:4d:a2:86:47:8b
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c  driverversion=1.0.1.0-NAPI duplex=full firmware=N/A ip=192.168.1.4  latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:30 memory:f68c0000-f68fffff ioport:df00(size=128)
0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results

auto lo
iface lo inet loopback

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.3 LTS"
00:00.0 Host bridge [0600]: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub [8086:2a40] (rev 07)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 4  Series Chipset Integrated Graphics Controller [8086:2a42] (rev 07)
00:02.1 Display controller [0380]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a43] (rev 07)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 03)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 [8086:2938] (rev 03)
00:1a.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 [8086:2939] (rev 03)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 [8086:2940] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 [8086:2942] (rev 03)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 [8086:2944] (rev 03)
00:1c.4 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 [8086:2948] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 93)
00:1f.0 ISA bridge [0601]: Intel Corporation ICH9M LPC Interface Controller [8086:2919] (rev 03)
00:1f.2 SATA controller [0106]: Intel Corporation ICH9M/M-E SATA AHCI Controller [8086:2929] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801I (ICH9 Family) SMBus Controller [8086:2930] (rev 03)
09:00.0 Ethernet controller [0200]: Atheros Communications AR8152 v2.0 Fast Ethernet [1969:2062] (rev c1)
0c:00.0 Network controller [0280]: Atheros Communications Inc. AR9285  Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0c45:6482 Microdia
Bus 001 Device 002: ID 0bda:0138 Realtek Semiconductor Corp.
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
H/W path           Device      Class       Description
======================================================
                               system      Inspiron N5030
/0                             bus         0H3XR9
/0/0                           memory      64KiB BIOS
/0/400                         processor   Intel(R) Celeron(R) CPU          900  @ 2.20GHz
/0/400/700                     memory      64KiB L1 cache
/0/400/701                     memory      1MiB L2 cache
/0/1000                        memory      3GiB System Memory
/0/1000/0                      memory      2GiB DIMM DDR Synchronous 800 MHz (1.2 ns)
/0/1000/1                      memory      1GiB DIMM DDR Synchronous 800 MHz (1.2 ns)
/0/100                         bridge      Mobile 4 Series Chipset Memory Controller Hub
/0/100/2                       display     Mobile 4 Series Chipset Integrated Graphics Controller
/0/100/2.1                     display     Mobile 4 Series Chipset Integrated Graphics Controller
/0/100/1a                      bus         82801I (ICH9 Family) USB UHCI Controller #4
/0/100/1a.1                    bus         82801I (ICH9 Family) USB UHCI Controller #5
/0/100/1a.2                    bus         82801I (ICH9 Family) USB UHCI Controller #6
/0/100/1a.7                    bus         82801I (ICH9 Family) USB2 EHCI Controller #2
/0/100/1b                      multimedia  82801I (ICH9 Family) HD Audio Controller
/0/100/1c                      bridge      82801I (ICH9 Family) PCI Express Port 1
/0/100/1c.1                    bridge      82801I (ICH9 Family) PCI Express Port 2
/0/100/1c.1/0      wlan0       network     AR9285 Wireless Network Adapter (PCI-Express)
/0/100/1c.2                    bridge      82801I (ICH9 Family) PCI Express Port 3
/0/100/1c.2/0      eth0        network     AR8152 v2.0 Fast Ethernet
/0/100/1c.4                    bridge      82801I (ICH9 Family) PCI Express Port 5
/0/100/1d                      bus         82801I (ICH9 Family) USB UHCI Controller #1
/0/100/1d.1                    bus         82801I (ICH9 Family) USB UHCI Controller #2
/0/100/1d.2                    bus         82801I (ICH9 Family) USB UHCI Controller #3
/0/100/1d.7                    bus         82801I (ICH9 Family) USB2 EHCI Controller #1
/0/100/1e                      bridge      82801 Mobile PCI Bridge
/0/100/1f                      bridge      ICH9M LPC Interface Controller
/0/100/1f.2        scsi0       storage     ICH9M/M-E SATA AHCI Controller
/0/100/1f.2/0      /dev/sda    disk        320GB TOSHIBA MK3276GS
/0/100/1f.2/0/1    /dev/sda1   volume      289GiB EXT4 volume
/0/100/1f.2/0/2    /dev/sda2   volume      8751MiB Extended partition
/0/100/1f.2/0/2/5  /dev/sda5   volume      8751MiB Linux swap / Solaris partition
/0/100/1f.2/1      /dev/cdrom  disk        DVD+-RW AD-7585H
/0/100/1f.3                    bus         82801I (ICH9 Family) SMBus Controller
/0/1               scsi6       storage     
/0/1/0.0.0         /dev/sdb    disk        SCSI Disk
/1                             power       DELL W7H3N07
Linux laptop2 2.6.32-33-generic #70-Ubuntu SMP Thu Jul 7 21:09:46 UTC 2011 i686 GNU/Linux
[    0.188527] ACPI: No dock devices found.
[    0.274035] pnp: PnP ACPI: found 13 devices
[    0.532243] hub 1-0:1.0: USB hub found
[    0.596377] hub 2-0:1.0: USB hub found
[    0.596666] hub 3-0:1.0: USB hub found
[    0.596879] hub 4-0:1.0: USB hub found
[    0.597072] hub 5-0:1.0: USB hub found
[    0.597268] hub 6-0:1.0: USB hub found
[    0.597467] hub 7-0:1.0: USB hub found
[    0.597662] hub 8-0:1.0: USB hub found
[    0.642822] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.649565] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.981530] isapnp: No Plug & Play device found
[    1.327381] usb-storage: device found at 2
[   11.135985] lp: driver loaded but no devices found
[   11.740872] uvcvideo: Found UVC 1.00 device Laptop_Integrated_Webcam_0.3M (0c45:6482)
[   12.973833] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   14.593057] atl1c 0000:09:00.0: atl1c: eth0 NIC Link is Up<100 Mbps Full Duplex>
[   14.593154] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   25.164038] eth0: no IPv6 routers present
[    0.642820] device-mapper: multipath: version 1.1.0 loaded
[    0.642822] device-mapper: multipath round-robin: version 1.0.0 loaded
[   11.851647] ath9k 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   11.851665] ath9k 0000:0c:00.0: setting latency timer to 64
[   11.901845] ath: EEPROM regdomain: 0x65
[   11.901847] ath: EEPROM indicates we should expect a direct regpair map
[   11.901850] ath: Country alpha2 being used: 00
[   11.901852] ath: Regpair used: 0x65
[   12.236528] phy0: Selected rate control algorithm 'ath9k_rate_control'
[   12.237064] Registered led device: ath9k-phy0::radio
[   12.237078] Registered led device: ath9k-phy0::assoc
[   12.237091] Registered led device: ath9k-phy0::tx
[   12.237105] Registered led device: ath9k-phy0::rx
[    0.020844] SMP alternatives: switching to UP code
[    0.228018] Switching to clocksource tsc
[    0.341289] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    0.342669] ACPI: Lid Switch [LID]
[    0.351534] Switching to clocksource hpet
[   13.327572] Console: switching to colour frame buffer device 170x48
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
/etc/modprobe.d/blacklist.conf:# replaced by b43 and ssb.
/etc/modprobe.d/blacklist-watchdog.conf:blacklist twl4030_wdt
28: PCI c00.0: 0282 WLAN controller                             
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_168c_2b
  Unique ID: y9sn.yTWiRrH1224
  Parent ID: qTvu.8Makl3iDVc3
  SysFS ID: /devices/pci0000:00/0000:00:1c.1/0000:0c:00.0
  SysFS BusID: 0000:0c:00.0
  Hardware Class: network
  Model: "Atheros WLAN controller"
  Vendor: pci 0x168c "Atheros Communications Inc."
  Device: pci 0x002b
  SubVendor: pci 0x185f "Wistron NeWeb Corp."
  SubDevice: pci 0x30af
  Revision: 0x01
  Driver: "ath9k"
  Driver Modules: "ath9k"
  Device File: wlan0
  Features: WLAN
  Memory Range: 0xf69f0000-0xf69fffff (rw,non-prefetchable)
  IRQ: 17 (3997 events)
  HW Address: 00:1b:b1:44:a3:44
  Link detected: no
  WLAN channels: 1 2 3 4 5 6 7 8 9 10 11 12 13
  WLAN frequencies: 2.412 2.417 2.422 2.427 2.432 2.437 2.442 2.447 2.452 2.457 2.462 2.467 2.472
  WLAN encryption modes: WEP40 WEP104 TKIP CCMP
  WLAN authentication modes: open sharedkey wpa-psk wpa-eap
  Module Alias: "pci:v0000168Cd0000002Bsv0000185Fsd000030AFbc02sc80i00"
  Driver Info #0:
    Driver Status: ath9k is active
    Driver Activation Cmd: "modprobe ath9k"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #17 (PCI bridge)

29: PCI 900.0: 0200 Ethernet controller
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_1969_2062
  Unique ID: rBUF.rujl3Q6AGn4
  Parent ID: hoOk.ABTEjCxdYN4
  SysFS ID: /devices/pci0000:00/0000:00:1c.2/0000:09:00.0
  SysFS BusID: 0000:09:00.0
  Hardware Class: network
  Model: "Attansic Ethernet controller"
  Vendor: pci 0x1969 "Attansic Technology Corp."
  Device: pci 0x2062
  SubVendor: pci 0x1028 "Dell"
  SubDevice: pci 0x04a6
  Revision: 0xc1
  Driver: "atl1c"
  Driver Modules: "atl1c"
  Device File: eth0
  Memory Range: 0xf68c0000-0xf68fffff (rw,non-prefetchable)
  I/O Ports: 0xdf00-0xdf7f (rw)
  IRQ: 30 (3237 events)
  HW Address: f0:4d:a2:86:47:8b
  Link detected: yes
  Module Alias: "pci:v00001969d00002062sv00001028sd000004A6bc02sc00i00"
  Driver Info #0:
    Driver Status: atl1c is active
    Driver Activation Cmd: "modprobe atl1c"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #18 (PCI bridge)
 * Reconfiguring network interfaces...

---

### Post by linuxfriendly on 2011-08-13
Hi, everybody seems to be as baffled as I am :). I did some more testing with my netbook and the laptop. Here the results:  

Test procedure N° 1: LAPTOP connected to wired LAN, **un**encrypted wireless network set up on laptop, netbook can see it and can connect and surf the internet.  

Test procedure N° 2: Netbook connected to wired LAN, **un**encrypted wireless network set up on netbook, laptop can see it and can connect and surf the internet.  

Test procedure N° 3: LAPTOP connected to wired LAN, **encrypted** wireless network set up on laptop, netbook can see it and can connect and surf the internet.  

Test procedure N° 4: Netbook connected to wired LAN, **encrypted** wireless network set up on netbook, laptop can see it BUT cannot connect and surf the internet.  The network shows up in the network manager menu but clicking on it shows no reaction. This means no requester pops up to ask for the password etc.

Any help is appreciated, the hardware seems to work otherwise I could not do the little network trick.

---

