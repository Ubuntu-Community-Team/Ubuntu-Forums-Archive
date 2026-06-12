---
title: "No sound. Edgy, Lifeboox 1410, HDA Intel"
date: 2007-03-05
forum: Multimedia &amp; Video
---

### Post by bracc0 on 2007-03-05
I've read the fine document named ""Comprehensive Sound Problem Solutions Guide",
I have identified my sound card, I've detected and upgraded my ALSA driver, I've played with alsamixer trying to mute "External Amplifier" but I still have no sound.

Here are some outputs:

```
lspci -l

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)

```

```
lshw

 description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 1001MB
     *-cpu:0
          product: Genuine Intel(R) CPU           T2300  @ 1.66GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.14.8
          serial: 0000-06E8-0000-0000-0000-0000
          size: 1GHz
          capacity: 1GHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc pni monitor est tm2 xtpr cpufreq
          configuration: id=0
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 32 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 32 bits
             capabilities: logical
     *-cpu:1
          product: Genuine Intel(R) CPU           T2300  @ 1.66GHz
          vendor: Intel Corp.
          physical id: 2
          bus info: cpu@1
          version: 6.14.8
          serial: 0000-06E8-0000-0000-0000-0000
          size: 1GHz
          capacity: 1GHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc pni monitor est tm2 xtpr cpufreq
          configuration: id=0
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 32 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 32 bits
             capabilities: logical
     *-pci
          description: Host bridge
          product: Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
        *-display:0
             description: VGA compatible controller
             product: Mobile 945GM/GMS/940GML Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@00:02.0
             version: 03
             size: 256MB
             width: 32 bits
             clock: 33MHz
             capabilities: vga bus_master cap_list
             resources: iomemory:f0300000-f037ffff ioport:1800-1807 iomemory:e0000000-efffffff iomemory:f0400000-f043ffff irq:193
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 945GM/GMS/940GML Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@00:02.1
             version: 03
             size: 512KB
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             resources: iomemory:f0380000-f03fffff
        *-multimedia
             description: Audio device
             product: 82801G (ICH7 Family) High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel
             resources: iomemory:f0640000-f0643fff irq:74
        *-pci:0
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Ethernet interface
                product: 88E8055 PCI-E Gigabit Ethernet Controller
                vendor: Marvell Technology Group Ltd.
                physical id: 0
                bus info: pci@02:00.0
                logical name: eth0
                version: 12
                serial: 00:17:42:23:1f:ee
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=sky2 ip=172.25.238.20 multicast=yes
                resources: iomemory:f0100000-f0103fff ioport:2000-20ff irq:82
        *-pci:1
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@00:1c.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:2
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@00:1c.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Wireless interface
                product: Atheros Communications, Inc.
                vendor: Atheros Communications, Inc.
                physical id: 0
                bus info: pci@05:00.0
                logical name: wifi0
                version: 01
                serial: 00:c0:a8:cd:e2:64
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list logical ethernet physical wireless
                configuration: broadcast=yes driver=ath_pci multicast=yes wireless=IEEE 802.11g
                resources: iomemory:52100000-5210ffff irq:233
        *-usb:0
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd
             resources: ioport:1820-183f irq:66
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.17-10-generic uhci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:1
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd
             resources: ioport:1840-185f irq:185
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.17-10-generic uhci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
              *-usb
                   description: Mouse
                   product: USB-PS/2 Optical Mouse
                   vendor: Logitech
                   physical id: 1
                   bus info: usb@3:1
                   version: 20.00
                   capabilities: usb-2.00
                   configuration: driver=usbhid maxpower=98mA speed=1.5MB/s
        *-usb:2
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd
             resources: ioport:1860-187f irq:233
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.17-10-generic uhci_hcd
                physical id: 1
                bus info: usb@4
                logical name: usb4
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:3
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@00:1d.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd
             resources: ioport:1880-189f irq:193
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.17-10-generic uhci_hcd
                physical id: 1
                bus info: usb@5
                logical name: usb5
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:4
             description: USB Controller
             product: 82801G (ICH7 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd
             resources: iomemory:f0644000-f06443ff irq:66
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 2.6.17-10-generic ehci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-2.00
                configuration: driver=hub maxpower=0mA slots=8 speed=480.0MB/s
        *-pci:3
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@00:1e.0
             version: e2
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
           *-pcmcia
                description: CardBus bridge
                product: RL5c476 II
                vendor: Ricoh Co Ltd
                physical id: 3
                bus info: pci@08:03.0
                version: b3
                width: 64 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus
                resources: iomemory:f0201000-f0201fff iomemory:b00c09080-b00c0907f irq:193
           *-firewire
                description: FireWire (IEEE 1394)
                product: R5C552 IEEE 1394 Controller
                vendor: Ricoh Co Ltd
                physical id: 3.1
                bus info: pci@08:03.1
                version: 08
                width: 32 bits
                clock: 33MHz
                capabilities: ohci bus_master cap_list
                configuration: driver=ohci1394
                resources: iomemory:f0200000-f02007ff irq:74
           *-system
                description: Generic system peripheral
                product: R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 3.2
                bus info: pci@08:03.2
                version: 17
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=sdhci
                resources: iomemory:f0200800-f02008ff irq:193
        *-isa UNCLAIMED
             description: ISA bridge
             product: 82801GBM (ICH7-M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
        *-ide
             description: IDE interface
             product: 82801G (ICH7 Family) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@00:1f.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=PIIX_IDE
             resources: ioport:1810-181f irq:233
           *-ide
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-cdrom
                   product: MATSHITADVD-RAM UJ-841S
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   capabilities: packet
        *-storage
             description: SATA controller
             product: 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller AHCI
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@00:1f.2
             logical name: scsi0
             logical name: scsi1
             logical name: scsi2
             logical name: scsi3
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: storage ahci_1.0 bus_master cap_list scsi-host
             configuration: driver=ahci
             resources: ioport:18d0-18d7 ioport:18c4-18c7 ioport:18c8-18cf ioport:18c0-18c3 ioport:18b0-18bf iomemory:f0644400-f06447ff irq:58
        *-serial UNCLAIMED
             description: SMBus
             product: 82801G (ICH7 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             resources: ioport:18e0-18ff irq:11

```

