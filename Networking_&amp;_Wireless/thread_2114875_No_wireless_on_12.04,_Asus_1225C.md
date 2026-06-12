---
title: "No wireless on 12.04, Asus 1225C"
date: 2013-02-11
forum: Networking &amp; Wireless
---

### Post by damianoloan on 2013-02-11
I've been having problems connecting via wifi for a few days now.  I've uninstalled and reinstalled the Broadcom STA drivers and network manager, followed the instructions [here]("http://ubuntuforums.org/askubuntu.com/questions/38327/how-can-i-get-broadcom-bcm4311-wireless-working"), had limited success with wicd despite it not , but still no solution.
Here is the lengthy output of the command given in the Wireless Troubleshooting Procedure:
sudo apt-get update; sudo apt-get install hwinfo grep rfkill; sudo lshw  -C network; rfkill list; sudo iwlist scan | egrep -i 'chan|ssid'; cat  /etc/network/interfaces; cat /etc/lsb-release; lspci -nnk | grep  -iA2 net; lsusb; nmcli nm status; sudo lshw -short; uname -a; dmesg |  egrep '02:00|80211|acx|at76|ath|b43|bcm|brcm|CX|eth|ipw|ireless|irmware|isl|lbtf|orinoco|ndiswrapper|NPE|ound|p54|prism|rror|rtl|rt2|rt3|rt5|rt6|rt7|usb|witch|wl';sudo dmidecode|egrep 'anufact|roduct|erial|elease'; iwconfig; cat /etc/modprobe.d/* | egrep '80211|acx|at76|ath|b43|bcm|brcm|CX|eth|ipw|irmware|isl|lbtf|orinoco|ndiswrapper|NPE|p54|prism|rtl|rt2|rt3|rt6|rt7|wmi|witch|wl'; cat /var/lib/NetworkManager/NetworkManager.state; sudo hwinfo --netcard ; ps -aux|egrep 'wpa|icd|etwork'; netstat -rn ; cat /etc/resolv.conf; sudo lsmod
Ign [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) precise InRelease
Ign [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) precise-updates InRelease
Ign [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) precise-backports InRelease
Hit [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) precise Release.gpg
Hit [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) precise-updates Release.gpg
Hit [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) precise-backports Release.gpg
Hit [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) precise Release
Hit [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) precise-updates Release
Hit [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) precise-backports Release
Hit [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) precise/main Sources
Hit [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) precise/restricted Sources
Hit [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) precise/universe Sources
Hit [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) precise/multiverse Sources
Hit [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) precise/main i386 Packages
Hit [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) precise/restricted i386 Packages
Hit [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) precise/universe i386 Packages
Hit [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) precise/multiverse i386 Packages
Hit [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) precise/main TranslationIndex
Hit [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) precise/multiverse TranslationIndex
Hit [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) precise/restricted TranslationIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security InRelease
Hit [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) precise/universe TranslationIndex
Hit [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) precise-updates/main Sources
Hit [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) precise-updates/restricted Sources
Hit [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) precise-updates/universe Sources
Hit [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) precise-updates/multiverse Sources
Hit [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) precise-updates/main i386 Packages
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise InRelease
Hit [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) precise-
updates/restricted i386 Packages
Hit [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) precise-updates/universe i386 Packages
Hit [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) precise-updates/multiverse i386 Packages
Hit [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) precise-updates/main TranslationIndex
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease
Hit [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) precise-updates/multiverse TranslationIndex
Hit [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) precise-updates/restricted TranslationIndex
Hit [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) precise-updates/universe TranslationIndex
Hit [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) precise-backports/main Sources
Hit [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) precise-backports/restricted Sources
Hit [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) precise-backports/universe Sources
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease
Hit [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) precise-backports/multiverse Sources
Hit [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) precise-backports/main i386 Packages
Hit [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) precise-backports/restricted i386 Packages
Hit [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) precise-backports/universe i386 Packages
Hit [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) precise-backports/multiverse i386 Packages
Hit [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) precise-backports/main TranslationIndex
Hit [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) precise-backports/multiverse TranslationIndex
Hit [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) precise-backports/restricted TranslationIndex
Hit [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) precise-backports/universe TranslationIndex
Hit [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) precise/main Translation-en
Hit [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) precise/multiverse Translation-en
Hit [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) precise/restricted Translation-en
Hit [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) precise/universe Translation-en
Hit [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) precise-updates/main Translation-en
Hit [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) precise-updates/multiverse Translation-en
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg [198 B]
Hit [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) precise-updates/restricted Translation-en
Hit [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) precise-updates/universe Translation-en
Hit [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) precise-backports/main Translation-en
Hit [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) precise-backports/multiverse Translation-en
Hit [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) precise-backports/restricted Translation-en
Hit [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) precise-
backports/universe Translation-en
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release [49.6 kB]
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources [63.1 kB]
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources [1,950 B]
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources [20.6 kB]
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources [1,379 B]
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages [233 kB]
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages [3,968 B]
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages [66.9 kB]
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages [2,366 B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_US
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Fetched 443 kB in 6s (65.2 kB/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree
Reading state information... Done
grep is already the newest version.
rfkill is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-
headers-3.2.0-32 linux-headers-3.2.0-29
  linux-headers-3.2.0-29-generic-pae linux-headers-3.2.0-32-generic-pae
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libhd16
The following NEW packages will be installed:
  hwinfo libhd16
0 upgraded, 2 newly installed, 0 to remove and 6 not upgraded.
Need to get 699 kB of archives.
After this operation, 2,054 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://cn.archive.ubuntu.com/ubuntu/](http://cn.archive.ubuntu.com/ubuntu/) precise/universe libhd16 i386 16.0-2.1 [681 kB]
Get:2 [http://cn.archive.ubuntu.com/ubuntu/](http://cn.archive.ubuntu.com/ubuntu/) precise/universe hwinfo i386 16.0-2.1 [18.2 kB]
Fetched 699 kB in 2s (260 kB/s)
Selecting previously unselected package libhd16.
(Reading database ... 344581 files and directories currently installed.)
Unpacking libhd16 (from .../libhd16_16.0-2.1_i386.deb) ...
Selecting previously unselected package hwinfo.
Unpacking hwinfo (from .../hwinfo_16.0-2.1_i386.deb) ...
Processing triggers for man-db ...
Setting up libhd16 (16.0-2.1) ...
Setting up hwinfo (16.0-2.1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 05
       serial: 10:bf:48:1d:6d:93
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       
capabilities: pm msi pciexpress msix vpd bus_master cap_list  ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8105e-1.fw ip=192.168.1.141 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:50 ioport:e000(size=256) memory:dfe04000-dfe04fff memory:dfe00000-dfe03fff
0: asus-wlan: Wireless LAN
 Soft blocked: no
 Hard blocked: no
1: asus-bluetooth: Bluetooth
 Soft blocked: yes
 Hard blocked: no
2: asus-wimax: WiMAX
 Soft blocked: no
 Hard blocked: no
lo        Interface doesn't support scanning.
eth0      Interface doesn't support scanning.
 auto lo
iface lo inet loopback
 DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.2 LTS"
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd.  RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev  05)
 Subsystem: ASUSTeK Computer Inc. Device [1043:100b]
 Kernel driver in use: r8169
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 1221:3234
Bus 001 Device 003: ID 13d3:5711 IMC Networks
RUNNING         STATE           WIFI-HARDWARE   WIFI       WWAN-HARDWARE   WWAN
running         connected       enabled         enabled    enabled         disabled
H/W path               Device     Class       Description
=========================================================
                                  system      1225C (1225C)
/0                                bus         1225C
/0/0                              memory      64KiB BIOS
/0/4                              processor   Intel(R) Atom(TM) CPU N2800   @ 1.
/0/4/5                            memory      24KiB L1 cache
/0/4/6                            memory      512KiB L2 cache
/0/4/2.1                          processor   Logical CPU
/0/4/2.2                          processor   Logical CPU
/0/4/2.3                          processor   Logical CPU
/0/4/2.4                          processor   Logical CPU
/0/28                             memory      2GiB System Memory
/0/28/0                           memory      SODIMM [empty]
/0/28/1                           memory      2GiB SODIMM DDR3 Synchronous 1066
/0/1                              processor
/0/1/2.1                          processor   Logical CPU
/0/1/2.2                          processor   Logical CPU
/0/1/2.3                          processor   Logical CPU
/0/1/2.4                          processor   Logical CPU
/0/100                            bridge      Atom Processor D2xxx/N2xxx DRAM Co
/0/100/2                          display     Atom Processor D2xxx/N2xxx Integra
/0/100/1b                         multimedia  N10/ICH 7 Family High Definition A
/0/100/1c                         bridge      N10/ICH 7 Family PCI Express Port
/0/100/1c.1                       bridge      N10/ICH 7 Family PCI Express Port
/0/100/1c.2                       bridge      N10/ICH 7 Family PCI Express Port
/0/100/1c.2/0          eth0       network     RTL8101E/RTL8102E PCI Express Fast
/0/100/1c.3                       bridge      N10/ICH 7 Family PCI Express Port
/0/100/1c.3/0                     bus         ASM1042 SuperSpeed USB Host Contro
/0/100/1d                         bus         N10/ICH 7 Family USB UHCI Controll
/0/100/1d.1                       bus         N10/ICH 7 Family USB UHCI Controll
/0/100/1d.2                       bus         N10/ICH 7 Family USB UHCI Controll
/0/100/1d.3                       bus         N10/ICH 7 Family USB UHCI Controll
/0/100/1d.7                       bus         N10/ICH 7 Family USB2 EHCI Control
/0/100/1e                         bridge      82801 Mobile PCI Bridge
/0/100/1f                         bridge      NM10 Family LPC Controller
/0/100/1f.2            scsi0      storage     N10/ICH7 Family SATA Controller [A
/0/100/1f.2/0.0.0      /dev/sda   disk        500GB ST9500325AS
/0/100/1f.2/0.0.0/1    /dev/sda1  volume      424GiB EXT4 volume
/0/100/1f.2/0.0.0/2    /dev/sda2  volume      41GiB Extended partition
/0/100/
1f.2/0.0.0/2/5  /dev/sda5  volume      2033MiB Linux swap / Solaris parti
/0/100/1f.2/0.0.0/2/6  /dev/sda6  volume      39GiB Linux filesystem partition
/0/100/1f.3                       bus         N10/ICH 7 Family SMBus Controller
/0/2                   scsi4      storage
/0/2/0.0.0             /dev/sdb   disk        17GB SCSI Disk
Linux damian-1225C 3.2.0-37-
generic-pae #58-Ubuntu SMP Thu Jan 24 15:51:02 UTC 2013 i686 i686 i386 GNU/Linux
[    0.000000] found SMP MP-table at [c00fccf0] fccf0
[    0.589491] ACPI: EC: EC description table is found, configuring boot EC
[    0.603661] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.799438] ACPI: No dock devices found.
[    0.799446] HEST: Table not found.
[    0.803854] pci 0000:00:1f.0: [Firmware Bug]: TigerPoint LPC.BM_STS cleared
[    0.838332] i2c-core: driver [aat2870] using legacy suspend method
[    0.838339] i2c-core: driver [aat2870] using legacy resume method
[    0.838931] usbcore: registered new interface driver usbfs
[    0.838974] usbcore: registered new interface driver hub
[    0.839091] usbcore: registered new device driver usb
[    0.857361] Switching to clocksource hpet
[    0.885518] pnp: PnP ACPI: found 17 devices
[    1.058024] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    1.061522] ACPI: Lid Switch [LID]
[    1.073581] ERST: Table is not found!
[    1.427919] isapnp: No Plug & Play device found
[    1.443434] ehci_hcd 0000:00:1d.7: using broken periodic workaround
[    1.461118] hub 1-0:1.0: USB hub found
[    1.461858] hub 2-0:1.0: USB hub found
[    1.462487] hub 3-0:1.0: USB hub found
[    1.463118] hub 4-0:1.0: USB hub found
[    1.463736] hub 5-0:1.0: USB hub found
[    1.525828] hub 6-0:1.0: USB hub found
[    1.526349] hub 7-0:1.0: USB hub found
[    1.560834] usbcore: registered new interface driver libusual
[    1.588342] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.772380] usb 1-1: new high-speed USB device number 2 using ehci_hcd
[    1.910267] scsi4 : usb-storage 1-1:1.0
[    1.910417] usbcore: registered new interface driver usb-storage
[    1.928120] Switching to clocksource tsc
[    2.015965] usb 1-6: new high-speed USB device number 3 using ehci_hcd
[    2.249510] r8169 0000:03:00.0: eth0: RTL8105e at 0xf8416000, 10:bf:48:1d:6d:93, XID 00a00000 IRQ 50
[   19.393002] ADDRCONF(
NETDEV_UP): eth0: link is not ready
[   19.498989] lp: driver loaded but no devices found
[   19.682875] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   20.059919] uvcvideo: Found UVC 1.00 device USB 2.0 UVC VGA WebCam (13d3:5711)
[   20.081623] input: USB 2.0 UVC VGA WebCam as /devices/pci0000:00/0000:00:1d.7/usb1/1-6/1-6:1.0/input/input5
[   20.081932] usbcore: registered new interface driver uvcvideo
[   20.714727] psmouse serio2: elantech: assuming hardware version 3 (with firmware version 0x450f00)
[   20.934679] Console: switching to colour frame buffer device 170x48
[   20.949750] Cedartrail: apply sample cache workaround
[   21.037306] input: HDA Intel HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   21.038400] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   21.039258] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   22.156740] r8169 0000:03:00.0: eth0: link down
[   22.156751] r8169 0000:03:00.0: eth0: link down
[   22.157245] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   22.170816] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   23.824364] r8169 0000:03:00.0: eth0: link up
[   23.824769] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   34.195807] eth0: no IPv6 routers present
[   50.796652] type=1400 audit(1360280593.774:29): apparmor="DENIED" operation="open" parent=2064 profile="/usr/lib/telepathy/mission-control-5" name="/etc/ld.so.preload" pid=2065 comm="mission-control" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
 Release Date: 04/26/2012
  Serial services are supported (int 14h)
 Manufacturer: ASUSTeK Computer Inc.
 Product Name: 1225C
 Serial Number: C5OAAS136969
 Manufacturer: ASUSTeK Computer Inc.
 Product Name: 1225C
 Serial Number: BSN123456789012
34567
 Manufacturer: ASUSTeK Computer Inc.
 Serial Number: CSN12345678901234567
 Manufacturer: Intel
 Serial Number: To Be Filled By O.E.M.
 Port Type: Serial Port 16550A Compatible
 Manufacturer: [Empty]
 Serial Number: [Empty]
 Manufacturer: 17
 Serial Number: 00000000
lo        no wireless extensions.
 eth0      no wireless extensions.
 install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi  $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist  snd-seq-midi ; : ; }
# which ath5k cannot recover. To prevent this condition, stop
blacklist ath_pci
# Warning: This file is autogenerated by bcmwl. All changes to this file will be lost.
blacklist b43
blacklist b43legacy
blacklist bcm43xx
blacklist brcm80211
blacklist brcmfmac
blacklist brcmsmac
blacklist bcma
blacklist eth1394
# replaced by p54pci
blacklist prism54
# replaced by b43 and ssb.
# blacklist bcm43xx
blacklist eth1394
# replaced by p54pci
blacklist prism54
# replaced by b43 and ssb.
blacklist bcm43xx
blacklist uart6850
blacklist twl4030_wdt [main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true
24: PCI 300.0: 0200 Ethernet controller
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_10ec_8136
  Unique ID: rBUF.KHPPRQ3oGJ3
  Parent ID: hoOk.t12b8gC8Ad0
  SysFS ID: /devices/pci0000:00/0000:00:1c.2/0000:03:00.0
  SysFS BusID: 0000:03:00.0
  Hardware Class: network
  Model: "Realtek RTL8101E/RTL8102E PCI Express Fast Ethernet controller"
  Vendor: pci 0x10ec "Realtek Semiconductor Co., Ltd."
  Device: pci 0x8136 "RTL8101E/RTL8102E PCI Express Fast Ethernet controller"
  SubVendor: pci 0x1043 "ASUSTeK Computer Inc."
  SubDevice: pci 0x100b
  Revision: 0x05
  Driver: "r8169"
  Driver Modules: "r8169"
  Device File: eth0
  I/O Ports: 0xe000-0xefff (rw)
  Memory Range: 0xdfe04000-0xdfe04fff (ro,non-prefetchable)
  Memory Range: 0xdfe00000-0xdfe03fff (ro,non-prefetchable)
  IRQ: 50 (26956 events)
  HW Address: 10:bf:48:1d:6d:93
Link detected: yes
  Module Alias: "pci:v000010ECd
00008136sv00001043sd0000100Bbc02sc00i00"
  Driver Info #0:
    Driver Status: r8169 is active
    Driver Activation Cmd: "modprobe r8169"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #13 (PCI bridge)
Warning: bad ps syntax, perhaps a bogus '-'? See [http://procps.sf.net/faq.html](http://procps.sf.net/faq.html)
root       847  0.0  0.2  31184  5036 ?        Ssl  07:42   0:00 NetworkManager
root      1262  0.0  0.0   2928  1332 ?        S    07:42   0:00 /sbin/dhclient -d -4 -sf /usr/lib/NetworkManager/nm-dhcp-client.action -pf /var/run/sendsigs.omit.d/network-manager.dhclient-eth0.pid -lf /var/lib/dhcp/dhclient-dc7b359c-0155-421d-9ede-18293f02a663-eth0.lease -cf /var/run/nm-dhclient-eth0.conf eth0
nobody    1366  0.0  0.0   5460  1224 ?        S    07:42   0:00 /usr/sbin/dnsmasq --no-resolv --keep-in-foreground --no-hosts --bind-interfaces --pid-file=/var/run/sendsigs.omit.d/network-manager.dnsmasq.pid --listen-address=127.0.0.1 --conf-file=/var/run/nm-dns-dnsmasq.conf --cache-size=0 --proxy-dnssec
damian    2695  0.0  0.0   4424   852 pts/0    S+   07:53   0:00 egrep --color=auto wpa|icd|etwork
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG        0 0          0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.0.1
Module                  Size  Used by
nls_utf8               12493  1
isofs                  39553  1
snd_hda_codec_hdmi     31775  1
snd_hda_codec_realtek   174313  1
joydev                 17393  0
eeepc_wmi              12949  0
asus_wmi               19624  1 eeepc_wmi
sparse_keymap          13658  1 asus_wmi
bnep                   17830  2
rfcomm                 38139  0
parport_pc             32114  0
bluetooth             158479  10 bnep,rfcomm
ppdev                  12849  0
snd_hda_intel          32765  5
snd_hda_codec         109562  3 snd_hda_
codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80916  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
binfmt_misc            17292  1
uvcvideo               67203  0
videodev               86588  1 uvcvideo
snd_seq_midi           13132  0
psmouse                86520  0
serio_raw              13027  0
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
cedarview_gfx         381372  4
snd                    62218  19 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ttm                    64734  1 cedarview_gfx
drm_kms_helper         32561  1 cedarview_gfx
drm                   196391  6 cedarview_gfx,ttm,drm_kms_helper
wmi                    18744  1 asus_wmi
i2c_algo_bit           13199  1 cedarview_gfx
video                  19068  1 cedarview_gfx
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
mac_hid                13077  0
lp                     17455  0
parport                40930  3 parport_pc,ppdev,lp
r8169                  56368  0
usb_storage            39646  1

---

### Post by damianoloan on 2013-02-11
Is there any further information I can provide that would help?  I haven't had a response here, on askubuntu or on launchpad - are there other places I'm likely to find a solution?

---

### Post by ahallubuntu on 2013-02-11
~

---

### Post by damianoloan on 2013-02-11
The output of ```
sudo lshw -C network
``` was:
```
*-network               
       description: Wireless interface
       product: BCM4313 802.11b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth1
       version: 01
       serial: e0:b9:a5:f7:9b:b2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=6.20.155.1 (r326264) ip=192.168.1.43 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:17 memory:dfe00000-dfe03fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 05
       serial: 10:bf:48:1d:6d:93
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8105e-1.fw ip=192.168.1.141 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:50 ioport:e000(size=256) memory:dfd04000-dfd04fff memory:dfd00000-dfd03fff
```

The output of ```
iwconfig
``` was:
```
lo        no wireless extensions.

eth1      IEEE 802.11abg  ESSID:"ChinaNet-GWhV"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:19:C7:BB:7A:FC   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
eth0      no wireless extensions.
```

I used Broadcom STA drivers and intermittently they appear in Additional Drivers.  I've removed and re-installed according to instructions in thread 38327 and a tutorial on howopensource.  I've installed wicd: it doesn't find any wireless networks, but after installing it, I would occasionally have a connection recognised in Network Manager, which I've also re-installed.  I'm currently using ethernet and have experienced no problems with it.

---

### Post by damianoloan on 2013-02-11
As you can see, the wireless connection is now working.  When it doesn't, it simply vanishes from these outputs.  So, in that case, the output of lscpi:```
Host bridge: Intel Corporation Atom Processor D2xxx/N2xxx DRAM Controller (rev 03) 00:02.0 VGA compatible controller: Intel Corporation Atom Processor D2xxx/N2xxx Integrated Graphics Controller (rev 09) 00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02) 00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02) 00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02) 00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02) 00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02) 00:1d.0 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02) 00:1d.1 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02) 00:1d.2 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02) 00:1d.3 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02) 00:1d.7 USB controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02) 00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) 00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02) 00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA Controller [AHCI mode] (rev 02) 00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02) 03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05) 04:00.0 USB controller: ASMedia Technology Inc. ASM1042 SuperSpeed USB Host Controller 

```

---

### Post by ahallubuntu on 2013-02-12
~

---

### Post by damianoloan on 2013-02-15
Thanks, I've been connected with just Network Manager for a few days, only experiencing some problems when using a VPN.  I don't think I solved the problem, but as long as it's not manifest I'll presume set-up is ok.

---

