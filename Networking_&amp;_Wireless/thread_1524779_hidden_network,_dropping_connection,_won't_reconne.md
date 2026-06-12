---
title: "hidden network, dropping connection, won't reconnect"
date: 2010-07-05
forum: Networking &amp; Wireless
---

### Post by dez93_2000 on 2010-07-05
Hi all. Been researching this and am going mad.

My problem:
Switch from karmic to lucid has meant that my wireless network is now hidden (i didn't change anything). When it connects upstairs in my house it'll keep the connection for a seemingly random amount of time, then drop it, and won't reconnect: I'll go through the usual process of connecting to a hidden network, select mine, but it'll simply never connect. A restart means that it'll connect again, but only for so long.

I've got a netgear WG121 usb plugin card and have done everything on [https://help.ubuntu.com/community/WifiDocs/Device/WG121](https://help.ubuntu.com/community/WifiDocs/Device/WG121) already. The router is a netgear dir-615; like i say, it's not set to hidden but i tried doing so just in case it was reversed for some reason, but this didn't change anything. I think getting this unhidden is the first stage.

I've tried swapping networkmanager for wicd but that didn't help - saw the network (hidden) once but didn't connect, and never found it again.
Tried this: [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide) but for 5.1 i don't know what i'm looking for, other than i see 2 wireless networks which aren't mine.
[http://ubuntuforums.org/showthread.php?t=1524739](http://ubuntuforums.org/showthread.php?t=1524739) my problem is similar to this guy's.

I'm completely lost for ideas. I'm tempted to either revert to karmic or get a 20m cat5 and run it through my house, annoying my housemates. If anyone's got any ideas, any logs i can query after the connection's dropped, anything i can try to make my router actually broadcast, or if it is broadcasting for ubuntu to actually see it?

Many many thanks in advance.

---

### Post by dez93_2000 on 2010-07-05
Output from here: [http://help.ubuntu.com/community/WirelessTroubleshootingProcedure](http://help.ubuntu.com/community/WirelessTroubleshootingProcedure)
Logged while hardlined. Currently downstairs where the wireless connects to the (hidden) wifi and stays on it because it's close enough to plug it in.

Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid Release.gpg
Get: 1 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_GB [62.9kB]
Get: 2 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg [189B]            
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_GB   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://ppa.launchpad.net/aheck/ppa/ubuntu/](http://ppa.launchpad.net/aheck/ppa/ubuntu/) lucid/main Translation-en_GB    
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg                             
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_GB       
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_GB
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_GB
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_GB
Get: 3 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release [38.5kB]              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release                                 
Get: 4 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_GB [2,332B]
Get: 5 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_GB [33.9kB]
Get: 6 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_GB [37.7kB]
Get: 7 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates Release.gpg [189B]           
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_GB  
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_GB
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_GB
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid Release                                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Get: 8 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates Release [44.7kB]             
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages                        
Get: 9 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages [43.3kB]        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/main Packages           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/universe Sources
Get: 10 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages [14B]
Get: 11 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources [14.2kB]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/multiverse Packages                    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/multiverse Sources
Get: 12 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates/main Packages [247kB]
Get: 13 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources [14B]
Get: 14 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages [17.9kB]
Get: 15 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources [2,813B]    
Get: 16 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages [1,668B] 
Get: 17 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources [580B]    
Get: 18 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates/restricted Packages [3,252B]
Get: 19 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates/main Sources [89.8kB]
Get: 20 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates/restricted Sources [1,292B]
Get: 21 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates/universe Packages [62.5kB]
Get: 22 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates/universe Sources [18.8kB]
Get: 23 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates/multiverse Packages [3,771B]
Get: 24 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates/multiverse Sources [1,499B]
Fetched 729kB in 1s (722kB/s)                            
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
grep is already the newest version.
The following packages were automatically installed and are no longer required:
  plasma-dataengines-workspace kdepim-runtime libprocessui4 libtaskmanager4
  libqimageblitz4 libkscreensaver5 plasma-widgets-workspace
  mysql-client-core-5.1 libplasma-geolocation-interface4 mysql-server-core-5.1
  libksgrd4 kdebase-workspace-bin libkworkspace4 libplasmagenericshell4
  libkfontinst4 python-iniparse libkephal4 kdebase-workspace-data ksysguardd
  libplasmaclock4 libweather-ion4 kdebase-workspace-kgreet-plugins
  akonadi-server libwbxml2-0 libplasma-applet-system-monitor4 libprocesscore4
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libhd16
The following NEW packages will be installed
  hwinfo libhd16
0 upgraded, 2 newly installed, 0 to remove and 99 not upgraded.
Need to get 744kB of archives.
After this operation, 2,060kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get: 1 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid/universe libhd16 16.0-2 [698kB]
Get: 2 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid/universe hwinfo 16.0-2 [46.1kB]
Fetched 744kB in 1s (589kB/s)
Selecting previously deselected package libhd16.
(Reading database ... 182087 files and directories currently installed.)
Unpacking libhd16 (from .../libhd16_16.0-2_i386.deb) ...
Selecting previously deselected package hwinfo.
Unpacking hwinfo (from .../hwinfo_16.0-2_i386.deb) ...
Processing triggers for man-db ...
Setting up libhd16 (16.0-2) ...

Setting up hwinfo (16.0-2) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
  *-network               
       description: Ethernet interface
       product: 88E8056 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 14
       serial: 00:1a:4d:43:34:91
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.25 duplex=full firmware=N/A ip=192.168.0.104 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:28 memory:f9000000-f9003fff ioport:9000(size=256) memory:80600000-8061ffff(prefetchable)
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan1
       serial: 00:09:5b:a3:88:92
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+netwg121 driverversion=1.55+NETGEAR, Inc.,11/13/2003, 1 link=no multicast=yes wireless=IEEE 802.11g
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

wlan1     Scan completed :
          Cell 01 - Address: 00:11:50:6E:52:64
                    ESSID:"deleted by user: not my wireless"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:32/100  Signal level:-75 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=1
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: 00:24:B2:B6:A5:6C
                    ESSID:"deleted by user: not my wireless either"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:34/100  Signal level:-74 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=3
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

auto lo
iface lo inet loopback

# WLAN
allow-hotplug wlan0
auto wlan0
iface wlan0 inet dhcp
 wireless-essid MyWireless
 wireless-key MyPassword
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04 LTS"
00:00.0 Host bridge [0600]: Intel Corporation 82P965/G965 Memory Controller Hub [8086:29a0] (rev 02)
00:01.0 PCI bridge [0604]: Intel Corporation 82P965/G965 PCI Express Root Port [8086:29a1] (rev 02)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 02)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 02)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 02)
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 02)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 [8086:2845] (rev 02)
00:1c.4 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 [8086:2847] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev f2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HB/HR (ICH8/R) LPC Interface Controller [8086:2810] (rev 02)
00:1f.2 IDE interface [0101]: Intel Corporation 82801H (ICH8 Family) 4 port SATA IDE Controller [8086:2820] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 02)
00:1f.5 IDE interface [0101]: Intel Corporation 82801H (ICH8 Family) 2 port SATA IDE Controller [8086:2825] (rev 02)
01:00.0 VGA compatible controller [0300]: nVidia Corporation G92 [GeForce 8800 GT] [10de:0611] (rev a2)
03:00.0 SATA controller [0106]: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller [197b:2363] (rev 02)
03:00.1 IDE interface [0101]: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller [197b:2363] (rev 02)
04:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller [11ab:4364] (rev 14)
05:00.0 Mass storage controller [0180]: Promise Technology, Inc. PDC20268 (Ultra100 TX2) [105a:4d68] (rev 02)
Bus 007 Device 003: ID 0518:0002 EzKEY Corp. EZ-9900C Keyboard
Bus 007 Device 002: ID 1532:000d Razer USA, Ltd 
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 0a5c:2101 Broadcom Corp. A-Link BlueUsbA2 Bluetooth
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 0846:4210 NetGear, Inc. WG121(v2) 54 Mbps Wireless [Intersil Prism GT]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
H/W path             Device      Class       Description
========================================================
                                 system      965P-DS3
