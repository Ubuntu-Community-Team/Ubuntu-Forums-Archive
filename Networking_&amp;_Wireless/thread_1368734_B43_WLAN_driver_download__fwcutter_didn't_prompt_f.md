---
title: "B43 WLAN driver download / fwcutter didn't prompt for firmware update..."
date: 2009-12-31
forum: Networking &amp; Wireless
---

### Post by alpacadaddy on 2009-12-31
Good Day All...

Am running 9.10 and trying to install a Linksys wireless nic (BCM4318), and I have followed several of the related threads. Problem is, I installed & activated the Broadcom B43 driver through Hardware Drivers, and it appears fwcutter is installed, however it never prompted me to get & install new firmware (the proprietary Broadcom stuff)...I have tried removing & re-installing the driver but I am never prompted for anything about firmware so I am pretty sure it is not loaded...how might I accomplish this?

I do have wired eth0 connection, and OS does see the wireless nic.

Thanks in advance for your help!

Phil

PS: As suggested in one of the other related threads, I executed several diagnostic commands and have attached the output below...since I am pretty new to Linux I only know about half of what I am looking at, but I can tell the wireless nic is detected...and I may well be out of range (which I can fix later), but first I wanted to make sure I had got the firmware downloaded & installed correctly!

$ sudo lshw -C network; sudo iwlist scanning; cat /etc/network/interfaces; cat /etc/lsb-release; lspci -nn; lsusb; sudo lshw -C usb; uname -a; dmesg | grep ound; dmesg | grep b43; dmesg | grep iwl; iwconfig; sudo /etc/init.d/networking restart
[sudo] password for sarah: 
  *-network:0             
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:11 memory:ec100000-ec101fff
  *-network:1
       description: Ethernet interface
       product: 3c905C-TX/TX-M [Tornado]
       vendor: 3Com Corporation
       physical id: 4
       bus info: pci@0000:01:04.0
       logical name: eth0
       version: 78
       serial: 00:04:75:3b:8d:d8
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=3c59x duplex=full ip=192.168.0.7 latency=80 link=yes maxlatency=10 mingnt=10 multicast=yes port=MII speed=100MB/s
       resources: irq:5 ioport:2000(size=128) memory:ec102000-ec10207f memory:20000000-2001ffff(prefetchable)
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1e:e5:29:7d:5c
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:23:69:EF:9E:47
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=53/70  Signal level=-57 dBm  
                    Encryption key:off
                    ESSID:"linksys"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000003a78ddbff83
                    Extra: Last beacon: 1056ms ago
                    IE: Unknown: 00076C696E6B737973
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A6C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606080000000000000000000000000000000000000000
                    IE: Unknown: DD8B0050F204104A00011010440001011041000100103B000103104700103090F0E050003090F0E05040000000001021001C4C696E6B7379732C2041204469766973696F6E206F6620436973636F102300075752543631304E1024000876312E30302E30321042000234321054000800060050F2040001101100075752543631304E100800020084103C000103
                    IE: Unknown: DD090010180200F0050000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C336C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406080000000000000000000000000000000000000000

auto lo
iface lo inet loopback

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.10
DISTRIB_CODENAME=karmic
DISTRIB_DESCRIPTION="Ubuntu 9.10"
00:00.0 Host bridge [0600]: Intel Corporation 82815 815 Chipset Host Bridge and Memory Controller Hub [8086:1130] (rev 02)
00:02.0 VGA compatible controller [0300]: Intel Corporation 82815 Chipset Graphics Controller (CGC) [8086:1132] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801AA PCI Bridge [8086:2418] (rev 02)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801AA ISA Bridge (LPC) [8086:2410] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801AA IDE Controller [8086:2411] (rev 02)
00:1f.2 USB Controller [0c03]: Intel Corporation 82801AA USB Controller [8086:2412] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801AA SMBus Controller [8086:2413] (rev 02)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801AA AC'97 Audio Controller [8086:2415] (rev 02)
01:00.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
01:04.0 Ethernet controller [0200]: 3Com Corporation 3c905C-TX/TX-M [Tornado] [10b7:9200] (rev 78)
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Linux bear-linux 2.6.31-16-generic #53-Ubuntu SMP Tue Dec 8 04:01:29 UTC 2009 i686 GNU/Linux
[    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.105384] ACPI: No dock devices found.
[    0.179145] pnp: PnP ACPI: found 13 devices
[    1.196299] isapnp: No Plug & Play device found
[    1.211393] hub 1-0:1.0: USB hub found
[    1.216142] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.221960] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.340233] ssb: Sonics Silicon Backplane found on PCI device 0000:01:00.0
[   17.706736] lp: driver loaded but no devices found
[   19.067633] b43-phy0: Broadcom 4318 WLAN found (core revision 9)
[   23.784150] mtrr: base(0xf0000000) is not aligned on a size(0x280000) boundary
[ 2399.557083] b43-phy1: Broadcom 4318 WLAN found (core revision 9)
[    2.265034] b43-pci-bridge 0000:01:00.0: PCI INT A -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
[   19.067633] b43-phy0: Broadcom 4318 WLAN found (core revision 9)
[   20.138386] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[   20.218127] b43 ssb0:0: firmware: requesting b43/pcm5.fw
[   20.269109] b43 ssb0:0: firmware: requesting b43/b0g0initvals5.fw
[   20.331414] b43 ssb0:0: firmware: requesting b43/b0g0bsinitvals5.fw
[   20.544976] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[   20.600768] Registered led device: b43-phy0::tx
[   20.600819] Registered led device: b43-phy0::rx
[   20.600867] Registered led device: b43-phy0::radio
[ 2399.557083] b43-phy1: Broadcom 4318 WLAN found (core revision 9)
[ 2399.760077] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[ 2399.849188] b43 ssb0:0: firmware: requesting b43/pcm5.fw
[ 2399.876765] b43 ssb0:0: firmware: requesting b43/b0g0initvals5.fw
[ 2399.903716] b43 ssb0:0: firmware: requesting b43/b0g0bsinitvals5.fw
[ 2400.040060] b43-phy1: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 2400.080647] Registered led device: b43-phy1::tx
[ 2400.080696] Registered led device: b43-phy1::rx
[ 2400.080743] Registered led device: b43-phy1::radio
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

 * Reconfiguring network interfaces...                                                                                                                       Ignoring unknown interface eth0=eth0.

---

### Post by focwiz on 2009-12-31
> **alpacadaddy said:**
> Good Day All...

Am running 9.10 and trying to install a Linksys wireless nic (BCM4318), and I have followed several of the related threads. Problem is, I installed & activated the Broadcom B43 driver through Hardware Drivers, and it appears fwcutter is installed, however it never prompted me to get & install new firmware (the proprietary Broadcom stuff)...I have tried removing & re-installing the driver but I am never prompted for anything about firmware so I am pretty sure it is not loaded...how might I accomplish this?

I do have wired eth0 connection, and OS does see the wireless nic.

Thanks in advance for your help!



See the following post...?
[http://ubuntuforums.org/showthread.php?t=1368699]("http://ubuntuforums.org/showthread.php?t=1368699")

---

