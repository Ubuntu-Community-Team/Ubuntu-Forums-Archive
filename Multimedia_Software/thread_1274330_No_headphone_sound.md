---
title: "No headphone sound"
date: 2009-09-24
forum: Multimedia Software
---

### Post by squeak24 on 2009-09-24
OK, I am very new to xubuntu.  I have had enough of paying MS for stuff I don't really need so thought I would try xubuntu.  And from what I have seen, I like.

The one problem I am having, and have noticed other people have also had this problem, is that I can get sound out of my laptop speakers, but I can't get anything out of my headphones.  I work in Radio so it is vital that I can use the headphone socket on my computer.  It also helps when making Skype calls as well. I have tried other solutions but none that I have found seem to work.  One even disabled sound completely so had to do a fresh install.  I have been trying to sort this out for about two weeks now and can't figure it out.  Like I say I can hear stuff through the inbuilt speakers, but not the headphone socket.  In reality if it was the other way round I would not be concerned as I don't normally use the laptop speakers.  The microphone jack is ok, just the headphone jack that isn't happy

My sound card is

```

@bob-xubuntu:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC861VD Analog [ALC861VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```These are my system specs

```


@bob-xubuntu:~$ sudo lshw
bob-xubuntu               
    description: Notebook
    product: Satellite A135
    vendor: TOSHIBA
    version: PSAD0U-0N500N
    serial: 5757568758675K
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: boot=oem-specific chassis=notebook cpus=1 uuid=27793FD0-32F2-11DC-90D3-001B381C6D4D
  *-core
       description: Motherboard
       product: IAKAA
       vendor: TOSHIBA
       physical id: 0
       version: 1.00
       serial: 0123456789AB
       slot: &#65533;
     *-firmware
          description: BIOS
          vendor: TOSHIBA
          physical id: 0
          version: V1.60 (07/05/2007)
          size: 105KiB
          capacity: 448KiB
          capabilities: pci pcmcia pnp upgrade shadowing cdboot bootselect int13floppytoshiba int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp smartbattery biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Celeron(R) M CPU        520  @ 1.60GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.6.1
          serial: 0001-0661-0000-0000-0000-0000
          slot: U2E1
          size: 1600MHz
          capacity: 2048MHz
          width: 64 bits
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss tm pbe x86-64 constant_tsc up arch_perfmon pebs bts pni dtes64 monitor ds_cpl tm2 ssse3 cx16 xtpr pdcm lahf_lm
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1 Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2 Cache
             size: 1MiB
             capabilities: burst external write-back
     *-memory
          description: System Memory
          physical id: d
          slot: System board or motherboard
          size: 512MiB
          capacity: 3GiB
        *-bank:0
             description: SODIMM DDR Synchronous
             physical id: 0
             slot: M1
             size: 512MiB
             width: 32 bits
        *-bank:1
             description: SODIMM DDR Synchronous [empty]
             physical id: 1
             slot: M2
     *-pci
          description: Host bridge
          product: Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-display:0 UNCLAIMED
             description: VGA compatible controller
             product: Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: msi pm bus_master cap_list
             configuration: latency=0
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
        *-multimedia
             description: Audio device
             product: 82801G (ICH7 Family) High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel
        *-pci:0
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:1
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Wireless interface
                product: AR242x 802.11abg Wireless PCI Express Adapter
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:04:00.0
                logical name: wmaster0
                version: 01
                serial: 00:19:7e:c0:70:e4
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
                configuration: broadcast=yes driver=ath5k_pci ip=192.168.1.2 latency=0 module=ath5k multicast=yes wireless=IEEE 802.11bg
        *-pci:2
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Ethernet interface
                product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:05:00.0
                logical name: eth0
                version: 01
                serial: 00:1b:38:1c:6d:4d
                size: 10MB/s
                capacity: 100MB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no module=r8169 multicast=yes port=MII speed=10MB/s
        *-usb:0
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: 82801G (ICH7 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:3
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e2
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
           *-pcmcia
                description: CardBus bridge
                product: PCIxx12 Cardbus Controller
                vendor: Texas Instruments
                physical id: 4
                bus info: pci@0000:06:04.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192 module=yenta_socket
           *-firewire
                description: FireWire (IEEE 1394)
                product: PCIxx12 OHCI Compliant IEEE 1394 Host Controller
                vendor: Texas Instruments
                physical id: 4.1
                bus info: pci@0000:06:04.1
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=ohci1394 latency=32 maxlatency=4 mingnt=2 module=ohci1394
           *-storage
                description: Mass storage controller
                product: 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
                vendor: Texas Instruments
                physical id: 4.2
                bus info: pci@0000:06:04.2
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: storage pm bus_master cap_list
                configuration: driver=tifm_7xx1 latency=57 maxlatency=4 mingnt=7 module=tifm_7xx1
           *-system
                description: SD Host controller
                product: PCIxx12 SDA Standard Compliant SD Host Controller
                vendor: Texas Instruments
                physical id: 4.3
                bus info: pci@0000:06:04.3
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=sdhci-pci latency=57 maxlatency=4 mingnt=7 module=sdhci_pci
        *-isa
             description: ISA bridge
             product: 82801GBM (ICH7-M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801GBM/GHM (ICH7 Family) SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             logical name: scsi1
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0
           *-disk
                description: ATA Disk
                product: TOSHIBA MK8037GS
                vendor: Toshiba
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: DL23
                serial: 776WT0KHT
                size: 74GiB (80GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=bde2c901
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: 684cbe5e-a041-5e4c-8e4c-d7732f75c1ef
                   size: 59GiB
                   capacity: 59GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2009-02-12 12:27:12 filesystem=ntfs label=SQ004508V01 state=clean
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 14GiB
                   capacity: 14GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux filesystem partition
                      physical id: 5
                      logical name: /dev/sda5
                      logical name: /
                      capacity: 13GiB
                      configuration: mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered state=mounted
                 *-logicalvolume:1
                      description: Linux swap / Solaris partition
                      physical id: 6
                      logical name: /dev/sda6
                      capacity: 674MiB
                      capabilities: nofs
           *-cdrom
                description: DVD-RAM writer
                product: DVD-RAM UJ-850S
                vendor: MATSHITA
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.90
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-serial UNCLAIMED
             description: SMBus
             product: 82801G (ICH7 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
     *-scsi
          physical id: 1
          bus info: usb@1:5
          logical name: scsi2
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             product: 1600BEV External
             vendor: WD
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sdb
             version: 1.05
             serial: WD-WXE408FW0687
             size: 149GiB (160GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=4 signature=8f9c798a
           *-volume
                description: Windows FAT volume
                vendor: MSWIN4.1
                physical id: 1
                bus info: scsi@2:0.0.0,1
                logical name: /dev/sdb1
                logical name: /media/My Passport
                version: FAT32
                serial: 0767-40f5
                size: 149GiB
                capacity: 149GiB
                capabilities: primary fat initialized
                configuration: FATs=2 filesystem=fat label=My Passport mount.fstype=vfat mount.options=rw,nosuid,nodev,uid=1000,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=winnt,utf8 state=mounted
  *-battery
       description: Lithium Ion Battery
       product: PA3395U
       vendor: TOSHIBA
       physical id: 1
       version: 12/01/2005
       serial: 3658Q
       slot: 1st Battery
       capacity: 31500mWh
       configuration: voltage=14.8V
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 3e:14:56:ca:86:0f
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```Any help is greatly received