```
aplay -l

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC262 Analog [ALC262 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 2: ALC262 Digital [ALC262 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

```
contents of /etc/modules:

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
sbp2
snd-hda-intel

```

installed ALSA driver 10.1.2 (latest)
alsamixer cheched: nothing is muted.

I can't hear neithr beep nor sounds.

My laptop has a dual partition. Useless to say, the windows stuff detect and use sound card correctly, so I assume my hardware is OK

Any Idea?
Thanks in advance
Claudio

---

### Post by pandu.rs on 2007-03-05
check the output of

sudo lsof /dev/dsp

if there is any process using it kill that process and then check if u r getting sound

---

### Post by bracc0 on 2007-03-05
Checked.
No such process.

Thanks for the tip
Claudio

---

### Post by MadeR on 2007-03-05
From my experience with my laptop, the simplest and only way to solve problems with intel hda is installing the new alsa package.

---

### Post by ammunition on 2007-03-05
I had the same problem with a Packard Bell laptop, and the only solution i found was to buy a usb soundcard.

---

### Post by bracc0 on 2007-03-05
> **MadeR said:**
> From my experience with my laptop, the simplest and only way to solve problems with intel hda is installing the new alsa package.

MadeR,
do you mean the latest ALSA driver, utils and dev?
I have ALSA rel. 10.1.12 installed. I have seen in the ALSA website that the latest release is 10.1.13, with 10.1.14 at the release candidate3.

Do you recommend a specific version?

Thanks
Claudio

---

### Post by MadeR on 2007-03-05
install "alsa everything", the newest version, even though it were a release candidate!

It solved everything as I wrote here: [http://www.ubuntuforums.org/showthread.php?t=324764](http://www.ubuntuforums.org/showthread.php?t=324764)

---

### Post by bracc0 on 2007-03-07
Thanks to your suggestion, I downloaded and installed alsa driver, dev and utils rel 1.10.14rc3. 
No errors. The installation went fine. (".configure", "sudo make", "sudo make install"). 

Unfortunately I still see alsa stuff rel. 1.10.11 in Synaptics and I can't find anything related to the new version apparently succesfull installed. If I ask synaptics to uninstall alsa 1.10.11 it warns that a lot of packages will be uninstalled. I stuck here.

What's the best way to get latest alsa driver in place of version 1.10.11? 
Uninstall before the older release with all dependancies?
Am I missing something?

TIA
Claudio

---

### Post by MadeR on 2007-03-07
I hope feisty fawn will include it :)

---

### Post by bracc0 on 2007-03-07
and in the mean time? :confused: 

:) :)

---

### Post by MadeR on 2007-03-07
> **bracc0 said:**
> and in the mean time? :confused: 

:) :)

You can create a .deb package !
but I never did such a thing...

---

