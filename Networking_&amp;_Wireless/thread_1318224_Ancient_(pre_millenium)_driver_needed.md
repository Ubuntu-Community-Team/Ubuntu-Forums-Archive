---
title: "Ancient (pre millenium) driver needed?"
date: 2009-11-07
forum: Networking &amp; Wireless
---

### Post by J V on 2009-11-07
I have an ancient laptop from 2000 with a network card that plugs in (anyone remember those?) and I need to get the [dynalink SPL100CLV driver](http://download.driverguide.com/driver/SPL100CLV/Dynalink/d1033842.html) for my laptop or I can't access the network and therefore can't update (to get real drivers?)

I know its an ancient driver, but is there a quick fix or hack to get it working?

---

### Post by skriefal on 2009-11-07
Most no-name ethernet cards use Realtek chips, so try the driver for the Realtek 8139 cards. IIRC the driver is named "8139too".

---

### Post by hal10000 on 2009-11-07
You can also try the ne2k_pci driver, which works on many old network cards

---

### Post by J V on 2009-11-07
Apparently it does... But the problem is that I've never installed drivers on linux (Never had to, hurray for linux!)

Know where I could get something like that?

Edit: "sudo modprobe 8139too" didn't do anything, still can't find how to install the other one, same way?

---

### Post by skriefal on 2009-11-07
Well, I downloaded the Windows drivers you linked above and peeked into the *.inf file.  According to that, it's a Realtek 8139.  So 8139too or 8139cp should do the job.

---

### Post by J V on 2009-11-08
ok thanks, I'll install both and reboot and see if there are any changes...

You do realise its on of those plug into laptop cards that dissapeared around the turn of the century?

---

### Post by cascade9 on 2009-11-08
You mean PCMCIA? 

[http://en.wikipedia.org/wiki/PC_Card](http://en.wikipedia.org/wiki/PC_Card)

If you never had to install the driver before, its possible that your network card is kaput. Also, I seem to recall seeing someone here, on the forums, say that the  RL8139 network cards just dont work with newer debian/debian based OSes.

---

### Post by neojames on 2009-11-08
If you have the windows drivers you could use ndswrapper, I havent done this before, but there are plenty of guides out there.

---

### Post by J V on 2009-11-08
Well I dont have internet to get ndiswrapper (and would prefer not to have to package use it) and yes, its a PCMIA from the images I see on wikipedia...

As for the driver, this thing was running ME cause it was so slow, took an alternate xubuntu install to get it installed this time...

So this is the first linux install of this driver...

It may well be that it just doesn't work...

---

### Post by hal10000 on 2009-11-08
perform ```
lspci
``` and post the output, so we can see if the network card is being recognized.
Also post the output of ```
sudo lshw -C network
```

---

### Post by J V on 2009-11-08
"sudo lshw -C/-c/-class Network didn't work, it spammed everything line for line, but on the same line (so everything got overwritten by the end)

I have the output from sudo lshw and lspci...

```
00:00.0 Host bridge: Intel Corporation 82815 815 Chipset Host Bridge and Memory Controller Hub (rev 11)
00:02.0 VGA compatible controller: Intel Corporation 82815 Chipset Graphics Controller (CGC) (rev 11)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801BAM ISA Bridge (LPC) (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801BAM IDE U100 Controller (rev 03)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 03)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus Controller (rev 03)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801BA/BAM AC'97 Modem Controller (rev 03)
01:00.0 FireWire (IEEE 1394): Texas Instruments TSB43AA22 IEEE-1394 Controller (PHY/Link Integrated) (rev 02)
01:02.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev 80)
01:02.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev 80)
``````
PCI (sysfs)  
xubuntu                   
    description: Computer
    product: PCG-FX101(GB)
    vendor: Sony Corporation
    version: 01
    serial: 28318450-5508262
    width: 32 bits
    capabilities: smbios-2.31 dmi-2.31
    configuration: administrator_password=enabled boot=oem-specific frontpanel_password=unknown keyboard_password=unknown power-on_password=disabled
  *-core
       description: Motherboard
       product: PCG-FX101(GB)
       vendor: Sony Corporation
       physical id: 0
       version: 01
       serial: 28318450-5508262
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies LTD
          physical id: 0
          version: R0211U0 (03/13/01)
          size: 105KiB
          capacity: 192KiB
          capabilities: isa pci pcmcia pnp apm upgrade shadowing usb smartbattery biosbootspecification
     *-cpu
          description: CPU
          product: Celeron (Coppermine)
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.8.6
          slot: U1
          size: 600MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 mtrr pge mca cmov pse36 mmx fxsr sse up
        *-cache:0
             description: L1 cache
             physical id: 8
             slot: L1 Cache
             size: 32KiB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 9
             slot: L2 Cache
             size: 128KiB
             capacity: 512KiB
             capabilities: burst external write-back
     *-memory
          description: System Memory
          physical id: 14
          slot: System board or motherboard
          size: 192MiB
          capacity: 512MiB
        *-bank:0
             description: DIMM DRAM Synchronous
             physical id: 0
             slot: M1
             size: 64MiB
             width: 32 bits
        *-bank:1
             description: DIMM DRAM Synchronous
             physical id: 1
             slot: M2
             size: 128MiB
             width: 32 bits
     *-pci
          description: Host bridge
          product: 82815 815 Chipset Host Bridge and Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 11
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display UNCLAIMED
             description: VGA compatible controller
             product: 82815 Chipset Graphics Controller (CGC)
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 11
             width: 32 bits
             clock: 66MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
             resources: memory:f8000000-fbffffff(prefetchable) memory:f4000000-f407ffff
        *-pci
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master
             resources: ioport:3000(size=4096) memory:f4100000-f41fffff memory:c000000-13ffffff(prefetchable)
           *-firewire UNCLAIMED
                description: FireWire (IEEE 1394)
                product: TSB43AA22 IEEE-1394 Controller (PHY/Link Integrated)
                vendor: Texas Instruments
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: latency=64 maxlatency=4 mingnt=3
                resources: memory:f4104000-f41047ff memory:f4100000-f4103fff
           *-pcmcia:0
                description: CardBus bridge
                product: RL5c476 II
                vendor: Ricoh Co Ltd
                physical id: 2
                bus info: pci@0000:01:02.0
                version: 80
                width: 64 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=128
                resources: iomemory:b00502010-b0050200f irq:0 memory:f4105000-f4105fff ioport:3000(size=256) ioport:3400(size=256) memory:c000000-fffffff(prefetchable) memory:14000000-17ffffff
           *-pcmcia:1
                description: CardBus bridge
                product: RL5c476 II
                vendor: Ricoh Co Ltd
                physical id: 2.1
                bus info: pci@0000:01:02.1
                version: 80
                width: 64 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5
                resources: iomemory:b00906010-b0090600f irq:0 memory:f4106000-f4106fff ioport:3800(size=256) ioport:3c00(size=256) memory:10000000-13ffffff(prefetchable) memory:18000000-1bffffff
        *-isa
             description: ISA bridge
             product: 82801BAM ISA Bridge (LPC)
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801BAM IDE U100 Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             logical name: scsi1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0
             resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:1800(size=16)
           *-disk
                description: ATA Disk
                product: HITACHI_DK23BA-2
                vendor: Hitachi
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 00E0
                serial: 11JW96
                size: 18GiB (20GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=184acb64
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 95ed7a5d-22fe-410b-8bc9-acaf61bc4c36
                   size: 18GiB
                   capacity: 18GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2009-11-07 17:04:52 filesystem=ext4 lastmountpoint=/&#65533;&#65533;`\&#65533;&#65533;0>H&#704;g&#668;&#65533;&#65533;&#65533;iW&#65533;8&#65533;H&#65533;8&#65533;H&#741;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;Y&#65533;&#65533;&#640;&#65533;%&#65533;&#65533;&#65533; modified=2009-11-07 18:03:54 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2009-11-08 17:03:04 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 525MiB
                   capacity: 525MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 525MiB
                      capabilities: nofs
           *-cdrom
                description: SCSI CD-ROM
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/scd0
                logical name: /dev/sr0
                capabilities: audio
                configuration: status=nodisc
        *-usb:0
             description: USB Controller
             product: 82801BA/BAM USB Controller #1
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:9 ioport:1820(size=32)
        *-serial UNCLAIMED
             description: SMBus
             product: 82801BA/BAM SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 03
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:1810(size=16)
        *-usb:1
             description: USB Controller
             product: 82801BA/BAM USB Controller #1
             vendor: Intel Corporation
             physical id: 1f.4
             bus info: pci@0000:00:1f.4
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:11 ioport:2400(size=32)
        *-multimedia
             description: Multimedia audio controller
             product: 82801BA/BAM AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=Intel ICH latency=0
             resources: irq:5 ioport:1c00(size=256) ioport:1840(size=64)
        *-communication UNCLAIMED
             description: Modem
             product: 82801BA/BAM AC'97 Modem Controller
             vendor: Intel Corporation
             physical id: 1f.6
             bus info: pci@0000:00:1f.6
             version: 03
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:2000(size=256) ioport:1880(size=128)
  *-remoteaccess UNCLAIMED
       vendor: Intel
       physical id: 1
       capabilities: inbound
```

---

### Post by skriefal on 2009-11-09
The NIC is not visible in either of those lists.  Either it's not installed into the slot properly, or it's defective, or the PCMCIA/Cardbus controller isn't working as expected.

Do you or anyone you know have an alternate NIC that you could test?

---

### Post by J V on 2009-11-10
Nope, but I thought it worked with windows like a week before...

Oh well, no bother, I'm not gonna spend 10 bucks on an adapter for a 10 year old PC...

---

