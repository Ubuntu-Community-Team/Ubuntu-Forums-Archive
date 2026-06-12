---
title: "built-in webcam not working on ubuntu 14.04 / acer travelmate 5735z"
date: 2014-07-12
forum: Multimedia Software
---

### Post by vida_utopia on 2014-07-12
Hi everybody,

I have just installed ubuntu 14.04, works great now, except it won't find the webcam. It's an Acer Travelmate 5735z notebook. I have nowhere found this topic in any forum.. even cheese doesn't find the cam. I had Kubuntu 13.04 before, the webcam worked. I don't even find any options about the webcam in the system preferences. when i run cheese, the error says "the camera is already in use/occupied":

> 
libv4l2: error setting pixformat: Das Gerät oder die Ressource ist belegt

(cheese:18214): cheese-WARNING **: Gerät »/dev/video0« ist belegt: gstv4l2object.c(2524): gst_v4l2_object_set_format (): /GstCameraBin:camerabin/GstWrapperCameraBinSrc:camera_source/GstBin:bin17/GstV4l2Src:video_source:
Call to S_FMT failed for YU12 @ 1280x1024: Das Gerät oder die Ressource ist belegt


what can i do?
thanks, greetings

---

### Post by vida_utopia on 2014-07-12
Here is my lshw:

