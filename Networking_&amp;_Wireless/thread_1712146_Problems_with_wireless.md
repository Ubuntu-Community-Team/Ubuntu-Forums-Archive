---
title: "Problems with wireless"
date: 2011-03-22
forum: Networking &amp; Wireless
---

### Post by Hrexen on 2011-03-22
My laptop is Gateway M-6335 and I have problems with wireless drivers. I couldn't find any drivers for it. I searched in Software Centre and tried to google it but it didn't help. I have also problems with Bluetooth driver, but it's an other story :)

P.S. I'm using Ubuntu 10.10.

Thanks for assistance.

---

### Post by TBABill on 2011-03-22
Can you run these commands in a terminal and post their outputs back here so we know what hardware you are trying to get going?
 
```
lspci
``` That's LSPCI in lowercase
 
```
sudo lshw -C network
```

---

### Post by Hrexen on 2011-03-22
> **TBABill said:**
> Can you run these commands in a terminal and post their outputs back here so we know what hardware you are trying to get going?
 
```
lspci
``` That's LSPCI in lowercase
 
```
sudo lshw -C network
```

```
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 04)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 04)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 04)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 04)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f4)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 04)
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8187SE Wireless LAN Controller (rev 22)
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)
```and response for second

```
  *-network               
       description: Wireless interface
       product: RTL8187SE Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 22
       serial: 00:16:44:e4:59:64
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=r8180 latency=0 multicast=yes wireless=802.11b/g
       resources: irq:16 ioport:2000(size=256) memory:f4000000-f4003fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 01
       serial: 00:e0:b8:fa:d4:3f
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=10.1.1.1 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:43 ioport:4000(size=256) memory:f8200000-f8200fff memory:80000000-8001ffff

```

---

### Post by Hippytaff on 2011-03-22
try```
rfkill unblock all
``` always worth a punt.and ```
ifconfig wlan0 up
```
 
If you have not luck with that, it would be worth seeing the output of ```
lsmod | grep -i r8180
```
 
Also if you do ```
 sudo apt-get update
``` that might help and check System -> Administration -> Additional Drivers. to see if there are additional drivers to download.

---

### Post by Hrexen on 2011-03-22
> **Hippytaff said:**
> try```
rfkill unblock all
``` always worth a punt.and ```
ifconfig wlan0 up
```If you have not luck with that, it would be worth seeing the output of ```
lsmod | grep -i r8180
```Also if you do ```
 sudo apt-get update
``` that might help and check System -> Administration -> Additional Drivers. to see if there are additional drivers to download.

ifconfig wlan0 returns ```
SIOCSIFFLAGS: Permission denied
```lsmod | grep -i r8180 returns nothing.

:-|

---

### Post by TBABill on 2011-03-22
Can you post the full output of lsmod?

---

### Post by Hrexen on 2011-03-22
```
Module                  Size  Used by
binfmt_misc             6599  1 
parport_pc             26058  0 
ppdev                   5556  0 
snd_hda_codec_idt      54919  1 
joydev                  8767  0 
snd_hda_intel          22235  4 
i915                  295435  4 
snd_hda_codec          87552  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71475  3 snd_hda_intel,snd_hda_codec
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
drm_kms_helper         30200  1 i915
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
usbhid                 36882  0 
hid                    67742  1 usbhid
uvcvideo               55847  0 
drm                   168060  4 i915,drm_kms_helper
videodev               43098  1 uvcvideo
v4l1_compat            13359  2 uvcvideo,videodev
snd                    49038  16 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
intel_agp              26566  2 i915
psmouse                59033  0 
i2c_algo_bit            5168  1 i915
video                  18712  1 i915
soundcore                880  1 snd
r8187se               150056  0 
eeprom_93cx6            1345  1 r8187se
serio_raw               4022  0 
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
output                  1883  1 video
agpgart                32011  2 drm,intel_agp
lp                      7342  0 
parport                31492  3 parport_pc,ppdev,lp
usb_storage            40204  0 
ahci                   19198  1 
r8169                  36521  0 
libahci                21728  1 ahci
mii                     4425  1 r8169

```

---

### Post by Hippytaff on 2011-03-22
> r8187se               150056  0 eeprom_93cx6            1345  1 r8187seLooks like the driver is loading, but not sure if its loading correctly. Reinstall it you think TBABILL?

Have you tried the proprietry driver 

what does dmesg look like?

Edit -> I notice there are a few bugs with this driver - have you thought of using th ewindows driver with [Ndisgtk]("http://linuxappfinder.com/package/ndisgtk")?

If not maybe look into it. If you decide to try it you will need to download and install ndisgtk thus-
```
sudo apt-get install ndisgtk
```

---

### Post by Hrexen on 2011-03-22
It's a bit long ;)

