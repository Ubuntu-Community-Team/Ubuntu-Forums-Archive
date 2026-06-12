---
title: "no wired connection"
date: 2010-01-05
forum: Networking &amp; Wireless
---

### Post by redshift88 on 2010-01-05
[SIZE=3]_***EDIT:***_   I found an old ethernet card and it works.  I would like to know what the original problem was and am willing to troubleshoot as long as anyone is willing to help me.  I like fixing things.

_***edit again***_:  card worked once, now experiencing same problems.







BACKGROUND (you can skip this if you like):[/SIZE]

My father has many old yet working computers and computer parts.  When I came back from school on winter break, I put a desktop together to be a quick e-mail and word processing machine.  My parents tend to bog their computers with too much anti-virus and firewalls, so I thought I could set up a linux machine, and they wouldn't be able to figure out how to mess it up.


Anyways, after days of fighting with dead parts, I found a combination that worked.  **For more than a week, the computer connected to the router and surfed the web just fine.**  Then, deciding I was done, I moved the computer to my parents' office.

[SIZE=5]
[SIZE=3]PROBLEM:[/SIZE][/SIZE]

XUBUNTU 9.10

After physically moving the computer upstairs, it booted and showed that no Ethernet cable was connected, even though the cable that was working earlier was actually connected.

So, I searched and tried a few things for about an hour, with no success. Eventually, I decided a reinstall was worth a try.   ** I reinstalled Xubuntu 9.10**.  This did not solve my problem.

[B]Please help me regain internet access.
[/B]

[SIZE=3]
INFORMATION:[/SIZE]

Somewhere I came across a fix that had something to do with VIA networking drivers, however, I could not find that thread again.  I think that might be a good starting point.




**ifconfig**

```


   andrew@andrew-desktop:~$ sudo ifconfig
  [sudo] password for andrew: 
  eth0      Link encap:Ethernet  HWaddr 00:50:2c:a0:c6:0b  
            UP BROADCAST MULTICAST  MTU:1500  Metric:1
            RX packets:0 errors:0 dropped:0 overruns:0 frame:0
            TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:1000 
            RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
            Interrupt:23 Base address:0x8000 
   
  lo        Link encap:Local Loopback  
            inet addr:127.0.0.1  Mask:255.0.0.0
            inet6 addr: ::1/128 Scope:Host
            UP LOOPBACK RUNNING  MTU:16436  Metric:1
            RX packets:0 errors:0 dropped:0 overruns:0 frame:0
            TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:0 
            RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
   
   
   
  


```**lshw**

