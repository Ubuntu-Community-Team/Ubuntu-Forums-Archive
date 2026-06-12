---
title: "[SOLVED] Sound Sound Sound ; The lack therof"
date: 2008-01-18
forum: Multimedia &amp; Video
---

### Post by curtis1552 on 2008-01-18
Ok,
I have used the sound troubleshooting guide to no avail.
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)


My computer detects my sound card (all 3 devices that I have tried over time; AC97 onboard, and old Sound Blaster, and currently a Sound Blaster Audigy)

To make sure I didn't have problem from 'fixing' this I formatted and reinstalled Mythbuntu.
I disabled the onboard AC97 in the BIOS.
Then I tried to install the sound drivers following that manual.
I tried to compile the drivers after I still go no sound.
in alsamixer everything is maxed out
i ran sudo modprobe snd-emu10k1

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Audigy [Audigy 1 [SB0090]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 32/32
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
  Subdevice #31: subdevice #31
card 0: Audigy [Audigy 1 [SB0090]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: Audigy [Audigy 1 [SB0090]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0



lscpi -v 
**************This is just the SB stuff*******************
04:07.1 Input device controller: Creative Labs SB Audigy Game Port (rev 03)
        Subsystem: Creative Labs SB Audigy MIDI/Game Port
        Flags: bus master, medium devsel, latency 32
        I/O ports at b800 [size=8]
        Capabilities: <access denied>

04:07.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (prog-if 10 [OHCI])
        Subsystem: Creative Labs SB Audigy FireWire Port
        Flags: bus master, medium devsel, latency 32, IRQ 22
        Memory at fe8fe000 (32-bit, non-prefetchable) [size=2K]
        Memory at fe8f4000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

04:08.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
        Subsystem: Hauppauge computer works Inc. WinTV PVR 150
        Flags: bus master, medium devsel, latency 64, IRQ 22
        Memory at f8000000 (32-bit, prefetchable) [size=64M]
        Capabilities: <access denied>



Any help or ideas is appreciated.


edit - i rebooted but forgot to initalize the sound (it still doesn't work)
04:07.0 Multimedia audio controller: Creative Labs SB Audigy (rev 03)
        Subsystem: Creative Labs SB0090 Audigy Player
        Flags: bus master, medium devsel, latency 32, IRQ 16
        I/O ports at bc00 [size=32]
        Capabilities: <access denied>

04:07.1 Input device controller: Creative Labs SB Audigy Game Port (rev 03)
        Subsystem: Creative Labs SB Audigy MIDI/Game Port
        Flags: bus master, medium devsel, latency 32
        I/O ports at b800 [size=8]
        Capabilities: <access denied>

04:07.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (prog-if 10 [OHCI])
        Subsystem: Creative Labs SB Audigy FireWire Port
        Flags: bus master, medium devsel, latency 32, IRQ 22
        Memory at fe8fe000 (32-bit, non-prefetchable) [size=2K]
        Memory at fe8f4000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

---

### Post by wolfen69 on 2008-01-18
see this thread [http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound](http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound)

---

### Post by curtis1552 on 2008-01-19
Umm, yeah, look at the link at the top of my post.
I already tried it; it didn't work.

---

### Post by Dave Otter on 2008-01-19
Applications-Accessories-Terminal

                            type:-  asoundconf set-default-cardCARD  replcing CARD with card you want to use

---

### Post by curtis1552 on 2008-01-19
I only have one card installed; but I gave it a shot anyway.

$ asoundconf set-default-card0

Usage:
asoundconf is-active
asoundconf get|delete PARAMETER
asoundconf set PARAMETER VALUE
asoundconf list

Convenience macro functions:
asoundconf set-default-card PARAMETER
asoundconf reset-default-card
asoundconf set-pulseaudio
asoundconf unset-pulseaudio


It still doesn't work.

---

### Post by xeth_delta on 2008-01-19
Issue a
```
sudo /etc/init.t/alsasound restart
```
then call a "dmesg". What are the last output lines like? the ones concerning your card.

---

### Post by curtis1552 on 2008-01-19
the /etc/init.t does not exist; I have init.d and has alsasound.
sudo /etc/init.d/alsasound restart
Shutting down sound driver: done
ALSA driver is already running.

I highlighted the ALSA stuff in purple but there could be more somewhere that I missed


[    0.000000] Linux version 2.6.22-14-generic (buildd@terranova) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Dec 18 08:02:57 UTC 2007 (Ubuntu 2.6.22-14.47-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000057ef0000 (usable)
[    0.000000]  BIOS-e820: 0000000057ef0000 - 0000000057ef3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 0000000057ef3000 - 0000000057f00000 (ACPI data)
[    0.000000]  BIOS-e820: 0000000058000000 - 0000000060000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] 510MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f3b40
[    0.000000] Entering add_active_range(0, 0, 360176) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   360176
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   360176
[    0.000000] On node 0 totalpages: 360176
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 1021 pages used for memmap
[    0.000000]   HighMem zone: 129779 pages, LIFO batch:31
[    0.000000] DMI 2.2 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F7C10 checksum 0
[    0.000000] ACPI: RSDP 000F7C10, 0014 (r0 Nvidia)
[    0.000000] ACPI: RSDT 57EF3040, 0038 (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: FACP 57EF30C0, 0074 (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: DSDT 57EF3180, 61A6 (r1 NVIDIA AWRDACPI     1000 MSFT  100000E)
[    0.000000] ACPI: FACS 57EF0000, 0040
[    0.000000] ACPI: SSDT 57EF9440, 0188 (r1 PTLTD  POWERNOW        1  LTP        1)
[    0.000000] ACPI: SRAT 57EF9640, 00A0 (r1 AMD    HAMMER          1 AMD         1)
[    0.000000] ACPI: MCFG 57EF9740, 003C (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: APIC 57EF9380, 0072 (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
[    0.000000] Nvidia board detected. Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:3 APIC version 16
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1 15:3 APIC version 16
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 68000000 (gap: 60000000:80000000)
[    0.000000] Built 1 zonelists.  Total pages: 357363
[    0.000000] Kernel command line: root=UUID=2da551f1-e83d-46af-bc6b-e48085874063 ro quiet splash
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1002.147 MHz processor.
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Memory: 1416372k/1440704k available (2015k kernel code, 23184k reserved, 916k data, 364k init, 523200k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[    0.000000]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[    0.000000]       .data : 0xc02f7de6 - 0xc03dce84   ( 916 kB)
[    0.000000]       .text : 0xc0100000 - 0xc02f7de6   (2015 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[    0.000000] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[    0.084000] Calibrating delay using timer specific routine.. 2006.28 BogoMIPS (lpj=4012568)
[    0.084000] Security Framework v1.0.0 initialized
[    0.084000] SELinux:  Disabled at boot.
[    0.084000] Mount-cache hash table entries: 512
[    0.084000] CPU: After generic identify, caps: 178bfbff e3d3fbff 00000000 00000000 00000001 00000000 00000003
[    0.084000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.084000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.084000] CPU 0(2) -> Core 0
[    0.084000] CPU: After all inits, caps: 178bfbff e3d3fbff 00000000 00000410 00000001 00000000 00000003
[    0.084000] Compat vDSO mapped to ffffe000.
[    0.084000] Checking 'hlt' instruction... OK.
[    0.100000] SMP alternatives: switching to UP code
[    0.100000] Early unpacking initramfs... done
[    0.688000] ACPI: Core revision 20070126
[    0.688000] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[    0.696000] CPU0: AMD Athlon(tm) 64 X2 Dual Core Processor 3800+ stepping 02
[    0.696000] SMP alternatives: switching to SMP code
[    0.696000] Booting processor 1/1 eip 3000
[    0.708000] Initializing CPU#1
[    0.788000] Calibrating delay using timer specific routine.. 2004.34 BogoMIPS (lpj=4008686)
[    0.788000] CPU: After generic identify, caps: 178bfbff e3d3fbff 00000000 00000000 00000001 00000000 00000003
[    0.788000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.788000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.788000] CPU 1(2) -> Core 1
[    0.788000] CPU: After all inits, caps: 178bfbff e3d3fbff 00000000 00000410 00000001 00000000 00000003
[    0.788000] CPU1: AMD Athlon(tm) 64 X2 Dual Core Processor 3800+ stepping 02
[    0.788000] Total of 2 processors activated (4010.62 BogoMIPS).
[    0.788000] ENABLING IO-APIC IRQs
[    0.788000] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
[    0.832000] Brought up 2 CPUs
[    0.876000] migration_cost=4000
[    0.876000] Booting paravirtualized kernel on bare hardware
[    0.876000] Time: 21:01:37  Date: 00/19/108
[    0.876000] NET: Registered protocol family 16
[    0.876000] EISA bus registered
[    0.876000] ACPI: bus type pci registered
[    0.884000] PCI: PCI BIOS revision 3.00 entry at 0xfa7c0, last bus=4
[    0.884000] PCI: Using configuration type 1
[    0.884000] Setting up standard PCI resources
[    0.892000] ACPI: EC: Look up EC in DSDT
[    0.904000] ACPI: Interpreter enabled
[    0.904000] ACPI: (supports S0 S3 S4 S5)
[    0.904000] ACPI: Using IOAPIC for interrupt routing
[    0.920000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.920000] PCI: Probing PCI hardware (bus 00)
[    0.924000] PCI: Transparent bridge - 0000:00:10.0
[    0.924000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.924000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[    1.104000] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 10 *11 14 15)
[    1.104000] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 *7 9 10 11 14 15)
[    1.104000] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    1.104000] ACPI: PCI Interrupt Link [LNK4] (IRQs *5 7 9 10 11 14 15)
[    1.104000] ACPI: PCI Interrupt Link [LNK5] (IRQs *5 7 9 10 11 14 15)
[    1.104000] ACPI: PCI Interrupt Link [LNK6] (IRQs 5 *7 9 10 11 14 15)
[    1.104000] ACPI: PCI Interrupt Link [LNK7] (IRQs *5 7 9 10 11 14 15)
[    1.104000] ACPI: PCI Interrupt Link [LNK8] (IRQs 5 *7 9 10 11 14 15)
[    1.108000] ACPI: PCI Interrupt Link [LUBA] (IRQs *5 7 9 10 11 14 15)
[    1.108000] ACPI: PCI Interrupt Link [LUBB] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    1.108000] ACPI: PCI Interrupt Link [LMAC] (IRQs 5 7 9 *10 11 14 15)
[    1.108000] ACPI: PCI Interrupt Link [LACI] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    1.108000] ACPI: PCI Interrupt Link [LAZA] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    1.108000] ACPI: PCI Interrupt Link [LPMU] (IRQs 5 7 9 10 *11 14 15)
[    1.108000] ACPI: PCI Interrupt Link [LMCI] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    1.108000] ACPI: PCI Interrupt Link [LSMB] (IRQs 5 7 9 10 *11 14 15)
[    1.108000] ACPI: PCI Interrupt Link [LUB2] (IRQs 5 7 9 10 *11 14 15)
[    1.108000] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    1.108000] ACPI: PCI Interrupt Link [LSID] (IRQs 5 7 9 10 *11 14 15)
[    1.112000] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0
[    1.112000] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0
[    1.112000] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0, disabled.
[    1.112000] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0
[    1.112000] ACPI: PCI Interrupt Link [APC5] (IRQs 16) *0
[    1.112000] ACPI: PCI Interrupt Link [APC6] (IRQs 16) *0
[    1.112000] ACPI: PCI Interrupt Link [APC7] (IRQs 16) *0
[    1.112000] ACPI: PCI Interrupt Link [APC8] (IRQs 16) *0
[    1.112000] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0
[    1.112000] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22 23) *0, disabled.
[    1.116000] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0
[    1.116000] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22 23) *0, disabled.
[    1.116000] ACPI: PCI Interrupt Link [APMU] (IRQs 20 21 22 23) *0
[    1.116000] ACPI: PCI Interrupt Link [AAZA] (IRQs 20 21 22 23) *0, disabled.
[    1.116000] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22 23) *0, disabled.
[    1.116000] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0
[    1.116000] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0
[    1.116000] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22 23) *0, disabled.
[    1.116000] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
[    1.116000] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0
[    1.116000] Linux Plug and Play Support v0.97 (c) Adam Belay
[    1.116000] pnp: PnP ACPI init
[    1.116000] ACPI: bus type pnp registered
[    1.128000] pnp: PnP ACPI: found 11 devices
[    1.128000] ACPI: ACPI bus type pnp unregistered
[    1.128000] PnPBIOS: Disabled by ACPI PNP
[    1.128000] PCI: Using ACPI for IRQ routing
[    1.128000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    1.292000] NET: Registered protocol family 8
[    1.292000] NET: Registered protocol family 20
[    1.292000] pnp: 00:01: ioport range 0x1000-0x107f has been reserved
[    1.292000] pnp: 00:01: ioport range 0x1080-0x10ff has been reserved
[    1.292000] pnp: 00:01: ioport range 0x1400-0x147f has been reserved
[    1.292000] pnp: 00:01: ioport range 0x1480-0x14ff has been reserved
[    1.292000] pnp: 00:01: ioport range 0x1800-0x187f has been reserved
[    1.292000] pnp: 00:01: ioport range 0x1880-0x18ff has been reserved
[    1.292000] pnp: 00:01: ioport range 0x2000-0x207f has been reserved
[    1.292000] pnp: 00:01: ioport range 0x2080-0x20ff has been reserved
[    1.292000] pnp: 00:01: iomem range 0xfefe0000-0xfefe01ff could not be reserved
[    1.292000] pnp: 00:01: iomem range 0x58000000-0x5fffffff could not be reserved
[    1.292000] pnp: 00:09: iomem range 0xe0000000-0xefffffff could not be reserved
[    1.292000] pnp: 00:0a: iomem range 0xd0000-0xd3fff has been reserved
[    1.292000] pnp: 00:0a: iomem range 0xd5800-0xd7fff has been reserved
[    1.292000] pnp: 00:0a: iomem range 0xf0000-0xfbfff could not be reserved
[    1.292000] pnp: 00:0a: iomem range 0xfc000-0xfffff could not be reserved
[    1.324000] PCI: Bridge: 0000:01:00.0
[    1.324000]   IO window: a000-afff
[    1.324000]   MEM window: fe700000-fe7fffff
[    1.324000]   PREFETCH window: fe600000-fe6fffff
[    1.324000] PCI: Bridge: 0000:00:03.0
[    1.324000]   IO window: a000-afff
[    1.324000]   MEM window: fe700000-fe7fffff
[    1.324000]   PREFETCH window: fe600000-fe6fffff
[    1.324000] PCI: Bridge: 0000:00:04.0
[    1.324000]   IO window: c000-cfff
[    1.324000]   MEM window: fea00000-feafffff
[    1.324000]   PREFETCH window: fe900000-fe9fffff
[    1.324000] PCI: Bridge: 0000:00:10.0
[    1.324000]   IO window: b000-bfff
[    1.324000]   MEM window: fe800000-fe8fffff
[    1.324000]   PREFETCH window: f8000000-fbffffff
[    1.324000] PCI: Setting latency timer of device 0000:00:03.0 to 64
[    1.324000] ACPI: PCI Interrupt Link [APC5] enabled at IRQ 16
[    1.324000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [APC5] -> GSI 16 (level, low) -> IRQ 16
[    1.324000] PCI: Setting latency timer of device 0000:01:00.0 to 64
[    1.324000] PCI: Setting latency timer of device 0000:00:04.0 to 64
[    1.324000] PCI: Setting latency timer of device 0000:00:10.0 to 64
[    1.324000] NET: Registered protocol family 2
[    1.328000] Time: acpi_pm clocksource has been installed.
[    1.328000] Switched to high resolution mode on CPU 0
[    1.328000] Switched to high resolution mode on CPU 1
[    1.364000] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    1.364000] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[    1.364000] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    1.364000] TCP: Hash tables configured (established 131072 bind 65536)
[    1.364000] TCP reno registered
[    1.380000] checking if image is initramfs... it is
[    2.540000] Freeing initrd memory: 7203k freed
[    2.540000] audit: initializing netlink socket (disabled)
[    2.540000] audit(1200776498.328:1): initialized
[    2.540000] highmem bounce pool size: 64 pages
[    2.544000] VFS: Disk quotas dquot_6.5.1
[    2.544000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    2.544000] io scheduler noop registered
[    2.544000] io scheduler anticipatory registered
[    2.544000] io scheduler deadline registered
[    2.544000] io scheduler cfq registered (default)
[    2.544000] Boot video device is 0000:00:05.0
[    2.560000] PCI: Setting latency timer of device 0000:00:03.0 to 64
[    2.560000] assign_interrupt_mode Found MSI capability
[    2.560000] Allocate Port Service[0000:00:03.0:pcie00]
[    2.560000] PCI: Setting latency timer of device 0000:00:04.0 to 64
[    2.560000] assign_interrupt_mode Found MSI capability
[    2.560000] Allocate Port Service[0000:00:04.0:pcie00]
[    2.560000] isapnp: Scanning for PnP cards...
[    2.912000] isapnp: No Plug & Play device found
[    2.956000] Real Time Clock Driver v1.12ac
[    2.956000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    2.956000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    2.956000] input: Macintosh mouse button emulation as /class/input/input0
[    2.956000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    2.960000] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.960000] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.960000] mice: PS/2 mouse device common for all mice
[    2.960000] EISA: Probing bus 0 at eisa.0
[    2.960000] Cannot allocate resource for EISA slot 1
[    2.960000] Cannot allocate resource for EISA slot 2
[    2.960000] EISA: Detected 0 cards.
[    2.960000] TCP cubic registered
[    2.960000] NET: Registered protocol family 1
[    2.960000] Using IPI No-Shortcut mode
[    2.960000]   Magic number: 8:585:45
[    2.960000]   hash matches device ttyee
[    2.964000] Freeing unused kernel memory: 364k freed
[    2.984000] input: AT Translated Set 2 keyboard as /class/input/input1
[    4.372000] AppArmor: AppArmor initialized<5>audit(1200776500.328:2):  type=1505 info="AppArmor initialized" pid=1256
[    4.384000] fuse init (API version 7.8)
[    4.396000] Failure registering capabilities with primary security module.
[    4.424000] ACPI: Fan [FAN] (on)
[    4.436000] ACPI: Thermal Zone [THRM] (17 C)
[    5.432000] usbcore: registered new interface driver usbfs
[    5.432000] usbcore: registered new interface driver hub
[    5.432000] usbcore: registered new device driver usb
[    5.432000] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[    5.436000] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 23
[    5.436000] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [APCF] -> GSI 23 (level, low) -> IRQ 17
[    5.436000] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[    5.436000] ohci_hcd 0000:00:0b.0: OHCI Host Controller
[    5.436000] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 1
[    5.436000] ohci_hcd 0000:00:0b.0: irq 17, io mem 0xfebff000
[    5.556000] SCSI subsystem initialized
[    5.564000] libata version 2.21 loaded.
[    5.568000] usb usb1: configuration #1 chosen from 1 choice
[    5.568000] hub 1-0:1.0: USB hub found
[    5.568000] hub 1-0:1.0: 8 ports detected
[    5.568000] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.60.
[    5.672000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [APC5] -> GSI 16 (level, low) -> IRQ 16
[    5.672000] ohci_hcd 0000:02:00.0: OHCI Host Controller
[    5.672000] ohci_hcd 0000:02:00.0: new USB bus registered, assigned bus number 2
[    5.672000] ohci_hcd 0000:02:00.0: irq 16, io mem 0xfe7ff000
[    5.672000] sata_nv 0000:00:0e.0: version 3.4
[    5.672000] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 22
[    5.672000] ACPI: PCI Interrupt 0000:00:0e.0[A] -> Link [APSI] -> GSI 22 (level, low) -> IRQ 18
[    5.672000] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[    5.672000] scsi0 : sata_nv
[    5.672000] scsi1 : sata_nv
[    5.672000] ata1: SATA max UDMA/133 cmd 0x000109f0 ctl 0x00010bf2 bmdma 0x0001e000 irq 18
[    5.672000] ata2: SATA max UDMA/133 cmd 0x00010970 ctl 0x00010b72 bmdma 0x0001e008 irq 18
[    5.756000] usb usb2: configuration #1 chosen from 1 choice
[    5.756000] hub 2-0:1.0: USB hub found
[    5.756000] hub 2-0:1.0: 3 ports detected
[    5.860000] ACPI: PCI Interrupt Link [APC6] enabled at IRQ 16
[    5.860000] ACPI: PCI Interrupt 0000:02:00.1[B] -> Link [APC6] -> GSI 16 (level, low) -> IRQ 16
[    5.860000] ohci_hcd 0000:02:00.1: OHCI Host Controller
[    5.860000] ohci_hcd 0000:02:00.1: new USB bus registered, assigned bus number 3
[    5.860000] ohci_hcd 0000:02:00.1: irq 16, io mem 0xfe7fe000
[    5.944000] usb usb3: configuration #1 chosen from 1 choice
[    5.944000] hub 3-0:1.0: USB hub found
[    5.944000] hub 3-0:1.0: 2 ports detected
[    5.988000] ata1: SATA link down (SStatus 0 SControl 300)
[    6.308000] ata2: SATA link down (SStatus 0 SControl 300)
[    6.316000] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 21
[    6.316000] ACPI: PCI Interrupt 0000:00:0b.1[B] -> Link [APCL] -> GSI 21 (level, low) -> IRQ 19
[    6.316000] PCI: Setting latency timer of device 0000:00:0b.1 to 64
[    6.316000] ehci_hcd 0000:00:0b.1: EHCI Host Controller
[    6.316000] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 4
[    6.316000] ehci_hcd 0000:00:0b.1: debug port 1
[    6.316000] PCI: cache line size of 64 is not supported by device 0000:00:0b.1
[    6.316000] ehci_hcd 0000:00:0b.1: irq 19, io mem 0xfebfe000
[    6.316000] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    6.316000] usb usb4: configuration #1 chosen from 1 choice
[    6.316000] hub 4-0:1.0: USB hub found
[    6.316000] hub 4-0:1.0: 8 ports detected
[    6.420000] ACPI: PCI Interrupt Link [APC7] enabled at IRQ 16
[    6.420000] ACPI: PCI Interrupt 0000:02:00.2[C] -> Link [APC7] -> GSI 16 (level, low) -> IRQ 16
[    6.420000] ehci_hcd 0000:02:00.2: EHCI Host Controller
[    6.420000] ehci_hcd 0000:02:00.2: new USB bus registered, assigned bus number 5
[    6.420000] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 20
[    6.420000] ACPI: PCI Interrupt 0000:00:14.0[A] -> Link [APCH] -> GSI 20 (level, low) -> IRQ 20
[    6.420000] PCI: Setting latency timer of device 0000:00:14.0 to 64
[    6.420000] forcedeth: using HIGHDMA
[    6.444000] ehci_hcd 0000:02:00.2: irq 16, io mem 0xfe7fd000
[    6.444000] ehci_hcd 0000:02:00.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    6.444000] usb usb5: configuration #1 chosen from 1 choice
[    6.444000] hub 5-0:1.0: USB hub found
[    6.444000] hub 5-0:1.0: 5 ports detected
[    6.940000] eth0: forcedeth.c: subsystem: 0105b:0ca8 bound to 0000:00:14.0
[    6.940000] ACPI: PCI Interrupt 0000:02:01.0[A] -> Link [APC6] -> GSI 16 (level, low) -> IRQ 16
[    6.992000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[16]  MMIO=[fe7fc000-fe7fc7ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    7.000000] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
[    7.000000] ACPI: PCI Interrupt 0000:04:06.0[A] -> Link [APC4] -> GSI 19 (level, low) -> IRQ 21
[    7.048000] ohci1394: fw-host1: OHCI-1394 1.1 (PCI): IRQ=[21]  MMIO=[fe8ff000-fe8ff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    7.048000] ACPI: PCI Interrupt Link [APC2] enabled at IRQ 17
[    7.048000] ACPI: PCI Interrupt 0000:04:07.2[B] -> Link [APC2] -> GSI 17 (level, low) -> IRQ 22
[    7.100000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[    7.100000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[    7.100000] ohci1394: fw-host2: OHCI-1394 1.1 (PCI): IRQ=[22]  MMIO=[fe8fe000-fe8fe7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    7.104000] NFORCE-MCP51: IDE controller at PCI slot 0000:00:0d.0
[    7.104000] NFORCE-MCP51: chipset revision 161
[    7.104000] NFORCE-MCP51: not 100% native mode: will probe irqs later
[    7.104000] NFORCE-MCP51: 0000:00:0d.0 (rev a1) UDMA133 controller
[    7.104000]     ide0: BM-DMA at 0xf400-0xf407, BIOS settings: hda:DMA, hdb:DMA
[    7.104000]     ide1: BM-DMA at 0xf408-0xf40f, BIOS settings: hdc:DMA, hdd:DMA
[    7.104000] Probing IDE interface ide0...
[    7.392000] hda: SAMSUNG HD300LD, ATA DISK drive
[    7.840000] hdb: CD-RW 52X24, ATAPI CD/DVD-ROM drive
[    7.896000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[    7.904000] Probing IDE interface ide1...
[    8.268000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00004c0100003ee0]
[    8.480000] hda: max request size: 512KiB
[    8.480000] hda: 586072368 sectors (300069 MB) w/8192KiB Cache, CHS=36481/255/63, UDMA(100)
[    8.480000] hda: cache flushes supported
[    8.480000]  hda: hda1 hda2 hda3
[    8.496000] hdb: ATAPI 52X CD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
[    8.496000] Uniform CD-ROM driver Revision: 3.20
[    8.540000] ieee1394: Host added: ID:BUS[1-00:1023]  GUID[00016c20001b7642]
[    8.788000] Attempting manual resume
[    8.788000] swsusp: Resume From Partition 3:1
[    8.788000] PM: Checking swsusp image.
[    8.788000] PM: Resume from disk failed.
[    8.804000] ReiserFS: hda3: found reiserfs format "3.6" with standard journal
[    8.804000] ReiserFS: hda3: using ordered data mode
[    8.812000] ieee1394: Host added: ID:BUS[2-00:1023]  GUID[00023c002000666d]
[    8.824000] ReiserFS: hda3: journal params: device hda3, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[    8.824000] ReiserFS: hda3: checking transaction log (hda3)
[    8.868000] ReiserFS: hda3: Using r5 hash to sort names
[   18.096000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   18.100000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   18.344000] Linux agpgart interface v0.102 (c) Dave Jones
[   18.548000] i2c-adapter i2c-0: nForce2 SMBus adapter at 0xfc00
[   18.548000] i2c-adapter i2c-1: nForce2 SMBus adapter at 0xf800
[   18.612000] nvidia: module license 'NVIDIA' taints kernel.
[   18.876000] ACPI: PCI Interrupt 0000:00:05.0[A] -> Link [APC7] -> GSI 16 (level, low) -> IRQ 16
[   18.876000] PCI: Setting latency timer of device 0000:00:05.0 to 64
[   18.880000] NVRM: loading NVIDIA UNIX x86 Kernel Module  100.14.19  Wed Sep 12 14:12:24 PDT 2007
[   19.232000] Linux video capture interface: v2.00
[   19.388000] gameport: EMU10K1 is pci0000:04:07.1/gameport0, io 0xb800, speed 59659kHz
[   19.388000] input: PC Speaker as /class/input/input2
[   19.520000] input: ImPS/2 Generic Wheel Mouse as /class/input/input3
[   19.528000] ivtv:  ==================== START INIT IVTV ====================
[   19.528000] ivtv:  version 1.0.0 (2.6.22-14-generic SMP mod_unload 586 ) loading
[   19.532000] ivtv0: Autodetected Hauppauge card (cx23416 based)
[   19.532000] ACPI: PCI Interrupt 0000:04:08.0[A] -> Link [APC2] -> GSI 17 (level, low) -> IRQ 22
[   19.532000] ivtv0: Unreasonably low latency timer, setting to 64 (was 32)
[   20.204000] ivtv0: loaded v4l-cx2341x-enc.fw firmware (4153553032 bytes)
[   20.420000] ivtv0: Encoder revision: 0x02050032
[   20.420000] ivtv0: Recommended firmware version is 0x02060039.
[   20.480000] tveeprom 2-0050: Hauppauge model 26132, rev F1B2, serial# 9898500
[   20.480000] tveeprom 2-0050: tuner model is TCL M2523_5N_E (idx 112, type 50)
[   20.480000] tveeprom 2-0050: TV standards NTSC(M) (eeprom 0x08)
[   20.480000] tveeprom 2-0050: audio processor is CX25841 (idx 35)
[   20.480000] tveeprom 2-0050: decoder processor is CX25841 (idx 28)
[   20.480000] tveeprom 2-0050: has no radio, has IR receiver, has IR transmitter
[   20.480000] ivtv0: Autodetected Hauppauge WinTV PVR-150
[   20.480000] ivtv0: reopen i2c bus for IR-blaster support
[   20.568000] tuner 2-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[   20.776000] cx25840 2-0044: cx25841-24 found @ 0x88 (ivtv i2c driver #0)
[   24.472000] cx25840 2-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
[   24.580000] wm8775 2-001b: chip found @ 0x36 (ivtv i2c driver #0)
[   24.632000] tuner 2-0061: type set to 50 (TCL 2002N)
[   24.952000] ivtv0: Registered device video0 for encoder MPEG (4 MB)
[   24.952000] ivtv0: Registered device video32 for encoder YUV (2 MB)
[   24.952000] ivtv0: Registered device vbi0 for encoder VBI (1 MB)
[   24.952000] ivtv0: Registered device video24 for encoder PCM audio (1 MB)
[   24.976000] ivtv0: Initialized Hauppauge WinTV PVR-150, card #0
[   24.976000] ivtv:  ====================  END INIT IVTV  ====================
[   24.976000] ACPI: PCI Interrupt Link [APC1] enabled at IRQ 16
[   24.976000] ACPI: PCI Interrupt 0000:04:07.0[A] -> Link [APC1] -> GSI 16 (level, low) -> IRQ 16
[COLOR="Magenta"][   24.976000] ALSA /usr/src/modules/alsa-driver/pci/emu10k1/emu10k1_main.c:1555: vendor=0x1102, device=0x4, subsystem_vendor_id=0x511102, subsystem_id=0x51
[   24.976000] ALSA /usr/src/modules/alsa-driver/pci/emu10k1/emu10k1_main.c:1580: Sound card name=Audigy 1 [SB0090][/COLOR]
[   25.688000] lp: driver loaded but no devices found
[   25.780000] Adding 2048248k swap on /dev/hda1.  Priority:-1 extents:1 across:2048248k
[   49.084000] No dock devices found.
[   49.168000] input: Power Button (FF) as /class/input/input4
[   49.168000] ACPI: Power Button (FF) [PWRF]
[   49.168000] input: Power Button (CM) as /class/input/input5
[   49.172000] ACPI: Power Button (CM) [PWRB]
[   49.724000] powernow-k8: Found 2 AMD Athlon(tm) 64 X2 Dual Core Processor 3800+ processors (version 2.00.00)
[   49.724000] powernow-k8:    0 : fid 0xc (2000 MHz), vid 0x8
[   49.724000] powernow-k8:    1 : fid 0xa (1800 MHz), vid 0xa
[   49.724000] powernow-k8:    2 : fid 0x2 (1000 MHz), vid 0x12
[   49.824000] Clocksource tsc unstable (delta = 95237417 ns)
[   50.956000] NET: Registered protocol family 10
[   50.956000] lo: Disabled Privacy Extensions
[   51.588000] ppdev: user-space parallel port driver
[   51.748000] audit(1200776547.836:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=5404 profile="/usr/sbin/cupsd"
[   52.640000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   52.640000] apm: disabled - APM is not SMP safe.
[   58.848000] Installing knfsd (copyright (C) 1996 [email]okir@monad.swb.de[/email]).
[   58.980000] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[   58.980000] NFSD: starting 90-second grace period
[   60.052000] Failure registering capabilities with primary security module.
[   60.316000] Bluetooth: Core ver 2.11
[   60.316000] NET: Registered protocol family 31
[   60.316000] Bluetooth: HCI device and connection manager initialized
[   60.316000] Bluetooth: HCI socket layer initialized
[   60.332000] Bluetooth: L2CAP ver 2.8
[   60.332000] Bluetooth: L2CAP socket layer initialized
[   60.412000] Bluetooth: RFCOMM socket layer initialized
[   60.412000] Bluetooth: RFCOMM TTY layer initialized
[   60.412000] Bluetooth: RFCOMM ver 1.8
[   61.212000] lirc_dev: IR Remote Control driver registered, at major 61 
[   61.368000] bttv: driver version 0.9.17 loaded
[   61.368000] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   61.528000] cx2388x v4l2 driver version 0.0.6 loaded
[   64.648000] NET: Registered protocol family 17
[   77.616000] eth0: no IPv6 routers present

---

### Post by xeth_delta on 2008-01-19
card seems to be recognized. Let's see if the modules / drivers are loaded:
```
lsmod | grep -i snd
```

[EDIT] Please also post the output of
```
sudo lshw -C audio
```
or
```
sudo lshw -C sound
```

---

### Post by curtis1552 on 2008-01-19
lsmod | grep -i snd

snd_emu10k1_synth       9856  0 
snd_emux_synth         39808  1 snd_emu10k1_synth
snd_seq_virmidi         8320  1 snd_emux_synth
snd_seq_midi_emul       8064  1 snd_emux_synth
snd_emu10k1           145056  2 snd_emu10k1_synth
snd_seq_dummy           4868  0 
snd_seq_oss            35712  0 
snd_seq_midi           10752  0 
snd_seq_midi_event      8576  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
snd_seq                58608  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_rawmidi            27392  3 snd_seq_virmidi,snd_emu10k1,snd_seq_midi
snd_ac97_codec        102180  1 snd_emu10k1
snd_pcm_oss            53632  0 
snd_mixer_oss          18304  1 snd_pcm_oss
snd_pcm                88836  4 snd_emu10k1,snd_ac97_codec,snd_pcm_oss
snd_seq_device          9740  8 snd_emu10k1_synth,snd_emux_synth,snd_emu10k1,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi
snd_timer              26116  3 snd_emu10k1,snd_seq,snd_pcm
snd_util_mem            6400  2 snd_emux_synth,snd_emu10k1
snd_hwdep              10884  2 snd_emux_synth,snd_emu10k1
ac97_bus                3456  1 snd_ac97_codec
snd_page_alloc         11528  2 snd_emu10k1,snd_pcm
snd                    64012  22 snd_emu10k1_synth,snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_emu10k1,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event,snd_seq,snd_rawmidi,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_device,snd_timer,snd_util_mem,snd_hwdep,snd_page_alloc
soundcore               8800  1 snd

---

### Post by xeth_delta on 2008-01-19
modules loaded...
Please see the edit in my previous post. Do you know the complete exact model name of the card? Maybe some useful information can be found here: [http://www.alsa-project.org/main/index.php/Matrix:Vendor-Creative_Labs]("http://www.alsa-project.org/main/index.php/Matrix:Vendor-Creative_Labs")

---

### Post by curtis1552 on 2008-01-19
No output when audio is used

sudo lshw -C sound

  *-multimedia:0          
       description: Multimedia audio controller
       product: SB Audigy
       vendor: Creative Labs
       physical id: 7
       bus info: pci@0000:04:07.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=EMU10K1_Audigy latency=32 maxlatency=20 mingnt=2 module=snd_emu10k1
  *-multimedia:1
       description: Multimedia video controller
       product: iTVC16 (CX23416) MPEG-2 Encoder
       vendor: Internext Compression Inc
       physical id: 8
       bus info: pci@0000:04:08.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=ivtv latency=64 maxlatency=8 mingnt=128 module=ivtv

---

### Post by xeth_delta on 2008-01-19
> **curtis1552 said:**
> No output when audio is used

sudo lshw -C sound

  *-multimedia:0          
       description: Multimedia audio controller
       product: SB Audigy
       vendor: Creative Labs
       physical id: 7
       bus info: pci@0000:04:07.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=EMU10K1_Audigy latency=32 maxlatency=20 mingnt=2 module=snd_emu10k1
  *-multimedia:1
       description: Multimedia video controller
       product: iTVC16 (CX23416) MPEG-2 Encoder
       vendor: Internext Compression Inc
       physical id: 8
       bus info: pci@0000:04:08.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=ivtv latency=64 maxlatency=8 mingnt=128 module=ivtv

No output, but are there any errors? I wonder if channels could just be muted. Please run alsamixer, unmute the eventually muted channels. What program are you trying to play audio with?

---

### Post by Yellow Pasque on 2008-01-19
One other solution I offer to everyone is to try OSS4 when they've exhausted all options with ALSA. See my sig when/if you're interested.

---

### Post by curtis1552 on 2008-01-19
lshw- -C audio
It ran and gave no errors and then next command line.

I checked Alsamixer when i did the tutorial.
I've tried mythTV Amarok, VLC, and Kaffene (and I set it to use alsa)

[http://hardware4linux.info/component/4582/](http://hardware4linux.info/component/4582/)
Manufacturer	Creative Labs
Model	SB0090 Audigy Player/OEM
Bus	pci
Type	Multimedia audio controller
Id	1102
Info2	0004
Info3	1102
Info4	0053
Module supporting this component
    * EMU10K1_Audigy


However now Alsa has a EMU10k2 (more specifically for my card), which had not been there before and is not available when I run $ sudo dpkg-reconfigure alsa-source
[http://www.alsa-project.org/main/index.php/Matrix:Vendor-Creative_Labs](http://www.alsa-project.org/main/index.php/Matrix:Vendor-Creative_Labs)

---

### Post by xeth_delta on 2008-01-19
> **curtis1552 said:**
> lshw- -C audio
It ran and gave no errors and then next command line.

I checked Alsamixer when i did the tutorial.
I've tried mythTV Amarok, VLC, and Kaffene (and I set it to use alsa)

[http://hardware4linux.info/component/4582/](http://hardware4linux.info/component/4582/)
Manufacturer	Creative Labs
Model	SB0090 Audigy Player/OEM
Bus	pci
Type	Multimedia audio controller
Id	1102
Info2	0004
Info3	1102
Info4	0053
Module supporting this component
    * EMU10K1_Audigy


However now Alsa has a EMU10k2 (more specifically for my card), which had not been there before and is not available when I run $ sudo dpkg-reconfigure alsa-source
[http://www.alsa-project.org/main/index.php/Matrix:Vendor-Creative_Labs](http://www.alsa-project.org/main/index.php/Matrix:Vendor-Creative_Labs)

Is your correct driver in the new alsa sources? You could try downloading the latest sources and compiling the drivers yourself, it is not very difficult, it would take approximately 5-10 minutes. I think there are instructions in the guide you saw. Otherwise, let us know and we'll try to help you.

---

### Post by curtis1552 on 2008-01-19
when i try to download them it says that i have the most current files.

---

### Post by Yellow Pasque on 2008-01-19
Are you still using Ubuntu 5.10? If so, xeth_delta is suggesting downloading ALSA 1.0.15 from [http://www.alsa-project.org/main/index.php/Main_Page](http://www.alsa-project.org/main/index.php/Main_Page) and building the package yourself.

---

### Post by xeth_delta on 2008-01-19
> **Temüjin said:**
> Are you still using Ubuntu 5.10? If so, xeth_delta is suggesting downloading ALSA 1.0.15 from [http://www.alsa-project.org/main/index.php/Main_Page](http://www.alsa-project.org/main/index.php/Main_Page) and building the package yourself.

Exactly :)

---

### Post by MountainX on 2008-01-19
> **xeth_delta said:**
> Issue a
```
sudo /etc/init.t/alsasound restart
```
then call a "dmesg". What are the last output lines like? the ones concerning your card.

I'm working on a no-sound issue too. I was trying to follow these steps. I found out that I do not have a /etc/init.t/alsasound but I do have /etc/init.t/alsa-utils. 

Here's the output from lsmod | grep -i snd
```

snd_intel8x0           40104  3 
snd_ac97_codec        122200  1 snd_intel8x0
snd_mpu401             11944  0 
snd_mpu401_uart        11008  1 snd_mpu401
ac97_bus                4096  1 snd_ac97_codec
snd_pcm_oss            50048  0 
snd_mixer_oss          20096  1 snd_pcm_oss
snd_seq_dummy           5380  0 
snd_seq_oss            36864  0 
snd_pcm                94344  4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_midi           11008  0 
snd_seq_midi_event      9984  2 snd_seq_oss,snd_seq_midi
snd_seq                62496  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              27272  3 snd_pcm,snd_seq
snd_rawmidi            29824  2 snd_mpu401_uart,snd_seq_midi
snd_seq_device         10260  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi
snd                    69288  16 snd_intel8x0,snd_ac97_codec,snd_mpu401,snd_mpu401_uart,snd_pcm_oss,snd_mixer_oss,snd_seq_oss,snd_pcm,snd_seq,snd_timer,snd_rawmidi,snd_seq_device
soundcore              10272  1 snd
snd_page_alloc         12560  2 snd_intel8x0,snd_pcm

```

My sound worked until I upgraded my nVidia drivers via Envy. I'm on the 64 bit version of Ubuntu 7.10.

---

### Post by curtis1552 on 2008-01-20
Let's compre my grep and see how were both messed up.
 lsmod | grep -i snd
snd_emu10k1_synth       9856  0 
snd_emux_synth           39808  1 snd_emu10k1_synth
snd_seq_virmidi              8320  1 snd_emux_synth
snd_seq_midi_emul         8064  1 snd_emux_synth
snd_emu10k1              145056  2 snd_emu10k1_synth
snd_ac97_codec        102180  1 snd_emu10k1
ac97_bus                        3456  1 snd_ac97_codec
snd_pcm_oss               53632  0 
snd_mixer_oss             18304  1 snd_pcm_oss
snd_pcm                       88836  3 snd_emu10k1,snd_ac97_codec,snd_pcm_oss
snd_page_alloc            11528  2 snd_emu10k1,snd_pcm
snd_util_mem                  6400  2 snd_emux_synth,snd_emu10k1
snd_hwdep                  10884  2 snd_emux_synth,snd_emu10k1
snd_seq_dummy            4868  0 
snd_seq_oss               35712  0 
snd_seq_midi               10752  0 
snd_rawmidi                27392  3 snd_seq_virmidi,snd_emu10k1,snd_seq_midi
snd_seq_midi_event      8576  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
snd_seq                       58608  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer                     26116  3 snd_emu10k1,snd_pcm,snd_seq
snd_seq_device           9740  8 snd_emu10k1_synth,snd_emux_synth,snd_emu10k1,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                             64012  22 snd_emu10k1_synth,snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_emu10k1,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_page_alloc,snd_util_mem,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq_midi_event,snd_seq,snd_timer,snd_seq_device
soundcore                     8800  1 snd



MountainX
Have you seen these:
>     * webbca01 figured out how to get AC'97 work with the help of the second last post here and this post. Basically, if you have an intel8x0 module, you can get AC'97 working by
      sudo nano /etc/modprobe.d/alsa-base
      and adding this as the last line:
      "options snd-intel8x0 ac97_quirk=3"


[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

the thread linked to in that post is:
[http://ubuntuforums.org/showthread.php?t=14989&highlight=ac97_quirk](http://ubuntuforums.org/showthread.php?t=14989&highlight=ac97_quirk)

---

### Post by MountainX on 2008-01-20
> **curtis1552 said:**
> 

MountainX
Have you seen these:

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

the thread linked to in that post is:
[http://ubuntuforums.org/showthread.php?t=14989&highlight=ac97_quirk](http://ubuntuforums.org/showthread.php?t=14989&highlight=ac97_quirk)

Thank you. I have been using the link to the Comprehensive Sound Problem Solving guide. That's a great thread. Unfortunately, it hasn't helped me solve my problem.

My issue seems to be different. I had sound until I installed the latest nVidia drivers using Envy. I have the AMD64 version of Gutsy. 

I tried the quirk=3 option, but it didn't work for me. My system is probably too screwed up now. After I lost sound I have tried everything, including OSS. I probably just need to uninstall the nVidia video driver and undo all the other changes I've made. (Maybe I'll just reinstall Ubuntu.)

---

### Post by xeth_delta on 2008-01-20
> **MountainX said:**
> Thank you. I have been using the link to the Comprehensive Sound Problem Solving guide. That's a great thread. Unfortunately, it hasn't helped me solve my problem.

My issue seems to be different. I had sound until I installed the latest nVidia drivers using Envy. I have the AMD64 version of Gutsy. 

I tried the quirk=3 option, but it didn't work for me. My system is probably too screwed up now. After I lost sound I have tried everything, including OSS. I probably just need to uninstall the nVidia video driver and undo all the other changes I've made. (Maybe I'll just reinstall Ubuntu.)

Certainly sounds odd that a video driver installtion would bring down the sound system, but eh, these things can happen. Does Envy tinker with sound drivers, too? I have never used it.

What is the output of "dmesg | grep -i alsa"?

---

### Post by MountainX on 2008-01-20
> **xeth_delta said:**
> 
What is the output of "dmesg | grep -i alsa"?

I can't say right now because I deleted my partition and I'm installing Ubuntu again from scratch. The first thing I am going to try on a clean install is using Envy again to see what happens.

---

### Post by xeth_delta on 2008-01-20
> **MountainX said:**
> I can't say right now because I deleted my partition and I'm installing Ubuntu again from scratch. The first thing I am going to try on a clean install is using Envy again to see what happens.

You should make a backup of several files before that, in order to see what is changed. For instance "/etc/modprobe.d/alsa-base", "/etc/default/alsa", "/etc/init.d/alsa-utils", "/etc/udev/rules.d/85-alsa.rules", "/etc/rc0.d/K50alsa-utils", "/etc/rc6.d/K50alsa-utils".

---

### Post by MountainX on 2008-01-20
> **xeth_delta said:**
> You should make a backup of several files before that, in order to see what is changed. For instance "/etc/modprobe.d/alsa-base", "/etc/default/alsa", "/etc/init.d/alsa-utils", "/etc/udev/rules.d/85-alsa.rules", "/etc/rc0.d/K50alsa-utils", "/etc/rc6.d/K50alsa-utils".

Thanks for the tips. Unfortunately, I'm already finished, but I'll keep this list of files for future reference.

After the fresh install I had sound, and after installing the latest nVidia drivers with Envy, I still have sound. :)

---

### Post by xeth_delta on 2008-01-20
That is great news!
Good luck!

---

### Post by curtis1552 on 2008-01-20
Sadly I have no such luck.
I'll try OSS but it might take me awhile to get to it.

---

### Post by xeth_delta on 2008-01-20
> **curtis1552 said:**
> Sadly I have no such luck.
I'll try OSS but it might take me awhile to get to it.

Did you also try compiling the latest alsa drivers yourself? [http://www.alsa-project.org/main/index.php/Download]("http://www.alsa-project.org/main/index.php/Download")

---

### Post by curtis1552 on 2008-03-25
Hey! I found the fix!
I did what i shouldn't have and read the guides which said to unmute all the options and turn the volume up. This MESSED IT UP! I Enabled the digital out - IEC958 (or something similar) - which in turn diables the analog out; hence my lack of sound. I muted these channels and was able to hear sound using  $ aplay *.wav
Thanks to all for trying to help me out.

---

