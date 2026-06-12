---
title: "Ubuntu 11.10 fresh instal wireless not working"
date: 2012-02-11
forum: Networking &amp; Wireless
---

### Post by Zeenomorph on 2012-02-11
The computer had working wireless before the instal, so it's doubtful a hardware issue.
The computer does have a switch for wireless, which is on, but the light is only on periodically.  I can make it flash on when I right click on the taskbar and select "enable wireless".  Other posts seem to think it's a firmware issue, I've followed all the advice I could find.  The computer is a Sony Viao (don't see a model # anywhere).

Here is some output that others have shown and gotten help.  Maybe I'll be one of the lucky too.  I'm stumped.  I'd love to hear your ideas;

> Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-updates/main amd64 Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-updates/restricted amd64 Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-updates/universe amd64 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Translation-en  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted Translation-en
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-updates/multiverse amd64 Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-updates/main i386 Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-updates/restricted i386 Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-updates/universe i386 Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-updates/multiverse i386 Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-updates/main TranslationIndex
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-updates/multiverse TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Translation-en
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-updates/restricted TranslationIndex
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-updates/universe TranslationIndex
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-backports/main Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-backports/restricted Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-backports/universe Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-backports/multiverse Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-backports/main amd64 Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-backports/restricted amd64 Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-backports/universe amd64 Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-backports/multiverse amd64 Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-backports/main i386 Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-backports/restricted i386 Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-backports/universe i386 Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-backports/multiverse i386 Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-backports/main TranslationIndex
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-backports/multiverse TranslationIndex
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-backports/restricted TranslationIndex
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-backports/universe TranslationIndex
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric/main Translation-en_CA
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric/main Translation-en
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric/multiverse Translation-en
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric/restricted Translation-en
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric/universe Translation-en
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-updates/main Translation-en
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-updates/multiverse Translation-en
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-updates/restricted Translation-en
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-updates/universe Translation-en
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-backports/main Translation-en
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-backports/multiverse Translation-en
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-backports/restricted Translation-en
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-backports/universe Translation-en
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en_CA
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
grep is already the newest version.
rfkill is already the newest version.
hwinfo is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
  *-network               
       description: Ethernet interface
       product: AR8151 v2.0 Gigabit Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: c0
       serial: 78:84:3c:9a:76:d2
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI duplex=full firmware=N/A ip=192.168.0.12 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:43 memory:f0200000-f023ffff ioport:2000(size=128)
  *-network DISABLED
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 90:00:4e:d2:6e:af
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.0.0-15-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:18 memory:f0000000-f000ffff
0: sony-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: sony-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
3: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
4: acer-wireless: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

auto lo
iface lo inet loopback

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
00:00.0 Host bridge [0600]: Advanced Micro Devices [AMD] Family 14h Processor Root Complex [1022:1510]
00:01.0 VGA compatible controller [0300]: ATI Technologies Inc AMD Radeon HD 6310 GraphicsATI [1002:9802]
00:01.1 Audio device [0403]: ATI Technologies Inc Wrestler HDMI Audio [Radeon HD 6250/6310] [1002:1314]
00:04.0 PCI bridge [0604]: Advanced Micro Devices [AMD] Family 14h Processor Root Port [1022:1512]
00:05.0 PCI bridge [0604]: Advanced Micro Devices [AMD] Family 14h Processor Root Port [1022:1513]
00:06.0 PCI bridge [0604]: Advanced Micro Devices [AMD] Family 14h Processor Root Port [1022:1514]
00:11.0 SATA controller [0106]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode] [1002:4391] (rev 40)
00:12.0 USB Controller [0c03]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397]
00:12.2 USB Controller [0c03]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396]
00:13.0 USB Controller [0c03]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397]
00:13.2 USB Controller [0c03]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396]
00:14.0 SMBus [0c05]: ATI Technologies Inc SBx00 SMBus Controller [1002:4385] (rev 42)
00:14.2 Audio device [0403]: ATI Technologies Inc SBx00 Azalia (Intel HDA) [1002:4383] (rev 40)
00:14.3 ISA bridge [0601]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 LPC host controller [1002:439d] (rev 40)
00:14.4 PCI bridge [0604]: ATI Technologies Inc SBx00 PCI to PCI Bridge [1002:4384] (rev 40)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 0 [1022:1700] (rev 43)
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 1 [1022:1701]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 2 [1022:1702]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 3 [1022:1703]
00:18.4 Host bridge [0600]: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 4 [1022:1704]
00:18.5 Host bridge [0600]: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 6 [1022:1718]
00:18.6 Host bridge [0600]: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 5 [1022:1716]
00:18.7 Host bridge [0600]: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 7 [1022:1719]
01:00.0 Ethernet controller [0200]: Atheros Communications AR8151 v2.0 Gigabit Ethernet [1969:1083] (rev c0)
02:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5116 PCI Express Card Reader [10ec:5209] (rev 01)
03:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 0c45:64be Microdia 
Bus 004 Device 002: ID 0489:e027 Foxconn / Hon Hai 
H/W path            Device      Class       Description
=======================================================
                                system      VPCEL13FD (N/A)
