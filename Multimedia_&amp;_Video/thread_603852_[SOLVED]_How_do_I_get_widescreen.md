---
title: "[SOLVED] How do I get widescreen?"
date: 2007-11-05
forum: Multimedia &amp; Video
---

### Post by KentS on 2007-11-05
I'm running Dapper Drake on an HP Pavilion dv2000 with a widescreen. I just installed nvidia-glx (version 1.0-8776) with the Synaptic package monitor. But i still can't choose widescreen resolution. Does anyone have any suggestions about what I can do to correct this?

My graphics processor is GeForce Go 6150.

The relevant part of my /etc/X11/xorg.conf is
> Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon RV100 QY [Radeon 7000/VE]"
	Driver		"nvidia"
	BusID		"PCI:0:5:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon RV100 QY [Radeon 7000/VE]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

---

### Post by overdrank on 2007-11-05
HI and have you tried the nvidia settings? If you use the command  ```
gksudo nvidia-settings
``` This may help in adjusting your settings. Good luck!

---

### Post by KentS on 2007-11-05
I've tried the nvidia-settings. The only thing i manage to find (so it might just be me not being able to find the right thing) that does anything related to this is FlatPanel scaling. And the only thing making my screen clearer is to set it to centered. But then I get 2-3 cm black frames on both sides of the screen.

---

### Post by overdrank on 2007-11-05
> **KentS said:**
> I'm running Dapper Drake on an HP Pavilion dv2000 with a widescreen. I just installed nvidia-glx (version 1.0-8776) with the Synaptic package monitor. But i still can't choose widescreen resolution. Does anyone have any suggestions about what I can do to correct this?

My graphics processor is GeForce Go 6150.

The relevant part of my /etc/X11/xorg.conf is

Hi I really did not look at your xorg the first time but why it the card identified as a ATI and your using a nvidia driver?

---

### Post by KentS on 2007-11-05
That's a really good question.
nvidia-settings recognizes the card as GeForce Go 6150, so does my windows partition. I think xorg.conf is the only place that says anything about ATI.

---

### Post by overdrank on 2007-11-05
> **KentS said:**
> That's a really good question.
nvidia-settings recognizes the card as GeForce Go 6150, so does my windows partition. I think xorg.conf is the only place that says anything about ATI.

Please post the output of the the command ```
lspci
``` and ```
lshw
```

---

### Post by KentS on 2007-11-05
lspci:

```
0000:00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
0000:00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
0000:00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
0000:00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
0000:00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
0000:00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
0000:00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
0000:00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
0000:00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
0000:00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
0000:00:05.0 VGA compatible controller: nVidia Corporation C51 PCI Express Bridg e (rev a2)
0000:00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
0000:00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
0000:00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
0000:00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
0000:00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
0000:00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
0000:00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
0000:00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1)
0000:00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
0000:00:10.1 0403: nVidia Corporation MCP51 High Definition Audio (rev a2)
0000:00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Hyp erTransport Technology Configuration
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Add ress Map
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRA M Controller
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Mis cellaneous Control
0000:01:00.0 Network controller: Broadcom Corporation BCM4310 UART (rev 01)
0000:03:09.0 FireWire (IEEE 1394): Ricoh Co Ltd: Unknown device 0832
0000:03:09.1 0805: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19 )
0000:03:09.2 System peripheral: Ricoh Co Ltd: Unknown device 0843 (rev 01)
0000:03:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapte r (rev 0a)
0000:03:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)

```