/0                               bus         965P-DS3
/0/0                             memory      128KiB BIOS
/0/4                             processor   Intel(R) Core(TM)2 CPU          660
/0/4/a                           memory      64KiB L1 cache
/0/4/b                           memory      4MiB L2 cache
/0/4/0.1                         processor   Logical CPU
/0/4/0.2                         processor   Logical CPU
/0/1b                            memory      2GiB System Memory
/0/1b/0                          memory      1GiB DIMM 800 MHz (1.2 ns)
/0/1b/1                          memory      DIMM [empty]
/0/1b/2                          memory      1GiB DIMM 800 MHz (1.2 ns)
/0/1b/3                          memory      DIMM [empty]
/0/1                             processor   
/0/1/0.1                         processor   Logical CPU
/0/1/0.2                         processor   Logical CPU
/0/100                           bridge      82P965/G965 Memory Controller Hub
/0/100/1                         bridge      82P965/G965 PCI Express Root Port
/0/100/1/0                       display     G92 [GeForce 8800 GT]
/0/100/1a                        bus         82801H (ICH8 Family) USB UHCI Contr
/0/100/1a.1                      bus         82801H (ICH8 Family) USB UHCI Contr
/0/100/1a.7                      bus         82801H (ICH8 Family) USB2 EHCI Cont
/0/100/1b                        multimedia  82801H (ICH8 Family) HD Audio Contr
/0/100/1c                        bridge      82801H (ICH8 Family) PCI Express Po
/0/100/1c.3                      bridge      82801H (ICH8 Family) PCI Express Po
/0/100/1c.3/0                    storage     JMB362/JMB363 Serial ATA Controller
/0/100/1c.3/0.1                  storage     JMB362/JMB363 Serial ATA Controller
/0/100/1c.4                      bridge      82801H (ICH8 Family) PCI Express Po
/0/100/1c.4/0        eth0        network     88E8056 PCI-E Gigabit Ethernet Cont
/0/100/1d                        bus         82801H (ICH8 Family) USB UHCI Contr
/0/100/1d.1                      bus         82801H (ICH8 Family) USB UHCI Contr
/0/100/1d.2                      bus         82801H (ICH8 Family) USB UHCI Contr
/0/100/1d.7                      bus         82801H (ICH8 Family) USB2 EHCI Cont
/0/100/1e                        bridge      82801 PCI Bridge
/0/100/1e/0          scsi8       storage     PDC20268 (Ultra100 TX2)
/0/100/1e/0/0.0.0    /dev/sdc    disk        80GB SAMSUNG SV0813H
/0/100/1e/0/0.0.0/1  /dev/sdc1   volume      74GiB Windows NTFS volume
/0/100/1e/0/0.1.0    /dev/sdd    disk        123GB HDS722512VLAT80
/0/100/1e/0/0.1.0/1  /dev/sdd1   volume      115GiB Windows NTFS volume
/0/100/1f                        bridge      82801HB/HR (ICH8/R) LPC Interface C
/0/100/1f.2          scsi0       storage     82801H (ICH8 Family) 4 port SATA ID
/0/100/1f.2/0        /dev/sda    disk        500GB SAMSUNG HD501LJ
/0/100/1f.2/0/1      /dev/sda1   volume      465GiB Windows NTFS volume
/0/100/1f.2/1        /dev/sdb    disk        500GB SAMSUNG HD501LJ
/0/100/1f.2/1/1      /dev/sdb1   volume      460GiB EXT4 volume
/0/100/1f.2/1/2      /dev/sdb2   volume      5891MiB Extended partition
/0/100/1f.2/1/2/5    /dev/sdb5   volume      5890MiB Linux swap / Solaris partit
/0/100/1f.3                      bus         82801H (ICH8 Family) SMBus Controll
/0/100/1f.5          scsi2       storage     82801H (ICH8 Family) 2 port SATA ID
/0/100/1f.5/0.0.0    /dev/cdrom  disk        BD-RE  GGW-H20L
/1                   wlan1       network     Wireless interface
Linux user-desktop 2.6.32-22-generic #36-Ubuntu SMP Thu Jun 3 22:02:19 UTC 2010 i686 GNU/Linux
[    0.000000] found SMP MP-table at [c00f53b0] f53b0
[    0.178018] ACPI: No dock devices found.
[    0.196011] Switching to clocksource tsc
[    0.200328] pnp: PnP ACPI: found 14 devices
[    0.427830] hub 1-0:1.0: USB hub found
[    0.447813] hub 2-0:1.0: USB hub found
[    0.448060] hub 3-0:1.0: USB hub found
[    0.448267] hub 4-0:1.0: USB hub found
[    0.448460] hub 5-0:1.0: USB hub found
[    0.448651] hub 6-0:1.0: USB hub found
[    0.448844] hub 7-0:1.0: USB hub found
[    0.448938] PNP: No PS/2 controller found. Probing ports directly.
[    0.449734] device-mapper: multipath: version 1.1.0 loaded
[    0.449736] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.453348] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.604485] isapnp: No Plug & Play device found
[    1.698874] sky2 eth0: addr 00:1a:4d:43:34:91
[   23.291763] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[   23.294239] lp: driver loaded but no devices found
[   23.605168] Console: switching to colour frame buffer device 80x30
[   23.810839] ndiswrapper: driver netwg121 (NETGEAR, Inc.,11/13/2003, 1.0.5.1000) loaded
[   24.611938] sky2 eth0: enabling interface
[   24.612097] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   25.645188] wlan0: ethernet device 00:09:5b:a3:88:92 using NDIS driver: netwg121, version: 0x10005, NDIS version: 0x501, vendor: 'NETGEAR WG121 802.11g Wireless USB2.0 Adapter', 0846:4210.F.conf
[   25.645210] wlan0: encryption modes supported: WEP; TKIP with WPA; AES/CCMP with WPA
[   25.647663] usbcore: registered new interface driver ndiswrapper
[   25.660706] ndiswrapper: changing interface name from 'wlan0' to 'wlan1'
[   25.660732] udev: renamed network interface wlan0 to wlan1
[   25.661789] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[   61.086240] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control both
[   61.086402] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   71.288033] eth0: no IPv6 routers present
[  328.403465] sky2 eth0: Link is down.
[  351.034755] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control both
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

