---
title: "Video HW configuration help"
date: 2012-12-05
forum: Multimedia Software
---

### Post by j3ff on 2012-12-05
Hello,

I have a few questions about video mode setting.  I reckon that the answers to
these questions would be generally useful in clarifying the various ways the
video hardware can be driven by X and/or the kernel.  It seems that there are
at least 3 ways:  X (userland) drivers, framebuffer drivers like vesafb and
intelfb, and modesetting.  I'm not sure about the last one though.

I am working on an intel atom based PC, similar to an Asus eee PC.  According
to hwinfo --gfxcard the video hardware is "Intel 945 GME" .

I have general questions about the different ways that video cards can be
driven by the kernel and/or by X.  I want to know about "modesetting",
framebuffer, and X drivers and how they play together.  My aim, if it's
possible, is to have the kernel set the video mode once and for all at startup
and not have X set a video mode at all.

The monitor is out of the ordinary.  It's made by Seform.  It's an LCD with a 
resistive touch screen.  The touch screen isn't really relevent for this
discussion though.   

The screen can be driven at the resolutions that I want, namely 1280x768. (I
know that's an odd res but it matches the screen, which is an unusual ratio
of 5:3).

I should also mention that the OS is a customised Ubuntu 12.10.  The kernel is
linux version 3.5.0.17.  

I can get Xorg to appear in the desired res and colour depth when I use the 
X intel driver.

There are framebuffer drivers intelfb and vesafb.  Then there's another intel
driver, i915, and I'm not sure how that relates to the framebuffer and video
hardware.

As I understand it, these days it's possible to have the kernel set the video
mode at startup and that's it.  X can be configured to start up and use the
mode set by the kernel.  X can be told not to set a mode of its own.  Is this
understanding correct?  If so, how do I get X to not attempt to set a mode?

What is the difference between modesetting driver and framebuffer driver?  It
seems that I can configure X to use a "modesetting" driver or the fbdev
driver.  Is this understanding correct?  When would I use one driver over the
other?

I take it that the fbdev driver uses a kernel framebuffer driver like intelfb
or vesafb??

I apologise for the somewhat abstract nature of the questions.  I do think
that good answers will benefit not just me though.  

Included below is the output of various "hwinfo" and "lshw" commands.

Thanks in advance,
Jeff





PS:

I've also found that the utility fbset doesn't like me giving it video timimg
parameters with either -t or any of the more specific timing/clock options.  
It spits out "ioctl FBIOPUT_VSCREENINFO: Invalid argument".
I have found that I can set my chosen resolutions if I supply zeros for the
timing numbers.  Here's an example from /etc/fb.modes:

#mode "1280x768-60"
mode "seform"
    # PCLK: 80.14 MHz, H: 47.70 kHz, V: 60.00 Hz
    geometry 1280 768 1280 768 32
    timings 0 0 0 0 0 0 0
    #timings 12479 200 64 23 1 136 3
    hsync low
    vsync high
    accel false
endmode

gtf gave me the timings but fbset won't apply them.








------------------------------------------------------------------------------
hwinfo --gfxcard:

09: PCI 02.0: 0300 VGA compatible controller (VGA)              
  [Created at pci.318]
  Unique ID: _Znp.GP3zrmbAw5B
  SysFS ID: /devices/pci0000:00/0000:00:02.0
  SysFS BusID: 0000:00:02.0
  Hardware Class: graphics card
  Model: "Intel 945 GME"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x27ae "945 GME"
  SubVendor: pci 0x8086 "Intel Corporation"
  SubDevice: pci 0x27ae 
  Revision: 0x03
  Driver: "i915"
  Driver Modules: "drm"
  Memory Range: 0xfde80000-0xfdefffff (rw,non-prefetchable)
  I/O Ports: 0xff00-0xff07 (rw)
  Memory Range: 0xd0000000-0xdfffffff (ro,non-prefetchable)
  Memory Range: 0xfdf80000-0xfdfbffff (rw,non-prefetchable)
  IRQ: 16 (no events)
  Module Alias: "pci:v00008086d000027AEsv00008086sd000027AEbc03sc00i00"
  Driver Info #0:
    XFree86 v4 Server Module: intel
  Driver Info #1:
    XFree86 v4 Server Module: intel
    3D Support: yes
    Extensions: dri
  Config Status: cfg=new, avail=yes, need=no, active=unknown

