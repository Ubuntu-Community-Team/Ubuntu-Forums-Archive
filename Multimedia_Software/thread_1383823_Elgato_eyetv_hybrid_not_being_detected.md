---
title: "Elgato eyetv hybrid not being detected"
date: 2010-01-17
forum: Multimedia Software
---

### Post by friesgaard on 2010-01-17
Hello.
I installed mythbuntu 9.10 this week on some old hardware, I had a Hauppauge 500MCE PVR in and made it work fairly easy. I'm used to gentoo :-)

However, I want to record HD signal, so I plugged in a Eyetv hybrid and followed this guide
[http://ubuntuforums.org/showthread.php?t=1015387]("http://ubuntuforums.org/showthread.php?t=1015387")

I extracted the driver, put it in into /lib/firmware, modprobed em28xx, rebooted. When I plug in the device, it is not recognised. I tried both usb ports. The ID is "0fd9:0018", which is somewhat different from similar hardware e.g. Hauppauge wintv-hvr-950 (ID 2040:6513 [http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-950]("http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-950") )

I think the hardware has been updated, hope someone knows how to crack this one :-)
Thanks, Morten


I have added some additional information below!
# uname -a
> Linux m 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686 GNU/Linux

# lsmod | egrep -R "video|em|video|v4l"
> 
em28xx                 80968  0 
ir_common              48512  1 em28xx
videobuf_vmalloc        6496  1 em28xx
videobuf_core          17952  2 em28xx,videobuf_vmalloc
v4l2_common            17500  6 em28xx,wm8775,tuner,cx25840,ivtv,cx2341x
videodev               36736  6 em28xx,wm8775,tuner,cx25840,ivtv,v4l2_common
v4l1_compat            14496  1 videodev
tveeprom               11872  2 em28xx,ivtv


# lsusb
> Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0fd9:0018  
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


# lsusb -v -d 0fd9:0018
> 
Bus 002 Device 002: ID 0fd9:0018  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x0fd9 
  idProduct          0x0018 
  bcdDevice            1.00
  iManufacturer           3 
  iProduct                1 
  iSerial                 2 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength          305
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           4
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol    255 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0001  1x 1 bytes
        bInterval             100
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0000  1x 0 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0000  1x 0 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x84  EP 4 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0000  1x 0 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       1
      bNumEndpoints           4
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol    255 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0001  1x 1 bytes
        bInterval             100
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0000  1x 0 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x84  EP 4 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0000  1x 0 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       2
      bNumEndpoints           4
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol    255 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0001  1x 1 bytes
        bInterval             100
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0280  1x 640 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0000  1x 0 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x84  EP 4 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0000  1x 0 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       3
      bNumEndpoints           4
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol    255 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0001  1x 1 bytes
        bInterval             100
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0300  1x 768 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0000  1x 0 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x84  EP 4 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0000  1x 0 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       4
      bNumEndpoints           4
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol    255 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0001  1x 1 bytes
        bInterval             100
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0340  1x 832 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0000  1x 0 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x84  EP 4 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0000  1x 0 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       5
      bNumEndpoints           4
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol    255 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0001  1x 1 bytes
        bInterval             100
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0380  1x 896 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0000  1x 0 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x84  EP 4 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0000  1x 0 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       6
      bNumEndpoints           4
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol    255 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0001  1x 1 bytes
        bInterval             100
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x03c0  1x 960 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0000  1x 0 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x84  EP 4 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0000  1x 0 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       7
      bNumEndpoints           4
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol    255 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0001  1x 1 bytes
        bInterval             100
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x03fc  1x 1020 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0000  1x 0 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x84  EP 4 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0000  1x 0 bytes
        bInterval               1


