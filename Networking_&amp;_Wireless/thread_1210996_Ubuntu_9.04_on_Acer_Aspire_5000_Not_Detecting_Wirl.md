---
title: "Ubuntu 9.04 on Acer Aspire 5000 Not Detecting Wirless Networks"
date: 2009-07-12
forum: Networking &amp; Wireless
---

### Post by FallSe7en on 2009-07-12
Hello, first time trying Linux out--decided to install Ubuntu 9.04 on my laptop. I'm running into problems when I try connecting to my wireless network. Not really sure where to go from here, and I really hope somebody can help. Thanks in advance!
[B]
1 ) Machine Brand and Model (PC/Laptop)[/B]: Acer Aspire 5000 Laptop
[B]2 ) Wireless Brand, Model and Wireless Chipset: 
[/B][INDENT]Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)

Network controller: Broadcom Corporation BCM4318 [Airforce One 54g] 802.11g Wireless LAN Controller
[/INDENT][B]3 ) check interface:
[/B][INDENT]Result of 'ifconfig':
eth0 Link encap:Ethernet HWaddr 00:16:36:34:dd:a0
       UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
       RX packets:0 errors:0 dropped:0 overruns:0 frame:0
       TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
       collisions:0 txqueuelen:1000
       RX bytes: 0 (0.0 B)  TX bytes:0 (0.0 B)
       Interrupt:19 Base address:0x1800
lo     Link encap: Local Loopback
       inet addr:127.0.0.1 Mask:255.0.0.0
       inet6 addr: ::1/128 Scope:Host
       UP LOOPBACK RUNNING MTU:16436 Metric:1
       RX packets:8 errors:0 dropped:0 overruns:0 frame:0
       TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
       collisions:0 txqueuelen:0
       RX bytes:516 (516.0 B)  TX bytes:516 (516.0 B)

Result of 'iwconfig':
lo             no wireless extensions.
eth0         no wireless extensions.
wmaster0 no wireless extensions.
wlan0       IEEE 802.11bg ESSID:""
               Mode:Managed Frequency:2.412 GHz Access Point: Not-Associated
               TX-Power=0 dBm
               Retry min limit:7  RTS thr:off  Fragment  thr=2352 B
               Power Management:off
               Link Quality:0 Signal level:0 Noise level:0
               Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
               Tx excessive retries:0 Invalid misc:0 Missed beacon:0
