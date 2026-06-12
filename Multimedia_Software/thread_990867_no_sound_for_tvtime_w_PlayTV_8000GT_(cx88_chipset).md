---
title: "no sound for tvtime w/ PlayTV 8000GT (cx88 chipset)"
date: 2008-11-23
forum: Multimedia Software
---

### Post by roiavidan on 2008-11-23
Hello everyone,

I'm having a problem getting TVTime to play sound on my machine.
I succeeded using both VLC and MPlayer for watching TV w/ sound, but they can't do it on the first time (I have to run TVTime, close it and then run either one of them to be able to watch TV).

On Windows XP I was also able to watch TV with the software that came with my TV Card, so I'm guessing it's not a hardware or a wiring issue.

I tried various solutions I found while googling (using SOX which worked but was out of sync with the image, verifying that the controls are not muted in alsa, reconnecting the cable on the back to the mic input instead of the line-in) but couldn't get it to work.

I also tried practically ALL the mixer options in TVTime but none worked.

TVTime shows TV in great quality (I think even better than VLC and MPlayer), but w/o sound and I would really like to use it.

Please help!

I'm running Ubuntu Intrepid w/ kernel 2.6.27-8-generic and TVTime 1.0.2 (which is in Intrepid repositories).

Here's my lspci:
```

00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0d.0 VGA compatible controller: nVidia Corporation GeForce 6150SE nForce 430 (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:06.0 Multimedia video controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
01:06.1 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port] (rev 05)

```

Output when running "tvtime -v":
```

Running tvtime 1.0.2.
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/roi/.tvtime/tvtime.xml
cpuinfo: CPU AMD Athlon(tm) 64 X2 Dual Core Processor 5000+, family 15, model 11, stepping 2.
cpuinfo: CPU measured at 2611.995MHz.
tvtime: Cannot set priority to -10: Permission denied.
xcommon: Display :0.0, vendor The X.Org Foundation, vendor release 10502000
xfullscreen: Using XINERAMA for dual-head information.
xfullscreen: Pixels are square.
xfullscreen: Number of displays is 1.
xfullscreen: Head 0 at 0,0 with size 1680x1050.
xcommon: Have XTest, will use it to ping the screensaver.
xcommon: Pixel aspect ratio 1:1.
xcommon: Pixel aspect ratio 1:1.
xcommon: Window manager is Metacity and is EWMH compliant.
xcommon: You are using metacity.  Disabling aspect ratio hints
xcommon: since most deployed versions of metacity are still broken.
xcommon: Using EWMH state fullscreen property.
xcommon: Using EWMH state above property.
xcommon: Using EWMH state below property.
xcommon: Pixel aspect ratio 1:1.
xcommon: Displaying in a 768x576 window inside 768x576 space.
xvoutput: Using XVIDEO adaptor 355: NV17 Video Texture.
speedycode: Using MMXEXT optimized functions.
station: Reading stationlist from /home/roi/.tvtime/stationlist.xml
videoinput: Using video4linux2 driver 'cx8800', card 'Prolink Pixelview MPEG 8000GT' (bus PCI:0000:01:06.0).
videoinput: Version is 6, capabilities 5010011.
videoinput: Maximum input width: 720 pixels.
tvtime: Sampling input at 720 pixels per scanline.
xcommon: Pixel aspect ratio 1:1.
xcommon: Displaying in a 768x576 window inside 768x576 space.
xcommon: Received a map, marking window as visible (61).
xcommon: Pixel aspect ratio 1:1.
xcommon: Pixel aspect ratio 1:1.
xcommon: Displaying in a 1400x1050 window inside 1680x1050 space.

```

output from "v4lctl show":
```

norm: PAL-M
input: Television
audio mode: mono
bright: 128
contrast: 128
color: 128
hue: 128
volume: 63
Balance: 64
mute: off
Chroma AGC: on
Color killer: on

```

output from "cat /proc/asound/devices":
```

  2:        : timer
  3:        : sequencer
  4: [ 0- 1]: digital audio playback
  5: [ 0- 1]: digital audio capture
  6: [ 0- 0]: digital audio playback
  7: [ 0- 0]: digital audio capture
  8: [ 0]   : control
  9: [ 1- 0]: digital audio capture
 10: [ 1]   : control

```