```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.35-28-generic (buildd@roseapple) (gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu5) ) #49-Ubuntu SMP Tue Mar 1 14:40:58 UTC 2011 (Ubuntu 2.6.35-28.49-generic 2.6.35.11)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007f6d0000 (usable)
[    0.000000]  BIOS-e820: 000000007f6d0000 - 000000007f6e3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007f6e3000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] Notice: NX (Execute Disable) protection cannot be enabled: non-PAE kernel!
[    0.000000] DMI 2.4 present.
[    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 update range: 0000000000000000 - 0000000000001000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x7f6d0 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-DFFFF uncachable
[    0.000000]   E0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 07F700000 mask FFFF00000 uncachable
[    0.000000]   2 base 07F800000 mask FFF800000 uncachable
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009f800 (usable)
[    0.000000]  modified: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000007f6d0000 (usable)
[    0.000000]  modified: 000000007f6d0000 - 000000007f6e3000 (ACPI NVS)
[    0.000000]  modified: 000000007f6e3000 - 0000000080000000 (reserved)
[    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  modified: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  modified: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  modified: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] found SMP MP-table at [c00f68d0] f68d0
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 15000-1a000
[    0.000000] RAMDISK: 375a8000 - 37ff0000
[    0.000000] Allocated new RAMDISK: 009a9000 - 013f0608
[    0.000000] Move RAMDISK from 00000000375a8000 - 0000000037fef607 to 009a9000 - 013f0607
[    0.000000] ACPI: RSDP 000f6830 00024 (v02 PTLTD )
[    0.000000] ACPI: XSDT 7f6d61a0 00084 (v01 ACRSYS ACRPRDCT 20080408 ANNI 00000000)
[    0.000000] ACPI: FACP 7f6dfbd2 000F4 (v03 GATEWA SYSTEM   20080408 ALAN 00000001)
[    0.000000] ACPI: DSDT 7f6d73f0 0876E (v02 GATEWA SYSTEM   20080408 INTL 20061109)
[    0.000000] ACPI: FACS 7f6e2fc0 00040
[    0.000000] ACPI: APIC 7f6dfcc6 00068 (v01 GATEWA SYSTEM   20080408 LOHR 0000005A)
[    0.000000] ACPI: HPET 7f6dfd2e 00038 (v01 GATEWA SYSTEM   20080408 LOHR 0000005A)
[    0.000000] ACPI: MCFG 7f6dfd66 0003C (v01 GATEWA SYSTEM   20080408 LOHR 0000005A)
[    0.000000] ACPI: TCPA 7f6dfda2 00032 (v01 GATEWA SYSTEM   20080408      00005A52)
[    0.000000] ACPI: TMOR 7f6dfdd4 00026 (v01 GATEWA SYSTEM   20080408 PTL  00000003)
[    0.000000] ACPI: SLIC 7f6dfdfa 00176 (v01 ACRSYS ACRPRDCT 00000001 ANNI 00000001)
[    0.000000] ACPI: APIC 7f6dff70 00068 (v01 GATEWA SYSTEM   20080408  LTP 00000000)
[    0.000000] ACPI: BOOT 7f6dffd8 00028 (v01 GATEWA SYSTEM   20080408  LTP 00000001)
[    0.000000] ACPI: SSDT 7f6d67e0 0025F (v01  PmRef  Cpu0Tst 00003000 INTL 20061109)
[    0.000000] ACPI: SSDT 7f6d673a 000A6 (v01  PmRef  Cpu1Tst 00003000 INTL 20061109)
[    0.000000] ACPI: SSDT 7f6d6224 00516 (v01  PmRef    CpuPm 00003000 INTL 20061109)
[    0.000000] ACPI: BIOS bug: multiple APIC/MADT found, using 0
[    0.000000] ACPI: If "acpi_apic_instance=2" works better, notify linux-acpi@vger.kernel.org
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 1150MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0007f6d0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0007f6d0
[    0.000000] On node 0 totalpages: 521823
[    0.000000] free_area_init_node: node 0, pgdat c0801fc0, node_mem_map c13f2200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2302 pages used for memmap
[    0.000000]   HighMem zone: 292308 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] early_res array is doubled to 64 at [16000 - 167ff]
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000dc000
[    0.000000] PM: Registered nosave memory: 00000000000dc000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 80000000:60000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @c2400000 s36416 r0 d20928 u2097152
[    0.000000] pcpu-alloc: s36416 r0 d20928 u2097152 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 1 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 517745
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-28-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 10438400 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Subtract (52 early reservations)
[    0.000000]   #1 [0000001000 - 0000002000]   EX TRAMPOLINE
[    0.000000]   #2 [0000100000 - 00009a4adc]   TEXT DATA BSS
[    0.000000]   #3 [00009a5000 - 00009a8278]             BRK
[    0.000000]   #4 [00000f68e0 - 0000100000]   BIOS reserved
[    0.000000]   #5 [00000f68d0 - 00000f68e0]    MP-table mpf
[    0.000000]   #6 [000009f800 - 000009fd71]   BIOS reserved
[    0.000000]   #7 [000009feed - 00000f68d0]   BIOS reserved
[    0.000000]   #8 [000009fd71 - 000009feed]    MP-table mpc
[    0.000000]   #9 [0000010000 - 0000011000]      TRAMPOLINE
[    0.000000]   #10 [0000011000 - 0000015000]     ACPI WAKEUP
[    0.000000]   #11 [0000015000 - 0000016000]         PGTABLE
[    0.000000]   #12 [00009a9000 - 00013f1000]     NEW RAMDISK
[    0.000000]   #13 [00013f1000 - 00013f2000]         BOOTMEM
[    0.000000]   #14 [00013f2000 - 00023e2000]         BOOTMEM
[    0.000000]   #15 [00023e2000 - 00023e2004]         BOOTMEM
[    0.000000]   #16 [00023e2040 - 00023e2100]         BOOTMEM
[    0.000000]   #17 [00023e2100 - 00023e2154]         BOOTMEM
[    0.000000]   #18 [00023e2180 - 00023e5180]         BOOTMEM
[    0.000000]   #19 [00023e5180 - 00023e51ec]         BOOTMEM
[    0.000000]   #20 [00023e5200 - 00023eb200]         BOOTMEM
[    0.000000]   #21 [00023eb200 - 00023eb225]         BOOTMEM
[    0.000000]   #22 [00023eb240 - 00023eb267]         BOOTMEM
[    0.000000]   #23 [00023eb280 - 00023eb408]         BOOTMEM
[    0.000000]   #24 [00023eb440 - 00023eb480]         BOOTMEM
[    0.000000]   #25 [00023eb480 - 00023eb4c0]         BOOTMEM
[    0.000000]   #26 [00023eb4c0 - 00023eb500]         BOOTMEM
[    0.000000]   #27 [00023eb500 - 00023eb540]         BOOTMEM
[    0.000000]   #28 [00023eb540 - 00023eb580]         BOOTMEM
[    0.000000]   #29 [00023eb580 - 00023eb5c0]         BOOTMEM
[    0.000000]   #30 [00023eb5c0 - 00023eb600]         BOOTMEM
[    0.000000]   #31 [00023eb600 - 00023eb640]         BOOTMEM
[    0.000000]   #32 [00023eb640 - 00023eb680]         BOOTMEM
[    0.000000]   #33 [00023eb680 - 00023eb6c0]         BOOTMEM
[    0.000000]   #34 [00023eb6c0 - 00023eb700]         BOOTMEM
[    0.000000]   #35 [00023eb700 - 00023eb740]         BOOTMEM
[    0.000000]   #36 [00023eb740 - 00023eb780]         BOOTMEM
[    0.000000]   #37 [00023eb780 - 00023eb790]         BOOTMEM
[    0.000000]   #38 [00023eb7c0 - 00023eb827]         BOOTMEM
[    0.000000]   #39 [00023eb840 - 00023eb8a7]         BOOTMEM
[    0.000000]   #40 [0002400000 - 000240e000]         BOOTMEM
[    0.000000]   #41 [0002600000 - 000260e000]         BOOTMEM
[    0.000000]   #42 [00023ed8c0 - 00023ed8c4]         BOOTMEM
[    0.000000]   #43 [00023ed900 - 00023ed904]         BOOTMEM
[    0.000000]   #44 [00023ed940 - 00023ed948]         BOOTMEM
[    0.000000]   #45 [00023ed980 - 00023ed988]         BOOTMEM
[    0.000000]   #46 [00023ed9c0 - 00023eda68]         BOOTMEM
[    0.000000]   #47 [00023eda80 - 00023edae8]         BOOTMEM
[    0.000000]   #48 [00023edb00 - 00023f1b00]         BOOTMEM
[    0.000000]   #49 [000240e000 - 000248e000]         BOOTMEM
[    0.000000]   #50 [000248e000 - 00024ce000]         BOOTMEM
[    0.000000]   #51 [000260e000 - 0003002700]         BOOTMEM
[    0.000000] Initializing HighMem for node 0 (000377fe:0007f6d0)
[    0.000000] Memory: 2040412k/2087744k available (4935k kernel code, 46880k reserved, 2337k data, 688k init, 1178440k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc081b000 - 0xc08c7000   ( 688 kB)
[    0.000000]       .data : 0xc05d1fde - 0xc081a7a8   (2337 kB)
[    0.000000]       .text : 0xc0100000 - 0xc05d1fde   (4935 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU-based detection of stalled CPUs is disabled.
[    0.000000]     Verbose stalled-CPUs detection is disabled.
[    0.000000] NR_IRQS:2304 nr_irqs:512
[    0.000000] Extended CMOS year: 2000
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1862.225 MHz processor.
[    0.004006] Calibrating delay loop (skipped), value calculated using timer frequency.. 3724.45 BogoMIPS (lpj=7448900)
[    0.004012] pid_max: default: 32768 minimum: 301
[    0.004035] Security Framework initialized
[    0.004056] AppArmor: AppArmor initialized
[    0.004058] Yama: becoming mindful.
[    0.004121] Mount-cache hash table entries: 512
[    0.004278] Initializing cgroup subsys ns
[    0.004283] Initializing cgroup subsys cpuacct
[    0.004288] Initializing cgroup subsys memory
[    0.004298] Initializing cgroup subsys devices
[    0.004301] Initializing cgroup subsys freezer
[    0.004304] Initializing cgroup subsys net_cls
[    0.004337] CPU: Physical Processor ID: 0
[    0.004339] CPU: Processor Core ID: 0
[    0.004342] mce: CPU supports 6 MCE banks
[    0.004351] CPU0: Thermal monitoring handled by SMI
[    0.004356] using mwait in idle threads.
[    0.004364] Performance Events: PEBS fmt0+, Core2 events, Intel PMU driver.
[    0.004371] PEBS disabled due to CPU errata.
[    0.004379] ... version:                2
[    0.004381] ... bit width:              40
[    0.004383] ... generic registers:      2
[    0.004385] ... value mask:             000000ffffffffff
[    0.004388] ... max period:             000000007fffffff
[    0.004390] ... fixed-purpose events:   3
[    0.004392] ... event mask:             0000000700000003
[    0.009326] ACPI: Core revision 20100428
[    0.024011] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.024017] ftrace: allocating 21762 entries in 43 pages
[    0.028068] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.028437] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.069420] CPU0: Intel(R) Pentium(R) Dual  CPU  T2390  @ 1.86GHz stepping 0d
[    0.072000] Booting Node   0, Processors  #1 Ok.
[    0.008000] Initializing CPU#1
[    0.008000] CPU1: Thermal monitoring handled by SMI
[    0.160017] Brought up 2 CPUs
[    0.160021] Total of 2 processors activated (7448.83 BogoMIPS).
[    0.160482] devtmpfs: initialized
[    0.161115] regulator: core version 0.5
[    0.161152] Time: 20:18:29  Date: 03/22/11
[    0.161200] NET: Registered protocol family 16
[    0.161227] Trying to unpack rootfs image as initramfs...
[    0.161353] EISA bus registered
[    0.161363] ACPI: bus type pci registered
[    0.161455] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.161459] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.161462] PCI: Using MMCONFIG for extended config space
[    0.161464] PCI: Using configuration type 1 for base access
[    0.168234] bio: create slab <bio-0> at 0
[    0.170437] ACPI: EC: Look up EC in DSDT
[    0.175722] ACPI: BIOS _OSI(Linux) query ignored
[    0.177041] ACPI: SSDT 7f6d70ae 0027A (v01  PmRef  Cpu0Ist 00003000 INTL 20061109)
[    0.177653] ACPI: Dynamic OEM Table Load:
[    0.177657] ACPI: SSDT (null) 0027A (v01  PmRef  Cpu0Ist 00003000 INTL 20061109)
[    0.178038] ACPI: SSDT 7f6d6a3f 005EA (v01  PmRef  Cpu0Cst 00003001 INTL 20061109)
[    0.178622] ACPI: Dynamic OEM Table Load:
[    0.178626] ACPI: SSDT (null) 005EA (v01  PmRef  Cpu0Cst 00003001 INTL 20061109)
[    0.179139] ACPI: SSDT 7f6d7328 000C8 (v01  PmRef  Cpu1Ist 00003000 INTL 20061109)
[    0.179736] ACPI: Dynamic OEM Table Load:
[    0.179740] ACPI: SSDT (null) 000C8 (v01  PmRef  Cpu1Ist 00003000 INTL 20061109)
[    0.180174] ACPI: SSDT 7f6d7029 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20061109)
[    0.180758] ACPI: Dynamic OEM Table Load:
[    0.180762] ACPI: SSDT (null) 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20061109)
[    0.183130] ACPI: Interpreter enabled
[    0.183130] ACPI: (supports S0 S3 S4 S5)
[    0.183130] ACPI: Using IOAPIC for interrupt routing
[    0.463235] Freeing initrd memory: 10528k freed
[    0.694309] ACPI: EC: GPE = 0x1b, I/O: command/status = 0x66, data = 0x62
[    0.694653] ACPI: No dock devices found.
[    0.694659] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.695384] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.696796] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    0.696800] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    0.696804] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.696807] pci_root PNP0A08:00: host bridge window [mem 0x000d0000-0x000d3fff]
[    0.696811] pci_root PNP0A08:00: host bridge window [mem 0x000d4000-0x000d7fff]
[    0.696814] pci_root PNP0A08:00: host bridge window [mem 0x000d8000-0x000dbfff]
[    0.696818] pci_root PNP0A08:00: host bridge window [mem 0x80000000-0xdfffffff]
[    0.696821] pci_root PNP0A08:00: host bridge window [mem 0xf0000000-0xfebfffff]
[    0.696910] pci 0000:00:02.0: reg 10: [mem 0xf8000000-0xf80fffff 64bit]
[    0.696920] pci 0000:00:02.0: reg 18: [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.696926] pci 0000:00:02.0: reg 20: [io  0x1800-0x1807]
[    0.696977] pci 0000:00:02.1: reg 10: [mem 0xf8100000-0xf81fffff 64bit]
[    0.697109] pci 0000:00:1a.0: reg 20: [io  0x1820-0x183f]
[    0.697185] pci 0000:00:1a.1: reg 20: [io  0x1840-0x185f]
[    0.697257] pci 0000:00:1a.7: reg 10: [mem 0xf8504800-0xf8504bff]
[    0.697331] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.697338] pci 0000:00:1a.7: PME# disabled
[    0.697390] pci 0000:00:1b.0: reg 10: [mem 0xf8500000-0xf8503fff 64bit]
[    0.697461] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.697467] pci 0000:00:1b.0: PME# disabled
[    0.697581] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.697586] pci 0000:00:1c.0: PME# disabled
[    0.697706] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.697711] pci 0000:00:1c.2: PME# disabled
[    0.697832] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    0.697838] pci 0000:00:1c.5: PME# disabled
[    0.697912] pci 0000:00:1d.0: reg 20: [io  0x1860-0x187f]
[    0.697986] pci 0000:00:1d.1: reg 20: [io  0x1880-0x189f]
[    0.698060] pci 0000:00:1d.2: reg 20: [io  0x18a0-0x18bf]
[    0.698133] pci 0000:00:1d.7: reg 10: [mem 0xf8504c00-0xf8504fff]
[    0.698206] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.698212] pci 0000:00:1d.7: PME# disabled
[    0.698399] pci 0000:00:1f.0: quirk: [io  0x1000-0x107f] claimed by ICH6 ACPI/GPIO/TCO
[    0.698404] pci 0000:00:1f.0: quirk: [io  0x1180-0x11bf] claimed by ICH6 GPIO
[    0.698409] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0068 (mask 0007)
[    0.698415] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 2 PIO at 1640 (mask 000f)
[    0.698476] pci 0000:00:1f.1: reg 10: [io  0x0000-0x0007]
[    0.698485] pci 0000:00:1f.1: reg 14: [io  0x0000-0x0003]
[    0.698494] pci 0000:00:1f.1: reg 18: [io  0x0000-0x0007]
[    0.698504] pci 0000:00:1f.1: reg 1c: [io  0x0000-0x0003]
[    0.698513] pci 0000:00:1f.1: reg 20: [io  0x1810-0x181f]
[    0.698586] pci 0000:00:1f.2: reg 10: [io  0x1c00-0x1c07]
[    0.698595] pci 0000:00:1f.2: reg 14: [io  0x18d4-0x18d7]
[    0.698604] pci 0000:00:1f.2: reg 18: [io  0x18d8-0x18df]
[    0.698614] pci 0000:00:1f.2: reg 1c: [io  0x18d0-0x18d3]
[    0.698623] pci 0000:00:1f.2: reg 20: [io  0x18e0-0x18ff]
[    0.698633] pci 0000:00:1f.2: reg 24: [mem 0xf8504000-0xf85047ff]
[    0.698683] pci 0000:00:1f.2: PME# supported from D3hot
[    0.698689] pci 0000:00:1f.2: PME# disabled
[    0.698725] pci 0000:00:1f.3: reg 10: [mem 0x00000000-0x000000ff]
[    0.698754] pci 0000:00:1f.3: reg 20: [io  0x1c20-0x1c3f]
[    0.698899] pci 0000:02:00.0: reg 10: [io  0x2000-0x20ff]
[    0.698911] pci 0000:02:00.0: reg 14: [mem 0xf4000000-0xf4003fff]
[    0.699011] pci 0000:02:00.0: supports D1 D2
[    0.699013] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot
[    0.699020] pci 0000:02:00.0: PME# disabled
[    0.704024] pci 0000:00:1c.0: PCI bridge to [bus 02-03]
[    0.704030] pci 0000:00:1c.0:   bridge window [io  0x2000-0x2fff]
[    0.704036] pci 0000:00:1c.0:   bridge window [mem 0xf4000000-0xf5ffffff]
[    0.704046] pci 0000:00:1c.0:   bridge window [mem 0xf0000000-0xf1ffffff 64bit pref]
[    0.704117] pci 0000:00:1c.2: PCI bridge to [bus 04-05]
[    0.704123] pci 0000:00:1c.2:   bridge window [io  0x3000-0x3fff]
[    0.704130] pci 0000:00:1c.2:   bridge window [mem 0xf6000000-0xf7ffffff]
[    0.704139] pci 0000:00:1c.2:   bridge window [mem 0xf2000000-0xf3ffffff 64bit pref]
[    0.704260] pci 0000:06:00.0: reg 10: [io  0x4000-0x40ff]
[    0.704291] pci 0000:06:00.0: reg 18: [mem 0xf8200000-0xf8200fff 64bit]
[    0.704323] pci 0000:06:00.0: reg 30: [mem 0x00000000-0x0001ffff pref]
[    0.704392] pci 0000:06:00.0: supports D1 D2
[    0.704395] pci 0000:06:00.0: PME# supported from D1 D2 D3hot D3cold
[    0.704402] pci 0000:06:00.0: PME# disabled
[    0.704434] pci 0000:06:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    0.704449] pci 0000:00:1c.5: PCI bridge to [bus 06-06]
[    0.704455] pci 0000:00:1c.5:   bridge window [io  0x4000-0x4fff]
[    0.704461] pci 0000:00:1c.5:   bridge window [mem 0xf8200000-0xf82fffff]
[    0.704471] pci 0000:00:1c.5:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.704573] pci 0000:00:1e.0: PCI bridge to [bus 07-07] (subtractive decode)
[    0.704579] pci 0000:00:1e.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.704585] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.704594] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.704597] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.704600] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.704604] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.704607] pci 0000:00:1e.0:   bridge window [mem 0x000d0000-0x000d3fff] (subtractive decode)
[    0.704610] pci 0000:00:1e.0:   bridge window [mem 0x000d4000-0x000d7fff] (subtractive decode)
[    0.704613] pci 0000:00:1e.0:   bridge window [mem 0x000d8000-0x000dbfff] (subtractive decode)
[    0.704616] pci 0000:00:1e.0:   bridge window [mem 0x80000000-0xdfffffff] (subtractive decode)
[    0.704619] pci 0000:00:1e.0:   bridge window [mem 0xf0000000-0xfebfffff] (subtractive decode)
[    0.704651] pci_bus 0000:00: on NUMA node 0
[    0.704656] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.705046] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.705162] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[    0.705269] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP06._PRT]
[    0.705417] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    0.718710] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.718841] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.718963] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.719086] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.719208] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    0.719331] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.719452] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.719573] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.719631] HEST: Table is not found!
[    0.719723] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.719742] vgaarb: loaded
[    0.719945] SCSI subsystem initialized
[    0.720015] libata version 3.00 loaded.
[    0.720074] usbcore: registered new interface driver usbfs
[    0.720093] usbcore: registered new interface driver hub
[    0.720102] usbcore: registered new device driver usb
[    0.720297] ACPI: WMI: Mapper loaded
[    0.720300] PCI: Using ACPI for IRQ routing
[    0.720304] PCI: pci_cache_line_size set to 64 bytes
[    0.720426] reserve RAM buffer: 000000000009f800 - 000000000009ffff 
[    0.720430] reserve RAM buffer: 000000007f6d0000 - 000000007fffffff 
[    0.720543] NetLabel: Initializing
[    0.720545] NetLabel:  domain hash size = 128
[    0.720547] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.720561] NetLabel:  unlabeled traffic allowed by default
[    0.720602] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.720609] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.720615] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.724022] Switching to clocksource tsc
[    0.737096] AppArmor: AppArmor Filesystem Enabled
[    0.737122] pnp: PnP ACPI init
[    0.737149] ACPI: bus type pnp registered
[    0.740726] pnp: PnP ACPI: found 10 devices
[    0.740728] ACPI: ACPI bus type pnp unregistered
[    0.740734] PnPBIOS: Disabled by ACPI PNP
[    0.740750] system 00:01: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.740753] system 00:01: [mem 0xfed14000-0xfed17fff] has been reserved
[    0.740757] system 00:01: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.740760] system 00:01: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.740764] system 00:01: [mem 0xe0000000-0xefffffff] has been reserved
[    0.740767] system 00:01: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.740770] system 00:01: [mem 0xfed45000-0xfed8ffff] has been reserved
[    0.740778] system 00:04: [mem 0xfed00000-0xfed003ff] has been reserved
[    0.740786] system 00:06: [io  0x0680-0x069f] has been reserved
[    0.740789] system 00:06: [io  0x0800-0x080f] has been reserved
[    0.740793] system 00:06: [io  0x1000-0x107f] has been reserved
[    0.740796] system 00:06: [io  0x1180-0x11bf] has been reserved
[    0.740799] system 00:06: [io  0x1640-0x164f] has been reserved
[    0.740802] system 00:06: [io  0xfe00] has been reserved
[    0.777155] pci 0000:00:1c.5: BAR 15: assigned [mem 0x80000000-0x801fffff pref]
[    0.777159] pci 0000:00:1f.3: BAR 0: assigned [mem 0x80200000-0x802000ff]
[    0.777167] pci 0000:00:1f.3: BAR 0: set to [mem 0x80200000-0x802000ff] (PCI address [0x80200000-0x802000ff]
[    0.777171] pci 0000:00:1c.0: PCI bridge to [bus 02-03]
[    0.777175] pci 0000:00:1c.0:   bridge window [io  0x2000-0x2fff]
[    0.777183] pci 0000:00:1c.0:   bridge window [mem 0xf4000000-0xf5ffffff]
[    0.777189] pci 0000:00:1c.0:   bridge window [mem 0xf0000000-0xf1ffffff 64bit pref]
[    0.777198] pci 0000:00:1c.2: PCI bridge to [bus 04-05]
[    0.777203] pci 0000:00:1c.2:   bridge window [io  0x3000-0x3fff]
[    0.777210] pci 0000:00:1c.2:   bridge window [mem 0xf6000000-0xf7ffffff]
[    0.777217] pci 0000:00:1c.2:   bridge window [mem 0xf2000000-0xf3ffffff 64bit pref]
[    0.777227] pci 0000:06:00.0: BAR 6: assigned [mem 0x80000000-0x8001ffff pref]
[    0.777230] pci 0000:00:1c.5: PCI bridge to [bus 06-06]
[    0.777234] pci 0000:00:1c.5:   bridge window [io  0x4000-0x4fff]
[    0.777241] pci 0000:00:1c.5:   bridge window [mem 0xf8200000-0xf82fffff]
[    0.777247] pci 0000:00:1c.5:   bridge window [mem 0x80000000-0x801fffff pref]
[    0.777256] pci 0000:00:1e.0: PCI bridge to [bus 07-07]
[    0.777259] pci 0000:00:1e.0:   bridge window [io  disabled]
[    0.777266] pci 0000:00:1e.0:   bridge window [mem disabled]
[    0.777271] pci 0000:00:1e.0:   bridge window [mem pref disabled]
[    0.777293]   alloc irq_desc for 17 on node -1
[    0.777296]   alloc kstat_irqs on node -1
[    0.777303] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.777310] pci 0000:00:1c.0: setting latency timer to 64
[    0.777322]   alloc irq_desc for 18 on node -1
[    0.777324]   alloc kstat_irqs on node -1
[    0.777329] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.777335] pci 0000:00:1c.2: setting latency timer to 64
[    0.777346]   alloc irq_desc for 16 on node -1
[    0.777348]   alloc kstat_irqs on node -1
[    0.777352] pci 0000:00:1c.5: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.777359] pci 0000:00:1c.5: setting latency timer to 64
[    0.777369] pci 0000:00:1e.0: setting latency timer to 64
[    0.777374] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.777377] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.777380] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.777383] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000d3fff]
[    0.777386] pci_bus 0000:00: resource 8 [mem 0x000d4000-0x000d7fff]
[    0.777389] pci_bus 0000:00: resource 9 [mem 0x000d8000-0x000dbfff]
[    0.777392] pci_bus 0000:00: resource 10 [mem 0x80000000-0xdfffffff]
[    0.777395] pci_bus 0000:00: resource 11 [mem 0xf0000000-0xfebfffff]
[    0.777398] pci_bus 0000:02: resource 0 [io  0x2000-0x2fff]
[    0.777401] pci_bus 0000:02: resource 1 [mem 0xf4000000-0xf5ffffff]
[    0.777404] pci_bus 0000:02: resource 2 [mem 0xf0000000-0xf1ffffff 64bit pref]
[    0.777407] pci_bus 0000:04: resource 0 [io  0x3000-0x3fff]
[    0.777410] pci_bus 0000:04: resource 1 [mem 0xf6000000-0xf7ffffff]
[    0.777413] pci_bus 0000:04: resource 2 [mem 0xf2000000-0xf3ffffff 64bit pref]
[    0.777416] pci_bus 0000:06: resource 0 [io  0x4000-0x4fff]
[    0.777418] pci_bus 0000:06: resource 1 [mem 0xf8200000-0xf82fffff]
[    0.777421] pci_bus 0000:06: resource 2 [mem 0x80000000-0x801fffff pref]
[    0.777424] pci_bus 0000:07: resource 4 [io  0x0000-0x0cf7]
[    0.777427] pci_bus 0000:07: resource 5 [io  0x0d00-0xffff]
[    0.777430] pci_bus 0000:07: resource 6 [mem 0x000a0000-0x000bffff]
[    0.777433] pci_bus 0000:07: resource 7 [mem 0x000d0000-0x000d3fff]
[    0.777435] pci_bus 0000:07: resource 8 [mem 0x000d4000-0x000d7fff]
[    0.777438] pci_bus 0000:07: resource 9 [mem 0x000d8000-0x000dbfff]
[    0.777441] pci_bus 0000:07: resource 10 [mem 0x80000000-0xdfffffff]
[    0.777444] pci_bus 0000:07: resource 11 [mem 0xf0000000-0xfebfffff]
[    0.777490] NET: Registered protocol family 2
[    0.777570] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.777887] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.778410] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.778759] TCP: Hash tables configured (established 131072 bind 65536)
[    0.778762] TCP reno registered
[    0.778766] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.778781] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.778925] NET: Registered protocol family 1
[    0.778951] pci 0000:00:02.0: Boot video device
[    0.779148] PCI: CLS 64 bytes, default 64
[    0.779181] Simple Boot Flag at 0x36 set to 0x1
[    0.779403] cpufreq-nforce2: No nForce2 chipset.
[    0.779441] Scanning for low memory corruption every 60 seconds
[    0.779582] audit: initializing netlink socket (disabled)
[    0.779596] type=2000 audit(1300825109.772:1): initialized
[    0.791550] highmem bounce pool size: 64 pages
[    0.791556] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.793285] VFS: Disk quotas dquot_6.5.2
[    0.793359] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.794051] fuse init (API version 7.14)
[    0.794161] msgmni has been set to 1704
[    0.797177] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.797181] io scheduler noop registered
[    0.797184] io scheduler deadline registered
[    0.797201] io scheduler cfq registered (default)
[    0.797355] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.797414]   alloc irq_desc for 40 on node -1
[    0.797416]   alloc kstat_irqs on node -1
[    0.797431] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
[    0.797553] pcieport 0000:00:1c.2: setting latency timer to 64
[    0.797608]   alloc irq_desc for 41 on node -1
[    0.797610]   alloc kstat_irqs on node -1
[    0.797621] pcieport 0000:00:1c.2: irq 41 for MSI/MSI-X
[    0.797741] pcieport 0000:00:1c.5: setting latency timer to 64
[    0.797795]   alloc irq_desc for 42 on node -1
[    0.797797]   alloc kstat_irqs on node -1
[    0.797807] pcieport 0000:00:1c.5: irq 42 for MSI/MSI-X
[    0.797943] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.798054] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.798170] intel_idle: MWAIT substates: 0x1110
[    0.798173] intel_idle: does not run on family 6 model 15
[    0.799213] ACPI: AC Adapter [ACAD] (on-line)
[    0.799306] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    0.799727] ACPI: Lid Switch [LID]
[    0.799781] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
[    0.799786] ACPI: Power Button [PWRB]
[    0.799836] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2
[    0.799840] ACPI: Sleep Button [SLPB]
[    0.799919] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.799923] ACPI: Power Button [PWRF]
[    0.800203] ACPI: acpi_idle registered with cpuidle
[    0.803253] Monitor-Mwait will be used to enter C-1 state
[    0.803279] Monitor-Mwait will be used to enter C-2 state
[    0.803286] Marking TSC unstable due to TSC halts in idle
[    0.803343] Switching to clocksource hpet
[    0.813892] thermal LNXTHERM:01: registered as thermal_zone0
[    0.813903] ACPI: Thermal Zone [TZ00] (61 C)
[    0.814005] ERST: Table is not found!
[    0.814058] isapnp: Scanning for PnP cards...
[    0.814439] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.816214] brd: module loaded
[    0.816852] loop: module loaded
[    0.817079] ata_piix 0000:00:1f.1: version 2.13
[    0.817099]   alloc irq_desc for 19 on node -1
[    0.817102]   alloc kstat_irqs on node -1
[    0.817110] ata_piix 0000:00:1f.1: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.817156] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.817251] scsi0 : ata_piix
[    0.817345] scsi1 : ata_piix
[    0.818127] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1810 irq 14
[    0.818131] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1818 irq 15
[    0.818517] Fixed MDIO Bus: probed
[    0.818556] PPP generic driver version 2.4.2
[    0.818615] tun: Universal TUN/TAP device driver, 1.6
[    0.818617] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.818714] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.818739] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.818759] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    0.818764] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    0.818802] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    0.818838] ehci_hcd 0000:00:1a.7: debug port 1
[    0.822726] ehci_hcd 0000:00:1a.7: cache line size of 64 is not supported
[    0.822768] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xf8504800
[    0.826851] ata2: port disabled. ignoring.
[    0.840018] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    0.840174] hub 1-0:1.0: USB hub found
[    0.840180] hub 1-0:1.0: 4 ports detected
[    0.840335]   alloc irq_desc for 23 on node -1
[    0.840338]   alloc kstat_irqs on node -1
[    0.840345] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.840362] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.840366] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.840413] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    0.840447] ehci_hcd 0000:00:1d.7: debug port 1
[    0.844335] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[    0.844355] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf8504c00
[    0.860038] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.860181] hub 2-0:1.0: USB hub found
[    0.860187] hub 2-0:1.0: 6 ports detected
[    0.860281] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.860300] uhci_hcd: USB Universal Host Controller Interface driver
[    0.860337] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.860346] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.860351] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    0.860394] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    0.860437] uhci_hcd 0000:00:1a.0: irq 16, io base 0x00001820
[    0.860587] hub 3-0:1.0: USB hub found
[    0.860593] hub 3-0:1.0: 2 ports detected
[    0.860668]   alloc irq_desc for 21 on node -1
[    0.860670]   alloc kstat_irqs on node -1
[    0.860677] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.860684] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    0.860688] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    0.860726] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    0.860767] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00001840
[    0.860906] hub 4-0:1.0: USB hub found
[    0.860911] hub 4-0:1.0: 2 ports detected
[    0.860984] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.860991] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.860996] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.861036] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    0.861065] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001860
[    0.861195] hub 5-0:1.0: USB hub found
[    0.861200] hub 5-0:1.0: 2 ports detected
[    0.861280] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.861287] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.861292] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.861330] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    0.861536] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001880
[    0.861678] hub 6-0:1.0: USB hub found
[    0.861683] hub 6-0:1.0: 2 ports detected
[    0.861757] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.861765] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.861769] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.861810] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    0.861842] uhci_hcd 0000:00:1d.2: irq 18, io base 0x000018a0
[    0.861984] hub 7-0:1.0: USB hub found
[    0.861989] hub 7-0:1.0: 2 ports detected
[    0.862137] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.864400] i8042.c: Detected active multiplexing controller, rev 1.1.
[    0.867315] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.867322] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    0.867354] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    0.867381] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    0.867410] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    0.867528] mice: PS/2 mouse device common for all mice
[    0.867744] rtc_cmos 00:07: RTC can wake from S4
[    0.867790] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
[    0.867825] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    0.867952] device-mapper: uevent: version 1.0.3
[    0.868151] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: dm-devel@redhat.com
[    0.868233] device-mapper: multipath: version 1.1.1 loaded
[    0.868236] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.868368] EISA: Probing bus 0 at eisa.0
[    0.868371] EISA: Cannot allocate resource for mainboard
[    0.868374] Cannot allocate resource for EISA slot 1
[    0.868376] Cannot allocate resource for EISA slot 2
[    0.868378] Cannot allocate resource for EISA slot 3
[    0.868381] Cannot allocate resource for EISA slot 4
[    0.868383] Cannot allocate resource for EISA slot 5
[    0.868385] Cannot allocate resource for EISA slot 6
[    0.868388] Cannot allocate resource for EISA slot 7
[    0.868390] Cannot allocate resource for EISA slot 8
[    0.868392] EISA: Detected 0 cards.
[    0.868536] cpuidle: using governor ladder
[    0.868631] cpuidle: using governor menu
[    0.869008] TCP cubic registered
[    0.869165] NET: Registered protocol family 10
[    0.869600] lo: Disabled Privacy Extensions
[    0.869890] NET: Registered protocol family 17
[    0.870602] Using IPI No-Shortcut mode
[    0.870729] PM: Resume from disk failed.
[    0.870749] registered taskstats version 1
[    0.871278]   Magic number: 3:29:347
[    0.871325]  pci0000:00: hash matches
[    0.871389] rtc_cmos 00:07: setting system clock to 2011-03-22 20:18:30 UTC (1300825110)
[    0.871393] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.871395] EDD information not available.
[    0.907117] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    0.989392] ata1.00: ATAPI: Optiarc DVD RW AD-7563A, WX05, max UDMA/33
[    1.045294] ata1.00: configured for UDMA/33
[    1.168761] isapnp: No Plug & Play device found
[    1.169883] scsi 0:0:0:0: CD-ROM            Optiarc  DVD RW AD-7563A  WX05 PQ: 0 ANSI: 5
[    1.175443] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.175447] Uniform CD-ROM driver Revision: 3.20
[    1.175576] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    1.175644] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    1.175761] Freeing unused kernel memory: 688k freed
[    1.176221] Write protecting the kernel text: 4936k
[    1.176284] Write protecting the kernel read-only data: 1980k
[    1.196094] usb 1-3: new high speed USB device using ehci_hcd and address 2
[    1.198965] udev[84]: starting version 163
[    1.370999] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.371033] r8169 0000:06:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.371097] r8169 0000:06:00.0: setting latency timer to 64
[    1.371185]   alloc irq_desc for 43 on node -1
[    1.371187]   alloc kstat_irqs on node -1
[    1.371209] r8169 0000:06:00.0: irq 43 for MSI/MSI-X
[    1.371856] r8169 0000:06:00.0: eth0: RTL8101e at 0xf80b4000, 00:e0:b8:fa:d4:3f, XID 94200000 IRQ 43
[    1.402790] ahci 0000:00:1f.2: version 3.0
[    1.402817] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.402881]   alloc irq_desc for 44 on node -1
[    1.402884]   alloc kstat_irqs on node -1
[    1.402899] ahci 0000:00:1f.2: irq 44 for MSI/MSI-X
[    1.403003] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0x7 impl SATA mode
[    1.403007] ahci 0000:00:1f.2: flags: 64bit ncq sntf ilck pm led clo pio slum part ccc 
[    1.403015] ahci 0000:00:1f.2: setting latency timer to 64
[    1.412356] scsi2 : ahci
[    1.412605] scsi3 : ahci
[    1.412750] scsi4 : ahci
[    1.412947] ata3: SATA max UDMA/133 abar m2048@0xf8504000 port 0xf8504100 irq 44
[    1.412952] ata4: SATA max UDMA/133 abar m2048@0xf8504000 port 0xf8504180 irq 44
[    1.412957] ata5: SATA max UDMA/133 abar m2048@0xf8504000 port 0xf8504200 irq 44
[    1.508039] usb 2-5: new high speed USB device using ehci_hcd and address 3
[    1.732050] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.732080] ata4: SATA link down (SStatus 0 SControl 300)
[    1.733029] ata5: SATA link down (SStatus 0 SControl 300)
[    1.733042] ata3.00: unexpected _GTF length (8)
[    1.733397] ata3.00: ATA-8: Hitachi HTS542516K9SA00, BBCOC31P, max UDMA/133
[    1.733400] ata3.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.734584] ata3.00: unexpected _GTF length (8)
[    1.734970] ata3.00: configured for UDMA/133
[    1.748197] scsi 2:0:0:0: Direct-Access     ATA      Hitachi HTS54251 BBCO PQ: 0 ANSI: 5
[    1.748390] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    1.748499] sd 2:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    1.748642] sd 2:0:0:0: [sda] Write Protect is off
[    1.748646] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.748702] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.748940]  sda: sda1 sda2 sda3
[    1.773701] sd 2:0:0:0: [sda] Attached SCSI disk
[    2.208320] Initializing USB Mass Storage driver...
[    2.208469] scsi5 : usb-storage 2-5:1.0
[    2.208599] usbcore: registered new interface driver usb-storage
[    2.208602] USB Mass Storage support registered.
[    2.441046] usb 5-2: new low speed USB device using uhci_hcd and address 2
[    2.468729] EXT4-fs (loop0): mounted filesystem with ordered data mode. Opts: (null)
[    2.702570] ACPI: Battery Slot [BAT1] (battery present)
[    3.215567] scsi 5:0:0:0: Direct-Access     Generic- Multi-Card       1.00 PQ: 0 ANSI: 0 CCS
[    3.216089] sd 5:0:0:0: Attached scsi generic sg2 type 0
[    3.217653] sd 5:0:0:0: [sdb] Attached SCSI removable disk
[   23.050795] udev[405]: starting version 163
[   23.104830] lp: driver loaded but no devices found
[   23.203804] r8187se: module is from the staging directory, the quality is unknown, you have been warned.
[   23.229812] Linux agpgart interface v0.103
[   23.284238] agpgart-intel 0000:00:00.0: Intel 965GM Chipset
[   23.284845] agpgart-intel 0000:00:00.0: detected 7676K stolen memory
[   23.357294] ieee80211_crypt: registered algorithm 'NULL'
[   23.357300] ieee80211_crypt: registered algorithm 'TKIP'
[   23.357303] ieee80211_crypt: registered algorithm 'CCMP'
[   23.357306] ieee80211_crypt: registered algorithm 'WEP'
[   23.357308] 
[   23.357309] Linux kernel driver for RTL8180 / RTL8185 based WLAN cards
[   23.357311] Copyright (c) 2004-2005, Andrea Merello
[   23.357313] r8180: Initializing module
[   23.357315] r8180: Wireless extensions version 22
[   23.357317] r8180: Initializing proc filesystem
[   23.357362] r8180: Configuring chip resources
[   23.357389] r8180 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   23.357398] r8180 0000:02:00.0: setting latency timer to 64
[   23.469989] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[   23.475549] Linux video capture interface: v2.00
[   23.479557] uvcvideo: Found UVC 1.00 device Gateway USB 2.0 Webcam (04f2:b027)
[   23.488867] r8180: Channel plan is 1
[   23.488869] 
[   23.488872] Dot11d_Init()
[   23.488877] r8180: MAC controller is a RTL8187SE b/g
[   23.491089] r8180: usValue is 0x100
[   23.491090] 
[   23.534437] r8180: EEPROM version 104
[   23.538772] r8180: WW:**PLEASE** REPORT SUCCESSFUL/UNSUCCESSFUL TO Realtek!
[   23.539358] r8180: IRQ 16
[   23.540302] r8180: Driver probe completed
[   23.540304] 
[   23.577585] input: Gateway USB 2.0 Webcam as /devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3:1.0/input/input5
[   23.578181] usbcore: registered new interface driver uvcvideo
[   23.578185] USB Video Class driver (v0.1.0)
[   23.595352] type=1400 audit(1300810733.220:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=688 comm="apparmor_parser"
[   23.596145] type=1400 audit(1300810733.224:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=688 comm="apparmor_parser"
[   23.596581] type=1400 audit(1300810733.224:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=688 comm="apparmor_parser"
[   23.620525] usbcore: registered new interface driver hiddev
[   23.633609] input: PS/2+USB Mouse as /devices/pci0000:00/0000:00:1d.0/usb5/5-2/5-2:1.0/input/input6
[   23.633766] generic-usb 0003:04F3:0210.0001: input,hidraw0: USB HID v1.11 Mouse [PS/2+USB Mouse] on usb-0000:00:1d.0-2/input0
[   23.633794] usbcore: registered new interface driver usbhid
[   23.633796] usbhid: USB HID core driver
[   23.646583] [drm] Initialized drm 1.1.0 20060810
[   23.773776] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   23.773784] i915 0000:00:02.0: setting latency timer to 64
[   23.825931]   alloc irq_desc for 45 on node -1
[   23.825936]   alloc kstat_irqs on node -1
[   23.825948] i915 0000:00:02.0: irq 45 for MSI/MSI-X
[   23.825964] [drm] set up 7M of stolen space
[   23.941566] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   23.941885] [drm] initialized overlay support
[   24.309016] Skipping EDID probe due to cached edid
[   24.477441] Synaptics Touchpad, model: 1, fw: 5.10, id: 0x258eb1, caps: 0xa04713/0x0/0x0
[   24.521986] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input7
[   24.675131] Console: switching to colour frame buffer device 160x50
[   24.679263] fb0: inteldrmfb frame buffer device
[   24.679266] drm: registered panic notifier
[   24.679271] Slow work thread pool: Starting up
[   24.679468] Slow work thread pool: Ready
[   24.688633] acpi device:07: registered as cooling_device2
[   24.696931] acpi device:08: registered as cooling_device3
[   24.698879] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:01/input/input8
[   24.698987] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   24.699038] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   24.699103] HDA Intel 0000:00:1b.0: power state changed by ACPI to D0
[   24.699114] HDA Intel 0000:00:1b.0: power state changed by ACPI to D0
[   24.699128]   alloc irq_desc for 22 on node -1
[   24.699131]   alloc kstat_irqs on node -1
[   24.699140] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   24.699214]   alloc irq_desc for 46 on node -1
[   24.699216]   alloc kstat_irqs on node -1
[   24.699231] HDA Intel 0000:00:1b.0: irq 46 for MSI/MSI-X
[   24.699271] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   24.740050] Skipping EDID probe due to cached edid
[   24.777423] input: HDA Intel Mic at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   24.777546] input: HDA Intel HP Out at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   25.005586] Adding 261116k swap on /host/ubuntu/disks/swap.disk.  Priority:-1 extents:1 across:261116k 
[   25.036739] EXT4-fs (loop0): re-mounted. Opts: errors=remount-ro
[   25.266147] type=1400 audit(1300810734.892:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=943 comm="apparmor_parser"
[   25.268651] type=1400 audit(1300810734.896:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=943 comm="apparmor_parser"
[   25.322053] ppdev: user-space parallel port driver
[   25.327235] r8180: Bringing up iface
[   25.486988] type=1400 audit(1300810735.112:7): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=1055 comm="apparmor_parser"
[   25.504698] type=1400 audit(1300810735.132:8): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=1057 comm="apparmor_parser"
[   25.517490] type=1400 audit(1300810735.144:9): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=1057 comm="apparmor_parser"
[   25.524026] type=1400 audit(1300810735.152:10): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-thumbnailer" pid=1057 comm="apparmor_parser"
[   25.525738] r8180: Card successfully reset
[   25.536481] type=1400 audit(1300810735.164:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=1061 comm="apparmor_parser"
[   25.537211] Skipping EDID probe due to cached edid
[   25.553128] Skipping EDID probe due to cached edid
[   25.989382] EXT4-fs (loop0): re-mounted. Opts: errors=remount-ro,commit=0
[   26.264977] r8180: WIRELESS_MODE_G
[   26.264980] 
[   26.279081] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   26.282696] r8169 0000:06:00.0: eth0: link up
[   26.282702] r8169 0000:06:00.0: eth0: link up
[   26.856062] Skipping EDID probe due to cached edid
[   26.880056] Skipping EDID probe due to cached edid
[   26.904055] Skipping EDID probe due to cached edid
[   26.920047] Skipping EDID probe due to cached edid
[   27.640815] EXT4-fs (loop0): re-mounted. Opts: errors=remount-ro,commit=0
[   34.460072] Skipping EDID probe due to cached edid
[   34.488054] Skipping EDID probe due to cached edid
[   34.512057] Skipping EDID probe due to cached edid
[   34.536054] Skipping EDID probe due to cached edid
[   35.861074] Skipping EDID probe due to cached edid
[   36.497015] eth0: no IPv6 routers present
[   39.464044] Skipping EDID probe due to cached edid
[ 1997.664113] Skipping EDID probe due to cached edid
[ 3847.941108] Skipping EDID probe due to cached edid

```And what means TBABILL? o_O?