/0                              bus         VAIO
/0/0                            memory      1MiB BIOS
/0/6                            memory      4GiB System Memory
/0/6/0                          memory      SODIMM [empty]
/0/6/1                          memory      4GiB SODIMM DDR3 1066 MHz (0.9 ns)
/0/b                            processor   AMD E-350 Processor
/0/b/c                          memory      128KiB L1 cache
/0/b/d                          memory      1MiB L2 cache
/0/100                          bridge      Family 14h Processor Root Complex
/0/100/1                        display     AMD Radeon HD 6310 GraphicsATI
/0/100/1.1                      multimedia  Wrestler HDMI Audio [Radeon HD 6250/
/0/100/4                        bridge      Family 14h Processor Root Port
/0/100/4/0          eth0        network     AR8151 v2.0 Gigabit Ethernet
/0/100/5                        bridge      Family 14h Processor Root Port
/0/100/5/0          scsi2       generic     RTS5116 PCI Express Card Reader
/0/100/5/0/0.0.0    /dev/sdb    disk        SCSI Disk
/0/100/5/0/0.0.1    /dev/sdc    disk        MemoryStick
/0/100/5/0/0.0.1/0  /dev/sdc    disk        
/0/100/6                        bridge      Family 14h Processor Root Port
/0/100/6/0          wlan0       network     AR9285 Wireless Network Adapter (PCI
/0/100/11           scsi0       storage     SB7x0/SB8x0/SB9x0 SATA Controller [A
/0/100/11/0         /dev/sda    disk        500GB TOSHIBA MK5059GS
/0/100/11/0/1       /dev/sda1   volume      100MiB Windows NTFS volume
/0/100/11/0/2       /dev/sda2   volume      93GiB Windows NTFS volume
/0/100/11/0/3       /dev/sda3   volume      372GiB Extended partition
/0/100/11/0/3/5     /dev/sda5   volume      369GiB Linux filesystem partition
/0/100/11/0/3/6     /dev/sda6   volume      3689MiB Linux swap / Solaris partiti
/0/100/11/1         /dev/cdrom  disk        DVDRAM GT30N
/0/100/12                       bus         SB7x0/SB8x0/SB9x0 USB OHCI0 Controll
/0/100/12.2                     bus         SB7x0/SB8x0/SB9x0 USB EHCI Controlle
/0/100/13                       bus         SB7x0/SB8x0/SB9x0 USB OHCI0 Controll
/0/100/13.2                     bus         SB7x0/SB8x0/SB9x0 USB EHCI Controlle
/0/100/14                       bus         SBx00 SMBus Controller
/0/100/14.2                     multimedia  SBx00 Azalia (Intel HDA)
/0/100/14.3                     bridge      SB7x0/SB8x0/SB9x0 LPC host controlle
/0/100/14.4                     bridge      SBx00 PCI to PCI Bridge
/0/101                          bridge      Family 12h/14h Processor Function 0
/0/102                          bridge      Family 12h/14h Processor Function 1
/0/103                          bridge      Family 12h/14h Processor Function 2
/0/104                          bridge      Family 12h/14h Processor Function 3
/0/105                          bridge      Family 12h/14h Processor Function 4
/0/106                          bridge      Family 12h/14h Processor Function 6
/0/107                          bridge      Family 12h/14h Processor Function 5
/0/108                          bridge      Family 12h/14h Processor Function 7
Linux steve-laptop 3.0.0-15-generic #26-Ubuntu SMP Fri Jan 20 17:23:00 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
[    0.000000] No AGP bridge found
[    0.000000] found SMP MP-table at [ffff8800000fe1b0] fe1b0
[    0.000000] No NUMA configuration found
[    0.000000] No AGP bridge found
[    0.203764] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.233207] ACPI: No dock devices found.
[    0.233211] HEST: Table not found.
[    0.281034] usbcore: registered new interface driver usbfs
[    0.281054] usbcore: registered new interface driver hub
[    0.281111] usbcore: registered new device driver usb
[    0.286397] Switching to clocksource hpet
[    0.286946] Switched to NOHz mode on CPU #0
[    0.286816] Switched to NOHz mode on CPU #1
[    0.298450] pnp: PnP ACPI: found 11 devices
[    0.496650] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
[    0.496700] ACPI: Lid Switch [LID0]
[    0.504842] ERST: Table is not found!
[    0.725326] ehci_hcd 0000:00:12.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    0.736540] hub 1-0:1.0: USB hub found
[    0.736826] ehci_hcd 0000:00:13.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    0.748550] hub 2-0:1.0: USB hub found
[    0.808495] hub 3-0:1.0: USB hub found
[    0.868495] hub 4-0:1.0: USB hub found
[    0.918869] powernow-k8: Found 1 AMD E-350 Processor (2 cpu cores) (version 2.20.00)
[    0.919722] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.176142] usb 2-3: new high speed USB device number 3 using ehci_hcd
[    1.416284] Switching to clocksource tsc
[    1.604253] usb 4-2: new full speed USB device number 2 using ohci_hcd
[   12.491768] lp: driver loaded but no devices found
[   13.412342] atl1c 0000:01:00.0: atl1c: eth0 NIC Link is Up<1000 Mbps Full Duplex>
[   13.456910] usbcore: registered new interface driver btusb
[   13.458353] ath9k 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   13.458370] ath9k 0000:03:00.0: setting latency timer to 64
[   13.532145] ath: EEPROM regdomain: 0x65
[   13.532153] ath: EEPROM indicates we should expect a direct regpair map
[   13.532161] ath: Country alpha2 being used: 00
[   13.532164] ath: Regpair used: 0x65
[   13.569622] input: HD-Audio Generic HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.1/sound/card0/input9
[   13.618456] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[   13.622548] Registered led device: ath9k-phy0
[   13.629495] type=1400 audit(1328941016.206:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=735 comm="apparmor_parser"
[   13.636652] type=1400 audit(1328941016.214:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/telepathy-*" pid=735 comm="apparmor_parser"
[   13.654623] hda_codec: CX20590: BIOS auto-probing.
[   13.701454] uvcvideo: Found UVC 1.00 device Sony Visual Communication Camera (0c45:64be)
[   13.722079] input: Sony Visual Communication Camer as /devices/pci0000:00/0000:00:13.2/usb2/2-3/2-3:1.0/input/input10
[   13.722273] usbcore: registered new interface driver uvcvideo
[   14.865405] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   15.160684] Console: switching to colour frame buffer device 170x48
[   16.030347] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   24.368087] eth0: no IPv6 routers present
[   73.938274] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   82.766135] atl1c 0000:01:00.0: atl1c: eth0 NIC Link is Down
[   85.307022] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   85.479861] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   88.460308] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   88.755059] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  101.121232] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  134.185785] type=1400 audit(1328941137.276:23): apparmor="STATUS" operation="profile_replace" name="/usr/lib/telepathy/mission-control-5" pid=2060 comm="apparmor_parser"
[  134.186659] type=1400 audit(1328941137.276:24): apparmor="STATUS" operation="profile_replace" name="/usr/lib/telepathy/telepathy-*" pid=2060 comm="apparmor_parser"
[  141.068792] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  178.600906] atl1c 0000:01:00.0: atl1c: eth0 NIC Link is Up<1000 Mbps Full Duplex>
[  178.602520] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  188.632210] eth0: no IPv6 routers present
[  575.892787] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  840.719234] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  850.192283] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  918.258764] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  935.288954] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1482.541263] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1506.180950] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1897.504677] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1904.365370] atl1c 0000:01:00.0: atl1c: eth0 NIC Link is Down
[ 1906.286889] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 1906.460421] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1908.460592] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1908.767108] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 1921.118329] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1923.678638] atl1c 0000:01:00.0: atl1c: eth0 NIC Link is Up<1000 Mbps Full Duplex>
[ 1923.680322] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 1934.136111] eth0: no IPv6 routers present
[ 2255.593768] atl1c 0000:01:00.0: atl1c: eth0 NIC Link is Down
[ 2256.283374] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 2258.676625] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2258.999140] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 2278.894424] atl1c 0000:01:00.0: atl1c: eth0 NIC Link is Up<1000 Mbps Full Duplex>
[ 2278.896093] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 2289.824209] eth0: no IPv6 routers present
	Release Date: 03/23/2011
	Manufacturer: Sony Corporation
	Product Name: VPCEL13FD
	Serial Number: 27545348-3003232
	Manufacturer: Sony Corporation
	Product Name: VAIO
	Serial Number: N/A
	Manufacturer: Sony Corporation
	Serial Number: N/A
	Manufacturer: Not Specified
	Serial Number: Not Specified
	Manufacturer: Kinston
	Serial Number: 6505210A
	Manufacturer: AMD processor
	Serial Number: N/A
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# which ath5k cannot recover. To prevent this condition, stop
blacklist ath_pci
blacklist eth1394
# replaced by p54pci
blacklist prism54
# replaced by b43 and ssb.
blacklist bcm43xx
blacklist uart6850
blacklist twl4030_wdt

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true
> hal.1: read hal dataprocess 5360: arguments to dbus_move_error() were incorrect, assertion "(dest) == NULL || !dbus_error_is_set ((dest))" failed in file ../../dbus/dbus-errors.c line 280.
This is normally a bug in some application using the D-Bus library.
libhal.c 3483 : Error unsubscribing to signals, error=The name org.freedesktop.Hal was not provided by any .service files
31: PCI 100.0: 0200 Ethernet controller                         
  [Created at pci.318]
  Unique ID: rBUF.TzHem5H4iyD
  Parent ID: 8otl.9+ZqoLdEnI9
  SysFS ID: /devices/pci0000:00/0000:00:04.0/0000:01:00.0
  SysFS BusID: 0000:01:00.0
  Hardware Class: network
  Model: "Attansic Ethernet controller"
  Vendor: pci 0x1969 "Attansic Technology Corp."
  Device: pci 0x1083 
  SubVendor: pci 0x104d "Sony Corporation"
  SubDevice: pci 0x908d 
  Revision: 0xc0
  Driver: "atl1c"
  Driver Modules: "atl1c"
  Device File: eth0
  Memory Range: 0xf0200000-0xf023ffff (rw,non-prefetchable)
  I/O Ports: 0x2000-0x2fff (rw)
  IRQ: 43 (1130 events)
  HW Address: 78:84:3c:9a:76:d2
  Link detected: yes
  Module Alias: "pci:v00001969d00001083sv0000104Dsd0000908Dbc02sc00i00"
  Driver Info #0:
    Driver Status: atl1c is active
    Driver Activation Cmd: "modprobe atl1c"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #11 (PCI bridge)

