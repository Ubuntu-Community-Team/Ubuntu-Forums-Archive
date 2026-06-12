---
title: "ati radeon help needed"
date: 2005-11-20
forum: Multimedia &amp; Video
---

### Post by danne on 2005-11-20
Hi,

My card: ati mobility radeon x600 pci-express

My problem: already configured with X but noticed there's no full hardware support (openGL errors etc...)

some help how to configure my card?

kind regards,

danne

---

### Post by bencrouse on 2005-11-20
have you installed the fglrx drivers?

---

### Post by danne on 2005-11-21
[QUOTE=bencrouse]have you installed the fglrx drivers?[/QUOTE]
yep (maybe because I have a mobility radeon in a laptop it doesn't work well I dunno)

---

### Post by Teroedni on 2005-11-21
What do glxinfo give you

```
sudo glxinfo
```

---

### Post by rsankuratri on 2005-11-21
I have a Dell Inspion 9100 laptop with ATI mobility 9600 card (128MB).  I followed the instructions in the thread below and got it to work.  I did use the new drivers earlier but without any luck.  This one got the 3D acceleration woking

[http://www.ubuntuforums.org/showthread.php?t=24557&pp=10](http://www.ubuntuforums.org/showthread.php?t=24557&pp=10)

Hope it works for you too.   :-)

---

### Post by danne on 2005-11-22
[QUOTE=Teroedni]What do glxinfo give you

```
sudo glxinfo
```[/QUOTE]

name of display: :0.0
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_OML_swap_method, GLX_SGI_make_current_read,
    GLX_SGIS_multisample, GLX_SGIX_fbconfig
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_ATI_pixel_format_float,
    GLX_ATI_render_texture
GLX version: 1.2
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_multisample
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multitexture, GL_ARB_texture_border_clamp,
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add,
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3,
    GL_ARB_transpose_matrix, GL_EXT_abgr, GL_EXT_blend_color,
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_texture_env_add,
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3,
    GL_EXT_texture_lod_bias
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  1 0 None
0x24 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  1 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  1 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  1 0 None
0x27 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  1 0 None
0x28 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  1 0 None
0x29 24 dc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  1 0 None

---

### Post by Teroedni on 2005-11-22
i couldnt find x600mobility support on Ati website

    *   Mobility™ Radeon® X700
    * Mobility™ Radeon® 9800
    * Mobility™ Radeon® 9600
    * Mobility™ Radeon® 9550
    * Mobility™ Radeon® 9000
    * Mobility™ Radeon® 9200
    * Radeon® Xpress 200M series 

[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.19.10.html](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.19.10.html)

Buts let try first:)

Begin with this (Uninstall your current fglrx)
[http://doc.gwos.org/index.php/Install_ATI_driver](http://doc.gwos.org/index.php/Install_ATI_driver)

---

### Post by danne on 2005-11-23
[QUOTE=Teroedni]i couldnt find x600mobility support on Ati website

    *   Mobility™ Radeon® X700
    * Mobility™ Radeon® 9800
    * Mobility™ Radeon® 9600
    * Mobility™ Radeon® 9550
    * Mobility™ Radeon® 9000
    * Mobility™ Radeon® 9200
    * Radeon® Xpress 200M series 

[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.19.10.html](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.19.10.html)

Buts let try first:)

