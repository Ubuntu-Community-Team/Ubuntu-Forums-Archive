---
title: "ATI 9550 using Envy"
date: 2007-02-26
forum: Multimedia &amp; Video
---

### Post by Gnoobuntu on 2007-02-26
I used the Envy script to install the drivers for my ATI Radeon 9550 and much to my dismay it made my system crash HARD. I used Envy again to REMOVE the drivers. I thought that it would just be a reversal of the install script and everything would revert to my systems previous state, but alas, the remove script failed to RE-install what it had removed leaving me without a desktop.

I know all of this sounds rather vague and nebulous, but as my name declares, I am a complete nuubie and don't really know the correct terminology and lingo of linux yet.   Anyway....

Instead of trying this, that and the other guide and getting things REALLY messed up in my system I figured that I'd do a fresh install of Ubuntu and work just ONE guild (Envy) and work the issue untill it gets resolved.

I think that I should:

A: take a snapshot of my computer as it is now right after the install

B: post the results of the envy script to see what it changed

C: post my Xorg.conf post Envy (if I can get it)


[SIZE="4"]**LSHW**[/SIZE]

ubuntu                    
    description: Desktop Computer
    product: K7VME
    vendor: soyocomputer
    version: 1.0
    serial: 00000000
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: chassis=desktop
  *-core
       description: Motherboard
       product: K7VME
       vendor: soyocomputer
       physical id: 0
       version: 1.0
       serial: 00000000
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: Version 07.00T (04/02/01)
          size: 64KB
          capacity: 192KB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: AMD Athlon(tm) XP 2000+
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 6.8.1
          slot: Socket-A
          size: 1667MHz
          capacity: 3GHz
          width: 32 bits
          clock: 133MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mmxext 3dnowext 3dnow up ts
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
          size: 767MB
     *-pci
          description: Host bridge
          product: VT8378 [KM400/A] Chipset Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: e0000000
          bus info: pci@00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
          resources: iomemory:e0000000-e3ffffff
        *-pci
             description: PCI bridge
             product: VT8237 PCI Bridge
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master cap_list
           *-display:0
                description: VGA compatible controller
                product: RV350 AS [Radeon 9550]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@01:00.0
                version: 00
                size: 256MB
                width: 32 bits
                clock: 66MHz
                capabilities: vga bus_master cap_list
                resources: iomemory:c0000000-cfffffff ioport:c800-c8ff iomemory:dfef0000-dfefffff irq:193
           *-display:1 UNCLAIMED
                description: Display controller
                product: RV350 ?? [Radeon 9550] (Secondary)
                vendor: ATI Technologies Inc
                physical id: 0.1
                bus info: pci@01:00.1
                version: 00
                size: 256MB
                width: 32 bits
                clock: 66MHz
                capabilities: bus_master cap_list
                resources: iomemory:b0000000-bfffffff iomemory:dfee0000-dfeeffff
        *-communication UNCLAIMED
             description: Communication controller
             product: HCF 56k Data/Fax/Voice/Spkp Modem
             vendor: Conexant
             physical id: 9
             bus info: pci@00:09.0
             version: 08
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             resources: iomemory:dffe0000-dffeffff ioport:ec00-ec07 irq:10
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
             resources: ioport:e800-e81f irq:169
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.17-10-generic uhci_hcd
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
             resources: ioport:e400-e41f irq:169
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.17-10-generic uhci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
              *-usb
                   description: Generic USB device
                   product: ClickSmart 310
                   vendor: Logitech, Inc.
                   physical id: 2
                   bus info: usb@2:2
                   version: 0.90
                   capabilities: usb-1.00
                   configuration: driver=spca5xx maxpower=500mA speed=12.0MB/s
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
             resources: ioport:e000-e01f irq:169
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.17-10-generic uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
              *-usb:0
                   description: Printer
                   product: deskjet 3320
                   vendor: hp
                   physical id: 1
                   bus info: usb@1:1
                   version: 1.00
                   serial: TH3183D0C843
                   capabilities: usb-2.00 bidirectional
                   configuration: driver=usblp maxpower=2mA speed=12.0MB/s
              *-usb:1
                   description: Mouse
                   product: USB 3D Mouse
                   vendor: ARROW STRONG
                   physical id: 2
                   bus info: usb@1:2
                   version: 0.10
                   capabilities: usb-1.00
                   configuration: driver=usbhid maxpower=40mA speed=1.5MB/s
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
             resources: iomemory:dfffff00-dfffffff irq:169
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 2.6.17-10-generic ehci_hcd
                physical id: 1
                bus info: usb@4
                logical name: usb4
                version: 2.06
                capabilities: usb-2.00
                configuration: driver=hub maxpower=0mA slots=6 speed=480.0MB/s
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
              *-disk
                   description: ATA Disk
                   product: Maxtor 92041U4
                   vendor: Maxtor
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   version: FA520860
                   serial: G407D0WC
                   size: 19GB
                   capacity: 19GB
                   capabilities: ata dma lba iordy smart pm apm partitioned partitioned:dos
                   configuration: apm=off smart=on
                 *-volume:0
                      description: HPFS/NTFS partition
                      physical id: 1
                      bus info: ide@0.0,1
                      logical name: /dev/hda1
                      capacity: 12GB
                      capabilities: primary bootable
                 *-volume:1
                      description: Linux filesystem partition
                      physical id: 2
                      bus info: ide@0.0,2
                      logical name: /dev/hda2
                      capacity: 6785MB
                      capabilities: primary
                 *-volume:2
                      description: Extended partition
                      physical id: 3
                      bus info: ide@0.0,3
                      logical name: /dev/hda3
                      capacity: 203MB
                      capabilities: extended partitioned partitioned:extended
              *-cdrom
                   description: CD-R/CD-RW writer
                   product: 32X10
                   physical id: 1
                   bus info: ide@0.1
                   logical name: /dev/hdb
                   version: T.FA
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio cd-r cd-rw
                 *-disc
                      physical id: 0
                      logical name: /dev/hdb
           *-ide:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 33MHz
              *-cdrom
                   description: DVD reader
                   product: DVD-ROM BDV212B
                   physical id: 1
                   bus info: ide@1.1
                   logical name: /dev/hdd
                   version: VER 0p43
                   serial: MT1318 Firmware
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio dvd
                   configuration: mode=udma2
                 *-disc
                      physical id: 0
                      logical name: /dev/hdd
        *-multimedia
             description: Multimedia audio controller
             product: VT8233/A/8235/8237 AC97 Audio Controller
             vendor: VIA Technologies, Inc.
             physical id: 11.5
             bus info: pci@00:11.5
             version: 50
             width: 32 bits
             clock: 33MHz
             capabilities: cap_list
             configuration: driver=VIA 82xx Audio
             resources: ioport:dc00-dcff irq:185
        *-network
             description: Ethernet interface
             product: VT6102 [Rhine-II]
             vendor: VIA Technologies, Inc.
             physical id: 12
             bus info: pci@00:12.0
             logical name: eth0
             version: 74
             serial: 00:50:2c:a6:4d:03
             size: 10MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
             configuration: autonegociation=on broadcast=yes driver=via-rhine driverversion=1.2.0-2.6 duplex=half link=yes multicast=yes port=MII speed=10MB/s
             resources: ioport:d800-d8ff iomemory:dffffe00-dffffeff irq:177
