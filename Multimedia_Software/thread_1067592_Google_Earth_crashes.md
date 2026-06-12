---
title: "Google Earth crashes"
date: 2009-02-12
forum: Multimedia Software
---

### Post by Dipper on 2009-02-12
I have the ATI video drivers installed.  Yet when I open Google Earth, I get as far as the startup tip and then the screens flicker and then the program shuts down.

Using:

Ubuntu Intrepid
ATI Driver (installed)

---

### Post by x33a on 2009-02-12
post all your hardware specifications here, then it will be easier to point the problem. and do mention the driver versions also.

---

### Post by Dipper on 2009-02-12
What hardware specifications are you referring to?  How do I access that info?

---

### Post by x33a on 2009-02-12
i mean your graphics card, your processor, ram etc.

you can install lshw.

open a terminal and type sudo aptitude lshw.

then after installation, run " sudo lshw | less " , and post the output here.

---

### Post by Dipper on 2009-02-12
```
root@dave-laptop:~# lshw
dave-laptop               
    description: Notebook
    product: Pavilion ZV6100 (EC361UA#ABA)
    vendor: Hewlett-Packard
    version: F.14
    serial: CND52500MJ
    width: 32 bits
    capabilities: smbios-2.31 dmi-2.31 smp-1.4 smp
    configuration: administrator_password=enabled boot=oem-specific chassis=notebook cpus=1 frontpanel_password=unknown keyboard_password=unknown power-on_password=disabled uuid=C1CD398A-D7AA-11D9-B558-000FB071BBFA
  *-core
       description: Motherboard
       product: 3085
       vendor: Hewlett-Packard
       physical id: 0
       version: 42.37
       serial: CND52500MJ
       slot: &#65533;
     *-firmware
          description: BIOS
          vendor: Hewlett-Packard
          physical id: 0
          version: F.14 (05/27/2005)
          size: 101KiB
          capacity: 448KiB
          capabilities: pci pcmcia pnp upgrade shadowing cdboot bootselect int5printscreen int9keyboard int17printer int10video acpi usb agp ls120boot smartbattery
     *-cpu
          description: CPU
          product: AMD Sempron(tm) Processor 3200+
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 15.15.0
          slot: U23
          size: 1800MHz
          capacity: 1800MHz
          width: 64 bits
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt x86-64 3dnowext 3dnow up cpufreq
        *-cache:0
             description: L2 cache
             physical id: 5
             slot: L2 Cache
             size: 256KiB
             capacity: 1MiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L1 cache
             physical id: 0
             size: 128KiB
        *-cache:2
             description: L2 cache
             physical id: 1
             size: 256KiB
     *-memory
          description: System Memory
          physical id: c
          slot: System board or motherboard
          size: 512MiB
        *-bank:0
             description: DIMM DRAM Synchronous
             physical id: 0
             slot: JP11
             size: 256MiB
             width: 64 bits
        *-bank:1
             description: DIMM DRAM Synchronous
             physical id: 1
             slot: JP30
             size: 256MiB
             width: 64 bits
     *-pci:0
          description: Host bridge
          product: RS480 Host Bridge
          vendor: ATI Technologies Inc
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
          configuration: latency=64
        *-pci:0
             description: PCI bridge
             product: RS480 PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci ht bus_master cap_list
           *-display
                description: VGA compatible controller
                product: Radeon XPRESS 200M 5955 (PCIE)
                vendor: ATI Technologies Inc
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: pm bus_master cap_list
                configuration: driver=fglrx_pci latency=255 mingnt=8 module=fglrx
        *-pci:1
             description: PCI bridge
             product: RS480 PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 4
             bus info: pci@0000:00:04.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht bus_master cap_list
             configuration: driver=pcieport-driver
        *-usb:0
             description: USB Controller
             product: IXP SB400 USB Host Controller
             vendor: ATI Technologies Inc
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: msi bus_master cap_list
             configuration: driver=ohci_hcd latency=64 module=ohci_hcd
        *-usb:1
             description: USB Controller
             product: IXP SB400 USB Host Controller
             vendor: ATI Technologies Inc
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: msi bus_master cap_list
             configuration: driver=ohci_hcd latency=64 module=ohci_hcd
        *-usb:2
             description: USB Controller
             product: IXP SB400 USB2 Host Controller
             vendor: ATI Technologies Inc
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=ehci_hcd latency=64 module=ehci_hcd
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
             configuration: driver=piix4_smbus latency=0 module=i2c_piix4
        *-ide
             description: IDE interface
             product: IXP SB400 IDE Controller
             vendor: ATI Technologies Inc
             physical id: 14.1
             bus info: pci@0000:00:14.1
             logical name: scsi0
             logical name: scsi1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide msi bus_master cap_list emulated
             configuration: driver=pata_atiixp latency=64 module=pata_atiixp
           *-disk
                description: ATA Disk
                product: Hitachi HTS54161
                vendor: Hitachi
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: SB4O
                serial: SB0444SJCNJGYE
                size: 149GiB (160GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=0630062f
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   logical name: /dev/.static/dev
                   version: 1.0
                   serial: 46eb29cd-9d19-4771-aa4f-a48187623911
                   size: 147GiB
                   capacity: 147GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2009-02-10 17:36:28 filesystem=ext3 modified=2009-02-11 21:59:43 mount.fstype=ext3 mount.options=ro,errors=remount-ro,data=ordered mounted=2009-02-11 21:59:43 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 1090MiB
                   capacity: 1090MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 1090MiB
                      capabilities: nofs
           *-cdrom
                description: DVD reader
                product: CDW/DVD TS-L462A
                vendor: TSSTcorp
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: HP17
                capabilities: removable audio cd-r cd-rw dvd
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
        *-pci:2
             description: PCI bridge
             product: IXP SB400 PCI-PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master
           *-network:0
                description: Network controller
                product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
                vendor: Broadcom Corporation
                physical id: 2
                bus info: pci@0000:03:02.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master
                configuration: driver=b43-pci-bridge latency=64 module=ssb
           *-pcmcia
                description: CardBus bridge
                product: PCI1510 PC card Cardbus Controller
                vendor: Texas Instruments
                physical id: 4
                bus info: pci@0000:03:04.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192 module=yenta_socket
           *-network:1
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 6
                bus info: pci@0000:03:06.0
                logical name: eth0
                version: 10
                serial: 00:0f:b0:71:bb:fa
                size: 10MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=128 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s
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
             configuration: driver=ATI IXP AC97 controller latency=64 mingnt=2 module=snd_atiixp
        *-communication
             description: Modem
             product: SB400 AC'97 Modem Controller
             vendor: ATI Technologies Inc
             physical id: 14.6
             bus info: pci@0000:00:14.6
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: msi bus_master cap_list
             configuration: driver=ATI IXP MC97 controller latency=64 mingnt=2 module=snd_atiixp_modem
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
          configuration: driver=k8temp module=k8temp
  *-battery
       physical id: 1
       slot: Left Front
  *-network:0
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:90:4b:f1:ad:3b
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.102 multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: pan0
       serial: fa:4e:7c:13:c8:d8
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```

---

### Post by x33a on 2009-02-12
hi, could you run google earth on windows easily?

and, please edit your post and put the lshw output in code.

---

### Post by Dipper on 2009-02-12
Yes, it works in both Windows and KDE.

---

### Post by x33a on 2009-02-12
i read a few similar threads, and it seems that compiz is responsible for it.

if you have compiz enabled, then disable it and then try to run google earth again.

---

### Post by Dipper on 2009-02-12
compiz is not installed.

---

### Post by x33a on 2009-02-12
take a look here:

 [http://blog.mymediasystem.net/avchd/google-earth-5-crashes-on-linux/](http://blog.mymediasystem.net/avchd/google-earth-5-crashes-on-linux/)

---

### Post by Dipper on 2009-02-12
That solved the problem.  thanks.

---