Begin with this (Uninstall your current fglrx)
[http://doc.gwos.org/index.php/Install_ATI_driver](http://doc.gwos.org/index.php/Install_ATI_driver)[/QUOTE]

I did what it said but it didn't work....when I did "fglrxinfo"  --->

Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

bye

---

### Post by Teroedni on 2005-11-23
Okay lets try the newest from ati then


But i need to know a little more about your machine
Is it a laptop ?
Can you include the name and brand of your machine and as much information thath you can find about your machine hardware

and give me the results 

```
sudo lshw
```

---

### Post by danne on 2005-11-24
[QUOTE=Teroedni]Okay lets try the newest from ati then


But i need to know a little more about your machine
Is it a laptop ?
Can you include the name and brand of your machine and as much information thath you can find about your machine hardware

and give me the results 

```
sudo lshw
```[/QUOTE]
here you go...

    description: Computer
    product: Aspire 1800
    vendor: Acer
    version: Null
    serial: Null
    width: 32 bits
    capabilities: smbios-2.31 dmi-2.31
    configuration: boot=oem-specific uuid=63346535-3135-3831-6238-000FB061389D
  *-core
       description: Motherboard
       product: Aspire 1800
       vendor: Acer
       physical id: 0
       version: Null
       serial: LXA390505351734036ED00
     *-firmware
          description: BIOS
          vendor: PHOENIX FirstBIOS
          physical id: 0
          version: V2.70 (02/17/2005)
          size: 111KB
          capacity: 448KB
          capabilities: isa pci pcmcia pnp apm upgrade shadowing escd acpi usb a gp smartbattery biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 2.93GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.4.1
          serial: 0000-0F41-0000-0000-0000-0000
          slot: WMT478/NWD
          size: 2930MHz
          width: 32 bits
          clock: 133MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic  sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe  nx pni monitor ds_cpl tm2 cid xtpr
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 8
             slot: L1 Cache
             size: 16KB
             capacity: 16KB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 9
             slot: L2 Cache
             size: 1MB
             capabilities: burst internal write-back
     *-cache UNCLAIMED
          description: L3 cache
          physical id: a
          slot: L3 Cache
          size: 1MB
          capabilities: burst internal write-back
     *-memory
          description: System Memory
          physical id: 14
          slot: System board or motherboard
          size: 512MB
        *-bank:0
             description: DIMM DDR Synchronous 133 MHz (7.5 ns)
             physical id: 0
             slot: J6G1
             size: 256MB
             width: 64 bits
             clock: 133MHz (7.5188ns)
        *-bank:1
             description: DIMM DDR Synchronous 133 MHz (7.5 ns)
             physical id: 1
             slot: J6H1
             size: 256MB
             width: 64 bits
             clock: 133MHz (7.5188ns)
     *-pci
          description: Host bridge
          product: 915G/P/GV/GL/PL/910GL Processor to I/O Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@00:00.0
          version: 04
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: 915G/P/GV/GL/PL/910GL PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@00:01.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-display
                description: VGA compatible controller
                product: M24 1P [Radeon Mobility X600]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@01:00.0
                version: 00
                size: 128MB
                width: 32 bits
                clock: 33MHz
                capabilities: vga bus_master cap_list
                resources: iomemory:d0000000-d7ffffff ioport:4000-40ff iomemory: c8100000-c810ffff irq:16
        *-usb:0
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd
             resources: ioport:1800-181f irq:23
           *-usbhost
                product: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) U SB UHCI #1
                vendor: Linux 2.6.12-10-386 uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:1
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd
             resources: ioport:38c0-38df irq:19
           *-usbhost
                product: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) U SB UHCI #2
                vendor: Linux 2.6.12-10-386 uhci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:2
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd
             resources: ioport:38e0-38ff irq:18
           *-usbhost
                product: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) U SB UHCI #3
                vendor: Linux 2.6.12-10-386 uhci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
              *-usb
                   description: Printer
                   product: deskjet 3500
                   vendor: hp
                   physical id: 1
                   bus info: usb@3:1
                   version: 1.00
                   serial: HU38T1R3K67O
                   capabilities: usb-2.00 bidirectional
                   configuration: driver=usblp maxpower=2mA speed=12.0MB/s
        *-usb:3
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@00:1d.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd
             resources: ioport:3c00-3c1f irq:16
           *-usbhost
                product: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) U SB UHCI #4
                vendor: Linux 2.6.12-10-386 uhci_hcd
                physical id: 1
                bus info: usb@4
                logical name: usb4
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
              *-usb
                   description: Mouse
                   product: USB Optical Mouse
                   vendor: Darfon
                   physical id: 1
                   bus info: usb@4:1
                   version: 1.00
                   capabilities: usb-2.00
                   configuration: driver=usbhid maxpower=100mA speed=1.5MB/s
        *-usb:4
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd
             resources: iomemory:c8000000-c80003ff irq:23
           *-usbhost
                product: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) U SB2 EHCI Controller
                vendor: Linux 2.6.12-10-386 ehci_hcd
                physical id: 1
                bus info: usb@5
                logical name: usb5
                version: 2.06
                capabilities: usb-2.00
                configuration: driver=hub maxpower=0mA slots=8 speed=480.0MB/s
              *-usb:0
                   description: Mass storage device
                   product: 5000LE v01.00.00
                   vendor: Maxtor
                   physical id: 1
                   bus info: usb@5:1
                   logical name: scsi0
                   version: 1.00
                   serial: R2R1PV1E
                   capabilities: usb-2.00 scsi emulated scsi-host
                   configuration: driver=usb-storage maxpower=0mA speed=480.0MB/ s
                 *-disk
                      description: SCSI Disk
                      product: 5000LE v01.00.00
                      vendor: Maxtor
                      physical id: 0.0.0
                      bus info: scsi@0.0:0.0
                      logical name: /dev/sda
                      version: 0100
                      size: 76GB
              *-usb:1
                   description: Mass storage device
                   product: USB 2.0  5 IN 1 CARD READER
                   vendor: Aspire 1800
                   physical id: 8
                   bus info: usb@5:8
                   logical name: scsi1
                   version: 3.23
                   serial: 040525200000
                   capabilities: usb-2.00 scsi emulated scsi-host
                   configuration: driver=usb-storage maxpower=96mA speed=480.0MB /s
                 *-disk
                      description: SCSI Disk
                      product: USB20 HS-5IN1
                      vendor: acer
                      physical id: 0.0.0
                      bus info: scsi@1.0:0.0
                      logical name: /dev/sdb
                      version: 3.23
                      capabilities: removable
        *-pci:1
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@00:1e.0
             version: d3
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
           *-firewire
                description: FireWire (IEEE 1394)
                product: TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
                vendor: Texas Instruments
                physical id: 0
                bus info: pci@0a:00.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: ohci bus_master cap_list
                configuration: driver=ohci1394
                resources: iomemory:c8214000-c82147ff iomemory:c8210000-c8213fff  irq:20
           *-network:0
                description: Ethernet interface
                product: NetXtreme BCM5788 Gigabit Ethernet
                vendor: Broadcom Corporation
                physical id: 1
                bus info: pci@0a:01.0
                logical name: eth0
                version: 03
                serial: 00:0f:b0:61:38:9d
                capacity: 1GB/s
                width: 32 bits
                clock: 66MHz
                capabilities: bus_master cap_list ethernet physical mii 10bt 10b t-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegociation
                configuration: autonegociation=on broadcast=yes driver=tg3 drive rversion=3.31 link=no multicast=yes port=twisted pair
                resources: iomemory:c8200000-c820ffff irq:21
           *-network:1
                description: Wireless interface
                product: [AirConn] INPROCOMM IPN 2220 Wireless LAN Adapter (rev 01)
                vendor: Linksys, A Division of Cisco Systems
                physical id: 2
                bus info: pci@0a:02.0
                logical name: wlan0
                version: 00
                serial: 00:0e:9b:94:3c:c8
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ndiswrapper ip=192.168.1.101  link=yes multicast=yes wireless=IEEE 802.11g
                resources: ioport:5000-501f iomemory:c8215000-c821501f iomemory: c8214800-c8214fff irq:22
           *-pcmcia
                description: CardBus bridge
                product: CB1410 Cardbus Controller
                vendor: ENE Technology Inc
                physical id: 4
                bus info: pci@0a:04.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus
                resources: iomemory:20000000-20000fff irq:16
        *-multimedia
             description: Multimedia audio controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1e.2
             bus info: pci@00:1e.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=Intel ICH
             resources: ioport:3000-30ff ioport:3880-38bf iomemory:c8000800-c800 09ff iomemory:c8000400-c80004ff irq:17
        *-communication UNCLAIMED
             description: Modem
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller
             vendor: Intel Corporation
             physical id: 1e.3
             bus info: pci@00:1e.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: generic cap_list
             resources: ioport:3400-34ff ioport:3800-387f irq:20
        *-isa UNCLAIMED
             description: ISA bridge
             product: 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
        *-ide
             description: IDE interface
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@00:1f.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=PIIX_IDE
             resources: ioport:3c40-3c4f irq:18
           *-ide
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-disk
                   description: ATA Disk
                   product: TOSHIBA MK8025GAS
                   vendor: Toshiba
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   version: KA023A
                   serial: 457Q6392T
                   size: 74GB
                   capacity: 74GB
                   capabilities: ata dma lba iordy smart security pm apm
                   configuration: apm=off mode=udma5 smart=on
              *-cdrom
                   description: DVD-RAM writer
                   product: HL-DT-ST DVDRAM GMA-4080N
                   physical id: 1
                   bus info: ide@0.1
                   logical name: /dev/hdb
                   version: 0H37
                   serial: K0053FM0214
                   capabilities: packet atapi cdrom removable nonmagnetic dma lb a iordy pm audio cd-r cd-rw dvd dvd-r dvd-ram
                   configuration: mode=udma2
        *-serial UNCLAIMED
             description: SMBus
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@00:1f.3
             version: 03
             width: 32 bits
             clock: 33MHz
             resources: ioport:3c20-3c3f irq:10