steve@Ubuntu:~$ 


**[SIZE="5"]XORG.CONF[/SIZE]**

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	FontPath	"/usr/share/fonts/X11/misc"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. RV350 AS [Radeon 9600]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. RV350 AS [Radeon 9600]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection


**[SIZE="5"]GLXINFO[/SIZE]**

 glxinfo
name of display: :0.0
libGL warning: 3D driver claims to not support visual 0x4b
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig, GLX_MESA_copy_sub_buffer
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 
    GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_OML_sync_control, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_MESA_swap_control, GLX_MESA_swap_frame_usage, GLX_OML_swap_method, 
    GLX_SGI_video_sync, GLX_SGIS_multisample, GLX_SGIX_fbconfig
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI R300 20060815 AGP 1x TCL
OpenGL version string: 1.3 Mesa 6.5.1
OpenGL extensions:
    GL_ARB_fragment_program, GL_ARB_imaging, GL_ARB_multisample, 
    GL_ARB_multitexture, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_MESAX_texture_float, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, 
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_window_pos, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_clip_volume_hint, 
    GL_EXT_compiled_vertex_array, GL_EXT_convolution, GL_EXT_copy_texture, 
    GL_EXT_draw_range_elements, GL_EXT_gpu_program_parameters, 
    GL_EXT_histogram, GL_EXT_packed_pixels, GL_EXT_polygon_offset, 
    GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp, 
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_vertex_array, 
    GL_APPLE_packed_pixels, GL_ATI_blend_equation_separate, 
    GL_ATI_texture_env_combine3, GL_ATI_texture_mirror_once, 
    GL_IBM_rasterpos_clip, GL_IBM_texture_mirrored_repeat, 
    GL_INGR_blend_func_separate, GL_MESA_pack_invert, GL_MESA_ycbcr_texture, 
    GL_MESA_window_pos, GL_NV_blend_square, GL_NV_light_max_exponent, 
    GL_NV_texture_rectangle, GL_NV_texgen_reflection, GL_NV_vertex_program, 
    GL_OES_read_format, GL_SGI_color_matrix, GL_SGI_color_table, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x24 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x26 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x27 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x29 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x2b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2c 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x2d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2e 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x2f 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x30 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x31 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x32 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x4b 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon
steve@Ubuntu:~$ 

Also.... I get this message when I do GLXGEARS:

 glxgears
libGL warning: 3D driver claims to not support visual 0x4b
*********************************WARN_ONCE*********************************
File radeon_mm.c function radeon_mm_alloc line 216
Ran out of GART memory!
Please consider adjusting GARTSize option.
***************************************************************************
Error: Could not get dma buffer... exiting
steve@Ubuntu:~$ 


GlxGears runs fine.... for 2 or 3 seconds before crapping out.

That's about it for now.  Is there anyother info that I should post before I try the script again?


Steve

---

### Post by el_rata on 2007-02-26
follow this guide, i always do this guide when i have to reinstall or when i recompile the kernel

[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)


let me know how it worked for you.

---

### Post by Gnoobuntu on 2007-02-27
Okay,....

So I ran the Envy script. Here's the output of that:

steve@Ubuntu:~$ sudo envy


       +-------------------------------------------------+
       |                                                 |
       |             Welcome to Envy 0.8.2               |
       |                                                 |
       |    Developed by Alberto Milone (aka tseliot)    |
       |                                                 |
       +-------------------------------------------------+


       +-----------------------------------------------------------+
       |    Envy Menu ver.0.8.2                                    |
       |                                                           |
       |    1 - Install the NVIDIA driver                          |
       |                                                           |
       |    2 - Uninstall the NVIDIA driver                        |
       |                                                           |
       |    3 - Install the ATI driver                             |
       |                                                           |
       |    4 - Uninstall the ATI driver                           |
       |                                                           |
       |    5 - Install the ATI/NVIDIA driver Manually             |
       |                                                           |
       |    6 - Restart the Xserver                                |
       |                                                           |
       |    7 - Exit                                               |
       |                                                           |
       |    NOTE: IF THE SCREEN TURNS BLACK, PLEASE TYPE ALT+F1    |
       +-----------------------------------------------------------+
Please select one of the activities displayed above and press ENTER:

3
rm: cannot remove `*.deb': No such file or directory
Ubuntu Edgy 32bit
Your graphic card has been detected as a ATI Radeon 9550
Your graphic card is supported by the latest driver
 * Stopping GNOME Display Manager...                                     [ ok ] 
[COLOR="Red"]sudo: /etc/init.d/kdm: command not found[/COLOR]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-2.6.17-10-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 126 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 126 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  xserver-xorg-dev
0 upgraded, 1 newly installed, 0 to remove and 126 not upgraded.
Need to get 297kB of archives.
After unpacking 1667kB of additional disk space will be used.
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main xserver-xorg-dev 1:1.1.1-0ubuntu12.1 [297kB]
Fetched 297kB in 1s (150kB/s)            
Selecting previously deselected package xserver-xorg-dev.
(Reading database ... 93502 files and directories currently installed.)
Unpacking xserver-xorg-dev (from .../xserver-xorg-dev_1%3a1.1.1-0ubuntu12.1_i386.deb) ...
Setting up xserver-xorg-dev (1.1.1-0ubuntu12.1) ...
Reading package lists... Done
Building dependency tree       
Reading state information... Done
pkg-config is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 126 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gcc is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 126 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
debconf is already the newest version.
libstdc++5 is already the newest version.
The following extra packages will be installed:
  html2text
The following NEW packages will be installed:
  debhelper dh-make fakeroot html2text module-assistant
0 upgraded, 5 newly installed, 0 to remove and 126 not upgraded.
Need to get 814kB of archives.
After unpacking 2777kB of additional disk space will be used.
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe module-assistant 0.10.6 [80.5kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main html2text 1.3.2a-3 [95.5kB]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main debhelper 5.0.37.3ubuntu4 [508kB]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main dh-make 0.41ubuntu1 [35.8kB]
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main fakeroot 1.5.9ubuntu1 [94.7kB]
Fetched 814kB in 4s (172kB/s) 
Selecting previously deselected package html2text.
(Reading database ... 93665 files and directories currently installed.)
Unpacking html2text (from .../html2text_1.3.2a-3_i386.deb) ...
Selecting previously deselected package debhelper.
Unpacking debhelper (from .../debhelper_5.0.37.3ubuntu4_all.deb) ...
Selecting previously deselected package dh-make.
Unpacking dh-make (from .../dh-make_0.41ubuntu1_all.deb) ...
Selecting previously deselected package fakeroot.
Unpacking fakeroot (from .../fakeroot_1.5.9ubuntu1_i386.deb) ...
Selecting previously deselected package module-assistant.
Unpacking module-assistant (from .../module-assistant_0.10.6_all.deb) ...
Setting up html2text (1.3.2a-3) ...

Setting up debhelper (5.0.37.3ubuntu4) ...
Setting up dh-make (0.41ubuntu1) ...
Setting up fakeroot (1.5.9ubuntu1) ...

Setting up module-assistant (0.10.6) ...
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package fglrx-control is not installed, so not removed
E: Couldn't find package fglrx-kernel-2.6.17-10-generic
An installer has been detected
md5new: d784fa8b6d98d27699781bd9a7cf19f0
md5sumold: 5fbd42d666d467a904acbaeb600c1d5a
md5 Error! Trying to fetch the driver from the website
No installer detected
Download of the driver in progress, please wait
--08:06:41--  [https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.33.6-x86.x86_64.run](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.33.6-x86.x86_64.run)
           => `ati-driver-installer-8.33.6-x86.x86_64.run'
Resolving a248.e.akamai.net... 204.2.192.40, 204.2.192.46
Connecting to a248.e.akamai.net|204.2.192.40|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 58,620,730 (56M) [application/octet-stream]

100%[====================================>] 58,620,730   185.74K/s    ETA 00:00

08:11:58 (181.28 KB/s) - `ati-driver-installer-8.33.6-x86.x86_64.run' saved [58620730/58620730]

md5new: 5fbd42d666d467a904acbaeb600c1d5a
md5sumold: 5fbd42d666d467a904acbaeb600c1d5a
rm: cannot remove `/usr/src/fglrx-kernel*.deb': No such file or directory
Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.33.6...................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================
Generating package: Ubuntu/edgy
Package /usr/share/envy/xorg-driver-fglrx_8.33.6-1_i386.deb has been successfully generated
Package /usr/share/envy/xorg-driver-fglrx-dev_8.33.6-1_i386.deb has been successfully generated
Package /usr/share/envy/fglrx-kernel-source_8.33.6-1_i386.deb has been successfully generated
Package /usr/share/envy/fglrx-control_8.33.6-1_i386.deb has been successfully generated
Package /usr/share/envy/fglrx-sources_8.33.6-1_i386.deb has been successfully generated
Removing temporary directory: fglrx-install
Selecting previously deselected package fglrx-control.
(Reading database ... 94082 files and directories currently installed.)
Unpacking fglrx-control (from fglrx-control_8.33.6-1_i386.deb) ...
Selecting previously deselected package fglrx-kernel-source.
Unpacking fglrx-kernel-source (from fglrx-kernel-source_8.33.6-1_i386.deb) ...
Selecting previously deselected package fglrx-sources.
Unpacking fglrx-sources (from fglrx-sources_8.33.6-1_i386.deb) ...
Selecting previously deselected package xorg-driver-fglrx-dev.
Unpacking xorg-driver-fglrx-dev (from xorg-driver-fglrx-dev_8.33.6-1_i386.deb) ...
Selecting previously deselected package xorg-driver-fglrx.
Unpacking xorg-driver-fglrx (from xorg-driver-fglrx_8.33.6-1_i386.deb) ...
Setting up fglrx-kernel-source (8.33.6-1) ...
Setting up fglrx-sources (8.33.6-1) ...
Setting up xorg-driver-fglrx (8.33.6-1) ...
Starting atieventsd: done.

Setting up fglrx-control (8.33.6-1) ...

Setting up xorg-driver-fglrx-dev (8.33.6-1) ...
Getting source for kernel version: 2.6.17-10-generic
Kernel headers available in /lib/modules/2.6.17-10-generic/build
Creating symlink...
apt-get install build-essential 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 126 not upgraded.

