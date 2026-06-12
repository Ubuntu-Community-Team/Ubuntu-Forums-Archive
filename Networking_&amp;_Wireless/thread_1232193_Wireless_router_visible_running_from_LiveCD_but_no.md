---
title: "Wireless router visible running from LiveCD but not while running installed system"
date: 2009-08-05
forum: Networking &amp; Wireless
---

### Post by Scol-R-LEA on 2009-08-05
I am having a rather peculiar issue with wireless connectivity in fresh installation of Jaunty on an older desktop PC. On starting the system following a smooth installation, I found that the wireless connection could not see the router I have set up in my location, though it could see other access points in the area (which I do not have permissions for). Since I was able to detect and connect to the router while running from the LiveCD on the same system, it does not appear to be a matter of incompatibility. I have restarted the system repeatedly, and this has remained consistent: the router is visible running off of the LiveCD, but not when booting the installed system.

While I suspect that running an upgrade/update and fetching all of the software I need in the immediate term would resolve the issue, I cannot connect to an Ethernet line from where I am located, and moving the desktop system closer to the router (even temporarily) would be a serious problem. Furthermore, I am concerned that doing this might simply mask a deeper issue, so I would prefer to find an explanation before going to that step.

I do not know if this is a relevant issue, but I have noted that the other routers which are visible are all running WPA, whereas mine is running WEP (to maintain compatibility for an older laptop system that someone else in the household is using).

details:

base sys: Intel D845WN, Celeron 2.0 GHz, 512MiB
wireless adapter: Linksys WUSB54GC
router: Belkin F5D8231, WEP security

If any further details are needed, please ask.

---