[/INDENT][B]4 ) Check for modules:
[/B][INDENT]justinyl@justinyl-laptop:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          13440  1 
nls_cp437              15104  1 
vfat                   21120  1 
fat                    65592  1 vfat
rfkill_input           14080  0 
binfmt_misc            18572  1 
ppdev                  16904  0 
bridge                 63904  0 
stp                    11140  1 bridge
bnep                   22912  0 
video                  29204  0 
output                 11648  1 video
lp                     19588  0 
parport                49584  2 ppdev,lp
joydev                 20864  0 
snd_intel8x0           43816  3 
snd_ac97_codec        133848  1 snd_intel8x0
arc4                   10240  2 
ecb                    11392  2 
ac97_bus               10368  1 snd_ac97_codec
snd_pcm_oss            52352  0 
snd_mixer_oss          24960  1 snd_pcm_oss
snd_pcm                99336  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy          11524  0 
snd_seq_oss            41984  0 
snd_seq_midi           15744  0 
snd_rawmidi            33920  1 snd_seq_midi
snd_seq_midi_event     16512  2 snd_seq_oss,snd_seq_midi
b43                   145192  0 
snd_seq                66272  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              34064  2 snd_pcm,snd_seq
snd_seq_device         16276  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
mac80211              251144  1 b43
cfg80211               43168  1 mac80211
pcmcia                 47640  0 
snd                    78792  16 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              16800  1 snd
led_class              13064  1 b43
input_polldev          12688  1 b43
k8temp                 13440  0 
psmouse                64028  0 
snd_page_alloc         18704  2 snd_intel8x0,snd_pcm
pcspkr                 11136  0 
serio_raw              14468  0 
yenta_socket           35596  1 
rsrc_nonstatic         19584  1 yenta_socket
pcmcia_core            49188  3 pcmcia,yenta_socket,rsrc_nonstatic
shpchp                 44572  0 
i2c_sis96x             13572  0 
ssb                    46724  1 b43
sis900                 31616  0 
mii                    14464  1 sis900
usb_storage            94912  1 
fbcon                  49792  0 
tileblit               11264  1 fbcon
font                   17024  1 fbcon
bitblit                14464  1 fbcon
softcursor             10368  1 bitblit
justinyl@justinyl-laptop:~$ 
[/INDENT][B]5 ) Kernel boot messages:
[/B][INDENT]Result of 'dmesg':
[    0.000000] BIOS EBDA/lowmem at: 0009f400/0009f400
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.28-11-generic (buildd@crested) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #42-Ubuntu SMP Fri Apr 17 01:58:03 UTC 2009 (Ubuntu 2.6.28-11.42-generic)
[    0.000000] Command line: root=UUID=5ec2828d-360a-436b-9da6-eeea001249aa ro quiet splash 
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f400 (usable)
[    0.000000]  BIOS-e820: 000000000009f400 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003bef0000 (usable)
[    0.000000]  BIOS-e820: 000000003bef0000 - 000000003befa000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003befa000 - 000000003bf00000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003bf00000 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] DMI present.
[    0.000000] last_pfn = 0x3bef0 max_arch_pfn = 0x3ffffffff
[    0.000000] Scanning 2 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000001000 (usable)
[    0.000000]  modified: 0000000000001000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 0000000000008000 (usable)
[    0.000000]  modified: 0000000000008000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 0000000000092400 (usable)
[    0.000000]  modified: 000000000009f400 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000003bef0000 (usable)
[    0.000000]  modified: 000000003bef0000 - 000000003befa000 (ACPI data)
[    0.000000]  modified: 000000003befa000 - 000000003bf00000 (ACPI NVS)
[    0.000000]  modified: 000000003bf00000 - 0000000040000000 (reserved)
[    0.000000]  modified: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] init_memory_mapping: 0000000000000000-000000003bef0000
[    0.000000]  0000000000 - 003be00000 page 2M
[    0.000000]  003be00000 - 003bef0000 page 4k
[    0.000000] kernel direct mapping tables up to 3bef0000 @ 10000-13000
[    0.000000] last_map_addr: 3bef0000 end: 3bef0000
[    0.000000] RAMDISK: 3785b000 - 37fefa3c
[    0.000000] ACPI: RSDP 000F7F60, 0014 (r0 PTLTD )
[    0.000000] ACPI: RSDT 3BEF619D, 0034 (r1 PTLTD    RSDT    6040000  LTP        0)
[    0.000000] ACPI: FACP 3BEF9E3E, 0074 (r1 SiS    755F      6040000 PTL     F4240)
[    0.000000] ACPI: DSDT 3BEF61D1, 3C6D (r1 PTLTD       755  6040000 MSFT  100000E)
[    0.000000] ACPI: FACS 3BEFAFC0, 0040
[    0.000000] ACPI: SSDT 3BEF9EB2, 00D6 (r1 PTLTD  POWERNOW  6040000  LTP        1)
[    0.000000] ACPI: APIC 3BEF9F88, 0050 (r1 PTLTD       APIC    6040000  LTP        0)
[    0.000000] ACPI: BOOT 3BEF9FD8, 0028 (r1 PTLTD  $SBFTBL$  6040000  LTP        1)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] (6 early reservations) ==> bootmem [0000000000 - 003bef0000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
[    0.000000]   #2 [0000200000 - 0000b854b0]    TEXT DATA BSS ==> [0000200000 - 0000b854b0]
[    0.000000]   #3 [003785b000 - 0037fefa3c]          RAMDISK ==> [003785b000 - 0037fefa3c]
[    0.000000]   #4 [000009f400 - 0000100000]    BIOS reserved ==> [000009f400 - 0000100000]
[    0.000000]   #5 [0000010000 - 0000011000]          PGTABLE ==> [0000010000 - 0000011000]
[    0.000000] found SMP MP-table at [ffff8800000f7fd0] 000f7fd0
[    0.000000]  [ffffe20000000000-ffffe20000dfffff] PMD -> [ffff880001200000-ffff880001ffffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00100000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[4] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000001
[    0.000000]     0: 0x00000006 -> 0x00000008
[    0.000000]     0: 0x00000010 -> 0x00000092
[    0.000000]     0: 0x00000100 -> 0x0003bef0
[    0.000000] On node 0 totalpages: 245365
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 2539 pages reserved
[    0.000000]   DMA zone: 1378 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 3301 pages used for memmap
[    0.000000]   DMA32 zone: 238091 pages, LIFO batch:31
[    0.000000]   Normal zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x8008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 0, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ11 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] PM: Registered nosave memory: 0000000000001000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 0000000000008000 - 0000000000010000
[    0.000000] PM: Registered nosave memory: 0000000000092000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000dc000
[    0.000000] PM: Registered nosave memory: 00000000000dc000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:bff00000)
[    0.000000] PERCPU: Allocating 69632 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 1, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 239469
[    0.000000] Kernel command line: root=UUID=5ec2828d-360a-436b-9da6-eeea001249aa ro quiet splash 
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1800.063 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 7, 524288 bytes)
[    0.004000] allocated 10485760 bytes of page_cgroup
[    0.004000] please try cgroup_disable=memory option if you don't want
[    0.004000] Scanning for low memory corruption every 60 seconds
[    0.004000] Checking aperture...
[    0.004000] AGP bridge at 00:00:00
[    0.004000] Aperture from AGP @ e0000000 old size 32 MB
[    0.004000] Aperture from AGP @ e0000000 size 32 MB (APSIZE f38)
[    0.004000] Node 0: aperture @ e0000000 size 32 MB
[    0.004000] Aperture too small (32 MB) than (64 MB)
[    0.004000] Memory: 936924k/981952k available (4760k kernel code, 492k absent, 43820k reserved, 2540k data, 536k init)
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.004014] Calibrating delay loop (skipped), value calculated using timer frequency.. 3600.12 BogoMIPS (lpj=7200252)
[    0.004047] Security Framework initialized
[    0.004058] SELinux:  Disabled at boot.
[    0.004084] AppArmor: AppArmor initialized
[    0.004095] Mount-cache hash table entries: 256
[    0.004297] Initializing cgroup subsys ns
[    0.004302] Initializing cgroup subsys cpuacct
[    0.004304] Initializing cgroup subsys memory
[    0.004309] Initializing cgroup subsys freezer
[    0.004325] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004328] CPU: L2 Cache: 1024K (64 bytes/line)
[    0.004330] tseg: 003bf00000
[    0.004348] SMP alternatives: switching to UP code
[    0.131376] Freeing SMP alternatives: 37k freed
[    0.132025] ACPI: Core revision 20080926
[    0.133571] ACPI: Checking initramfs for custom DSDT
[    0.452059] Setting APIC routing to flat
[    0.452509] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.497089] CPU0: AMD Turion(tm) 64 Mobile Technology ML-34 stepping 02
[    0.500001] Brought up 1 CPUs
[    0.500001] Total of 1 processors activated (3600.12 BogoMIPS).
[    0.500001] CPU0 attaching NULL sched-domain.
[    0.500001] net_namespace: 1400 bytes
[    0.500001] Booting paravirtualized kernel on bare hardware
[    0.500001] Time: 18:01:47  Date: 07/11/09
[    0.500001] regulator: core version 0.5
[    0.500001] NET: Registered protocol family 16
[    0.500001] node 0 link 0: io port [0, fffff]
[    0.500001] TOM: 0000000040000000 aka 1024M
[    0.500001] node 0 link 0: mmio [a0000, bffff]
[    0.500001] node 0 link 0: mmio [40000000, fe0bffff]
[    0.500001] bus: [00,ff] on node 0 link 0
[    0.500001] bus: 00 index 0 io port: [0, ffff]
[    0.500001] bus: 00 index 1 mmio: [a0000, bffff]
[    0.500001] bus: 00 index 2 mmio: [40000000, fcffffffff]
[    0.500001] ACPI: bus type pci registered
[    0.500001] PCI: Using configuration type 1 for base access
[    0.500001] ACPI: EC: Look up EC in DSDT
[    0.501513] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.524061] ACPI: Interpreter enabled
[    0.524063] ACPI: (supports S0 S3 S4 S5)
[    0.524078] ACPI: Using IOAPIC for interrupt routing
[    0.529834] ACPI: EC: GPE = 0x19, I/O: command/status = 0x66, data = 0x62
[    0.529837] ACPI: EC: driver started in interrupt mode
[    0.529917] ACPI: No dock devices found.
[    0.529926] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.529976] pci 0000:00:00.0: reg 10 32bit mmio: [0xe0000000-0xe1ffffff]
[    0.530056] pci 0000:00:02.0: Enabling SiS 96x SMBus
[    0.530084] pci 0000:00:02.1: reg 20 io port: [0x8100-0x811f]
[    0.530108] pci 0000:00:02.5: reg 10 io port: [0x1f0-0x1f7]
[    0.530112] pci 0000:00:02.5: reg 14 io port: [0x3f4-0x3f7]
[    0.530117] pci 0000:00:02.5: reg 18 io port: [0x170-0x177]
[    0.530122] pci 0000:00:02.5: reg 1c io port: [0x374-0x377]
[    0.530126] pci 0000:00:02.5: reg 20 io port: [0x2000-0x200f]
[    0.530155] pci 0000:00:02.6: reg 10 io port: [0x1000-0x10ff]
[    0.530160] pci 0000:00:02.6: reg 14 io port: [0x1c00-0x1c7f]
[    0.530181] pci 0000:00:02.6: supports D1 D2
[    0.530184] pci 0000:00:02.6: PME# supported from D3hot D3cold
[    0.530188] pci 0000:00:02.6: PME# disabled
[    0.530211] pci 0000:00:02.7: reg 10 io port: [0x1400-0x14ff]
[    0.530216] pci 0000:00:02.7: reg 14 io port: [0x1c80-0x1cff]
[    0.530237] pci 0000:00:02.7: supports D1 D2
[    0.530239] pci 0000:00:02.7: PME# supported from D3hot D3cold
[    0.530243] pci 0000:00:02.7: PME# disabled
[    0.530258] pci 0000:00:03.0: reg 10 32bit mmio: [0xe2002000-0xe2002fff]
[    0.530290] pci 0000:00:03.1: reg 10 32bit mmio: [0xe2003000-0xe2003fff]
[    0.530327] pci 0000:00:03.2: reg 10 32bit mmio: [0xe2004000-0xe2004fff]
[    0.530349] pci 0000:00:03.2: PME# supported from D0 D3hot D3cold
[    0.530352] pci 0000:00:03.2: PME# disabled
[    0.530378] pci 0000:00:04.0: reg 10 io port: [0x1800-0x18ff]
[    0.530383] pci 0000:00:04.0: reg 14 32bit mmio: [0xe2005000-0xe2005fff]
[    0.530399] pci 0000:00:04.0: reg 30 32bit mmio: [0x000000-0x01ffff]
[    0.530406] pci 0000:00:04.0: supports D1 D2
[    0.530408] pci 0000:00:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.530411] pci 0000:00:04.0: PME# disabled
[    0.530435] pci 0000:00:06.0: reg 10 32bit mmio: [0x000000-0x000fff]
[    0.530443] pci 0000:00:06.0: supports D1 D2
[    0.530444] pci 0000:00:06.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.530448] pci 0000:00:06.0: PME# disabled
[    0.530466] pci 0000:00:0b.0: reg 10 32bit mmio: [0xe2000000-0xe2001fff]
[    0.530578] pci 0000:01:00.0: reg 10 32bit mmio: [0xe8000000-0xefffffff]
[    0.530582] pci 0000:01:00.0: reg 14 32bit mmio: [0xe2100000-0xe211ffff]
[    0.530586] pci 0000:01:00.0: reg 18 io port: [0xa000-0xa07f]
[    0.530596] pci 0000:01:00.0: supports D1 D2
[    0.530614] pci 0000:00:01.0: bridge io port: [0xa000-0xafff]
[    0.530617] pci 0000:00:01.0: bridge 32bit mmio: [0xe2100000-0xe21fffff]
[    0.530621] pci 0000:00:01.0: bridge 32bit mmio pref: [0xe8000000-0xefffffff]
[    0.530639] bus 00 -> node 0
[    0.530645] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.537218] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 *7 9 10 11)
[    0.537322] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 *4 5 7 9 10 11)
[    0.537422] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 7 9 10 11)
[    0.537522] ACPI: PCI Interrupt Link [LNKD] (IRQs *3 4 5 7 9 10 11)
[    0.537642] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 *9 10 11)
[    0.537741] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 *11)
[    0.537837] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 9 10 11) *0, disabled.
[    0.537934] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 *10 11)
[    0.538048] ACPI: WMI: Mapper loaded
[    0.538204] SCSI subsystem initialized
[    0.538243] libata version 3.00 loaded.
[    0.538292] usbcore: registered new interface driver usbfs
[    0.538308] usbcore: registered new interface driver hub
[    0.538338] usbcore: registered new device driver usb
[    0.538445] PCI: Using ACPI for IRQ routing
[    0.538454] pci 0000:00:00.0: BAR 0: can't allocate resource
[    0.548009] Bluetooth: Core ver 2.13
[    0.548054] NET: Registered protocol family 31
[    0.548056] Bluetooth: HCI device and connection manager initialized
[    0.548059] Bluetooth: HCI socket layer initialized
[    0.548062] NET: Registered protocol family 8
[    0.548063] NET: Registered protocol family 20
[    0.548074] NetLabel: Initializing
[    0.548075] NetLabel:  domain hash size = 128
[    0.548077] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.548094] NetLabel:  unlabeled traffic allowed by default
[    0.548128] agpgart-amd64 0000:00:00.0: AGP bridge [1039/0760]
[    0.549925] agpgart-amd64 0000:00:00.0: AGP aperture is 32M @ 0xe0000000
[    0.550035] AppArmor: AppArmor Filesystem Enabled
[    0.560014] pnp: PnP ACPI init
[    0.560022] ACPI: bus type pnp registered
[    0.561859] pnp: PnP ACPI: found 8 devices
[    0.561861] ACPI: ACPI bus type pnp unregistered
[    0.561871] system 00:04: ioport range 0x8000-0x807f has been reserved
[    0.561874] system 00:04: ioport range 0x8080-0x80ff has been reserved
[    0.561880] system 00:04: ioport range 0x8100-0x811f has been reserved
[    0.561883] system 00:04: ioport range 0x4d0-0x4d1 has been reserved
[    0.561886] system 00:04: ioport range 0x3f0-0x3f1 has been reserved
[    0.561889] system 00:04: iomem range 0xfec00000-0xfecfffff has been reserved
[    0.561892] system 00:04: iomem range 0xfed00000-0xfed003ff has been reserved
[    0.561894] system 00:04: iomem range 0xfee00000-0xfeefffff has been reserved
[    0.561897] system 00:04: iomem range 0xffc00000-0xffc00fff has been reserved
[    0.561900] system 00:04: iomem range 0xffe00000-0xffe00fff has been reserved
[    0.561902] system 00:04: iomem range 0xffe80000-0xffefffff has been reserved
[    0.561905] system 00:04: iomem range 0xfffe0000-0xfffeffff has been reserved
[    0.561907] system 00:04: iomem range 0xffff0000-0xffffffff has been reserved
[    0.566583] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.566587] pci 0000:00:01.0:   IO window: 0xa000-0xafff
[    0.566591] pci 0000:00:01.0:   MEM window: 0xe2100000-0xe21fffff
[    0.566595] pci 0000:00:01.0:   PREFETCH window: 0x000000e8000000-0x000000efffffff
[    0.566600] pci 0000:00:06.0: CardBus bridge, secondary bus 0000:02
[    0.566602] pci 0000:00:06.0:   IO window: 0x002400-0x0024ff
[    0.566606] pci 0000:00:06.0:   IO window: 0x002800-0x0028ff
[    0.566609] pci 0000:00:06.0:   PREFETCH window: 0x50000000-0x53ffffff
[    0.566613] pci 0000:00:06.0:   MEM window: 0x54000000-0x57ffffff
[    0.566625] pci 0000:00:06.0: enabling device (0000 -> 0003)
[    0.566634] pci 0000:00:06.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.566639] bus: 00 index 0 io port: [0x00-0xffff]
[    0.566641] bus: 00 index 1 mmio: [0x000000-0xffffffffffffffff]
[    0.566644] bus: 01 index 0 io port: [0xa000-0xafff]
[    0.566646] bus: 01 index 1 mmio: [0xe2100000-0xe21fffff]
[    0.566648] bus: 01 index 2 mmio: [0xe8000000-0xefffffff]
[    0.566649] bus: 01 index 3 mmio: [0x0-0x0]
[    0.566651] bus: 02 index 0 io port: [0x2400-0x24ff]
[    0.566653] bus: 02 index 1 io port: [0x2800-0x28ff]
[    0.566655] bus: 02 index 2 mmio: [0x50000000-0x53ffffff]
[    0.566657] bus: 02 index 3 mmio: [0x54000000-0x57ffffff]
[    0.566668] NET: Registered protocol family 2
[    0.600055] IP route cache hash table entries: 32768 (order: 6, 262144 bytes)
[    0.600399] TCP established hash table entries: 131072 (order: 9, 2097152 bytes)
[    0.602554] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.603796] TCP: Hash tables configured (established 131072 bind 65536)
[    0.603800] TCP reno registered
[    0.612131] NET: Registered protocol family 1
[    0.612291] checking if image is initramfs... it is
[    1.068038] Switched to high resolution mode on CPU 0
[    1.266024] Freeing initrd memory: 7762k freed
[    1.275087] Simple Boot Flag at 0x38 set to 0x1
[    1.275377] audit: initializing netlink socket (disabled)
[    1.275398] type=2000 audit(1247335307.272:1): initialized
[    1.284321] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.285607] VFS: Disk quotas dquot_6.5.1
[    1.285673] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.286244] fuse init (API version 7.10)
[    1.286319] msgmni has been set to 1846
[    1.286490] alg: No test for stdrng (krng)
[    1.286502] io scheduler noop registered
[    1.286503] io scheduler anticipatory registered
[    1.286505] io scheduler deadline registered
[    1.286542] io scheduler cfq registered (default)
[    1.707087] pci 0000:01:00.0: Boot video device
[    1.708031] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.708039] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.710233] ACPI: AC Adapter [ACAD] (on-line)
[    1.710285] ACPI: Battery Slot [BAT1] (battery absent)
[    1.710351] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.710354] ACPI: Power Button (FF) [PWRF]
[    1.710403] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
[    1.713136] ACPI: Lid Switch [LID]
[    1.713185] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input2
[    1.713187] ACPI: Power Button (CM) [PWRB]
[    1.713231] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input3
[    1.713233] ACPI: Sleep Button (CM) [SLPB]
[    1.713409] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    1.713432] processor ACPI_CPU:00: registered as cooling_device0
[    1.717646] thermal LNXTHERM:01: registered as thermal_zone0
[    1.723424] ACPI: Thermal Zone [THRM] (69 C)
[    1.760132] Linux agpgart interface v0.103
[    1.760140] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.760378] serial 0000:00:02.6: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.760383] serial 0000:00:02.6: PCI INT C disabled
[    1.761038] brd: module loaded
[    1.761346] loop: module loaded
[    1.761411] Fixed MDIO Bus: probed
[    1.761417] PPP generic driver version 2.4.2
[    1.761473] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    1.761498] Driver 'sd' needs updating - please use bus_type methods
[    1.761506] Driver 'sr' needs updating - please use bus_type methods
[    1.761999] pata_sis 0000:00:02.5: version 0.5.2
[    1.762008] pata_sis 0000:00:02.5: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.762194] scsi0 : pata_sis
[    1.762302] scsi1 : pata_sis
[    1.762472] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x2000 irq 14
[    1.762475] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x2008 irq 15
[    1.925973] ata1.00: ATA-6: ST9100825A, 3.06, max UDMA/100
[    1.925976] ata1.00: 195371568 sectors, multi 16: LBA48 
[    1.940792] ata1.00: configured for UDMA/100
[    2.104204] ata2.00: ATAPI: Slimtype DVDRW SOSW-833S, VRS2, max UDMA/33
[    2.120219] ata2.00: configured for UDMA/33
[    2.120543] isa bounce pool size: 16 pages
[    2.120647] scsi 0:0:0:0: Direct-Access     ATA      ST9100825A       3.06 PQ: 0 ANSI: 5
[    2.120735] sd 0:0:0:0: [sda] 195371568 512-byte hardware sectors: (100 GB/93.1 GiB)
[    2.120752] sd 0:0:0:0: [sda] Write Protect is off
[    2.120755] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.120779] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.120839] sd 0:0:0:0: [sda] 195371568 512-byte hardware sectors: (100 GB/93.1 GiB)
[    2.120852] sd 0:0:0:0: [sda] Write Protect is off
[    2.120854] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.120877] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.120881]  sda: sda1 sda2 < sda5 >
[    2.220982] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.221027] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.221873] scsi 1:0:0:0: CD-ROM            Slimtype DVDRW SOSW-833S  VRS2 PQ: 0 ANSI: 5
[    2.224567] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    2.224570] Uniform CD-ROM driver Revision: 3.20
[    2.224658] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.224689] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.224790] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.224812] ehci_hcd 0000:00:03.2: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    2.224838] ehci_hcd 0000:00:03.2: EHCI Host Controller
[    2.224897] ehci_hcd 0000:00:03.2: new USB bus registered, assigned bus number 1
[    2.224942] ehci_hcd 0000:00:03.2: cache line size of 64 is not supported
[    2.224963] ehci_hcd 0000:00:03.2: irq 23, io mem 0xe2004000
[    2.236005] ehci_hcd 0000:00:03.2: USB 2.0 started, EHCI 1.00
[    2.236087] usb usb1: configuration #1 chosen from 1 choice
[    2.236116] hub 1-0:1.0: USB hub found
[    2.236126] hub 1-0:1.0: 6 ports detected
[    2.236238] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.236255] ohci_hcd 0000:00:03.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    2.236265] ohci_hcd 0000:00:03.0: OHCI Host Controller
[    2.236313] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 2
[    2.236335] ohci_hcd 0000:00:03.0: irq 20, io mem 0xe2002000
[    2.292063] usb usb2: configuration #1 chosen from 1 choice
[    2.292096] hub 2-0:1.0: USB hub found
[    2.292106] hub 2-0:1.0: 3 ports detected
[    2.292183] ohci_hcd 0000:00:03.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    2.292192] ohci_hcd 0000:00:03.1: OHCI Host Controller
[    2.292235] ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 3
[    2.292257] ohci_hcd 0000:00:03.1: irq 21, io mem 0xe2003000
[    2.348063] usb usb3: configuration #1 chosen from 1 choice
[    2.348086] hub 3-0:1.0: USB hub found
[    2.348095] hub 3-0:1.0: 3 ports detected
[    2.348173] uhci_hcd: USB Universal Host Controller Interface driver
[    2.348226] usbcore: registered new interface driver libusual
[    2.348259] usbcore: registered new interface driver usbserial
[    2.348269] USB Serial support registered for generic
[    2.348284] usbcore: registered new interface driver usbserial_generic
[    2.348287] usbserial: USB Serial Driver core
[    2.348325] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    2.351365] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.351371] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.360033] mice: PS/2 mouse device common for all mice
[    2.420045] rtc_cmos 00:02: RTC can wake from S4
[    2.420086] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    2.420109] rtc0: alarms up to one year, y3k, 114 bytes nvram
[    2.420163] device-mapper: uevent: version 1.0.3
[    2.420276] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[    2.420323] device-mapper: multipath: version 1.0.5 loaded
[    2.420326] device-mapper: multipath round-robin: version 1.0.0 loaded
[    2.420437] cpuidle: using governor ladder
[    2.420494] cpuidle: using governor menu
[    2.420927] TCP cubic registered
[    2.420995] NET: Registered protocol family 10
[    2.421382] lo: Disabled Privacy Extensions
[    2.421669] NET: Registered protocol family 17
[    2.421694] Bluetooth: L2CAP ver 2.11
[    2.421695] Bluetooth: L2CAP socket layer initialized
[    2.421698] Bluetooth: SCO (Voice Link) ver 0.6
[    2.421699] Bluetooth: SCO socket layer initialized
[    2.421725] Bluetooth: RFCOMM socket layer initialized
[    2.421730] Bluetooth: RFCOMM TTY layer initialized
[    2.421732] Bluetooth: RFCOMM ver 1.10
[    2.421751] powernow-k8: Found 1 AMD Turion(tm) 64 Mobile Technology ML-34 processors (1 cpu cores) (version 2.20.00)
[    2.421797] powernow-k8:    0 : fid 0xa (1800 MHz), vid 0x4
[    2.421799] powernow-k8:    1 : fid 0x8 (1600 MHz), vid 0x6
[    2.421801] powernow-k8:    2 : fid 0x0 (800 MHz), vid 0x16
[    2.421909] registered taskstats version 1
[    2.422029]   Magic number: 1:702:38
[    2.422041] bdi 7:3: hash matches
[    2.422102] rtc_cmos 00:02: setting system clock to 2009-07-11 18:01:49 UTC (1247335309)
[    2.422105] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.422107] EDD information not available.
[    2.422150] Freeing unused kernel memory: 536k freed
[    2.422638] Write protecting the kernel read-only data: 6708k
[    2.465370] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    2.572024] usb 1-3: new high speed USB device using ehci_hcd and address 2
[    2.713174] usb 1-3: configuration #1 chosen from 1 choice
[    2.728538] Initializing USB Mass Storage driver...
[    2.737261] scsi2 : SCSI emulation for USB Mass Storage devices
[    2.744024] usbcore: registered new interface driver usb-storage
[    2.744027] USB Mass Storage support registered.
[    2.744125] usb-storage: device found at 2
[    2.744126] usb-storage: waiting for device to settle before scanning
[    3.125423] sis900.c: v1.08.10 Apr. 2 2006
[    3.125468] sis900 0000:00:04.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    3.130204] 0000:00:04.0: Realtek RTL8201 PHY transceiver found at address 13.
[    3.136113] 0000:00:04.0: Using transceiver found at address 13 as default
[    3.137400] eth0: SiS 900 PCI Fast Ethernet at 0x1800, IRQ 19, 00:16:36:34:dd:a0
[    3.145132] b43-pci-bridge 0000:00:0b.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    3.204106] ssb: Sonics Silicon Backplane found on PCI device 0000:00:0b.0
[    3.408003] Marking TSC unstable due to TSC halts in idle
[    3.459515] PM: Starting manual resume from disk
[    3.459519] PM: Resume from partition 8:5
[    3.459520] PM: Checking hibernation image.
[    3.459704] PM: Resume from disk failed.
[    3.501767] kjournald starting.  Commit interval 5 seconds
[    3.501778] EXT3-fs: mounted filesystem with ordered data mode.
[    7.744493] usb-storage: device scan complete
[    7.745568] scsi 2:0:0:0: Direct-Access              Patriot Memory   PMAP PQ: 0 ANSI: 0 CCS
[    7.746422] sd 2:0:0:0: [sdb] 15663104 512-byte hardware sectors: (8.01 GB/7.46 GiB)
[    7.746921] sd 2:0:0:0: [sdb] Write Protect is off
[    7.746924] sd 2:0:0:0: [sdb] Mode Sense: 23 00 00 00
[    7.746926] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[    7.748423] sd 2:0:0:0: [sdb] 15663104 512-byte hardware sectors: (8.01 GB/7.46 GiB)
[    7.748920] sd 2:0:0:0: [sdb] Write Protect is off
[    7.748922] sd 2:0:0:0: [sdb] Mode Sense: 23 00 00 00
[    7.748924] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[    7.748928]  sdb: sdb1
[    7.749533] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[    7.749593] sd 2:0:0:0: Attached scsi generic sg2 type 0
[   10.313665] udev: starting version 141
[   10.509545] sis96x_smbus 0000:00:02.1: SiS96x SMBus base address: 0x8100
[   10.653043] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   10.785401] yenta_cardbus 0000:00:06.0: CardBus bridge found [1025:0083]
[   10.785419] yenta_cardbus 0000:00:06.0: Using CSCINT to route CSC interrupts to PCI
[   10.785421] yenta_cardbus 0000:00:06.0: Routing CardBus interrupts to PCI
[   10.785426] yenta_cardbus 0000:00:06.0: TI: mfunc 0x00521d22, devctl 0x64
[   10.970302] input: PC Speaker as /devices/platform/pcspkr/input/input6
[   11.017283] yenta_cardbus 0000:00:06.0: ISA IRQ mask 0x06f8, PCI irq 19
[   11.017288] yenta_cardbus 0000:00:06.0: Socket status: 30000007
[   11.300779] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[   11.355211] acer-wmi: Acer Laptop ACPI-WMI Extras
[   11.355224] acer-wmi: No or unsupported WMI interface, unable to load
[   11.384101] cfg80211: Calling CRDA to update world regulatory domain
[   11.489440] cfg80211: World regulatory domain updated:
[   11.489444]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   11.489447]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   11.489449]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   11.489452]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   11.489454]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   11.489456]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   11.718651] b43-phy0: Broadcom 4318 WLAN found
[   11.784980] phy0: Selected rate control algorithm 'pid'
[   11.927201] Broadcom 43xx driver loaded [ Features: PLR, Firmware-ID: FW13 ]
[   11.943892] Intel ICH 0000:00:02.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[   12.135588] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x12a0b1, caps: 0xa04713/0x204000
[   12.169728] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input7
[   12.768025] intel8x0_measure_ac97_clock: measured 55354 usecs
[   12.768029] intel8x0: clocking to 48000
[   12.930165] lp: driver loaded but no devices found
[   13.011562] Adding 2763140k swap on /dev/sda5.  Priority:-1 extents:1 across:2763140k
[   13.554023] EXT3 FS on sda1, internal journal
[   14.638732] type=1505 audit(1247335321.713:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=1912
[   14.689240] type=1505 audit(1247335321.765:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=1916
[   14.689450] type=1505 audit(1247335321.765:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=1916
[   14.689520] type=1505 audit(1247335321.765:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=1916
[   14.689580] type=1505 audit(1247335321.765:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=1916
[   14.837393] type=1505 audit(1247335321.913:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=1921
[   14.837692] type=1505 audit(1247335321.913:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=1921
[   14.871060] type=1505 audit(1247335321.945:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=1925
[   17.330483] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   17.330486] Bluetooth: BNEP filters: protocol multicast
[   17.361726] Bridge firewalling registered
[   19.216028] ppdev: user-space parallel port driver
[   22.923388] eth0: Media Link Off
[   22.923746] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   23.008279] input: b43-phy0 as /devices/virtual/input/input8
[   23.096043] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[   23.158105] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   23.158111] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the latest firmware (version 4).
[   23.241329] input: b43-phy0 as /devices/virtual/input/input9
[   23.304084] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[   23.306910] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   23.306917] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the latest firmware (version 4).
[   82.064091] Clocksource tsc unstable (delta = -277810783 ns)
[ 1864.664226] usb 1-3: USB disconnect, address 2
[ 1864.960082] usb 1-3: new high speed USB device using ehci_hcd and address 3
[ 1865.016050] hub 1-0:1.0: unable to enumerate USB device on port 3
[ 1966.140040] usb 1-3: new high speed USB device using ehci_hcd and address 4
[ 1966.314014] usb 1-3: configuration #1 chosen from 1 choice
[ 1966.352245] scsi3 : SCSI emulation for USB Mass Storage devices
[ 1966.355192] usb-storage: device found at 4
[ 1966.355197] usb-storage: waiting for device to settle before scanning
[ 1971.352574] usb-storage: device scan complete
[ 1971.353669] scsi 3:0:0:0: Direct-Access              Patriot Memory   PMAP PQ: 0 ANSI: 0 CCS
[ 1972.357142] sd 3:0:0:0: [sdb] 15663104 512-byte hardware sectors: (8.01 GB/7.46 GiB)
[ 1972.357624] sd 3:0:0:0: [sdb] Write Protect is off
[ 1972.357631] sd 3:0:0:0: [sdb] Mode Sense: 23 00 00 00
[ 1972.357637] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[ 1972.362521] sd 3:0:0:0: [sdb] 15663104 512-byte hardware sectors: (8.01 GB/7.46 GiB)
[ 1972.362999] sd 3:0:0:0: [sdb] Write Protect is off
[ 1972.363005] sd 3:0:0:0: [sdb] Mode Sense: 23 00 00 00
[ 1972.363010] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[ 1972.363019]  sdb: sdb1
[ 1972.363895] sd 3:0:0:0: [sdb] Attached SCSI removable disk
[ 1972.366904] sd 3:0:0:0: Attached scsi generic sg2 type 0
[/INDENT][B]6 ) Network configuration:
[/B][INDENT]justinyl@justinyl-laptop:~$ sudo lshw -C network
[sudo] password for justinyl: 
  *-network:0             
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 91
       serial: 00:16:36:34:dd:a0
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 duplex=half latency=173 link=no maxlatency=11 mingnt=52 module=sis900 multicast=yes port=MII speed=10MB/s
  *-network:1
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: b
       bus info: pci@0000:00:0b.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:16:ce:36:cb:71
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
[/INDENT][B]7 ) Scan for networks:
[/B][INDENT]Result of 'iwlist scan':
lo              Interface doesn't support scanning.
eth0          Interface doesn't support scanning.
wmaster0  Interface doesn't support scanning.
wlan0        No scan results
[/INDENT]**8 ) Ubuntu Version: **Ubuntu 9.04**9 ) Kernel/architecture (including 32 vs. 64 bit): **2.6.28-11-generic x86_64**10 ) Restarting the network:**[INDENT]Result of 'sudo /etc/init.d/networking restart':
* Reconfiguring network interfaces...    [ OK ]
[/INDENT]

---