---

### Post by mlomker on 2005-11-24
I'm not sure what processes you've tried, but my how-to's have worked for many people.  You can use the ATI wiki link in my sig.  Let me know if you have any problems.

---

### Post by Teroedni on 2005-11-24
edit 
Try mlomker howto as he is an expert in Ati cards 
Much wiser than me;)

---

### Post by Robocoastie on 2005-11-24
[QUOTE=danne]I did what it said but it didn't work....when I did "fglrxinfo"  --->

Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

bye[/QUOTE]

Then something didn't work. Did you see it build the kernel? If not then likely you missed a step and It's probably the "apt-get install module-assistant" step that's missing because you have to enable the universe and multiverse repositories in order to get that. And without that the ati kernel won't build thus giving the illussion that everything installed when in fact you're actually still stuck with the mesa3d one.

---

### Post by danne on 2005-11-25
[QUOTE=mlomker]I'm not sure what processes you've tried, but my how-to's have worked for many people.  You can use the ATI wiki link in my sig.  Let me know if you have any problems.[/QUOTE]

but I have a notebook with a mobility card....the driver that is in the wiki is the desktop radeon 8500 or higher....???

---

### Post by mlomker on 2005-11-25
[QUOTE=danne]but I have a notebook with a mobility card....the driver that is in the wiki is the desktop radeon 8500 or higher....???[/QUOTE]

I don't know where you're seeing desktop...it's simply 8500+.  I only own a laptop...

---

