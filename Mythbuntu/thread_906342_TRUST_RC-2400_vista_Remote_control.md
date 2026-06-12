---
title: "TRUST RC-2400 vista Remote control"
date: 2008-08-31
forum: Mythbuntu
---

### Post by bggr on 2008-08-31
Hi,

I'm using mythbuntu 8.04.1 there is any way to work my remote control "TRUST RC-2400 Vista Remote control" with my mythbuntu???

Thanks.

---

### Post by DemonBob on 2008-08-31
Might be. 

Give me the outputs of (with the remote plugged in)

```
lsusb -v
```
```
ls -la /dev/input/by-id/
```
```
dmesg
```

Also i am right in the path of Hurricane Gustav, so i might be unable to reply.

---

### Post by bggr on 2008-09-01
I' m hope that this can help......

**lsusb -v**

Bus 004 Device 003: ID 147a:e017 Formosa Industrial Computing, Inc.
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0
  bDeviceProtocol         0
  bMaxPacketSize0         8
  idVendor           0x147a Formosa Industrial Computing, Inc.
  idProduct          0xe017
  bcdDevice            1.30
  iManufacturer           1 Formosa21
  iProduct                2 SnowflakeEmulation
  iSerial                 3 C0015499
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval              10
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval              10
can't get device qualifier: Timer expired
can't get debug descriptor: Timer expired
cannot read device status, Timer expired (62)

Bus 004 Device 002: ID 062a:0107 Creative Labs
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0
  bDeviceProtocol         0
  bMaxPacketSize0         8
  idVendor           0x062a Creative Labs
  idProduct          0x0107
  bcdDevice            1.00
  iManufacturer           1 MOSART Semi.
  iProduct                2 Input Device
  iSerial                 0
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           59
    bNumInterfaces          2
    bConfigurationValue     1
    iConfiguration          0
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      1 Boot Interface Subclass
      bInterfaceProtocol      1 Keyboard
      iInterface              0
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.10
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength      65
         Report Descriptors:
           ** UNAVAILABLE **
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval              10
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      1 Boot Interface Subclass
      bInterfaceProtocol      2 Mouse
      iInterface              0
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.10
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength     119
         Report Descriptors:
           ** UNAVAILABLE **
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0006  1x 6 bytes
        bInterval              10
Device Status:     0x0000
  (Bus Powered)

Bus 004 Device 001: ID 0000:0000
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x0000
  idProduct          0x0000
  bcdDevice            2.06
  iManufacturer           3 Linux 2.6.24-19-generic ohci_hcd
  iProduct                2 OHCI Host Controller
  iSerial                 1 0000:00:04.0
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             6
  wHubCharacteristic 0x0012
    No power switching (usb 1.0)
    No overcurrent protection
  bPwrOn2PwrGood        1 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x00
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0303 lowspeed power enable connect
   Port 3: 0000.0303 lowspeed power enable connect
   Port 4: 0000.0100 power
   Port 5: 0000.0100 power
   Port 6: 0000.0100 power
Device Status:     0x0003
  Self Powered
  Remote Wakeup Enabled

Bus 003 Device 001: ID 0000:0000
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x0000
  idProduct          0x0000
  bcdDevice            2.06
  iManufacturer           3 Linux 2.6.24-19-generic ohci_hcd
  iProduct                2 OHCI Host Controller
  iSerial                 1 0000:00:02.0
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             6
  wHubCharacteristic 0x0012
    No power switching (usb 1.0)
    No overcurrent protection
  bPwrOn2PwrGood        1 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x00
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0100 power
   Port 3: 0000.0100 power
   Port 4: 0000.0100 power
   Port 5: 0000.0100 power
   Port 6: 0000.0100 power
Device Status:     0x0003
  Self Powered
  Remote Wakeup Enabled

Bus 001 Device 001: ID 0000:0000
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         1 Single TT
  bMaxPacketSize0        64
  idVendor           0x0000
  idProduct          0x0000
  bcdDevice            2.06
  iManufacturer           3 Linux 2.6.24-19-generic ehci_hcd
  iProduct                2 EHCI Host Controller
  iSerial                 1 0000:00:02.1
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0004  1x 4 bytes
        bInterval              12
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             6
  wHubCharacteristic 0x000a
    No power switching (usb 1.0)
    Per-port overcurrent protection
    TT think time 8 FS bits
  bPwrOn2PwrGood       10 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x00
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0100 power
   Port 3: 0000.0100 power
   Port 4: 0000.0100 power
   Port 5: 0000.0100 power
   Port 6: 0000.0100 power
Device Status:     0x0003
  Self Powered
  Remote Wakeup Enabled

Bus 002 Device 001: ID 0000:0000
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         1 Single TT
  bMaxPacketSize0        64
  idVendor           0x0000
  idProduct          0x0000
  bcdDevice            2.06
  iManufacturer           3 Linux 2.6.24-19-generic ehci_hcd
  iProduct                2 EHCI Host Controller


  iSerial                 1 0000:00:04.1
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0004  1x 4 bytes
        bInterval              12
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             6
  wHubCharacteristic 0x000a
    No power switching (usb 1.0)
    Per-port overcurrent protection
    TT think time 8 FS bits
  bPwrOn2PwrGood       10 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x00
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0100 power
   Port 3: 0000.0100 power
   Port 4: 0000.0100 power
   Port 5: 0000.0100 power
   Port 6: 0000.0100 power