33: PCI 300.0: 0282 WLAN controller
  [Created at pci.318]
  Unique ID: y9sn.eVj0IaBAaq2
  Parent ID: H0_h.BqSKmUseq3A
  SysFS ID: /devices/pci0000:00/0000:00:06.0/0000:03:00.0
  SysFS BusID: 0000:03:00.0
  Hardware Class: network
  Model: "Atheros WLAN controller"
  Vendor: pci 0x168c "Atheros Communications Inc."
  Device: pci 0x002b 
  SubVendor: pci 0x105b "Foxconn International, Inc."
  SubDevice: pci 0xe037 
  Revision: 0x01
  Driver: "ath9k"
  Driver Modules: "ath9k", "ath9k"
  Device File: wlan0
  Features: WLAN
  Memory Range: 0xf0000000-0xf000ffff (rw,non-prefetchable)
  IRQ: 18 (21392 events)
  HW Address: 90:00:4e:d2:6e:af
  Link detected: no
  WLAN channels: 1 2 3 4 5 6 7 8 9 10 11 12 13
  WLAN frequencies: 2.412 2.417 2.422 2.427 2.432 2.437 2.442 2.447 2.452 2.457 2.462 2.467 2.472
  WLAN encryption modes: WEP40 WEP104 TKIP CCMP
  WLAN authentication modes: open sharedkey wpa-psk wpa-eap
  Module Alias: "pci:v0000168Cd0000002Bsv0000105Bsd0000E037bc02sc80i00"
  Driver Info #0:
    Driver Status: ath9k is active
    Driver Activation Cmd: "modprobe ath9k"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #13 (PCI bridge)