Done!

Updated infos about 84 packages
Extracting the package tarball, /usr/src/fglrx.tar.bz2, please wait...
Done with /usr/src/fglrx-kernel-2.6.17-10-generic_8.33.6-1+2.6.17.1-10.34_i386.deb .
Selecting previously deselected package fglrx-kernel-2.6.17-10-generic.
(Reading database ... 94220 files and directories currently installed.)
Unpacking fglrx-kernel-2.6.17-10-generic (from .../fglrx-kernel-2.6.17-10-generic_8.33.6-1+2.6.17.1-10.34_i386.deb) ...
Setting up fglrx-kernel-2.6.17-10-generic (8.33.6-1+2.6.17.1-10.34) ...

Do you want your xorg.conf to be automatically configured? (y/n) \ "y" is the default answer
y
Uninitialised file found, configuring.
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.original-0
Warning: Option 'VideoOverlay' doesn't affect running session.
Warning: Option 'OpenGLOverlay' doesn't affect running session.
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.fglrx-0
Do you want to restart your computer now (Recommended)? (y/n) \ "y" is the default answer


It appears that I've got one error.
sudo: /etc/init.d/kdm: command not found

What is this command? Gonna restart my computer now... *crosses fingers*..............................

---

### Post by Gnoobuntu on 2007-02-27
The plot thickens!


rm: cannot remove `*.deb': No such file or directory
[COLOR="red"]Ubuntu Edgy 32bit[/COLOR]
Your graphic card has been detected as a ATI Radeon 9550
Your graphic card is supported by the latest driver
* Stopping GNOME Display Manager... [ ok ] 
[COLOR="Red"]sudo: /etc/init.d/kdm: command not found[/COLOR]

Edgy correctly detected my graphics card and the version of Ubuntu that I am using, but
failed to give a version specific command.  Apparently KDM is from Ubuntu 6.06 and GDM is from Ubuntu 6.10.

Not sure if NOT shutting down GDM during the install of the graphics drivers would cause it to crash or not, but I'm sure Mr. Elliot had a good reason to want GDM to close.  *shrug* 

Stay tuned.....

---

### Post by Gnoobuntu on 2007-02-27
> **Gnoobuntu said:**
> The plot thickens!


rm: cannot remove `*.deb': No such file or directory
[COLOR="red"]Ubuntu Edgy 32bit[/COLOR]
Your graphic card has been detected as a ATI Radeon 9550
Your graphic card is supported by the latest driver
* Stopping GNOME Display Manager... [ ok ] 
[COLOR="Red"]sudo: /etc/init.d/kdm: command not found[/COLOR]

.

What a dope I am.... 

Envy gave BOTH commands... *eye roll*

---

### Post by tseliot on 2007-02-27
The things which you  highlighted are warnings (not errors) therefore you shouldn't worry about that.

Add these lines to the end of your /etc/X11/xorg.conf:
```
Section "ServerFlags"
        Option  "AIGLX" "off"
EndSection
```

I would like to see your /var/log/Xorg.0.log

---

### Post by Gnoobuntu on 2007-02-28
I reinstalled Ubuntu again as I had no desktop to speak of and didn't know how to get it back.
I pasted the code into my Xorg.conf before running envy.
Would you recommend running the update manager before running envy?

I'm running a dual boot system. Could you please tell me how I can output the log and conf files to a text file and put them in the root of my XP install?  That way if I can't get a desktop running in linux I can log into windows and get  the filles and post them here.

Thanks for your help!

Steve

I've attached my fresh out of the box, pre envy /var/log/Xorg.0.log  it was too big to paste

---

### Post by Gnoobuntu on 2007-02-28
I can't paste the whole file or attach it either. Is there someplace that I can send the file please?

---

### Post by el_rata on 2007-02-28
wait ... stop .... WHAT?!?!?!? .... GDM is for Gnome and KDM is for KDE ... if you are using Gnome the correct command is 

sudo /etc/init.d/gdm restart

did you use the guide i posted earlier??

i always make that installation and i've never had any problems with my ati drivers. just follow the instructions. i know it works.

---

### Post by doobydave on 2007-02-28
@gnoobuntu

Click 'manage attachments' to post a file when making a post

For /var/log/Xorg.0.log you will have to make a copy and rename it to a *.txt file.

The forum only allows certain filetypes to be posted.

---

