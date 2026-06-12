---
title: "hires, but no widescreen?"
date: 2007-12-03
forum: Multimedia &amp; Video
---

### Post by tg4 on 2007-12-03
I have searched for hours on this topic -- my apologies if it's been covered somewhere.  I can't find info that will help me.  Here's my problem:

I have just installed 7.10 on my pc and have an ATI Radeon 7000 graphics card. I cannot get my monitor to work in widescreen mode EVEN THOUGH the resolution setting says (through the gui and xorg.conf) 1440 x 900 (which is what I want).  The problem is that the whole screen is not used -- there is a large black bar on left side of screen (takes up about 1/5th of screen) and I can't utilize this portion of the screen.  The screen resolution that IS being used is good (high-res).  Here's what I've done:

* I have [re]configured xorg.conf manually AND have also run dpkg-reconfigure and stepped through this script a few times.
* I believe I can't use fglrx (or the native ati drivers from ati's website?) because my ati card is a model below 9500.  I have 7000.  (But I've still downloaded and installed fglrx, but I bet I didn't full install it -- or at least didn't do it properly...)
* Manually added modelines to the xorg.conf file (which I generated on the website for my specs).  From everything I've read, it should be working for me, but it's not...  What am I missing?

Here is the output from lspci:
```

00:00.0 Host bridge: VIA Technologies, Inc. PT880 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. PT880 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. PT880 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. PT880 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. PT880 Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. PT880 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]

```

Here is my xorg.conf file:
```

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbOptions"	"altwin:meta_win"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"LG Flatron Wide L194WT"
	Option		"DPMS"
	HorizSync	28-83
	VertRefresh	56-75
 	# 1440x900 @ 60.00 Hz (GTF) hsync: 55.92 kHz; pclk: 106.47 MHz
 	Modeline	"1440x900_60.00"  106.47  1440 1520 1672 1904  900 901 904 932  -HSync +Vsync
 	DisplaySize 	1440 900
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]"
	Monitor		"LG Flatron Wide L194WT"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1920x1440" "1440x900"
		Depth	24
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
EndSection

```

Here is output from lshw:
```

    description: Desktop Computer
    product: PT880-8237
    vendor: VIA Technologies, Inc.
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: boot=normal chassis=desktop
  *-core
       description: Motherboard
       product: PT880-8237
       physical id: 0
       slot: Internal Cache
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: 6.00 PG (08/29/2005)
          size: 128KB
          capacity: 192KB
          capabilities: isa pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot
     *-cpu:0
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 3.00GHz
          vendor: Intel Corp.
          physical id: 5
          bus info: cpu@0
          version: 15.4.1
          serial: 0000-0F41-0000-0000-0000-0000
          slot: Socket 478
          size: 3GHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc pni monitor ds_cpl cid cx16 xtpr
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: b
             slot: Internal Cache
             size: 32KB
             capacity: 32KB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: d
             slot: External Cache
             size: 1MB
             capacity: 1MB
             capabilities: synchronous external write-back
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 64 bits
             capabilities: logical
     *-cpu:1
          description: CPU
          vendor: Intel
          physical id: 6
          bus info: cpu@1
          version: 15.4.1
          serial: 0000-0F41-0000-0000-0000-0000
          slot: Socket 478
          size: 3GHz
          clock: 200MHz
          capabilities: ht
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: c
             slot: Internal Cache
             size: 32KB
             capacity: 32KB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: e
             slot: External Cache
             size: 1MB
             capacity: 1MB
             capabilities: synchronous external write-back
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             capabilities: logical
     *-memory
          description: System Memory
          physical id: 1f
          slot: System board or motherboard
          size: 511MB
          capacity: 768MB
        *-bank:0
             description: DIMM
             product: None
             vendor: None
             physical id: 0
             serial: None
             slot: A0
             size: 256MB
        *-bank:1
             description: DIMM [empty]
             product: None
             vendor: None
             physical id: 1
             serial: None
             slot: A1
        *-bank:2
             description: DIMM [empty]
             product: None
             vendor: None
             physical id: 2
             serial: None
             slot: A2
     *-pci:0
          description: Host bridge
          product: PT880 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
          configuration: driver=agpgart-via latency=8 module=via_agp
        *-pci
             description: PCI bridge
             product: VT8237 PCI Bridge
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci pm normal_decode bus_master cap_list
           *-display
                description: VGA compatible controller
                product: Radeon RV100 QY [Radeon 7000/VE]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: agp agp-2.0 pm vga bus_master vga_palette cap_list
                configuration: latency=32 mingnt=8
        *-storage
             description: RAID bus controller
             product: VIA VT6420 SATA RAID Controller
             vendor: VIA Technologies, Inc.
             physical id: f
             bus info: pci@0000:00:0f.0
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: storage pm bus_master cap_list
             configuration: driver=sata_via latency=32 module=sata_via
        *-ide
             description: IDE interface
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             vendor: VIA Technologies, Inc.
             physical id: f.1
             bus info: pci@0000:00:0f.1
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=VIA_IDE latency=32 module=via82cxxx
           *-ide:0
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-disk:0
                   description: ATA Disk
                   product: QUANTUM FIREBALLP LM30.0
                   vendor: Quantum
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   version: A35.0700
                   serial: 186005731764
                   size: 27GB
                   capacity: 27GB
                   capabilities: ata dma lba iordy smart security pm partitioned partitioned:dos
                   configuration: mode=udma4 smart=on
                 *-volume:0
                      description: Linux filesystem partition
                      physical id: 1
                      bus info: ide@0.0,1
                      logical name: /dev/hda1
                      capacity: 26GB
                      capabilities: primary bootable
                 *-volume:1
                      description: Extended partition
                      physical id: 2
                      bus info: ide@0.0,2
                      logical name: /dev/hda2
                      size: 1223MB
                      capacity: 1223MB
                      capabilities: primary extended partitioned partitioned:extended
                    *-logicalvolume
                         description: Linux swap / Solaris partition
                         physical id: 5
                         logical name: /dev/hda5
                         capacity: 1223MB
                         capabilities: nofs
              *-disk:1
                   description: ATA Disk
                   product: Maxtor 6Y120L0
                   vendor: Maxtor
                   physical id: 1
                   bus info: ide@0.1
                   logical name: /dev/hdb
                   version: YAR41BW0
                   serial: Y34V3V1E
                   size: 114GB
                   capacity: 114GB
                   capabilities: ata dma lba iordy smart security pm apm partitioned partitioned:dos
                   configuration: apm=off mode=udma6 smart=on
                 *-volume
                      description: HPFS/NTFS partition
                      physical id: 1
                      bus info: ide@0.1,1
                      logical name: /dev/hdb1
                      capacity: 114GB
                      capabilities: primary
           *-ide:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 33MHz
              *-cdrom:0
                   description: CD-R/CD-RW writer
                   product: CD-RW 52X24
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   version: K.UC
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio cd-r cd-rw
                   configuration: mode=udma2 status=nodisc
              *-cdrom:1
                   description: DVD reader
                   product: SAMSUNG DVD-ROM SD-608
                   physical id: 1
                   bus info: ide@1.1
                   logical name: /dev/hdd
                   version: bp22
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio dvd
                   configuration: status=open
        *-usb:0
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10
             bus info: pci@0000:00:10.0
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=32 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.1
             bus info: pci@0000:00:10.1
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=32 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.2
             bus info: pci@0000:00:10.2
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=32 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.3
             bus info: pci@0000:00:10.3
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=32 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: USB 2.0
             vendor: VIA Technologies, Inc.
             physical id: 10.4
             bus info: pci@0000:00:10.4
             version: 86
             width: 32 bits
             clock: 33MHz
             capabilities: pm ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=32 module=ehci_hcd
        *-isa
             description: ISA bridge
             product: VT8237 ISA bridge [KT600/K8T800/K8T890 South]
             vendor: VIA Technologies, Inc.
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa pm bus_master cap_list
             configuration: latency=0
        *-multimedia
             description: Multimedia audio controller
             product: VT8233/A/8235/8237 AC97 Audio Controller
             vendor: VIA Technologies, Inc.
             physical id: 11.5
             bus info: pci@0000:00:11.5
             version: 60
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: driver=VIA 82xx Audio latency=0 module=snd_via82xx
        *-network
             description: Ethernet interface
             product: VT6102 [Rhine-II]
             vendor: VIA Technologies, Inc.
             physical id: 12
             bus info: pci@0000:00:12.0
             logical name: eth0
             version: 78
             serial: 00:30:18:a8:69:3a
             size: 100MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=full ip=192.168.9.14 latency=32 link=yes maxlatency=8 mingnt=3 module=via_rhine multicast=yes port=MII speed=100MB/s
     *-pci:1
          description: Host bridge
          product: PT880 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 101
          bus info: pci@0000:00:00.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: PT880 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 102
          bus info: pci@0000:00:00.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: PT880 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 103
          bus info: pci@0000:00:00.3
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: PT880 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 104
          bus info: pci@0000:00:00.4
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: PT880 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 105
          bus info: pci@0000:00:00.7
          version: 00
          width: 32 bits
          clock: 33MHz

```

Thank you SO MUCH for any help you can provide.  I am NEW to ubuntu and really want to get it working correctly.  thanks.

---

### Post by tg4 on 2007-12-03
Am I being an idiot here?  Is there any easy fix or should I go back to the drawing board and keep searching?  It's in the painful stage right now - your help is very appreciated.

---

### Post by tg4 on 2007-12-04
Is the problem because I have an onboard graphics card too?  (the via controller?)  I think my bus id is correct, though...

Is this the type of thing I have to live with?  If I move to lower resolutions, then the whole screen IS utilized, but the graphics are stretched out and display is not that clear...

---

### Post by bkoonce on 2007-12-04
I am having the same problem. I have a radeon 9800 pro graphics card and an Optiquest 20 inch wide screen (1680 x 1050 native res). When I set it to a widescreen resolution there is about a 2 inch black bar on the left side of the screen. When I set to a 4:3 or 5:4 resolution the picture is stretched to fit the whole widescreen. I'm at work, but when I get back home I will post my xorg.

---

### Post by tg4 on 2007-12-04
bkoonce, I think you're gonna be ok...  From what I've gathered, you can do this because you have a model above the ati 9500 series -- you just need to install the proprietary drivers from ATI and not use the opensource drivers which are packaged with ubuntu.  Here's the instructions from ubuntu:  [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

My question is still outstanding:  Am I out of luck because I have an ATI 7000 card and I want to use my monitor's native widescreen res of 1440 x 900?  Is it common behaivor for the opensource "ati" drivers not to work correctly in widescreen?  I'm totally perplexed -- everything I can think of reads 1440 x 900, but I still have this black bar on the left side of my screen.  (I have an "LG flatron wide" monitor with native res at 1440 x 900).  Any help?

---

### Post by tg4 on 2007-12-09
I think I've found the answer.  My video card doesn't support 1440 x 900 I don't believe... maaa bad.  I can get a lower res that stretches a bit, but it looks ok.  Hope this thread helps someone else...

---

### Post by MGStreak on 2008-02-27
After a *lot* of nights of trial and error and board hunting, I finally solved this problem on my machine.  Here are my specs:

O/S: Ubuntu 7.10 (Gutsy Gibbon)
Video Card: Intel Corporation 82945G/GZ Integrated Graphics Controller
Driver: 'intel'
Monitor: Samsung SyncMaster 920NW
Native Resolution: 1440X900 @ 60 hz (Widescreen)

Solution:
[http://ubuntuforums.org/showthread.php?t=203905](http://ubuntuforums.org/showthread.php?t=203905)

My comment/addendum to the solution:
[http://ubuntuforums.org/showpost.php?p=4416287&postcount=67](http://ubuntuforums.org/showpost.php?p=4416287&postcount=67)

---