my dmesg output:
```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-8-generic (buildd@rothera) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Thu Nov 6 17:33:54 UTC 2008 (Ubuntu 2.6.27-8.17-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000077fb0000 (usable)
[    0.000000]  BIOS-e820: 0000000077fb0000 - 0000000077fbe000 (ACPI data)
[    0.000000]  BIOS-e820: 0000000077fbe000 - 0000000077fe0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 0000000077fe0000 - 0000000077fee000 (reserved)
[    0.000000]  BIOS-e820: 0000000077ff0000 - 0000000078000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fef00000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] last_pfn = 0x77fb0 max_arch_pfn = 0x100000
[    0.000000] kernel direct mapping tables up to 38000000 @ 7000-c000
[    0.000000] RAMDISK: 3782c000 - 37fefa37
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP 000FB770, 0024 (r2 ACPIAM)
[    0.000000] ACPI: XSDT 77FB0100, 004C (r1 A_M_I_ OEMXSDT   3000826 MSFT       97)
[    0.000000] ACPI: FACP 77FB0290, 00F4 (r3 A_M_I_ OEMFACP   3000826 MSFT       97)
[    0.000000] ACPI: DSDT 77FB05D0, 65E6 (r1  A0865 A0865000        0 INTL 20051117)
[    0.000000] ACPI: FACS 77FBE000, 0040
[    0.000000] ACPI: APIC 77FB0390, 0080 (r1 A_M_I_ OEMAPIC   3000826 MSFT       97)
[    0.000000] ACPI: MCFG 77FB0410, 003C (r1 A_M_I_ OEMMCFG   3000826 MSFT       97)
[    0.000000] ACPI: OEMB 77FBE040, 0060 (r1 A_M_I_ AMI_OEM   3000826 MSFT       97)
[    0.000000] ACPI: HPET 77FB6BC0, 0038 (r1 A_M_I_ OEMHPET0  3000826 MSFT       97)
[    0.000000] 1023MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 38000000
[    0.000000]   low ram: 00000000 - 38000000
[    0.000000]   bootmap 00008000 - 0000f000
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 0038000000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00005c0a20]    TEXT DATA BSS ==> [0000100000 - 00005c0a20]
[    0.000000]   #4 [003782c000 - 0037fefa37]          RAMDISK ==> [003782c000 - 0037fefa37]
[    0.000000]   #5 [00005c1000 - 00005c4000]    INIT_PG_TABLE ==> [00005c1000 - 00005c4000]
[    0.000000]   #6 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #7 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
[    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
[    0.000000] found SMP MP-table at [c00ff780] 000ff780
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00038000
[    0.000000]   HighMem  0x00038000 -> 0x00077fb0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x00077fb0
[    0.000000] On node 0 totalpages: 491343
[    0.000000] free_area_init_node: node 0, pgdat c048a500, node_mem_map c1000000
[    0.000000]   DMA zone: 3963 pages, LIFO batch:0
[    0.000000]   Normal zone: 223300 pages, LIFO batch:31
[    0.000000]   HighMem zone: 259760 pages, LIFO batch:31
[    0.000000] Detected use of extended apic ids on hypertransport bus
[    0.000000] ACPI: PM-Timer IO Port: 0x508
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 0 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e4000
[    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 78000000:86c00000)
[    0.000000] PERCPU: Allocating 41628 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 4, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 487023
[    0.000000] Kernel command line: root=UUID=73cd964a-d6e2-4895-853e-ba3a062680cd ro quiet splash 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Extended CMOS year: 2000
[    0.000000] TSC: PIT calibration confirmed by PMTIMER.
[    0.000000] TSC: using PIT calibration value
[    0.000000] Detected 2611.807 MHz processor.
[    0.004000] spurious 8259A interrupt: IRQ7.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] Memory: 1933384k/1965760k available (2572k kernel code, 31136k reserved, 1160k data, 424k init, 1048256k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xf8800000 - 0xff3fe000   ( 107 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[    0.004000]       .init : 0xc04ab000 - 0xc0515000   ( 424 kB)
[    0.004000]       .data : 0xc03832da - 0xc04a5680   (1160 kB)
[    0.004000]       .text : 0xc0100000 - 0xc03832da   (2572 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.004000] hpet clockevent registered
[    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 5223.61 BogoMIPS (lpj=10447228)
[    0.004000] Security Framework initialized
[    0.004000] SELinux:  Disabled at boot.
[    0.004000] AppArmor: AppArmor initialized
[    0.004000] Mount-cache hash table entries: 512
[    0.004000] Initializing cgroup subsys ns
[    0.004000] Initializing cgroup subsys cpuacct
[    0.004000] Initializing cgroup subsys memory
[    0.004000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.004000] CPU 0(2) -> Core 0
[    0.004000] using C1E aware idle routine
[    0.004000] Checking 'hlt' instruction... OK.
[    0.017327] ACPI: Core revision 20080609
[    0.019297] ACPI: Checking initramfs for custom DSDT
[    0.278450] ENABLING IO-APIC IRQs
[    0.278674] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
[    0.284017] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
[    0.284017] ...trying to set up timer (IRQ0) through the 8259A ...
[    0.284017] ..... (found apic 0 pin 0) ...
[    0.326126] ....... works.
[    0.326128] CPU0: AMD Athlon(tm) 64 X2 Dual Core Processor 5000+ stepping 02
[    0.328020] Booting processor 1/1 ip 6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 5223.79 BogoMIPS (lpj=10447596)
[    0.004000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.004000] CPU 1(2) -> Core 1
[    0.412148] CPU1: AMD Athlon(tm) 64 X2 Dual Core Processor 5000+ stepping 02
[    0.412171] Brought up 2 CPUs
[    0.412174] Total of 2 processors activated (10447.41 BogoMIPS).
[    0.412210] CPU0 attaching sched-domain:
[    0.412212]  domain 0: span 0-1 level CPU
[    0.412214]   groups: 0 1
[    0.412219] CPU1 attaching sched-domain:
[    0.412220]  domain 0: span 0-1 level CPU
[    0.412222]   groups: 1 0
[    0.412274] net_namespace: 840 bytes
[    0.412274] Booting paravirtualized kernel on bare hardware
[    0.412274] Time:  9:36:50  Date: 11/23/08
[    0.412274] NET: Registered protocol family 16
[    0.412276] EISA bus registered
[    0.412276] ACPI: bus type pci registered
[    0.412276] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.412276] PCI: Not using MMCONFIG.
[    0.412661] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=4
[    0.412663] PCI: Using configuration type 1 for base access
[    0.412855] ACPI: EC: Look up EC in DSDT
[    0.426347] ACPI: Interpreter enabled
[    0.426350] ACPI: (supports S0 S1 S3 S4 S5)
[    0.426366] ACPI: Using IOAPIC for interrupt routing
[    0.426418] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.433067] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
[    0.433069] PCI: Using MMCONFIG for extended config space
[    0.440197] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.440197] PCI: 0000:00:01.0 reg 10 io port: [900, 9ff]
[    0.440197] PCI: 0000:00:01.1 reg 10 io port: [e00, e3f]
[    0.440198] PCI: 0000:00:01.1 reg 20 io port: [600, 63f]
[    0.440202] PCI: 0000:00:01.1 reg 24 io port: [700, 73f]
[    0.440216] pci 0000:00:01.1: PME# supported from D3hot D3cold
[    0.440222] pci 0000:00:01.1: PME# disabled
[    0.440260] PCI: 0000:00:02.0 reg 10 32bit mmio: [ddfff000, ddffffff]
[    0.440279] pci 0000:00:02.0: supports D1
[    0.440280] pci 0000:00:02.0: supports D2
[    0.440282] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.440285] pci 0000:00:02.0: PME# disabled
[    0.440303] PCI: 0000:00:02.1 reg 10 32bit mmio: [ddffec00, ddffecff]
[    0.440324] pci 0000:00:02.1: supports D1
[    0.440326] pci 0000:00:02.1: supports D2
[    0.440328] pci 0000:00:02.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.440331] pci 0000:00:02.1: PME# disabled
[    0.440377] PCI: 0000:00:05.0 reg 10 32bit mmio: [ddff8000, ddffbfff]
[    0.440398] pci 0000:00:05.0: PME# supported from D3hot D3cold
[    0.440401] pci 0000:00:05.0: PME# disabled
[    0.440430] PCI: 0000:00:06.0 reg 20 io port: [ffa0, ffaf]
[    0.440458] PCI: 0000:00:07.0 reg 10 32bit mmio: [ddffd000, ddffdfff]
[    0.440462] PCI: 0000:00:07.0 reg 14 io port: [e480, e487]
[    0.440478] pci 0000:00:07.0: supports D1
[    0.440480] pci 0000:00:07.0: supports D2
[    0.440482] pci 0000:00:07.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.440486] pci 0000:00:07.0: PME# disabled
[    0.440500] PCI: 0000:00:08.0 reg 10 io port: [e400, e407]
[    0.440504] PCI: 0000:00:08.0 reg 14 io port: [e080, e083]
[    0.440507] PCI: 0000:00:08.0 reg 18 io port: [e000, e007]
[    0.440510] PCI: 0000:00:08.0 reg 1c io port: [dc00, dc03]
[    0.440513] PCI: 0000:00:08.0 reg 20 io port: [d880, d88f]
[    0.440517] PCI: 0000:00:08.0 reg 24 32bit mmio: [ddffc000, ddffcfff]
[    0.440552] pci 0000:00:09.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.440555] pci 0000:00:09.0: PME# disabled
[    0.440577] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.440579] pci 0000:00:0b.0: PME# disabled
[    0.440600] pci 0000:00:0c.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.440602] pci 0000:00:0c.0: PME# disabled
[    0.440613] PCI: 0000:00:0d.0 reg 10 32bit mmio: [dc000000, dcffffff]
[    0.440617] PCI: 0000:00:0d.0 reg 14 32bit mmio: [c0000000, cfffffff]
[    0.440623] PCI: 0000:00:0d.0 reg 1c 64bit mmio: [db000000, dbffffff]
[    0.440627] PCI: 0000:00:0d.0 reg 30 32bit mmio: [ddfc0000, ddfdffff]
[    0.444051] PCI: 0000:01:06.0 reg 10 32bit mmio: [df000000, dfffffff]
[    0.444095] PCI: 0000:01:06.1 reg 10 32bit mmio: [de000000, deffffff]
[    0.444150] pci 0000:00:04.0: transparent bridge
[    0.444153] PCI: bridge 0000:00:04.0 32bit mmio: [de000000, dfffffff]
[    0.444261] bus 00 -> node 0
[    0.444266] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.444499] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.444635] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P2._PRT]
[    0.444741] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR11._PRT]
[    0.444846] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR12._PRT]
[    0.452412] ACPI: PCI Interrupt Link [LNKA] (IRQs 16 17 18 19) *11
[    0.452469] ACPI: PCI Interrupt Link [LNKB] (IRQs 16 17 18 19) *0, disabled.
[    0.452696] ACPI: PCI Interrupt Link [LNKC] (IRQs 16 17 18 19) *0, disabled.
[    0.452924] ACPI: PCI Interrupt Link [LNKD] (IRQs 16 17 18 19) *0, disabled.
[    0.453152] ACPI: PCI Interrupt Link [LNEA] (IRQs 16 17 18 19) *0, disabled.
[    0.453379] ACPI: PCI Interrupt Link [LNEB] (IRQs 16 17 18 19) *0, disabled.
[    0.453607] ACPI: PCI Interrupt Link [LNEC] (IRQs 16 17 18 19) *0, disabled.
[    0.453834] ACPI: PCI Interrupt Link [LNED] (IRQs 16 17 18 19) *0, disabled.
[    0.454062] ACPI: PCI Interrupt Link [LUB0] (IRQs 20 21 22 23) *5
[    0.454290] ACPI: PCI Interrupt Link [LUB2] (IRQs 20 21 22 23) *11
[    0.454517] ACPI: PCI Interrupt Link [LMAC] (IRQs 20 21 22 23) *5
[    0.454745] ACPI: PCI Interrupt Link [LAZA] (IRQs 20 21 22 23) *10
[    0.454976] ACPI: PCI Interrupt Link [LACI] (IRQs 20 21 22 23) *0, disabled.
[    0.455204] ACPI: PCI Interrupt Link [LMC9] (IRQs 20 21 22 23) *11
[    0.456134] ACPI: PCI Interrupt Link [LSMB] (IRQs 20 21 22 23) *10
[    0.456362] ACPI: PCI Interrupt Link [LPMU] (IRQs 20 21 22 23) *0, disabled.
[    0.456590] ACPI: PCI Interrupt Link [LSA0] (IRQs 20 21 22 23) *11
[    0.456817] ACPI: PCI Interrupt Link [LSA1] (IRQs 20 21 22 23) *0, disabled.
[    0.457088] ACPI: PCI Interrupt Link [LATA] (IRQs 20 21 22 23) *0, disabled.
[    0.457140] ACPI Warning (tbutils-0217): Incorrect checksum in table [OEMB] - 04, should be FF [20080609]
[    0.457140] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.457140] pnp: PnP ACPI init
[    0.457140] ACPI: bus type pnp registered
[    0.460579] pnp 00:06: io resource (0x900-0x97f) overlaps 0000:00:01.0 BAR 0 (0x900-0x9ff), disabling
[    0.460582] pnp 00:06: io resource (0x980-0x9ff) overlaps 0000:00:01.0 BAR 0 (0x900-0x9ff), disabling
[    0.464395] pnp: PnP ACPI: found 15 devices
[    0.464396] ACPI: ACPI bus type pnp unregistered
[    0.464399] PnPBIOS: Disabled by ACPI PNP
[    0.464416] PCI: Using ACPI for IRQ routing
[    0.472038] NET: Registered protocol family 8
[    0.472040] NET: Registered protocol family 20
[    0.472068] NetLabel: Initializing
[    0.472070] NetLabel:  domain hash size = 128
[    0.472072] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.472087] NetLabel:  unlabeled traffic allowed by default
[    0.472094] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 31
[    0.472098] hpet0: 3 32-bit timers, 25000000 Hz
[    0.474072] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    0.474074]    actual entries 65620
[    0.474212] AppArmor: AppArmor Filesystem Enabled
[    0.474237] ACPI: RTC can wake from S4
[    0.476044] Switched to high resolution mode on CPU 0
[    0.476187] Switched to high resolution mode on CPU 1
[    0.480037] system 00:06: ioport range 0xa30-0xa37 has been reserved
[    0.480040] system 00:06: ioport range 0x4d0-0x4d1 has been reserved
[    0.480042] system 00:06: ioport range 0x800-0x80f has been reserved
[    0.480045] system 00:06: ioport range 0x500-0x57f has been reserved
[    0.480047] system 00:06: ioport range 0x580-0x5ff has been reserved
[    0.480049] system 00:06: ioport range 0x800-0x87f could not be reserved
[    0.480052] system 00:06: ioport range 0x880-0x8ff has been reserved
[    0.480054] system 00:06: ioport range 0xd00-0xd7f has been reserved
[    0.480057] system 00:06: ioport range 0xd80-0xdff has been reserved
[    0.480060] system 00:06: ioport range 0x2000-0x207f has been reserved
[    0.480062] system 00:06: ioport range 0x2080-0x20ff has been reserved
[    0.480066] system 00:06: iomem range 0xfefe0000-0xfefe01ff has been reserved
[    0.480068] system 00:06: iomem range 0xfefe1000-0xfefe1fff has been reserved
[    0.480071] system 00:06: iomem range 0xfee01000-0xfeefffff could not be reserved
[    0.480074] system 00:06: iomem range 0xffb80000-0xffffffff could not be reserved
[    0.480076] system 00:06: iomem range 0xff300000-0xff3fffff has been reserved
[    0.480083] system 00:08: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.480086] system 00:08: iomem range 0xfee00000-0xfee00fff could not be reserved
[    0.480088] system 00:08: iomem range 0x78000000-0x7fffffff has been reserved
[    0.480095] system 00:0b: ioport range 0x230-0x23f has been reserved
[    0.480097] system 00:0b: ioport range 0x290-0x29f has been reserved
[    0.480100] system 00:0b: ioport range 0xa00-0xa0f has been reserved
[    0.480102] system 00:0b: ioport range 0xa10-0xa1f has been reserved
[    0.480108] system 00:0d: iomem range 0xe0000000-0xefffffff has been reserved
[    0.480114] system 00:0e: iomem range 0x0-0x9ffff could not be reserved
[    0.480116] system 00:0e: iomem range 0xc0000-0xcffff could not be reserved
[    0.480119] system 00:0e: iomem range 0xe0000-0xfffff could not be reserved
[    0.480121] system 00:0e: iomem range 0x100000-0x77ffffff could not be reserved
[    0.480124] system 00:0e: iomem range 0xff700000-0xffffffff could not be reserved
[    0.515357] pci 0000:00:04.0: PCI bridge, secondary bus 0000:01
[    0.515359] pci 0000:00:04.0:   IO window: disabled
[    0.515363] pci 0000:00:04.0:   MEM window: 0xde000000-0xdfffffff
[    0.515365] pci 0000:00:04.0:   PREFETCH window: disabled
[    0.515369] pci 0000:00:09.0: PCI bridge, secondary bus 0000:02
[    0.515371] pci 0000:00:09.0:   IO window: disabled
[    0.515373] pci 0000:00:09.0:   MEM window: disabled
[    0.515375] pci 0000:00:09.0:   PREFETCH window: disabled
[    0.515378] pci 0000:00:0b.0: PCI bridge, secondary bus 0000:03
[    0.515380] pci 0000:00:0b.0:   IO window: disabled
[    0.515382] pci 0000:00:0b.0:   MEM window: disabled
[    0.515384] pci 0000:00:0b.0:   PREFETCH window: disabled
[    0.515387] pci 0000:00:0c.0: PCI bridge, secondary bus 0000:04
[    0.515389] pci 0000:00:0c.0:   IO window: disabled
[    0.515391] pci 0000:00:0c.0:   MEM window: disabled
[    0.515393] pci 0000:00:0c.0:   PREFETCH window: disabled
[    0.515402] pci 0000:00:04.0: setting latency timer to 64
[    0.515407] pci 0000:00:09.0: setting latency timer to 64
[    0.515411] pci 0000:00:0b.0: setting latency timer to 64
[    0.515415] pci 0000:00:0c.0: setting latency timer to 64
[    0.515418] bus: 00 index 0 io port: [0, ffff]
[    0.515419] bus: 00 index 1 mmio: [0, ffffffff]
[    0.515421] bus: 01 index 0 mmio: [0, 0]
[    0.515423] bus: 01 index 1 mmio: [de000000, dfffffff]
[    0.515424] bus: 01 index 2 mmio: [0, 0]
[    0.515426] bus: 01 index 3 io port: [0, ffff]
[    0.515428] bus: 01 index 4 mmio: [0, ffffffff]
[    0.515430] bus: 02 index 0 mmio: [0, 0]
[    0.515431] bus: 02 index 1 mmio: [0, 0]
[    0.515433] bus: 02 index 2 mmio: [0, 0]
[    0.515434] bus: 02 index 3 mmio: [0, 0]
[    0.515436] bus: 03 index 0 mmio: [0, 0]
[    0.515437] bus: 03 index 1 mmio: [0, 0]
[    0.515439] bus: 03 index 2 mmio: [0, 0]
[    0.515440] bus: 03 index 3 mmio: [0, 0]
[    0.515442] bus: 04 index 0 mmio: [0, 0]
[    0.515443] bus: 04 index 1 mmio: [0, 0]
[    0.515445] bus: 04 index 2 mmio: [0, 0]
[    0.515446] bus: 04 index 3 mmio: [0, 0]
[    0.515458] NET: Registered protocol family 2
[    0.528057] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.528324] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.529026] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.529394] TCP: Hash tables configured (established 131072 bind 65536)
[    0.529397] TCP reno registered
[    0.536093] NET: Registered protocol family 1
[    0.536205] checking if image is initramfs... it is
[    1.071958] Freeing initrd memory: 7950k freed
[    1.073202] audit: initializing netlink socket (disabled)
[    1.073220] type=2000 audit(1227433010.072:1): initialized
[    1.077900] highmem bounce pool size: 64 pages
[    1.077906] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.080172] VFS: Disk quotas dquot_6.5.1
[    1.080256] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.080350] msgmni has been set to 1745
[    1.080456] io scheduler noop registered
[    1.080458] io scheduler anticipatory registered
[    1.080459] io scheduler deadline registered
[    1.080470] io scheduler cfq registered (default)
[    1.080507] pci 0000:00:00.0: Enabling HT MSI Mapping
[    1.080596] pci 0000:00:04.0: Enabling HT MSI Mapping
[    1.080612] pci 0000:00:05.0: Enabling HT MSI Mapping
[    1.080637] pci 0000:00:07.0: Enabling HT MSI Mapping
[    1.080650] pci 0000:00:08.0: Enabling HT MSI Mapping
[    1.080664] pci 0000:00:09.0: Enabling HT MSI Mapping
[    1.080678] pci 0000:00:0b.0: Enabling HT MSI Mapping
[    1.080691] pci 0000:00:0c.0: Enabling HT MSI Mapping
[    1.080705] pci 0000:00:0d.0: Boot video device
[    1.080809] pcieport-driver 0000:00:09.0: setting latency timer to 64
[    1.080829] pcieport-driver 0000:00:09.0: found MSI capability
[    1.080847] pci_express 0000:00:09.0:pcie00: allocate port service
[    1.080893] pci_express 0000:00:09.0:pcie03: allocate port service
[    1.080961] pcieport-driver 0000:00:0b.0: setting latency timer to 64
[    1.080981] pcieport-driver 0000:00:0b.0: found MSI capability
[    1.080995] pci_express 0000:00:0b.0:pcie00: allocate port service
[    1.081039] pci_express 0000:00:0b.0:pcie03: allocate port service
[    1.081107] pcieport-driver 0000:00:0c.0: setting latency timer to 64
[    1.081127] pcieport-driver 0000:00:0c.0: found MSI capability
[    1.081141] pci_express 0000:00:0c.0:pcie00: allocate port service
[    1.081182] pci_express 0000:00:0c.0:pcie03: allocate port service
[    1.081487] isapnp: Scanning for PnP cards...
[    1.434777] isapnp: No Plug & Play device found
[    1.469593] hpet_resources: 0xfed00000 is busy
[    1.469688] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.469821] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.470547] 00:0c: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.472378] brd: module loaded
[    1.472446] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.472572] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    1.472968] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.472973] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.473282] mice: PS/2 mouse device common for all mice
[    1.473409] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    1.473443] rtc0: alarms up to one year, y3k, hpet irqs
[    1.473586] EISA: Probing bus 0 at eisa.0
[    1.473595] Cannot allocate resource for EISA slot 2
[    1.473609] EISA: Detected 0 cards.
[    1.473613] cpuidle: using governor ladder
[    1.473614] cpuidle: using governor menu
[    1.474020] TCP cubic registered
[    1.474046] Using IPI No-Shortcut mode
[    1.474238] registered taskstats version 1
[    1.474348]   Magic number: 0:294:627
[    1.474549] rtc_cmos 00:02: setting system clock to 2008-11-23 09:36:51 UTC (1227433011)
[    1.474552] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.474553] EDD information not available.
[    1.474840] Freeing unused kernel memory: 424k freed
[    1.474891] Write protecting the kernel text: 2576k
[    1.474923] Write protecting the kernel read-only data: 936k
[    1.503688] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    1.608401] fuse init (API version 7.9)
[    1.705044] processor ACPI0007:00: registered as cooling_device0
[    1.705299] processor ACPI0007:01: registered as cooling_device1
[    2.078557] usbcore: registered new interface driver usbfs
[    2.078580] usbcore: registered new interface driver hub
[    2.080552] usbcore: registered new device driver usb
[    2.087316] No dock devices found.
[    2.098999] SCSI subsystem initialized
[    2.116483] ACPI: PCI Interrupt Link [LUB2] enabled at IRQ 23
[    2.116495] ehci_hcd 0000:00:02.1: PCI INT B -> Link[LUB2] -> GSI 23 (level, low) -> IRQ 23
[    2.116505] ehci_hcd 0000:00:02.1: setting latency timer to 64
[    2.116508] ehci_hcd 0000:00:02.1: EHCI Host Controller
[    2.116556] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 1
[    2.116583] ehci_hcd 0000:00:02.1: debug port 1
[    2.116587] ehci_hcd 0000:00:02.1: cache line size of 64 is not supported
[    2.116606] ehci_hcd 0000:00:02.1: irq 23, io mem 0xddffec00
[    2.116676] libata version 3.00 loaded.
[    2.122505] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.132029] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    2.132181] usb usb1: configuration #1 chosen from 1 choice
[    2.132204] hub 1-0:1.0: USB hub found
[    2.132213] hub 1-0:1.0: 8 ports detected
[    2.236802] ACPI: PCI Interrupt Link [LUB0] enabled at IRQ 22
[    2.236814] ohci_hcd 0000:00:02.0: PCI INT A -> Link[LUB0] -> GSI 22 (level, low) -> IRQ 22
[    2.236828] ohci_hcd 0000:00:02.0: setting latency timer to 64
[    2.236831] ohci_hcd 0000:00:02.0: OHCI Host Controller
[    2.236943] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 2
[    2.236966] ohci_hcd 0000:00:02.0: irq 22, io mem 0xddfff000
[    2.294692] usb usb2: configuration #1 chosen from 1 choice
[    2.294720] hub 2-0:1.0: USB hub found
[    2.294729] hub 2-0:1.0: 8 ports detected
[    2.396905] pata_acpi 0000:00:06.0: setting latency timer to 64
[    2.396936] pata_amd 0000:00:06.0: version 0.3.10
[    2.396958] pata_amd 0000:00:06.0: setting latency timer to 64
[    2.397051] scsi0 : pata_amd
[    2.397163] scsi1 : pata_amd
[    2.397921] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    2.397924] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    2.560284] ata1.00: ATAPI: HL-DT-ST RW/DVD GCC-4521B, 1.00, max UDMA/33
[    2.560296] ata1: nv_mode_filter: 0x739f&0x701f->0x701f, BIOS=0x7000 (0xc0000000) ACPI=0x701f (60:900:0x11)
[    2.576219] ata1.00: configured for UDMA/33
[    2.576246] ata2: port disabled. ignoring.
[    2.576737] scsi 0:0:0:0: CD-ROM            HL-DT-ST RW/DVD GCC-4521B 1.00 PQ: 0 ANSI: 5
[    2.577230] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[    2.577578] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 21
[    2.577588] forcedeth 0000:00:07.0: PCI INT A -> Link[LMAC] -> GSI 21 (level, low) -> IRQ 21
[    2.577592] forcedeth 0000:00:07.0: setting latency timer to 64
[    3.096475] forcedeth 0000:00:07.0: ifname eth0, PHY OUI 0x1374 @ 1, addr 00:1f:c6:7c:be:15
[    3.096479] forcedeth 0000:00:07.0: highdma pwrctl mgmt timirq gbit lnktim msi desc-v3
[    3.096878] ACPI: PCI Interrupt Link [LSA0] enabled at IRQ 20
[    3.096887] pata_acpi 0000:00:08.0: PCI INT A -> Link[LSA0] -> GSI 20 (level, low) -> IRQ 20
[    3.096919] pata_acpi 0000:00:08.0: setting latency timer to 64
[    3.096929] pata_acpi 0000:00:08.0: PCI INT A disabled
[    3.100732] sata_nv 0000:00:08.0: version 3.5
[    3.100750] sata_nv 0000:00:08.0: PCI INT A -> Link[LSA0] -> GSI 20 (level, low) -> IRQ 20
[    3.100793] sata_nv 0000:00:08.0: setting latency timer to 64
[    3.101206] scsi2 : sata_nv
[    3.101286] scsi3 : sata_nv
[    3.101454] ata3: SATA max UDMA/133 cmd 0xe400 ctl 0xe080 bmdma 0xd880 irq 20
[    3.101456] ata4: SATA max UDMA/133 cmd 0xe000 ctl 0xdc00 bmdma 0xd888 irq 20
[    3.568034] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    3.576219] ata3.00: ATA-7: SAMSUNG HD753LJ, 1AA01110, max UDMA7
[    3.576223] ata3.00: 1465149168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    3.584206] ata3.00: configured for UDMA/133
[    3.896112] scsi 2:0:0:0: Direct-Access     ATA      SAMSUNG HD753LJ  1AA0 PQ: 0 ANSI: 5
[    3.906872] scsi 0:0:0:0: Attached scsi generic sg0 type 5
[    3.906906] scsi 2:0:0:0: Attached scsi generic sg1 type 0
[    3.919015] Driver 'sr' needs updating - please use bus_type methods
[    3.926367] sr0: scsi3-mmc drive: 52x/52x writer cd/rw xa/form2 cdda tray
[    3.926372] Uniform CD-ROM driver Revision: 3.20
[    3.926457] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    3.929694] Driver 'sd' needs updating - please use bus_type methods
[    3.929808] sd 2:0:0:0: [sda] 1465149168 512-byte hardware sectors (750156 MB)
[    3.929826] sd 2:0:0:0: [sda] Write Protect is off
[    3.929828] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.929856] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.929919] sd 2:0:0:0: [sda] 1465149168 512-byte hardware sectors (750156 MB)
[    3.929934] sd 2:0:0:0: [sda] Write Protect is off
[    3.929936] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.929962] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.929966]  sda: sda2 < sda5 > sda3 sda4
[    3.943728] sd 2:0:0:0: [sda] Attached SCSI disk
[    4.138107] PM: Starting manual resume from disk
[    4.138110] PM: Resume from partition 8:4
[    4.138112] PM: Checking hibernation image.
[    4.138277] PM: Resume from disk failed.
[    4.172558] kjournald starting.  Commit interval 5 seconds
[    4.172573] EXT3-fs: mounted filesystem with ordered data mode.
[    9.166066] udevd version 124 started
[    9.669538] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    9.715872] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    9.805575] Linux agpgart interface v0.103
[    9.920926] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x600
[    9.920945] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x700
[    9.954851] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    9.972536] ACPI: Power Button (FF) [PWRF]
[    9.972636] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input3
[   10.004524] ACPI: Power Button (CM) [PWRB]
[   10.373026] nvidia: module license 'NVIDIA' taints kernel.
[   10.668766] Linux video capture interface: v2.00
[   10.705457] ACPI: PCI Interrupt Link [LMC9] enabled at IRQ 23
[   10.705463] nvidia 0000:00:0d.0: PCI INT A -> Link[LMC9] -> GSI 23 (level, low) -> IRQ 23
[   10.705469] nvidia 0000:00:0d.0: setting latency timer to 64
[   10.705722] NVRM: loading NVIDIA UNIX x86 Kernel Module  177.80  Wed Oct  1 14:38:10 PDT 2008
[   10.736042] input: PC Speaker as /devices/platform/pcspkr/input/input4
[   10.840962] cx88/0: cx2388x v4l2 driver version 0.0.6 loaded
[   10.841374] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 19
[   10.841385] cx8800 0000:01:06.0: PCI INT A -> Link[LNKA] -> GSI 19 (level, low) -> IRQ 19
[   10.842747] cx88[0]: subsystem: 1554:4935, board: Prolink Pixelview MPEG 8000GT [card=66,autodetected]
[   10.842750] cx88[0]: TV tuner type 71, Radio tuner type 0
[   11.069781] cx2388x alsa driver version 0.0.6 loaded
[   11.105223] tuner' 2-0061: chip found @ 0xc2 (cx88[0])
[   11.250867] xc2028 2-0061: creating new instance
[   11.250871] xc2028 2-0061: type set to XCeive xc2028/xc3028 tuner
[   11.250877] cx88[0]: Asking xc2028/3028 to load firmware xc3028-v27.fw
[   11.250949] input: cx88 IR (Prolink Pixelview MPEG as /devices/pci0000:00/0000:00:04.0/0000:01:06.0/input/input5
[   11.276678] cx88[0]/0: found at 0000:01:06.0, rev: 5, irq: 19, latency: 64, mmio: 0xdf000000
[   11.276739] cx88[0]/0: registered device video0 [v4l2]
[   11.276772] cx88[0]/0: registered device vbi0
[   11.276801] cx88[0]/0: registered device radio0
[   11.276862] firmware: requesting xc3028-v27.fw
[   11.476640] xc2028 2-0061: Loading 80 firmware images from xc3028-v27.fw, type: xc2028 firmware, ver 2.7
[   11.476750] cx88[0]: Calling XC2028/3028 callback
[   11.575958] xc2028 2-0061: Loading firmware for type=BASE (1), id 0000000000000000.
[   11.575962] cx88[0]: Calling XC2028/3028 callback
[   11.582216] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input6
[   11.769181] parport_pc 00:05: reported by Plug and Play ACPI
[   11.769250] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   12.658223] xc2028 2-0061: Loading firmware for type=(0), id 000000000000b700.
[   12.673676] SCODE (20000000), id 000000000000b700:
[   12.673679] xc2028 2-0061: Loading SCODE for type=MONO SCODE HAS_IF_4320 (60008000), id 0000000000008000.
[   12.736010] cx88[0]: Calling XC2028/3028 callback
[   12.856744] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 22
[   12.856750] HDA Intel 0000:00:05.0: PCI INT B -> Link[LAZA] -> GSI 22 (level, low) -> IRQ 22
[   12.856771] HDA Intel 0000:00:05.0: setting latency timer to 64
[   12.927838] cx88_audio 0000:01:06.1: PCI INT A -> Link[LNKA] -> GSI 19 (level, low) -> IRQ 19
[   12.927861] cx88[0]/1: CX88x/0: ALSA support for cx2388x boards
[   13.228606] lp0: using parport0 (interrupt-driven).
[   13.372559] Adding 1052248k swap on /dev/sda4.  Priority:-1 extents:1 across:1052248k
[   13.935235] EXT3 FS on sda3, internal journal
[   15.739967] type=1505 audit(1227440225.699:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4312
[   15.899646] type=1505 audit(1227440225.859:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4317
[   15.899860] type=1505 audit(1227440225.859:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4317
[   16.033625] ip_tables: (C) 2000-2006 Netfilter Core Team
[   16.551052] ACPI: WMI: Mapper loaded
[   16.745457] powernow-k8: Found 1 AMD Athlon(tm) 64 X2 Dual Core Processor 5000+ processors (2 cpu cores) (version 2.20.00)
[   16.745936] powernow-k8: ACPI Processor support is required for SMP systems but is absent. Please load the ACPI Processor module before starting this driver.
[   16.746218] powernow-k8: ACPI Processor support is required for SMP systems but is absent. Please load the ACPI Processor module before starting this driver.
[   17.247748] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   17.402127] NET: Registered protocol family 10
[   17.403269] lo: Disabled Privacy Extensions
[   17.562021] ppdev: user-space parallel port driver
[   19.335290] tun: Universal TUN/TAP device driver, 1.6
[   19.335297] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[   19.766478] cx88[0]: Calling XC2028/3028 callback
[   19.865698] xc2028 2-0061: Loading firmware for type=BASE FM (401), id 0000000000000000.
[   19.865702] cx88[0]: Calling XC2028/3028 callback
[   20.930749] xc2028 2-0061: Loading firmware for type=FM (400), id 0000000000000000.
[   20.976085] cx88[0]: Calling XC2028/3028 callback
[   25.482312] NET: Registered protocol family 17
[   30.571869] cx88[0]: Calling XC2028/3028 callback
[   30.671095] xc2028 2-0061: Loading firmware for type=BASE (1), id 0000000000000000.
[   30.671103] cx88[0]: Calling XC2028/3028 callback
[   31.790971] xc2028 2-0061: Loading firmware for type=(0), id 000000000000b700.
[   31.806929] SCODE (20000000), id 000000000000b700:
[   31.806937] xc2028 2-0061: Loading SCODE for type=MONO SCODE HAS_IF_4320 (60008000), id 0000000000008000.
[   31.868721] cx88[0]: Calling XC2028/3028 callback
[   32.180531] cx88[0]: Calling XC2028/3028 callback
[   32.936541] cx88[0]: Calling XC2028/3028 callback
[   35.944008] eth0: no IPv6 routers present
[   97.732490] ppdev0: registered pardevice
[   97.780020] ppdev0: unregistered pardevice
[   98.404205] ppdev0: registered pardevice
[   98.452281] ppdev0: unregistered pardevice
[   99.541554] ppdev0: registered pardevice
[   99.588250] ppdev0: unregistered pardevice

```


THANKS!!!

---

