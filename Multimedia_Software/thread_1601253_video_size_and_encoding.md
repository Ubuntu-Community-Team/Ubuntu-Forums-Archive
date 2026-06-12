---
title: "video size and encoding"
date: 2010-10-20
forum: Multimedia Software
---

### Post by Messyhair42 on 2010-10-20
Is there any way for my computer to decode blu-ray quality video better? my monitor is smaller than 1080p and my video card is just good, not great. i use VLC for most everything and Mplayer when VLC doesn't do something right. my problem with blu-ray quality is that it's inconsistent, some things play well, some play mostly well but are choppy or they hang up, some doesn't play at all. are there any workarounds that don't require new hardware? (not that i don't have and upgrade already in mind)

---

### Post by P4man on 2010-10-20
Its probably if the bitrate is too high, that your CPU cant keep up. Been doing some tests with XBMC as I was building a hometheater PC from scrap parts. 

Without GPU acceleration (old geforce 7300), a Pentium 4 3 GHz I had laying around can do HD decode up to about 10 MBit. Above that, it starts skipping and dropping frames rather badly, regardless if its 720 or 1080. If I swap  the cpu for a Core2 duo 2.8 GHz, they play flawlessly again, with cpu usage in the 40% range.

If I replace the old geforce with a slightly less old videocard that supports VDPAU (nvidia 8600), the P4 can do it easily again.

I dont know what hardware you have, but you will either need to grab a card that can accelerate h264 decode (under linux, that means an nvidia card, and 8600 is a cheap way of getting there). Or you need a fairly fast CPU. Or you need to recode your vids and lower the maximum bitrate.

---

### Post by P4man on 2010-10-20
BTW, in xbmc you can see the bitrate and CPU usage by playing the vid and pressing O. Dont know how to do it in smplayer or vlc.

---

### Post by shantiq on 2010-10-20
-

---

### Post by P4man on 2010-10-20
There is no need for the OP to install XBMC (unless he wants to, its a great app!). The issue is the same with all mediaplayers, most of which even use the same backends. I just checked, in VLC you can see current bitrate by pressing control+i, and then go to statistics. Input bitrate is what you are looking for, and that will almost certainly correlate with skipping/stuttering on too slow hardware.

Anyway, if you want to install xmbc, just add the PPA for lucid. It works on maverick as well.

---

### Post by shantiq on 2010-10-20
was intrigued by cpu reader you mentioned p4   had to have a look  yes sorry might not be relevant to the question asked just thought might be useful for some to take a look at   seems a bit cumbersome a programme on my machine great tip on vlc for stats   i also cannot really play 720 and 1080 on my machine (serious stutter)not HD ready

AM I right in thinking that one needs to have an HD ready computer to play 720 and 1080 ?
maybe that is not true




===================================================

to install xbmc


```
sudo apt-get install python-software-properties pkg-config

``````
sudo add-apt-repository ppa:team-xbmc
```

found it was not happy on maverick so had to relabel to lucid in software sources

click on System->Administration->Synaptic Package Manager->Settings->Repositories->Other Software.

Select the first ppa for team-xbmc, then click on "Edit..."

Change the Distribution to "lucid". Click OK.
Select the 2nd ppa for team-xbmc, and make  the same change to "lucid".

```
sudo apt-get update
```
```
sudo apt-get install xbmc xbmc-standalone

``````
sudo apt-get update
```




==================================================================================================

---

### Post by shantiq on 2010-10-20
trying both the 720p and the 1080 on a youtube pink floyd vid


720p  ```
youtube-dl -t -f 22  http://www.youtube.com/watch?v=CjKU3HqpVdY&feature=related
```

1080p  ```
youtube-dl -t -b  http://www.youtube.com/watch?v=CjKU3HqpVdY&feature=related
```

i found the 720 just about goes through the 1080 simply does nor move enough
surely it has to be a hardware issue ?  or would really high cpu fix this notwithstanding the hardware?   currently using 2.5 gb ram


this must be the question

---

### Post by P4man on 2010-10-20
RAM has nothing to do with it. Its the cpu and videocard. I have to wonder what hardware you have, because the 1080p video ends up being 2-3 Mbit max, and unsurprisingly plays  effortlessly on both my desktop (core2duo 3 GHz ATI 4870) and laptop (core2duo 1.8 GHz with x3100 intel IGP), even when I underclock the laptop to 800 MHz.

edit: I was too quick. Some parts have 5 Mbit and near the end there seem to be a few brief moments where bitrate spikes up to 8 MBit. Still doesnt cause frame skipping on my laptop @800 Mhz though. Surprisingly. THe intel x3100 must do some hardware decode.

---

### Post by ron999 on 2010-10-20
Hi shantiq
The 1080 videos don't play nice with my PC either.
In my case it is a hardware thing.

That CrazyDiamond vid is available in 720p **webm** format too.
It looks OK with VLC or SMPlayer in fullscreen.
```
youtube-dl -t -f 45  http://www.youtube.com/watch?v=CjKU3HqpVdY&feature=related
```

---

### Post by P4man on 2010-10-20
> **ron999 said:**
> Hi shantiq
The 1080 videos don't play nice with my PC either.
In my case it is a hardware thing.

Out of curiousity, what hardware do you have? ATI videocard with a relatively slow (single core P4/A64) cpu?

---

### Post by shantiq on 2010-10-20
ok my bad:KS thought cpu was dependent on ram  is there anyway to increase the cpu?  so that i can play those higher formats


these are the specs of my computer

```
  description: Desktop Computer
    product: 00000000000000000000000
    vendor: Packard Bell NEC
    version: PB34225301
    serial: 049652320227
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=1 uuid=549D0B9A-BE69-DA11-8000-4E45435F4349
  *-core
       description: Motherboard
       product: MS-7168
       vendor: NEC COMPUTERS INTERNATIONAL
       physical id: 0
       version: 1.0
       slot: To Be Filled By O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 080012 (09/06/2005)
          size: 64KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification netboot
     *-cpu
          description: CPU
          product: AMD Athlon(tm) 64 Processor 3400+
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 15.15.2
          serial: To Be Filled By O.E.M.
          slot: CPU 1
          size: 2200MHz
          capacity: 2200MHz
          width: 64 bits
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt x86-64 3dnowext 3dnow up extd_apicid pni lahf_lm cpufreq
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 128KiB
             capabilities: pipeline-burst internal varies data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: pipeline-burst internal varies unified
     *-memory
          description: System Memory
          physical id: 2d
          slot: System board or motherboard
          size: 2560MiB
        *-bank:0
             description: DIMM DDR Synchronous 333 MHz (3.0 ns)
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: SerNum0
             slot: DIMM0
             size: 512MiB
             width: 64 bits
             clock: 333MHz (3.0ns)
        *-bank:1
             description: DIMM DDR Synchronous 333 MHz (3.0 ns)
             product: PartNum1
             vendor: Manufacturer1
             physical id: 1
             serial: SerNum1
             slot: DIMM1
             size: 1GiB
             width: 64 bits
             clock: 333MHz (3.0ns)
        *-bank:2
             description: DIMM DDR Synchronous 333 MHz (3.0 ns)
             product: PartNum2
             vendor: Manufacturer2
             physical id: 2
             serial: SerNum2
             slot: DIMM2
             size: 1GiB
             width: 64 bits
             clock: 333MHz (3.0ns)
        *-bank:3
             description: DIMM SDRAM [empty]
             product: PartNum3
             vendor: Manufacturer3
             physical id: 3
             serial: SerNum3
             slot: DIMM3
     *-generic UNCLAIMED
          physical id: 1
          bus info: parisc@1
     *-pci:0
          description: Host bridge
          product: RS480 Host Bridge
          vendor: ATI Technologies Inc
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 10
          width: 32 bits
          clock: 66MHz
        *-pci:0
             description: PCI bridge
             product: RS480 PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci ht normal_decode bus_master cap_list
             resources: ioport:7000(size=4096) memory:ff200000-ff2fffff ioport:cff00000(size=268435456)
           *-display
                description: VGA compatible controller
                product: RS480 [Radeon Xpress 200G Series]
                vendor: ATI Technologies Inc
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: pm vga_controller bus_master cap_list rom
                configuration: driver=radeon latency=64 mingnt=8
                resources: irq:17 memory:d0000000-d7ffffff ioport:7800(size=256) memory:ff2f0000-ff2fffff memory:ff2c0000-ff2dffff
        *-ide:0
             description: IDE interface
             product: IXP SB400 Serial ATA Controller
             vendor: ATI Technologies Inc
             physical id: 11
             bus info: pci@0000:00:11.0
             logical name: scsi0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm msi bus_master cap_list rom emulated
             configuration: driver=sata_sil latency=64
             resources: irq:23 ioport:bc00(size=8) ioport:b800(size=4) ioport:b400(size=8) ioport:b000(size=4) ioport:ac00(size=16) memory:ff6ffc00-ff6ffdff memory:ff600000-ff67ffff
           *-disk
                description: ATA Disk
                product: ST3500630AS
                vendor: Seagate
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 3.AA
                serial: 5QG10JMC
                size: 465GiB (500GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=000d7ce3
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /media/17d51555-8677-4283-98ed-ac23e8d0a8d4
                   version: 1.0
                   serial: 17d51555-8677-4283-98ed-ac23e8d0a8d4
                   size: 77GiB
                   capacity: 77GiB
                   capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2010-08-22 00:42:15 filesystem=ext4 lastmountpoint=/media/17d51555-8677-4283-98ed-ac23e8d0a8d4~&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;#&#65533;`>j modified=2010-10-20 13:50:22 mount.fstype=ext4 mount.options=rw,nosuid,nodev,relatime,barrier=1,data=ordered mounted=2010-10-20 13:50:22 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 362GiB
                   capacity: 362GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 7192MiB
                      capabilities: nofs
                 *-logicalvolume:1
                      description: Linux filesystem partition
                      physical id: 6
                      logical name: /dev/sda6
                      logical name: /
                      capacity: 342GiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered state=mounted
                 *-logicalvolume:2
                      description: Linux swap / Solaris partition
                      physical id: 7
                      logical name: /dev/sda7
                      capacity: 6337MiB
                      capabilities: nofs
              *-volume:2
                   description: Linux filesystem partition
                   vendor: Linux
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   version: 1.0
                   serial: 0287982d-1c73-4d64-8153-71b98cecf19b
                   size: 25GiB
                   capacity: 25GiB
                   capabilities: primary extended_attributes large_files ext2 initialized
                   configuration: filesystem=ext2 modified=2010-09-28 19:26:36 mounted=2010-09-28 19:26:36 state=clean
        *-ide:1
             description: IDE interface
             product: IXP SB400 Serial ATA Controller
             vendor: ATI Technologies Inc
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm msi bus_master cap_list rom
             configuration: driver=sata_sil latency=64
             resources: irq:22 ioport:a800(size=8) ioport:a400(size=4) ioport:a000(size=8) ioport:9c00(size=4) ioport:9800(size=16) memory:ff6ff800-ff6ff9ff memory:ff580000-ff5fffff
        *-usb:0
             description: USB Controller
             product: IXP SB400 USB Host Controller
             vendor: ATI Technologies Inc
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: msi ohci bus_master cap_list
             configuration: driver=ohci_hcd latency=64
             resources: irq:19 memory:ff6fe000-ff6fefff
        *-usb:1
             description: USB Controller
             product: IXP SB400 USB Host Controller
             vendor: ATI Technologies Inc
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: msi ohci bus_master cap_list
             configuration: driver=ohci_hcd latency=64
             resources: irq:19 memory:ff6fd000-ff6fdfff
        *-usb:2
             description: USB Controller
             product: IXP SB400 USB2 Host Controller
             vendor: ATI Technologies Inc
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm msi ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=64
             resources: irq:19 memory:ff6fc000-ff6fcfff
        *-serial
             description: SMBus
             product: IXP SB400 SMBus Controller
             vendor: ATI Technologies Inc
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 10
             width: 32 bits
             clock: 66MHz
             capabilities: ht cap_list
             configuration: driver=piix4_smbus latency=0
             resources: irq:0 ioport:b00(size=16) memory:a0000000-a00003ff
        *-ide:2
             description: IDE interface
             product: IXP SB400 IDE Controller
             vendor: ATI Technologies Inc
             physical id: 14.1
             bus info: pci@0000:00:14.1
             logical name: scsi5
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide msi bus_master cap_list emulated
             configuration: driver=pata_atiixp latency=64
             resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ff00(size=16)
           *-cdrom
                description: DVD writer
                product: DVD_RW ND-3550A
                vendor: _NEC
                physical id: 0.0.0
                bus info: scsi@5:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.52
                serial: [_NEC    DVD_RW ND-3550A 1.5205100300
                capabilities: removable audio cd-r cd-rw dvd dvd-r
                configuration: ansiversion=5 status=nodisc
        *-isa
             description: ISA bridge
             product: IXP SB400 PCI-ISA Bridge
             vendor: ATI Technologies Inc
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:1
             description: PCI bridge
             product: IXP SB400 PCI-PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master
             resources: ioport:8000(size=4096) memory:ff300000-ff3fffff
           *-communication
                description: Modem
                product: SmartLink SmartPCI562 56K Modem
                vendor: Smart Link Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 04
                width: 32 bits
                clock: 33MHz
                capabilities: pm generic bus_master cap_list
                configuration: driver=serial latency=64 maxlatency=62 mingnt=1
                resources: irq:20 memory:ff3ff000-ff3fffff ioport:8800(size=256)
           *-network
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 3
                bus info: pci@0000:02:03.0
                logical name: eth0
                version: 10
                serial: 00:13:d3:b6:0d:bb
                size: 100MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.0.100 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
                resources: irq:20 ioport:8400(size=256) memory:ff3fec00-ff3fecff memory:ff3e0000-ff3effff
           *-firewire
                description: FireWire (IEEE 1394)
                product: VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller
                vendor: VIA Technologies, Inc.
                physical id: 4
                bus info: pci@0000:02:04.0
                version: 80
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=64 maxlatency=32
                resources: irq:21 memory:ff3fe000-ff3fe7ff ioport:8c00(size=128)
        *-multimedia
             description: Multimedia audio controller
             product: IXP SB400 AC'97 Audio Controller
             vendor: ATI Technologies Inc
             physical id: 14.5
             bus info: pci@0000:00:14.5
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: msi bus_master cap_list
             configuration: driver=ATI IXP AC97 controller latency=64 mingnt=2
             resources: irq:17 memory:ff6ff400-ff6ff4ff
     *-pci:1
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp
          resources: irq:0
     *-scsi
          physical id: 2
          bus info: usb@2:4
          logical name: scsi6
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk:0
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@6:0.0.0
             logical name: /dev/sdb
        *-disk:1
             description: SCSI Disk
             physical id: 0.0.1
             bus info: scsi@6:0.0.1
             logical name: /dev/sdc
        *-disk:2
             description: SCSI Disk
             physical id: 0.0.2
             bus info: scsi@6:0.0.2
             logical name: /dev/sdd
        *-disk:3
             description: SCSI Disk
             physical id: 0.0.3
             bus info: scsi@6:0.0.3
             logical name: /dev/sde


```

---

### Post by shantiq on 2010-10-20
> **ron999 said:**
> Hi shantiq
The 1080 videos don't play nice with my PC either.
In my case it is a hardware thing.

That CrazyDiamond vid is available in 720p **webm** format too.
It looks OK with VLC or SMPlayer in fullscreen.
```
youtube-dl -t -f 45  http://www.youtube.com/watch?v=CjKU3HqpVdY&feature=related
```



hi ron    also found 720p was **just** just ok 1080 no way


vlc was cool but that xbmc seem to handle it perfect but still no 1080

are you saying webm goes through better than mp4 on yours?

---

### Post by P4man on 2010-10-20
> **shantiq said:**
> ok my bad:KS thought cpu was dependent on ram  is there anyway to increase the cpu?  so that i can play those higher formats

Probably not. You could try a dualcore Athlon64 X2 in the board, but most OEM machines (HP, Dell, Packard Bell etc) dont let you.

Your biggest bottleneck is probably not the CPU but the videocard though. You dont have one, it seems you have only a really crappy onboard graphics (ATI radeon xpress). 

If your motherboard has a PCI-Express or AGP slot, you could pick up a videocard on ebay that supports h264 decode under linux. As I wrote earlier, that means an nVidia 8600 or newer. That should let you play any movie file with ease, as well as enable compiz and all that, because I suspect you cant use that either now.

---

### Post by shantiq on 2010-10-20
amd 64 athlon is what i have but maybe we are talking about something else 

that amd 64 athlon i think is the core processor not sure not very aware of hardware (there is a sticker on the tower)


compiz is absolutely fine here

if you do not mind
can you say a bit more about [Nvidia card ]("http://ecx.images-amazon.com/images/I/51l8eCRUaGL.jpg") is it worth doing or should one wait until buying a new machine? and is there a way to know if i have PCI-Express or AGP slot or is it a case of opening the tower?

---

### Post by P4man on 2010-10-20
> **shantiq said:**
> amd 64 athlon is what i have but maybe we are talking about something else 

You have a single core Athlon 64. I was suggesting a dual core Athlon 64 X2, but I doubt it will work in your machine.

> 
if you do not mind
can you say a bit more about [Nvidia card ]("http://ecx.images-amazon.com/images/I/51l8eCRUaGL.jpg") is it worth doing or should one wait until buying a new machine? and is there a way to know if i have PCI-Express or AGP slot or is it a case of opening the tower?


Your manual should say it I guess. Or if you give the type of packard bell, we can probably look it up. Is it worth it? Well, is 40-50 euro or so worth it to you watch HD content? I cant answer that for you.

---

### Post by Messyhair42 on 2010-10-20
i have a Core 2 Duo 8400 3.0 GHZ and an ATI? video card with 512 MB

---

### Post by shantiq on 2010-10-20
probably really worth it

 Packard Bell NEC
    version: PB34225301

is all i know the manual is just a generic manual for all their products

---

### Post by P4man on 2010-10-20
> **Messyhair42 said:**
> i have a Core 2 Duo 8400 3.0 GHZ and an ATI? video card with 512 MB

Im surprised you cant play that video properly then. The ATI card is no help, but that cpu should be able to decode it in software

> probably really worth it

Packard Bell NEC
version: PB34225301


It appears to be this OEM board:

[http://www.pcupgrade.co.uk/productdetails.asp?productid=5229&categoryid=271](http://www.pcupgrade.co.uk/productdetails.asp?productid=5229&categoryid=271)

You can safely forget a dualcore cpu on that, but it seem to have one PCI-E slot. So that should work. Selecting a card can be tricky though. See here:
[http://en.wikipedia.org/wiki/Nvidia_PureVideo](http://en.wikipedia.org/wiki/Nvidia_PureVideo)

A geforce 8400 is about the minimum card to support VDPAU (h264 decode acceleration under linux). You can get those cheap, like here (Im assuming you are from the UK):
[http://www.overclockers.co.uk/showproduct.php?prodid=GX-132-GW&groupid=701&catid=56&subcat=1833](http://www.overclockers.co.uk/showproduct.php?prodid=GX-132-GW&groupid=701&catid=56&subcat=1833)

Id consider spending a tiny bit more on a card that can also serve in your next rig for some causal gaming, something like this:

[http://www.overclockers.co.uk/showproduct.php?prodid=GX-109-GW&groupid=701&catid=56&subcat=1009](http://www.overclockers.co.uk/showproduct.php?prodid=GX-109-GW&groupid=701&catid=56&subcat=1009)

(btw, check out the 'review' page, you may see why others buy it.. for VDPAU :) )

Or check ebay, lots of such cards selling there.

---

### Post by shantiq on 2010-10-20
thanx for info
motherboard is the one you said   

```
core
       description: Motherboard
       product: MS-7168
       vendor: NEC COMPUTERS INTERNATIONAL
       physical id: 0
       version: 1.0
       slot: To Be Filled By O.E.M.

```

will have a look around:KS

is this the place where it goes if you can see anything? and how is it connected to the rest of the machine are there connecting wires?


[IMG]http://img146.imageshack.us/img146/6605/1003358.jpg[/IMG][IMG]http://img251.imageshack.us/img251/8471/1003362.jpg[/IMG]

---

### Post by Messyhair42 on 2010-10-21
I was able to run one of the sort of choppy 1080p videos while running a new Maverick installation on a thumb drive perfectly, why shouldn't it work perfectly on my Lucid installation?

---

### Post by P4man on 2010-10-21
> **Messyhair42 said:**
> I was able to run one of the sort of choppy 1080p videos while running a new Maverick installation on a thumb drive perfectly, why shouldn't it work perfectly on my Lucid installation?

Are you testing the same video? 1080p doesnt tell half the story, the codec matters a lot, the bitrate maybe even more.

---

### Post by P4man on 2010-10-21
> **shantiq said:**
> tis this the place where it goes if you can see anything? 

No, that is a PCI slot. You need the black PCI-Express slot:
[IMG]http://imm.io/media/1I/1Ixx.jpg[/IMG]

 > and how is it connected to the rest of the machine are there connecting wires?

If you get a card that doesnt require more than 75W, then no, no other wires needed, just connect your monitor to the videocard.

Many 'powerful' videocards do require a power connector, sometimes severa.  that can be a molex connector like this:

[IMG]http://img296.imageshack.us/img296/8571/71933444bc0.jpg[/IMG]

Molex is used on older cards. Newer cards use a 6 pin PCI-E connector like this:

[IMG]http://www.techaddicts.net/reviews/sea_m12_500w/sea_m21.jpg[/IMG]

Highend cards often even require 2 such connectors. The cards I listed do not seem to require a power connector, and any card that draws < 75W should not, but make sure you have spare connectors if you buy a card that requires one.

You probably dont have a PCI-E power connector, but you can buy adaptors that go from molex to PCi-E and you can get splitters if you dont have any spare connectors (so you can 'split' the cable to your harddrive). Anyway, try to avoid high power cards that require additional connectors, your power supply may not be able to handle it.

---

### Post by cascade9 on 2010-10-21
> **P4man said:**
> Id consider spending a tiny bit more on a card that can also serve in your next rig for some causal gaming, something like this:

[http://www.overclockers.co.uk/showproduct.php?prodid=GX-109-GW&groupid=701&catid=56&subcat=1009](http://www.overclockers.co.uk/showproduct.php?prodid=GX-109-GW&groupid=701&catid=56&subcat=1009)

(btw, check out the 'review' page, you may see why others buy it.. for VDPAU :) )


IMO, dont get a 9800GT for VDPAU (less features than the older or newer cards). Its not a great idea to put a 9800GT in a 'corporate' computer as well, they tend to have very weak power supplies and poor case cooling, and 9800GTs use a lot of power and run pretty hot. 

If its just for VDPAU, a GT220 is a better choice. (best VDPAU feature set, not 64bit like the 8400GS + GT210, fairly low power requirements and heat output)

---

### Post by P4man on 2010-10-21
GT220 is fine for video, but then so is a cheaper 8400 GS (the differences in VDPAU support seem pretty minor to me, mostly support for oddball resolutions no one uses). 

The 9800GT green edition I linked to, isnt a powerhog at all, its underclocked and it doesnt even require a PCI-E connector (so its <75W). I picked it exactly because I figured his PSU wouldnt support a power hog. Unlike the GT220, that card is still pretty usable for games and its about the same price. Easy choice if you ask me.

---

### Post by cascade9 on 2010-10-21
> **P4man said:**
> GT220 is fine for video, but then so is a cheaper 8400 GS (the differences in VDPAU support seem pretty minor to me, mostly support for oddball resolutions no one uses). 

The 9800GT green edition I linked to, isnt a powerhog at all, its underclocked and it doesnt even require a PCI-E connector (so its <75W). I picked it exactly because I figured his PSU wouldnt support a power hog. Unlike the GT220, that card is still pretty usable for games and its about the same price. Easy choice if you ask me.

Some of the 64bit nVidia cards (8300/8400GS, 9300GS, GT205/GT210) arent so great at VDPAU. They work, but sometimes have issues (frame drops, etc IIRC). I havent had any issues with VDPAU on a 8400GS, but that doesnt prove that some people dont have issues. I dont try to push much 720p content throught the 8400GS as well, and I dont think I have any 1080p content at all apart from a test video....IIRC its 1080p where the 64bit cards start to struggle. 

I've never seen a head to head comparison of the 9800GT vs the 9800GT 'green edition' so this is semi speculation.

The '9800GT GE' runs about 10% less speed on the core and shaders. Memory runs at the same speed (well, in most cases, there are some with slower memory as well). I'd doubt that a 10% decease in core/shaders will give much more than a 20% drop in power consumption. Even with calling it 20% (and thats generous IMO) a 9800GT GE will still suck about as much power at idle as the GT220 would at full 3D gaming loads- 

[http://www.xbitlabs.com/articles/video/display/htpc-graphics-cards_4.html#sect0](http://www.xbitlabs.com/articles/video/display/htpc-graphics-cards_4.html#sect0)

BTW, I wouldnt call it 'underclocked' as thats the factory speeds, but anyway...  

9800GTs ARE power hogs. Nice gamers cards, but not a great choice for non-gamers. If shantiq is a gamer, then it might be worth it, but I doubt that shantiq is a gamer (too busy transcoding audio files to play games LOL). Not that you ned a 9800GT for 'casual gaming' anyway.

---

### Post by shantiq on 2010-10-21
9800 too expensive for me and i really never use games   (52 years old :KS:KS and yes cascade too busy with audio conversions :KS:KS)

GT220   there is [one here]("http://cgi.ebay.co.uk/PNY-GT220-Graphics-Card-/330486968871?pt=UK_Computing_Computer_Components_Graphics_Video_TV_Cards_TW&hash=item4cf28ef227#ht_500wt_1156") is this the right beast? it seems awfully big with fan not just a card

where can i find this as just a card  pm me if this info not appropriate here although it might be of use to many others

---

### Post by cascade9 on 2010-10-21
> **shantiq said:**
> 9800 too expensive for me and i really never use games   (52 years old :KS:KS)

GT220   there is [one here]("http://cgi.ebay.co.uk/PNY-GT220-Graphics-Card-/330486968871?pt=UK_Computing_Computer_Components_Graphics_Video_TV_Cards_TW&hash=item4cf28ef227#ht_500wt_1156") is this the right beast? it seems awfully big with fan not just a card

where can i find this as just a card  pm me if this info not appropriate here although it might be of use to many others

They arent that big......you should see the monster card my sisters is running (a 9800GX2). :lolflag: 

As for where to find it...try staticice (UK)- 

[http://www.staticice.co.uk/cgi-bin/search.cgi?q=GT220&spos=3](http://www.staticice.co.uk/cgi-bin/search.cgi?q=GT220&spos=3)

I've been pasting that link up everytime I see someone from the UK after hardware. I use the australian version quite often, great site. You should be able to find some local store with a decent price, or failing that, get one mailed to you (postman pat...where is that b!st!rd with my video card)

---

### Post by P4man on 2010-10-21
> **cascade9 said:**
> Some of the 64bit nVidia cards (8300/8400GS, 9300GS, GT205/GT210) arent so great at VDPAU. They work, but sometimes have issues (frame drops, etc IIRC). I havent had any issues with VDPAU on a 8400GS, but that doesnt prove that some people dont have issues. I dont try to push much 720p content throught the 8400GS as well, and I dont think I have any 1080p content at all apart from a test video....IIRC its 1080p where the 64bit cards start to struggle. 

Have a look at these testimonials:
[http://forum.xbmc.org/showthread.php?t=61218](http://forum.xbmc.org/showthread.php?t=61218)

They have no issues playing 1080p with a PCI version of the 8400GS and stone age CPU's (pentium III and even a 1 GHz geode !!) with still very low CPU loads.

Anyway, its up to the OP. 8400GS is the cheapest route to smooth 1080p h264 playback, but Im not saying it cant be worth spending a tiny bit more.

> The '9800GT GE' runs about 10% less speed on the core and shaders. Memory runs at the same speed (well, in most cases, there are some with slower memory as well). I'd doubt that a 10% decease in core/shaders will give much more than a 20% drop in power consumption.

10% lower core = 10% lower power consumption **at equal voltage**. Here is the kicker, lowering the core by a tiny bit can enable you to drop voltage disproprortionally. Any overclocker knows the opposite effect of this, increasing vcore helps overclock, but a 10% increase in vcore results in nowhere near 10% extra clock. Power consumption scales with voltage exponentially.  The end result is likely a bigger drop than 20%. 

Either way, since the card has no PCI-E or molex connectors, its cant draw more than 75W no matter what (thats the limit of the PCI-E bus). 75W is more than a GT220, but I wouldnt call that a power hog, and I would expect an OEM power supply to be able to cope with that.

Oh well. I guess shantiq has all the info he needs now, and more, its up to him to decide what suits him best.

---

### Post by cascade9 on 2010-10-21
> **P4man said:**
> Have a look at these testimonials:
[http://forum.xbmc.org/showthread.php?t=61218](http://forum.xbmc.org/showthread.php?t=61218)

They have no issues playing 1080p with a PCI version of the 8400GS and stone age CPU's (pentium III and even a 1 GHz geode !!) with still very low CPU loads.

Anyway, its up to the OP. 8400GS is the cheapest route to smooth 1080p h264 playback, but Im not saying it cant be worth spending a tiny bit more.

Testimonials =/=reality. 

If testimonials were all that mattered, then depending on what posts you look at in the T&E section here, ubuntu is 100% perfect, or 100% wrong LOL. 

I'll see if I can dig up where I heard the reports of 8400s (etc) dropping frames. 

> **P4man said:**
> 10% lower core = 10% lower power consumption **at equal voltage**. Here is the kicker, lowering the core by a tiny bit can enable you to drop voltage disproprortionally. Any overclocker knows the opposite effect of this, increasing vcore helps overclock, but a 10% increase in vcore results in nowhere near 10% extra clock. Power consumption scales with voltage exponentially.  The end result is likely a bigger drop than 20%. 

I've been underclocking (and overclocking) for a long time now. Trying to push a chip past the design point takes a lot more voltage than you can skim off when you drop the clocks. 

Without a decent power consumption comparison between a 9800GT and a 980GT GE, this is pure speculation.   

> **P4man said:**
> Either way, since the card has no PCI-E or molex connectors, its cant draw more than 75W no matter what (thats the limit of the PCI-E bus). 75W is more than a GT220, but I wouldnt call that a power hog, and I would expect an OEM power supply to be able to cope with that.

You did look at the power consumption comparison I posted before, right? 

Even if the 9800GT GE was 30% lower in power consumption the 9800 GT will still use a lot more power. BTW, the test was with a G92B 9800GT. 16.1/42.1/60.1 watts (idle/HD video decode/full 3D game load). Thats a lot more than a GT220s 5.1/13.5/21.9. (on average, its 3 times the draw of a GT220). 

That, in my book, is a power hog. 

I'd be really wary of pushing OEM power supplies that hard.....to be honest, I'd evern think about replacing the power supply to put in a GT220 in a lot of cases.

---

### Post by P4man on 2010-10-21
Since the OP has already said he is not interested in gaming or anything else 3d, this discussion is moot as there is no point in a more expensive and (indeed) hotter 9800 over a GT220 or even slower card. For a (potential) gamer, IMO its definitely a worthwhile trade-off, but lets just agree to disagree on that.

BTW, wikipedia says recent Via Chrome cards also have VDPAU support:
[http://en.wikipedia.org/wiki/VDPAU](http://en.wikipedia.org/wiki/VDPAU)

That surprised me. Last time I tried to get a chrome (admitedly, an IGP)  under linux I struggled to get any 2D working at all. You know anything about newer cards and how they perform and their linux support? Could be an interesting low power and cheap alternative for the adventurous types :)

---

### Post by cascade9 on 2010-10-21
VIA added support for VDPAU? *blinks*. Odd, but nice of them. 

Honestly, I dont know that much about the newer VIA stuff. I havent seen much of it, mostly VIA was overpriced here, and the the 'low power' end of things has been dominated by Atom since it release. 

The only time I used VIA video on a machine I owned, the experience lasted about 15 minutes. Power down, install a ATI/nVidia (cant remember which LOL) AGP card, power back up......thats better :D  

> **P4man said:**
> Since the OP has already said he is not interested in gaming or anything else 3d, this discussion is moot as there is no point in a more expensive and (indeed) hotter 9800 over a GT220 or even slower card. For a (potential) gamer, IMO its definitely a worthwhile trade-off, but lets just agree to disagree on that.

Hey, dont get me wrong...the 9800GTs are good cards for gamers, though right now unless its a 'desperation' buy saving your money for a GTX460 would be better.

---

### Post by P4man on 2010-10-21
A 460 is definitely nice and a pair of them high on my wish list, but its also 2 or 3x as expensive and keep in mind the OP has a single core  Athlon 64 2.2 GHz. That wouldnt do a 460 justice.

I picked the 9800 because its dirt cheap, ubiquitous on ebay, fast enough for most games and has good VDPAU support. The green version likely wouldnt cause PSU trouble. I just saw it as a good stop gap compromise if he wanted to keep gaming options open and not spend more on a PC that he is considering replacing anyhow.  And a gamer could hang on to it even when buying a new PC, buy using it as an excellent PhysX card.

But enough of that now :)

---

### Post by shantiq on 2010-10-24
ok p4   had a good look around and found this


MSI NVIDIA 8400GS 512MB 64BIT DDR2 FAN PCI-E GRAPHICS CARD

would this be ok do you think  is the 64bit ok?

and then looking inside the tower

[CENTER][IMG]http://img541.imageshack.us/img541/6456/msinvidia8400gspic.jpg[/IMG][/CENTER]


place it at first arrow comes out out second

then connect monitor to new socket at front of the tower with lead which currently comes out of the back with the 2 screws


hope i have got all this right/?    available for around 30 $/£/euro    so well worth the effort    thanx for help from both


ps will i need the drivers from the software centre?

---

### Post by P4man on 2010-10-24
> **shantiq said:**
> ok p4   had a good look around and found this


MSI NVIDIA 8400GS 512MB 64BIT DDR2 FAN PCI-E GRAPHICS CARD

would this be ok do you think  is the 64bit ok?

SHould be okay. Its not exactly the fastest card out there, but should do for VDPAU. The 64 bit here just refers to the wideness of the memory controller of the videocard. Wider is faster, 64 bit isnt wide for a GPU, midrange GPUs will have 128 or 256 bit interfaces, highend ones 384 or more. But thats not too important for you, and it has absolutely nothing to do with i386 / AMD64  ubuntu 32 bit or 64 bit. That something else completely, dont worry about it.

> 
and then looking inside the tower

place it at first arrow comes out out second

then connect monitor to new socket at front of the tower with lead which currently comes out of the back with the 2 screws

hope i have got all this right/?


Pretty much. Have a look here:
[http://www.youtube.com/watch?v=O9x097QRXeA&feature=related](http://www.youtube.com/watch?v=O9x097QRXeA&feature=related)

>  will i need the drivers from the software centre?

Yes. I dont know if you are using proprietary drivers now, but if you are, disable them before inserting the new card. Go to system > administration > additional drivers. Disable ATI drivers if they are active now. Then with the new card, go to the same app, and you should be presented with the option to install nVidia proprietary drivers. Select the "current" version, activate them, reboot and that should be about it.

---

### Post by shantiq on 2010-10-26
ok did it


well worth the effort
plumped for even cheaper card in the end
Palit nVidia GeForce 8400GS 256MB Graphics Card


plays 720p in mplayer/vlc/smplayer    but only plays 1080p flawlessly i might add in [xbmc]("http://ubuntuforums.org/showpost.php?p=9999878&postcount=6")   so really glad i installed it

---

### Post by P4man on 2010-10-26
make sure VDPAU support is installed. You probably have them already, but run this:

```
sudo apt-get install vdpau-va-driver libvdpau1
```

For SMPlayer, enable it in tools > preferences > video > output driver > vdpau

In VLC im not entirely sure and there seem to be some bug reports open on it but  experiment with these two settings:

Tools > Preferences > Video, select "Accelerated Video Output" 
Tools > Preferences > input & codecs > use GPU acceleration

Check your CPU useage in system monitor, if VPDAU is working correctly, cpu load should be extremely low.

In XMBC its usually enabled by default if you have it set to "auto" and that seems to work for you.

---

### Post by shantiq on 2010-10-26
:KS   smplayer really happy with that on most 1080p although on some of the mp4 files it gives me a grey/blanked out thing

or seems to go in audio and not pick it up as a vid


vlc not reALLy getting there with 1080p but hey xbmc and smplayer will certainly do for the time being


again ta for all info provided\:KS


also found this on wiki

[COLOR=#000000][FONT=sans-serif]**Software supporting VDPAU**


[LIST]
[*][Boxee]("http://ubuntuforums.org/wiki/Boxee") ([Linux]("http://ubuntuforums.org/wiki/Linux"))[[12]]("http://ubuntuforums.org/#cite_note-11")
[*][GStreamer]("http://ubuntuforums.org/wiki/GStreamer")[[13]]("http://ubuntuforums.org/#cite_note-Fluendo_Codec_Pack-12")
[*][MPlayer]("http://ubuntuforums.org/wiki/MPlayer")
[*][MythTV]("http://ubuntuforums.org/wiki/MythTV") ([Linux]("http://ubuntuforums.org/wiki/Linux"))[[14]]("http://ubuntuforums.org/#cite_note-13")
[*][XBMC Media Center]("http://ubuntuforums.org/wiki/XBMC_Media_Center") ([Linux]("http://ubuntuforums.org/wiki/Linux"))[[15]]("http://ubuntuforums.org/#cite_note-xbmc.org-14")[[16]]("http://ubuntuforums.org/#cite_note-ReferenceA-15")[[17]]("http://ubuntuforums.org/#cite_note-16")
[*][XBMC Live]("http://ubuntuforums.org/wiki/XBMC_Live") (Linux Live CD/USB operating-system)[[15]]("http://ubuntuforums.org/#cite_note-xbmc.org-14")[[16]]("http://ubuntuforums.org/#cite_note-ReferenceA-15")[[18]]("http://ubuntuforums.org/#cite_note-17")
[*][Xine]("http://ubuntuforums.org/wiki/Xine") ([Linux]("http://ubuntuforums.org/wiki/Linux"))[[19]]("http://ubuntuforums.org/#cite_note-18")[[20]]("http://ubuntuforums.org/#cite_note-19")
[*][MLT]("http://ubuntuforums.org/wiki/Media_Lovin%27_Toolkit") ([Linux]("http://ubuntuforums.org/wiki/Linux"))[[21]]("http://ubuntuforums.org/#cite_note-20")
[/LIST]
[/FONT][/COLOR]

---

### Post by cascade9 on 2010-10-29
There was a way to sort of get at least some hardware video decoding with VLC, using VA-API. 

IIRC there was some work toward actually getting VDPAU working on VLC, and there was a VDPAU VLC patch, but I never tried it.

---

### Post by P4man on 2010-10-29
shantiq, out of curiousity, what  CPU load are you getting in xbmc now ?   Can you play a h264 fragment with at least 8-10 Mbit stream and tell me how much CPU load xbmc reports?

---

### Post by shantiq on 2010-10-31
ok so on a 1080p vid i get 55 to 65% cpu and  vdcpu about 1%

i hope this is the info you were seeking  :KS

---

### Post by shantiq on 2010-11-10
an issue has come up using the nvidia card


any ideas?




Code:
```

ffmpeg -f alsa -ac 2 -i pulse -f x11grab -r 30 -s 1024x768 -i :0.0 -acodec pcm_s16le -vcodec libx264 -vpre lossless_ultrafast -threads 0 ./Desktop/mydesktop.mkv
```



does not work anymore any idea why; the image is all garbled ; i have no idea why




any thoughts/fixes?

ps screenshot of what i get

---