---

### Post by Hippytaff on 2011-03-22
> And what means TBABILL? o_Othe oter guy helping out :-)

I don't think the driver is loading correctly
```

23.488877] r8180: MAC controller is a RTL8187SE b/g
[   23.491089] r8180: usValue is 0x100
[   23.491090] 
[   23.534437] r8180: EEPROM version 104
[   23.538772] r8180: [COLOR=Red]WW[/COLOR]:**PLEASE** REPORT SUCCESSFUL/UNSUCCESSFUL TO Realtek!
[   23.539358] r8180: IRQ 16
[   23.540302] r8180: Driver probe completed
```

Do you have the windows wireless driver on disc?

---

### Post by Hrexen on 2011-03-22
Good news! I used ndisgtk to install existing Windows driver and lost my wireless entirely. Trying to get it back :D

---

### Post by Hrexen on 2011-03-22
Now in my network manager I have only Wired networks. O_O

---

### Post by Hippytaff on 2011-03-22
ok...can you do ```
sudo apt-get update
``` and reboot.

---

### Post by Hrexen on 2011-03-22
I did it, and I have the same.

---

### Post by Hippytaff on 2011-03-22
how did you install the windows drivers (inf and sys files?) can you do```
cd /etc/modprobe.d/
```
and```
sudo cat blacklist.conf
``` and post the output.