# dmesg
> [    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.31-14-generic (buildd@rothera) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 (Ubuntu 2.6.31-14.48-generic)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001feb0000 (usable)
[    0.000000]  BIOS-e820: 000000001feb0000 - 000000001fefc000 (ACPI data)
[    0.000000]  BIOS-e820: 000000001fefc000 - 000000001fefd000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000001fefd000 - 000000001ff00000 (reserved)
[    0.000000]  BIOS-e820: 000000001ff00000 - 000000001ff80000 (usable)
[    0.000000]  BIOS-e820: 000000001ff80000 - 0000000020000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff800000 - 00000000ffc00000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] DMI present.
[    0.000000] last_pfn = 0x1ff80 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-C7FFF write-protect
[    0.000000]   C8000-E3FFF uncachable
[    0.000000]   E4000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask FE0000000 write-back
[    0.000000]   1 disabled
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 0000000000002000 - 0000000000006000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 000000000009f800 (usable)
[    0.000000]  modified: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000001feb0000 (usable)
[    0.000000]  modified: 000000001feb0000 - 000000001fefc000 (ACPI data)
[    0.000000]  modified: 000000001fefc000 - 000000001fefd000 (ACPI NVS)
[    0.000000]  modified: 000000001fefd000 - 000000001ff00000 (reserved)
[    0.000000]  modified: 000000001ff00000 - 000000001ff80000 (usable)
[    0.000000]  modified: 000000001ff80000 - 0000000020000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000ff800000 - 00000000ffc00000 (reserved)
[    0.000000]  modified: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-000000001ff80000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 001fc00000 page 2M
[    0.000000]  001fc00000 - 001ff80000 page 4k
[    0.000000] kernel direct mapping tables up to 1ff80000 @ 7000-c000
[    0.000000] RAMDISK: 177f9000 - 17f43032
[    0.000000] ACPI: RSDP 000f5fc0 00014 (v00 PTLTD )
[    0.000000] ACPI: RSDT 1fef87f4 00030 (v01 PTLTD    RSDT   060400D0  LTP 00000000)
[    0.000000] ACPI: FACP 1fefbf0a 00074 (v01 IBM    MARLIN   060400D0 PTL  00000001)
[    0.000000] ACPI: DSDT 1fef8824 036E6 (v01    IBM   Marlin 060400D0 MSFT 0100000D)
[    0.000000] ACPI: FACS 1fefcfc0 00040
[    0.000000] ACPI: APIC 1fefbf7e 0005A (v01 PTLTD  	 APIC   060400D0  LTP 00000000)
[    0.000000] ACPI: BOOT 1fefbfd8 00028 (v01 PTLTD  $SBFTBL$ 060400D0  LTP 00000001)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 511MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 1ff80000
[    0.000000]   low ram: 0 - 1ff80000
[    0.000000]   node 0 low ram: 00000000 - 1ff80000
[    0.000000]   node 0 bootmap 00008000 - 0000bff0
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 001ff80000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008a80a0]    TEXT DATA BSS ==> [0000100000 - 00008a80a0]
[    0.000000]   #4 [00177f9000 - 0017f43032]          RAMDISK ==> [00177f9000 - 0017f43032]
[    0.000000]   #5 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
[    0.000000]   #6 [00008a9000 - 00008ac0ac]              BRK ==> [00008a9000 - 00008ac0ac]
[    0.000000]   #7 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
[    0.000000]   #8 [0000008000 - 000000c000]          BOOTMAP ==> [0000008000 - 000000c000]
[    0.000000] found SMP MP-table at [c00f5f70] f5f70
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x0001ff80
[    0.000000]   HighMem  0x0001ff80 -> 0x0001ff80
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[4] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0001feb0
[    0.000000]     0: 0x0001ff00 -> 0x0001ff80
[    0.000000] On node 0 totalpages: 130763
[    0.000000] free_area_init_node: node 0, pgdat c0784900, node_mem_map c1000000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3963 pages, LIFO batch:0
[    0.000000]   Normal zone: 991 pages used for memmap
[    0.000000]   Normal zone: 125777 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 000000001feb0000 - 000000001fefc000
[    0.000000] PM: Registered nosave memory: 000000001fefc000 - 000000001fefd000
[    0.000000] PM: Registered nosave memory: 000000001fefd000 - 000000001ff00000
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 20000000:dec00000)
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages at c1402000, static data 35612 bytes
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 129740
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-14-generic root=UUID=e65cf676-7e29-4252-af07-650d4e0e6507 ro quiet splash
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 2618880 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (00000000:00000000)
[    0.000000] Memory: 500116k/523776k available (4565k kernel code, 22476k reserved, 2143k data, 540k init, 0k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xe0780000 - 0xff7fe000   ( 496 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xdff80000   ( 511 MB)
[    0.000000]       .init : 0xc078e000 - 0xc0815000   ( 540 kB)
[    0.000000]       .data : 0xc0575554 - 0xc078d308   (2143 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0575554   (4565 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=128, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.000000] NR_IRQS:2304 nr_irqs:256
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1595.004 MHz processor.
[    0.001786] Console: colour VGA+ 80x25
[    0.001796] console [tty0] enabled
[    0.004018] Calibrating delay loop (skipped), value calculated using timer frequency.. 3190.00 BogoMIPS (lpj=6380016)
[    0.004066] Security Framework initialized
[    0.004114] AppArmor: AppArmor initialized
[    0.004133] Mount-cache hash table entries: 512
[    0.004449] Initializing cgroup subsys ns
[    0.004463] Initializing cgroup subsys cpuacct
[    0.004475] Initializing cgroup subsys memory
[    0.004496] Initializing cgroup subsys freezer
[    0.004503] Initializing cgroup subsys net_cls
[    0.004543] CPU: Trace cache: 12K uops, L1 D cache: 8K
[    0.004553] CPU: L2 cache: 256K
[    0.004560] CPU: Hyper-Threading is disabled
[    0.004571] mce: CPU supports 4 MCE banks
[    0.004594] CPU0: Thermal monitoring enabled (TM1)
[    0.004618] Performance Counters: no PMU driver, software counters only.
[    0.004636] Checking 'hlt' instruction... OK.
[    0.021577] SMP alternatives: switching to UP code
[    0.036060] Freeing SMP alternatives: 19k freed
[    0.036114] ACPI: Core revision 20090521
[    0.052551] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.093564] CPU0: Intel(R) Pentium(R) 4 CPU 1.60GHz stepping 02
[    0.096001] Brought up 1 CPUs
[    0.096001] Total of 1 processors activated (3190.00 BogoMIPS).
[    0.096001] CPU0 attaching NULL sched-domain.
[    0.096001] Booting paravirtualized kernel on bare hardware
[    0.096001] regulator: core version 0.5
[    0.096001] Time: 21:42:55  Date: 01/17/10
[    0.096001] NET: Registered protocol family 16
[    0.096001] EISA bus registered
[    0.096001] ACPI: bus type pci registered
[    0.096001] PCI: PCI BIOS revision 2.10 entry at 0xfd933, last bus=3
[    0.096001] PCI: Using configuration type 1 for base access
[    0.097533] bio: create slab <bio-0> at 0
[    0.098588] ACPI: EC: Look up EC in DSDT
[    0.118294] ACPI: Interpreter enabled
[    0.118310] ACPI: (supports S0 S1 S3 S4 S5)
[    0.118374] ACPI: Using IOAPIC for interrupt routing
[    0.163236] ACPI: No dock devices found.
[    0.165480] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.165606] pci 0000:00:00.0: reg 10 32bit mmio: [0xd4000000-0xd7ffffff]
[    0.165865] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH4 ACPI/GPIO/TCO
[    0.165874] pci 0000:00:1f.0: quirk: region 1180-11bf claimed by ICH4 GPIO
[    0.165937] pci 0000:00:1f.1: reg 20 io port: [0x1800-0x180f]
[    0.166020] pci 0000:00:1f.2: reg 20 io port: [0x1820-0x183f]
[    0.166104] pci 0000:00:1f.3: reg 20 io port: [0x1810-0x181f]
[    0.166185] pci 0000:00:1f.4: reg 20 io port: [0x1840-0x185f]
[    0.166244] pci 0000:00:1f.5: reg 10 io port: [0x1c00-0x1cff]
[    0.166257] pci 0000:00:1f.5: reg 14 io port: [0x1880-0x18bf]
[    0.166361] pci 0000:01:00.0: reg 10 32bit mmio: [0xd0000000-0xd0ffffff]
[    0.166374] pci 0000:01:00.0: reg 14 32bit mmio: [0xe0000000-0xe7ffffff]
[    0.166386] pci 0000:01:00.0: reg 18 32bit mmio: [0xd9000000-0xd907ffff]
[    0.166412] pci 0000:01:00.0: reg 30 32bit mmio: [0x000000-0x01ffff]
[    0.166494] pci 0000:00:01.0: bridge 32bit mmio: [0xd0000000-0xd1ffffff]
[    0.166504] pci 0000:00:01.0: bridge 32bit mmio pref: [0xd9000000-0xe8ffffff]
[    0.166575] pci 0000:02:08.0: reg 10 32bit mmio: [0xd2000000-0xd2000fff]
[    0.166588] pci 0000:02:08.0: reg 14 io port: [0x2000-0x203f]
[    0.166644] pci 0000:02:08.0: supports D1 D2
[    0.166650] pci 0000:02:08.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.166659] pci 0000:02:08.0: PME# disabled
[    0.166761] pci 0000:02:0d.0: supports D1 D2
[    0.166767] pci 0000:02:0d.0: PME# supported from D1 D2 D3hot D3cold
[    0.166776] pci 0000:02:0d.0: PME# disabled
[    0.166819] pci 0000:00:1e.0: transparent bridge
[    0.166829] pci 0000:00:1e.0: bridge io port: [0x2000-0x2fff]
[    0.166839] pci 0000:00:1e.0: bridge 32bit mmio: [0xd2000000-0xd20fffff]
[    0.166849] pci 0000:00:1e.0: bridge 32bit mmio pref: [0xec000000-0xf3ffffff]
[    0.166925] pci 0000:03:08.0: reg 10 32bit mmio: [0xec000000-0xefffffff]
[    0.167052] pci 0000:03:09.0: reg 10 32bit mmio: [0xf0000000-0xf3ffffff]
[    0.167184] pci 0000:02:0d.0: bridge 32bit mmio pref: [0xec000000-0xf3ffffff]
[    0.167214] pci_bus 0000:00: on NUMA node 0
[    0.167226] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.167397] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    0.167497] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.SLOT._PRT]
[    0.201127] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[    0.201322] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[    0.201507] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[    0.201693] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[    0.201889] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[    0.202084] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[    0.202281] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[    0.202479] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 *10 11 12 14 15)
[    0.202977] SCSI subsystem initialized
[    0.203171] libata version 3.00 loaded.
[    0.203382] usbcore: registered new interface driver usbfs
[    0.203441] usbcore: registered new interface driver hub
[    0.203509] usbcore: registered new device driver usb
[    0.203858] ACPI: WMI: Mapper loaded
[    0.203866] PCI: Using ACPI for IRQ routing
[    0.204213] Bluetooth: Core ver 2.15
[    0.204339] NET: Registered protocol family 31
[    0.204344] Bluetooth: HCI device and connection manager initialized
[    0.204353] Bluetooth: HCI socket layer initialized
[    0.204359] NetLabel: Initializing
[    0.204364] NetLabel:  domain hash size = 128
[    0.204368] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.204402] NetLabel:  unlabeled traffic allowed by default
[    0.208733] pnp: PnP ACPI init
[    0.208798] ACPI: bus type pnp registered
[    0.268144] pnp: PnP ACPI: found 15 devices
[    0.268156] ACPI: ACPI bus type pnp unregistered
[    0.268165] PnPBIOS: Disabled by ACPI PNP
[    0.268214] system 00:01: ioport range 0x4d0-0x4d1 has been reserved
[    0.268224] system 00:01: ioport range 0xfe00-0xfe00 has been reserved
[    0.268232] system 00:01: ioport range 0x800-0x84f has been reserved
[    0.268241] system 00:01: ioport range 0x1000-0x107f has been reserved
[    0.268249] system 00:01: ioport range 0x1180-0x11bf has been reserved
[    0.268261] system 00:01: iomem range 0xfec00000-0xfec000ff could not be reserved
[    0.303210] AppArmor: AppArmor Filesystem Enabled
[    0.303276] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.303282] pci 0000:00:01.0:   IO window: disabled
[    0.303293] pci 0000:00:01.0:   MEM window: 0xd0000000-0xd1ffffff
[    0.303302] pci 0000:00:01.0:   PREFETCH window: 0xd9000000-0xe8ffffff
[    0.303313] pci 0000:02:0d.0: PCI bridge, secondary bus 0000:03
[    0.303318] pci 0000:02:0d.0:   IO window: disabled
[    0.303328] pci 0000:02:0d.0:   MEM window: disabled
[    0.303337] pci 0000:02:0d.0:   PREFETCH window: 0xec000000-0xf3ffffff
[    0.303347] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:02
[    0.303355] pci 0000:00:1e.0:   IO window: 0x2000-0x2fff
[    0.303366] pci 0000:00:1e.0:   MEM window: 0xd2000000-0xd20fffff
[    0.303376] pci 0000:00:1e.0:   PREFETCH window: 0xec000000-0xf3ffffff
[    0.303406] pci 0000:00:1e.0: setting latency timer to 64
[    0.303427] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.303435] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.303443] pci_bus 0000:01: resource 1 mem: [0xd0000000-0xd1ffffff]
[    0.303451] pci_bus 0000:01: resource 2 pref mem [0xd9000000-0xe8ffffff]
[    0.303459] pci_bus 0000:02: resource 0 io:  [0x2000-0x2fff]
[    0.303466] pci_bus 0000:02: resource 1 mem: [0xd2000000-0xd20fffff]
[    0.303474] pci_bus 0000:02: resource 2 pref mem [0xec000000-0xf3ffffff]
[    0.303481] pci_bus 0000:02: resource 3 io:  [0x00-0xffff]
[    0.303488] pci_bus 0000:02: resource 4 mem: [0x000000-0xffffffff]
[    0.303496] pci_bus 0000:03: resource 2 pref mem [0xec000000-0xf3ffffff]
[    0.303589] NET: Registered protocol family 2
[    0.303802] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    0.304420] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    0.304607] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[    0.304822] TCP: Hash tables configured (established 16384 bind 16384)
[    0.304830] TCP reno registered
[    0.305170] NET: Registered protocol family 1
[    0.305350] Trying to unpack rootfs image as initramfs...
[    0.744696] Freeing initrd memory: 7464k freed
[    0.765855] Simple Boot Flag at 0x72 set to 0x1
[    0.766041] cpufreq-nforce2: No nForce2 chipset.
[    0.766109] Scanning for low memory corruption every 60 seconds
[    0.766419] audit: initializing netlink socket (disabled)
[    0.766468] type=2000 audit(1263764575.763:1): initialized
[    0.780863] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.783992] VFS: Disk quotas dquot_6.5.2
[    0.784154] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.785520] fuse init (API version 7.12)
[    0.785746] msgmni has been set to 992
[    0.786334] alg: No test for stdrng (krng)
[    0.786389] io scheduler noop registered
[    0.786395] io scheduler anticipatory registered
[    0.786401] io scheduler deadline registered
[    0.786554] io scheduler cfq registered (default)
[    0.786653] pci 0000:01:00.0: Boot video device
[    0.786689] pci 0000:02:08.0: Firmware left e100 interrupts enabled; disabling
[    0.786938] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.786996] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.787271] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    0.787283] ACPI: Power Button [PWRF]
[    0.787404] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0A03:00/PNP0C0C:00/input/input1
[    0.787411] ACPI: Power Button [PWRB]
[    0.787812] processor LNXCPU:00: registered as cooling_device0
[    0.787822] ACPI: Processor [CPU0] (supports 8 throttling states)
[    0.805132] Switched to high resolution mode on CPU 0
[    0.822680] thermal LNXTHERM:01: registered as thermal_zone0
[    0.822711] ACPI: Thermal Zone [THM0] (22 C)
[    0.822877] isapnp: Scanning for PnP cards...
[    1.177242] isapnp: No Plug & Play device found
[    1.180105] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    1.180291] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.180444] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    1.181117] 00:0c: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.181325] 00:0d: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    1.183570] brd: module loaded
[    1.184678] loop: module loaded
[    1.184921] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    1.185209] ata_piix 0000:00:1f.1: version 2.13
[    1.185348] ata_piix 0000:00:1f.1: setting latency timer to 64
[    1.185600] scsi0 : ata_piix
[    1.185878] scsi1 : ata_piix
[    1.187911] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1800 irq 14
[    1.187920] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1808 irq 15
[    1.190343] Fixed MDIO Bus: probed
[    1.190435] PPP generic driver version 2.4.2
[    1.190741] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.190803] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.190837] uhci_hcd: USB Universal Host Controller Interface driver
[    1.190964]   alloc irq_desc for 19 on node -1
[    1.190970]   alloc kstat_irqs on node -1
[    1.190989] uhci_hcd 0000:00:1f.2: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    1.191009] uhci_hcd 0000:00:1f.2: setting latency timer to 64
[    1.191018] uhci_hcd 0000:00:1f.2: UHCI Host Controller
[    1.191197] uhci_hcd 0000:00:1f.2: new USB bus registered, assigned bus number 1
[    1.191261] uhci_hcd 0000:00:1f.2: irq 19, io base 0x00001820
[    1.191499] usb usb1: configuration #1 chosen from 1 choice
[    1.191579] hub 1-0:1.0: USB hub found
[    1.191615] hub 1-0:1.0: 2 ports detected
[    1.191751]   alloc irq_desc for 23 on node -1
[    1.191757]   alloc kstat_irqs on node -1
[    1.191775] uhci_hcd 0000:00:1f.4: PCI INT C -> GSI 23 (level, low) -> IRQ 23
[    1.191797] uhci_hcd 0000:00:1f.4: setting latency timer to 64
[    1.191806] uhci_hcd 0000:00:1f.4: UHCI Host Controller
[    1.191932] uhci_hcd 0000:00:1f.4: new USB bus registered, assigned bus number 2
[    1.192000] uhci_hcd 0000:00:1f.4: irq 23, io base 0x00001840
[    1.192287] usb usb2: configuration #1 chosen from 1 choice
[    1.192385] hub 2-0:1.0: USB hub found
[    1.192407] hub 2-0:1.0: 2 ports detected
[    1.192662] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PSM] at 0x60,0x64 irq 1,12
[    1.352604] ata2.00: ATAPI: CD-RW   CDR-2440MB, 5SGC, max UDMA/33
[    1.360591] ata2.00: configured for UDMA/33
[    1.360685] ata1.00: ATA-7: HDS728080PLAT20, PF2OA21B, max UDMA/133
[    1.360693] ata1.00: 160836480 sectors, multi 16: LBA48 
[    1.384406] ata1.00: configured for UDMA/100
[    1.384685] scsi 0:0:0:0: Direct-Access     ATA      HDS728080PLAT20  PF2O PQ: 0 ANSI: 5
[    1.385025] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.385162] sd 0:0:0:0: [sda] 160836480 512-byte logical blocks: (82.3 GB/76.6 GiB)
[    1.385271] sd 0:0:0:0: [sda] Write Protect is off
[    1.385278] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.385332] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.385657]  sda:
[    1.386284] scsi 1:0:0:0: CD-ROM            CD-RW    CDR-2440MB       5SGC PQ: 0 ANSI: 5
[    1.388440] sr0: scsi3-mmc drive: 48x/40x writer cd/rw xa/form2 cdda tray
[    1.388450] Uniform CD-ROM driver Revision: 3.20
[    1.388700] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.388841] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.396983]  sda1 sda2 < sda5 >
[    1.414472] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.444225] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.444447] mice: PS/2 mouse device common for all mice
[    1.444668] rtc_cmos 00:04: RTC can wake from S4
[    1.444777] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    1.444818] rtc0: alarms up to one month, y3k, 114 bytes nvram
[    1.445102] device-mapper: uevent: version 1.0.3
[    1.445413] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
[    1.445659] device-mapper: multipath: version 1.1.0 loaded
[    1.445670] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.446034] EISA: Probing bus 0 at eisa.0
[    1.446050] Cannot allocate resource for EISA slot 1
[    1.446058] Cannot allocate resource for EISA slot 2
[    1.446090] EISA: Detected 0 cards.
[    1.446240] cpuidle: using governor ladder
[    1.446247] cpuidle: using governor menu
[    1.447426] TCP cubic registered
[    1.447713] NET: Registered protocol family 10
[    1.448687] lo: Disabled Privacy Extensions
[    1.449314] NET: Registered protocol family 17
[    1.449386] Bluetooth: L2CAP ver 2.13
[    1.449391] Bluetooth: L2CAP socket layer initialized
[    1.449399] Bluetooth: SCO (Voice Link) ver 0.6
[    1.449404] Bluetooth: SCO socket layer initialized
[    1.449554] Bluetooth: RFCOMM TTY layer initialized
[    1.449561] Bluetooth: RFCOMM socket layer initialized
[    1.449566] Bluetooth: RFCOMM ver 1.11
[    1.449660] Using IPI No-Shortcut mode
[    1.449892] PM: Resume from disk failed.
[    1.449930] registered taskstats version 1
[    1.450175]   Magic number: 10:159:753
[    1.450338] rtc_cmos 00:04: setting system clock to 2010-01-17 21:42:56 UTC (1263764576)
[    1.450346] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.450351] EDD information not available.
[    1.450517] Freeing unused kernel memory: 540k freed
[    1.452085] Write protecting the kernel text: 4568k
[    1.452154] Write protecting the kernel read-only data: 1836k
[    1.854974] Linux agpgart interface v0.103
[    1.937164] agpgart-intel 0000:00:00.0: Intel 845G Chipset
[    1.954246] agpgart-intel 0000:00:00.0: AGP aperture is 64M @ 0xd4000000
[    1.994434] e100: Intel(R) PRO/100 Network Driver, 3.5.24-k2-NAPI
[    1.994443] e100: Copyright(c) 1999-2006 Intel Corporation
[    1.994551]   alloc irq_desc for 20 on node -1
[    1.994557]   alloc kstat_irqs on node -1
[    1.994575] e100 0000:02:08.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    2.018895] e100 0000:02:08.0: PME# disabled
[    2.077482] FDC 0 is a National Semiconductor PC87306
[    2.229421] e100: eth0: e100_probe: addr 0xd2000000, irq 20, MAC addr 00:02:55:5b:a7:b6
[    3.641644] PM: Starting manual resume from disk
[    3.641658] PM: Resume from partition 8:5
[    3.641663] PM: Checking hibernation image.
[    3.641988] PM: Resume from disk failed.
[    3.666565] EXT4-fs (sda1): barriers enabled
[    3.684197] kjournald2 starting: pid 300, dev sda1:8, commit interval 5 seconds
[    3.684256] EXT4-fs (sda1): delayed allocation enabled
[    3.684264] EXT4-fs: file extents enabled
[    3.703122] EXT4-fs: mballoc enabled
[    3.703184] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    4.355780] type=1505 audit(1263764579.403:2): operation="profile_load" pid=323 name=/sbin/dhclient3
[    4.356850] type=1505 audit(1263764579.405:3): operation="profile_load" pid=323 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    4.357396] type=1505 audit(1263764579.405:4): operation="profile_load" pid=323 name=/usr/lib/connman/scripts/dhclient-script
[    4.402861] type=1505 audit(1263764579.449:5): operation="profile_load" pid=324 name=/usr/bin/evince
[    4.419504] type=1505 audit(1263764579.465:6): operation="profile_load" pid=324 name=/usr/bin/evince-previewer
[    4.429752] type=1505 audit(1263764579.477:7): operation="profile_load" pid=324 name=/usr/bin/evince-thumbnailer
[    4.462679] type=1505 audit(1263764579.509:8): operation="profile_load" pid=326 name=/usr/sbin/mysqld
[    4.468257] type=1505 audit(1263764579.517:9): operation="profile_load" pid=327 name=/usr/sbin/ntpd
[    4.473639] type=1505 audit(1263764579.521:10): operation="profile_load" pid=328 name=/usr/sbin/tcpdump
[    5.225264] Adding 1485972k swap on /dev/sda5.  Priority:-1 extents:1 across:1485972k 
[    5.458684] EXT4-fs (sda1): internal journal on sda1:8
[    6.089749] udev: starting version 147
[    7.182555] intel_rng: Firmware space is locked read-only. If you can't or
[    7.182560] intel_rng: don't want to disable this in firmware setup, and if
[    7.182563] intel_rng: you are certain that your system has a functional
[    7.182566] intel_rng: RNG, try using the 'no_fwh_detect' option.
[    7.279335] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    7.707740] Linux video capture interface: v2.00
[    8.038162] lp: driver loaded but no devices found
[    8.069101] parport_pc 00:0e: reported by Plug and Play ACPI
[    8.069193] parport0: PC-style at 0x378 (0x778), irq 7, dma 1 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[    8.149093] ppdev: user-space parallel port driver
[    8.167781] lp0: using parport0 (interrupt-driven).
[    8.273581] type=1505 audit(1263764583.321:11): operation="profile_replace" pid=596 name=/sbin/dhclient3
[    8.274596] type=1505 audit(1263764583.321:12): operation="profile_replace" pid=596 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    8.275153] type=1505 audit(1263764583.321:13): operation="profile_replace" pid=596 name=/usr/lib/connman/scripts/dhclient-script
[    8.291464] type=1505 audit(1263764583.337:14): operation="profile_replace" pid=597 name=/usr/bin/evince
[    8.326450] type=1505 audit(1263764583.373:15): operation="profile_replace" pid=597 name=/usr/bin/evince-previewer
[    8.355051] type=1505 audit(1263764583.401:16): operation="profile_replace" pid=597 name=/usr/bin/evince-thumbnailer
[    8.373434] type=1505 audit(1263764583.421:17): operation="profile_replace" pid=602 name=/usr/sbin/mysqld
[    8.378721] type=1505 audit(1263764583.425:18): operation="profile_replace" pid=603 name=/usr/sbin/ntpd
[    8.383962] type=1505 audit(1263764583.429:19): operation="profile_replace" pid=604 name=/usr/sbin/tcpdump
[    8.543057] ivtv: Start initialization, version 1.4.1
[    8.543433] ivtv0: Initializing card 0
[    8.543444] ivtv0: Autodetected Hauppauge card (cx23416 based)
[    8.543649]   alloc irq_desc for 21 on node -1
[    8.543657]   alloc kstat_irqs on node -1
[    8.543675] ivtv 0000:03:08.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    8.543696] ivtv0: Unreasonably low latency timer, setting to 64 (was 32)
[    8.627058] tveeprom 0-0050: Hauppauge model 23559, rev D591, serial# 2989618
[    8.627070] tveeprom 0-0050: tuner model is Philips FQ1216AME MK4 (idx 91, type 56)
[    8.627079] tveeprom 0-0050: TV standards PAL(B/G) PAL(I) SECAM(L/L') PAL(D/D1/K) (eeprom 0x74)
[    8.627088] tveeprom 0-0050: second tuner model is Philips TEA5768HL FM Radio (idx 101, type 62)
[    8.627097] tveeprom 0-0050: audio processor is CX25843 (idx 37)
[    8.627105] tveeprom 0-0050: decoder processor is CX25843 (idx 30)
[    8.627112] tveeprom 0-0050: has radio
[    8.627120] ivtv0: Autodetected WinTV PVR 500 (unit #1)
[    8.934108] nvidia: module license 'NVIDIA' taints kernel.
[    8.934119] Disabling lock debugging due to kernel taint
[    9.217503] cx25840 0-0044: cx25843-23 found @ 0x88 (ivtv i2c driver #0)
[    9.253459]   alloc irq_desc for 16 on node -1
[    9.253469]   alloc kstat_irqs on node -1
[    9.253488] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    9.254307] NVRM: loading NVIDIA Linux x86 Kernel Module  96.43.13  Thu Jun 25 18:42:21 PDT 2009
[    9.535374] tuner 0-0060: chip found @ 0xc0 (ivtv i2c driver #0)
[    9.535580] tea5767 0-0060: type set to Philips TEA5767HN FM Radio
[    9.607656] ip_tables: (C) 2000-2006 Netfilter Core Team
[    9.967513] tuner 0-0043: chip found @ 0x86 (ivtv i2c driver #0)
[   10.032151]   alloc irq_desc for 17 on node -1
[   10.032161]   alloc kstat_irqs on node -1
[   10.032179] Intel ICH 0000:00:1f.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   10.032218] Intel ICH 0000:00:1f.5: setting latency timer to 64
[   10.088157] tda9887 0-0043: creating new instance
[   10.088167] tda9887 0-0043: tda988[5/6/7] found
[   10.095600] tuner 0-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[   10.143352] wm8775 0-001b: chip found @ 0x36 (ivtv i2c driver #0)
[   10.416495] tuner-simple 0-0061: creating new instance
[   10.416507] tuner-simple 0-0061: type set to 56 (Philips PAL/SECAM multi (FQ1216AME MK4))
[   10.418628] IRQ 21/ivtv0: IRQF_DISABLED is not guaranteed on shared IRQs
[   10.419628] ivtv0: Registered device video0 for encoder MPG (4096 kB)
[   10.419857] ivtv0: Registered device video32 for encoder YUV (2048 kB)
[   10.423198] ivtv0: Registered device vbi0 for encoder VBI (1024 kB)
[   10.423386] ivtv0: Registered device video24 for encoder PCM (320 kB)
[   10.423470] ivtv0: Registered device radio0 for encoder radio
[   10.423478] ivtv0: Initialized card: WinTV PVR 500 (unit #1)
[   10.423804] ivtv1: Initializing card 1
[   10.423814] ivtv1: Autodetected Hauppauge card (cx23416 based)
[   10.424089]   alloc irq_desc for 22 on node -1
[   10.424096]   alloc kstat_irqs on node -1
[   10.424117] ivtv 0000:03:09.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   10.424138] ivtv1: Unreasonably low latency timer, setting to 64 (was 32)
[   10.508756] tveeprom 1-0050: Hauppauge model 23559, rev D591, serial# 2989618
[   10.508768] tveeprom 1-0050: tuner model is Philips FQ1216AME MK4 (idx 91, type 56)
[   10.508778] tveeprom 1-0050: TV standards PAL(B/G) PAL(I) SECAM(L/L') PAL(D/D1/K) (eeprom 0x74)
[   10.508787] tveeprom 1-0050: second tuner model is Philips TEA5768HL FM Radio (idx 101, type 62)
[   10.508796] tveeprom 1-0050: audio processor is CX25843 (idx 37)
[   10.508806] tveeprom 1-0050: decoder processor is CX25843 (idx 30)
[   10.508813] tveeprom 1-0050: has radio
[   10.508822] ivtv1: Correcting tveeprom data: no radio present on second unit
[   10.508828] ivtv1: Autodetected WinTV PVR 500 (unit #2)
[   10.523642] cx25840 1-0044: cx25843-23 found @ 0x88 (ivtv i2c driver #1)
[   10.546274] tuner 1-0043: chip found @ 0x86 (ivtv i2c driver #1)
[   10.546481] tda9887 1-0043: creating new instance
[   10.546488] tda9887 1-0043: tda988[5/6/7] found
[   10.566970] tuner 1-0061: chip found @ 0xc2 (ivtv i2c driver #1)
[   10.571568] wm8775 1-001b: chip found @ 0x36 (ivtv i2c driver #1)
[   10.587406] tuner-simple 1-0061: creating new instance
[   10.587419] tuner-simple 1-0061: type set to 56 (Philips PAL/SECAM multi (FQ1216AME MK4))
[   10.589705] IRQ 22/ivtv1: IRQF_DISABLED is not guaranteed on shared IRQs
[   10.615177] ivtv1: Registered device video1 for encoder MPG (4096 kB)
[   10.615370] ivtv1: Registered device video33 for encoder YUV (2048 kB)
[   10.615435] ivtv1: Registered device vbi1 for encoder VBI (1024 kB)
[   10.615494] ivtv1: Registered device video25 for encoder PCM (320 kB)
[   10.615501] ivtv1: Initialized card: WinTV PVR 500 (unit #2)
[   10.615563] ivtv: End initialization
[   10.652107] intel8x0_measure_ac97_clock: measured 53395 usecs (2990 samples)
[   10.652117] intel8x0: clocking to 41145
[   11.292031] ivtv 0000:03:08.0: firmware: requesting v4l-cx2341x-enc.fw
[   11.296530] ivtv 0000:03:09.0: firmware: requesting v4l-cx2341x-enc.fw
[   12.362825] ivtv1: Loaded v4l-cx2341x-enc.fw firmware (376836 bytes)
[   12.374267] ivtv0: Loaded v4l-cx2341x-enc.fw firmware (376836 bytes)
[   12.560195] ivtv1: Encoder revision: 0x02060039
[   12.572694] ivtv0: Encoder revision: 0x02060039
[   12.607265] cx25840 1-0044: firmware: requesting v4l-cx25840.fw
[   12.619982] cx25840 0-0044: firmware: requesting v4l-cx25840.fw
[   13.777848] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   15.733394] lirc_dev: IR Remote Control driver registered, major 61 
[   15.816213] e100: eth0 NIC Link is Up 100 Mbps Full Duplex
[   15.818257] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   15.988225] lirc_mceusb: Windows Media Center Edition USB IR Transceiver driver for LIRC 1.90
[   15.988234] lirc_mceusb: Daniel Melander <lirc@rajidae.se>, Martin Blatter <martin_a_blatter@yahoo.com>, Dan Conti <dconti@acm.wwu.edu>
[   15.988302] usbcore: registered new interface driver lirc_mceusb
[   18.873732] type=1503 audit(1263764593.921:20): operation="open" pid=1037 parent=1036 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   20.180609] type=1503 audit(1263764595.880:21): operation="open" pid=1136 parent=1135 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   21.800374] type=1503 audit(1263764597.500:22): operation="open" pid=1242 parent=1241 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   22.203376] type=1503 audit(1263764597.900:23): operation="open" pid=1277 parent=1157 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   22.243683] cx25840 0-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
[   22.278592] cx25840 1-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
[   22.961300] type=1503 audit(1263764598.660:24): operation="open" pid=1294 parent=1293 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   24.038495] type=1503 audit(1263764599.736:25): operation="open" pid=1331 parent=1330 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   25.145557] type=1503 audit(1263764600.844:26): operation="open" pid=1352 parent=1351 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   25.257712] type=1503 audit(1263764600.956:27): operation="open" pid=1363 parent=1362 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   26.239672] agpgart-intel 0000:00:00.0: AGP 2.0 bridge
[   26.239705] agpgart-intel 0000:00:00.0: putting AGP V2 device into 4x mode
[   26.239741] nvidia 0000:01:00.0: putting AGP V2 device into 4x mode
[   26.364060] eth0: no IPv6 routers present
[  107.729225] usbcore: registered new interface driver em28xx
[  107.729236] em28xx driver loaded
[  124.472068] usb 2-1: new full speed USB device using uhci_hcd and address 2
[  124.639625] usb 2-1: configuration #1 chosen from 1 choice


---

### Post by jis on 2010-02-23
Does this help? [http://vanvalkinburgh.org/blog/2009](http://vanvalkinburgh.org/blog/2009)

---

### Post by rickcn on 2010-03-16
same problem here.... cannot get the card to be detected...

I also noticed that the emm drivers cannot load. Running Ubuntu 2.6.31-20-generic

---

### Post by jis on 2010-03-16
What are emm drivers?

---

### Post by bmhoff on 2011-08-10
going to add my self to this list, wold love if someone had a fix for this?

My em28xx drivers load

[ 3039.687084] usbcore: registered new interface driver em28xx
[ 3039.687136] em28xx driver loaded
[ 3039.688193] lirc_dev: IR Remote Control driver registered, major 249 
[ 3039.689135] IR LIRC bridge handler initialized



root@bt:~# lsusb
Bus 002 Device 007: ID 0fd9:0018  
Bus 002 Device 003: ID 0e0f:0002 VMware, Inc. Virtual USB Hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

