---
title: "DLink DWA-525 &amp; Ubuntu 10.10 Maverick"
date: 2010-11-07
forum: Networking &amp; Wireless
---

### Post by sukharevd on 2010-11-07
Hi,

trying to create new WiFi connections I understood that perhaps I have a problem with driver.
So my problem is that when I create new connection it either isn't established if it's without pw, or endlessly asks pw if it's WEP with pw, or establishes connection, but very fake one 'cause computers don't see each other and have IPs in very different subnets.

I hope all my problems linked with wrong install of drivers and not with kernel...

So what did I do:
1. I banned rt2860sta driver how it was described here: [http://ubuntuforums.org/showpost.php?p=10055176&postcount=4](http://ubuntuforums.org/showpost.php?p=10055176&postcount=4)
2. I installed new rt3062sta driver just like was said here: [http://ubuntuforums.org/showpost.php?p=9660765&postcount=4](http://ubuntuforums.org/showpost.php?p=9660765&postcount=4)

Installing driver I changed RT2860STA2.dat in this way:
```
#The word of "Default" must not be removed
Default
CountryRegion=0
CountryRegionABand=7
CountryCode=UA
ChannelGeography=1
SSID=Dennis2860AP
NetworkType=Adhoc
WirelessMode=5
Channel=0
BeaconPeriod=100
TxPower=100
BGProtection=0
TxPreamble=0
RTSThreshold=2347
FragThreshold=2346
TxBurst=1
PktAggregate=0
WmmCapable=1
AckPolicy=0;0;0;0
AuthMode=WEPAUTO
EncrypType=WEP
WPAPSK=
DefaultKeyID=1
Key1Type=1
Key1Str=asdfg
Key2Type=1
Key2Str=qwert
Key3Type=1
Key3Str=jkl;'
Key4Type=1
Key4Str=uiop[
PSMode=CAM
AutoRoaming=0
RoamThreshold=70
APSDCapable=0
APSDAC=0;0;0;0
HT_RDG=1
HT_EXTCHA=0
HT_OpMode=0
HT_MpduDensity=4
HT_BW=1
HT_AutoBA=1
HT_BADecline=0
HT_AMSDU=0
HT_BAWinSize=64
HT_GI=1
HT_MCS=33
HT_MIMOPSMode=3
HT_DisallowTKIP=1
HT_STBC=0
IEEE80211H=0
TGnWifiTest=0
WirelessEvent=0
CarrierDetect=0
AntDiversity=0
BeaconLostTime=4
PSP_XLINK_MODE=0
RadioOn=1
``````
dmitriy@dmitriy-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:22:15:2c:cb:ea  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:45 

eth2      Link encap:Ethernet  HWaddr 00:22:b0:dc:b3:76  
          inet addr:188.231.187.9  Bcast:188.231.187.255  Mask:255.255.255.0
          inet6 addr: 2002:bce7:bb96:4:222:b0ff:fedc:b376/64 Scope:Global
          inet6 addr: fec0::4:222:b0ff:fedc:b376/64 Scope:Site
          inet6 addr: fec0::b:222:b0ff:fedc:b376/64 Scope:Site
          inet6 addr: 2002:bce7:90a8:b:222:b0ff:fedc:b376/64 Scope:Global
          inet6 addr: fe80::222:b0ff:fedc:b376/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3104442 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2005120 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2154208367 (2.1 GB)  TX bytes:2410547858 (2.4 GB)
          Interrupt:17 Base address:0xec00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:18298 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18298 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3295307 (3.2 MB)  TX bytes:3295307 (3.2 MB)

ra0       Link encap:Ethernet  HWaddr 1c:bd:b9:8c:07:99  
          inet6 addr: fe80::1ebd:b9ff:fe8c:799/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:3506 errors:0 dropped:0 overruns:0 frame:0
          TX packets:41902 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:289332 (289.3 KB)  TX bytes:67262 (67.2 KB)
          Interrupt:18 

``````

dmitriy@dmitriy-desktop:~$ iwconfig
lo        no wireless extensions.

eth2      no wireless extensions.

eth0      no wireless extensions.

ra0       Ralink STA  ESSID:""  Nickname:"RT3562STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=78/100  Signal level:0 dBm  Noise level:0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

vboxnet0  no wireless extensions.

``````
dmitriy@dmitriy-desktop:~$ iwlist scann
lo        Interface doesn't support scanning.

eth2      Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

ra0       No scan results

vboxnet0  Interface doesn't support scanning.

``````
dmitriy@dmitriy-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 4 Series Chipset PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
00:1a.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
00:1a.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6
00:1a.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 1
00:1c.4 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 5
00:1c.5 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 6
00:1d.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
00:1d.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
00:1d.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
00:1d.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation 82801JIR (ICH10R) LPC Interface Controller
00:1f.2 IDE interface: Intel Corporation 82801JI (ICH10 Family) 4 port SATA IDE Controller #1
00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
00:1f.5 IDE interface: Intel Corporation 82801JI (ICH10 Family) 2 port SATA IDE Controller #2
01:00.0 VGA compatible controller: nVidia Corporation G84 [GeForce 8600 GT] (rev a1)
02:00.0 Ethernet controller: Atheros Communications AR8121/AR8113/AR8114 Gigabit or Fast Ethernet (rev b0)
03:00.0 IDE interface: Marvell Technology Group Ltd. 88SE6121 SATA II Controller (rev b2)
05:01.0 Ethernet controller: VIA Technologies, Inc. VT6105/VT6106S [Rhine-III] (rev 8b)
05:02.0 Network controller: RaLink Device 3060
05:03.0 FireWire (IEEE 1394): Agere Systems FW322/323 (rev 70)

```
Does it looks like problem with installing driver?

Please help me to solve my problem. I spent 2 days solving it, but even don't know what is wrong...

Best regards, Dmitriy.

---

### Post by sukharevd on 2010-11-08
Any ideas? Maybe have I to share more information/command results about my problem? Feel free to ask me about it.

---

### Post by sukharevd on 2010-11-08
Little more information and required by forum info:
My modprobe blacklist:```
dmitriy@dmitriy-desktop:~$ sudo cat /etc/modprobe.d/blacklist.conf
[sudo] password for dmitriy: 
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac

blacklist rt2800pci

```Also I executed this for enabling WIRELESS_EXT:```
$ cd /usr/src/linux
$ sudo make menuconfig[INDENT]Device Drivers --->
[*] Network device support --->
[*] Wireless LAN --->
<*> IEEE 802.11 for HostAP (Prism2/2.5/3 and WEP/TKIP/CCMP)[/INDENT]
```Required:```
dmitriy@dmitriy-desktop:~$ lsmod | grep rt
parport_pc             30086  0 
rt3562sta            1008283  1 
parport                37032  3 parport_pc,ppdev,lp
``````
dmitriy@dmitriy-desktop:~$ sudo lshw -C network
[sudo] password for dmitriy: 
  *-network               
       description: Ethernet interface
       product: AR8121/AR8113/AR8114 Gigabit or Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: b0
       serial: 00:22:15:2c:cb:ea
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=ATL1E driverversion=1.0.0.7-NAPI firmware=L1e latency=0 link=no multicast=yes port=twisted pair
       resources: irq:45 memory:fe9c0000-fe9fffff ioport:cc00(size=128)
  *-network:0
       description: Ethernet interface
       product: VT6105/VT6106S [Rhine-III]
       vendor: VIA Technologies, Inc.
       physical id: 1
       bus info: pci@0000:05:01.0
       logical name: eth2
       version: 8b
       serial: 00:22:b0:dc:b3:76
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=full ip=188.231.187.9 latency=64 link=yes maxlatency=8 mingnt=3 multicast=yes port=MII speed=100MB/s
       resources: irq:17 ioport:e800(size=256) memory:febffc00-febffcff
  *-network:1
       description: Wireless interface
       product: RaLink
       vendor: RaLink
       physical id: 2
       bus info: pci@0000:05:02.0
       logical name: ra0
       version: 00
       serial: 1c:bd:b9:8c:07:99
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=RALINK WLAN driverversion=2.4.0.0 latency=64 maxlatency=4 mingnt=2 multicast=yes wireless=Ralink STA
       resources: irq:18 memory:febe0000-febeffff
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
``````
dmitriy@dmitriy-desktop:~$ lsb_release -d
Description:    Ubuntu 10.10
``````
dmitriy@dmitriy-desktop:~$ uname -mr
2.6.35-22-generic x86_64
``````
dmitriy@dmitriy-desktop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          Ignoring unknown interface eth2=eth2.
                                                                         [ OK ]
``````
$dmesg[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.35-22-generic (buildd@yellow) (gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu5) ) #35-Ubuntu SMP Sat Oct 16 20:45:36 UTC 2010 (Ubuntu 2.6.35-22.35-generic 2.6.35.4)
[    0.000000] Command line: root=UUID=4ff0a8ac-d8b7-4b89-9633-1ae824988cdb ro quiet splash 
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000cff70000 (usable)
[    0.000000]  BIOS-e820: 00000000cff70000 - 00000000cff7e000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000cff7e000 - 00000000cffd0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000cffd0000 - 00000000d0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000130000000 (usable)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 update range: 0000000000000000 - 0000000000001000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] No AGP bridge found
[    0.000000] last_pfn = 0x130000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-DFFFF write-protect
[    0.000000]   E0000-EFFFF write-through
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F00000000 write-back
[    0.000000]   1 base 100000000 mask FE0000000 write-back
[    0.000000]   2 base 120000000 mask FF0000000 write-back
[    0.000000]   3 base 0D0000000 mask FF0000000 uncachable
[    0.000000]   4 base 0E0000000 mask FE0000000 uncachable
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 00000000d0000000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0xcff70 max_arch_pfn = 0x400000000
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009f800 (usable)
[    0.000000]  modified: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000cff70000 (usable)
[    0.000000]  modified: 00000000cff70000 - 00000000cff7e000 (ACPI data)
[    0.000000]  modified: 00000000cff7e000 - 00000000cffd0000 (ACPI NVS)
[    0.000000]  modified: 00000000cffd0000 - 00000000d0000000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000]  modified: 0000000100000000 - 0000000130000000 (usable)
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] found SMP MP-table at [ffff8800000ff780] ff780
[    0.000000] init_memory_mapping: 0000000000000000-00000000cff70000
[    0.000000]  0000000000 - 00cfe00000 page 2M
[    0.000000]  00cfe00000 - 00cff70000 page 4k
[    0.000000] kernel direct mapping tables up to cff70000 @ 16000-1c000
[    0.000000] init_memory_mapping: 0000000100000000-0000000130000000
[    0.000000]  0100000000 - 0130000000 page 2M
[    0.000000] kernel direct mapping tables up to 130000000 @ 1a000-20000
[    0.000000] RAMDISK: 37570000 - 37ff0000
[    0.000000] ACPI: RSDP 00000000000faff0 00014 (v00 ACPIAM)
[    0.000000] ACPI: RSDT 00000000cff70000 0003C (v01 A_M_I_ OEMRSDT  02001025 MSFT 00000097)
[    0.000000] ACPI: FACP 00000000cff70200 00084 (v02 A_M_I_ OEMFACP  02001025 MSFT 00000097)
[    0.000000] ACPI: DSDT 00000000cff70440 09720 (v01  A0993 A0993001 00000001 INTL 20060113)
[    0.000000] ACPI: FACS 00000000cff7e000 00040
[    0.000000] ACPI: APIC 00000000cff70390 0006C (v01 A_M_I_ OEMAPIC  02001025 MSFT 00000097)
[    0.000000] ACPI: MCFG 00000000cff70400 0003C (v01 A_M_I_ OEMMCFG  02001025 MSFT 00000097)
[    0.000000] ACPI: OEMB 00000000cff7e040 00089 (v01 A_M_I_ AMI_OEM  02001025 MSFT 00000097)
[    0.000000] ACPI: HPET 00000000cff79b60 00038 (v01 A_M_I_ OEMHPET  02001025 MSFT 00000097)
[    0.000000] ACPI: OSFR 00000000cff79ba0 000B0 (v01 A_M_I_ OEMOSFR  02001025 MSFT 00000097)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000130000000
[    0.000000] Initmem setup node 0 0000000000000000-0000000130000000
[    0.000000]   NODE_DATA [0000000100000000 - 0000000100004fff]
[    0.000000]  [ffffea0000000000-ffffea00043fffff] PMD -> [ffff880100200000-ffff880103bfffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00130000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x000cff70
[    0.000000]     0: 0x00100000 -> 0x00130000
[    0.000000] On node 0 totalpages: 1048319
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3927 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 833448 pages, LIFO batch:31
[    0.000000]   Normal zone: 2688 pages used for memmap
[    0.000000]   Normal zone: 193920 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a301 base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] early_res array is doubled to 64 at [1b000 - 1b7ff]
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e4000
[    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000cff70000 - 00000000cff7e000
[    0.000000] PM: Registered nosave memory: 00000000cff7e000 - 00000000cffd0000
[    0.000000] PM: Registered nosave memory: 00000000cffd0000 - 00000000d0000000
[    0.000000] PM: Registered nosave memory: 00000000d0000000 - 00000000fee00000
[    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
[    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000fff00000
[    0.000000] PM: Registered nosave memory: 00000000fff00000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at d0000000 (gap: d0000000:2ee00000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880001e00000 s91520 r8192 d23168 u524288
[    0.000000] pcpu-alloc: s91520 r8192 d23168 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1031295
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: root=UUID=4ff0a8ac-d8b7-4b89-9633-1ae824988cdb ro quiet splash 
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Subtract (56 early reservations)
[    0.000000]   #1 [0001000000 - 0001d17114]   TEXT DATA BSS
[    0.000000]   #2 [0037570000 - 0037ff0000]         RAMDISK
[    0.000000]   #3 [0001d18000 - 0001d18270]             BRK
[    0.000000]   #4 [00000ff790 - 0000100000]   BIOS reserved
[    0.000000]   #5 [00000ff780 - 00000ff790]    MP-table mpf
[    0.000000]   #6 [000009f800 - 00000e3e00]   BIOS reserved
[    0.000000]   #7 [00000e3f7c - 00000ff780]   BIOS reserved
[    0.000000]   #8 [00000e3e00 - 00000e3f7c]    MP-table mpc
[    0.000000]   #9 [0000010000 - 0000012000]      TRAMPOLINE
[    0.000000]   #10 [0000012000 - 0000016000]     ACPI WAKEUP
[    0.000000]   #11 [0000016000 - 000001a000]         PGTABLE
[    0.000000]   #12 [000001a000 - 000001b000]         PGTABLE
[    0.000000]   #13 [0100000000 - 0100005000]       NODE_DATA
[    0.000000]   #14 [0001d18280 - 0001d19280]         BOOTMEM
[    0.000000]   #15 [0001d17140 - 0001d17440]         BOOTMEM
[    0.000000]   #16 [0100005000 - 0100006000]         BOOTMEM
[    0.000000]   #17 [0100006000 - 0100007000]         BOOTMEM
[    0.000000]   #18 [0100200000 - 0103c00000]        MEMMAP 0
[    0.000000]   #19 [0001d17440 - 0001d175c0]         BOOTMEM
[    0.000000]   #20 [0001d19280 - 0001d31280]         BOOTMEM
[    0.000000]   #21 [0001d31280 - 0001d37280]         BOOTMEM
[    0.000000]   #22 [0001d38000 - 0001d39000]         BOOTMEM
[    0.000000]   #23 [0001d175c0 - 0001d17601]         BOOTMEM
[    0.000000]   #24 [0001d17640 - 0001d17683]         BOOTMEM
[    0.000000]   #25 [0001d176c0 - 0001d17928]         BOOTMEM
[    0.000000]   #26 [0001d17940 - 0001d179a8]         BOOTMEM
[    0.000000]   #27 [0001d179c0 - 0001d17a28]         BOOTMEM
[    0.000000]   #28 [0001d17a40 - 0001d17aa8]         BOOTMEM
[    0.000000]   #29 [0001d17ac0 - 0001d17b28]         BOOTMEM
[    0.000000]   #30 [0001d17b40 - 0001d17ba8]         BOOTMEM
[    0.000000]   #31 [0001d17bc0 - 0001d17c28]         BOOTMEM
[    0.000000]   #32 [0001d17c40 - 0001d17ca8]         BOOTMEM
[    0.000000]   #33 [0001d17cc0 - 0001d17d28]         BOOTMEM
[    0.000000]   #34 [0001d17d40 - 0001d17da8]         BOOTMEM
[    0.000000]   #35 [0001d17dc0 - 0001d17e28]         BOOTMEM
[    0.000000]   #36 [0001d17e40 - 0001d17e60]         BOOTMEM
[    0.000000]   #37 [0001d17e80 - 0001d17ea0]         BOOTMEM
[    0.000000]   #38 [0001d17ec0 - 0001d17f00]         BOOTMEM
[    0.000000]   #39 [0001d17f00 - 0001d17f40]         BOOTMEM
[    0.000000]   #40 [0001e00000 - 0001e1e000]         BOOTMEM
[    0.000000]   #41 [0001e80000 - 0001e9e000]         BOOTMEM
[    0.000000]   #42 [0001f00000 - 0001f1e000]         BOOTMEM
[    0.000000]   #43 [0001f80000 - 0001f9e000]         BOOTMEM
[    0.000000]   #44 [0001d17f40 - 0001d17f48]         BOOTMEM
[    0.000000]   #45 [0001d17f80 - 0001d17f88]         BOOTMEM
[    0.000000]   #46 [0001d17fc0 - 0001d17fd0]         BOOTMEM
[    0.000000]   #47 [0001d37280 - 0001d372a0]         BOOTMEM
[    0.000000]   #48 [0001d372c0 - 0001d373f0]         BOOTMEM
[    0.000000]   #49 [0001d37400 - 0001d37450]         BOOTMEM
[    0.000000]   #50 [0001d37480 - 0001d374d0]         BOOTMEM
[    0.000000]   #51 [0001d39000 - 0001d41000]         BOOTMEM
[    0.000000]   #52 [0001f9e000 - 0005f9e000]         BOOTMEM
[    0.000000]   #53 [0001d41000 - 0001d61000]         BOOTMEM
[    0.000000]   #54 [0001d61000 - 0001da1000]         BOOTMEM
[    0.000000]   #55 [000001b800 - 0000023800]         BOOTMEM
[    0.000000] Memory: 4043052k/4980736k available (5708k kernel code, 787460k absent, 150224k reserved, 5382k data, 908k init)
[    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU-based detection of stalled CPUs is disabled.
[    0.000000]     Verbose stalled-CPUs detection is disabled.
[    0.000000] NR_IRQS:4352 nr_irqs:712
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 41943040 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 3166.339 MHz processor.
[    0.000006] Calibrating delay loop (skipped), value calculated using timer frequency.. 6332.67 BogoMIPS (lpj=31663390)
[    0.000009] pid_max: default: 32768 minimum: 301
[    0.000027] Security Framework initialized
[    0.000044] AppArmor: AppArmor initialized
[    0.000045] Yama: becoming mindful.
[    0.010038] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.011677] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.012444] Mount-cache hash table entries: 256
[    0.012556] Initializing cgroup subsys ns
[    0.012561] Initializing cgroup subsys cpuacct
[    0.012564] Initializing cgroup subsys memory
[    0.012571] Initializing cgroup subsys devices
[    0.012572] Initializing cgroup subsys freezer
[    0.012574] Initializing cgroup subsys net_cls
[    0.012598] CPU: Physical Processor ID: 0
[    0.012599] CPU: Processor Core ID: 0
[    0.012601] mce: CPU supports 6 MCE banks
[    0.012607] CPU0: Thermal monitoring enabled (TM2)
[    0.012610] using mwait in idle threads.
[    0.012612] Performance Events: PEBS fmt0+, Core2 events, Intel PMU driver.
[    0.012618] ... version:                2
[    0.012619] ... bit width:              40
[    0.012620] ... generic registers:      2
[    0.012621] ... value mask:             000000ffffffffff
[    0.012622] ... max period:             000000007fffffff
[    0.012623] ... fixed-purpose events:   3
[    0.012624] ... event mask:             0000000700000003
[    0.014518] ACPI: Core revision 20100428
[    0.030006] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.030011] ftrace: allocating 22680 entries in 89 pages
[    0.040037] Setting APIC routing to flat
[    0.040337] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.141555] CPU0: Intel(R) Core(TM)2 Duo CPU     E8500  @ 3.16GHz stepping 06
[    0.150000] Booting Node   0, Processors  #1
[    0.310014] Brought up 2 CPUs
[    0.310017] Total of 2 processors activated (12665.27 BogoMIPS).
[    0.310775] devtmpfs: initialized
[    0.310775] regulator: core version 0.5
[    0.310775] Time: 12:36:13  Date: 11/08/10
[    0.310775] NET: Registered protocol family 16
[    0.310775] Trying to unpack rootfs image as initramfs...
[    0.310775] ACPI: bus type pci registered
[    0.310775] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.310775] PCI: not using MMCONFIG
[    0.310775] PCI: Using configuration type 1 for base access
[    0.320092] bio: create slab <bio-0> at 0
[    0.321027] ACPI: EC: Look up EC in DSDT
[    0.321995] ACPI: Executed 1 blocks of module-level executable AML code
[    0.330695] ACPI: Interpreter enabled
[    0.330697] ACPI: (supports S0 S1 S3 S4 S5)
[    0.330713] ACPI: Using IOAPIC for interrupt routing
[    0.330754] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.332107] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI motherboard resources
[    0.367228] ACPI Warning: Incorrect checksum in table [OEMB] - 0xAF, should be 0xAE (20100428/tbutils-314)
[    0.367350] ACPI: No dock devices found.
[    0.367353] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.367470] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.367695] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    0.367697] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    0.367699] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.367701] pci_root PNP0A08:00: host bridge window [mem 0x000d0000-0x000dffff]
[    0.367703] pci_root PNP0A08:00: host bridge window [mem 0xd0000000-0xdfffffff]
[    0.367704] pci_root PNP0A08:00: host bridge window [mem 0xf0000000-0xffffffff]
[    0.367756] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.367759] pci 0000:00:01.0: PME# disabled
[    0.367811] pci 0000:00:1a.0: reg 20: [io  0xa800-0xa81f]
[    0.367864] pci 0000:00:1a.1: reg 20: [io  0xa880-0xa89f]
[    0.367917] pci 0000:00:1a.2: reg 20: [io  0xac00-0xac1f]
[    0.367967] pci 0000:00:1a.7: reg 10: [mem 0xf9fffc00-0xf9ffffff]
[    0.368012] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.368015] pci 0000:00:1a.7: PME# disabled
[    0.368042] pci 0000:00:1b.0: reg 10: [mem 0xf9ff8000-0xf9ffbfff 64bit]
[    0.368073] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.368076] pci 0000:00:1b.0: PME# disabled
[    0.368128] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.368131] pci 0000:00:1c.0: PME# disabled
[    0.368184] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.368187] pci 0000:00:1c.4: PME# disabled
[    0.368240] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    0.368243] pci 0000:00:1c.5: PME# disabled
[    0.368282] pci 0000:00:1d.0: reg 20: [io  0xa080-0xa09f]
[    0.368334] pci 0000:00:1d.1: reg 20: [io  0xa400-0xa41f]
[    0.368387] pci 0000:00:1d.2: reg 20: [io  0xa480-0xa49f]
[    0.368437] pci 0000:00:1d.7: reg 10: [mem 0xf9fff800-0xf9fffbff]
[    0.368481] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.368485] pci 0000:00:1d.7: PME# disabled
[    0.368580] pci 0000:00:1f.0: quirk: [io  0x0800-0x087f] claimed by ICH6 ACPI/GPIO/TCO
[    0.368583] pci 0000:00:1f.0: quirk: [io  0x0500-0x053f] claimed by ICH6 GPIO
[    0.368586] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0294 (mask 0003)
[    0.368590] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 3 PIO at 4700 (mask 001f)
[    0.368627] pci 0000:00:1f.2: reg 10: [io  0x9000-0x9007]
[    0.368631] pci 0000:00:1f.2: reg 14: [io  0x8c00-0x8c03]
[    0.368635] pci 0000:00:1f.2: reg 18: [io  0x8880-0x8887]
[    0.368639] pci 0000:00:1f.2: reg 1c: [io  0x8800-0x8803]
[    0.368643] pci 0000:00:1f.2: reg 20: [io  0x8480-0x848f]
[    0.368647] pci 0000:00:1f.2: reg 24: [io  0x8400-0x840f]
[    0.368682] pci 0000:00:1f.3: reg 10: [mem 0xf9fff400-0xf9fff4ff 64bit]
[    0.368692] pci 0000:00:1f.3: reg 20: [io  0x0400-0x041f]
[    0.368723] pci 0000:00:1f.5: reg 10: [io  0xa000-0xa007]
[    0.368727] pci 0000:00:1f.5: reg 14: [io  0x9c00-0x9c03]
[    0.368731] pci 0000:00:1f.5: reg 18: [io  0x9880-0x9887]
[    0.368736] pci 0000:00:1f.5: reg 1c: [io  0x9800-0x9803]
[    0.368740] pci 0000:00:1f.5: reg 20: [io  0x9480-0x948f]
[    0.368744] pci 0000:00:1f.5: reg 24: [io  0x9400-0x940f]
[    0.368798] pci 0000:01:00.0: reg 10: [mem 0xfd000000-0xfdffffff]
[    0.368805] pci 0000:01:00.0: reg 14: [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.368812] pci 0000:01:00.0: reg 1c: [mem 0xfa000000-0xfbffffff 64bit]
[    0.368816] pci 0000:01:00.0: reg 24: [io  0xbc00-0xbc7f]
[    0.368820] pci 0000:01:00.0: reg 30: [mem 0xfe8e0000-0xfe8fffff pref]
[    0.368854] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.368856] pci 0000:00:01.0:   bridge window [io  0xb000-0xbfff]
[    0.368859] pci 0000:00:01.0:   bridge window [mem 0xfa000000-0xfe8fffff]
[    0.368862] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.368892] pci 0000:00:1c.0: PCI bridge to [bus 04-04]
[    0.368895] pci 0000:00:1c.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.368898] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.368903] pci 0000:00:1c.0:   bridge window [mem 0xf8f00000-0xf8ffffff 64bit pref]
[    0.368960] pci 0000:03:00.0: reg 10: [io  0xdc00-0xdc07]
[    0.368967] pci 0000:03:00.0: reg 14: [io  0xd880-0xd883]
[    0.368973] pci 0000:03:00.0: reg 18: [io  0xd800-0xd807]
[    0.368979] pci 0000:03:00.0: reg 1c: [io  0xd480-0xd483]
[    0.368986] pci 0000:03:00.0: reg 20: [io  0xd400-0xd40f]
[    0.368992] pci 0000:03:00.0: reg 24: [mem 0xfeaffc00-0xfeafffff]
[    0.369027] pci 0000:03:00.0: supports D1
[    0.369028] pci 0000:03:00.0: PME# supported from D0 D1 D3hot
[    0.369032] pci 0000:03:00.0: PME# disabled
[    0.369046] pci 0000:03:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    0.369054] pci 0000:00:1c.4: PCI bridge to [bus 03-03]
[    0.369056] pci 0000:00:1c.4:   bridge window [io  0xd000-0xdfff]
[    0.369059] pci 0000:00:1c.4:   bridge window [mem 0xfea00000-0xfeafffff]
[    0.369064] pci 0000:00:1c.4:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.369126] pci 0000:02:00.0: reg 10: [mem 0xfe9c0000-0xfe9fffff 64bit]
[    0.369133] pci 0000:02:00.0: reg 18: [io  0xcc00-0xcc7f]
[    0.369183] pci 0000:02:00.0: PME# supported from D3hot D3cold
[    0.369187] pci 0000:02:00.0: PME# disabled
[    0.369205] pci 0000:02:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    0.369212] pci 0000:00:1c.5: PCI bridge to [bus 02-02]
[    0.369215] pci 0000:00:1c.5:   bridge window [io  0xc000-0xcfff]
[    0.369218] pci 0000:00:1c.5:   bridge window [mem 0xfe900000-0xfe9fffff]
[    0.369222] pci 0000:00:1c.5:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.369258] pci 0000:05:01.0: reg 10: [io  0xe800-0xe8ff]
[    0.369264] pci 0000:05:01.0: reg 14: [mem 0xfebffc00-0xfebffcff]
[    0.369301] pci 0000:05:01.0: supports D1 D2
[    0.369302] pci 0000:05:01.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.369305] pci 0000:05:01.0: PME# disabled
[    0.369329] pci 0000:05:02.0: reg 10: [mem 0xfebe0000-0xfebeffff]
[    0.369389] pci 0000:05:03.0: reg 10: [mem 0xfebfe000-0xfebfefff]
[    0.369426] pci 0000:05:03.0: supports D1 D2
[    0.369428] pci 0000:05:03.0: PME# supported from D0 D1 D2 D3hot
[    0.369431] pci 0000:05:03.0: PME# disabled
[    0.369466] pci 0000:00:1e.0: PCI bridge to [bus 05-05] (subtractive decode)
[    0.369469] pci 0000:00:1e.0:   bridge window [io  0xe000-0xefff]
[    0.369472] pci 0000:00:1e.0:   bridge window [mem 0xfeb00000-0xfebfffff]
[    0.369476] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.369478] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.369480] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.369481] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.369483] pci 0000:00:1e.0:   bridge window [mem 0x000d0000-0x000dffff] (subtractive decode)
[    0.369485] pci 0000:00:1e.0:   bridge window [mem 0xd0000000-0xdfffffff] (subtractive decode)
[    0.369486] pci 0000:00:1e.0:   bridge window [mem 0xf0000000-0xffffffff] (subtractive decode)
[    0.369504] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.369604] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P2._PRT]
[    0.369644] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.369724] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P8._PRT]
[    0.369761] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P9._PRT]
[    0.369820] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[    0.381646] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.381727] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.381805] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11 12 14 *15)
[    0.381884] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.381962] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.382043] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 *14 15)
[    0.382121] ACPI: PCI Interrupt Link [LNKG] (IRQs *3 4 5 6 7 10 11 12 14 15)
[    0.382198] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 *7 10 11 12 14 15)
[    0.382233] HEST: Table is not found!
[    0.382299] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.382302] vgaarb: loaded
[    0.382404] SCSI subsystem initialized
[    0.382470] libata version 3.00 loaded.
[    0.382509] usbcore: registered new interface driver usbfs
[    0.382517] usbcore: registered new interface driver hub
[    0.382533] usbcore: registered new device driver usb
[    0.382614] ACPI: WMI: Mapper loaded
[    0.382616] PCI: Using ACPI for IRQ routing
[    0.382618] PCI: pci_cache_line_size set to 64 bytes
[    0.382692] reserve RAM buffer: 000000000009f800 - 000000000009ffff 
[    0.382694] reserve RAM buffer: 00000000cff70000 - 00000000cfffffff 
[    0.382763] NetLabel: Initializing
[    0.382764] NetLabel:  domain hash size = 128
[    0.382765] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.382777] NetLabel:  unlabeled traffic allowed by default
[    0.382801] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
[    0.382805] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.382808] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
[    0.400026] Switching to clocksource tsc
[    0.406672] AppArmor: AppArmor Filesystem Enabled
[    0.406687] pnp: PnP ACPI init
[    0.406703] ACPI: bus type pnp registered
[    0.409002] pnp: PnP ACPI: found 17 devices
[    0.409004] ACPI: ACPI bus type pnp unregistered
[    0.409015] system 00:01: [mem 0xfed14000-0xfed19fff] has been reserved
[    0.409020] system 00:06: [io  0x0290-0x029f] has been reserved
[    0.409024] system 00:07: [io  0x04d0-0x04d1] has been reserved
[    0.409026] system 00:07: [io  0x0800-0x087f] has been reserved
[    0.409028] system 00:07: [io  0x0500-0x057f] could not be reserved
[    0.409030] system 00:07: [mem 0xfed08000-0xfed08fff] has been reserved
[    0.409032] system 00:07: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.409034] system 00:07: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.409036] system 00:07: [mem 0xfed50000-0xfed8ffff] has been reserved
[    0.409040] system 00:0a: [mem 0xffc00000-0xffefffff] has been reserved
[    0.409043] system 00:0c: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.409045] system 00:0c: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.409049] system 00:0f: [mem 0xe0000000-0xefffffff] has been reserved
[    0.409053] system 00:10: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.409054] system 00:10: [mem 0x000c0000-0x000cffff] has been reserved
[    0.409056] system 00:10: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.409058] system 00:10: [mem 0x00100000-0xcfffffff] could not be reserved
[    0.409060] system 00:10: [mem 0xe0000000-0xffffffff] could not be reserved
[    0.414575] pci 0000:00:1c.0: BAR 14: assigned [mem 0xf0000000-0xf03fffff]
[    0.414578] pci 0000:00:1c.4: BAR 15: assigned [mem 0xf0400000-0xf05fffff 64bit pref]
[    0.414581] pci 0000:00:1c.5: BAR 15: assigned [mem 0xf0600000-0xf07fffff 64bit pref]
[    0.414583] pci 0000:00:1c.0: BAR 13: assigned [io  0x1000-0x1fff]
[    0.414585] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.414587] pci 0000:00:01.0:   bridge window [io  0xb000-0xbfff]
[    0.414589] pci 0000:00:01.0:   bridge window [mem 0xfa000000-0xfe8fffff]
[    0.414591] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.414594] pci 0000:00:1c.0: PCI bridge to [bus 04-04]
[    0.414596] pci 0000:00:1c.0:   bridge window [io  0x1000-0x1fff]
[    0.414600] pci 0000:00:1c.0:   bridge window [mem 0xf0000000-0xf03fffff]
[    0.414603] pci 0000:00:1c.0:   bridge window [mem 0xf8f00000-0xf8ffffff 64bit pref]
[    0.414607] pci 0000:00:1c.4: PCI bridge to [bus 03-03]
[    0.414609] pci 0000:00:1c.4:   bridge window [io  0xd000-0xdfff]
[    0.414613] pci 0000:00:1c.4:   bridge window [mem 0xfea00000-0xfeafffff]
[    0.414616] pci 0000:00:1c.4:   bridge window [mem 0xf0400000-0xf05fffff 64bit pref]
[    0.414620] pci 0000:00:1c.5: PCI bridge to [bus 02-02]
[    0.414622] pci 0000:00:1c.5:   bridge window [io  0xc000-0xcfff]
[    0.414625] pci 0000:00:1c.5:   bridge window [mem 0xfe900000-0xfe9fffff]
[    0.414628] pci 0000:00:1c.5:   bridge window [mem 0xf0600000-0xf07fffff 64bit pref]
[    0.414633] pci 0000:00:1e.0: PCI bridge to [bus 05-05]
[    0.414635] pci 0000:00:1e.0:   bridge window [io  0xe000-0xefff]
[    0.414639] pci 0000:00:1e.0:   bridge window [mem 0xfeb00000-0xfebfffff]
[    0.414641] pci 0000:00:1e.0:   bridge window [mem pref disabled]
[    0.414651]   alloc irq_desc for 16 on node -1
[    0.414653]   alloc kstat_irqs on node -1
[    0.414657] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.414660] pci 0000:00:01.0: setting latency timer to 64
[    0.414665] pci 0000:00:1c.0: enabling device (0106 -> 0107)
[    0.414668]   alloc irq_desc for 17 on node -1
[    0.414669]   alloc kstat_irqs on node -1
[    0.414672] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.414675] pci 0000:00:1c.0: setting latency timer to 64
[    0.414680] pci 0000:00:1c.4: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.414683] pci 0000:00:1c.4: setting latency timer to 64
[    0.414689] pci 0000:00:1c.5: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.414692] pci 0000:00:1c.5: setting latency timer to 64
[    0.414697] pci 0000:00:1e.0: setting latency timer to 64
[    0.414700] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.414701] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.414703] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.414704] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
[    0.414706] pci_bus 0000:00: resource 8 [mem 0xd0000000-0xdfffffff]
[    0.414708] pci_bus 0000:00: resource 9 [mem 0xf0000000-0xffffffff]
[    0.414709] pci_bus 0000:01: resource 0 [io  0xb000-0xbfff]
[    0.414711] pci_bus 0000:01: resource 1 [mem 0xfa000000-0xfe8fffff]
[    0.414712] pci_bus 0000:01: resource 2 [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.414714] pci_bus 0000:04: resource 0 [io  0x1000-0x1fff]
[    0.414716] pci_bus 0000:04: resource 1 [mem 0xf0000000-0xf03fffff]
[    0.414717] pci_bus 0000:04: resource 2 [mem 0xf8f00000-0xf8ffffff 64bit pref]
[    0.414719] pci_bus 0000:03: resource 0 [io  0xd000-0xdfff]
[    0.414720] pci_bus 0000:03: resource 1 [mem 0xfea00000-0xfeafffff]
[    0.414722] pci_bus 0000:03: resource 2 [mem 0xf0400000-0xf05fffff 64bit pref]
[    0.414724] pci_bus 0000:02: resource 0 [io  0xc000-0xcfff]
[    0.414725] pci_bus 0000:02: resource 1 [mem 0xfe900000-0xfe9fffff]
[    0.414727] pci_bus 0000:02: resource 2 [mem 0xf0600000-0xf07fffff 64bit pref]
[    0.414728] pci_bus 0000:05: resource 0 [io  0xe000-0xefff]
[    0.414730] pci_bus 0000:05: resource 1 [mem 0xfeb00000-0xfebfffff]
[    0.414731] pci_bus 0000:05: resource 4 [io  0x0000-0x0cf7]
[    0.414733] pci_bus 0000:05: resource 5 [io  0x0d00-0xffff]
[    0.414734] pci_bus 0000:05: resource 6 [mem 0x000a0000-0x000bffff]
[    0.414735] pci_bus 0000:05: resource 7 [mem 0x000d0000-0x000dffff]
[    0.414737] pci_bus 0000:05: resource 8 [mem 0xd0000000-0xdfffffff]
[    0.414738] pci_bus 0000:05: resource 9 [mem 0xf0000000-0xffffffff]
[    0.414765] NET: Registered protocol family 2
[    0.414874] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.415747] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.418904] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.419319] TCP: Hash tables configured (established 524288 bind 65536)
[    0.419321] TCP reno registered
[    0.419330] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[    0.419361] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    0.419480] NET: Registered protocol family 1
[    0.419638] pci 0000:01:00.0: Boot video device
[    0.419651] PCI: CLS 32 bytes, default 64
[    0.419653] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.419655] Placing 64MB software IO TLB between ffff880001f9e000 - ffff880005f9e000
[    0.419656] software IO TLB at phys 0x1f9e000 - 0x5f9e000
[    0.419818] Scanning for low memory corruption every 60 seconds
[    0.419925] audit: initializing netlink socket (disabled)
[    0.419938] type=2000 audit(1289219772.410:1): initialized
[    0.429657] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.430619] VFS: Disk quotas dquot_6.5.2
[    0.430658] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.431056] fuse init (API version 7.14)
[    0.431110] msgmni has been set to 7896
[    0.432125] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.432128] io scheduler noop registered
[    0.432129] io scheduler deadline registered
[    0.432153] io scheduler cfq registered (default)
[    0.432232] pcieport 0000:00:01.0: setting latency timer to 64
[    0.432249]   alloc irq_desc for 40 on node -1
[    0.432250]   alloc kstat_irqs on node -1
[    0.432257] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
[    0.432295] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.432318]   alloc irq_desc for 41 on node -1
[    0.432319]   alloc kstat_irqs on node -1
[    0.432324] pcieport 0000:00:1c.0: irq 41 for MSI/MSI-X
[    0.432380] pcieport 0000:00:1c.4: setting latency timer to 64
[    0.432406]   alloc irq_desc for 42 on node -1
[    0.432407]   alloc kstat_irqs on node -1
[    0.432412] pcieport 0000:00:1c.4: irq 42 for MSI/MSI-X
[    0.432467] pcieport 0000:00:1c.5: setting latency timer to 64
[    0.432489]   alloc irq_desc for 43 on node -1
[    0.432491]   alloc kstat_irqs on node -1
[    0.432495] pcieport 0000:00:1c.5: irq 43 for MSI/MSI-X
[    0.432560] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.432626] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.432679] intel_idle: MWAIT substates: 0x22220
[    0.432680] intel_idle: does not run on family 6 model 23
[    0.432757] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.432761] ACPI: Power Button [PWRB]
[    0.432791] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.432793] ACPI: Power Button [PWRF]
[    0.432975] ACPI: acpi_idle registered with cpuidle
[    0.434759] ERST: Table is not found!
[    0.434896] Linux agpgart interface v0.103
[    0.434911] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.434996] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.435260] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.436014] brd: module loaded
[    0.436337] loop: module loaded
[    0.436443] ata_piix 0000:00:1f.2: version 2.13
[    0.436455]   alloc irq_desc for 19 on node -1
[    0.436457]   alloc kstat_irqs on node -1
[    0.436462] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.436466] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    0.436495] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.436549] scsi0 : ata_piix
[    0.436595] scsi1 : ata_piix
[    0.437592] ata1: SATA max UDMA/133 cmd 0x9000 ctl 0x8c00 bmdma 0x8480 irq 19
[    0.437596] ata2: SATA max UDMA/133 cmd 0x8880 ctl 0x8800 bmdma 0x8488 irq 19
[    0.437611] ata_piix 0000:00:1f.5: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.437614] ata_piix 0000:00:1f.5: MAP [ P0 -- P1 -- ]
[    0.437641] ata_piix 0000:00:1f.5: setting latency timer to 64
[    0.437676] scsi2 : ata_piix
[    0.437738] scsi3 : ata_piix
[    0.438629] ata3: SATA max UDMA/133 cmd 0xa000 ctl 0x9c00 bmdma 0x9480 irq 19
[    0.438632] ata4: SATA max UDMA/133 cmd 0x9880 ctl 0x9800 bmdma 0x9488 irq 19
[    0.438665] pata_acpi 0000:03:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.438684] pata_acpi 0000:03:00.0: setting latency timer to 64
[    0.438693] pata_acpi 0000:03:00.0: PCI INT A disabled
[    0.438866] Fixed MDIO Bus: probed
[    0.438889] PPP generic driver version 2.4.2
[    0.438911] tun: Universal TUN/TAP device driver, 1.6
[    0.438912] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.438966] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.438978]   alloc irq_desc for 18 on node -1
[    0.438979]   alloc kstat_irqs on node -1
[    0.438982] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.438994] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    0.438996] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    0.439019] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    0.439040] ehci_hcd 0000:00:1a.7: debug port 1
[    0.442941] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    0.442951] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xf9fffc00
[    0.459978] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    0.460090] hub 1-0:1.0: USB hub found
[    0.460094] hub 1-0:1.0: 6 ports detected
[    0.460160]   alloc irq_desc for 23 on node -1
[    0.460162]   alloc kstat_irqs on node -1
[    0.460167] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.460188] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.460190] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.460221] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    0.460243] ehci_hcd 0000:00:1d.7: debug port 1
[    0.464118] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.464134] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf9fff800
[    0.479584] Freeing initrd memory: 10752k freed
[    0.479973] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.480136] hub 2-0:1.0: USB hub found
[    0.480142] hub 2-0:1.0: 6 ports detected
[    0.480222] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.480239] uhci_hcd: USB Universal Host Controller Interface driver
[    0.480331] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.480340] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.480343] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    0.480378] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    0.480421] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000a800
[    0.480518] hub 3-0:1.0: USB hub found
[    0.480522] hub 3-0:1.0: 2 ports detected
[    0.480569]   alloc irq_desc for 21 on node -1
[    0.480570]   alloc kstat_irqs on node -1
[    0.480578] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.480583] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    0.480585] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    0.480616] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    0.480647] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000a880
[    0.480734] hub 4-0:1.0: USB hub found
[    0.480737] hub 4-0:1.0: 2 ports detected
[    0.480784] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.480789] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    0.480791] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    0.480819] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
[    0.480841] uhci_hcd 0000:00:1a.2: irq 18, io base 0x0000ac00
[    0.480930] hub 5-0:1.0: USB hub found
[    0.480936] hub 5-0:1.0: 2 ports detected
[    0.480985] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.480989] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.480992] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.481017] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
[    0.481038] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000a080
[    0.481139] hub 6-0:1.0: USB hub found
[    0.481142] hub 6-0:1.0: 2 ports detected
[    0.481186] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.481191] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.481193] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.481219] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
[    0.481241] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000a400
[    0.481336] hub 7-0:1.0: USB hub found
[    0.481339] hub 7-0:1.0: 2 ports detected
[    0.481382] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.481386] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.481389] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.481418] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
[    0.481438] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000a480
[    0.481528] hub 8-0:1.0: USB hub found
[    0.481534] hub 8-0:1.0: 2 ports detected
[    0.481644] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    0.484201] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.484206] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.484288] mice: PS/2 mouse device common for all mice
[    0.484369] rtc_cmos 00:03: RTC can wake from S4
[    0.484401] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.484422] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.484511] device-mapper: uevent: version 1.0.3
[    0.484585] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: dm-devel@redhat.com
[    0.484635] device-mapper: multipath: version 1.1.1 loaded
[    0.484638] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.484743] cpuidle: using governor ladder
[    0.484744] cpuidle: using governor menu
[    0.484933] TCP cubic registered
[    0.485017] NET: Registered protocol family 10
[    0.485261] lo: Disabled Privacy Extensions
[    0.485386] NET: Registered protocol family 17
[    0.485473] PM: Resume from disk failed.
[    0.485483] registered taskstats version 1
[    0.485738]   Magic number: 2:484:632
[    0.485833] rtc_cmos 00:03: setting system clock to 2010-11-08 12:36:13 UTC (1289219773)
[    0.485835] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.485836] EDD information not available.
[    0.503414] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    0.800587] ata4: SATA link down (SStatus 0 SControl 300)
[    0.800623] usb 2-1: new high speed USB device using ehci_hcd and address 2
[    0.959968] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    0.980050] ata3.00: ATAPI: TSSTcorp CDDVDW SH-S203D, SB00, max UDMA/100
[    1.020127] ata3.00: configured for UDMA/100
[    1.140616] ata1.00: SATA link down (SStatus 0 SControl 300)
[    1.140627] ata1.01: SATA link down (SStatus 0 SControl 300)
[    1.310052] ata2.00: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.310064] ata2.01: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.350119] ata2.00: ATAPI: TSSTcorp CDDVDW SH-S203P, SB00, max UDMA/100
[    1.350220] ata2.01: ATA-7: SAMSUNG HD103UJ, 1AA01112, max UDMA7
[    1.350223] ata2.01: 1953525168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.360008] usb 7-1: new full speed USB device using uhci_hcd and address 2
[    1.390127] ata2.00: configured for UDMA/100
[    1.410216] ata2.01: configured for UDMA/133
[    1.411306] scsi 1:0:0:0: CD-ROM            TSSTcorp CDDVDW SH-S203P  SB00 PQ: 0 ANSI: 5
[    1.415066] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.415069] Uniform CD-ROM driver Revision: 3.20
[    1.415170] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.415202] sr 1:0:0:0: Attached scsi generic sg0 type 5
[    1.415275] scsi 1:0:1:0: Direct-Access     ATA      SAMSUNG HD103UJ  1AA0 PQ: 0 ANSI: 5
[    1.415344] sd 1:0:1:0: [sda] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    1.415351] sd 1:0:1:0: Attached scsi generic sg1 type 0
[    1.415384] sd 1:0:1:0: [sda] Write Protect is off
[    1.415386] sd 1:0:1:0: [sda] Mode Sense: 00 3a 00 00
[    1.415402] sd 1:0:1:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.415503]  sda:
[    1.415976] scsi 2:0:0:0: CD-ROM            TSSTcorp CDDVDW SH-S203D  SB00 PQ: 0 ANSI: 5
[    1.417994] sr1: scsi3-mmc drive: 16x/16x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.418064] sr 2:0:0:0: Attached scsi CD-ROM sr1
[    1.418100] sr 2:0:0:0: Attached scsi generic sg2 type 5
[    1.429056]  sda1 sda2 sda3 < sda5 sda6 > sda4
[    1.458085] sd 1:0:1:0: [sda] Attached SCSI disk
[    1.458100] Freeing unused kernel memory: 908k freed
[    1.458345] Write protecting the kernel read-only data: 10240k
[    1.458462] Freeing unused kernel memory: 416k freed
[    1.458661] Freeing unused kernel memory: 1644k freed
[    1.468370] udev[82]: starting version 163
[    1.511106] ATL1E 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.511117] ATL1E 0000:02:00.0: setting latency timer to 64
[    1.528682] ahci 0000:03:00.0: version 3.0
[    1.529510] pata_marvell 0000:03:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.529537] pata_marvell 0000:03:00.0: setting latency timer to 64
[    1.534942] firewire_ohci 0000:05:03.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.535017] via-rhine.c:v1.10-LK1.4.3 2007-03-06 Written by Donald Becker
[    1.545000] scsi4 : pata_marvell
[    1.549388] Initializing USB Mass Storage driver...
[    1.554765] scsi5 : pata_marvell
[    1.554803] ata5: PATA max UDMA/100 cmd 0xdc00 ctl 0xd880 bmdma 0xd400 irq 16
[    1.554806] ata6: PATA max UDMA/133 cmd 0xd800 ctl 0xd480 bmdma 0xd408 irq 16
[    1.559331] scsi6 : usb-storage 2-1:1.0
[    1.559425] usbcore: registered new interface driver usb-storage
[    1.559427] USB Mass Storage support registered.
[    1.670012] firewire_ohci: Added fw-ohci device 0000:05:03.0, OHCI v1.0, 8 IR + 8 IT contexts, quirks 0x0
[    1.670040] via-rhine 0000:05:01.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.675608] eth1: VIA Rhine III at 0xfebffc00, 00:22:b0:dc:b3:76, IRQ 17.
[    1.676319] eth1: MII PHY found at address 1, status 0x786d advertising 05e1 Link 41e1.
[    1.871412] EXT3-fs: barriers not enabled
[    1.880708] kjournald starting.  Commit interval 5 seconds
[    1.880727] EXT3-fs (sda4): mounted filesystem with ordered data mode
[    2.151342] firewire_core: created device fw0: GUID 001e8c0001549458, S400
[    2.551562] scsi 6:0:0:0: Direct-Access              USB FLASH DRIVE  34CH PQ: 0 ANSI: 0 CCS
[    2.551848] sd 6:0:0:0: Attached scsi generic sg3 type 0
[    2.552426] sd 6:0:0:0: [sdb] 2015232 512-byte logical blocks: (1.03 GB/984 MiB)
[    2.552922] sd 6:0:0:0: [sdb] Write Protect is off
[    2.552925] sd 6:0:0:0: [sdb] Mode Sense: 23 00 00 00
[    2.552927] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[    2.554921] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[    2.554926]  sdb: sdb1
[    2.556182] sdb: p1 size 2015937 extends beyond EOD, enabling native capacity
[    2.557295] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[    2.557299]  sdb: sdb1
[    2.558553] sdb: p1 size 2015937 extends beyond EOD, truncated
[    2.559796] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[    2.559799] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[   28.410906] udev[388]: starting version 163
[   28.567980] lp: driver loaded but no devices found
[   28.591182] udev[402]: renamed network interface eth1 to eth2
[   28.599804] WARNING! power/level is deprecated; use power/control instead
[   28.627029] type=1400 audit(1289212601.633:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=674 comm="apparmor_parser"
[   28.627492] type=1400 audit(1289212601.633:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=674 comm="apparmor_parser"
[   28.627739] type=1400 audit(1289212601.633:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=674 comm="apparmor_parser"
[   28.635477] rt2860 0000:05:02.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   28.635645] 
[   28.635646] 
[   28.635646] === pAd = ffffc90011d8f000, size = 576720 ===
[   28.635647] 
[   28.635665] <-- RTMPAllocTxRxRingMemory, Status=0
[   28.635702] <-- RTMPAllocAdapterBlock, Status=0
[   28.635704] pAd->CSRBaseAddress =0xffffc90011f00000, csr_addr=0xffffc90011f00000!
[   28.659031] nvidia: module license 'NVIDIA' taints kernel.
[   28.659034] Disabling lock debugging due to kernel taint
[   28.664466] w83627ehf: Found W83667HG chip at 0x290
[   28.664665] ACPI: resource w83627ehf [io  0x0295-0x0296] conflicts with ACPI region HWRE [io  0x0290-0x0299 64bit pref]
[   28.664667] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   28.702544]   alloc irq_desc for 22 on node -1
[   28.702547]   alloc kstat_irqs on node -1
[   28.702553] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   28.702599]   alloc irq_desc for 44 on node -1
[   28.702600]   alloc kstat_irqs on node -1
[   28.702607] HDA Intel 0000:00:1b.0: irq 44 for MSI/MSI-X
[   28.702628] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   29.258465] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input3
[   29.282199] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   29.282205] nvidia 0000:01:00.0: setting latency timer to 64
[   29.282210] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   29.282319] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  260.19.06  Mon Sep 13 04:29:19 PDT 2010
[   29.304524] w83627ehf: Found W83667HG chip at 0x290
[   29.304648] ACPI: resource w83627ehf [io  0x0295-0x0296] conflicts with ACPI region HWRE [io  0x0290-0x0299 64bit pref]
[   29.304650] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   29.638223] EXT3-fs (sda4): using internal journal
[   30.291688]   alloc irq_desc for 45 on node -1
[   30.291690]   alloc kstat_irqs on node -1
[   30.291704] ATL1E 0000:02:00.0: irq 45 for MSI/MSI-X
[   30.292090] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   30.294769] eth2: link up, 100Mbps, full-duplex, lpa 0x41E1
[   30.299568] RX DESC ffff8800cf849000  size = 2048
[   30.305369] type=1400 audit(1289212603.313:5): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=1063 comm="apparmor_parser"
[   30.305399] type=1400 audit(1289212603.313:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=1064 comm="apparmor_parser"
[   30.305848] type=1400 audit(1289212603.313:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1064 comm="apparmor_parser"
[   30.306095] type=1400 audit(1289212603.313:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1064 comm="apparmor_parser"
[   30.307455] type=1400 audit(1289212603.313:9): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=1065 comm="apparmor_parser"
[   30.307720] type=1400 audit(1289212603.313:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=1067 comm="apparmor_parser"
[   30.308266] type=1400 audit(1289212603.313:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=1067 comm="apparmor_parser"
[   30.357368] 1. Phy Mode = 5
[   30.357370] 2. Phy Mode = 5
[   30.357372] NVM is Efuse and its size =3c[3c0-3fb] 
[   30.358015] phy mode> Error! The chip does not support 5G band 8!
[   30.358066] RTMPSetPhyMode: channel is out of range, use first channel=1 
[   30.360452] 3. Phy Mode = 9
[   30.379594] MCS Set = ff 00 00 00 01
[   30.379596] <==== rt28xx_init, Status=0
[   30.379657] 0x1300 = 00064300
[   30.421042] RX DESC ffff8800cf849000  size = 2048
[   30.424262] CfgSetCountryRegion():CountryRegion in eeprom was programmed
[   30.424268] CfgSetCountryRegion():CountryRegion in eeprom was programmed
[   30.425086] 1. Phy Mode = 5
[   30.425087] 2. Phy Mode = 5
[   30.425089] NVM is Efuse and its size =3c[3c0-3fb] 
[   30.425742] phy mode> Error! The chip does not support 5G band 8!
[   30.425779] RTMPSetPhyMode: channel is out of range, use first channel=1 
[   30.428140] 3. Phy Mode = 9
[   30.447349] MCS Set = ff 00 00 00 01
[   30.447352] <==== rt28xx_init, Status=0
[   30.447415] 0x1300 = 00064300
[   30.522498] ppdev: user-space parallel port driver
[   31.719248] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   31.719251] vboxdrv: Warning: 2.6.31+ kernel detected. Most likely the hardware performance
[   31.719252] vboxdrv: counter framework which can generate NMIs is active. You have to prevent
[   31.719253] vboxdrv: the usage of hardware performance counters by
[   31.719254] vboxdrv:   echo 2 > /proc/sys/kernel/perf_counter_paranoid
[   31.719256] vboxdrv: Found 2 processor cores.
[   31.719414] VBoxDrv: dbg - g_abExecMemory=ffffffffa0dddd60
[   31.719425] vboxdrv: fAsync=0 offMin=0x1e5 offMax=0x1f35
[   31.719897] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   31.719899] vboxdrv: Successfully loaded version 3.2.8 (interface 0x00140001).
[   37.115513] UDF-fs: No VRS found
[   37.115517] UDF-fs: No partition found (1)
[   37.191652] ISO 9660 Extensions: Microsoft Joliet Level 3
[   37.233317] ISOFS: changing to secondary root
[   40.321257] eth2: no IPv6 routers present
[   40.880005] ra0: no IPv6 routers present
```Most of all now I interest why iwconfig show ESSID="" (empty!) while in RT2860STA.dat it's not empty.
P.S. I'm still not able to establish any connection...

---

### Post by sukharevd on 2010-11-09
Everything has changed dramatically. After some actions my  adapter can see another networks. Moreover when it creates connection to  some network my netbook with windows with automatic establishment of  connection establishes it! BUT finally Ubuntu can't finish establishment  of connection, it just asks password endlessly and/or just says that  wireless network was disabled :sad:
So everything changed but I still can't use the network.

Please, help me finish setting up my adapter!

-------------------------------------------
Below is a new full info set:
**1.Machine Brand and Model**:
```
PC: Intel Core 2 Duo E8500, P5Q, 4GB, 8600GT
WiFi adapter: DLink DWA-525 (with driver from Ralink)
```**2.Wireless Brand, Model and Wireless Chipset:**
```
dmitriy@dmitriy-desktop:~$ lspci -nn | grep 'RaLink'
05:02.0 Network controller [0280]: RaLink Device [1814:3060]

```**3.check interface:**
```
dmitriy@dmitriy-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:22:15:2c:cb:ea  
          inet6 addr: fe80::222:15ff:fe2c:cbea/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34 errors:0 dropped:0 overruns:0 carrier:3
          collisions:0 txqueuelen:1000 
          RX bytes:823 (823.0 B)  TX bytes:6785 (6.7 KB)
          Interrupt:28 

eth2      Link encap:Ethernet  HWaddr 00:22:b0:dc:b3:76  
          inet addr:188.231.187.9  Bcast:188.231.187.255  Mask:255.255.255.0
          inet6 addr: fec0::a:222:b0ff:fedc:b376/64 Scope:Site
          inet6 addr: 2002:bce7:9031:a:222:b0ff:fedc:b376/64 Scope:Global
          inet6 addr: fe80::222:b0ff:fedc:b376/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:156494 errors:0 dropped:0 overruns:0 frame:0
          TX packets:23645 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:54056695 (54.0 MB)  TX bytes:3293008 (3.2 MB)
          Interrupt:17 Base address:0xec00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4302 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4302 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:964683 (964.6 KB)  TX bytes:964683 (964.6 KB)

ra0       Link encap:Ethernet  HWaddr 1c:bd:b9:8c:07:99  
          inet6 addr: fe80::1ebd:b9ff:fe8c:799/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:3055 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15171 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:244905 (244.9 KB)  TX bytes:35716 (35.7 KB)
          Interrupt:18 
``````
dmitriy@dmitriy-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth2      no wireless extensions.

ra0       Ralink STA  ESSID:""  Nickname:"RT3562STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=100/100  Signal level:0 dBm  Noise level:0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

vboxnet0  no wireless extensions.

```**4.Check for modules:**
```
dmitriy@dmitriy-desktop:~$ lsmod | grep "rt3562sta"
rt3562sta            1007507  1 
```**5.Kernel boot messages**
```
it's in attachment and there are several
"**ERROR!!! RTMPSetTimer failed, Halt in Progress!**",
looks not good, but I don't know what is it.
```**6.Network configuration**
```
dmitriy@dmitriy-desktop:~$ sudo lshw -C network
[sudo] password for dmitriy: 
  *-network               
       description: Ethernet interface
       product: AR8121/AR8113/AR8114 Gigabit or Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: b0
       serial: 00:22:15:2c:cb:ea
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet  physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=ATL1E  driverversion=1.0.0.7-NAPI firmware=L1e latency=0 link=no multicast=yes  port=twisted pair
       resources: irq:28 memory:fe9c0000-fe9fffff ioport:cc00(size=128)
  *-network:0
       description: Ethernet interface
       product: VT6105/VT6106S [Rhine-III]
       vendor: VIA Technologies, Inc.
       physical id: 1
       bus info: pci@0000:05:01.0
       logical name: eth2
       version: 8b
       serial: 00:22:b0:dc:b3:76
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine  driverversion=1.4.3 duplex=full ip=188.231.187.9 latency=64 link=yes  maxlatency=8 mingnt=3 multicast=yes port=MII speed=100MB/s
       resources: irq:17 ioport:e800(size=256) memory:febffc00-febffcff
  *-network:1
       description: Wireless interface
       product: RaLink
       vendor: RaLink
       physical id: 2
       bus info: pci@0000:05:02.0
       logical name: ra0
       version: 00
       serial: 1c:bd:b9:8c:07:99
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=RALINK WLAN  driverversion=2.4.0.0 latency=64 maxlatency=4 mingnt=2 multicast=yes  wireless=Ralink STA
       resources: irq:18 memory:febe0000-febeffff
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
```**7.Scan for networks:**
```
dmitriy@dmitriy-desktop:~$ iwlist ra0 scanning
ra0       Scan completed :
          Cell 01 - Address: 02:E0:C7:DE:A3:D3
                    Protocol:802.11g
                    ESSID:"con2"
                    Mode:Ad-Hoc
                    Frequency:2.457 GHz (Channel 10)
                    Quality:100/100  Signal level:-43 dBm  Noise level:-92 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s

```[B]8.Ubuntu Version:
[/B]```
dmitriy@dmitriy-desktop:~$ sudo lsb_release -d
Description:    Ubuntu 10.10

```[B]9.Kernel/architecture (including 32 vs. 64 bit):
[/B]```
dmitriy@dmitriy-desktop:~$ uname -mr
2.6.32-25-generic x86_64

```**10.Restarting the network:**
```
dmitriy@dmitriy-desktop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          Ignoring unknown interface eth2=eth2.
                                                                         [ OK ]
```

---

### Post by sukharevd on 2010-11-10
I achieved next level! :) Yesterday I connected my notebook with desktop. The most tricky thing is that I had to create new connection with adhoc WEP security level, set manual mode of getting IP and input IP, clicked 'Connect to hired wireless network' and chose created network; just after this I had to organize connection establishment on the second machine. Only in this way I can now link my machines. If one of them loose connection I have to break down another and start all again. So there is no such thing as autoconnection. I can make them exchanged big piece of data, BUT response time is very huge, every fourth ping ejected. Moreover I cannot choose DHCP (sharing) mode of IP obtaining in this network because it doesn't work after this :(
Another very strange thing is that adapter doesn't see any connections except that ones which were created by me (in both(!) ubuntu and windows). All my neighbours' network visible for my netbook and aren't visible for desktop (which is with DWA-525).

IF YOU have a problem with establishment of connection try to do it how did I describe above.

---

### Post by sukharevd on 2010-11-10
My question now is how to organize sharing of internet using static IPs (and not "shared to other computers" mode)? What I have now are: Ethernet connection with internet and my wireless connection to share notebook internet. Is there a way to do it???

Alternatively maybe there are some way to enable DHCP in my case??? (how I noticed by simply choosing "shared to others" wifi doesn't work at all now)

---

### Post by uncaspi on 2010-11-10
I read a thread erlier today about endlessly polling for password. The solution was to give the password located under the router box. If connection where established it will never ask again.

---

### Post by sukharevd on 2010-11-10
> **uncaspi said:**
> I read a thread erlier today about endlessly polling for password. The solution was to give the password located under the router box. If connection where established it will never ask again.
What do you mean by "located under the router box"?
By the way I have no router... But I copied that you have :)

---

### Post by uncaspi on 2010-11-10
Is it a ad-hoc lan with several machines to are trying to do?

---

### Post by sukharevd on 2010-11-10
Yes, it's network of two machines: my desktop (Ubuntu, DWA-525 adapter) and my netbook (Windows XP); mode of connection is Adhoc.

---

### Post by suchathrill on 2010-12-19
im able to connect to a netgeer wnr2000 wireless router with my rt2860 card that's in my newer quadcore HP desktop, but...

i cant connect to my dlink dir-615 wireless routher with the same ***puter


i can connect to each router with my laptop which has a differen wifi card and is running the same version of ubuntu 10.04LTS

---

### Post by sukharevd on 2011-05-22
Still have no much success :(
I did everything like they say to do (say, [here]("http://xenstreet.com/2011/02/installing-dlink-dwa-525-linux-drivers.html")), just after installation and rebooting everything worked, but after a while connection became unstable. Only the forth part of pings succeeded, I could "connect to server" using this adapter only for the third time. Requests in browser works rarely as well. I've just tried to copy files (~3GB) via network, only 1.2 was copied, then I had a message
Error while copying "VTS_02_2.VOB".
Connection timed out
And now, just after that, all 4 pings succeeded. I don't understand what's wrong with this adapter and how the others could make it worked...

I want to emphasise that I'm trying to create wifi network between desktop and netbook WITHOUT ROUTER. There is Windows XP at netbook. Also I did downgrade at desktop to Ubuntu **10.04**.
And once more this adapter works in Windows 7.
[B]
Any ideas how-to solve this problem?[/B]

-------------------------------------------
Below is a new full info set:
**1.Machine Brand and Model**:
```
PC: Intel Core 2 Duo E8500, P5Q, 6GB, 8600GT
WiFi adapter: DLink DWA-525 (with driver from Ralink)
```**2.Wireless Brand, Model and Wireless Chipset:**
```
dmitriy@dmitriy-desktop:~$ lspci -nn | grep 'RaLink'
05:02.0 Network controller [0280]: RaLink Device [1814:3060]

```**3.check interface:**
```
dmitriy@dmitriy-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:22:b0:dc:b3:76  
          inet addr:188.231.187.9  Bcast:188.231.187.255  Mask:255.255.255.0
          inet6 addr: fec0::b:222:b0ff:fedc:b376/64 Scope:Site
          inet6 addr: 2002:bce7:bbf0:b:222:b0ff:fedc:b376/64 Scope:Global
          inet6 addr: fe80::222:b0ff:fedc:b376/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:147240 errors:0 dropped:0 overruns:0 frame:0
          TX packets:33626 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:75326827 (75.3 MB)  TX bytes:3754442 (3.7 MB)
          Interrupt:17 Base address:0xec00 

eth1      Link encap:Ethernet  HWaddr 00:22:15:2c:cb:ea  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:28 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:11335 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11335 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6124564 (6.1 MB)  TX bytes:6124564 (6.1 MB)

ra0       Link encap:Ethernet  HWaddr 1c:bd:b9:8c:07:99  
          inet addr:10.42.43.1  Bcast:10.42.43.255  Mask:255.255.255.0
          inet6 addr: fe80::1ebd:b9ff:fe8c:799/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:513494 errors:0 dropped:0 overruns:0 frame:0
          TX packets:947285 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:45745687 (45.7 MB)  TX bytes:1415340325 (1.4 GB)
          Interrupt:18 
``````
dmitriy@dmitriy-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

ra0       Ralink STA  ESSID:""  Nickname:"RT3562STA"
          Mode:Ad-Hoc  Frequency=2.457 GHz  Cell: CA:43:EA:29:EC:FB   
          Bit Rate=1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=100/100  Signal level:-47 dBm  Noise level:-115 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

vboxnet0  no wireless extensions.

```**4.Check for modules:**
```
dmitriy@dmitriy-desktop:~$ lsmod | grep "rt3562sta"
rt3562sta             975362  1 
```**5.Kernel boot messages**
Skipped.
**6.Network configuration**
```
dmitriy@dmitriy-desktop:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: Atheros AR8121/AR8113/AR8114 PCI-E Ethernet Controller
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth1
       version: b0
       serial: 00:22:15:2c:cb:ea
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=ATL1E driverversion=1.0.0.7-NAPI firmware=L1e latency=0 link=no multicast=yes port=twisted pair
       resources: irq:28 memory:fe9c0000-fe9fffff ioport:cc00(size=128)
  *-network:0
       description: Ethernet interface
       product: VT6105/VT6106S [Rhine-III]
       vendor: VIA Technologies, Inc.
       physical id: 1
       bus info: pci@0000:05:01.0
       logical name: eth0
       version: 8b
       serial: 00:22:b0:dc:b3:76
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=full ip=188.231.187.9 latency=64 link=yes maxlatency=8 mingnt=3 multicast=yes port=MII speed=100MB/s
       resources: irq:17 ioport:e800(size=256) memory:febffc00-febffcff
  *-network:1
       description: Wireless interface
       product: RaLink
       vendor: RaLink
       physical id: 2
       bus info: pci@0000:05:02.0
       logical name: ra0
       version: 00
       serial: 1c:bd:b9:8c:07:99
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=RALINK WLAN driverversion=2.3.0.0-alpha20100128 ip=10.42.43.1 latency=64 maxlatency=4 mingnt=2 multicast=yes wireless=Ralink STA
       resources: irq:18 memory:febe0000-febeffff
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes

```**7.Scan for networks:**
```
dmitriy@dmitriy-desktop:~$ iwlist ra0 scanning
ra0       Scan completed :
          Cell 01 - Address: CA:43:EA:29:EC:FB
                    Protocol:802.11b/g
                    ESSID:"dmitriyNet"
                    Mode:Ad-Hoc
                    Frequency:2.457 GHz (Channel 10)
                    Quality:83/100  Signal level:-57 dBm  Noise level:-92 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s


```[B]8.Ubuntu Version:
[/B]```
dmitriy@dmitriy-desktop:~$ sudo lsb_release -d
Description:    Ubuntu 10.04.2 LTS

```[B]9.Kernel/architecture (including 32 vs. 64 bit):
[/B]```
dmitriy@dmitriy-desktop:~$ uname -mr
2.6.32-31-generic x86_64

```

---

### Post by philipg on 2011-05-23
have a look at [http://ubuntuforums.org/showthread.php?t=1635039](http://ubuntuforums.org/showthread.php?t=1635039)
and [http://www.ubuntugeek.com/creating-an-adhoc-host-with-ubuntu.html](http://www.ubuntugeek.com/creating-an-adhoc-host-with-ubuntu.html)

---

### Post by sukharevd on 2011-05-23
It looks like I did the same steps that are at the first link (except I don't have a router, so I didn't customise it). And the second link isn't about internet sharing.

But idea is the same. I set "Share internet connection" in Ubuntu and ip-address 10.42.43.* in Windows XP.

---

