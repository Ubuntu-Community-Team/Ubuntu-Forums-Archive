---
title: "Ubuntu 12.04 - Wireless works, but takes 30min or more to connect"
date: 2012-05-07
forum: Networking &amp; Wireless
---

### Post by M4570D0N on 2012-05-07
So, I've never really had any wireless issues on this laptop with Ubuntu  or Linux Mint since 10.04, but after wiping my 11.10 partition and  installing 12.04 fresh, my wireless has gone to complete crap. It seems  as though signal strength/dropped connections for me progressively  improved with each release up to 11.04, declined slightly with 11.10 and  has now fallen off a cliff.

When I first boot up it will not  connect to any wireless network. The only connection that seems to work  right after booting up/returning from sleep is that I managed to get it  to connect via USB tether with my SGSII as well as wifi tethering with  my phone, without much issue. However, after some variable, ridiculously  long period of time (anywhere from 20min to 45min) my notebook will  finally successfully connect to my home network (or any wireless  network) and it will stay connected as well. However, if I close the lid  or do anything else to lose the connection, I have to start all over  again, even if it was just a few seconds and the notebook is in the same  spot.

The notebook is a HP Pavillion dv5t-1000 w/ Intel PRO/Wireless 5100 AGN. The syslog and kernlog extends from boot up, until it finally connected to my home network. Files are too large to attach, so here's the google docs links:

kern.log05-05-2012.txt
_[https://docs.google.com/open?id=0B0bpxu46xkWSWXZGTHBIMXQ3SDQ](https://docs.google.com/open?id=0B0bpxu46xkWSWXZGTHBIMXQ3SDQ)_

syslog05-05-2012.txt
[U][https://docs.google.com/open?id=0B0bpxu46xkWSNHJGRGJQTEZ2N2s](https://docs.google.com/open?id=0B0bpxu46xkWSNHJGRGJQTEZ2N2s)
[/U]
results from the [_wireless script_]("http://sourceforge.net/projects/wirelessscript/files/") 
_[https://docs.google.com/open?id=0B0bpxu46xkWSOG5TemJkLU9kcjA](https://docs.google.com/open?id=0B0bpxu46xkWSOG5TemJkLU9kcjA)_

additional info:
```
m4570d0n@HP-dv5t:~$  sudo lshw -C network; sudo iwlist scanning; cat  /etc/network/interfaces; cat /etc/lsb-release; lspci -nn; lsusb; sudo  lshw -short; uname -a; dmesg | grep ound; dmesg | grep irmware ; dmesg |  grep eth; dmesg | grep ath; dmesg | grep b43; dmesg | grep wl; dmesg |  grep witch; iwconfig; grep b43 /etc/modprobe.d/*; grep wl  /etc/modprobe.d/*; hwinfo --netcard ; sudo /etc/init.d/networking  restart b43; dmesg | grep wl; dmesg | grep witch; iwconfig; grep b43  /etc/modpbe.d/*; hwinfo --netcard ; sudo /etc/init.d/network *-network
  *-network              
       description: Wireless interface
       product: PRO/Wireless 5100 AGN [Shiloh] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 00
       serial: 00:16:ea:df:95:d2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
        configuration: broadcast=yes driver=iwlwifi  driverversion=3.2.0-24-generic firmware=8.83.5.1 build 33692  ip=192.168.1.103 latency=0 link=yes multicast=yes wireless=IEEE  802.11abgn
       resources: irq:49 memory:db600000-db601fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:68:e3:0e:c5
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
        capabilities: pm msi pciexpress msix vpd bus_master cap_list rom  ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
        configuration: autonegotiation=on broadcast=yes driver=r8169  driverversion=2.3LK-NAPI duplex=half firmware=N/A latency=0 link=no  multicast=yes port=MII speed=10Mbit/s
       resources: irq:47 ioport:6000(size=256) memory:d1410000-d1410fff memory:d1400000-d140ffff memory:d1420000-d142ffff
lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 98:FC:11:A9:0F:06
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"homenet"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000001c02ff005
                    Extra: Last beacon: 228ms ago
                    IE: Unknown: 0007686F6D656E6574
                    IE: Unknown: 010482848B96
                    IE: Unknown: 03010B
                    IE: Unknown: 200100
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A2C001EFFFF000001000000000000000000000080000000000000
                    IE: Unknown: 32080C1218243048606C
                    IE: Unknown: 3D160B001700000000000000000000000000000000000000
                    IE: Unknown: DD1E00904C332C001EFFFF000001000000000000000000000080000000000000
                    IE: Unknown: DD1A00904C340B001700000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101030003A4000027A4000042435E0062322F00
                    IE: Unknown: DD050050F20500
                     IE: Unknown:  DD8C0050F204104A00011010440001021041000100103B0001031047001062C66E408BA14EC7ACD4F25485E0829410210012436973636F2D4C696E6B7379732C204C4C4310230017576972656C6573732D4E2041636365737320506F696E74102400075741503631304E104200033030301054000800060050F2040001101100075741503631304E100800020086
                    IE: Unknown: DD050009860100
          Cell 02 - Address: 00:15:E9:D6:86:24
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"dlink2xr"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000293d7538f6
                    Extra: Last beacon: 5744ms ago
                    IE: Unknown: 0008646C696E6B327872
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030102
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
                    IE: Unknown: DD0900037F010100040000
          Cell 03 - Address: 00:14:BF:7A:0E:57
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"sgrh0me"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Mode:Master
                    Extra:tsf=000000752aba0188
                    Extra: Last beacon: 5328ms ago
                    IE: Unknown: 000773677268306D65
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030108
                    IE: Unknown: DD06001018010000
          Cell 04 - Address: 00:1E:E5:EF:F4:9D
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"dunmire"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000025f301bc79
                    Extra: Last beacon: 5516ms ago
                    IE: Unknown: 000764756E6D697265
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 200100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101020003A4000027A4000042435E0062322F00
                    IE: Unknown: 2D1A4C101BFF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606001B00000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010020000000
                    IE: Unknown: 071044422020131B00101BDA021B100B1B00
                     IE: Unknown:  DD910050F204104A00011010440001021041000100103B0001031047001000000000000000011000001EE5EFF49D102100134C696E6B73797320436F72706F726174696F6E102300075752543132304E1024000776312E302E30301042000A4A3932323037373636321054000800060050F204000110110014576972656C65737320526F757465722857464129100800020004
          Cell 05 - Address: E0:91:F5:67:AC:1D
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"SugarLand"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000006bf562b4184
                    Extra: Last beacon: 5292ms ago
                    IE: Unknown: 000953756761724C616E64
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 050400020000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001300000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD270050F204104A00011010440001021047001065595E54C867848DBE6896AD32115FA4103C000103
                    IE: Unknown: DD090010180201F0050000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C337C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B001300000000000000000000000000000000000000

eth0      Interface doesn't support scanning.

auto lo
iface lo inet loopback

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"
00:00.0 Host bridge [0600]: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub [8086:2a40] (rev 07)
00:02.0  VGA compatible controller [0300]: Intel Corporation Mobile 4 Series  Chipset Integrated Graphics Controller [8086:2a42] (rev 07)
00:02.1 Display controller [0380]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a43] (rev 07)
00:1a.0 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 03)
00:1a.1 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 [8086:2938] (rev 03)
00:1a.7 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 [8086:2940] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 [8086:2942] (rev 03)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 [8086:2944] (rev 03)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 [8086:2946] (rev 03)
00:1c.4 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 [8086:2948] (rev 03)
00:1c.5 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 [8086:294a] (rev 03)
00:1d.0 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 03)
00:1d.1 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 03)
00:1d.2 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 03)
00:1d.3 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 [8086:2939] (rev 03)
00:1d.7 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 93)
00:1f.0 ISA bridge [0601]: Intel Corporation ICH9M LPC Interface Controller [8086:2919] (rev 03)
00:1f.2  SATA controller [0106]: Intel Corporation 82801IBM/IEM (ICH9M/ICH9M-E) 4  port SATA Controller [AHCI mode] [8086:2929] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801I (ICH9 Family) SMBus Controller [8086:2930] (rev 03)
00:1f.6 Signal processing controller [1180]: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem [8086:2932] (rev 03)
02:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection [8086:4237]
03:00.0  Ethernet controller [0200]: Realtek Semiconductor Co., Ltd.  RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev  02)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
Bus 001 Device 006: ID 04e8:685e Samsung Electronics Co., Ltd GT-I9100 Phone [Galaxy S II] (USB Debugging mode)
Bus 002 Device 004: ID 0408:03ba Quanta Computer, Inc.
Bus 005 Device 002: ID 03f0:a407 Hewlett-Packard
Bus 006 Device 002: ID 138a:0001 Validity Sensors, Inc. VFS101 Fingerprint Reader
H/W path           Device      Class       Description
======================================================
                               system      HP Pavilion dv5 Notebook PC (KQ574AV)
/0                             bus         3602
/0/0                           memory      1MiB BIOS
/0/f                           processor   Intel(R) Core(TM)2 Duo CPU     P8400
/0/f/10                        memory      3MiB L2 cache
/0/f/12                        memory      32KiB L1 cache
/0/11                          memory      32KiB L1 cache
/0/13                          memory      8GiB System Memory
/0/13/0                        memory      4GiB SODIMM DDR2 Synchronous 800 MHz
/0/13/1                        memory      4GiB SODIMM DDR2 Synchronous 800 MHz
/0/100                         bridge      Mobile 4 Series Chipset Memory Contro
/0/100/2                       display     Mobile 4 Series Chipset Integrated Gr
/0/100/2.1                     display     Mobile 4 Series Chipset Integrated Gr
/0/100/1a                      bus         82801I (ICH9 Family) USB UHCI Control
/0/100/1a.1                    bus         82801I (ICH9 Family) USB UHCI Control
/0/100/1a.7                    bus         82801I (ICH9 Family) USB2 EHCI Contro
/0/100/1b                      multimedia  82801I (ICH9 Family) HD Audio Control
/0/100/1c                      bridge      82801I (ICH9 Family) PCI Express Port
/0/100/1c/0        wlan0       network     PRO/Wireless 5100 AGN [Shiloh] Networ
/0/100/1c.1                    bridge      82801I (ICH9 Family) PCI Express Port
/0/100/1c.1/0      eth0        network     RTL8101E/RTL8102E PCI Express Fast Et
/0/100/1c.2                    bridge      82801I (ICH9 Family) PCI Express Port
/0/100/1c.3                    bridge      82801I (ICH9 Family) PCI Express Port
/0/100/1c.4                    bridge      82801I (ICH9 Family) PCI Express Port
/0/100/1c.5                    bridge      82801I (ICH9 Family) PCI Express Port
/0/100/1d                      bus         82801I (ICH9 Family) USB UHCI Control
/0/100/1d.1                    bus         82801I (ICH9 Family) USB UHCI Control
/0/100/1d.2                    bus         82801I (ICH9 Family) USB UHCI Control
/0/100/1d.3                    bus         82801I (ICH9 Family) USB UHCI Control
/0/100/1d.7                    bus         82801I (ICH9 Family) USB2 EHCI Contro
/0/100/1e                      bridge      82801 Mobile PCI Bridge
/0/100/1f                      bridge      ICH9M LPC Interface Controller
/0/100/1f.2        scsi0       storage     82801IBM/IEM (ICH9M/ICH9M-E) 4 port S
/0/100/1f.2/0      /dev/sda    disk        250GB TOSHIBA MK2552GS
/0/100/1f.2/0/1    /dev/sda1   volume      140GiB Windows NTFS volume
/0/100/1f.2/0/3    /dev/sda3   volume      92GiB Extended partition
/0/100/1f.2/0/3/5  /dev/sda5   volume      48GiB Linux filesystem partition
/0/100/1f.2/0/3/6  /dev/sda6   volume      2446MiB Linux swap / Solaris partitio
/0/100/1f.2/0/3/7  /dev/sda7   volume      41GiB Linux filesystem partition
/0/100/1f.2/1      /dev/cdrom  disk        CDDVDW TS-L633A
/0/100/1f.3                    bus         82801I (ICH9 Family) SMBus Controller
/0/100/1f.6                    generic     82801I (ICH9 Family) Thermal Subsyste
/0/1               scsi9       storage    
/0/1/0.0.0         /dev/sdb    disk        SCSI Disk
/0/1/0.0.1         /dev/sdc    disk        SCSI Disk
/0/2               scsi7       storage    
/0/2/0.0.0         /dev/sdd    disk        SCSI Disk
Linux HP-dv5t 3.2.0-24-generic #37-Ubuntu SMP Wed Apr 25 08:43:22 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
[    0.000000] No AGP bridge found
[    0.429423] ACPI: No dock devices found.
[    0.429426] HEST: Table not found.
[    0.469817] pnp: PnP ACPI: found 12 devices
[    0.588535] ERST: Table is not found!
[    0.732140] hub 1-0:1.0: USB hub found
[    0.752140] hub 2-0:1.0: USB hub found
[    0.752461] hub 3-0:1.0: USB hub found
[    0.752744] hub 4-0:1.0: USB hub found
[    0.753024] hub 5-0:1.0: USB hub found
[    0.753291] hub 6-0:1.0: USB hub found
[    0.753560] hub 7-0:1.0: USB hub found
[    0.753838] hub 8-0:1.0: USB hub found
[    0.808516] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   16.061854] lp: driver loaded but no devices found
[   16.185238] lis3lv02d: 8 bits sensor found
[   16.362644] uvcvideo: Found UVC 1.00 device HP Webcam (0408:03ba)
[   16.996632] input: HDA Intel HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13
[   16.996792] input: HDA Intel Dock Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input14
[   16.996928] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input15
[   16.997062] input: HDA Intel Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input16
[    0.186634] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.587960] [Firmware Bug]: Invalid critical threshold (0)
[   16.258709] ene_ir: Firmware regs: 80 00
[   16.783778] iwlwifi 0000:02:00.0: loaded firmware version 8.83.5.1 build 33692
[    0.454045] i2c-core: driver [aat2870] using legacy suspend method
[    0.454045] i2c-core: driver [aat2870] using legacy resume method
[    2.493359] r8169 0000:03:00.0: eth0: RTL8102e at 0xffffc90000c6e000, 00:1e:68:e3:0e:c5, XID 14a00000 IRQ 47
[   15.955769] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   17.019743] r8169 0000:03:00.0: eth0: link down
[   17.020889] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 4573.910516] usbcore: registered new interface driver cdc_ether
[   16.291269] iwlwifi 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   16.291278] iwlwifi 0000:02:00.0: setting latency timer to 64
[   16.291303] iwlwifi 0000:02:00.0: pci_resource_len = 0x00002000
[   16.291305] iwlwifi 0000:02:00.0: pci_resource_base = ffffc90000c7c000
[   16.291308] iwlwifi 0000:02:00.0: HW Revision ID = 0x0
[   16.292126] iwlwifi 0000:02:00.0: irq 49 for MSI/MSI-X
[   16.292169] iwlwifi 0000:02:00.0: Detected Intel(R) WiFi Link 5100 AGN, REV=0x54
[   16.292388] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S
[   16.313496] iwlwifi 0000:02:00.0: device EEPROM VER=0x11f, CALIB=0x4
[   16.313500] iwlwifi 0000:02:00.0: Device SKU: 0Xf0
[   16.313824] iwlwifi 0000:02:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   16.783778] iwlwifi 0000:02:00.0: loaded firmware version 8.83.5.1 build 33692
[   16.819086] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   16.834087] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S
[   16.837121] iwlwifi 0000:02:00.0: Radio type=0x1-0x2-0x0
[   16.954376] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S
[   16.957438] iwlwifi 0000:02:00.0: Radio type=0x1-0x2-0x0
[   17.013476] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   24.598789] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[   24.601257] wlan0: authenticated
[   24.605210] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[   24.607989] wlan0: RX AssocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[   24.607994] wlan0: associated
[   24.607997] wlan0: invalid AID value 0x7; bits 15:14 not set
[   24.612700] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   28.173382] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[   28.180559] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[   31.525100] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[   31.528974] wlan0: authenticated
[   31.530530] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[   31.533558] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[   31.533563] wlan0: associated
[   31.533565] wlan0: invalid AID value 0x7; bits 15:14 not set
[   35.102738] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[   35.116531] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[   38.408394] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[   38.410825] wlan0: authenticated
[   38.411835] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[   38.414772] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[   38.414777] wlan0: associated
[   38.414780] wlan0: invalid AID value 0x7; bits 15:14 not set
[   41.982571] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[   42.000599] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[   45.289415] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[   45.291736] wlan0: authenticated
[   45.292779] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[   45.295606] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[   45.295611] wlan0: associated
[   45.295614] wlan0: invalid AID value 0x7; bits 15:14 not set
[   48.862077] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[   48.880490] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[   52.217673] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[   52.219351] wlan0: authenticated
[   52.220382] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[   52.223216] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[   52.223220] wlan0: associated
[   52.223223] wlan0: invalid AID value 0x7; bits 15:14 not set
[   55.405357] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[   55.416494] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[   58.736880] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[   58.739255] wlan0: authenticated
[   58.740252] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[   58.743113] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[   58.743117] wlan0: associated
[   58.743121] wlan0: invalid AID value 0x7; bits 15:14 not set
[   62.747341] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[   62.752528] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[   66.114735] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[   66.312054] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 2)
[   66.367236] wlan0: authenticated
[   66.368264] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[   66.372298] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[   66.372302] wlan0: associated
[   66.372305] wlan0: invalid AID value 0x7; bits 15:14 not set
[   66.376188] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 7)
[   66.388581] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[   69.651013] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[   69.816051] wlan0: authenticated
[   69.817082] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[   69.820063] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[   69.820069] wlan0: associated
[   69.820073] wlan0: invalid AID value 0x7; bits 15:14 not set
[   73.456725] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[   73.464535] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[   76.791934] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[   76.794384] wlan0: authenticated
[   76.795385] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[   76.798118] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[   76.798122] wlan0: associated
[   76.798125] wlan0: invalid AID value 0x7; bits 15:14 not set
[   89.152018] wlan0: no IPv6 routers present
[  124.218943] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[  124.257929] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  131.381055] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[  131.383137] wlan0: authenticated
[  131.384201] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[  131.389754] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[  131.389758] wlan0: associated
[  131.389761] wlan0: invalid AID value 0x7; bits 15:14 not set
[  144.552068] wlan0: no IPv6 routers present
[  179.218068] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[  179.261845] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  185.160681] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[  185.162943] wlan0: authenticated
[  185.163938] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[  185.166694] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[  185.166699] wlan0: associated
[  185.166702] wlan0: invalid AID value 0x7; bits 15:14 not set
[  188.361622] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[  188.373366] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[  191.613101] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[  191.615475] wlan0: authenticated
[  191.616480] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[  191.619296] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[  191.619301] wlan0: associated
[  191.619304] wlan0: invalid AID value 0x7; bits 15:14 not set
[  195.409863] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[  195.416562] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[  198.703207] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[  198.900054] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 2)
[  198.966953] wlan0: authenticated
[  198.967993] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[  198.971529] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[  198.971533] wlan0: associated
[  198.971536] wlan0: invalid AID value 0x7; bits 15:14 not set
[  212.776022] wlan0: no IPv6 routers present
[  248.214217] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[  254.230620] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[  254.232723] wlan0: authenticated
[  254.233784] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[  254.236685] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[  254.236689] wlan0: associated
[  254.236691] wlan0: invalid AID value 0x7; bits 15:14 not set
[  254.240296] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  257.799562] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[  257.804513] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[  261.143533] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[  261.145875] wlan0: authenticated
[  261.146869] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[  261.149612] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[  261.149616] wlan0: associated
[  261.149620] wlan0: invalid AID value 0x7; bits 15:14 not set
[  264.186343] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[  264.200550] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[  267.514628] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[  267.517031] wlan0: authenticated
[  267.518051] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[  267.520797] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[  267.520802] wlan0: associated
[  267.520805] wlan0: invalid AID value 0x7; bits 15:14 not set
[  270.809389] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[  270.829123] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[  274.118060] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[  274.120161] wlan0: authenticated
[  274.121158] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[  274.123886] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[  274.123890] wlan0: associated
[  274.123893] wlan0: invalid AID value 0x7; bits 15:14 not set
[  287.072050] wlan0: no IPv6 routers present
[  322.236751] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[  322.278076] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  625.275359] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[  625.277616] wlan0: authenticated
[  625.278651] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[  625.281381] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[  625.281385] wlan0: associated
[  625.281388] wlan0: invalid AID value 0x7; bits 15:14 not set
[  628.848975] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[  628.872590] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[  632.145099] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[  632.147388] wlan0: authenticated
[  632.148408] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[  632.151138] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[  632.151143] wlan0: associated
[  632.151146] wlan0: invalid AID value 0x7; bits 15:14 not set
[  635.717497] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[  635.724520] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[  639.014743] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[  639.017112] wlan0: authenticated
[  639.018249] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[  639.021001] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[  639.021005] wlan0: associated
[  639.021008] wlan0: invalid AID value 0x7; bits 15:14 not set
[  642.493305] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[  642.496649] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[  645.765794] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[  645.767917] wlan0: authenticated
[  645.768962] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[  645.771703] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[  645.771709] wlan0: associated
[  645.771712] wlan0: invalid AID value 0x7; bits 15:14 not set
[  657.760055] wlan0: no IPv6 routers present
[  692.211890] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[  692.269875] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  698.192771] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[  698.194955] wlan0: authenticated
[  698.196044] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[  698.198912] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[  698.198917] wlan0: associated
[  698.198920] wlan0: invalid AID value 0x7; bits 15:14 not set
[  701.240108] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[  701.256531] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[  704.591932] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[  704.594046] wlan0: authenticated
[  704.595042] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[  704.597813] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[  704.597818] wlan0: associated
[  704.597821] wlan0: invalid AID value 0x7; bits 15:14 not set
[  708.163718] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[  708.168582] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[  711.402618] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[  711.404731] wlan0: authenticated
[  711.405974] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[  711.408738] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[  711.408742] wlan0: associated
[  711.408745] wlan0: invalid AID value 0x7; bits 15:14 not set
[  714.449542] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[  714.464554] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[  717.649780] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[  717.848035] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 2)
[  718.048026] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 3)
[  718.248027] wlan0: authentication with 98:fc:11:a9:0f:06 timed out
[  726.353278] wlan0: direct probe to 98:fc:11:a9:0f:06 (try 1/3)
[  726.552056] wlan0: direct probe to 98:fc:11:a9:0f:06 (try 2/3)
[  726.615514] wlan0: direct probe responded
[  726.615580] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[  726.816109] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 2)
[  727.016051] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 3)
[  727.184129] wlan0: authenticated
[  727.185156] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[  727.189303] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[  727.189306] wlan0: associated
[  727.189309] wlan0: invalid AID value 0x7; bits 15:14 not set
[  730.752077] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[  730.760622] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[  734.033071] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[  734.035388] wlan0: authenticated
[  734.036498] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[  734.039311] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[  734.039316] wlan0: associated
[  734.039319] wlan0: invalid AID value 0x7; bits 15:14 not set
[  737.601705] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[  737.608532] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[  740.895474] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[  740.897660] wlan0: authenticated
[  740.898654] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[  740.904370] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[  740.904375] wlan0: associated
[  740.904378] wlan0: invalid AID value 0x7; bits 15:14 not set
[  744.291954] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[  744.304772] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[  747.593887] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[  747.596042] wlan0: authenticated
[  747.597082] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[  747.599933] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[  747.599937] wlan0: associated
[  747.599941] wlan0: invalid AID value 0x7; bits 15:14 not set
[  750.690091] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[  750.696548] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[  754.033502] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[  754.035722] wlan0: authenticated
[  754.036732] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[  754.039460] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[  754.039465] wlan0: associated
[  754.039468] wlan0: invalid AID value 0x7; bits 15:14 not set
[  755.009619] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 1066.216371] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 1066.218589] wlan0: authenticated
[ 1066.219920] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 1066.222664] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 1066.222670] wlan0: associated
[ 1066.222673] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 1069.303669] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[ 1069.320547] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 1072.585305] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 1072.587507] wlan0: authenticated
[ 1072.588530] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 1072.591263] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 1072.591268] wlan0: associated
[ 1072.591271] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 1084.208023] wlan0: no IPv6 routers present
[ 1119.213254] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 1119.257974] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1422.175655] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 1422.177870] wlan0: authenticated
[ 1422.179969] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 1422.183743] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 1422.183746] wlan0: associated
[ 1422.183749] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 1434.176017] wlan0: no IPv6 routers present
[ 1469.209918] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 1469.265847] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1475.228526] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 1475.428039] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 2)
[ 1475.539702] wlan0: authenticated
[ 1475.542773] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 1475.546413] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 1475.546417] wlan0: associated
[ 1475.546419] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 1490.676019] wlan0: no IPv6 routers present
[ 1526.211892] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 1526.282346] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1531.360599] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 1531.363502] wlan0: authenticated
[ 1531.364588] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 1531.367410] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 1531.367414] wlan0: associated
[ 1531.367417] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 1535.335228] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[ 1535.337762] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 1538.605764] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 1538.608163] wlan0: authenticated
[ 1538.609472] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 1538.612280] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 1538.612284] wlan0: associated
[ 1538.612287] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 1550.848028] wlan0: no IPv6 routers present
[ 1585.212156] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 1585.285874] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1591.358629] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 1591.556032] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 2)
[ 1591.613759] wlan0: authenticated
[ 1591.614968] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 1591.621637] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 1591.621640] wlan0: associated
[ 1591.621643] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 1591.626756] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 7)
[ 1591.652563] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 1594.943161] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 1594.945342] wlan0: authenticated
[ 1594.947084] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 1594.949823] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 1594.949827] wlan0: associated
[ 1594.949829] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 1598.511856] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[ 1598.528699] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 1601.887634] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 1601.889885] wlan0: authenticated
[ 1601.890901] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 1601.893979] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 1601.893983] wlan0: associated
[ 1601.893986] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 1606.870224] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[ 1606.896507] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 1610.194541] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 1610.226804] wlan0: authenticated
[ 1610.227790] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 1610.230537] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 1610.230541] wlan0: associated
[ 1610.230544] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 1620.848022] wlan0: no IPv6 routers present
[ 1656.213708] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 1959.226529] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 1959.260364] wlan0: authenticated
[ 1959.261437] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 1959.264166] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 1959.264171] wlan0: associated
[ 1959.264174] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 1959.267540] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1962.830479] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[ 1962.834114] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 1966.134471] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 1966.332052] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 2)
[ 1966.342663] wlan0: authenticated
[ 1966.344612] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 1966.350499] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 1966.350504] wlan0: associated
[ 1966.350507] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 1969.910508] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[ 1969.916767] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 1973.231044] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 1973.428048] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 2)
[ 1973.628034] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 3)
[ 1973.726209] wlan0: authenticated
[ 1973.727402] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 1973.731696] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 1973.731701] wlan0: associated
[ 1973.731704] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 1973.735809] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 7)
[ 1973.748740] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 1976.994863] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 1976.998442] wlan0: authenticated
[ 1976.999452] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 1977.002310] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 1977.002314] wlan0: associated
[ 1977.002317] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 1987.496087] wlan0: no IPv6 routers present
[ 2022.210118] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 2028.167164] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 2028.368039] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 2)
[ 2028.506205] wlan0: authenticated
[ 2028.507286] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 2028.511327] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 2028.511332] wlan0: associated
[ 2028.511335] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 2028.515063] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 2028.515482] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 7)
[ 2028.528582] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 2031.852789] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 2031.855006] wlan0: authenticated
[ 2031.856077] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 2031.858831] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 2031.858836] wlan0: associated
[ 2031.858839] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 2042.464085] wlan0: no IPv6 routers present
[ 2077.210036] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 2083.183922] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 2083.186506] wlan0: authenticated
[ 2083.192861] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 2083.195778] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 2083.195782] wlan0: associated
[ 2083.195785] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 2083.199206] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 2093.528083] wlan0: no IPv6 routers present
[ 2129.219699] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 2135.217377] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 2135.219495] wlan0: authenticated
[ 2135.220544] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 2135.223326] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 2135.223332] wlan0: associated
[ 2135.223336] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 2135.226692] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 2148.784026] wlan0: no IPv6 routers present
[ 2183.214841] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 2183.281882] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 2486.198689] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 2486.200886] wlan0: authenticated
[ 2486.201899] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 2486.204641] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 2486.204645] wlan0: associated
[ 2486.204648] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 2489.454030] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[ 2489.476439] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 2492.762379] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 2492.816341] wlan0: authenticated
[ 2492.817415] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 2492.820234] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 2492.820237] wlan0: associated
[ 2492.820240] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 2497.779308] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[ 2497.784522] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 2501.101083] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 2501.214842] wlan0: authenticated
[ 2501.215902] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 2501.218679] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 2501.218684] wlan0: associated
[ 2501.218686] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 2511.840033] wlan0: no IPv6 routers present
[ 2547.211008] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 2547.246271] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 2553.230153] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 2553.341539] wlan0: authenticated
[ 2553.342559] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 2553.345303] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 2553.345307] wlan0: associated
[ 2553.345310] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 2556.862213] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[ 2556.872652] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 2560.198362] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 2560.322605] wlan0: authenticated
[ 2560.323908] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 2560.326389] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 2560.326393] wlan0: associated
[ 2560.326397] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 2564.945637] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[ 2564.952770] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 2568.172595] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 2568.372098] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 2)
[ 2568.401868] wlan0: authenticated
[ 2568.402875] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 2568.405349] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 2568.405353] wlan0: associated
[ 2568.405356] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 2568.411075] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 7)
[ 2568.436615] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 2571.678954] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 2571.681263] wlan0: authenticated
[ 2571.682256] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 2571.685046] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 2571.685050] wlan0: associated
[ 2571.685053] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 2576.323209] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[ 2576.328538] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 2579.655252] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 2579.852103] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 2)
[ 2580.051719] wlan0: authenticated
[ 2580.052921] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 2580.057173] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 2580.057177] wlan0: associated
[ 2580.057179] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 2580.560380] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 7)
[ 2580.568597] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 2583.802776] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 2584.000124] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 2)
[ 2584.200034] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 3)
[ 2584.400124] wlan0: authentication with 98:fc:11:a9:0f:06 timed out
[ 2596.748847] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 2596.852260] wlan0: authenticated
[ 2596.853315] wlan0: waiting for beacon from 98:fc:11:a9:0f:06
[ 2596.894167] wlan0: beacon received
[ 2596.916035] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 2596.920164] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 2596.920167] wlan0: associated
[ 2596.920170] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 2608.400109] wlan0: no IPv6 routers present
[ 2644.210204] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 2644.262796] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 2650.159035] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 2650.274440] wlan0: authenticated
[ 2650.275507] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 2650.278316] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 2650.278320] wlan0: associated
[ 2650.278324] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 2661.080106] wlan0: no IPv6 routers present
[ 2696.209090] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 2696.253825] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 2702.176546] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 2702.178890] wlan0: authenticated
[ 2702.179881] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 2702.182623] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 2702.182627] wlan0: associated
[ 2702.182630] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 2712.464085] wlan0: no IPv6 routers present
[ 2748.207876] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 3051.181911] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 3051.184094] wlan0: authenticated
[ 3051.185118] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 3051.187880] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 3051.187884] wlan0: associated
[ 3051.187887] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 3051.191310] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 3064.096087] wlan0: no IPv6 routers present
[ 3099.211514] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 3099.266368] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 3105.248612] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 3105.250812] wlan0: authenticated
[ 3105.251817] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 3105.254551] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 3105.254556] wlan0: associated
[ 3105.254560] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 3108.970823] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[ 3108.976528] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 3112.320976] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 3112.323121] wlan0: authenticated
[ 3112.324124] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 3112.328204] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 3112.328208] wlan0: associated
[ 3112.328211] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 3123.440110] wlan0: no IPv6 routers present
[ 3158.211063] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 3158.269809] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 3164.233450] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 3164.236367] wlan0: authenticated
[ 3164.237379] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 3164.240154] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 3164.240157] wlan0: associated
[ 3164.240160] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 3164.769453] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 3217.005233] wlan0: direct probe to 00:1d:7e:59:ea:1a (try 1/3)
[ 3217.204121] wlan0: direct probe to 00:1d:7e:59:ea:1a (try 2/3)
[ 3217.404047] wlan0: direct probe to 00:1d:7e:59:ea:1a (try 3/3)
[ 3217.604084] wlan0: direct probe to 00:1d:7e:59:ea:1a timed out
[ 3231.240731] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 3231.242862] wlan0: authenticated
[ 3231.243975] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 3231.246963] wlan0: RX AssocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 3231.246968] wlan0: associated
[ 3231.246971] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 3234.284562] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[ 3234.290560] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 3237.565981] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 3237.571070] wlan0: authenticated
[ 3237.572204] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 3237.576618] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 3237.576622] wlan0: associated
[ 3237.576626] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 3240.615232] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[ 3240.630406] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 3243.911685] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 3243.914036] wlan0: authenticated
[ 3243.915463] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 3243.918853] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 3243.918858] wlan0: associated
[ 3243.918861] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 3246.965342] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[ 3246.968725] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 3250.265298] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 3250.267774] wlan0: authenticated
[ 3250.268859] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 3250.271623] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 3250.271627] wlan0: associated
[ 3250.271631] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 3253.313842] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[ 3253.320589] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 3256.643449] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 3256.645621] wlan0: authenticated
[ 3256.646648] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 3256.649394] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 3256.649398] wlan0: associated
[ 3256.649400] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 3259.694016] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[ 3259.707104] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 3263.065298] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 3263.067688] wlan0: authenticated
[ 3263.068712] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 3263.071465] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 3263.071469] wlan0: associated
[ 3263.071472] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 3266.113572] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[ 3266.120568] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 3269.378250] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 3269.380380] wlan0: authenticated
[ 3269.381411] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 3269.384176] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 3269.384179] wlan0: associated
[ 3269.384182] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 3272.425496] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[ 3272.444497] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 3275.710835] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 3275.713190] wlan0: authenticated
[ 3275.715488] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 3275.719493] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 3275.719497] wlan0: associated
[ 3275.719501] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 3278.763890] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[ 3278.780599] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 3282.005369] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 3282.007636] wlan0: authenticated
[ 3282.009677] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 3282.012914] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 3282.012919] wlan0: associated
[ 3282.012922] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 3285.052212] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[ 3285.056732] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 3293.878764] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 3293.881030] wlan0: authenticated
[ 3293.882047] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 3293.884777] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 3293.884781] wlan0: associated
[ 3293.884785] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 3296.931507] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[ 3296.936552] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 3300.224217] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 3300.226513] wlan0: authenticated
[ 3300.227537] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 3300.230288] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 3300.230292] wlan0: associated
[ 3300.230296] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 3303.271351] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[ 3303.276553] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 3306.547292] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 3306.549527] wlan0: authenticated
[ 3306.550524] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 3306.553270] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 3306.553275] wlan0: associated
[ 3306.553277] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 3309.590360] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[ 3309.596550] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 3312.927257] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 3312.929579] wlan0: authenticated
[ 3312.930576] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 3312.933316] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 3312.933321] wlan0: associated
[ 3312.933324] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 3315.980547] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[ 3315.984709] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 3319.300207] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 3319.302547] wlan0: authenticated
[ 3319.303545] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 3319.306275] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 3319.306279] wlan0: associated
[ 3319.306282] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 3322.350620] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[ 3322.356486] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 3325.696640] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 3325.699044] wlan0: authenticated
[ 3325.700052] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 3325.702795] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 3325.702799] wlan0: associated
[ 3325.702802] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 3328.749143] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[ 3328.760423] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 3332.046698] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 3332.048900] wlan0: authenticated
[ 3332.049900] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 3332.052684] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 3332.052687] wlan0: associated
[ 3332.052690] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 3335.099349] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[ 3335.116566] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 3338.406519] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 3338.408680] wlan0: authenticated
[ 3338.409685] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 3338.412438] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 3338.412443] wlan0: associated
[ 3338.412446] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 3341.459955] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[ 3341.468055] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 3344.748991] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 3344.751261] wlan0: authenticated
[ 3344.752272] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 3344.755013] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 3344.755018] wlan0: associated
[ 3344.755021] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 3347.799048] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[ 3347.804574] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 3358.899016] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 3358.901108] wlan0: authenticated
[ 3358.902123] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 3358.904966] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 3358.904971] wlan0: associated
[ 3358.904974] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 3361.952376] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[ 3361.968691] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 3365.258326] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 3365.261364] wlan0: authenticated
[ 3365.262829] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 3365.265564] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 3365.265569] wlan0: associated
[ 3365.265572] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 3368.307450] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[ 3368.320591] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 3371.614655] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 3371.616938] wlan0: authenticated
[ 3371.617934] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 3371.620694] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 3371.620698] wlan0: associated
[ 3371.620701] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 3374.666808] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[ 3374.672727] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 3377.933070] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 3377.935119] wlan0: authenticated
[ 3377.936121] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 3377.938851] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 3377.938855] wlan0: associated
[ 3377.938859] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 3380.976584] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[ 3380.988551] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 3384.173202] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 3384.175406] wlan0: authenticated
[ 3384.176435] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 3384.179226] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 3384.179230] wlan0: associated
[ 3384.179233] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 3387.225490] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[ 3387.236546] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 3390.539793] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 3390.542127] wlan0: authenticated
[ 3390.543133] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 3390.545882] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 3390.545886] wlan0: associated
[ 3390.545889] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 3393.586871] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[ 3393.592565] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 3396.905410] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 3396.907856] wlan0: authenticated
[ 3396.908870] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 3396.911603] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 3396.911607] wlan0: associated
[ 3396.911611] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 3399.956299] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[ 3399.960660] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 3403.216436] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 3403.218706] wlan0: authenticated
[ 3403.219707] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 3403.223620] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 3403.223624] wlan0: associated
[ 3403.223627] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 3410.123033] iwlwifi 0000:02:00.0: Tx aggregation enabled on ra = 98:fc:11:a9:0f:06 tid = 0
[ 3417.056021] wlan0: no IPv6 routers present
[ 3452.211992] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 3458.228555] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 3458.230953] wlan0: authenticated
[ 3458.231949] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 3458.234774] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 3458.234778] wlan0: associated
[ 3458.234781] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 3458.238346] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 3461.272172] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[ 3461.288561] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 3464.577491] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 3464.579786] wlan0: authenticated
[ 3464.580801] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 3464.583555] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 3464.583561] wlan0: associated
[ 3464.583565] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 3467.621598] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[ 3467.627903] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 3470.953313] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 3470.955420] wlan0: authenticated
[ 3470.956434] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 3470.959165] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 3470.959169] wlan0: associated
[ 3470.959172] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 3474.000619] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[ 3474.008554] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 3477.274251] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 3477.276372] wlan0: authenticated
[ 3477.277371] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 3477.280115] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 3477.280120] wlan0: associated
[ 3477.280124] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 3480.321235] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[ 3480.324712] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 3483.601163] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 3483.603507] wlan0: authenticated
[ 3483.605087] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 3483.607808] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 3483.607812] wlan0: associated
[ 3483.607814] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 3486.651147] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[ 3486.656538] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 3489.973355] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 3489.975545] wlan0: authenticated
[ 3489.976564] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 3489.979352] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 3489.979356] wlan0: associated
[ 3489.979359] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 3493.020079] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[ 3493.040519] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 3496.336683] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 3496.339811] wlan0: authenticated
[ 3496.340910] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 3496.343718] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 3496.343722] wlan0: associated
[ 3496.343726] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 3499.390159] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[ 3499.392676] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 3502.715053] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 3502.717328] wlan0: authenticated
[ 3502.719102] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 3502.721850] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 3502.721854] wlan0: associated
[ 3502.721857] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 3505.759306] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[ 3505.768520] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 3509.087365] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 3509.091011] wlan0: authenticated
[ 3509.092249] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 3509.094976] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 3509.094980] wlan0: associated
[ 3509.094983] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 3512.188219] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[ 3512.199005] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3512.199197] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3512.240251] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 3515.471464] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 3515.473728] wlan0: authenticated
[ 3515.474727] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 3515.477466] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 3515.477471] wlan0: associated
[ 3515.477474] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 3515.480834] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 3520.977527] iwlwifi 0000:02:00.0: Tx aggregation enabled on ra = 98:fc:11:a9:0f:06 tid = 0
[ 3525.980084] wlan0: no IPv6 routers present
[ 3557.211195] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 3557.273692] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 3563.195961] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 3563.198381] wlan0: authenticated
[ 3563.199376] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 3563.202255] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 3563.202260] wlan0: associated
[ 3563.202263] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 3577.656034] wlan0: no IPv6 routers present
[ 3613.209542] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 3619.187825] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 3619.190015] wlan0: authenticated
[ 3619.191012] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 3619.193738] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 3619.193742] wlan0: associated
[ 3619.193745] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 3619.197143] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 3631.056143] wlan0: no IPv6 routers present
[ 3658.210869] iwlwifi 0000:02:00.0: Tx aggregation enabled on ra = 98:fc:11:a9:0f:06 tid = 0
[ 3666.209040] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 3666.265942] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 3969.090856] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 3969.092965] wlan0: authenticated
[ 3969.093960] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 3969.096755] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 3969.096760] wlan0: associated
[ 3969.096763] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 3980.200052] wlan0: no IPv6 routers present
[ 4014.209275] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 4020.189669] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 4020.388033] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 2)
[ 4020.579721] wlan0: authenticated
[ 4020.580843] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 4020.584978] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 4020.584982] wlan0: associated
[ 4020.584985] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 4020.591491] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 4020.592341] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 7)
[ 4020.608516] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 4023.775866] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 4023.778295] wlan0: authenticated
[ 4023.779286] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 4023.782024] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 4023.782028] wlan0: associated
[ 4023.782030] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 4034.480085] wlan0: no IPv6 routers present
[ 4069.211317] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 4075.199733] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 4075.201969] wlan0: authenticated
[ 4075.202968] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 4075.205773] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 4075.205777] wlan0: associated
[ 4075.205781] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 4075.209143] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 4088.592028] wlan0: no IPv6 routers present
[ 4123.210612] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 4129.248514] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 4129.250872] wlan0: authenticated
[ 4129.251872] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 4129.254743] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 4129.254747] wlan0: associated
[ 4129.254750] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 4129.258151] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 4141.264030] wlan0: no IPv6 routers present
[ 4176.210103] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 4176.273863] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 4438.827859] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 4438.830072] wlan0: authenticated
[ 4438.831066] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 4438.833804] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 4438.833808] wlan0: associated
[ 4438.833811] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 4442.021467] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[ 4442.024636] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 4445.317333] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 4445.319683] wlan0: authenticated
[ 4445.320743] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 4445.323521] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 4445.323525] wlan0: associated
[ 4445.323528] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 4448.371448] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[ 4448.376517] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 4451.690228] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 4451.692544] wlan0: authenticated
[ 4451.693542] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 4451.696280] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 4451.696285] wlan0: associated
[ 4451.696288] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 4463.008051] wlan0: no IPv6 routers present
[ 4497.208084] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 4497.277836] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 4503.119881] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 4503.122160] wlan0: authenticated
[ 4503.123172] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 4503.127221] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 4503.127225] wlan0: associated
[ 4503.127229] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 4514.116071] wlan0: no IPv6 routers present
[ 4549.207536] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 4549.250325] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 4555.133634] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 4555.135941] wlan0: authenticated
[ 4555.136943] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 4555.139811] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 4555.139815] wlan0: associated
[ 4555.139818] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 4558.368259] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[ 4558.379096] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4558.379271] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4558.404216] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 4561.721062] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 4561.723350] wlan0: authenticated
[ 4561.724424] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 4561.727207] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 4561.727211] wlan0: associated
[ 4561.727214] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 4561.731634] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 4572.080119] wlan0: no IPv6 routers present
[ 4604.210643] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 4610.166106] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 4610.168471] wlan0: authenticated
[ 4610.169535] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 4610.172293] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 4610.172298] wlan0: associated
[ 4610.172301] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 4610.178478] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 4621.584049] wlan0: no IPv6 routers present
[ 4657.211618] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 4657.261911] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 4960.228372] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 4960.230581] wlan0: authenticated
[ 4960.231572] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 4960.234664] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 4960.234668] wlan0: associated
[ 4960.234671] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 4963.423551] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[ 4963.426018] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 4966.657879] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 4966.660269] wlan0: authenticated
[ 4966.661321] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 4966.664086] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 4966.664093] wlan0: associated
[ 4966.664097] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 4979.304060] wlan0: no IPv6 routers present
[ 4981.873084] martian source 255.255.255.255 from 192.168.1.1, on dev wlan0
[ 4981.876057] martian source 255.255.255.255 from 192.168.1.1, on dev wlan0
[ 4997.010404] iwlwifi 0000:02:00.0: Tx aggregation enabled on ra = 98:fc:11:a9:0f:06 tid = 0
[ 5015.721281] iwlwifi 0000:02:00.0: Tx aggregation enabled on ra = 98:fc:11:a9:0f:06 tid = 0
[ 5074.393621] iwlwifi 0000:02:00.0: Tx aggregation enabled on ra = 98:fc:11:a9:0f:06 tid = 0
[ 5154.445560] iwlwifi 0000:02:00.0: Tx aggregation enabled on ra = 98:fc:11:a9:0f:06 tid = 0
[    0.460120] Switching to clocksource hpet
[    0.581679] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
[    0.582683] ACPI: Lid Switch [LID0]
[   16.921307] Console: switching to colour frame buffer device 160x50
lo        no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"homenet"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 98:FC:11:A9:0F:06  
          Bit Rate=28.9 Mb/s   Tx-Power=15 dBm  
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=46/70  Signal level=-64 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:9418  Invalid misc:133   Missed beacon:0

eth0      no wireless extensions.

/etc/modprobe.d/blacklist.conf:# replaced by b43 and ssb.
/etc/modprobe.d/blacklist-watchdog.conf:blacklist twl4030_wdt
/etc/modprobe.d/wlan.conf:options iwlcore led_mode=1
>  hal.1: read hal dataprocess 7394: arguments to dbus_move_error() were  incorrect, assertion "(dest) == NULL || !dbus_error_is_set ((dest))"  failed in file ../../dbus/dbus-errors.c line 282.
This is normally a bug in some application using the D-Bus library.
libhal.c 3483 : Error unsubscribing to signals, error=The name org.freedesktop.Hal was not provided by any .service files
30: PCI 200.0: 0282 WLAN controller                            
  [Created at pci.318]
  Unique ID: y9sn.GbTjk0YbA70
  Parent ID: z8Q3.yhz5TIKH5m7
  SysFS ID: /devices/pci0000:00/0000:00:1c.0/0000:02:00.0
  SysFS BusID: 0000:02:00.0
  Hardware Class: network
  Model: "Intel PRO/Wireless 5100 AGN [Shiloh] Network Connection"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x4237 "PRO/Wireless 5100 AGN [Shiloh] Network Connection"
  SubVendor: pci 0x8086 "Intel Corporation"
  SubDevice: pci 0x1211
  Driver: "iwlwifi"
  Driver Modules: "iwlwifi"
  Device File: wlan0
  Features: WLAN
  Memory Range: 0xdb600000-0xdb601fff (rw,non-prefetchable)
  IRQ: 49 (189425 events)
  HW Address: 00:16:ea:df:95:d2
  Link detected: yes
  WLAN channels: 1 2 3 4 5 6 7 8 9 10 11 12 13 36 40 44 48 52 56 60 64 100 104 108 112 116 120 124 128 132 136 140
   WLAN frequencies: 2.412 2.417 2.422 2.427 2.432 2.437 2.442 2.447 2.452  2.457 2.462 2.467 2.472 5.18 5.2 5.22 5.24 5.26 5.28 5.3 5.32 5.5 5.52  5.54 5.56 5.58 5.6 5.62 5.64 5.66 5.68 5.7
  WLAN encryption modes: WEP40 WEP104 TKIP CCMP
  WLAN authentication modes: open sharedkey wpa-psk wpa-eap
  Module Alias: "pci:v00008086d00004237sv00008086sd00001211bc02sc80i00"
  Driver Info #0:
    Driver Status: iwlwifi is active
    Driver Activation Cmd: "modprobe iwlwifi"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #14 (PCI bridge)

31: PCI 300.0: 0200 Ethernet controller
  [Created at pci.318]
  Unique ID: rBUF.NCUxv_EAKE0
  Parent ID: qTvu._WsbQRZh8X8
  SysFS ID: /devices/pci0000:00/0000:00:1c.1/0000:03:00.0
  SysFS BusID: 0000:03:00.0
  Hardware Class: network
  Model: "Realtek RTL8101E/RTL8102E PCI Express Fast Ethernet controller"
  Vendor: pci 0x10ec "Realtek Semiconductor Co., Ltd."
  Device: pci 0x8136 "RTL8101E/RTL8102E PCI Express Fast Ethernet controller"
  SubVendor: pci 0x103c "Hewlett-Packard Company"
  SubDevice: pci 0x3602
  Revision: 0x02
  Driver: "r8169"
  Driver Modules: "r8169"
  Device File: eth0
  I/O Ports: 0x6000-0x7fff (rw)
  Memory Range: 0xd1410000-0xd1410fff (ro,non-prefetchable)
  Memory Range: 0xd1400000-0xd140ffff (ro,non-prefetchable)
  Memory Range: 0xd1420000-0xd142ffff (ro,non-prefetchable,disabled)
  IRQ: 47 (no events)
  HW Address: 00:1e:68:e3:0e:c5
  Link detected: no
  Module Alias: "pci:v000010ECd00008136sv0000103Csd00003602bc02sc00i00"
  Driver Info #0:
    Driver Status: r8169 is active
    Driver Activation Cmd: "modprobe r8169"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #15 (PCI bridge)
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                   [ OK ]
[   16.291269] iwlwifi 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   16.291278] iwlwifi 0000:02:00.0: setting latency timer to 64
[   16.291303] iwlwifi 0000:02:00.0: pci_resource_len = 0x00002000
[   16.291305] iwlwifi 0000:02:00.0: pci_resource_base = ffffc90000c7c000
[   16.291308] iwlwifi 0000:02:00.0: HW Revision ID = 0x0
[   16.292126] iwlwifi 0000:02:00.0: irq 49 for MSI/MSI-X
[   16.292169] iwlwifi 0000:02:00.0: Detected Intel(R) WiFi Link 5100 AGN, REV=0x54
[   16.292388] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S
[   16.313496] iwlwifi 0000:02:00.0: device EEPROM VER=0x11f, CALIB=0x4
[   16.313500] iwlwifi 0000:02:00.0: Device SKU: 0Xf0
[   16.313824] iwlwifi 0000:02:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   16.783778] iwlwifi 0000:02:00.0: loaded firmware version 8.83.5.1 build 33692
[   16.819086] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   16.834087] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S
[   16.837121] iwlwifi 0000:02:00.0: Radio type=0x1-0x2-0x0
[   16.954376] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S
[   16.957438] iwlwifi 0000:02:00.0: Radio type=0x1-0x2-0x0
[   17.013476] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   24.598789] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[   24.601257] wlan0: authenticated
[   24.605210] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[   24.607989] wlan0: RX AssocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[   24.607994] wlan0: associated
[   24.607997] wlan0: invalid AID value 0x7; bits 15:14 not set
[   24.612700] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   28.173382] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[   28.180559] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[   31.525100] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[   31.528974] wlan0: authenticated
[   31.530530] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[   31.533558] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[   31.533563] wlan0: associated
[   31.533565] wlan0: invalid AID value 0x7; bits 15:14 not set
[   35.102738] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[   35.116531] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[   38.408394] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[   38.410825] wlan0: authenticated
[   38.411835] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[   38.414772] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[   38.414777] wlan0: associated
[   38.414780] wlan0: invalid AID value 0x7; bits 15:14 not set
[   41.982571] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[   42.000599] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[   45.289415] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[   45.291736] wlan0: authenticated
[   45.292779] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[   45.295606] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[   45.295611] wlan0: associated
[   45.295614] wlan0: invalid AID value 0x7; bits 15:14 not set
[   48.862077] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[   48.880490] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[   52.217673] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[   52.219351] wlan0: authenticated
[   52.220382] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[   52.223216] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[   52.223220] wlan0: associated
[   52.223223] wlan0: invalid AID value 0x7; bits 15:14 not set
[   55.405357] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[   55.416494] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[   58.736880] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[   58.739255] wlan0: authenticated
[   58.740252] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[   58.743113] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[   58.743117] wlan0: associated
[   58.743121] wlan0: invalid AID value 0x7; bits 15:14 not set
[   62.747341] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[   62.752528] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[   66.114735] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[   66.312054] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 2)
[   66.367236] wlan0: authenticated
[   66.368264] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[   66.372298] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[   66.372302] wlan0: associated
[   66.372305] wlan0: invalid AID value 0x7; bits 15:14 not set
[   66.376188] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 7)
[   66.388581] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[   69.651013] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[   69.816051] wlan0: authenticated
[   69.817082] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[   69.820063] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[   69.820069] wlan0: associated
[   69.820073] wlan0: invalid AID value 0x7; bits 15:14 not set
[   73.456725] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[   73.464535] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[   76.791934] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[   76.794384] wlan0: authenticated
[   76.795385] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[   76.798118] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[   76.798122] wlan0: associated
[   76.798125] wlan0: invalid AID value 0x7; bits 15:14 not set
[   89.152018] wlan0: no IPv6 routers present
[  124.218943] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[  124.257929] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  131.381055] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[  131.383137] wlan0: authenticated
[  131.384201] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[  131.389754] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[  131.389758] wlan0: associated
[  131.389761] wlan0: invalid AID value 0x7; bits 15:14 not set
[  144.552068] wlan0: no IPv6 routers present
[  179.218068] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[  179.261845] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  185.160681] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[  185.162943] wlan0: authenticated
[  185.163938] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[  185.166694] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[  185.166699] wlan0: associated
[  185.166702] wlan0: invalid AID value 0x7; bits 15:14 not set
[  188.361622] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[  188.373366] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[  191.613101] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[  191.615475] wlan0: authenticated
[  191.616480] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[  191.619296] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[  191.619301] wlan0: associated
[  191.619304] wlan0: invalid AID value 0x7; bits 15:14 not set
[  195.409863] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[  195.416562] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[  198.703207] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[  198.900054] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 2)
[  198.966953] wlan0: authenticated
[  198.967993] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[  198.971529] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[  198.971533] wlan0: associated
[  198.971536] wlan0: invalid AID value 0x7; bits 15:14 not set
[  212.776022] wlan0: no IPv6 routers present
[  248.214217] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[  254.230620] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[  254.232723] wlan0: authenticated
[  254.233784] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[  254.236685] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[  254.236689] wlan0: associated
[  254.236691] wlan0: invalid AID value 0x7; bits 15:14 not set
[  254.240296] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  257.799562] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[  257.804513] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[  261.143533] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[  261.145875] wlan0: authenticated
[  261.146869] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[  261.149612] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[  261.149616] wlan0: associated
[  261.149620] wlan0: invalid AID value 0x7; bits 15:14 not set
[  264.186343] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[  264.200550] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[  267.514628] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[  267.517031] wlan0: authenticated
[  267.518051] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[  267.520797] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[  267.520802] wlan0: associated
[  267.520805] wlan0: invalid AID value 0x7; bits 15:14 not set
[  270.809389] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[  270.829123] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[  274.118060] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[  274.120161] wlan0: authenticated
[  274.121158] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[  274.123886] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[  274.123890] wlan0: associated
[  274.123893] wlan0: invalid AID value 0x7; bits 15:14 not set
[  287.072050] wlan0: no IPv6 routers present
[  322.236751] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[  322.278076] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  625.275359] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[  625.277616] wlan0: authenticated
[  625.278651] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[  625.281381] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[  625.281385] wlan0: associated
[  625.281388] wlan0: invalid AID value 0x7; bits 15:14 not set
[  628.848975] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[  628.872590] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[  632.145099] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[  632.147388] wlan0: authenticated
[  632.148408] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[  632.151138] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[  632.151143] wlan0: associated
[  632.151146] wlan0: invalid AID value 0x7; bits 15:14 not set
[  635.717497] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[  635.724520] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[  639.014743] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[  639.017112] wlan0: authenticated
[  639.018249] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[  639.021001] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[  639.021005] wlan0: associated
[  639.021008] wlan0: invalid AID value 0x7; bits 15:14 not set
[  642.493305] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[  642.496649] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[  645.765794] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[  645.767917] wlan0: authenticated
[  645.768962] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[  645.771703] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[  645.771709] wlan0: associated
[  645.771712] wlan0: invalid AID value 0x7; bits 15:14 not set
[  657.760055] wlan0: no IPv6 routers present
[  692.211890] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[  692.269875] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  698.192771] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[  698.194955] wlan0: authenticated
[  698.196044] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[  698.198912] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[  698.198917] wlan0: associated
[  698.198920] wlan0: invalid AID value 0x7; bits 15:14 not set
[  701.240108] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[  701.256531] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[  704.591932] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[  704.594046] wlan0: authenticated
[  704.595042] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[  704.597813] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[  704.597818] wlan0: associated
[  704.597821] wlan0: invalid AID value 0x7; bits 15:14 not set
[  708.163718] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[  708.168582] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[  711.402618] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[  711.404731] wlan0: authenticated
[  711.405974] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[  711.408738] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[  711.408742] wlan0: associated
[  711.408745] wlan0: invalid AID value 0x7; bits 15:14 not set
[  714.449542] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[  714.464554] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[  717.649780] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[  717.848035] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 2)
[  718.048026] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 3)
[  718.248027] wlan0: authentication with 98:fc:11:a9:0f:06 timed out
[  726.353278] wlan0: direct probe to 98:fc:11:a9:0f:06 (try 1/3)
[  726.552056] wlan0: direct probe to 98:fc:11:a9:0f:06 (try 2/3)
[  726.615514] wlan0: direct probe responded
[  726.615580] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[  726.816109] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 2)
[  727.016051] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 3)
[  727.184129] wlan0: authenticated
[  727.185156] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[  727.189303] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[  727.189306] wlan0: associated
[  727.189309] wlan0: invalid AID value 0x7; bits 15:14 not set
[  730.752077] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[  730.760622] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[  734.033071] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[  734.035388] wlan0: authenticated
[  734.036498] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[  734.039311] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[  734.039316] wlan0: associated
[  734.039319] wlan0: invalid AID value 0x7; bits 15:14 not set
[  737.601705] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[  737.608532] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[  740.895474] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[  740.897660] wlan0: authenticated
[  740.898654] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[  740.904370] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[  740.904375] wlan0: associated
[  740.904378] wlan0: invalid AID value 0x7; bits 15:14 not set
[  744.291954] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[  744.304772] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[  747.593887] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[  747.596042] wlan0: authenticated
[  747.597082] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[  747.599933] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[  747.599937] wlan0: associated
[  747.599941] wlan0: invalid AID value 0x7; bits 15:14 not set
[  750.690091] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[  750.696548] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[  754.033502] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[  754.035722] wlan0: authenticated
[  754.036732] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[  754.039460] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[  754.039465] wlan0: associated
[  754.039468] wlan0: invalid AID value 0x7; bits 15:14 not set
[  755.009619] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 1066.216371] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 1066.218589] wlan0: authenticated
[ 1066.219920] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 1066.222664] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 1066.222670] wlan0: associated
[ 1066.222673] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 1069.303669] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[ 1069.320547] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 1072.585305] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 1072.587507] wlan0: authenticated
[ 1072.588530] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 1072.591263] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 1072.591268] wlan0: associated
[ 1072.591271] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 1084.208023] wlan0: no IPv6 routers present
[ 1119.213254] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 1119.257974] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1422.175655] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 1422.177870] wlan0: authenticated
[ 1422.179969] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 1422.183743] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 1422.183746] wlan0: associated
[ 1422.183749] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 1434.176017] wlan0: no IPv6 routers present
[ 1469.209918] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 1469.265847] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1475.228526] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 1475.428039] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 2)
[ 1475.539702] wlan0: authenticated
[ 1475.542773] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 1475.546413] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 1475.546417] wlan0: associated
[ 1475.546419] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 1490.676019] wlan0: no IPv6 routers present
[ 1526.211892] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 1526.282346] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1531.360599] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 1531.363502] wlan0: authenticated
[ 1531.364588] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 1531.367410] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 1531.367414] wlan0: associated
[ 1531.367417] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 1535.335228] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[ 1535.337762] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 1538.605764] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 1538.608163] wlan0: authenticated
[ 1538.609472] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 1538.612280] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 1538.612284] wlan0: associated
[ 1538.612287] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 1550.848028] wlan0: no IPv6 routers present
[ 1585.212156] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 1585.285874] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1591.358629] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 1591.556032] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 2)
[ 1591.613759] wlan0: authenticated
[ 1591.614968] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 1591.621637] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 1591.621640] wlan0: associated
[ 1591.621643] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 1591.626756] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 7)
[ 1591.652563] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 1594.943161] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 1594.945342] wlan0: authenticated
[ 1594.947084] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 1594.949823] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 1594.949827] wlan0: associated
[ 1594.949829] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 1598.511856] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[ 1598.528699] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 1601.887634] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 1601.889885] wlan0: authenticated
[ 1601.890901] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 1601.893979] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 1601.893983] wlan0: associated
[ 1601.893986] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 1606.870224] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[ 1606.896507] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 1610.194541] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 1610.226804] wlan0: authenticated
[ 1610.227790] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 1610.230537] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 1610.230541] wlan0: associated
[ 1610.230544] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 1620.848022] wlan0: no IPv6 routers present
[ 1656.213708] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 1959.226529] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 1959.260364] wlan0: authenticated
[ 1959.261437] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 1959.264166] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 1959.264171] wlan0: associated
[ 1959.264174] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 1959.267540] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1962.830479] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[ 1962.834114] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 1966.134471] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 1966.332052] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 2)
[ 1966.342663] wlan0: authenticated
[ 1966.344612] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 1966.350499] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 1966.350504] wlan0: associated
[ 1966.350507] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 1969.910508] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[ 1969.916767] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 1973.231044] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 1973.428048] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 2)
[ 1973.628034] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 3)
[ 1973.726209] wlan0: authenticated
[ 1973.727402] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 1973.731696] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 1973.731701] wlan0: associated
[ 1973.731704] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 1973.735809] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 7)
[ 1973.748740] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 1976.994863] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 1976.998442] wlan0: authenticated
[ 1976.999452] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 1977.002310] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 1977.002314] wlan0: associated
[ 1977.002317] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 1987.496087] wlan0: no IPv6 routers present
[ 2022.210118] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 2028.167164] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 2028.368039] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 2)
[ 2028.506205] wlan0: authenticated
[ 2028.507286] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 2028.511327] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 2028.511332] wlan0: associated
[ 2028.511335] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 2028.515063] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 2028.515482] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 7)
[ 2028.528582] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 2031.852789] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 2031.855006] wlan0: authenticated
[ 2031.856077] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 2031.858831] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 2031.858836] wlan0: associated
[ 2031.858839] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 2042.464085] wlan0: no IPv6 routers present
[ 2077.210036] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 2083.183922] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 2083.186506] wlan0: authenticated
[ 2083.192861] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 2083.195778] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 2083.195782] wlan0: associated
[ 2083.195785] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 2083.199206] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 2093.528083] wlan0: no IPv6 routers present
[ 2129.219699] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 2135.217377] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 2135.219495] wlan0: authenticated
[ 2135.220544] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 2135.223326] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 2135.223332] wlan0: associated
[ 2135.223336] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 2135.226692] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 2148.784026] wlan0: no IPv6 routers present
[ 2183.214841] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 2183.281882] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 2486.198689] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 2486.200886] wlan0: authenticated
[ 2486.201899] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 2486.204641] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 2486.204645] wlan0: associated
[ 2486.204648] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 2489.454030] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[ 2489.476439] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 2492.762379] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 2492.816341] wlan0: authenticated
[ 2492.817415] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 2492.820234] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 2492.820237] wlan0: associated
[ 2492.820240] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 2497.779308] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[ 2497.784522] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 2501.101083] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 2501.214842] wlan0: authenticated
[ 2501.215902] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 2501.218679] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 2501.218684] wlan0: associated
[ 2501.218686] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 2511.840033] wlan0: no IPv6 routers present
[ 2547.211008] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 2547.246271] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 2553.230153] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 2553.341539] wlan0: authenticated
[ 2553.342559] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 2553.345303] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 2553.345307] wlan0: associated
[ 2553.345310] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 2556.862213] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[ 2556.872652] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 2560.198362] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 2560.322605] wlan0: authenticated
[ 2560.323908] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 2560.326389] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 2560.326393] wlan0: associated
[ 2560.326397] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 2564.945637] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[ 2564.952770] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 2568.172595] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 2568.372098] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 2)
[ 2568.401868] wlan0: authenticated
[ 2568.402875] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 2568.405349] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 2568.405353] wlan0: associated
[ 2568.405356] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 2568.411075] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 7)
[ 2568.436615] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 2571.678954] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 2571.681263] wlan0: authenticated
[ 2571.682256] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 2571.685046] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 2571.685050] wlan0: associated
[ 2571.685053] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 2576.323209] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[ 2576.328538] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 2579.655252] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 2579.852103] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 2)
[ 2580.051719] wlan0: authenticated
[ 2580.052921] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 2580.057173] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 2580.057177] wlan0: associated
[ 2580.057179] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 2580.560380] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 7)
[ 2580.568597] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 2583.802776] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 2584.000124] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 2)
[ 2584.200034] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 3)
[ 2584.400124] wlan0: authentication with 98:fc:11:a9:0f:06 timed out
[ 2596.748847] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 2596.852260] wlan0: authenticated
[ 2596.853315] wlan0: waiting for beacon from 98:fc:11:a9:0f:06
[ 2596.894167] wlan0: beacon received
[ 2596.916035] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 2596.920164] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 2596.920167] wlan0: associated
[ 2596.920170] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 2608.400109] wlan0: no IPv6 routers present
[ 2644.210204] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 2644.262796] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 2650.159035] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 2650.274440] wlan0: authenticated
[ 2650.275507] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 2650.278316] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 2650.278320] wlan0: associated
[ 2650.278324] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 2661.080106] wlan0: no IPv6 routers present
[ 2696.209090] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 2696.253825] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 2702.176546] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 2702.178890] wlan0: authenticated
[ 2702.179881] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 2702.182623] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 2702.182627] wlan0: associated
[ 2702.182630] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 2712.464085] wlan0: no IPv6 routers present
[ 2748.207876] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 3051.181911] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 3051.184094] wlan0: authenticated
[ 3051.185118] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 3051.187880] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 3051.187884] wlan0: associated
[ 3051.187887] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 3051.191310] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 3064.096087] wlan0: no IPv6 routers present
[ 3099.211514] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 3099.266368] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 3105.248612] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 3105.250812] wlan0: authenticated
[ 3105.251817] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 3105.254551] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 3105.254556] wlan0: associated
[ 3105.254560] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 3108.970823] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[ 3108.976528] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 3112.320976] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 3112.323121] wlan0: authenticated
[ 3112.324124] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 3112.328204] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 3112.328208] wlan0: associated
[ 3112.328211] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 3123.440110] wlan0: no IPv6 routers present
[ 3158.211063] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 3158.269809] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 3164.233450] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 3164.236367] wlan0: authenticated
[ 3164.237379] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 3164.240154] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 3164.240157] wlan0: associated
[ 3164.240160] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 3164.769453] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 3217.005233] wlan0: direct probe to 00:1d:7e:59:ea:1a (try 1/3)
[ 3217.204121] wlan0: direct probe to 00:1d:7e:59:ea:1a (try 2/3)
[ 3217.404047] wlan0: direct probe to 00:1d:7e:59:ea:1a (try 3/3)
[ 3217.604084] wlan0: direct probe to 00:1d:7e:59:ea:1a timed out
[ 3231.240731] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 3231.242862] wlan0: authenticated
[ 3231.243975] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 3231.246963] wlan0: RX AssocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 3231.246968] wlan0: associated
[ 3231.246971] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 3234.284562] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[ 3234.290560] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 3237.565981] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 3237.571070] wlan0: authenticated
[ 3237.572204] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 3237.576618] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 3237.576622] wlan0: associated
[ 3237.576626] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 3240.615232] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[ 3240.630406] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 3243.911685] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 3243.914036] wlan0: authenticated
[ 3243.915463] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 3243.918853] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 3243.918858] wlan0: associated
[ 3243.918861] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 3246.965342] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[ 3246.968725] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 3250.265298] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 3250.267774] wlan0: authenticated
[ 3250.268859] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 3250.271623] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 3250.271627] wlan0: associated
[ 3250.271631] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 3253.313842] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[ 3253.320589] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 3256.643449] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 3256.645621] wlan0: authenticated
[ 3256.646648] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 3256.649394] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 3256.649398] wlan0: associated
[ 3256.649400] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 3259.694016] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[ 3259.707104] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 3263.065298] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 3263.067688] wlan0: authenticated
[ 3263.068712] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 3263.071465] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 3263.071469] wlan0: associated
[ 3263.071472] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 3266.113572] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[ 3266.120568] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 3269.378250] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 3269.380380] wlan0: authenticated
[ 3269.381411] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 3269.384176] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 3269.384179] wlan0: associated
[ 3269.384182] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 3272.425496] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[ 3272.444497] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 3275.710835] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 3275.713190] wlan0: authenticated
[ 3275.715488] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 3275.719493] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 3275.719497] wlan0: associated
[ 3275.719501] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 3278.763890] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[ 3278.780599] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 3282.005369] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 3282.007636] wlan0: authenticated
[ 3282.009677] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 3282.012914] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 3282.012919] wlan0: associated
[ 3282.012922] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 3285.052212] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[ 3285.056732] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 3293.878764] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 3293.881030] wlan0: authenticated
[ 3293.882047] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 3293.884777] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 3293.884781] wlan0: associated
[ 3293.884785] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 3296.931507] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[ 3296.936552] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 3300.224217] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 3300.226513] wlan0: authenticated
[ 3300.227537] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 3300.230288] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 3300.230292] wlan0: associated
[ 3300.230296] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 3303.271351] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[ 3303.276553] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 3306.547292] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 3306.549527] wlan0: authenticated
[ 3306.550524] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 3306.553270] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 3306.553275] wlan0: associated
[ 3306.553277] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 3309.590360] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[ 3309.596550] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 3312.927257] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 3312.929579] wlan0: authenticated
[ 3312.930576] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 3312.933316] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 3312.933321] wlan0: associated
[ 3312.933324] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 3315.980547] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[ 3315.984709] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 3319.300207] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 3319.302547] wlan0: authenticated
[ 3319.303545] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 3319.306275] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 3319.306279] wlan0: associated
[ 3319.306282] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 3322.350620] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[ 3322.356486] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 3325.696640] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 3325.699044] wlan0: authenticated
[ 3325.700052] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 3325.702795] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 3325.702799] wlan0: associated
[ 3325.702802] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 3328.749143] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[ 3328.760423] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 3332.046698] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 3332.048900] wlan0: authenticated
[ 3332.049900] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 3332.052684] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 3332.052687] wlan0: associated
[ 3332.052690] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 3335.099349] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[ 3335.116566] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 3338.406519] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 3338.408680] wlan0: authenticated
[ 3338.409685] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 3338.412438] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 3338.412443] wlan0: associated
[ 3338.412446] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 3341.459955] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[ 3341.468055] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 3344.748991] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 3344.751261] wlan0: authenticated
[ 3344.752272] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 3344.755013] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 3344.755018] wlan0: associated
[ 3344.755021] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 3347.799048] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[ 3347.804574] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 3358.899016] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 3358.901108] wlan0: authenticated
[ 3358.902123] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 3358.904966] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 3358.904971] wlan0: associated
[ 3358.904974] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 3361.952376] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[ 3361.968691] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 3365.258326] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 3365.261364] wlan0: authenticated
[ 3365.262829] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 3365.265564] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 3365.265569] wlan0: associated
[ 3365.265572] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 3368.307450] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[ 3368.320591] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 3371.614655] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 3371.616938] wlan0: authenticated
[ 3371.617934] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 3371.620694] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 3371.620698] wlan0: associated
[ 3371.620701] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 3374.666808] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[ 3374.672727] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 3377.933070] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 3377.935119] wlan0: authenticated
[ 3377.936121] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 3377.938851] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 3377.938855] wlan0: associated
[ 3377.938859] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 3380.976584] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[ 3380.988551] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 3384.173202] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 3384.175406] wlan0: authenticated
[ 3384.176435] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 3384.179226] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 3384.179230] wlan0: associated
[ 3384.179233] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 3387.225490] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[ 3387.236546] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 3390.539793] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 3390.542127] wlan0: authenticated
[ 3390.543133] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 3390.545882] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 3390.545886] wlan0: associated
[ 3390.545889] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 3393.586871] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[ 3393.592565] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 3396.905410] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 3396.907856] wlan0: authenticated
[ 3396.908870] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 3396.911603] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 3396.911607] wlan0: associated
[ 3396.911611] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 3399.956299] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[ 3399.960660] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 3403.216436] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 3403.218706] wlan0: authenticated
[ 3403.219707] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 3403.223620] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 3403.223624] wlan0: associated
[ 3403.223627] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 3410.123033] iwlwifi 0000:02:00.0: Tx aggregation enabled on ra = 98:fc:11:a9:0f:06 tid = 0
[ 3417.056021] wlan0: no IPv6 routers present
[ 3452.211992] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 3458.228555] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 3458.230953] wlan0: authenticated
[ 3458.231949] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 3458.234774] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 3458.234778] wlan0: associated
[ 3458.234781] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 3458.238346] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 3461.272172] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[ 3461.288561] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 3464.577491] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 3464.579786] wlan0: authenticated
[ 3464.580801] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 3464.583555] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 3464.583561] wlan0: associated
[ 3464.583565] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 3467.621598] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[ 3467.627903] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 3470.953313] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 3470.955420] wlan0: authenticated
[ 3470.956434] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 3470.959165] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 3470.959169] wlan0: associated
[ 3470.959172] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 3474.000619] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[ 3474.008554] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 3477.274251] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 3477.276372] wlan0: authenticated
[ 3477.277371] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 3477.280115] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 3477.280120] wlan0: associated
[ 3477.280124] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 3480.321235] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[ 3480.324712] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 3483.601163] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 3483.603507] wlan0: authenticated
[ 3483.605087] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 3483.607808] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 3483.607812] wlan0: associated
[ 3483.607814] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 3486.651147] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[ 3486.656538] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 3489.973355] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 3489.975545] wlan0: authenticated
[ 3489.976564] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 3489.979352] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 3489.979356] wlan0: associated
[ 3489.979359] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 3493.020079] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[ 3493.040519] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 3496.336683] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 3496.339811] wlan0: authenticated
[ 3496.340910] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 3496.343718] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 3496.343722] wlan0: associated
[ 3496.343726] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 3499.390159] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[ 3499.392676] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 3502.715053] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 3502.717328] wlan0: authenticated
[ 3502.719102] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 3502.721850] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 3502.721854] wlan0: associated
[ 3502.721857] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 3505.759306] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[ 3505.768520] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 3509.087365] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 3509.091011] wlan0: authenticated
[ 3509.092249] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 3509.094976] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 3509.094980] wlan0: associated
[ 3509.094983] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 3512.188219] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[ 3512.199005] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3512.199197] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3512.240251] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 3515.471464] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 3515.473728] wlan0: authenticated
[ 3515.474727] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 3515.477466] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 3515.477471] wlan0: associated
[ 3515.477474] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 3515.480834] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 3520.977527] iwlwifi 0000:02:00.0: Tx aggregation enabled on ra = 98:fc:11:a9:0f:06 tid = 0
[ 3525.980084] wlan0: no IPv6 routers present
[ 3557.211195] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 3557.273692] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 3563.195961] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 3563.198381] wlan0: authenticated
[ 3563.199376] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 3563.202255] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 3563.202260] wlan0: associated
[ 3563.202263] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 3577.656034] wlan0: no IPv6 routers present
[ 3613.209542] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 3619.187825] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 3619.190015] wlan0: authenticated
[ 3619.191012] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 3619.193738] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 3619.193742] wlan0: associated
[ 3619.193745] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 3619.197143] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 3631.056143] wlan0: no IPv6 routers present
[ 3658.210869] iwlwifi 0000:02:00.0: Tx aggregation enabled on ra = 98:fc:11:a9:0f:06 tid = 0
[ 3666.209040] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 3666.265942] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 3969.090856] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 3969.092965] wlan0: authenticated
[ 3969.093960] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 3969.096755] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 3969.096760] wlan0: associated
[ 3969.096763] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 3980.200052] wlan0: no IPv6 routers present
[ 4014.209275] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 4020.189669] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 4020.388033] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 2)
[ 4020.579721] wlan0: authenticated
[ 4020.580843] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 4020.584978] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 4020.584982] wlan0: associated
[ 4020.584985] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 4020.591491] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 4020.592341] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 7)
[ 4020.608516] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 4023.775866] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 4023.778295] wlan0: authenticated
[ 4023.779286] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 4023.782024] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 4023.782028] wlan0: associated
[ 4023.782030] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 4034.480085] wlan0: no IPv6 routers present
[ 4069.211317] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 4075.199733] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 4075.201969] wlan0: authenticated
[ 4075.202968] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 4075.205773] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 4075.205777] wlan0: associated
[ 4075.205781] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 4075.209143] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 4088.592028] wlan0: no IPv6 routers present
[ 4123.210612] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 4129.248514] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 4129.250872] wlan0: authenticated
[ 4129.251872] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 4129.254743] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 4129.254747] wlan0: associated
[ 4129.254750] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 4129.258151] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 4141.264030] wlan0: no IPv6 routers present
[ 4176.210103] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 4176.273863] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 4438.827859] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 4438.830072] wlan0: authenticated
[ 4438.831066] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 4438.833804] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 4438.833808] wlan0: associated
[ 4438.833811] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 4442.021467] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[ 4442.024636] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 4445.317333] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 4445.319683] wlan0: authenticated
[ 4445.320743] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 4445.323521] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 4445.323525] wlan0: associated
[ 4445.323528] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 4448.371448] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[ 4448.376517] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 4451.690228] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 4451.692544] wlan0: authenticated
[ 4451.693542] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 4451.696280] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 4451.696285] wlan0: associated
[ 4451.696288] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 4463.008051] wlan0: no IPv6 routers present
[ 4497.208084] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 4497.277836] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 4503.119881] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 4503.122160] wlan0: authenticated
[ 4503.123172] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 4503.127221] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 4503.127225] wlan0: associated
[ 4503.127229] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 4514.116071] wlan0: no IPv6 routers present
[ 4549.207536] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 4549.250325] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 4555.133634] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 4555.135941] wlan0: authenticated
[ 4555.136943] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 4555.139811] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 4555.139815] wlan0: associated
[ 4555.139818] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 4558.368259] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[ 4558.379096] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4558.379271] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4558.404216] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 4561.721062] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 4561.723350] wlan0: authenticated
[ 4561.724424] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 4561.727207] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 4561.727211] wlan0: associated
[ 4561.727214] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 4561.731634] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 4572.080119] wlan0: no IPv6 routers present
[ 4604.210643] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 4610.166106] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 4610.168471] wlan0: authenticated
[ 4610.169535] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 4610.172293] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 4610.172298] wlan0: associated
[ 4610.172301] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 4610.178478] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 4621.584049] wlan0: no IPv6 routers present
[ 4657.211618] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 4657.261911] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 4960.228372] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 4960.230581] wlan0: authenticated
[ 4960.231572] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 4960.234664] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 4960.234668] wlan0: associated
[ 4960.234671] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 4963.423551] wlan0: disassociated from 98:fc:11:a9:0f:06 (Reason: 3)
[ 4963.426018] wlan0: deauthenticating from 98:fc:11:a9:0f:06 by local choice (reason=3)
[ 4966.657879] wlan0: authenticate with 98:fc:11:a9:0f:06 (try 1)
[ 4966.660269] wlan0: authenticated
[ 4966.661321] wlan0: associate with 98:fc:11:a9:0f:06 (try 1)
[ 4966.664086] wlan0: RX ReassocResp from 98:fc:11:a9:0f:06 (capab=0x431 status=0 aid=7)
[ 4966.664093] wlan0: associated
[ 4966.664097] wlan0: invalid AID value 0x7; bits 15:14 not set
[ 4979.304060] wlan0: no IPv6 routers present
[ 4981.873084] martian source 255.255.255.255 from 192.168.1.1, on dev wlan0
[ 4981.876057] martian source 255.255.255.255 from 192.168.1.1, on dev wlan0
[ 4997.010404] iwlwifi 0000:02:00.0: Tx aggregation enabled on ra = 98:fc:11:a9:0f:06 tid = 0
[ 5015.721281] iwlwifi 0000:02:00.0: Tx aggregation enabled on ra = 98:fc:11:a9:0f:06 tid = 0
[ 5074.393621] iwlwifi 0000:02:00.0: Tx aggregation enabled on ra = 98:fc:11:a9:0f:06 tid = 0
[ 5154.445560] iwlwifi 0000:02:00.0: Tx aggregation enabled on ra = 98:fc:11:a9:0f:06 tid = 0
[    0.460120] Switching to clocksource hpet
[    0.581679] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
[    0.582683] ACPI: Lid Switch [LID0]
[   16.921307] Console: switching to colour frame buffer device 160x50
lo        no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"homenet"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 98:FC:11:A9:0F:06  
          Bit Rate=28.9 Mb/s   Tx-Power=15 dBm  
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=47/70  Signal level=-63 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:9418  Invalid misc:133   Missed beacon:0

eth0      no wireless extensions.

grep: /etc/modpbe.d/*: No such file or directory
>  hal.1: read hal dataprocess 7433: arguments to dbus_move_error() were  incorrect, assertion "(dest) == NULL || !dbus_error_is_set ((dest))"  failed in file ../../dbus/dbus-errors.c line 282.
This is normally a bug in some application using the D-Bus library.
libhal.c 3483 : Error unsubscribing to signals, error=The name org.freedesktop.Hal was not provided by any .service files
30: PCI 200.0: 0282 WLAN controller                            
  [Created at pci.318]
  Unique ID: y9sn.GbTjk0YbA70
  Parent ID: z8Q3.yhz5TIKH5m7
  SysFS ID: /devices/pci0000:00/0000:00:1c.0/0000:02:00.0
  SysFS BusID: 0000:02:00.0
  Hardware Class: network
  Model: "Intel PRO/Wireless 5100 AGN [Shiloh] Network Connection"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x4237 "PRO/Wireless 5100 AGN [Shiloh] Network Connection"
  SubVendor: pci 0x8086 "Intel Corporation"
  SubDevice: pci 0x1211
  Driver: "iwlwifi"
  Driver Modules: "iwlwifi"
  Device File: wlan0
  Features: WLAN
  Memory Range: 0xdb600000-0xdb601fff (rw,non-prefetchable)
  IRQ: 49 (189438 events)
  HW Address: 00:16:ea:df:95:d2
  Link detected: yes
  WLAN channels: 1 2 3 4 5 6 7 8 9 10 11 12 13 36 40 44 48 52 56 60 64 100 104 108 112 116 120 124 128 132 136 140
   WLAN frequencies: 2.412 2.417 2.422 2.427 2.432 2.437 2.442 2.447 2.452  2.457 2.462 2.467 2.472 5.18 5.2 5.22 5.24 5.26 5.28 5.3 5.32 5.5 5.52  5.54 5.56 5.58 5.6 5.62 5.64 5.66 5.68 5.7
  WLAN encryption modes: WEP40 WEP104 TKIP CCMP
  WLAN authentication modes: open sharedkey wpa-psk wpa-eap
  Module Alias: "pci:v00008086d00004237sv00008086sd00001211bc02sc80i00"
  Driver Info #0:
    Driver Status: iwlwifi is active
    Driver Activation Cmd: "modprobe iwlwifi"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #14 (PCI bridge)

31: PCI 300.0: 0200 Ethernet controller
  [Created at pci.318]
  Unique ID: rBUF.NCUxv_EAKE0
  Parent ID: qTvu._WsbQRZh8X8
  SysFS ID: /devices/pci0000:00/0000:00:1c.1/0000:03:00.0
  SysFS BusID: 0000:03:00.0
  Hardware Class: network
  Model: "Realtek RTL8101E/RTL8102E PCI Express Fast Ethernet controller"
  Vendor: pci 0x10ec "Realtek Semiconductor Co., Ltd."
  Device: pci 0x8136 "RTL8101E/RTL8102E PCI Express Fast Ethernet controller"
  SubVendor: pci 0x103c "Hewlett-Packard Company"
  SubDevice: pci 0x3602
  Revision: 0x02
  Driver: "r8169"
  Driver Modules: "r8169"
  Device File: eth0
  I/O Ports: 0x6000-0x7fff (rw)
  Memory Range: 0xd1410000-0xd1410fff (ro,non-prefetchable)
  Memory Range: 0xd1400000-0xd140ffff (ro,non-prefetchable)
  Memory Range: 0xd1420000-0xd142ffff (ro,non-prefetchable,disabled)
  IRQ: 47 (no events)
  HW Address: 00:1e:68:e3:0e:c5
  Link detected: no
  Module Alias: "pci:v000010ECd00008136sv0000103Csd00003602bc02sc00i00"
  Driver Info #0:
    Driver Status: r8169 is active
    Driver Activation Cmd: "modprobe r8169"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #15 (PCI bridge)
sudo: /etc/init.d/network: command not found
```

---

### Post by chili555 on 2012-05-07
You may have better luck if your router is set to WPA2 only and not the tricky WPA and WPA2 mixed mode:> Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=46/70  Signal level=-64 dBm 
                    Encryption key:on
                    ESSID:"homenet"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000001c02ff005
                    Extra: Last beacon: 228ms ago
                    <snip>
                    IE: IEEE 802.11i/[COLOR="Red"]WPA2 Version 1[/COLOR]
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: [COLOR="Red"]WPA Version 1[/COLOR]
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    <snip>
                   Also, let's try a driver parameter:```
sudo gedit /etc/modprobe.d/iwlwifi.conf
```Add one single line:```
options iwlwifi 11n_disable=1
```Proofread carefully, save and close gedit. Now does it perform as expected?

---

### Post by M4570D0N on 2012-05-13
> **chili555 said:**
> You may have better luck if your router is set to WPA2 only and not the tricky WPA and WPA2 mixed mode:Also, let's try a driver parameter:```
sudo gedit /etc/modprobe.d/iwlwifi.conf
```Add one single line:```
options iwlwifi 11n_disable=1
```Proofread carefully, save and close gedit. Now does it perform as expected?

Thank you for your prompt reply. I apologize for taking so long to respond. I'm in school and it was final exam week, so I was pretty busy with that (and unfortunately, it also required me to be on my Windows partition for much of the time as well). 

Changing the mixed mode setting did not seem to have any affect. I don't believe this is the issue though as I do not have this issue on my Linux Mint 10 partition. I have a triple boot setup with Mint 10, Win7 and Ubuntu 12.04. Prior to 12.04, I had Mint 12 on that partition, and Ubuntu 11.04 before that and did not have this issue then.

After creating the iwlwifi.conf file it seems to have improved the time it takes to connect somewhat, but it still takes at least 10 minutes. Once it finally connects though, it stays connected and works great. I'm not sure what to make of that.

Oh, one other additional detail about my home network. The notebook does not connect to a wireless router, but rather it connects to the network through a Cisco-Linksys WAP610N Wireless-N Access Point with dual-band.

---

### Post by mamut0o1 on 2012-05-13
You should try to hardcode the IP in the wifi config. see if that helps.
if it connects right away after making that change,it might have been a corrupted DNS setting.

---

### Post by chili555 on 2012-05-13
> The notebook does not connect to a wireless router, but rather it connects to the network through a Cisco-Linksys WAP610N Wireless-N Access Point with dual-band.And where is the DHCP server? In the WAP or in the modem (I assume) behind it or, heaven forbid, *both*?

---