wlan1     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:2 Mb/s   
          RTS thr:2432 B   Fragment thr:2432 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

/etc/modprobe.d/blacklist.conf:# replaced by b43 and ssb.
/etc/modprobe.d/blacklist-watchdog.conf:blacklist twl4030_wdt
31: PCI 400.0: 0200 Ethernet controller                         
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_11ab_4364
  Unique ID: rBUF.fZtLncaJYvE
  Parent ID: QSNP.ZDO8ElpEKyA
  SysFS ID: /devices/pci0000:00/0000:00:1c.4/0000:04:00.0
  SysFS BusID: 0000:04:00.0
  Hardware Class: network
  Model: "Marvell 88E8056 PCI-E Gigabit Ethernet Controller"
  Vendor: pci 0x11ab "Marvell Technology Group Ltd."
  Device: pci 0x4364 "88E8056 PCI-E Gigabit Ethernet Controller"
  SubVendor: pci 0x1458 "Giga-byte Technology"
  SubDevice: pci 0xe000 
  Revision: 0x14
  Driver: "sky2"
  Driver Modules: "sky2"
  Device File: eth0
  Memory Range: 0xf9000000-0xf9003fff (rw,non-prefetchable)
  I/O Ports: 0x9000-0x9fff (rw)
  Memory Range: 0x80600000-0x8061ffff (ro,prefetchable,disabled)
  IRQ: 28 (12924 events)
  HW Address: 00:1a:4d:43:34:91
  Link detected: yes
  Module Alias: "pci:v000011ABd00004364sv00001458sd0000E000bc02sc00i00"
  Driver Info #0:
    Driver Status: sky2 is active
    Driver Activation Cmd: "modprobe sky2"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #18 (PCI bridge)