---

### Post by Hrexen on 2011-03-22
Yes, there was 3 files: an *.inf file, *.sys file and a *.cat file.

Here it is.
```

# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac

```

---

### Post by Hippytaff on 2011-03-22
In that file again with ```
sudo nano blacklist.conf
``` in the file do this```

#wireless driver
blacklist r8187se
```in the same way other files are blacklisted. The save and close  (CTRL+X) then try rebooting.

---

### Post by Hippytaff on 2011-03-22
If still no luck...make sure you have the right windows driver and remove the windows driver with Ndisgtk. Then get the inf and sys files and put the in a folder on your desktop. Point Ndisgtk at the inf file. install it again.

---

### Post by Hippytaff on 2011-03-22
If this doesn't work we need to go back to square one. By removing the windows driver, reinstalling the r8187se module, and removing the r8187se module from the blacklist.conf. We can go through that step by step if you like or you can crack on...any problems let me know. once that is all in place...we can make sure we haven't overlooked something obvious and simple...like selecting a network to connect to :?

---

### Post by Hrexen on 2011-03-23
I found an other driver installed it and all the same. It was no use of it. If you need I can post blacklist.conf again or lsmod. :(

---

### Post by Hippytaff on 2011-03-23
Can you tell me what drivers you have installed...I think we need to go back to the original state of the wireless. lsmod and your blacklist.conf file would be worth seeing again because I don't know where we are with what drivers have been installed etc etc

---

### Post by TBABill on 2011-03-24
Ok, I'm not positive, but shouldn't this be listed in lsmod as "rtl8187se", not "r8187se"? If so, it could be a simple update of /etc/modules to concatenate (#) the r8187 listing and below it add rtl8187se, then restart.
 
Thoughts? Please advise if I'm off base on this one, but that original lsmod listed it as r8187se.
 
What made me ask is it is listed [http://wiki.debian.org/rtl818x](http://wiki.debian.org/rtl818x) as rtl8187se and they even modprobe rtl8187se to enable the driver.

---

### Post by Hrexen on 2011-03-24
> **Hippytaff said:**
> Can you tell me what drivers you have installed...I think we need to go back to the original state of the wireless. lsmod and your blacklist.conf file would be worth seeing again because I don't know where we are with what drivers have been installed etc etc

Now it's installed driver downloaded from Gateway support centre. Folder is named VistaX86, and has three files: net8187se.cat, net8187Se.inf, rtl8187Se.sys.
Maybe the problem is with Net. Manager applet, it doesn't show anything except Wired Network. :???:

---

### Post by Hippytaff on 2011-03-24
TBABill might have something there
 
Though in a different thread replacing Network Manager with WICD seemd to resolve the unresolvable

---

### Post by Hrexen on 2011-03-24
When I wrote* ifconfig wlan0 up*:
wlan0: ERROR while getting interface flags: No such device

It seems wicd doesn't help.

---

### Post by TBABill on 2011-03-24
I'm at a loss. I think you need to get back to square one and go after only ONE path to get it working. If you want to use ndiswrapper, then do so till you get it working. If you want to use a native Linux driver, then do the same. Going in multiple directions is going to create a mess in your drivers and will be even more difficult to fix.

---

### Post by Hrexen on 2011-03-24
modprobe r8187se returns:

```

FATAL: Error inserting r8187se (/lib/modules/2.6.35-28-generic/kernel/drivers/staging/rtl8187se/r8187se.ko): Operation not permitted

```

I'll try again from very beginning.

---

### Post by TBABill on 2011-03-24
That would have been ```
sudo modprobe rtl8187se
```

---

### Post by Hrexen on 2011-03-24
> **TBABill said:**
> That would have been ```
sudo modprobe rtl8187se
```

answer for this is 
```

FATAL: Module rtl8187se not found.

```

---

### Post by TBABill on 2011-03-24
Is it blacklisted? If it is it needs to be un-blacklisted, then probably a restart and try again.

---

### Post by Hippytaff on 2011-03-24
> **TBABill said:**
> Is it blacklisted? If it is it needs to be un-blacklisted, then probably a restart and try again.


I think we did blacklist it...but your right...lets get back to the original state and decide which option you want to go with. I know a lot of people don't like the Ndiswrapper route, but I've found it to be succesful the majority of the time.

---

### Post by Hrexen on 2011-03-24
> **TBABill said:**
> Is it blacklisted? If it is it needs to be un-blacklisted, then probably a restart and try again.

No, it's not. I had deleted the changes we did.
There is nothing in blacklist.conf (*sudo nano blacklist.conf*)
And there is no drivers installed in ndisgtk.
And I still don't have all list of connections (even inactive) in my Network Manager applet.

---

### Post by Hippytaff on 2011-03-24
You should have something in blacklist.conf (just the default stuff). Double check```
sudo nano /etc/modprobe.d/blacklist.conf
```

because if the default stuff isn't blacklisted then that could be fun :-)

(not a problem really, we'll just replace it)

---

### Post by Hrexen on 2011-03-25
Please let's start from beginning.

P.S. I've installed a programme named SWScanner, and it shows this:

---

### Post by Hrexen on 2011-05-30
The problem is solved. I've just reinstalled ubuntu, and everything is ok, wireless works.

P.S. During the installation computer was connected to the internet (LAN cable). Maybe that helped to solve the problem.;)

---

### Post by Hippytaff on 2011-05-31
Glad it's sorted :)

---

