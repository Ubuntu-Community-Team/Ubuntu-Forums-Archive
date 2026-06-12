---
title: "Leadtek DTV2000ds wont configure in new install, newbie"
date: 2016-02-13
forum: Mythbuntu
---

### Post by philip34 on 2016-02-13
Hi, a newbie here and out of my depth with Myth etc etc.I  have been using 2 Leadtek DTV2000DS cards with xp, dv scheduler and a Gigabyte A75-D3H for years but xp is breaking so I tried to load the latest Myth, its a clean install, it fires up ok but when I try to configure the cards in the backend setup I get an error message. I have updated.  It seems that these cards were recognized at some time but are they broken again? One response to another message is to go back to Natty to get it to work but that was a very old message as is Natty. So if I have to go back to an old version how far back do I have to go, the lasy 32bit? what was that? Please keep it very simple I am not across any of the linux knowledge with kernals , terminals and so forth. So if there isn't a fairly simple answer this isnt a skill set I really want to obtain so I probably should look for another solution. Thanks

---

### Post by khPWXxF on 2016-02-13
XP breaking?  Xp should be stable though that message might be unpopular here.
Try cleaning Heatsinks?
Have you seen comments here?
[http://linuxtv.org/wiki/index.php/Leadtek_WinFast_DTV2000DS](http://linuxtv.org/wiki/index.php/Leadtek_WinFast_DTV2000DS)
What is the error message you are getting?
Which version of Mythbuntu are you using?
Phil

---

### Post by philip34 on 2016-02-14
Hi khPWXxF, 

When I go to Github and download the zip file from the link you posted, do I follow the  instructions I found here?  [http://community.linuxmint.com/tutorial/view/313](http://community.linuxmint.com/tutorial/view/313) ? I unzip it first, but where do I put it?  Will it find the  correct place to install itself? 

Id like any instructions using a graphical interface if possible , I am a Newbie to Myth, I started in the days of Dos but that was a long time ago.

Re your questions, 
XP is not being supported by Chrome and firefox soon, the system itself is getting very slow, I have tried the usual fixes, CC cleaner, spybot etc to no avail, it may have suffered some fiddling with by others, its had its day and its past time to move on, Win 7 is a giant leap from xp. If I cant get a Mythbox running i will likely move to a 64bit Win and MediaPortal. 

Yes I have seen that comment, its dated June 2012. I was thinking that two and a half years later it may be out of date? 

I didnt note the error message, I think it was just "error finding tuner" or similar. It was just the backend tuner card setup where the prompt suggests that when you start the change the name a search for the tuner will occur and if it doesnt find the tuner an error will occur, it did.

Myth version 14.04.2
Thanks


> **khPWXxF said:**
> 
XP breaking?  Xp should be stable though that message might be unpopular here.
Try cleaning Heatsinks?
Have you seen comments here?
[http://linuxtv.org/wiki/index.php/Leadtek_WinFast_DTV2000DS](http://linuxtv.org/wiki/index.php/Leadtek_WinFast_DTV2000DS)
What is the error message you are getting?
Which version of Mythbuntu are you using?
Phil

---

### Post by mörgæs on 2016-02-14
Let's see the hardware details. Please run ```
sudo lshw -sanitize -> lshw.txt
``` and post lshw.txt in CODE tags.

---

### Post by philip34 on 2016-02-15
The error I get is 
Frontend ID: could not get info for card/dev/dvb/adaptor1/frontend  (this is just the default location with the last digit removed which triggers the search for the card)   Subtype  PCI  Unknown error

I have downloaded the zip at Github which was linked at the thread at [http://linuxtv.org/wiki/index.php/Le...Fast_DTV2000DS](http://linuxtv.org/wiki/index.php/Le...Fast_DTV2000DS)   I ran it as root and it appeared to install , I rebooted but error remains.

The hardware is as follows.  I  couldnt get the ->lshw.txt part of the request to work? I dont know what it does?

Thanks for the replies.

```
 [lshw]
computer                  
    description: Desktop Computer
    product: GA-A75-D3H ()
    vendor: Gigabyte Technology Co., Ltd.
    width: 64 bits
    capabilities: smbios-2.4 dmi-2.4 vsyscall32
    configuration: boot=normal chassis=desktop uuid=[REMOVED]
  *-coredescription: Motherboard
       product: GA-A75-D3H
       vendor: Gigabyte Technology Co., Ltd.
       physical id: 0
       version: x.x
     *-firmware
          description: BIOS
          vendor: Award Software International, Inc.
          physical id: 0
          version: F1
          date: 06/13/2011
          size: 128KiB
          capacity: 4032KiB
          capabilities: isa pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: AMD A8-3850 APU with Radeon(tm) HD Graphics
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: AMD A8-3850 APU with Radeon(tm) HD Graphics
          slot: Socket M2
          size: 800MHz
          capacity: 3GHz
          width: 64 bits
          clock: 100MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp x86-64 3dnowext 3dnow constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt arat hw_pstate npt lbrv svm_lock nrip_save pausefilter vmmcall cpufreq
        *-cache:0
             description: L1 cache
             physical id: a
             slot: Internal Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L3 cache
             physical id: c
             slot: External Cache
             size: 1MiB
             capacity: 1MiB
             capabilities: synchronous internal write-back
     *-cache
          description: L1 cache
          physical id: b
          slot: Internal Cache
          size: 128KiB
          capacity: 128KiB
          capabilities: synchronous internal write-back
     *-memory
          description: System Memory
          physical id: 26
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: DIMM 1333 MHz (0.8 ns) [empty]
             product: None
             vendor: None
             physical id: 0
             serial: [REMOVED]
             slot: A0
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:1
             description: DIMM 1333 MHz (0.8 ns) [empty]
             product: None
             vendor: None
             physical id: 1
             serial: [REMOVED]
             slot: A1
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:2
             description: DIMM 1333 MHz (0.8 ns)
             product: None
             vendor: None
             physical id: 2
             serial: [REMOVED]
             slot: A2
             size: 2GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:3
             description: DIMM 1333 MHz (0.8 ns)
             product: None
             vendor: None
             physical id: 3
             serial: [REMOVED]
             slot: A3
             size: 2GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
     *-pci:0
          description: Host bridge
          product: Family 12h Processor Root Complex
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
          configuration: latency=32
        *-display
             description: VGA compatible controller
             product: BeaverCreek [Radeon HD 6550D]
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
             configuration: driver=radeon latency=0
             resources: irq:52 memory:d0000000-dfffffff ioport:f800(size=256) memory:fdfc0000-fdffffff
        *-multimedia:0
             description: Audio device
             product: BeaverCreek HDMI Audio [Radeon HD 6500D and 6400G-6600G series]
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 1.1
             bus info: pci@0000:00:01.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm pciexpress msi bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:53 memory:fe01c000-fe01ffff
        *-usb:0
             description: USB controller
             product: FCH USB XHCI Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 10
             bus info: pci@0000:00:10.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi msix pciexpress xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:18 memory:fe028000-fe029fff
        *-usb:1
             description: USB controller
             product: FCH USB XHCI Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 10.1
             bus info: pci@0000:00:10.1
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi msix pciexpress xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:17 memory:fe026000-fe027fff
        *-storage
             description: SATA controller
             product: FCH SATA Controller [IDE mode]
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 40
             width: 32 bits
             clock: 66MHz
             capabilities: storage ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=32
             resources: irq:19 ioport:ff00(size=8) ioport:fe00(size=4) ioport:fd00(size=8) ioport:fc00(size=4) ioport:fb00(size=16) memory:fe02f000-fe02f7ff
        *-usb:2
             description: USB controller
             product: FCH USB OHCI Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 11
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci-pci latency=32
             resources: irq:18 memory:fe02e000-fe02efff
        *-usb:3
             description: USB controller
             product: FCH USB EHCI Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 12.2
             bus info: pci@0000:00:12.2
             version: 11
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=32
             resources: irq:17 memory:fe02d000-fe02d0ff
        *-usb:4
             description: USB controller
             product: FCH USB OHCI Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 11
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci-pci latency=32
             resources: irq:18 memory:fe02c000-fe02cfff
        *-usb:5
             description: USB controller
             product: FCH USB EHCI Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 11
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=32
             resources: irq:17 memory:fe02b000-fe02b0ff
        *-serial
             description: SMBus
             product: FCH SMBus Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 13
             width: 32 bits
             clock: 66MHz
             configuration: driver=piix4_smbus latency=0
             resources: irq:0
        *-ide
             description: IDE interface
             product: FCH IDE Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 14.1
             bus info: pci@0000:00:14.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master
             configuration: driver=pata_atiixp latency=32
             resources: irq:17 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:fa00(size=16)
        *-multimedia:1
             description: Audio device
             product: FCH Azalia Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=snd_hda_intel latency=32
             resources: irq:16 memory:fe020000-fe023fff
        *-isa
             description: ISA bridge
             product: FCH LPC Bridge
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 11
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:0
             description: PCI bridge
             product: FCH PCI Bridge
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 40
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master vga_palette
             resources: ioport:e000(size=4096) memory:fdd00000-fddfffff memory:fde00000-fdefffff
           *-usb:0
                description: USB controller
                product: VT82xxxxx UHCI USB 1.1 Controller
                vendor: VIA Technologies, Inc.
                physical id: 8
                bus info: pci@0000:01:08.0
                version: 62
                width: 32 bits
                clock: 33MHz
                capabilities: pm uhci bus_master cap_list
                configuration: driver=uhci_hcd latency=32
                resources: irq:22 ioport:ef00(size=32)
           *-usb:1
                description: USB controller
                product: USB 2.0
                vendor: VIA Technologies, Inc.
                physical id: 8.2
                bus info: pci@0000:01:08.2
                version: 65
                width: 32 bits
                clock: 33MHz
                capabilities: pm ehci bus_master cap_list
                configuration: driver=ehci-pci latency=32
                resources: irq:20 memory:fddff000-fddff0ff
        *-usb:6
             description: USB controller
             product: FCH USB OHCI Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 14.5
             bus info: pci@0000:00:14.5
             version: 11
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci-pci latency=32
             resources: irq:18 memory:fe02a000-fe02afff
        *-pci:1
             description: PCI bridge
             product: Hudson PCI to PCI bridge (PCIE port 0)
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 15
             bus info: pci@0000:00:15.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 ioport:d000(size=4096) memory:fdc00000-fdcfffff ioport:fdb00000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: 06
                serial: [REMOVED]
                size: 1Gbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168e-3_0.0.4 03/27/12 ip=[REMOVED] latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
                resources: irq:51 ioport:de00(size=256) memory:fdbff000-fdbfffff memory:fdbf8000-fdbfbfff
        *-pci:2
             description: PCI bridge
             product: Hudson PCI to PCI bridge (PCIE port 2)
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 15.2
             bus info: pci@0000:00:15.2
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 ioport:c000(size=4096) memory:fda00000-fdafffff ioport:fd900000(size=1048576)
           *-usb
                description: USB controller
                product: EJ168 USB 3.0 Host Controller
                vendor: Etron Technology, Inc.
                physical id: 0
                bus info: pci@0000:03:00.0
                version: 01
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress xhci bus_master cap_list
                configuration: driver=xhci_hcd latency=0
                resources: irq:50 memory:fdaf8000-fdafffff
     *-pci:1
          description: Host bridge
          product: Family 12h/14h Processor Function 0
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 43
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Family 12h/14h Processor Function 1
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Family 12h/14h Processor Function 2
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Family 12h/14h Processor Function 3
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k10temp
          resources: irq:0
     *-pci:5
          description: Host bridge
          product: Family 12h/14h Processor Function 4
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 105
          bus info: pci@0000:00:18.4
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: Family 12h/14h Processor Function 6
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 106
          bus info: pci@0000:00:18.5
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:7
          description: Host bridge
          product: Family 12h/14h Processor Function 5
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 107
          bus info: pci@0000:00:18.6
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:8
          description: Host bridge
          product: Family 12h/14h Processor Function 7
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 108
          bus info: pci@0000:00:18.7
          version: 00
          width: 32 bits
          clock: 33MHz
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: ST2000DL003-9VT1
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: CC32
             serial: [REMOVED]
             size: 1863GiB (2TB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=0009b232
           *-volume:0
                description: Linux filesystem partition
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /boot
                version: 1.0
                serial: [REMOVED]
                size: 243MiB
                capacity: 243MiB
                capabilities: primary bootable extended_attributes ext2 initialized
                configuration: filesystem=ext2 lastmountpoint=/boot modified=2016-02-15 15:12:48 mount.fstype=ext2 mount.options=rw,relatime mounted=2016-02-15 14:34:23 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                size: 1862GiB
                capacity: 1862GiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux LVM Physical Volume partition
                   physical id: 5
                   logical name: /dev/sda5
                   serial: [REMOVED]
                   size: 1862GiB
                   capacity: 1862GiB
                   capabilities: multi lvm2
     *-scsi:1
          physical id: 2
          logical name: scsi2
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: CDDVDW SH-222AB
             vendor: TSSTcorp
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/sr0
             version: SB00
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
phil@htpc:~$ 
``` [/lshw]

---

### Post by mörgæs on 2016-02-16
So, are you saying that it worked in Natty but broke some time after that? 
Then it would be interesting to see how it works in 16.04 (development version).

---

### Post by philip34 on 2016-02-16
Hi, I have not run Natty, that was just one of the comments I found and there was no follow up as to it working or not.

---

### Post by mörgæs on 2016-02-19
But how does 16.04 behave?

---