```


   andrew@andrew-desktop:~$ sudo lshw
  andrew-desktop            
      description: Desktop Computer
      product: P4M266A-8235
      vendor: VIA Technologies, Inc.
      width: 32 bits
      capabilities: smbios-2.2 dmi-2.2 smp-1.1 smp
      configuration: boot=normal chassis=desktop cpus=1
    *-core
         description: Motherboard
         product: P4M266A-8235
         vendor: soyocomputer
         physical id: 0
       *-firmware
            description: BIOS
            vendor: Phoenix Technologies, LTD
            physical id: 0
            version: 6.00 PG (09/09/2003)
            size: 128KiB
            capacity: 192KiB
            capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot
       *-cpu:0
            description: CPU
            product: Intel(R) Celeron(R) CPU 2.60GHz
            vendor: Intel Corp.
            physical id: 4
            bus info: cpu@0
            version: 15.2.9
            slot: Socket 478
            size: 2600MHz
            width: 32 bits
            clock: 100MHz
            capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe up pebs bts cid xtpr
            configuration: id=0
          *-cache:0
               description: L1 cache
               physical id: a
               slot: Internal Cache
               size: 8KiB
               capacity: 20KiB
               capabilities: synchronous internal write-back
          *-cache:1
               description: L2 cache
               physical id: c
               slot: External Cache
               size: 128KiB
               capacity: 128KiB
               capabilities: synchronous external write-back
       *-cpu:1 DISABLED
            description: CPU
            vendor: Unknown
            physical id: 5
            bus info: cpu@1
            version: 15.2.9
            slot: Socket 478
            size: 2600MHz
            clock: 100MHz
            capabilities: ht
            configuration: id=0
          *-cache:0
               description: L1 cache
               physical id: b
               slot: Internal Cache
               size: 8KiB
               capacity: 20KiB
               capabilities: synchronous internal write-back
          *-cache:1
               description: L2 cache
               physical id: d
               slot: External Cache
               size: 128KiB
               capacity: 128KiB
               capabilities: synchronous external write-back
       *-memory
            description: System Memory
            physical id: 1e
            slot: System board or motherboard
            size: 512MiB
            capacity: 768MiB
          *-bank:0
               description: DIMM
               physical id: 0
               slot: A0
               size: 256MiB
          *-bank:1
               description: DIMM
               physical id: 1
               slot: A1
               size: 256MiB
          *-bank:2
               description: DIMM [empty]
               physical id: 2
               slot: A2
       *-pci
            description: Host bridge
            product: P4M266 Host Bridge
            vendor: VIA Technologies, Inc.
            physical id: 100
            bus info: pci@0000:00:00.0
            version: 00
            width: 32 bits
            clock: 66MHz
            configuration: driver=agpgart-via latency=8
            resources: irq:0 memory:e8000000-ebffffff(prefetchable)
          *-pci
               description: PCI bridge
               product: VT8633 [Apollo Pro266 AGP]
               vendor: VIA Technologies, Inc.
               physical id: 1
               bus info: pci@0000:00:01.0
               version: 00
               width: 32 bits
               clock: 66MHz
               capabilities: pci pm bus_master cap_list
               resources: memory:ec000000-edffffff memory:e0000000-e7ffffff(prefetchable)
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
                  resources: memory:ec000000-ecffffff memory:e0000000-e7ffffff(prefetchable) memory:ed000000-ed00ffff(prefetchable)
          *-usb:0
               description: USB Controller
               product: VT82xxxxx UHCI USB 1.1 Controller
               vendor: VIA Technologies, Inc.
               physical id: 10
               bus info: pci@0000:00:10.0
               version: 80
               width: 32 bits
               clock: 33MHz
               capabilities: pm bus_master cap_list
               configuration: driver=uhci_hcd latency=32
               resources: irq:21 ioport:d000(size=32)
          *-usb:1
               description: USB Controller
               product: VT82xxxxx UHCI USB 1.1 Controller
               vendor: VIA Technologies, Inc.
               physical id: 10.1
               bus info: pci@0000:00:10.1
               version: 80
               width: 32 bits
               clock: 33MHz
               capabilities: pm bus_master cap_list
               configuration: driver=uhci_hcd latency=32
               resources: irq:21 ioport:d400(size=32)
          *-usb:2
               description: USB Controller
               product: VT82xxxxx UHCI USB 1.1 Controller
               vendor: VIA Technologies, Inc.
               physical id: 10.2
               bus info: pci@0000:00:10.2
               version: 80
               width: 32 bits
               clock: 33MHz
               capabilities: pm bus_master cap_list
               configuration: driver=uhci_hcd latency=32
               resources: irq:21 ioport:d800(size=32)
          *-usb:3
               description: USB Controller
               product: USB 2.0
               vendor: VIA Technologies, Inc.
               physical id: 10.3
               bus info: pci@0000:00:10.3
               version: 82
               width: 32 bits
               clock: 33MHz
               capabilities: pm bus_master cap_list
               configuration: driver=ehci_hcd latency=32
               resources: irq:21 memory:ee000000-ee0000ff
          *-isa
               description: ISA bridge
               product: VT8235 ISA Bridge
               vendor: VIA Technologies, Inc.
               physical id: 11
               bus info: pci@0000:00:11.0
               version: 00
               width: 32 bits
               clock: 33MHz
               capabilities: isa pm bus_master cap_list
               configuration: latency=0
          *-ide
               description: IDE interface
               product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
               vendor: VIA Technologies, Inc.
               physical id: 11.1
               bus info: pci@0000:00:11.1
               logical name: scsi0
               logical name: scsi1
               version: 06
               width: 32 bits
               clock: 33MHz
               capabilities: ide pm bus_master cap_list emulated
               configuration: driver=pata_via latency=32
               resources: irq:20 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:dc00(size=16)
             *-disk
                  description: ATA Disk
                  product: WDC WD1600AAJB-0
                  vendor: Western Digital
                  physical id: 0
                  bus info: scsi@0:0.0.0
                  logical name: /dev/sda
                  version: 01.0
                  serial: WD-WCAV33345708
                  size: 149GiB (160GB)
                  capabilities: partitioned partitioned:dos
                  configuration: ansiversion=5 signature=000b356c
                *-volume:0
                     description: EXT4 volume
                     vendor: Linux
                     physical id: 1
                     bus info: scsi@0:0.0.0,1
                     logical name: /dev/sda1
                     logical name: /
                     version: 1.0
                     serial: dc3eeac0-fa7e-4d5d-a236-fa51ba7baf1d
                     size: 147GiB
                     capacity: 147GiB
                     capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                     configuration: created=2001-12-31 18:33:59 filesystem=ext4 lastmountpoint=/target^[FONT=&quot]&#65533;&#65533;[/FONT] wm[FONT=&quot]&#1856;[/FONT]0&#1984;vm&#1884;>k[FONT=&quot]&#65533;[/FONT]iW[FONT=&quot]&#65533;[/FONT]0[FONT=&quot]&#65533;&#65533;[/FONT]0[FONT=&quot]&#65533;&#65533;[/FONT]wm[FONT=&quot]&#65533;&#65533;[/FONT]>k&#1912;>k[FONT=&quot]&#65533;&#65533;[/FONT]Y[FONT=&quot]&#65533;[/FONT]wm modified=2001-12-31 18:52:43 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2001-12-31 18:53:41 state=mounted
                *-volume:1
                     description: Extended partition
                     physical id: 2
                     bus info: scsi@0:0.0.0,2
                     logical name: /dev/sda2
                     size: 1459MiB
                     capacity: 1459MiB
                     capabilities: primary extended partitioned partitioned:extended
                   *-logicalvolume
                        description: Linux swap / Solaris partition
                        physical id: 5
                        logical name: /dev/sda5
                        capacity: 1458MiB
                        capabilities: nofs
             *-cdrom
                  description: DVD-RAM writer
                  product: CDDVDW SH-S222A
                  vendor: TSSTcorp
                  physical id: 1
                  bus info: scsi@1:0.0.0
                  logical name: /dev/cdrom
                  logical name: /dev/cdrw
                  logical name: /dev/dvd
                  logical name: /dev/dvdrw
                  logical name: /dev/scd0
                  logical name: /dev/sr0
                  version: SB01
                  capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                  configuration: ansiversion=5 status=nodisc
          *-multimedia
               description: Multimedia audio controller
               product: VT8233/A/8235/8237 AC97 Audio Controller
               vendor: VIA Technologies, Inc.
               physical id: 11.5
               bus info: pci@0000:00:11.5
               version: 50
               width: 32 bits
               clock: 33MHz
               capabilities: pm cap_list
               configuration: driver=VIA 82xx Audio latency=0
               resources: irq:22 ioport:e000(size=256)
          *-network
               description: Ethernet interface
               product: VT6102 [Rhine-II]
               vendor: VIA Technologies, Inc.
               physical id: 12
               bus info: pci@0000:00:12.0
               logical name: eth0
               version: 74
               serial: 00:50:2c:a0:c6:0b
               size: 10MB/s
               capacity: 100MB/s
               width: 32 bits
               clock: 33MHz
               capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
               configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=half latency=32 link=no maxlatency=8 mingnt=3 multicast=yes port=MII speed=10MB/s
               resources: irq:23 ioport:e400(size=256) memory:ee001000-ee0010ff
       *-scsi
            physical id: 1
            bus info: usb@1:4
            logical name: scsi2
            capabilities: emulated scsi-host
            configuration: driver=usb-storage
          *-disk
               description: SCSI Disk
               physical id: 0.0.0
               bus info: scsi@2:0.0.0
               logical name: /dev/sdb
               size: 1937MiB (2031MB)
               capabilities: partitioned partitioned:dos
             *-volume
                  description: Windows FAT volume
                  vendor: *5>+kIHC
                  physical id: 1
                  bus info: scsi@2:0.0.0,1
                  logical name: /dev/sdb1
                  logical name: /media/disk
                  version: FAT16
                  serial: 5e92-e433
                  size: 1929MiB
                  capacity: 1933MiB
                  capabilities: primary bootable fat initialized
                  configuration: FATs=2 filesystem=fat mount.fstype=vfat mount.options=rw,nosuid,nodev,relatime,uid=1000,fmask=0022,dmask=0022,codepage=cp437,iocharset=utf8,shortname=winnt,errors=remount-ro state=mounted
  


```**sudo dhclient eth0**


