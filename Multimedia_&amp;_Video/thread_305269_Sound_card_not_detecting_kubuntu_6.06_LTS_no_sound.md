---
title: "Sound card not detecting kubuntu 6.06 LTS no sound"
date: 2006-11-23
forum: Multimedia &amp; Video
---

### Post by londo4 on 2006-11-23
I am a newbie to Kubuntu and basically to Linux (I do have some limited Windows experience).
I seem to have the same problem as many seem to be having. I have not found a real resolution (at least one that seems to work in my case) for this:
I installed Kubuntu 6.06 LTS on a Dell Optiplec GX1 (this is a test bed system). I did find on a Dell public board that the GX1 seems to have an on board (mother board) Crystal chip set CS4236. Here is what Windows XP shows the sound card as, it is the integrated sound card on the mother board of this system:

Crystal WDM Audio Codec

Device type: Sound, video and game controllers

Manufacturer: Crystal Semiconductor

Please Help me
Additional Information 	This is the Output when I Hit;
root@londo4-desktop:/home/londo4# lspci

0000:00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 02)
0000:00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 02)
0000:00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
0000:00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
0000:00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
0000:00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
0000:00:0f.0 PCI bridge: Digital Equipment Corporation DECchip 21152 (rev 03)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc 3D Rage Pro AGP 1X/2X (rev 5c)
0000:02:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:02:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

OR When I Hit root@londo4-desktop:/home/londo4# lshw

londo4-desktop
    description: Desktop Computer
    product: OptiPlex GX1 350Mbr
    vendor: Dell Computer Corporation
    serial: PJ976
    width: 32 bits
    capabilities: smbios-2.2 dmi-2.2
    configuration: administrator_password=enabled chassis=desktop frontpanel_password=enabled power-on_password=enabled uuid=44454C4C-0082-1050-804A-80C04F393736
  *-core
       description: Motherboard
       product: OptiPlex GX1 350Mbr
       vendor: Dell Computer Corporation
       physical id: 0
     *-firmware
          description: BIOS
          vendor: Dell Computer Corporation
          physical id: 0
          version: A10 (08/01/01)
          size: 64KB
          capacity: 192KB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect edd int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video agp ls120boot zipboot
     *-cpu
          description: CPU
          product: Pentium II (Deschutes)
          vendor: Intel Corp.
          physical id: 400
          bus info: cpu@0
          version: 6.5.2
          slot: Microprocessor
          size: 350MHz
          capacity: 800MHz
          width: 32 bits
          clock: 100MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr
        *-cache:0
             description: L1 cache
             physical id: 700
             size: 32KB
             capacity: 32KB
             capabilities: internal varies unified
        *-cache:1
             description: L2 cache
             physical id: 701
             size: 512KB
             capacity: 512KB
             capabilities: pipeline-burst synchronous internal varies unified
     *-memory
          description: System Memory
          physical id: 1000
          slot: System board or motherboard
          size: 256MB
          capacity: 768MB
        *-bank:0
             description: DIMM DRAM Synchronous
             physical id: 0
             slot: DIMM_A
             size: 64MB
             width: 64 bits
        *-bank:1
             description: DIMM DRAM Synchronous
             physical id: 1
             slot: DIMM_B
             size: 128MB
             width: 64 bits
        *-bank:2
             description: DIMM DRAM Synchronous
             physical id: 2
             slot: DIMM_C
             size: 64MB
             width: 64 bits
     *-pci
          description: Host bridge
          product: 440BX/ZX/DX - 82443BX/ZX/DX Host bridge
          vendor: Intel Corporation
          physical id: f0000000
          bus info: pci@00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          resources: iomemory:f0000000-f3ffffff
        *-pci:0
             description: PCI bridge
             product: 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@00:01.0
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
           *-display
                description: VGA compatible controller
                product: 3D Rage Pro AGP 1X/2X
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@01:00.0
                version: 5c
                size: 16MB
                width: 32 bits
                clock: 33MHz
                capabilities: vga bus_master cap_list
                resources: iomemory:fd000000-fdffffff ioport:ec00-ecff iomemory:fcfff000-fcffffff irq:9
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
             resources: ioport:ffa0-ffaf
           *-ide
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-disk
                   description: ATA Disk
                   product: SAMSUNG SV0411N
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   version: UA100-07
                   serial: 0611J2FW527757
                   size: 37GB
                   capacity: 37GB
                   capabilities: ata dma lba iordy smart security pm partitioned partitioned:dos
                   configuration: mode=udma2 smart=on
                 *-volume:0
                      description: HPFS/NTFS partition
                      physical id: 1
                      bus info: ide@0.0,1
                      logical name: /dev/hda1
                      capacity: 8001MB
                      capabilities: primary bootable
                 *-volume:1
                      description: W95 Ext'd (LBA) partition
                      physical id: 2
                      bus info: ide@0.0,2
                      logical name: /dev/hda2
                      capacity: 29GB
                      capabilities: primary
              *-cdrom
                   description: IDE CD-ROM
                   product: ASUS CD-S520/A5
                   physical id: 1
                   bus info: ide@0.1
                   logical name: /dev/hdb
                   version: 1.22
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio
                   configuration: mode=udma2
                 *-disc
                      physical id: 0
                      logical name: /dev/hdb
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
             resources: ioport:cce0-ccff irq:11
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.15-27-386 uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
              *-usb
                   description: Generic USB device
                   product: USB camera
                   vendor: Microdia
                   physical id: 2
                   bus info: usb@1:2
                   version: 1.01
                   capabilities: usb-1.10
                   configuration: driver=spca5xx maxpower=500mA speed=12.0MB/s
        *-bridge UNCLAIMED
             description: Bridge
             product: 82371AB/EB/MB PIIX4 ACPI
             vendor: Intel Corporation
             physical id: 7.3
             bus info: pci@00:07.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bridge
             resources: irq:9
        *-pci:1
             description: PCI bridge
             product: DECchip 21152
             vendor: Digital Equipment Corporation
             physical id: f
             bus info: pci@00:0f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
           *-network:0
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 9
                bus info: pci@02:09.0
                logical name: eth0
                version: 10
                serial: 00:00:b4:92:3b:58
                size: 100MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
                configuration: autonegociation=on broadcast=yes driver=8139too driverversion=0.9.27 duplex=full ip=83.83.176.35 link=yes multicast=yes port=MII speed=100MB/s
                resources: ioport:dc00-dcff iomemory:fafffc00-fafffcff irq:9
           *-network:1
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: b
                bus info: pci@02:0b.0
                logical name: eth1
                version: 10
                serial: 00:02:44:51:08:97
                size: 10MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
                configuration: autonegociation=on broadcast=yes driver=8139too driverversion=0.9.27 duplex=half link=no multicast=yes port=MII speed=10MB/s
                resources: ioport:d800-d8ff iomemory:fafff800-fafff8ff irq:9