```
Beschreibung: Notebook
    Produkt: TravelMate 5735Z (Montevina_Fab)
    Hersteller: Acer
    Version: V1.00
    Seriennummer: LXV0K0C00104030CFA1601
    Breite: 32 bits
    Fähigkeiten: smbios-2.4 dmi-2.4
    Konfiguration: boot=normal chassis=notebook family=Intel_Mobile sku=Montevina_Fab uuid=168411CE-C556-11DF-AB43-1C7508023004
  *-core
       Beschreibung: Hauptplatine
       Produkt: BA51_MV
       Hersteller: Acer
       Physische ID: 0
       Version: V1.00
       Seriennummer: Base Board Serial Number
       Steckplatz: Base Board Chassis Location
     *-firmware
          Beschreibung: BIOS
          Hersteller: Acer
          Physische ID: 0
          Version: V1.00
          date: 09/013/2010
          Größe: 1MiB
          Kapazität: 1984KiB
          Fähigkeiten: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppynec int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int9keyboard int10video acpi usb
     *-memory
          Beschreibung: Systemspeicher
          Physische ID: 14
          Steckplatz: Systemplatine oder Hauptplatine
          Größe: 4GiB
        *-bank:0
             Beschreibung: SODIMM DDR2 Synchron 667 MHz (1,5 ns)
             Produkt: E6E6E6E6E6E6E6E6E6E6E6E6E6E6E6E6E6E6
             Hersteller: Kinston
             Physische ID: 0
             Seriennummer: 2F224EE6
             Steckplatz: DIMM0
             Größe: 2GiB
             Breite: 64 bits
             Takt: 667MHz (1.5ns)
        *-bank:1
             Beschreibung: SODIMM DDR2 Synchron 667 MHz (1,5 ns)
             Produkt: DCDCDCDCDCDCDCDCDCDCDCDCDCDCDCDCDCDC
             Hersteller: Kinston
             Physische ID: 1
             Seriennummer: 791446DC
             Steckplatz: DIMM2
             Größe: 2GiB
             Breite: 64 bits
             Takt: 667MHz (1.5ns)
     *-cpu
          Beschreibung: CPU
          Produkt: Pentium(R) Dual-Core CPU       T4500  @ 2.30GHz
          Hersteller: Intel Corp.
          Physische ID: 1f
          Bus-Informationen: cpu@0
          Version: 6.7.10
          Seriennummer: 0001-067A-0000-0000-0000-0000
          Steckplatz: uPGA-478
          Größe: 2300MHz
          Kapazität: 2300MHz
          Breite: 64 bits
          Takt: 200MHz
          Fähigkeiten: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm xsave lahf_lm dtherm cpufreq
          Konfiguration: id=0
        *-cache:0
             Beschreibung: L2 Cache
             Physische ID: 20
             Steckplatz: L2 Cache
             Größe: 1MiB
             Kapazität: 1MiB
             Fähigkeiten: synchronous internal write-back unified
        *-cache:1
             Beschreibung: L1 Cache
             Physische ID: 22
             Steckplatz: L1 Cache
             Größe: 32KiB
             Kapazität: 32KiB
             Fähigkeiten: synchronous internal write-back data
        *-logicalcpu:0
             Beschreibung: Logische CPU
             Physische ID: 0.1
             Breite: 64 bits
             Fähigkeiten: logical
        *-logicalcpu:1
             Beschreibung: Logische CPU
             Physische ID: 0.2
             Breite: 64 bits
             Fähigkeiten: logical
     *-cache
          Beschreibung: L1 Cache
          Physische ID: 21
          Steckplatz: L1 Cache
          Größe: 32KiB
          Kapazität: 32KiB
          Fähigkeiten: synchronous internal write-back instruction
     *-pci
          Beschreibung: Host bridge
          Produkt: Mobile 4 Series Chipset Memory Controller Hub
          Hersteller: Intel Corporation
          Physische ID: 100
          Bus-Informationen: pci@0000:00:00.0
          Version: 09
          Breite: 32 bits
          Takt: 33MHz
          Konfiguration: driver=agpgart-intel
          Ressourcen: irq:0
        *-display:0
             Beschreibung: VGA compatible controller
             Produkt: Mobile 4 Series Chipset Integrated Graphics Controller
             Hersteller: Intel Corporation
             Physische ID: 2
             Bus-Informationen: pci@0000:00:02.0
             Version: 09
             Breite: 64 bits
             Takt: 33MHz
             Fähigkeiten: msi pm vga_controller bus_master cap_list rom
             Konfiguration: driver=i915 latency=0
             Ressourcen: irq:43 memory:d0000000-d03fffff memory:c0000000-cfffffff ioport:4110(Größe=8)
        *-display:1 UNGEFORDERT
             Beschreibung: Display controller
             Produkt: Mobile 4 Series Chipset Integrated Graphics Controller
             Hersteller: Intel Corporation
             Physische ID: 2.1
             Bus-Informationen: pci@0000:00:02.1
             Version: 09
             Breite: 64 bits
             Takt: 33MHz
             Fähigkeiten: pm bus_master cap_list
             Konfiguration: latency=0
             Ressourcen: memory:d3400000-d34fffff
        *-usb:0
             Beschreibung: USB controller
             Produkt: 82801I (ICH9 Family) USB UHCI Controller #4
             Hersteller: Intel Corporation
             Physische ID: 1a
             Bus-Informationen: pci@0000:00:1a.0
             Version: 03
             Breite: 32 bits
             Takt: 33MHz
             Fähigkeiten: uhci bus_master cap_list
             Konfiguration: driver=uhci_hcd latency=0
             Ressourcen: irq:20 ioport:40c0(Größe=32)
        *-usb:1
             Beschreibung: USB controller
             Produkt: 82801I (ICH9 Family) USB UHCI Controller #5
             Hersteller: Intel Corporation
             Physische ID: 1a.1
             Bus-Informationen: pci@0000:00:1a.1
             Version: 03
             Breite: 32 bits
             Takt: 33MHz
             Fähigkeiten: uhci bus_master cap_list
             Konfiguration: driver=uhci_hcd latency=0
             Ressourcen: irq:21 ioport:40a0(Größe=32)
        *-usb:2
             Beschreibung: USB controller
             Produkt: 82801I (ICH9 Family) USB2 EHCI Controller #2
             Hersteller: Intel Corporation
             Physische ID: 1a.7
             Bus-Informationen: pci@0000:00:1a.7
             Version: 03
             Breite: 32 bits
             Takt: 33MHz
             Fähigkeiten: pm debug ehci bus_master cap_list
             Konfiguration: driver=ehci-pci latency=0
             Ressourcen: irq:21 memory:d6704400-d67047ff
        *-multimedia
             Beschreibung: Audio device
             Produkt: 82801I (ICH9 Family) HD Audio Controller
             Hersteller: Intel Corporation
             Physische ID: 1b
             Bus-Informationen: pci@0000:00:1b.0
             Version: 03
             Breite: 64 bits
             Takt: 33MHz
             Fähigkeiten: pm msi pciexpress bus_master cap_list
             Konfiguration: driver=snd_hda_intel latency=0
             Ressourcen: irq:44 memory:d6700000-d6703fff
        *-pci:0
             Beschreibung: PCI bridge
             Produkt: 82801I (ICH9 Family) PCI Express Port 1
             Hersteller: Intel Corporation
             Physische ID: 1c
             Bus-Informationen: pci@0000:00:1c.0
             Version: 03
             Breite: 32 bits
             Takt: 33MHz
             Fähigkeiten: pci pciexpress msi pm normal_decode bus_master cap_list
             Konfiguration: driver=pcieport
             Ressourcen: irq:40 ioport:3000(Größe=4096) memory:d5700000-d66fffff ioport:d0400000(Größe=16777216)
        *-pci:1
             Beschreibung: PCI bridge
             Produkt: 82801I (ICH9 Family) PCI Express Port 2
             Hersteller: Intel Corporation
             Physische ID: 1c.1
             Bus-Informationen: pci@0000:00:1c.1
             Version: 03
             Breite: 32 bits
             Takt: 33MHz
             Fähigkeiten: pci pciexpress msi pm normal_decode bus_master cap_list
             Konfiguration: driver=pcieport
             Ressourcen: irq:41 ioport:2000(Größe=4096) memory:d4600000-d56fffff ioport:d1400000(Größe=16777216)
           *-network
                Beschreibung: Kabellose Verbindung
                Produkt: BCM43225 802.11b/g/n
                Hersteller: Broadcom Corporation
                Physische ID: 0
                Bus-Informationen: pci@0000:04:00.0
                Logischer Name: wlan0
                Version: 01
                Seriennummer: 4c:0f:6e:68:b4:ea
                Breite: 64 bits
                Takt: 33MHz
                Fähigkeiten: pm msi pciexpress bus_master cap_list ethernet physical wireless
                Konfiguration: broadcast=yes driver=wl0 driverversion=6.30.223.141 (r415941) ip=192.168.178.22 latency=0 multicast=yes wireless=IEEE 802.11abg
                Ressourcen: irq:17 memory:d4600000-d4603fff
        *-pci:2
             Beschreibung: PCI bridge
             Produkt: 82801I (ICH9 Family) PCI Express Port 3
             Hersteller: Intel Corporation
             Physische ID: 1c.2
             Bus-Informationen: pci@0000:00:1c.2
             Version: 03
             Breite: 32 bits
             Takt: 33MHz
             Fähigkeiten: pci pciexpress msi pm normal_decode bus_master cap_list
             Konfiguration: driver=pcieport
             Ressourcen: irq:42 ioport:1000(Größe=4096) memory:d3500000-d45fffff ioport:d2400000(Größe=16777216)
           *-network
                Beschreibung: Ethernet interface
                Produkt: NetLink BCM57780 Gigabit Ethernet PCIe
                Hersteller: Broadcom Corporation
                Physische ID: 0
                Bus-Informationen: pci@0000:05:00.0
                Logischer Name: eth0
                Version: 01
                Seriennummer: 1c:75:08:02:30:04
                Größe: 10Mbit/s
                Kapazität: 1Gbit/s
                Breite: 64 bits
                Takt: 33MHz
                Fähigkeiten: pm msi pciexpress bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                Konfiguration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.134 duplex=half firmware=sb latency=0 link=no multicast=yes port=MII speed=10Mbit/s
                Ressourcen: irq:45 memory:d3500000-d350ffff
        *-usb:3
             Beschreibung: USB controller
             Produkt: 82801I (ICH9 Family) USB UHCI Controller #1
             Hersteller: Intel Corporation
             Physische ID: 1d
             Bus-Informationen: pci@0000:00:1d.0
             Version: 03
             Breite: 32 bits
             Takt: 33MHz
             Fähigkeiten: uhci bus_master cap_list
             Konfiguration: driver=uhci_hcd latency=0
             Ressourcen: irq:23 ioport:4080(Größe=32)
        *-usb:4
             Beschreibung: USB controller
             Produkt: 82801I (ICH9 Family) USB UHCI Controller #2
             Hersteller: Intel Corporation
             Physische ID: 1d.1
             Bus-Informationen: pci@0000:00:1d.1
             Version: 03
             Breite: 32 bits
             Takt: 33MHz
             Fähigkeiten: uhci bus_master cap_list
             Konfiguration: driver=uhci_hcd latency=0
             Ressourcen: irq:19 ioport:4060(Größe=32)
        *-usb:5
             Beschreibung: USB controller
             Produkt: 82801I (ICH9 Family) USB UHCI Controller #3
             Hersteller: Intel Corporation
             Physische ID: 1d.2
             Bus-Informationen: pci@0000:00:1d.2
             Version: 03
             Breite: 32 bits
             Takt: 33MHz
             Fähigkeiten: uhci bus_master cap_list
             Konfiguration: driver=uhci_hcd latency=0
             Ressourcen: irq:20 ioport:4040(Größe=32)
        *-usb:6
             Beschreibung: USB controller
             Produkt: 82801I (ICH9 Family) USB UHCI Controller #6
             Hersteller: Intel Corporation
             Physische ID: 1d.3
             Bus-Informationen: pci@0000:00:1d.3
             Version: 03
             Breite: 32 bits
             Takt: 33MHz
             Fähigkeiten: uhci bus_master cap_list
             Konfiguration: driver=uhci_hcd latency=0
             Ressourcen: irq:18 ioport:4020(Größe=32)
        *-usb:7
             Beschreibung: USB controller
             Produkt: 82801I (ICH9 Family) USB2 EHCI Controller #1
             Hersteller: Intel Corporation
             Physische ID: 1d.7
             Bus-Informationen: pci@0000:00:1d.7
             Version: 03
             Breite: 32 bits
             Takt: 33MHz
             Fähigkeiten: pm debug ehci bus_master cap_list
             Konfiguration: driver=ehci-pci latency=0
             Ressourcen: irq:23 memory:d6704000-d67043ff
        *-pci:3
             Beschreibung: PCI bridge
             Produkt: 82801 Mobile PCI Bridge
             Hersteller: Intel Corporation
             Physische ID: 1e
             Bus-Informationen: pci@0000:00:1e.0
             Version: 93
             Breite: 32 bits
             Takt: 33MHz
             Fähigkeiten: pci subtractive_decode bus_master cap_list
        *-isa
             Beschreibung: ISA bridge
             Produkt: ICH9M LPC Interface Controller
             Hersteller: Intel Corporation
             Physische ID: 1f
             Bus-Informationen: pci@0000:00:1f.0
             Version: 03
             Breite: 32 bits
             Takt: 33MHz
             Fähigkeiten: isa bus_master cap_list
             Konfiguration: driver=lpc_ich latency=0
             Ressourcen: irq:0
        *-ide
             Beschreibung: IDE interface
             Produkt: 82801IBM/IEM (ICH9M/ICH9M-E) 2 port SATA Controller [IDE mode]
             Hersteller: Intel Corporation
             Physische ID: 1f.2
             Bus-Informationen: pci@0000:00:1f.2
             Version: 03
             Breite: 32 bits
             Takt: 66MHz
             Fähigkeiten: ide pm bus_master cap_list
             Konfiguration: driver=ata_piix latency=0
             Ressourcen: irq:19 ioport:4108(Größe=8) ioport:411c(Größe=4) ioport:4100(Größe=8) ioport:4118(Größe=4) ioport:40f0(Größe=16) ioport:40e0(Größe=16)
        *-serial UNGEFORDERT
             Beschreibung: SMBus
             Produkt: 82801I (ICH9 Family) SMBus Controller
             Hersteller: Intel Corporation
             Physische ID: 1f.3
             Bus-Informationen: pci@0000:00:1f.3
             Version: 03
             Breite: 64 bits
             Takt: 33MHz
             Konfiguration: latency=0
             Ressourcen: memory:d6704800-d67048ff ioport:4000(Größe=32)
     *-scsi:0
          Physische ID: 1
          Logischer Name: scsi0
          Fähigkeiten: emulated
        *-disk
             Beschreibung: ATA Disk
             Produkt: Hitachi HTS54503
             Hersteller: Hitachi
             Physische ID: 0.0.0
             Bus-Informationen: scsi@0:0.0.0
             Logischer Name: /dev/sda
             Version: PB3O
             Seriennummer: 100916PBNC03EYK8S44R
             Größe: 298GiB (320GB)
             Fähigkeiten: partitioned partitioned:dos
             Konfiguration: ansiversion=5 sectorsize=512 signature=000915e2
           *-volume:0
                Beschreibung: EXT4-Laufwerk
                Hersteller: Linux
                Physische ID: 1
                Bus-Informationen: scsi@0:0.0.0,1
                Logischer Name: /dev/sda1
                Logischer Name: /
                Version: 1.0
                Seriennummer: 8c0a725a-2b13-412e-9b96-0b24706e99a4
                Größe: 11GiB
                Kapazität: 11GiB
                Fähigkeiten: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                Konfiguration: created=2014-07-12 17:53:44 filesystem=ext4 lastmountpoint=/ modified=2014-07-12 21:11:02 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2014-07-12 21:11:02 state=mounted
           *-volume:1
                Beschreibung: Extended partition
                Physische ID: 2
                Bus-Informationen: scsi@0:0.0.0,2
                Logischer Name: /dev/sda2
                Größe: 286GiB
                Kapazität: 286GiB
                Fähigkeiten: primary extended partitioned partitioned:extended
              *-logicalvolume:0
                   Beschreibung: Linux swap / Solaris partition
                   Physische ID: 5
                   Logischer Name: /dev/sda5
                   Kapazität: 2931MiB
                   Fähigkeiten: nofs
              *-logicalvolume:1
                   Beschreibung: Linux filesystem partition
                   Physische ID: 6
                   Logischer Name: /dev/sda6
                   Logischer Name: /home
                   Kapazität: 284GiB
                   Konfiguration: mount.fstype=ext4 mount.options=rw,relatime,data=ordered state=mounted
     *-scsi:1
          Physische ID: 2
          Logischer Name: scsi1
          Fähigkeiten: emulated
        *-cdrom
             Beschreibung: DVD-RAM writer
             Produkt: DVDRAM GT32N
             Hersteller: HL-DT-ST
             Physische ID: 0.0.0
             Bus-Informationen: scsi@1:0.0.0
             Logischer Name: /dev/cdrom
             Logischer Name: /dev/sr0
             Version: 1.00
             Fähigkeiten: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             Konfiguration: ansiversion=5 status=nodisc

```

---

