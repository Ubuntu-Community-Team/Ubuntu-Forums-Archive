---
title: "How to install the ATI All in Wonder with TV tuner ?"
date: 2006-02-15
forum: Multimedia &amp; Video
---

### Post by patrick295767 on 2006-02-15
Hi, 

With trying gaming with mupen64, I discovered that my video is nto installed :-( 

When I check it with fglrxinfo, I get sthg like  MESA ..

I did that to install my video at then beginning:

 ```

sudo apt-get install xorg-driver-fglrx sudo apt-get install linux-restricted-modules-$(uname -r) sudo dpkg-reconfigure xserver-xorg #Select the ATI driver
 
```
And it's saying mesa !!

I will try this:
 ```

sudo apt-get install xorg-driver-fglrx sudo apt-get install linux-restricted-modules-$(uname -r) #Okay if it is already installed sudo dpkg-reconfigure xserver-xorg #Select the fglrx driver
 
```

...

Tried !
Ok so when I do sudo dpkg-reconfigure xserver-xorg #Select the fglrx driver
the startx or /etc/init.d/gdm start
doesnt work anymore. I rebooted and similar.

Thank you, 

Greetings, 

Patrick
  
That's my lshw:
```
 
    description: Desktop Computer
    product: MS-6380E
    vendor: MSI
    version: 1.0
    serial: 00000000
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: chassis=desktop
  *-core
       description: Motherboard
       product: MS-6380E
       vendor: MSI
       physical id: 0
       version: 1.0
       serial: 00000000
       slot: PCI2
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 07.00T (04/02/01)
          size: 64KB
          capacity: 192KB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: AMD Athlon(tm) Processor
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 6.6.2
          slot: Socket-A
          size: 1250MHz
          capacity: 3GHz
          width: 32 bits
          clock: 100MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mmxext 3dnowext 3dnow
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: Internal Cache
             size: 128KB
             capacity: 1MB
             capabilities: synchronous internal write-back unified
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: Internal Cache
             size: 256KB
             capacity: 1MB
             capabilities: synchronous internal write-back unified
     *-memory
          description: System memory
          physical id: 1
          size: 255MB
     *-pci
          description: Host bridge
          product: VT8366/A/7 [Apollo KT266/A/333]
          vendor: VIA Technologies, Inc.
          physical id: e0000000
          bus info: pci@00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
          resources: iomemory:e0000000-e7ffffff
        *-pci
             description: PCI bridge
             product: VT8366/A/7 [Apollo KT266/A/333 AGP]
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master cap_list
           *-display
                description: VGA compatible controller
                product: Rage 128 RF/SG AGP
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@01:00.0
                version: 00
                size: 64MB
                width: 32 bits
                clock: 66MHz
                capabilities: vga bus_master cap_list
                resources: iomemory:d8000000-dbffffff ioport:c800-c8ff iomemory:dfefc000-dfefffff irq:16
        *-network
             description: Ethernet interface
             product: RTL-8029(AS)
             vendor: Realtek Semiconductor Co., Ltd.
             physical id: 5
             bus info: pci@00:05.0
             logical name: eth0
             version: 00
             serial: 00:00:b4:98:ce:f7
             width: 32 bits
             clock: 33MHz
             capabilities: ethernet physical
             configuration: broadcast=yes driver=ne2k-pci driverversion=1.03 ip=192.168.123.100 multicast=yes
             resources: ioport:e800-e81f irq:16
        *-multimedia
             description: Multimedia audio controller
             product: SB Live! EMU10k1
             vendor: Creative Labs
             physical id: 6
             bus info: pci@00:06.0
             version: 0a
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=EMU10K1_Audigy
             resources: ioport:e400-e41f irq:17
        *-input
             description: Input device controller
             product: SB Live! MIDI/Game Port
             vendor: Creative Labs
             physical id: 6.1
             bus info: pci@00:06.1
             version: 0a
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=Emu10k1_gameport
             resources: ioport:ec00-ec07
        *-usb:0
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.2
             bus info: pci@00:10.2
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd
             resources: ioport:e000-e01f irq:21
           *-usbhost
                product: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (#3)
                vendor: Linux 2.6.12-9-386 uhci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:1
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.1
             bus info: pci@00:10.1
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd
             resources: ioport:dc00-dc1f irq:21
           *-usbhost
                product: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (#2)
                vendor: Linux 2.6.12-9-386 uhci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:2
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10
             bus info: pci@00:10.0
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd
             resources: ioport:d800-d81f irq:21
           *-usbhost
                product: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
                vendor: Linux 2.6.12-9-386 uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
              *-usb
                   description: Mouse
                   product: Microsoft Wireless Optical Mouse
                   vendor: Microsoft
                   physical id: 2
                   bus info: usb@1:2
                   version: 0.57
                   capabilities: usb-2.00
                   configuration: driver=usbhid maxpower=50mA speed=1.5MB/s
        *-usb:3
             description: USB Controller
             product: USB 2.0
             vendor: VIA Technologies, Inc.
             physical id: 10.3
             bus info: pci@00:10.3
             version: 82
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd
             resources: iomemory:dfffff00-dfffffff irq:21
           *-usbhost
                product: VIA Technologies, Inc. USB 2.0
                vendor: Linux 2.6.12-9-386 ehci_hcd
                physical id: 1
                bus info: usb@4
                logical name: usb4
                version: 2.06
                capabilities: usb-2.00
                configuration: driver=hub maxpower=0mA slots=6 speed=480.0MB/s
              *-usb
                   description: USB hub
                   product: CY7C65640 USB-2.0 "TetraHub"
                   vendor: Cypress Semiconductor Corp.
                   physical id: 1
                   bus info: usb@4:1
                   version: 0.08
                   capabilities: usb-2.00
                   configuration: driver=hub maxpower=100mA slots=4 speed=480.0MB/s
                 *-usb:0
                      description: Mouse
                      product: USB & PS/2 Mouse
                      vendor: Acrox
                      physical id: 2
                      bus info: usb@4:1.2
                      version: 0.01
                      capabilities: usb-1.10
                      configuration: driver=usbhid maxpower=100mA speed=1.5MB/s
                 *-usb:1
                      description: Human interface device
                      product: Logitech Dual Action
                      vendor: Logitech
                      physical id: 4
                      bus info: usb@4:1.4
                      version: 2.00
                      capabilities: usb-1.10
                      configuration: driver=usbhid maxpower=30mA speed=1.5MB/s
        *-isa UNCLAIMED
             description: ISA bridge
             product: VT8235 ISA Bridge
             vendor: VIA Technologies, Inc.
             physical id: 11
             bus info: pci@00:11.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
        *-ide
             description: IDE interface
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             vendor: VIA Technologies, Inc.
             physical id: 11.1
             bus info: pci@00:11.1
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master cap_list
             configuration: driver=VIA_IDE
             resources: ioport:fc00-fc0f irq:255
           *-ide:0
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-disk:0
                   description: ATA Disk
                   product: SAMSUNG SP1604N
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   version: TM100-30
                   serial: S02DJ10Y302901
                   size: 149GB
                   capabilities: ata dma lba iordy smart security pm
                   configuration: mode=udma2 smart=on
              *-disk:1
                   description: ATA Disk
                   product: MAXTOR 4K080H4
                   vendor: Maxtor
                   physical id: 1
                   bus info: ide@0.1
                   logical name: /dev/hdb
                   version: A08.1500
                   serial: 674201467129
                   size: 74GB
                   capacity: 74GB
                   capabilities: ata dma lba iordy smart security pm
                   configuration: mode=udma2 smart=on
           *-ide:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 33MHz
              *-cdrom
                   description: DVD writer
                   product: LITE-ON DVDRW SHW-1635S
                   physical id: 1
                   bus info: ide@1.1
                   logical name: /dev/hdd
                   version: YS0F
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio cd-r cd-rw dvd dvd-r
 
```

---

### Post by patrick295767 on 2006-02-15
I'll try then this guide : [http://ubuntuforums.org/showpost.php?p=423584](http://ubuntuforums.org/showpost.php?p=423584)
  
I hope that'll help ...
(I dont find my video card)

Greetz

---

