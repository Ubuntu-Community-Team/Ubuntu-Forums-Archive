---
title: "Orinoco Strange Happenings"
date: 2006-01-09
forum: Networking &amp; Wireless
---

### Post by aethiolas on 2006-01-09
So I've been using Ubuntu for a while but I'm still a complete newbie.  Because it works fine right out of the box I haven't been forced to learn a lot.  Now I'm trying to setup a laptop and can't seem to get it working correctly.  I've got an Orinoco Gold Card v8.72, and on the live version of 5.10 it works perfectly, no configuration needed. So I tried installing it with the card in the slot and EVERYTIME I ran the installation I got an error message while copying the packages to the hard drive.  After trying 4 different times(including a server instal.  I gave up and installed it w/o the card.  Worked fine.  Now unfortunately when I insert the card, it doesn't seem to be working @ all.  It shows a wireless device in networking but I have an idea its not connected to the card b/c when I remove the card that doesn't go away.  If you all can help I would really appreciate it.  Just let me know what info needs to be posted!  Thanks in advance!

---

### Post by Lambert on 2006-01-09
Go to the WTG link in my signatuare and walk through the steps. You should find out where the problem is. Post the output of the commands in that section.

The main one's to start with here are lshw and lspci -v

---

### Post by aethiolas on 2006-01-10
Here's the lshw!  Thanks for the help!!


```
mjsunit
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 255MB
     *-cpu
          product: Pentium III (Coppermine)
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.8.3
          size: 600MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr sse
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 32KB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 256KB
     *-pci
          description: Host bridge
          product: 440BX/ZX/DX - 82443BX/ZX/DX Host bridge
          vendor: Intel Corporation
          physical id: e0000000
          bus info: pci@00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          resources: iomemory:e0000000-efffffff
        *-pci
             description: PCI bridge
             product: 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@00:01.0
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
           *-display
                description: VGA compatible controller
                product: Rage Mobility P/M AGP 2x
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@01:00.0
                version: 64
                size: 16MB
                width: 32 bits
                clock: 33MHz
                capabilities: vga bus_master cap_list
                resources: iomemory:d1000000-d1ffffff ioport:2000-20ff iomemory:d0100000-d0100fff irq:10
        *-isa UNCLAIMED
             description: ISA bridge
             product: 82371AB/EB/MB PIIX4 ISA
             vendor: Intel Corporation
             physical id: 7
             bus info: pci@00:07.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
        *-ide
             description: IDE interface
             product: 82371AB/EB/MB PIIX4 IDE
             vendor: Intel Corporation
             physical id: 7.1
             bus info: pci@00:07.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=PIIX_IDE
             resources: ioport:1090-109f
           *-ide:0
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-disk
                   product: HITACHI_DK23BA-10
                   vendor: Hitachi
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   capacity: 9590MB
           *-ide:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 33MHz
              *-cdrom
                   product: TORiSAN DVD-ROM DRD-U824
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   capacity: 499MB
                   capabilities: packet
        *-usb
             description: USB Controller
             product: 82371AB/EB/MB PIIX4 USB
             vendor: Intel Corporation
             physical id: 7.2
             bus info: pci@00:07.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd
             resources: ioport:1060-107f irq:5
           *-usbhost
                product: Intel Corporation 82371AB/EB/MB PIIX4 USB
                vendor: Linux 2.6.12-9-386 uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-bridge
             description: Bridge
             product: 82371AB/EB/MB PIIX4 ACPI
             vendor: Intel Corporation
             physical id: 7.3
             bus info: pci@00:07.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bridge
             configuration: driver=piix4_smbus
             resources: irq:9
        *-pcmcia
             description: CardBus bridge
             product: PCI1410 PC card Cardbus Controller
             vendor: Texas Instruments
             physical id: 8
             bus info: pci@00:08.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pcmcia bus_master cap_list
             configuration: driver=yenta_cardbus
             resources: iomemory:10000000-10000fff irq:9
        *-network
             description: Ethernet interface
             product: HCF 56k Modem
             vendor: Conexant
             physical id: 9
             bus info: pci@00:09.0
             logical name: eth0
             version: 08
             serial: 00:50:8b:aa:61:fa
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical
             configuration: broadcast=yes driver=tulip ip=192.168.0.100 multicast=yes
             resources: ioport:1400-14ff iomemory:d0000000-d0003fff irq:9
        *-communication UNCLAIMED
             description: Communication controller
             product: HCF 56k Modem
             vendor: Conexant
             physical id: 9.1
             bus info: pci@00:09.1
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: cap_list
             resources: ioport:1080-1087 iomemory:d0004000-d0007fff irq:9
        *-multimedia
             description: Multimedia audio controller
             product: ES1988 Allegro-1
             vendor: ESS Technology
             physical id: a
             bus info: pci@00:0a.0
             version: 12
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=Maestro3
             resources: ioport:1800-18ff irq:5
  *-network
       description: Wireless interface
       physical id: 1
       logical name: eth1
       serial: 00:02:2d:2e:88:e5
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11-DS

```

---

### Post by aethiolas on 2006-01-10
lspci -v

```
0000:00:00.0 Host bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
        Flags: bus master, medium devsel, latency 64
        Memory at e0000000 (32-bit, prefetchable) [size=256M]
        Capabilities: <available only to root>

0000:00:01.0 PCI bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 96
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
        I/O behind bridge: 00002000-00002fff
        Memory behind bridge: d0100000-d1ffffff

0000:00:07.0 ISA bridge: Intel Corp. 82371AB/EB/MB PIIX4 ISA (rev 02)
        Flags: bus master, medium devsel, latency 0

0000:00:07.1 IDE interface: Intel Corp. 82371AB/EB/MB PIIX4 IDE (rev 01) (prog-if 80 [Master])
        Flags: bus master, medium devsel, latency 64
        I/O ports at 1090 [size=16]

0000:00:07.2 USB Controller: Intel Corp. 82371AB/EB/MB PIIX4 USB (rev 01) (prog-if 00 [UHCI])
        Flags: bus master, medium devsel, latency 32, IRQ 5
        I/O ports at 1060 [size=32]

0000:00:07.3 Bridge: Intel Corp. 82371AB/EB/MB PIIX4 ACPI (rev 03)
        Flags: medium devsel, IRQ 9

0000:00:08.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 01)
        Subsystem: Compaq Computer Corporation: Unknown device b103
        Flags: bus master, medium devsel, latency 168, IRQ 9
        Memory at 10000000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=00, secondary=02, subordinate=05, sec-latency=176
        Memory window 0: 10400000-107ff000 (prefetchable)
        Memory window 1: 10800000-10bff000
        I/O window 0: 00004000-000040ff
        I/O window 1: 00004400-000044ff
        16-bit legacy interface ports at 0001

0000:00:09.0 Ethernet controller: Conexant HCF 56k Modem (rev 08)
        Subsystem: Compaq Computer Corporation 623-LAN Grizzly
        Flags: bus master, medium devsel, latency 160, IRQ 9
        BIST result: 00
        I/O ports at 1400 [size=256]
        Memory at d0000000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <available only to root>

0000:00:09.1 Communication controller: Conexant HCF 56k Modem (rev 05)
        Subsystem: Compaq Computer Corporation Grizzly
        Flags: medium devsel, IRQ 9
        BIST result: 00
        I/O ports at 1080 [size=8]
        Memory at d0004000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <available only to root>

0000:00:0a.0 Multimedia audio controller: ESS Technology ES1988 Allegro-1 (rev 12)
        Subsystem: Compaq Computer Corporation: Unknown device 002e
        Flags: bus master, medium devsel, latency 64, IRQ 5
        I/O ports at 1800 [size=256]
        Capabilities: <available only to root>

0000:01:00.0 VGA compatible controller: ATI Technologies Inc Rage Mobility P/M AGP 2x (rev 64) (prog-if 00 [VGA])
        Subsystem: Compaq Computer Corporation: Unknown device b18b
        Flags: bus master, stepping, medium devsel, latency 66, IRQ 10
        Memory at d1000000 (32-bit, non-prefetchable) [size=16M]
        I/O ports at 2000 [size=256]
        Memory at d0100000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>

```

---

### Post by Lambert on 2006-01-10
Can you use the live cd and run the lshw command again while the card is working.

Something that I haven't seen before is the line *serial:*
which is telling me the device is on the SPI bus and not the PCI bus.???

---

### Post by aethiolas on 2006-01-10
Sure I'll throw the live in tommorow and run it!  Thanks again!

---

### Post by aethiolas on 2006-01-11
Here is the live cd running, any help would be greatly appreciated!!  I am so close to installing SuSe but I really don't want to!

```

ubuntu
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 255MB
     *-cpu
          product: Pentium III (Coppermine)
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.8.3
          size: 600MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr sse
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 32KB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 256KB
     *-pci
          description: Host bridge
          product: 440BX/ZX/DX - 82443BX/ZX/DX Host bridge
          vendor: Intel Corporation
          physical id: f8000000
          bus info: pci@00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          resources: iomemory:f8000000-fbffffff
        *-pci
             description: PCI bridge
             product: 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@00:01.0
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
           *-display
                description: VGA compatible controller
                product: Rage Mobility P/M AGP 2x
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@01:00.0
                version: 64
                size: 16MB
                width: 32 bits
                clock: 33MHz
                capabilities: vga bus_master cap_list
                resources: iomemory:f5000000-f5ffffff ioport:2000-20ff iomemory:f4100000-f4100fff irq:10
        *-isa UNCLAIMED
             description: ISA bridge
             product: 82371AB/EB/MB PIIX4 ISA
             vendor: Intel Corporation
             physical id: 7
             bus info: pci@00:07.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
        *-ide
             description: IDE interface
             product: 82371AB/EB/MB PIIX4 IDE
             vendor: Intel Corporation
             physical id: 7.1
             bus info: pci@00:07.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=PIIX_IDE
             resources: ioport:1090-109f
           *-ide:0
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-disk
                   product: HITACHI_DK23BA-10
                   vendor: Hitachi
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   capacity: 9590MB
           *-ide:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 33MHz
              *-cdrom
                   product: TORiSAN DVD-ROM DRD-U824
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   capacity: 627MB
                   capabilities: packet
        *-usb
             description: USB Controller
             product: 82371AB/EB/MB PIIX4 USB
             vendor: Intel Corporation
             physical id: 7.2
             bus info: pci@00:07.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd
             resources: ioport:1060-107f irq:5
           *-usbhost
                product: Intel Corporation 82371AB/EB/MB PIIX4 USB
                vendor: Linux 2.6.12-9-386 uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-bridge
             description: Bridge
             product: 82371AB/EB/MB PIIX4 ACPI
             vendor: Intel Corporation
             physical id: 7.3
             bus info: pci@00:07.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bridge
             configuration: driver=piix4_smbus
             resources: irq:9
        *-pcmcia
             description: CardBus bridge
             product: PCI1410 PC card Cardbus Controller
             vendor: Texas Instruments
             physical id: 8
             bus info: pci@00:08.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pcmcia bus_master cap_list
             configuration: driver=yenta_cardbus
             resources: iomemory:10000000-10000fff irq:9
        *-network DISABLED
             description: Ethernet interface
             product: HCF 56k Modem
             vendor: Conexant
             physical id: 9
             bus info: pci@00:09.0
             logical name: eth0
             version: 08
             serial: 00:50:8b:aa:61:fa
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical
             configuration: broadcast=yes driver=tulip multicast=yes
             resources: ioport:1400-14ff iomemory:f4000000-f4003fff irq:9
        *-communication UNCLAIMED
             description: Communication controller
             product: HCF 56k Modem
             vendor: Conexant
             physical id: 9.1
             bus info: pci@00:09.1
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: cap_list
             resources: ioport:1080-1087 iomemory:f4004000-f4007fff irq:9
        *-multimedia
             description: Multimedia audio controller
             product: ES1988 Allegro-1
             vendor: ESS Technology
             physical id: a
             bus info: pci@00:0a.0
             version: 12
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=Maestro3
             resources: ioport:1800-18ff irq:5
  *-network
       description: Wireless interface
       physical id: 1
       logical name: eth1
       serial: 00:02:2d:2e:88:e5
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.0.105 multicast=yes wireless=IEEE 802.11-DS

```

---

### Post by Lambert on 2006-01-12
I'll have to say I can't offer much here as this is an area I haven't dealt with before and I may be way off base on what I see.

your card looks to be on the a serial bus and I don'b believe it's ths usb so I'm not sure what's happening here. I 'm not sure if it even works with hotplug so maybe that's why the interface stays when card is removed.

But it does look like it's showing up with an eth1 interface.

If you try to configure and activate the interface what is the output of these commands?

iwconfig
ifconfig 
route -n

---