lshw:
```
description: Notebook
    product: HP Pavilion dv2000 (RE277EA#ABN)
    vendor: Hewlett-Packard
    version: F.11
    serial: 2CE642160Y
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4
    configuration: administrator_password=enabled boot=oem-specific chassis=notebook frontpanel_password=unknown keyboard_password=unknown power-on_password=disabled uuid=A4BA9F80-5FA8-11DB-B308-ED83DE0B796F
  *-core
       description: Motherboard
       product: 30B5
       vendor: Wistron
       physical id: 0
       version: 62.45
     *-firmware
          description: BIOS
          vendor: Phoenix
          physical id: 0
          version: F.11 (08/25/2006)
          size: 95KB
          capacity: 960KB
          capabilities: isa pci pcmcia pnp apm upgrade shadowing escd cdboot acpi usb agp biosbootspecification
     *-cpu
          description: CPU
          product: AMD Turion(tm) 64 X2
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 15.8.2
          slot: U1
          size: 800MHz
          capacity: 1600MHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt x86-64 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy cpufreq
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1 Cache
             size: 128KB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2 Cache
             size: 256KB
             capacity: 2MB
             capabilities: synchronous external write-back
     *-memory:0
          description: System Memory
          physical id: 1
          slot: System board or motherboard
          size: 1GB
        *-bank:0
             description: SODIMM DDR Synchronous 533 MHz (1.9 ns)
             physical id: 0
             slot: M1
             size: 512MB
             width: 32 bits
             clock: 533MHz (1.87617ns)
        *-bank:1
             description: SODIMM DDR Synchronous 533 MHz (1.9 ns)
             physical id: 1
             slot: M2
             size: 512MB
             width: 32 bits
             clock: 533MHz (1.87617ns)
     *-memory:1 UNCLAIMED
          description: RAM memory
          product: C51 Host Bridge
          vendor: nVidia Corporation
          physical id: 6
          bus info: pci@00:00.0
          version: a2
          width: 32 bits
          clock: 66MHz (15.1515ns)
          capabilities: bus_master cap_list
     *-memory:2 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 0
          vendor: nVidia Corporation
          physical id: 0.1
          bus info: pci@00:00.1
          version: a2
          width: 32 bits
          clock: 66MHz (15.1515ns)
     *-memory:3 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 1
          vendor: nVidia Corporation
          physical id: 0.2
          bus info: pci@00:00.2
          version: a2
          width: 32 bits
          clock: 66MHz (15.1515ns)
     *-memory:4 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 5
          vendor: nVidia Corporation
          physical id: 0.3
          bus info: pci@00:00.3
          version: a2
          width: 32 bits
          clock: 66MHz (15.1515ns)
     *-memory:5 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 4
          vendor: nVidia Corporation
          physical id: 0.4
          bus info: pci@00:00.4
          version: a2
          width: 32 bits
          clock: 66MHz (15.1515ns)
          capabilities: bus_master
     *-memory:6 UNCLAIMED
          description: RAM memory
          product: C51 Host Bridge
          vendor: nVidia Corporation
          physical id: 0.5
          bus info: pci@00:00.5
          version: a2
          width: 32 bits
          clock: 66MHz (15.1515ns)
          capabilities: bus_master cap_list
     *-memory:7 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 3
          vendor: nVidia Corporation
          physical id: 0.6
          bus info: pci@00:00.6
          version: a2
          width: 32 bits
          clock: 66MHz (15.1515ns)
     *-memory:8 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 2
          vendor: nVidia Corporation
          physical id: 0.7
          bus info: pci@00:00.7
          version: a2
          width: 32 bits
          clock: 66MHz (15.1515ns)
     *-pci:0
          description: PCI bridge
          product: C51 PCI Express Bridge
          vendor: nVidia Corporation
          physical id: 2
          bus info: pci@00:02.0
          version: a1
          width: 32 bits
          clock: 33MHz
          capabilities: pci normal_decode bus_master cap_list
          configuration: driver=pcieport-driver
        *-network
             description: Wireless interface
             product: BCM4310 UART
             vendor: Broadcom Corporation
             physical id: 0
             bus info: pci@01:00.0
             logical name: eth1
             version: 01
             serial: 00:14:a5:fd:92:c8
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical wireless
             configuration: broadcast=yes driver=ndiswrapper driverversion=1.33 firmware=Broadcom,12/17/2005, 4.10.40.1 ip=192.168.1.1 link=yes multicast=yes wireless=IEEE 802.11g
             resources: iomemory:c3000000-c3003fff irq:233
     *-pci:1
          description: PCI bridge
          product: C51 PCI Express Bridge
          vendor: nVidia Corporation
          physical id: 3
          bus info: pci@00:03.0
          version: a1
          width: 32 bits
          clock: 33MHz
          capabilities: pci normal_decode bus_master cap_list
          configuration: driver=pcieport-driver
     *-display
          description: VGA compatible controller
          product: C51 PCI Express Bridge
          vendor: nVidia Corporation
          physical id: 5
          bus info: pci@00:05.0
          version: a2
          size: 256MB
          width: 64 bits
          clock: 66MHz
          capabilities: vga bus_master cap_list
          configuration: driver=nvidia
          resources: iomemory:c2000000-c2ffffff iomemory:d0000000-dfffffff iomemory:c1000000-c1ffffff irq:217
     *-memory:9 UNCLAIMED
          description: RAM memory
          product: MCP51 Host Bridge
          vendor: nVidia Corporation
          physical id: 9
          bus info: pci@00:09.0
          version: a2
          width: 32 bits
          clock: 66MHz (15.1515ns)
          capabilities: bus_master cap_list
     *-isa UNCLAIMED
          description: ISA bridge
          product: MCP51 LPC Bridge
          vendor: nVidia Corporation
          physical id: a
          bus info: pci@00:0a.0
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: isa bus_master
     *-serial UNCLAIMED
          description: SMBus
          product: MCP51 SMBus
          vendor: nVidia Corporation
          physical id: a.1
          bus info: pci@00:0a.1
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: cap_list
          resources: ioport:3040-307f ioport:3000-303f irq:10
     *-processor UNCLAIMED
          description: Co-processor
          product: MCP51 PMU
          vendor: nVidia Corporation
          physical id: a.3
          bus info: pci@00:0a.3
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: bus_master
          resources: iomemory:c0040000-c007ffff irq:11
     *-usb:0
          description: USB Controller
          product: MCP51 USB Controller
          vendor: nVidia Corporation
          physical id: 7
          bus info: pci@00:0b.0
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: ohci bus_master cap_list
          configuration: driver=ohci_hcd
          resources: iomemory:c0004000-c0004fff irq:225
        *-usbhost
             product: OHCI Host Controller
             vendor: Linux 2.6.15-27-386 ohci_hcd
             physical id: 1
             bus info: usb@2
             logical name: usb2
             version: 2.06
             capabilities: usb-1.10
             configuration: driver=hub maxpower=0mA slots=8 speed=12.0MB/s
     *-usb:1
          description: USB Controller
          product: MCP51 USB Controller
          vendor: nVidia Corporation
          physical id: b.1
          bus info: pci@00:0b.1
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: ehci bus_master cap_list
          configuration: driver=ehci_hcd
          resources: iomemory:c0005000-c00050ff irq:217
        *-usbhost
             product: EHCI Host Controller
             vendor: Linux 2.6.15-27-386 ehci_hcd
             physical id: 1
             bus info: usb@1
             logical name: usb1
             version: 2.06
             capabilities: usb-2.00
             configuration: driver=hub maxpower=0mA slots=8 speed=480.0MB/s
     *-ide:0
          description: IDE interface
          product: MCP51 IDE
          vendor: nVidia Corporation
          physical id: d
          bus info: pci@00:0d.0
          version: f1
          width: 32 bits
          clock: 66MHz
          capabilities: ide bus_master cap_list
          configuration: driver=AMD_IDE
          resources: ioport:3080-308f
        *-ide
             description: IDE Channel 1
             physical id: 1
             bus info: ide@1
             logical name: ide1
             clock: 66MHz
           *-cdrom
                description: DVD-RAM writer
                product: HL-DT-ST DVDRAM GSA-T10N
                physical id: 0
                bus info: ide@1.0
                logical name: /dev/hdc
                version: PC05
                serial: K0269SM5714
                capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy pm audio cd-r cd-rw dvd dvd-r dvd-ram
              *-disc
                   physical id: 0
                   logical name: /dev/hdc
     *-ide:1
          description: IDE interface
          product: MCP51 Serial ATA Controller
          vendor: nVidia Corporation
          physical id: e
          bus info: pci@00:0e.0
          logical name: scsi0
          logical name: scsi1
          version: f1
          width: 32 bits
          clock: 66MHz
          capabilities: ide bus_master cap_list emulated scsi-host
          configuration: driver=sata_nv
          resources: ioport:30b0-30b7 ioport:30a4-30a7 ioport:30a8-30af ioport:30a0-30a3 ioport:3090-309f iomemory:c0006000-c0006fff irq:201
        *-disk
             description: SCSI Disk
             product: ST98823AS
             vendor: ATA
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 7.24
             serial: 5PK2RD08
             size: 74GB
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5
           *-volume:0
                description: HPFS/NTFS partition
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                capacity: 19GB
                capabilities: primary bootable
           *-volume:1
                description: W95 FAT32 (LBA) partition
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                capacity: 7397MB
                capabilities: primary
           *-volume:2
                description: Primary partition
                physical id: 3
                bus info: scsi@0:0.0.0,3
                logical name: /dev/sda3
                capacity: 1027MB
                capabilities: primary
           *-volume:3
                description: Extended partition
                physical id: 4
                bus info: scsi@0:0.0.0,4
                logical name: /dev/sda4
                capacity: 45GB
                capabilities: extended partitioned partitioned:extended
     *-pci:2
          description: PCI bridge
          product: MCP51 PCI Bridge
          vendor: nVidia Corporation
          physical id: 10
          bus info: pci@00:10.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pci subtractive_decode bus_master cap_list
        *-firewire
             description: FireWire (IEEE 1394)
             product: Ricoh Co Ltd
             vendor: Ricoh Co Ltd
             physical id: 9
             bus info: pci@03:09.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master cap_list
             configuration: driver=ohci1394
             resources: iomemory:c3100000-c31007ff irq:233
        *-system:0
             description: Generic system peripheral
             product: R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
             vendor: Ricoh Co Ltd
             physical id: 9.1
             bus info: pci@03:09.1
             version: 19
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=sdhci
             resources: iomemory:c3100800-c31008ff irq:58
        *-system:1 UNCLAIMED
             description: System peripheral
             product: Ricoh Co Ltd
             vendor: Ricoh Co Ltd
             physical id: 9.2
             bus info: pci@03:09.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             resources: iomemory:c3100c00-c3100cff irq:11
        *-system:2 UNCLAIMED
             description: System peripheral
             product: R5C592 Memory Stick Bus Host Adapter
             vendor: Ricoh Co Ltd
             physical id: 9.3
             bus info: pci@03:09.3
             version: 0a
             width: 32 bits
             clock: 33MHz
             capabilities: cap_list
             resources: iomemory:c3101000-c31010ff irq:11
        *-system:3 UNCLAIMED
             description: System peripheral
             product: xD-Picture Card Controller
             vendor: Ricoh Co Ltd
             physical id: 9.4
             bus info: pci@03:09.4
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: cap_list
             resources: iomemory:c3101400-c31014ff irq:11
     *-multimedia
          description: Multimedia controller
          product: MCP51 High Definition Audio
          vendor: nVidia Corporation
          physical id: 10.1
          bus info: pci@00:10.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: bus_master cap_list
          configuration: driver=HDA Intel
          resources: iomemory:c0000000-c0003fff irq:50
     *-bridge
          description: Ethernet interface
          product: MCP51 Ethernet Controller
          vendor: nVidia Corporation
          physical id: 14
          bus info: pci@00:14.0
          logical name: eth0
          version: a3
          serial: 00:16:d3:11:60:00
          size: 10000000
          capacity: 100000000
          width: 32 bits
          clock: 66MHz
          capabilities: bridge bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
          configuration: autonegociation=on broadcast=yes driver=forcedeth driverversion=0.54 duplex=half link=no multicast=yes port=MII speed=10MB/s
          resources: iomemory:c0007000-c0007fff ioport:30b8-30bf irq:209
     *-pci:3
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 100
          bus info: pci@00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz

```

---

### Post by overdrank on 2007-11-05
Ok all looks good for nvidia I have no idea how the ATI got detected  so try and reconfigure your xorg ```
sudo dpkg-reconfigure -phigh xserver-xorg 
``` then check you xorg and see what is detected,

---

### Post by KentS on 2007-11-05
It worked!
Thank you so much!

---

### Post by overdrank on 2007-11-05
> **KentS said:**
> It worked!
Thank you so much!

Man that was strange, please mark the thread as solved under the thread tools and you can look in my signature. Good luck! :KS

---