55: USB 00.0: 0282 WLAN controller
  [Created at usb.122]
  UDI: /org/freedesktop/Hal/devices/usb_device_846_4210_noserial_if0
  Unique ID: cLrx.wFhXmXeLIn4
  Parent ID: k4bc.cO89g+iefn1
  SysFS ID: /devices/pci0000:00/0000:00:1a.7/usb1/1-2/1-2:1.0
  SysFS BusID: 1-2:1.0
  Hardware Class: network
  Model: "NetGear WG121 WiFi (v2)"
  Hotplug: USB
  Vendor: usb 0x0846 "NetGear, Inc."
  Device: usb 0x4210 "WG121 WiFi (v2)"
  Revision: "2.03"
  Driver: "ndiswrapper"
  Driver Modules: "ndiswrapper", "ndiswrapper"
  Device File: wlan1
  Features: WLAN
  Speed: 480 Mbps
  HW Address: 00:09:5b:a3:88:92
  Link detected: no
  WLAN channels: 1 2 3 4 5 6 7 8 9 10 11 12 13 14
  WLAN frequencies: 2.412 2.417 2.422 2.427 2.432 2.437 2.442 2.447 2.452 2.457 2.462 2.467 2.472 2.484
  WLAN bitrates: 1 2 5.5 11 6 9 12 18 24 36 48 54
  WLAN encryption modes: WEP40 WEP104 TKIP CCMP
  WLAN authentication modes: open sharedkey wpa-psk wpa-eap
  Module Alias: "usb:v0846p4210d0203dcFFdsc00dp00icFFisc00ip00"
  Driver Info #0:
    Driver Status: p54usb is not active
    Driver Activation Cmd: "modprobe p54usb"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #48 (Hub)
 * Reconfiguring network interfaces...                                          Ignoring unknown interface eth0=eth0.
wlan0: ERROR while getting interface flags: No such device
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device wlan0 ; No such device.
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wlan0 ; No such device.
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.

---