---

### Post by khelben1979 on 2009-09-24
[Pulse audio]("http://en.wikipedia.org/wiki/Pulse_audio") is the solution. I suggest you spend time on learning how it works.

I have no experience on using this myself and the fast solution is that you get yourself an usb headset instead.

---

### Post by squeak24 on 2009-09-24
OK, I will look into pulseaudio

OK, I have installed pulseaudio, and I am still not getting anything through the headphones.  I have tried other methods and still northing.

I have found this thread

[B][http://ubuntuforums.org/showthread.php?p=5159019&highlight=ALC861VD#post5159019](http://ubuntuforums.org/showthread.php?p=5159019&highlight=ALC861VD#post5159019)

[/B]But this doesn't give anything for the sound card which I have.

Any help is greatly recevied

---

### Post by khelben1979 on 2009-09-24
According to [this place]("http://www.linuxforums.org/forum/gentoo-linux-help/99291-intel-82801g-ich7-family-high-definition-audio-controller-microphone-problem.html"), they got it solved by choosing the default sound through the application alsaconf.
[URL="http://www.google.se/search?q=82801G+with+linux&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a"]
I made a google search[/URL] on your sound chip which was provided by your hardware list. I believe you might even try to pm any of the members of that forum to see what they say if you're in a hurry.

---

### Post by squeak24 on 2009-09-25
Looks like it may be a Kernel I am trying this out on isn't vital if anything goes wrong so I am going to try and update my Kernel to the latest version, just need to figure out how to do that now.

---

### Post by markharding557 on 2009-09-25
i have had this problem found out the headphone jack works on intrepid another option for you if you don't mind a bit older version of ubuntu

---

### Post by squeak24 on 2009-09-25
I will have a look at that, I have to re-install tomorrow as I did something and have no sound at all now.  I thought it would be wise not to go with upgrading the kernal software as it looked a bit to complicated, especially being a newbie here.

How come this is a problem which causes problems, does the netbook version correct with it being especially for portable devices.

OK, I downloaded to intrepid, but I still get the same problem.  I think I will try it on a pre 2005 laptop to see if that does anything.

If anyone can think of anything I can do to make this work it would be greatly received.  Not vital at the moment, I may try USB headphones or sound card see if that does anything.

I down graded to Intrepid, but the headphone jack still doesn't work.  

I have tried adding 

```

options snd-hda-intel model=toshiba-satellite-a135-s4656

```

which from what I have read shoudl work, but it doesn't in my case.  My computer is a Toshiba Satellite A135-S4656 I am unsure if this is the model I need to indicate.

Does anyone know how I can get the headphones to work.  I don't really want to go down the route of USB headphones as you can't get the same sound quality out of them.

I would like to use UBUNTU in a business venture which will rely heavily on listening to audio on trains and other forms of public transport so it is vital that I can get the headphone jack to work.

Any help is greatly appreciated.

Finally got the headphone issue resolved thanks to this thread [https://answers.launchpad.net/ubuntu/+question/15343](https://answers.launchpad.net/ubuntu/+question/15343)

In /etc/modprobe.d/alsa-base.conf at the end I have simply added "options snd-hda-intel model=lenovo"

This is using UBUNTU 9.04.

Just need to make sure the mic works ok now.

This doesn't mute the front speakers but this can be changed in the volume control and it still comes out of the headphones.

Many thanks for all your help

---