10: PCI 02.1: 0380 Display controller
  [Created at pci.318]
  Unique ID: ruGf.87xrQUqUSGD
  SysFS ID: /devices/pci0000:00/0000:00:02.1
  SysFS BusID: 0000:00:02.1
  Hardware Class: graphics card
  Model: "Intel Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x27a6 "Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller"
  SubVendor: pci 0x8086 "Intel Corporation"
  SubDevice: pci 0x27ae 
  Revision: 0x03
  Memory Range: 0xfdf00000-0xfdf7ffff (rw,non-prefetchable,disabled)
  Module Alias: "pci:v00008086d000027A6sv00008086sd000027AEbc03sc80i00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
------------------------------------------------------------------------------




------------------------------------------------------------------------------
This is the graphics hw related bits of lshw output:

     *-pci
          description: Host bridge
          product: Mobile 945GSE Express Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display:0
             description: VGA compatible controller
             product: Mobile 945GSE Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:fde80000-fdefffff ioport:ff00(size=8) memory:d0000000-dfffffff memory:fdf80000-fdfbffff
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: latency=0
             resources: memory:fdf00000-fdf7ffff
------------------------------------------------------------------------------

------------------------------------------------------------------------------
Here's the output of hwinfo --vbe.  It's rather long but the video modes are
listed at the bottom.  The screen and intel HW can do more that the listed
modes though.



