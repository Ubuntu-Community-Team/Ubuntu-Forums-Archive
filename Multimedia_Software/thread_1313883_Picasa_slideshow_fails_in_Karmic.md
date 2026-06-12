---
title: "Picasa slideshow fails in Karmic"
date: 2009-11-04
forum: Multimedia Software
---

### Post by Teacher Lion on 2009-11-04
**Hi All,**

Well, I pressed the upgrade button for Karmic and everything went horribly wrong! I backed everything up, formatted, installed it clean... and damn, it's good! Just one slight problem...

I like using Picasa 2.7. It does everything I've ever needed a photo manager to do. I installed it from Synaptic after updating my Software sources. It runs alright but the slideshow isn't working. The program just freezes. After that I've got to right click on the taskbar, close the program, then force quit.

I'd really like everything to return back to normal. Thank you in advance for any help you might be able to offer. Here's my system/graphics info:

**hwinfo --short:**

cpu:                                                            
                       AMD Turion(tm) 64 X2 Mobile Technology TL-60, 2000 MHz
                       AMD Turion(tm) 64 X2 Mobile Technology TL-60, 2000 MHz
keyboard:
  /dev/input/event5    AT Translated Set 2 keyboard
mouse:
  /dev/input/mice      Logitech USB Optical Mouse
  /dev/input/mice      Macintosh mouse button emulation
  /dev/input/mice      SynPS/2 Synaptics TouchPad
graphics card:
                       nVidia GeForce 8400M G
sound:
                       nVidia MCP67 High Definition Audio
storage:
                       nVidia MCP67 IDE Controller
                       nVidia MCP67 AHCI Controller
network:
  eth0                 nVidia MCP67 Ethernet
  wlan0                Atheros AR5006EG 802.11bg NIC (2.4GHz, PCI Express)
network interface:
  lo                   Loopback network interface
  eth0                 Ethernet network interface
  wmaster0             Network Interface
  wlan0                WLAN network interface
  pan0                 Ethernet network interface
disk:
  /dev/sda             ST9160821AS
partition:
  /dev/sda1            Partition
  /dev/sda2            Partition
  /dev/sda3            Partition
  /dev/sda4            Partition
  /dev/sda5            Partition
cdrom:
  /dev/sr0             MATSHITA DVD-RAM UJ-860S
usb controller:
                       nVidia MCP67 OHCI USB 1.1 Controller
                       nVidia MCP67 EHCI USB 2.0 Controller
                       nVidia MCP67 OHCI USB 1.1 Controller
                       nVidia MCP67 EHCI USB 2.0 Controller
bios:
                       BIOS
bridge:
                       nVidia MCP67 ISA Bridge
                       nVidia MCP67 PCI Bridge
                       nVidia MCP67 PCI Express Bridge
                       nVidia MCP67 PCI Express Bridge
                       nVidia MCP67 PCI Express Bridge
                       AMD K8 [Athlon64/Opteron] HyperTransport Technology Configuration
                       AMD K8 [Athlon64/Opteron] Address Map
                       AMD K8 [Athlon64/Opteron] DRAM Controller
                       AMD K8 [Athlon64/Opteron] Miscellaneous Control
hub:
                       Linux 2.6.31-14-generic ehci_hcd EHCI Host Controller
                       Linux 2.6.31-14-generic ehci_hcd EHCI Host Controller
                       Linux 2.6.31-14-generic ohci_hcd OHCI Host Controller
                       Linux 2.6.31-14-generic ohci_hcd OHCI Host Controller
memory:
                       Main Memory
firewire controller:
                       Ricoh R5C832 IEEE 1394 Controller
bluetooth:
                       ASUSTek Bluetooth Device
unknown:
                       FPU
                       DMA controller
                       PIC
                       Timer
                       Keyboard controller
                       nVidia MCP67 Memory Controller
                       nVidia MCP67 SMBus
                       Ricoh R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
                       Ricoh R5C843 MMC Host Controller
                       Ricoh R5C592 Memory Stick Bus Host Adapter
                       Ricoh xD-Picture Card Controller
  /dev/input/event10   Chicony Electronics USB2.0 0.3M UVC WebCam

**glxinfo:**

name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_EXT_texture_from_pixmap, GLX_ARB_create_context, GLX_ARB_multisample, 
    GLX_NV_float_buffer, GLX_ARB_fbconfig_float, GLX_EXT_framebuffer_sRGB
client glx vendor string: NVIDIA Corporation
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_EXT_import_context, GLX_SGI_video_sync, 
    GLX_NV_swap_group, GLX_NV_video_out, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGI_swap_control, GLX_ARB_create_context, GLX_NV_float_buffer, 
    GLX_ARB_fbconfig_float, GLX_EXT_fbconfig_packed_float, 
    GLX_EXT_texture_from_pixmap, GLX_EXT_framebuffer_sRGB, 
    GLX_NV_present_video, GLX_NV_multisample_coverage
GLX version: 1.3
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_EXT_texture_from_pixmap, GLX_ARB_create_context, GLX_ARB_multisample, 
    GLX_NV_float_buffer, GLX_ARB_fbconfig_float, GLX_EXT_framebuffer_sRGB, 
    GLX_ARB_get_proc_address
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce 8400M G/PCI/SSE2
OpenGL version string: 3.0.0 NVIDIA 185.18.36
OpenGL shading language version string: 1.30 NVIDIA via Cg compiler

---

### Post by Teacher Lion on 2009-11-05
I just tried reinstalling everything and no luck. This'll sound stupid but I thought that Wine was somehow integrated with Karmic so I saw no need to install it. Picasa seemed to run just fine without it, slideshow failure aside. That was all a bit confusing. Anyway, I have installed Wine and have messed around with the configuration and nothing has changed.

The only thing I've found that might be worth mentioning is that there's this page fault thing that comes up (see attachment) when I first try and run it. I don't think that happened in Jaunty.

I have also just noticed that I posted this thread in the wrong place. I got in trouble once for duplicating a thread elsewhere (understandable, really) though if one of the powers that be wouldn't mind moving it for me that would be rather nice.

---