Device Status:     0x0003
  Self Powered
  Remote Wakeup Enabled


**ls -la /dev/input/by-id/**
total 0
drwxr-xr-x 2 root root 100 2008-09-01 21:23 .
drwxr-xr-x 4 root root 320 2008-09-01 21:23 ..
lrwxrwxrwx 1 root root   9 2008-09-01 21:23 usb-MOSART_Semi._Input_Device-event-kbd -> ../event2
lrwxrwxrwx 1 root root   9 2008-09-01 21:23 usb-MOSART_Semi._Input_Device-event-mouse -> ../event3
lrwxrwxrwx 1 root root   9 2008-09-01 21:23 usb-MOSART_Semi._Input_Device-mouse -> ../mouse1


 **dmesg**
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-19-generic (buildd@king) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed Aug 20 17:53:40 UTC 2008 (Ubuntu 2.6.24-19.41-generic)
[    0.000000] Command line: root=UUID=fb86acf9-9c2a-4a6d-8bde-ace9b0d45363 ro quiet splash locale=el_GR
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000037fa0000 (usable)
[    0.000000]  BIOS-e820: 0000000037fa0000 - 0000000037fae000 (ACPI data)
[    0.000000]  BIOS-e820: 0000000037fae000 - 0000000037fe0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 0000000037fe0000 - 0000000037fee000 (reserved)
[    0.000000]  BIOS-e820: 0000000037ff0000 - 0000000038000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fef00000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 229280) 1 entries of 3200 used
[    0.000000] end_pfn_map = 1048576
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP signature @ 0xFFFF8100000FB740 checksum 0
[    0.000000] ACPI: RSDP 000FB740, 0014 (r0 ACPIAM)
[    0.000000] ACPI: RSDT 37FA0000, 0040 (r1 103107 RSDT0915 20071031 MSFT    97)
[    0.000000] ACPI: FACP 37FA0200, 0084 (r2 103107 FACP0915 20071031 MSFT    97)
[    0.000000] ACPI: DSDT 37FA0450, 7233 (r1  A0878 A0878000        0 INTL 20051117)
[    0.000000] ACPI: FACS 37FAE000, 0040
[    0.000000] ACPI: APIC 37FA0390, 0080 (r1 103107 APIC0915 20071031 MSFT    97)
[    0.000000] ACPI: MCFG 37FA0410, 003C (r1 103107 OEMMCFG  20071031 MSFT    97)
[    0.000000] ACPI: OEMB 37FAE040, 0071 (r1 103107 OEMB0915 20071031 MSFT    97)
[    0.000000] ACPI: HPET 37FA7690, 0038 (r1 103107 OEMHPET0 20071031 MSFT    97)
[    0.000000] ACPI: NVHD 37FAE0C0, 0554 (r1 103107  NVHDCP  20071031 MSFT    97)
[    0.000000] ACPI: SSDT 37FA76D0, 02CC (r1 A_M_I_ POWERNOW        1 AMD     1)
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] CPU has 2 num_cores
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000037fa0000
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 229280) 1 entries of 3200 used
[    0.000000] Bootmem setup node 0 0000000000000000-0000000037fa0000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   DMA32        4096 ->  1048576
[    0.000000]   Normal    1048576 ->  1048576
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0:        0 ->      159
[    0.000000]     0:      256 ->   229280
[    0.000000] On node 0 totalpages: 229183
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 1219 pages reserved
[    0.000000]   DMA zone: 2724 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 3078 pages used for memmap
[    0.000000]   DMA32 zone: 222106 pages, LIFO batch:31
[    0.000000]   Normal zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x508
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] Processor #1
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Setting APIC routing to flat
[    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e4000
[    0.000000] swsusp: Registered nosave memory region: 00000000000e4000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 38000000:c6c00000)
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] PERCPU: Allocating 34656 bytes of per cpu data
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Totalpages: 224830
[    0.000000] Policy zone: DMA32
[    0.000000] Kernel command line: root=UUID=fb86acf9-9c2a-4a6d-8bde-ace9b0d45363 ro quiet splash locale=el_GR
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] hpet clockevent registered
[    0.000000] TSC calibrated against HPET
[   15.005830] Marking TSC unstable due to TSCs unsynchronized
[   15.005831] time.c: Detected 2700.251 MHz processor.
[   15.009004] Console: colour VGA+ 80x25
[   15.009006] console [tty0] enabled
[   15.009021] Checking aperture...
[   15.009023] CPU 0: aperture @ 2248000000 size 32 MB
[   15.009024] Aperture too small (32 MB)
[   15.015007] No AGP bridge found
[   15.024120] Memory: 891080k/917120k available (2489k kernel code, 25652k reserved, 1318k data, 320k init)
[   15.024155] SLUB: Genslabs=12, HWalign=64, Order=0-1, MinObjects=4, CPUs=4, Nodes=1
[   15.103756] Calibrating delay using timer specific routine.. 5405.66 BogoMIPS (lpj=10811328)
[   15.103782] Security Framework initialized
[   15.103789] SELinux:  Disabled at boot.
[   15.103801] AppArmor: AppArmor initialized
[   15.103804] Failure registering capabilities with primary security module.
[   15.103877] Dentry cache hash table entries: 131072 (order: 8, 1048576 bytes)
[   15.104522] Inode-cache hash table entries: 65536 (order: 7, 524288 bytes)
[   15.104861] Mount-cache hash table entries: 256
[   15.104977] Initializing cgroup subsys ns
[   15.104980] Initializing cgroup subsys cpuacct
[   15.104990] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   15.104991] CPU: L2 Cache: 512K (64 bytes/line)
[   15.104993] CPU 0/0 -> Node 0
[   15.104995] CPU: Physical Processor ID: 0
[   15.104996] CPU: Processor Core ID: 0
[   15.105016] SMP alternatives: switching to UP code
[   15.105500] Early unpacking initramfs... done
[   15.347619] ACPI: Core revision 20070126
[   15.347674] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   15.390669] Using local APIC timer interrupts.
[   15.427684] APIC timer calibration result 12501159
[   15.427686] Detected 12.501 MHz APIC timer.
[   15.427763] SMP alternatives: switching to SMP code
[   15.428156] Booting processor 1/2 APIC 0x1
[   15.438447] Initializing CPU#1
[   15.515860] Calibrating delay using timer specific routine.. 5400.51 BogoMIPS (lpj=10801027)
[   15.515866] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   15.515867] CPU: L2 Cache: 512K (64 bytes/line)
[   15.515869] CPU 1/1 -> Node 0
[   15.515870] CPU: Physical Processor ID: 0
[   15.515871] CPU: Processor Core ID: 1
[   15.515950] AMD Athlon(tm) 64 X2 Dual Core Processor 5200+ stepping 02
[   15.515744] Brought up 2 CPUs
[   15.515843] CPU0 attaching sched-domain:
[   15.515845]  domain 0: span 03
[   15.515847]   groups: 01 02
[   15.515849]   domain 1: span 03
[   15.515850]    groups: 03
[   15.515851] CPU1 attaching sched-domain:
[   15.515852]  domain 0: span 03
[   15.515853]   groups: 02 01
[   15.515855]   domain 1: span 03
[   15.515856]    groups: 03
[   15.516048] net_namespace: 120 bytes
[   15.516376] Time: 18:23:09  Date: 09/01/08
[   15.516408] NET: Registered protocol family 16
[   15.516562] ACPI: bus type pci registered
[   15.516618] PCI: Using configuration type 1
[   15.519647] ACPI: EC: Look up EC in DSDT
[   15.524852] ACPI: Interpreter enabled
[   15.524853] ACPI: (supports S0 S1 S3 S4 S5)
[   15.524867] ACPI: Using IOAPIC for interrupt routing
[   15.525125] Error attaching device data
[   15.525129] Error attaching device data
[   15.525132] Error attaching device data
[   15.525136] Error attaching device data
[   15.533201] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   15.533771] PCI: Transparent bridge - 0000:00:08.0
[   15.534110] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   15.534265] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[   15.534360] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR10._PRT]
[   15.534440] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR11._PRT]
[   15.546218] ACPI: PCI Interrupt Link [LNKA] (IRQs 16 17 18 19) *0, disabled.
[   15.546402] ACPI: PCI Interrupt Link [LNKB] (IRQs 16 17 18 19) *0, disabled.
[   15.546586] ACPI: PCI Interrupt Link [LNKC] (IRQs 16 17 18 19) *0, disabled.
[   15.546769] ACPI: PCI Interrupt Link [LNKD] (IRQs 16 17 18 19) *0, disabled.
[   15.546952] ACPI: PCI Interrupt Link [LNEA] (IRQs 16 17 18 19) *0, disabled.
[   15.547134] ACPI: PCI Interrupt Link [LNEB] (IRQs 16 17 18 19) *0, disabled.
[   15.547317] ACPI: PCI Interrupt Link [LNEC] (IRQs 16 17 18 19) *0, disabled.
[   15.547500] ACPI: PCI Interrupt Link [LNED] (IRQs 16 17 18 19) *0, disabled.
[   15.547719] ACPI: PCI Interrupt Link [LUB0] (IRQs 20 21 22 23) *11
[   15.547903] ACPI: PCI Interrupt Link [LUB2] (IRQs 20 21 22 23) *10
[   15.548087] ACPI: PCI Interrupt Link [LMAC] (IRQs 20 21 22 23) *10
[   15.548271] ACPI: PCI Interrupt Link [LAZA] (IRQs 20 21 22 23) *11
[   15.548457] ACPI: PCI Interrupt Link [SGRU] (IRQs 20 21 22 23) *11
[   15.548639] ACPI: PCI Interrupt Link [LSMB] (IRQs 20 21 22 23) *10
[   15.549117] ACPI: PCI Interrupt Link [LPMU] (IRQs 20 21 22 23) *0, disabled.
[   15.549299] ACPI: PCI Interrupt Link [LSA0] (IRQs 20 21 22 23) *15
[   15.549509] ACPI: PCI Interrupt Link [LATA] (IRQs 20 21 22 23) *0, disabled.
[   15.549691] ACPI: PCI Interrupt Link [UB11] (IRQs 20 21 22 23) *11
[   15.549872] ACPI: PCI Interrupt Link [UB12] (IRQs 20 21 22 23) *11
[   15.549985] ACPI Warning (tbutils-0217): Incorrect checksum in table [OEMB] -  BF, should be B2 [20070126]
[   15.549993] Linux Plug and Play Support v0.97 (c) Adam Belay
[   15.550015] pnp: PnP ACPI init
[   15.550022] ACPI: bus type pnp registered
[   15.555410] pnp: PnP ACPI: found 16 devices
[   15.555412] ACPI: ACPI bus type pnp unregistered
[   15.555592] PCI: Using ACPI for IRQ routing
[   15.555594] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   15.571612] NET: Registered protocol family 8
[   15.571613] NET: Registered protocol family 20
[   15.571680] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 31
[   15.571683] hpet0: 3 32-bit timers, 25000000 Hz
[   15.572727] AppArmor: AppArmor Filesystem Enabled
[   15.575605] Time: hpet clocksource has been installed.
[   15.575615] Switched to high resolution mode on CPU 0
[   15.575937] Switched to high resolution mode on CPU 1
[   15.583602] system 00:06: ioport range 0x4d0-0x4d1 has been reserved
[   15.583605] system 00:06: ioport range 0x800-0x80f has been reserved
[   15.583607] system 00:06: ioport range 0x500-0x57f has been reserved
[   15.583608] system 00:06: ioport range 0x580-0x5ff has been reserved
[   15.583610] system 00:06: ioport range 0x800-0x87f could not be reserved
[   15.583612] system 00:06: ioport range 0x880-0x8ff has been reserved
[   15.583614] system 00:06: ioport range 0xd00-0xd7f has been reserved
[   15.583615] system 00:06: ioport range 0xd80-0xdff has been reserved
[   15.583617] system 00:06: ioport range 0x900-0x97f has been reserved
[   15.583619] system 00:06: ioport range 0x980-0x9ff has been reserved
[   15.583621] system 00:06: ioport range 0x1100-0x117f has been reserved
[   15.583623] system 00:06: ioport range 0x1180-0x11ff has been reserved
[   15.583625] system 00:06: iomem range 0x0-0x0 could not be reserved
[   15.583627] system 00:06: iomem range 0xfefe0000-0xfefe01ff has been reserved
[   15.583629] system 00:06: iomem range 0xfefe1000-0xfefe1fff has been reserved
[   15.583631] system 00:06: iomem range 0xfee01000-0xfeefffff has been reserved
[   15.583636] system 00:09: iomem range 0xfec00000-0xfec00fff could not be reserved
[   15.583638] system 00:09: iomem range 0xfee00000-0xfee00fff could not be reserved
[   15.583643] system 00:0c: ioport range 0x230-0x23f has been reserved
[   15.583645] system 00:0c: ioport range 0x290-0x29f has been reserved
[   15.583647] system 00:0c: ioport range 0xa00-0xa0f has been reserved
[   15.583649] system 00:0c: ioport range 0xa10-0xa1f has been reserved
[   15.583656] system 00:0e: iomem range 0xe0000000-0xefffffff has been reserved
[   15.583660] system 00:0f: iomem range 0x0-0x9ffff could not be reserved
[   15.583662] system 00:0f: iomem range 0xc0000-0xcffff has been reserved
[   15.583663] system 00:0f: iomem range 0xe0000-0xfffff could not be reserved
[   15.583665] system 00:0f: iomem range 0x100000-0x37ffffff could not be reserved
[   15.583667] system 00:0f: iomem range 0xfec00000-0xffffffff could not be reserved
[   15.583976] PCI: Bridge: 0000:00:08.0
[   15.583977]   IO window: disabled.
[   15.583980]   MEM window: disabled.
[   15.583982]   PREFETCH window: disabled.
[   15.583984] PCI: Bridge: 0000:00:0b.0
[   15.583985]   IO window: disabled.
[   15.583986]   MEM window: disabled.
[   15.583987]   PREFETCH window: disabled.
[   15.583989] PCI: Bridge: 0000:00:0c.0
[   15.583990]   IO window: disabled.
[   15.583991]   MEM window: disabled.
[   15.583993]   PREFETCH window: disabled.
[   15.583994] PCI: Bridge: 0000:00:0d.0
[   15.583995]   IO window: disabled.
[   15.583997]   MEM window: disabled.
[   15.583998]   PREFETCH window: disabled.
[   15.583999] PCI: Bridge: 0000:00:0e.0
[   15.584000]   IO window: disabled.
[   15.584002]   MEM window: disabled.
[   15.584003]   PREFETCH window: disabled.
[   15.584005] PCI: Bridge: 0000:00:0f.0
[   15.584005]   IO window: disabled.
[   15.584007]   MEM window: disabled.
[   15.584008]   PREFETCH window: disabled.
[   15.584010] PCI: Bridge: 0000:00:10.0
[   15.584010]   IO window: disabled.
[   15.584012]   MEM window: disabled.
[   15.584013]   PREFETCH window: disabled.
[   15.584015] PCI: Bridge: 0000:00:11.0
[   15.584016]   IO window: disabled.
[   15.584017]   MEM window: disabled.
[   15.584018]   PREFETCH window: disabled.
[   15.584026] PCI: Setting latency timer of device 0000:00:08.0 to 64
[   15.584035] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[   15.584040] PCI: Setting latency timer of device 0000:00:0c.0 to 64
[   15.584044] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[   15.584048] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[   15.584052] PCI: Setting latency timer of device 0000:00:0f.0 to 64
[   15.584056] PCI: Setting latency timer of device 0000:00:10.0 to 64
[   15.584060] PCI: Setting latency timer of device 0000:00:11.0 to 64
[   15.584069] NET: Registered protocol family 2
[   15.619623] IP route cache hash table entries: 32768 (order: 6, 262144 bytes)
[   15.620015] TCP established hash table entries: 131072 (order: 9, 2097152bytes)
[   15.621456] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   15.622126] TCP: Hash tables configured (established 131072 bind 65536)
[   15.622129] TCP reno registered
[   15.631682] checking if image is initramfs... it is
[   16.174968] Freeing initrd memory: 7990k freed
[   16.181194] audit: initializing netlink socket (disabled)
[   16.181204] audit(1220293390.144:1): initialized
[   16.182702] VFS: Disk quotas dquot_6.5.1
[   16.182760] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   16.182867] io scheduler noop registered
[   16.182869] io scheduler anticipatory registered
[   16.182870] io scheduler deadline registered
[   16.182947] io scheduler cfq registered (default)
[   16.182975] pci 0000:00:00.0: Enabling HT MSI Mapping
[   16.231595] pci 0000:00:07.0: Enabling HT MSI Mapping
[   16.231610] pci 0000:00:08.0: Enabling HT MSI Mapping
[   16.231633] pci 0000:00:0a.0: Enabling HT MSI Mapping
[   16.231645] pci 0000:00:0b.0: Enabling HT MSI Mapping
[   16.231657] pci 0000:00:0c.0: Enabling HT MSI Mapping
[   16.231668] pci 0000:00:0d.0: Enabling HT MSI Mapping
[   16.231681] pci 0000:00:0e.0: Enabling HT MSI Mapping
[   16.231696] pci 0000:00:0f.0: Enabling HT MSI Mapping
[   16.231707] pci 0000:00:10.0: Enabling HT MSI Mapping
[   16.231719] pci 0000:00:11.0: Enabling HT MSI Mapping
[   16.231731] Boot video device is 0000:00:12.0
[   16.231864] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[   16.231880] assign_interrupt_mode Found MSI capability
[   16.231895] Allocate Port Service[0000:00:0b.0:pcie00]
[   16.231944] PCI: Setting latency timer of device 0000:00:0c.0 to 64
[   16.231960] assign_interrupt_mode Found MSI capability
[   16.231971] Allocate Port Service[0000:00:0c.0:pcie00]
[   16.232012] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[   16.232028] assign_interrupt_mode Found MSI capability
[   16.232039] Allocate Port Service[0000:00:0d.0:pcie00]
[   16.232083] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[   16.232098] assign_interrupt_mode Found MSI capability
[   16.232109] Allocate Port Service[0000:00:0e.0:pcie00]
[   16.232153] PCI: Setting latency timer of device 0000:00:0f.0 to 64
[   16.232168] assign_interrupt_mode Found MSI capability
[   16.232179] Allocate Port Service[0000:00:0f.0:pcie00]
[   16.232222] PCI: Setting latency timer of device 0000:00:10.0 to 64
[   16.232238] assign_interrupt_mode Found MSI capability
[   16.232249] Allocate Port Service[0000:00:10.0:pcie00]
[   16.232290] PCI: Setting latency timer of device 0000:00:11.0 to 64
[   16.232306] assign_interrupt_mode Found MSI capability
[   16.232317] Allocate Port Service[0000:00:11.0:pcie00]
[   16.253941] Real Time Clock Driver v1.12ac
[   16.254106] hpet_resources: 0xfed00000 is busy
[   16.254141] Linux agpgart interface v0.102
[   16.254143] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   16.254255] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   16.254738] 00:0d: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   16.255280] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   16.255330] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   16.255404] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64irq 1,12
[   16.256004] serio: i8042 KBD port at 0x60,0x64 irq 1
[   16.256011] serio: i8042 AUX port at 0x60,0x64 irq 12
[   16.275959] mice: PS/2 mouse device common for all mice
[   16.275995] cpuidle: using governor ladder
[   16.275997] cpuidle: using governor menu
[   16.276108] NET: Registered protocol family 1
[   16.276193] registered taskstats version 1
[   16.276290]   Magic number: 8:823:391
[   16.276402] /build/buildd/linux-2.6.24/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   16.276404] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   16.276405] EDD information not available.
[   16.276415] Freeing unused kernel memory: 320k freed
[   16.313213] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   17.423181] fuse init (API version 7.9)
[   17.438964] ACPI Exception (processor_core-0816): AE_NOT_FOUND, ProcessorDevice is not present [20070126]
[   17.438974] ACPI Exception (processor_core-0816): AE_NOT_FOUND, ProcessorDevice is not present [20070126]
[   17.690414] usbcore: registered new interface driver usbfs
[   17.690434] usbcore: registered new interface driver hub
[   17.691081] usbcore: registered new device driver usb
[   17.693098] ACPI: PCI Interrupt Link [LUB2] enabled at IRQ 23
[   17.693109] ACPI: PCI Interrupt 0000:00:02.1[B] -> Link [LUB2] -> GSI 23 (level, low) -> IRQ 23
[   17.693339] PCI: Setting latency timer of device 0000:00:02.1 to 64
[   17.693345] ehci_hcd 0000:00:02.1: EHCI Host Controller
[   17.693574] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 1
[   17.693604] ehci_hcd 0000:00:02.1: debug port 1
[   17.693607] PCI: cache line size of 64 is not supported by device 0000:00:02.1
[   17.693617] ehci_hcd 0000:00:02.1: irq 23, io mem 0xdfffec00
[   17.700624] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   17.702252] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   17.702360] usb usb1: configuration #1 chosen from 1 choice
[   17.702378] hub 1-0:1.0: USB hub found
[   17.702383] hub 1-0:1.0: 6 ports detected
[   17.712848] SCSI subsystem initialized
[   17.726819] libata version 3.00 loaded.
[   17.802364] Floppy drive(s): fd0 is 1.44M
[   17.806542] forcedeth: Reverse Engineered nForce ethernet driver. Version0.61.
[   17.806882] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 22
[   17.806892] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [LMAC] -> GSI 22 (level, low) -> IRQ 22
[   17.806896] PCI: Setting latency timer of device 0000:00:0a.0 to 64
[   17.826855] FDC 0 is a post-1991 82077
[   18.326986] forcedeth 0000:00:0a.0: ifname eth0, PHY OUI 0x1374 @ 1, addr00:1e:8c:d5:70:a8
[   18.326990] forcedeth 0000:00:0a.0: highdma pwrctl mgmt timirq gbit lnktim msi desc-v3
[   18.327109] ACPI: PCI Interrupt Link [UB12] enabled at IRQ 21
[   18.327120] ACPI: PCI Interrupt 0000:00:04.1[B] -> Link [UB12] -> GSI 21 (level, low) -> IRQ 21
[   18.327301] PCI: Setting latency timer of device 0000:00:04.1 to 64
[   18.327307] ehci_hcd 0000:00:04.1: EHCI Host Controller
[   18.327363] ehci_hcd 0000:00:04.1: new USB bus registered, assigned bus number 2
[   18.327391] ehci_hcd 0000:00:04.1: debug port 1
[   18.327394] PCI: cache line size of 64 is not supported by device 0000:00:04.1
[   18.327404] ehci_hcd 0000:00:04.1: irq 21, io mem 0xdfffe800
[   18.337820] ehci_hcd 0000:00:04.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   18.337896] usb usb2: configuration #1 chosen from 1 choice
[   18.337912] hub 2-0:1.0: USB hub found
[   18.337916] hub 2-0:1.0: 6 ports detected
[   18.442005] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   18.442328] ACPI: PCI Interrupt Link [LSA0] enabled at IRQ 20
[   18.442337] ACPI: PCI Interrupt 0000:00:09.0[A] -> Link [LSA0] -> GSI 20 (level, low) -> IRQ 20
[   18.442358] PCI: Setting latency timer of device 0000:00:09.0 to 64
[   18.442363] ACPI: PCI interrupt for device 0000:00:09.0 disabled
[   18.444736] ACPI: PCI Interrupt Link [LUB0] enabled at IRQ 23
[   18.444740] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [LUB0] -> GSI 23 (level, low) -> IRQ 23
[   18.444907] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   18.444912] ohci_hcd 0000:00:02.0: OHCI Host Controller
[   18.444962] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 3
[   18.444974] ohci_hcd 0000:00:02.0: irq 23, io mem 0xdffff000
[   18.500056] usb usb3: configuration #1 chosen from 1 choice
[   18.500077] hub 3-0:1.0: USB hub found
[   18.500083] hub 3-0:1.0: 6 ports detected
[   18.602285] ACPI: PCI Interrupt Link [UB11] enabled at IRQ 22
[   18.602290] ACPI: PCI Interrupt 0000:00:04.0[A] -> Link [UB11] -> GSI 22 (level, low) -> IRQ 22
[   18.602475] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   18.602481] ohci_hcd 0000:00:04.0: OHCI Host Controller
[   18.602531] ohci_hcd 0000:00:04.0: new USB bus registered, assigned bus number 4
[   18.602548] ohci_hcd 0000:00:04.0: irq 22, io mem 0xdfffd000
[   18.659968] usb usb4: configuration #1 chosen from 1 choice
[   18.659987] hub 4-0:1.0: USB hub found
[   18.659994] hub 4-0:1.0: 6 ports detected
[   18.762057] pata_amd 0000:00:06.0: version 0.3.10
[   18.762104] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   18.763895] scsi0 : pata_amd
[   18.764010] scsi1 : pata_amd
[   18.764677] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[   18.764679] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[   18.928456] ata2: port disabled. ignoring.
[   18.928529] ahci 0000:00:09.0: version 3.0
[   18.928539] ACPI: PCI Interrupt 0000:00:09.0[A] -> Link [LSA0] -> GSI 20 (level, low) -> IRQ 20
[   19.113326] usb 4-2: new low speed USB device using ohci_hcd and address 2
[   19.339557] usb 4-2: configuration #1 chosen from 1 choice
[   19.645723] usb 4-3: new low speed USB device using ohci_hcd and address 3
[   19.862249] usb 4-3: configuration #1 chosen from 1 choice
[   19.928808] ahci 0000:00:09.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xfimpl IDE mode
[   19.928811] ahci 0000:00:09.0: flags: 64bit ncq sntf led clo pmp pio
[   19.928815] PCI: Setting latency timer of device 0000:00:09.0 to 64
[   19.929084] scsi2 : ahci
[   19.929143] scsi3 : ahci
[   19.929172] scsi4 : ahci
[   19.929201] scsi5 : ahci
[   19.929258] ata3: SATA max UDMA/133 abar m8192@0xdfff6000 port 0xdfff6100irq 20
[   19.929260] ata4: SATA max UDMA/133 abar m8192@0xdfff6000 port 0xdfff6180irq 20
[   19.929263] ata5: SATA max UDMA/133 abar m8192@0xdfff6000 port 0xdfff6200irq 20
[   19.929265] ata6: SATA max UDMA/133 abar m8192@0xdfff6000 port 0xdfff6280irq 20
[   20.568384] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   20.569559] ata3.00: ATAPI: HL-DT-STDVD-ROM GDRH20N, 0L02, max UDMA/100
[   20.725205] ata3.00: configured for UDMA/100
[   21.367862] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   21.368690] ata4.00: ATA-7: ST3250410AS, 3.AAC, max UDMA/133
[   21.368693] ata4.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[   21.369374] ata4.00: configured for UDMA/133
[   21.687658] ata5: SATA link down (SStatus 0 SControl 300)
[   22.007451] ata6: SATA link down (SStatus 0 SControl 300)
[   22.009047] scsi 2:0:0:0: CD-ROM            HL-DT-ST DVD-ROM GDRH20N  0L02 PQ: 0 ANSI: 5
[   22.009492] scsi 3:0:0:0: Direct-Access     ATA      ST3250410AS      3.AA PQ: 0 ANSI: 5
[   22.026580] Driver 'sd' needs updating - please use bus_type methods
[   22.028767] sd 3:0:0:0: [sda] 488397168 512-byte hardware sectors (250059MB)
[   22.028778] sd 3:0:0:0: [sda] Write Protect is off
[   22.028780] sd 3:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   22.028790] sd 3:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   22.028828] sd 3:0:0:0: [sda] 488397168 512-byte hardware sectors (250059MB)
[   22.028834] sd 3:0:0:0: [sda] Write Protect is off
[   22.028835] sd 3:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   22.028844] sd 3:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   22.028848]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   22.043623] usbcore: registered new interface driver hiddev
[   22.047183] sr0: scsi3-mmc drive: 52x/52x cd/rw xa/form2 cdda tray
[   22.047188] Uniform CD-ROM driver Revision: 3.20
[   22.047233] sr 2:0:0:0: Attached scsi CD-ROM sr0
[   22.049074] input: MOSART Semi. Input Device as /devices/pci0000:00/0000:00:04.0/usb4/4-2/4-2:1.0/input/input2
[   22.050513]  sda1 sda2 <<6>input,hidraw0: USB HID v1.10 Keyboard [MOSART Semi. Input Device] on usb-0000:00:04.0-2
[   22.072111] input: MOSART Semi. Input Device as /devices/pci0000:00/0000:00:04.0/usb4/4-2/4-2:1.1/input/input3
[   22.073103]  sda5 >
[   22.073177] sd 3:0:0:0: [sda] Attached SCSI disk
[   22.076346] sr 2:0:0:0: Attached scsi generic sg0 type 5
[   22.076363] sd 3:0:0:0: Attached scsi generic sg1 type 0
[   22.124191] input,hidraw1: USB HID v1.10 Mouse [MOSART Semi. Input Device] on usb-0000:00:04.0-2
[   22.124209] usbcore: registered new interface driver usbhid
[   22.124212] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   22.290416] Attempting manual resume
[   22.290419] swsusp: Resume From Partition 8:5
[   22.290421] PM: Checking swsusp image.
[   22.290586] PM: Resume from disk failed.
[   22.333664] kjournald starting.  Commit interval 5 seconds
[   22.333915] EXT3-fs: mounted filesystem with ordered data mode.
[   28.488269] input: PC Speaker as /devices/platform/pcspkr/input/input4
[   28.707692] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   28.735062] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   28.770022] nvidia: module license 'NVIDIA' taints kernel.
[   29.055692] parport_pc 00:05: reported by Plug and Play ACPI
[   29.055739] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   29.076257] input: Power Button (FF) as /devices/virtual/input/input5
[   29.138906] ACPI: Power Button (FF) [PWRF]
[   29.138971] input: Power Button (CM) as /devices/virtual/input/input6
[   29.202858] ACPI: Power Button (CM) [PWRB]
[   29.256735] ACPI: PCI Interrupt Link [SGRU] enabled at IRQ 21
[   29.256740] ACPI: PCI Interrupt 0000:00:12.0[A] -> Link [SGRU] -> GSI 21 (level, low) -> IRQ 21
[   29.256746] PCI: Setting latency timer of device 0000:00:12.0 to 64
[   29.256892] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  169.12  Thu Feb 14 17:51:09 PST 2008
[   29.714627] ACPI: WMI-Acer: Mapper loaded
[   29.767216] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 20
[   29.767220] ACPI: PCI Interrupt 0000:00:07.0[A] -> Link [LAZA] -> GSI 20 (level, low) -> IRQ 20
[   29.767380] PCI: Setting latency timer of device 0000:00:07.0 to 64
[   29.802020] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[   30.440263] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input7
[   31.706902] lp0: using parport0 (interrupt-driven).
[   31.792628] Adding 2634620k swap on /dev/sda5.  Priority:-1 extents:1 across:2634620k
[   32.350338] EXT3 FS on sda1, internal journal
[   32.461252] device-mapper: uevent: version 1.0.3
[   32.461291] device-mapper: ioctl: 4.12.0-ioctl (2007-10-02) initialised: [email]dm-devel@redhat.com[/email]
[   33.815671] ip_tables: (C) 2000-2006 Netfilter Core Team
[   35.623200] RPC: Registered udp transport module.
[   35.623203] RPC: Registered tcp transport module.
[   36.562132] No dock devices found.
[   36.942932] powernow-k8: Found 1 AMD Athlon(tm) 64 X2 Dual Core Processor5200+ processors (2 cpu cores) (version 2.20.00)
[   36.942767] powernow-k8:    0 : fid 0x13 (2700 MHz), vid 0x8
[   36.942771] powernow-k8:    1 : fid 0x12 (2600 MHz), vid 0x9
[   36.942773] powernow-k8:    2 : fid 0x10 (2400 MHz), vid 0xb
[   36.942774] powernow-k8:    3 : fid 0xe (2200 MHz), vid 0xd
[   36.942776] powernow-k8:    4 : fid 0xc (2000 MHz), vid 0xf
[   36.942777] powernow-k8:    5 : fid 0xa (1800 MHz), vid 0x11
[   36.942778] powernow-k8:    6 : fid 0x2 (1000 MHz), vid 0x12
[   36.942818] powernow-k8: ph2 null fid transition 0x13
[   38.107531] NET: Registered protocol family 10
[   38.107763] lo: Disabled Privacy Extensions
[   40.329115] ppdev: user-space parallel port driver
[   40.729015] audit(1220293415.121:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5411 profile="/usr/sbin/cupsd" namespace="default"
[   51.097716] Installing knfsd (copyright (C) 1996 [email]okir@monad.swb.de[/email]).
[   51.221506] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[   51.252864] NFSD: starting 90-second grace period
[   52.137005] Clocksource tsc unstable (delta = -314809340 ns)
[   53.797813] lirc_dev: IR Remote Control driver registered, major 61
[   53.800572] lirc_mceusb2: no version for "lirc_get_pdata" found: kernel tainted.
[   53.801228]
[   53.801231] lirc_mceusb2: Philips eHome USB IR Transciever and Microsoft MCE 2005 Remote Control driver for LIRC $Revision: 1.36 $
[   53.801234] lirc_mceusb2: Daniel Melander <lirc@rajidae.se>, Martin Blatter <martin_a_blatter@yahoo.com>
[   53.803266] usbcore: registered new interface driver lirc_mceusb2
[   54.170152] NET: Registered protocol family 17
[   59.684289] eth0: no IPv6 routers present
[ 3852.854202] usb 4-3: usbfs: USBDEVFS_CONTROL failed cmd lsusb rqt 128 rq 6 len 10 ret -62
[ 3852.855303] usb 4-3: usbfs: USBDEVFS_CONTROL failed cmd lsusb rqt 128 rq 6 len 4 ret -62
[ 3852.856412] usb 4-3: usbfs: USBDEVFS_CONTROL failed cmd lsusb rqt 128 rq 0 len 2 ret -62



**_Also hope everything to be OK with the Hurricane Gustav....._**

> **DemonBob said:**
> Might be. 

Give me the outputs of (with the remote plugged in)

```
lsusb -v
```
```
ls -la /dev/input/by-id/
```
```
dmesg
```

Also i am right in the path of Hurricane Gustav, so i might be unable to reply.

---

### Post by salamaza on 2008-12-03
yes please i have the same problem, does anyone know how to make it work?

---