01: None 00.0: 10105 BIOS                                       
  [Created at bios.190]
  Unique ID: rdCR.lZF+r4EgHp4
  Hardware Class: bios
  VESA BIOS Version: 3.0
  Current VESA Mode: 0x4112
  BIOS Keyboard LED Status:
    Scroll Lock: off
    Num Lock: on
    Caps Lock: off
  Serial Port 0: 0x3f8
  Serial Port 1: 0x2f8
  Serial Port 2: 0x3e8
  Serial Port 3: 0x2e8
  Base Memory: 636 kB
  PnP BIOS: @@@0000
  MP spec rev 1.4 info:
    OEM id: "OEM00000"
    Product id: "PROD00000000"
    1 CPUs (0 disabled)
  BIOS32 Service Directory Entry: 0xf9f00
  SMBIOS Version: 2.2
  BIOS Info: #0
    Vendor: "Phoenix Technologies, LTD"
    Version: "6.00 PG"
    Date: "05/03/2012"
    Start Address: 0xe0000
    ROM Size: 1024 kB
    Features: 0x0003000000007fcb9e90
      ISA supported
      PCI supported
      PnP supported
      APM supported
      BIOS flashable
      BIOS shadowing allowed
      CD boot supported
      Selectable boot supported
      BIOS ROM socketed
      EDD spec supported
      360kB Floppy supported
      1.2MB Floppy supported
      720kB Floppy supported
      2.88MB Floppy supported
      Print Screen supported
      8042 Keyboard Services supported
      Serial Services supported
      Printer Services supported
      CGA/Mono Video supported
      ACPI supported
      USB Legacy supported
  System Info: #1
    Manufacturer: "PhoenixAward"
    Product: "945GSE"
    Version: "6.0"
    Serial: "0123456789"
    UUID: undefined, but settable
    Wake-up: 0x06 (Power Switch)
  Board Info: #2
    Manufacturer: "PhoenixAward"
    Product: "945GSE"
    Version: "6.0"
    Serial: "0123456789"
  Chassis Info: #3
    Type: 0x03 (Desktop)
    Bootup State: 0x02 (Unknown)
    Power Supply State: 0x02 (Unknown)
    Thermal State: 0x02 (Unknown)
    Security Status: 0x02 (Unknown)
  Processor Info: #4
    Socket: "Other"
    Socket Type: 0x04 (ZIF Socket)
    Socket Status: Populated
    Type: 0x03 (CPU)
    Family: 0x01 (Other)
    Manufacturer: "Intel"
    Version: "Intel(R) Atom(TM)"
    Processor ID: 0xbfe9fbff000106c2
    Status: 0x01 (Enabled)
    Voltage: 1.1 V
    External Clock: 133 MHz
    Max. Speed: 3066 MHz
    Current Speed: 1600 MHz
    L1 Cache: #10
    L2 Cache: #11
  Type 5 Record: #5
    Data 00: 05 18 05 00 04 04 03 03 0a 01 00 01 00 01 04 06
    Data 10: 00 07 00 08 00 09 00 04
  Type 6 Record: #6
    Data 00: 06 0c 06 00 01 01 00 01 00 8b 8b 00
    String 1: "A0"
  Type 6 Record: #7
    Data 00: 06 0c 07 00 01 ff 00 02 00 7f 7f 00
    String 1: "A1"
  Type 6 Record: #8
    Data 00: 06 0c 08 00 01 ff 00 02 00 7f 7f 00
    String 1: "A2"
  Type 6 Record: #9
    Data 00: 06 0c 09 00 01 ff 00 02 00 7f 7f 00
    String 1: "A3"
  Cache Info: #10
    Designation: "Internal Cache"
    Level: L1
    State: Enabled
    Mode: 0x01 (Write Back)
    Location: 0x00 (Internal, Not Socketed)
    ECC: 0x02 (Unknown)
    Type: 0x02 (Unknown)
    Associativity: 0x02 (Unknown)
    Max. Size: 64 kB
    Current Size: 64 kB
    Supported SRAM Types: 0x0020 (Synchronous)
    Current SRAM Type: 0x0020 (Synchronous)
  Cache Info: #11
    Designation: "External Cache"
    Level: L2
    State: Enabled
    Mode: 0x01 (Write Back)
    Location: 0x01 (External, Not Socketed)
    ECC: 0x02 (Unknown)
    Type: 0x02 (Unknown)
    Associativity: 0x02 (Unknown)
    Supported SRAM Types: 0x0020 (Synchronous)
    Current SRAM Type: 0x0020 (Synchronous)
  Port Connector: #12
    Type: 0xff (Other)
    Internal Designator: "PRIMARY IDE"
    Internal Connector: 0x16 (On Board IDE)
  Port Connector: #13
    Type: 0xff (Other)
    Internal Designator: "SECONDARY IDE"
    Internal Connector: 0x16 (On Board IDE)
  Port Connector: #14
    Type: 0x07 (Serial Port 16450 Compatible)
    Internal Designator: "COM1"
    Internal Connector: 0x18 (9 Pin Dual Inline [pin 10 cut])
    External Connector: 0x08 (DB-9 pin male)
  Port Connector: #15
    Type: 0x07 (Serial Port 16450 Compatible)
    Internal Designator: "COM2"
    Internal Connector: 0x18 (9 Pin Dual Inline [pin 10 cut])
    External Connector: 0x08 (DB-9 pin male)
  Port Connector: #16
    Type: 0x05 (Parallel Port ECP/EPP)
    Internal Designator: "LPT1"
    Internal Connector: 0x05 (DB-25 pin female)
    External Connector: 0x05 (DB-25 pin female)
  Port Connector: #17
    Type: 0x0d (Keyboard Port)
    Internal Designator: "Keyboard"
    Internal Connector: 0x0f (PS/2)
    External Connector: 0x0f (PS/2)
  Port Connector: #18
    Type: 0x0e (Mouse Port)
    Internal Designator: "PS/2 Mouse"
    Internal Connector: 0x0f (PS/2)
    External Connector: 0x0f (PS/2)
  Port Connector: #19
    Type: 0x10 (USB)
    External Designator: "USB0"
    External Connector: 0xff (Other)
  Port Connector: #20
    Type: 0x10 (USB)
    External Designator: "USB1"
    External Connector: 0xff (Other)
  System Slot: #21
    Designation: "PCI0"
    Type: 0x06 (PCI)
    Bus Width: 0x05 (32 bit)
    Status: 0x03 (Available)
    Length: 0x04 (Long)
    Slot ID: 1
    Characteristics: 0x0102 (5.0 V, PME#)
  System Slot: #22
    Designation: "PCI1"
    Type: 0x06 (PCI)
    Bus Width: 0x05 (32 bit)
    Status: 0x03 (Available)
    Length: 0x04 (Long)
    Slot ID: 2
    Characteristics: 0x0102 (5.0 V, PME#)
  System Slot: #23
    Designation: "PCI2"
    Type: 0x06 (PCI)
    Bus Width: 0x05 (32 bit)
    Status: 0x03 (Available)
    Length: 0x04 (Long)
    Slot ID: 3
    Characteristics: 0x0102 (5.0 V, PME#)
  System Slot: #24
    Designation: "PCI3"
    Type: 0x06 (PCI)
    Bus Width: 0x05 (32 bit)
    Status: 0x03 (Available)
    Length: 0x04 (Long)
    Slot ID: 4
    Characteristics: 0x0102 (5.0 V, PME#)
  System Slot: #25
    Designation: "PCI4"
    Type: 0x06 (PCI)
    Bus Width: 0x05 (32 bit)
    Status: 0x03 (Available)
    Length: 0x04 (Long)
    Slot ID: 5
    Characteristics: 0x0102 (5.0 V, PME#)
  System Slot: #26
    Designation: "PCI5"
    Type: 0x06 (PCI)
    Bus Width: 0x05 (32 bit)
    Status: 0x03 (Available)
    Length: 0x04 (Long)
    Slot ID: 6
    Characteristics: 0x0102 (5.0 V, PME#)
  System Slot: #27
    Designation: "PCI6"
    Type: 0x06 (PCI)
    Bus Width: 0x05 (32 bit)
    Status: 0x03 (Available)
    Length: 0x04 (Long)
    Slot ID: 7
    Characteristics: 0x0102 (5.0 V, PME#)
  System Slot: #28
    Designation: "PCI7"
    Type: 0x06 (PCI)
    Bus Width: 0x05 (32 bit)
    Status: 0x03 (Available)
    Length: 0x04 (Long)
    Slot ID: 8
    Characteristics: 0x0102 (5.0 V, PME#)
  System Slot: #29
    Designation: "PCI8"
    Type: 0x06 (PCI)
    Bus Width: 0x05 (32 bit)
    Status: 0x03 (Available)
    Length: 0x04 (Long)
    Slot ID: 9
    Characteristics: 0x0102 (5.0 V, PME#)
  System Slot: #30
    Designation: "PCI9"
    Type: 0xa5 (Other)
    Bus Width: 0x05 (32 bit)
    Status: 0x04 (In Use)
    Length: 0x04 (Long)
    Slot ID: 10
    Characteristics: 0x0102 (5.0 V, PME#)
  System Slot: #31
    Designation: "PCI10"
    Type: 0x06 (PCI)
    Bus Width: 0x05 (32 bit)
    Status: 0x04 (In Use)
    Length: 0x04 (Long)
    Slot ID: 0
    Characteristics: 0x0102 (5.0 V, PME#)
  Language Info: #32
    Languages: n|US|iso8859-1, n|US|iso8859-1, r|CA|iso8859-1, a|JP|unicode
    Current: n|US|iso8859-1
  Physical Memory Array: #33
    Use: 0x03 (System memory)
    Location: 0x03 (Motherboard)
    Slots: 4
    Max. Size: 4 GB
    ECC: 0x03 (None)
  Memory Device: #34
    Location: "A0"
    Bank: "Bank0/1"
    Memory Array: #33
    Form Factor: 0x09 (DIMM)
    Type: 0x13 (Other)
    Type Detail: 0x0080 (Synchronous)
    Data Width: 64 bits
    Size: 2 GB
  Memory Device: #35
    Location: "A1"
    Bank: "Bank2/3"
    Memory Array: #33
    Form Factor: 0x09 (DIMM)
    Type: 0x02 (Unknown)
    Type Detail: 0x0004 (Unknown)
    Data Width: 0 bits
    Size: No Memory Installed
  Memory Device: #36
    Location: "A2"
    Bank: "Bank4/5"
    Memory Array: #33
    Form Factor: 0x09 (DIMM)
    Type: 0x02 (Unknown)
    Type Detail: 0x0004 (Unknown)
    Data Width: 0 bits
    Size: No Memory Installed
  Memory Device: #37
    Location: "A3"
    Bank: "Bank6/7"
    Memory Array: #33
    Form Factor: 0x09 (DIMM)
    Type: 0x02 (Unknown)
    Type Detail: 0x0004 (Unknown)
    Data Width: 0 bits
    Size: No Memory Installed
  32bit-Memory Error Info: #38
    Type: 0x01 (Other)
    Granularity: 0x01 (Other)
    Operation: 0x01 (Other)
  Memory Array Mapping: #39
    Memory Array: #34
    Partition Width: 1
    Start Address: 0x00000000
    End Address: 0x80000000
  Memory Device Mapping: #40
    Memory Device: #35
    Array Mapping: #39
    Row: 1
    Interleave Pos: 0
    Interleaved Depth: 0
    Start Address: 0x00000000
    End Address: 0x80000000
  Memory Device Mapping: #41
    Memory Device: #36
    Array Mapping: #39
    Row: 1
    Interleave Pos: 0
    Interleaved Depth: 0
    Start Address: 0x00000000
    End Address: 0x00000400
  Memory Device Mapping: #42
    Memory Device: #37
    Array Mapping: #39
    Row: 1
    Interleave Pos: 0
    Interleaved Depth: 0
    Start Address: 0x00000000
    End Address: 0x00000400
  Memory Device Mapping: #43
    Memory Device: #38
    Array Mapping: #39
    Row: 1
    Interleave Pos: 0
    Interleaved Depth: 0
    Start Address: 0x00000000
    End Address: 0x00000400
  Type 32 Record: #44
    Data 00: 20 0b 2c 00 00 00 00 00 00 00 00
  Config Status: cfg=new, avail=yes, need=no, active=unknown

02: None 00.0: 11001 VESA Framebuffer
  [Created at bios.464]
  Unique ID: rdCR.il6towt04X5
  Hardware Class: framebuffer
  Model: "Intel(r) 82945GM Chipset Family Graphics Controller"
  Vendor: "Intel Corporation"
  Device: "Intel(r) 82945GM Chipset Family Graphics Controller"
  SubVendor: "Intel(r) 82945GM Chipset Family Graphics Chip Accelerated VGA BIOS"
  SubDevice: 
  Revision: "Hardware Version 0.0"
  Memory Size: 7 MB + 704 kB
  Memory Range: 0xd0000000-0xd07affff (rw)
  Mode 0x033c: 1920x1440 (+1920), 8 bits
  Mode 0x034d: 1920x1440 (+3840), 16 bits
  Mode 0x033a: 1600x1200 (+1600), 8 bits
  Mode 0x034b: 1600x1200 (+3200), 16 bits
  Mode 0x035a: 1600x1200 (+6400), 24 bits
  Mode 0x0307: 1280x1024 (+1280), 8 bits
  Mode 0x031a: 1280x1024 (+2560), 16 bits
  Mode 0x031b: 1280x1024 (+5120), 24 bits
  Mode 0x0305: 1024x768 (+1024), 8 bits
  Mode 0x0317: 1024x768 (+2048), 16 bits
  Mode 0x0318: 1024x768 (+4096), 24 bits
  Mode 0x0312: 640x480 (+2560), 24 bits
  Mode 0x0314: 800x600 (+1600), 16 bits
  Mode 0x0315: 800x600 (+3200), 24 bits
  Mode 0x0301: 640x480 (+640), 8 bits
  Mode 0x0303: 800x600 (+832), 8 bits
  Mode 0x0311: 640x480 (+1280), 16 bits
  Config Status: cfg=new, avail=yes, need=no, active=unknown

------------------------------------------------------------------------------

---