### Post by Scol-R-LEA on 2009-08-06
In the interest of full disclosure (and, not entirely incidentally, bumping the thread), here is the sanitized output of [FONT="Courier New"]lshw[/FONT] for the system in question:
```
computer
    description: Computer
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: boot=normal uuid=83589399-CC8E-11D5-A876-001083FDCE08
  *-core
       description: Motherboard
       product: D845WN
       vendor: Intel Corporation
       physical id: 0
       version: AAA64181-203
       serial: [REMOVED]
     *-firmware
          description: BIOS
          vendor: Intel Corp.
          physical id: 0
          version: HV84510A.86A.0050.P15.0305252001 (05/25/2003)
          size: 64KiB
          capacity: 448KiB
          capabilities: pci pnp apm upgrade shadowing escd cdboot bootselect edd int13floppynec int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Celeron(R) CPU 2.00GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.2.7
          slot: J2E1
          size: 2GHz
          capacity: 2GHz
          width: 32 bits
          clock: 100MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe up pebs bts cid xtpr
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: None
             size: 8KiB
             capacity: 8KiB
             clock: 25MHz (40.0ns)
             capabilities: pipeline-burst synchronous internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: None
             size: 128KiB
             capacity: 128KiB
             capabilities: synchronous internal write-back unified
     *-memory
          description: System Memory
          physical id: 35
          slot: System board or motherboard
          size: 512MiB
          capacity: 3GiB
        *-bank:0
             description: DIMM SDRAM Synchronous 133 MHz (7.5 ns)
             physical id: 0
             slot: J6G1
             size: 128MiB
             width: 64 bits
             clock: 133MHz (7.5ns)
        *-bank:1
             description: DIMM SDRAM Synchronous 133 MHz (7.5 ns)
             physical id: 1
             slot: J6G2
             size: 128MiB
             width: 64 bits
             clock: 133MHz (7.5ns)
        *-bank:2
             description: DIMM SDRAM Synchronous 133 MHz (7.5 ns)
             physical id: 2
             slot: J6H1
             size: 256MiB
             width: 64 bits
             clock: 133MHz (7.5ns)
     *-pci
          description: Host bridge
          product: 82845 845 [Brookdale] Chipset Host Bridge
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-pci:0
             description: PCI bridge
             product: 82845 845 [Brookdale] Chipset AGP Bridge
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master
           *-display UNCLAIMED
                description: VGA compatible controller
                product: NV11 [GeForce2 MX/MX 400]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: b2
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-2.0 bus_master cap_list
                configuration: latency=32 maxlatency=1 mingnt=5
        *-pci:1
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 12
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master
           *-network
                description: Ethernet interface
                product: 82801BA/BAM/CA/CAM Ethernet Controller
                vendor: Intel Corporation
                physical id: 8
                bus info: pci@0000:02:08.0
                logical name: eth0
                version: 03
                serial: [REMOVED]
                size: 10MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k6-NAPI duplex=half firmware=N/A latency=32 link=no maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=10MB/s
           *-usb:0
                description: USB Controller
                product: VT82xxxxx UHCI USB 1.1 Controller
                vendor: VIA Technologies, Inc.
                physical id: a
                bus info: pci@0000:02:0a.0
                version: 62
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=uhci_hcd latency=32 module=uhci_hcd
           *-usb:1
                description: USB Controller
                product: VT82xxxxx UHCI USB 1.1 Controller
                vendor: VIA Technologies, Inc.
                physical id: a.1
                bus info: pci@0000:02:0a.1
                version: 62
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=uhci_hcd latency=32 module=uhci_hcd
           *-usb:2
                description: USB Controller
                product: USB 2.0
                vendor: VIA Technologies, Inc.
                physical id: a.2
                bus info: pci@0000:02:0a.2
                version: 65
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=ehci_hcd latency=32 module=ehci_hcd
           *-firewire
                description: FireWire (IEEE 1394)
                product: VT6306 Fire II IEEE 1394 OHCI Link Layer Controller
                vendor: VIA Technologies, Inc.
                physical id: a.3
                bus info: pci@0000:02:0a.3
                version: 46
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=ohci1394 latency=32 maxlatency=32 module=ohci1394
           *-storage
                description: RAID bus controller
                product: VT6421 IDE RAID Controller
                vendor: VIA Technologies, Inc.
                physical id: a.4
                bus info: pci@0000:02:0a.4
                logical name: scsi2
                version: 50
                width: 32 bits
                clock: 33MHz
                capabilities: storage pm bus_master cap_list emulated
                configuration: driver=sata_via latency=32
              *-disk
                   description: ATA Disk
                   product: WDC WD10EACS-00D
                   vendor: Western Digital
                   physical id: 0.0.0
                   bus info: scsi@2:0.0.0
                   logical name: /dev/sdb
                   version: 01.0
                   serial: [REMOVED]
                   size: 931GiB (1TB)
                   capabilities: partitioned partitioned:dos
                   configuration: ansiversion=5 signature=00033c4f
                 *-volume:0
                      description: Windows NTFS volume
                      physical id: 1
                      bus info: scsi@2:0.0.0,1
                      logical name: /dev/sdb1
                      version: 3.1
                      serial: [REMOVED]
                      size: 119GiB
                      capacity: 119GiB
                      capabilities: primary ntfs initialized
                      configuration: clustersize=4096 created=2009-08-04 10:27:51 filesystem=ntfs label=New Volume state=clean
                 *-volume:1
                      description: EXT3 volume
                      vendor: Linux
                      physical id: 2
                      bus info: scsi@2:0.0.0,2
                      logical name: /dev/sdb2
                      logical name: /media/disk-1
                      version: 1.0
                      serial: [REMOVED]
                      size: 29GiB
                      capacity: 29GiB
                      capabilities: primary journaled extended_attributes large_files recover ext3 ext2 initialized
                      configuration: created=2009-08-03 21:12:49 filesystem=ext3 modified=2009-08-06 13:33:11 mount.fstype=ext3 mount.options=rw,nosuid,nodev,errors=continue,data=ordered mounted=2009-08-06 13:33:11 state=mounted
                 *-volume:2
                      description: Extended partition
                      physical id: 3
                      bus info: scsi@2:0.0.0,3
                      logical name: /dev/sdb3
                      size: 439GiB
                      capacity: 439GiB
                      capabilities: primary extended partitioned partitioned:extended
                    *-logicalvolume:0
                         description: Linux swap / Solaris partition
                         physical id: 5
                         logical name: /dev/sdb5
                         capacity: 3906MiB
                         capabilities: nofs
                    *-logicalvolume:1
                         description: Linux filesystem partition
                         physical id: 6
                         logical name: /dev/sdb6
                         logical name: /media/disk
                         capacity: 63GiB
                         configuration: mount.fstype=ext3 mount.options=rw,nosuid,nodev,errors=continue,data=ordered state=mounted
                    *-logicalvolume:2
                         description: Linux filesystem partition
                         physical id: 7
                         logical name: /dev/sdb7
                         logical name: /media/disk-3
                         capacity: 372GiB
                         configuration: mount.fstype=ext3 mount.options=rw,nosuid,nodev,errors=continue,data=ordered state=mounted
                 *-volume:3
                      description: Windows NTFS volume
                      physical id: 4
                      bus info: scsi@2:0.0.0,4
                      logical name: /dev/sdb4
                      logical name: /media/disk-4
                      version: 3.1
                      serial: [REMOVED]
                      size: 333GiB
                      capacity: 333GiB
                      capabilities: primary ntfs initialized
                      configuration: clustersize=4096 created=2009-08-04 04:00:13 filesystem=ntfs mount.fstype=fuseblk mount.options=rw,nosuid,nodev,user_id=0,group_id=0,allow_other,blksize=4096 state=mounted
           *-multimedia
                description: Multimedia audio controller
                product: SB Live! EMU10k1
                vendor: Creative Labs
                physical id: b
                bus info: pci@0000:02:0b.0
                version: 07
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=EMU10K1_Audigy latency=32 maxlatency=20 mingnt=2 module=snd_emu10k1
           *-input
                description: Input device controller
                product: SB Live! Game Port
                vendor: Creative Labs
                physical id: b.1
                bus info: pci@0000:02:0b.1
                version: 07
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=Emu10k1_gameport latency=32 module=emu10k1_gp
           *-communication UNCLAIMED
                description: Communication controller
                product: HaM controllerless modem
                vendor: Ambient Technologies Inc
                physical id: e
                bus info: pci@0000:02:0e.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: pm cap_list
                configuration: latency=0
        *-isa
             description: ISA bridge
             product: 82801BA ISA Bridge (LPC)
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 12
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801BA IDE U100 Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             logical name: scsi1
             version: 12
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0
           *-disk
                description: ATA Disk
                product: WDC WD800BB-00CA
                vendor: Western Digital
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 16.0
                serial: [REMOVED]
                size: 74GiB (80GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=e5c1e5c1
              *-volume
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /media/disk-2
                   version: 3.1
                   serial: [REMOVED]
                   size: 74GiB
                   capacity: 74GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2009-04-12 20:44:39 filesystem=ntfs mount.fstype=fuseblk mount.options=rw,nosuid,nodev,user_id=0,group_id=0,allow_other,blksize=4096 state=mounted
           *-cdrom:0
                description: DVD reader
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                logical name: /cdrom
                capabilities: audio dvd
                configuration: mount.fstype=iso9660 mount.options=ro,noatime state=mounted status=ready
           *-cdrom:1
                description: CD-R/CD-RW writer
                product: 241240 CDRW
                vendor: PHILIPS
                physical id: 0.1.0
                bus info: scsi@1:0.1.0
                logical name: /dev/cdrom1
                logical name: /dev/cdrw1
                logical name: /dev/scd1
                logical name: /dev/sr1
                logical name: /media/Ubuntu 9.04 i386
                version: 1.0B
                serial: [REMOVED]
                capabilities: removable audio cd-r cd-rw
                configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,nosuid,nodev,uid=999,utf8 state=mounted status=ready
              *-medium
                   physical id: 0
                   logical name: /dev/cdrom1
                   logical name: /media/Ubuntu 9.04 i386
                   configuration: mount.fstype=iso9660 mount.options=ro,nosuid,nodev,uid=999,utf8 state=mounted
        *-usb:0
             description: USB Controller
             product: 82801BA/BAM USB Controller #1
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 12
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-serial UNCLAIMED
             description: SMBus
             product: 82801BA/BAM SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 12
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
        *-usb:1
             description: USB Controller
             product: 82801BA/BAM USB Controller #1
             vendor: Intel Corporation
             physical id: 1f.4
             bus info: pci@0000:00:1f.4
             version: 12
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-multimedia
             description: Multimedia audio controller
             product: 82801BA/BAM AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 12
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=Intel ICH latency=0 module=snd_intel8x0
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: [REMOVED]
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=[REMOVED] multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: [REMOVED]
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```