Warning: bad ps syntax, perhaps a bogus '-'? See [http://procps.sf.net/faq.html](http://procps.sf.net/faq.html)
root       549  0.0  0.1 170820  5296 ?        Ssl  22:16   0:01 NetworkManager
root       944  0.9  0.3  96508 12088 ?        S    22:16   0:25 /usr/bin/python -O /usr/share/wicd/daemon/wicd-daemon.py
root      1025  0.1  0.2  85504 10624 ?        S    22:16   0:02 /usr/bin/python -O /usr/share/wicd/daemon/monitor.py
root      1190  0.0  0.0  30944  2496 ?        S    22:16   0:00 /sbin/wpa_supplicant -u -s -O /var/run/wpa_supplicant
steve     1665  0.0  0.6 240168 25408 ?        Sl   22:17   0:01 /usr/bin/python -O /usr/share/wicd/gtk/wicd-client.py
root      5091  0.0  0.0   7128  1532 ?        S    22:54   0:00 /sbin/dhclient -d -4 -sf /usr/lib/NetworkManager/nm-dhcp-client.action -pf /var/run/dhclient-eth0.pid -lf /var/lib/dhcp/dhclient-63121b87-4282-4c38-bde3-f6a209a1ae83-eth0.lease -cf /var/run/nm-dhclient-eth0.conf eth0
steve     5376  0.0  0.0  13448   880 pts/0    S+   22:58   0:00 egrep --color=auto wpa|icd|etwork
Module                  Size  Used by
parport_pc             36962  0 
ppdev                  17113  0 
vesafb                 13809  1 
joydev                 17693  0 
bnep                   18436  2 
rfcomm                 47946  0 
acer_wmi               23948  0 
sparse_keymap          13890  1 acer_wmi
uvcvideo               72711  0 
videodev               92992  1 uvcvideo
v4l2_compat_ioctl32    17083  1 videodev
snd_hda_codec_conexant    62197  1 
arc4                   12529  2 
snd_hda_codec_hdmi     32040  1 
psmouse                73882  0 
serio_raw              13166  0 
ath9k                 127538  0 
btusb                  18600  1 
snd_hda_intel          33390  2 
snd_hda_codec         104931  3 snd_hda_codec_conexant,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
mac80211              462092  1 ath9k
sp5100_tco             13791  0 
bluetooth             166112  13 bnep,rfcomm,btusb
snd_pcm                96714  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
i2c_piix4              13301  0 
k10temp                13166  0 
ath9k_common           13839  1 ath9k
ath9k_hw              312914  2 ath9k,ath9k_common
ath                    24067  2 ath9k,ath9k_hw
snd_seq_midi           13324  0 
cfg80211              199630  3 ath9k,mac80211,ath
rts_pstor             445246  0 
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
binfmt_misc            17540  1 
sony_laptop            45393  0 
snd                    68266  14 snd_hda_codec_conexant,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
fglrx                2928969  106 
wmi                    19256  1 acer_wmi
video                  19412  0 
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
ahci                   26002  2 
libahci                26861  1 ahci
atl1c                  41643  0 
steve@steve-laptop:~$ 

---

### Post by praseodym on 2012-02-11
Hi,

the module acer_wmi is wrong on a Sony Vaio:

```
echo "blacklist acer_wmi" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
You also should deactivate the hardware encryption of the driver ath9k (bug in 11.10):

```
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
```
Reboot needed after that

---