```


    andrew@andrew-desktop:~$ sudo dhclient eth0
  Internet Systems Consortium DHCP Client V3.1.2
  Copyright 2004-2008 Internet Systems Consortium.
  All rights reserved.
  For info, please visit http://www.isc.org/sw/dhcp/
   
  Listening on LPF/eth0/00:50:2c:a0:c6:0b
  Sending on   LPF/eth0/00:50:2c:a0:c6:0b
  Sending on   Socket/fallback
  DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
  DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 20
  DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
  DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
  DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
  No DHCPOFFERS received.
  No working leases in persistent database - sleeping.
   
  

```[B]sudo /etc/init.d/networking restart
[/B] 

```


   andrew@andrew-desktop:~$ sudo /etc/init.d/networking restart
   * Reconfiguring network interfaces...                                   [ OK ] 
  


```I also forgot to mention that i tried the ifdown eth0 and ifup eth0 with a "not configured" error


edit:  I forgot another item.  The ethernet cable works on my netbook just fine.

---

### Post by johnson.d on 2010-01-06
This seems to be a hardware issue where the PCI slot may be having a problem (If the Ethernet card is connected to PCI).So you can try changing the slot for the Ethernet card. 

Since you had been networking at least for some times with both the cards, the problem may not be related to the drivers. To eliminate any physical problems with the PCI slot, it may be worth testing the NIC with another PCI slot.

---

### Post by redshift88 on 2010-01-06
The next PCI slot worked.  Thank you.  :D

---