If you look at the partition information, you will note from the system dual-boots Windows XP, which I currently need for work (and gaming) related reasons; I anticipate using Linux for the bulk of my purposes, with Windows applications run virtualized/emulated whenever possible. I have also left a small (9GiB) partition for experimenting with an LFS build at some point in the future, though that I may end up running that virtualized as well (depending on whether I have the funds to replace this motherboard and/or add more memory by that point). The drive with the Linux partitions is a 1TB WDC SATA drive, which is interfaced through a PCI multi-controller (USB/FW/SATA) card.

While I doubt that any of this is particularly relevant, I thought it would be better to give as much information as possible - though by putting it in a separate post, I am hopefully allowing respondents to bypass it if it wasn't helpful. C&CW.

---

### Post by Scol-R-LEA on 2009-08-15
I've still had little luck with this; most cases I've read about have involved a total failure of the wireless driver, which does not seem to be the case here. Both the LiveCD and the installed system detect the device correctly, AFAICT, but the latter can't detect the specific network (though it does detect others) even when less than 2m away from the router, line-of-sight.

Here is some additional information about the configuration running on the liveCD:
```
**ubuntu@ubuntu:~$ sudo lsusb -vv | grep Linksys**
Bus 003 Device 003: ID 13b1:0020 Linksys WUSB54GC 802.11g Adapter [ralink rt73]
  idVendor           0x13b1 Linksys
  iManufacturer           1 Cisco-Linksys

**ubuntu@ubuntu:~$ ifconfig **
eth0      Link encap:Ethernet  HWaddr 00:03:47:c8:bd:fb  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:03:47:c8:bd:fb  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 B)  TX bytes:100 (100.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:22:6b:a3:7e:d7  
          inet addr:192.168.2.3  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: 2002:4c7a:4988:1234:222:6bff:fea3:7ed7/64 Scope:Global
          inet6 addr: fe80::222:6bff:fea3:7ed7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5580707 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5629520 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3980593812 (3.9 GB)  TX bytes:324081441 (324.0 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-22-6B-A3-7E-D7-65-64-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 B)  TX bytes:100 (100.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:22:6b:a3:7e:d7  
          inet addr:192.168.2.3  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: 2002:4c7a:4988:1234:222:6bff:fea3:7ed7/64 Scope:Global
          inet6 addr: fe80::222:6bff:fea3:7ed7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5580707 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5629520 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3980593812 (3.9 GB)  TX bytes:324081441 (324.0 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-22-6B-A3-7E-D7-65-64-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

**ubuntu@ubuntu:~$ iwconfig **
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"Jericho"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:17:3F:91:5F:FB   
          Bit Rate=54 Mb/s   Tx-Power=19 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=68/100  Signal level:-72 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

```