Please Help me

---

### Post by danrael on 2006-11-26
Try this:

How to activate Crystal CS4236B Audio on Optiplex GX1:

> At the Desktop, open Applications> Accessories> Terminal
> At the flashing cursor, type: sudo gedit
> Type your system password
> In gedit, click on the "Open" icon
> Double-click "File System" from the lefthand sidebar
> Double-click the "etc" folder
> Scroll down past the folders to the "modules" file, and open it
> On the line after the last entry, type:

snd-cs4236 dma1=1 dma2=3 io=0x0534 irq=5

> Click the "Save" icon, and Quit the program. Reboot.
> Go to System> Preferences> Sound
> "CS4236B" should appear in the Default sound card field
> Make sure "Enable sound server startup" is unchecked
> Go to Applications> Sound and Video> Volume Control
> Make sure the volume level is up in both Playback and Capture
> Open CD Player or Sound Juicer and test for audio from a music cd

---

### Post by seedybee on 2007-01-20
Thanks Danrael: this solution almost worked for me on a Dell Optiplex GX1 - 450, and got me on track to find a solution that worked for me.

in the end I just needed to use this line in the /etc/modules file:

snd-cs4236

without the DMA, IO address, and IRQ info (must be different on this version of the GX1).

So a modified instruction would be:

Run terminal: Click:  Applications/Accessories/Terminal
In terminal type:
[INDENT][FONT="Fixedsys"]sudo gedit /etc/modules[/FONT][/INDENT]

enter your password

append line to end of modules file:
[INDENT][FONT="Fixedsys"]snd-cs4236[/FONT][/INDENT]

save and reboot system

that worked for me, though you may still need to go into sound properties and ensure sound card is selected as per Danraels instructions above.

If its still not woirking you may need to check that sound is enabled in the BIOS: reboot and hit F2 to enter BIOS settings, ALT+P will take you to page 2 where the sound option is located.

---

### Post by bluedude on 2007-02-13
> Run terminal: Click: Applications/Accessories/Terminal
In terminal type:
sudo gedit /etc/modules
enter your password

append line to end of modules file:
snd-cs4236
save and reboot system

This worked great for me.  Yeah, I know I'm a n00b for using an outdated GX1, but I'm still pleased to get it working.  Thanks for your help guys.

---

### Post by zaphoid on 2007-02-25
This worked for me.

Now the Dell Optiplex GX1 has sound.  yeah!

---

### Post by castoroil97 on 2007-03-08
this worked for my GX1 in edgy 6.10

THANK YOU

I Love UBUNTU!!!!!

:popcorn:

---

### Post by radiophage on 2007-04-30
Many thanks to seedybee- this worked for our old GX1 box also!  Hats off to ya!

---

### Post by redpawn on 2007-12-02
Thanks...It also works with Kubuntu 7.10.  Sound again from this old box :)

---

### Post by mariuz on 2007-12-22
it works on xubuntu and wubi 7.04 too :)

---