As you can see, it seems to be using the ralink rt73 driver, which most say is the correct chipset (though at least one link indicated that it was actually the RTL8187B chipset). Any comments?

If this should be transferred to a different message board, please let me know. I felt that this was an installation issue, as the hardware and driver seems to be working correctly but differs between the two configurations, but in retrospect it may have been better in a forum specific to wifi networking.

---

### Post by Scol-R-LEA on 2009-08-28
Bump.

I've tried installing the older version (1.4.0.0) of the rt73 driver, as described [here](http://ubuntuforums.org/showpost.php?p=7262158&postcount=2), but with no success; indeed, it appears to have been using that version of the driver already. No progress has been made.

---

### Post by Scol-R-LEA on 2009-09-01
I am at the point where I'll probably try another re-installation if I can't find a solution soon. If that doesn't work, I may simply buy a different wireless adapter (after checking the compatibility list of course), but since the WUSB54GC adapter is working - just not seeing the specific router when running from the installed system - I'd much rather avoid that. Any advice, either about fixing the problem or about wireless cards?

---

### Post by Flash858 on 2009-09-01
Some things to try: 

1) Try using the ndiswrapper (windows) driver for the adapter.

2) Try changing the encryption on the router from WEP to WPA - Some adapters will work on one, but not the other on a specific router.

3) While running from the live CD, download the newest driver and save it to a partition on the hard drive, or some removeable media, then install it from the installed version.

Hopefully one of these will work, and my guess is it will be #2.

---

### Post by Scol-R-LEA on 2009-09-01
Well, I've wanted a reason to switch to WPA for some time, and we aren't using the older laptop that I had had WEP set up for anyway, so I started with that. This wasn't enough on its own, so I set up ndisdriver and installed (or at least set up) the Windows driver, as well.

Between these changes, the router is now visible, but I'm having another problem: when I enter the key using the network manager tool, it allows me to enter it, but the link does not connect, and when I then go to check the key, it shows a series of hex numerals. The numerals don't match the ASCII or UTF-8 values for the keys, and the size of the string is about one and half times the size of the original (rather than either the same size or double it). I haven't had a chance to look up this problem, or see if anything needs to be set with wpa-supplicant, but I'll be working on it later. Any advice would be appreciated.

---

