---
title: "Hardy, sound not working anymore"
date: 2008-05-11
forum: Multimedia Software
---

### Post by mr.snuff on 2008-05-11
Hi all,

I know there are a lot of posts regarding sound issues already. I think I read most of them, searched this forum and via Google for possible solutions. Unfortunately, all the solutions and bug fixes I tried didn't work for me. Therefore, I'm now hoping that by posting my concrete problem, someone here will be able to help me.

My story is the following: I installed Ubuntu Hardy 64bit version fresh from CD two days after the final release. Everything seemed to work fine and I had sound as well. Then, from one day to the other (about 3 weeks ago), my sound stopped working. Unfortunately, I can't exactly recall if there was an Ubuntu update that might have changed the settings or so. I myself didn't change anything sound-related.

I'm not an expert when it comes to Ubuntu, so I don't really have an idea what is wrong with my system. The sound devices seem to be recognized correctly and I don't get any error messages when I open volume control or so.

I even followed instructions and recompiled alsa, all without success. Hopefully, someone here can help me to fix this annoying problem.

Here are some information about my system. Please let me know if you need anything else!

Lenovo Thinkpad T61

```
$ lspci -v
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
	Subsystem: Lenovo ThinkPad T61
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at fe020000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

```

```
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

```
$ lsmod
Module                  Size  Used by
ath_pci               107824  0 
e1000                 137152  0 
wlan_wep                8704  1 
af_packet              27272  4 
ipv6                  311720  10 
i915                   38144  2 
drm                   106152  3 i915
rfcomm                 47392  2 
l2cap                  28800  13 rfcomm
bluetooth              67748  4 rfcomm,l2cap
vboxdrv              1649152  0 
uinput                 11904  1 
ppdev                  11400  0 
acpi_cpufreq           10832  2 
cpufreq_powersave       3200  0 
cpufreq_stats           8416  0 
cpufreq_userspace       6180  0 
cpufreq_ondemand       11152  1 
cpufreq_conservative    10632  0 
freq_table              6464  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
container               6656  0 
sbs                    17808  0 
bay                     8064  0 
sbshc                   8960  1 sbs
dock                   12960  1 bay
iptable_filter          4608  0 
ip_tables              24104  1 iptable_filter
x_tables               23560  1 ip_tables
nls_utf8                3456  1 
nls_cp437               8320  1 
vfat                   16256  1 
fat                    60592  1 vfat
sbp2                   27272  0 
parport_pc             41128  0 
lp                     14916  0 
parport                44300  3 ppdev,parport_pc,lp
joydev                 15488  0 
snd_hda_intel         460376  4 
snd_hwdep              12680  1 snd_hda_intel
pcmcia                 45976  0 
snd_seq_dummy           6020  0 
snd_seq_oss            38912  0 
snd_seq_midi           10944  0 
snd_pcm_oss            48032  0 
snd_mixer_oss          20352  1 snd_pcm_oss
snd_rawmidi            30112  1 snd_seq_midi
snd_seq_midi_event     10368  2 snd_seq_oss,snd_seq_midi
snd_pcm                92552  3 snd_hda_intel,snd_pcm_oss
thinkpad_acpi          60304  0 
sdhci                  21508  0 
yenta_socket           30092  1 
wlan_scan_sta          16512  1 
psmouse                46236  0 
nvram                  11400  2 thinkpad_acpi
snd_seq                63232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
rsrc_nonstatic         14080  1 yenta_socket
ath_rate_sample        15744  1 
snd_page_alloc         13456  2 snd_hda_intel,snd_pcm
serio_raw               9092  0 
mmc_core               59272  1 sdhci
pcspkr                  4992  0 
pcmcia_core            46116  3 pcmcia,yenta_socket,rsrc_nonstatic
evdev                  14976  9 
ricoh_mmc               5120  0 
battery                16776  0 
iTCO_wdt               15312  0 
iTCO_vendor_support     5764  1 iTCO_wdt
wlan                  227104  5 ath_pci,wlan_wep,wlan_scan_sta,ath_rate_sample
snd_timer              28168  2 snd_pcm,snd_seq
snd_seq_device         10772  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ath_hal               219888  3 ath_pci,ath_rate_sample
ac                      8328  0 
video                  23444  0 
output                  5632  1 video
snd                    71240  18 snd_hda_intel,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_pcm_oss,snd_mixer_oss,snd_rawmidi,snd_pcm,snd_seq,snd_timer,snd_seq_device
soundcore              10400  1 snd
shpchp                 38172  0 
pci_hotplug            34608  1 shpchp
button                 10912  0 
intel_agp              30624  1 
reiserfs              246912  2 
usbhid                 35168  0 
hid                    44992  1 usbhid
sg                     41880  0 
sr_mod                 20132  0 
cdrom                  41512  1 sr_mod
sd_mod                 33280  5 
ata_piix               24196  4 
ata_generic             9988  0 
pata_acpi               9856  0 
ohci1394               36532  0 
libata                176304  3 ata_piix,ata_generic,pata_acpi
scsi_mod              178488  5 sbp2,sg,sr_mod,sd_mod,libata
ieee1394              106968  2 sbp2,ohci1394
ehci_hcd               41996  0 
uhci_hcd               29856  0 
usbcore               169904  4 usbhid,ehci_hcd,uhci_hcd
thermal                19744  0 
processor              41448  4 acpi_cpufreq,thermal
fan                     6792  0 
fbcon                  46336  0 
tileblit                4096  1 fbcon
font                   10112  1 fbcon
bitblit                 7424  1 fbcon
softcursor              3712  1 bitblit
fuse                   56112  3 

```

```
$ dmesg
[    0.000000] Linux version 2.6.24-16-generic (buildd@yellow) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Thu Apr 10 12:47:45 UTC 2008 (Ubuntu 2.6.24-16.30-generic)
[    0.000000] Command line: root=UUID=e407827b-d549-4d5d-b937-8736e76667b2 ro quiet splash
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009d800 (usable)
[    0.000000]  BIOS-e820: 000000000009d800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d2000 - 00000000000d4000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007d6b0000 (usable)
[    0.000000]  BIOS-e820: 000000007d6b0000 - 000000007d6cd000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007d6cd000 - 000000007d700000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007d700000 - 000000007e000000 (reserved)
[    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] Entering add_active_range(0, 0, 157) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 513712) 1 entries of 3200 used
[    0.000000] end_pfn_map = 1048576
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP signature @ 0xFFFF8100000F68D0 checksum 0
[    0.000000] ACPI: RSDP 000F68D0, 0024 (r2 LENOVO)
[    0.000000] ACPI: XSDT 7D6BDFB8, 009C (r1 LENOVO TP-7L        1070  LTP        0)
[    0.000000] ACPI: FACP 7D6BE100, 00F4 (r3 LENOVO TP-7L        1070 LNVO        1)
[    0.000000] ACPI Warning (tbfadt-0442): Optional field "Gpe1Block" has zero address or length: 000000000000102C/0 [20070126]
[    0.000000] ACPI: DSDT 7D6BE50C, E6A9 (r1 LENOVO TP-7L        1070 MSFT  3000000)
[    0.000000] ACPI: FACS 7D6E4000, 0040
[    0.000000] ACPI: SSDT 7D6BE2B4, 0258 (r1 LENOVO TP-7L        1070 MSFT  3000000)
[    0.000000] ACPI: ECDT 7D6CCBB5, 0052 (r1 LENOVO TP-7L        1070 LNVO        1)
[    0.000000] ACPI: TCPA 7D6CCC07, 0032 (r2 LENOVO TP-7L        1070 LNVO        1)
[    0.000000] ACPI: APIC 7D6CCC39, 0068 (r1 LENOVO TP-7L        1070 LNVO        1)
[    0.000000] ACPI: MCFG 7D6CCCA1, 003C (r1 LENOVO TP-7L        1070 LNVO        1)
[    0.000000] ACPI: HPET 7D6CCCDD, 0038 (r1 LENOVO TP-7L        1070 LNVO        1)
[    0.000000] ACPI: SLIC 7D6CCDF0, 0176 (r1 LENOVO TP-7L        1070  LTP        0)
[    0.000000] ACPI: BOOT 7D6CCF66, 0028 (r1 LENOVO TP-7L        1070  LTP        1)
[    0.000000] ACPI: ASF! 7D6CCF8E, 0072 (r16 LENOVO TP-7L        1070 PTL         1)
[    0.000000] ACPI: SSDT 7D6E26D9, 025F (r1 LENOVO TP-7L        1070 INTL 20050513)
[    0.000000] ACPI: SSDT 7D6E2938, 00A6 (r1 LENOVO TP-7L        1070 INTL 20050513)
[    0.000000] ACPI: SSDT 7D6E29DE, 04F7 (r1 LENOVO TP-7L        1070 INTL 20050513)
[    0.000000] ACPI: SSDT 7D6E2ED5, 08BD (r1 LENOVO TP-7L        1070 INTL 20050513)
[    0.000000] ACPI: SSDT 7D6E3792, 069C (r1 LENOVO TP-7L        1070 INTL 20050513)
[    0.000000] ACPI: DMI detected: Lenovo ThinkPad T61
[    0.000000] ACPI: Added _OSI(Linux)
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000007d6b0000
[    0.000000] Entering add_active_range(0, 0, 157) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 513712) 1 entries of 3200 used
[    0.000000] Bootmem setup node 0 0000000000000000-000000007d6b0000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   DMA32        4096 ->  1048576
[    0.000000]   Normal    1048576 ->  1048576
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0:        0 ->      157
[    0.000000]     0:      256 ->   513712
[    0.000000] On node 0 totalpages: 513613
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 1208 pages reserved
[    0.000000]   DMA zone: 2733 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 6967 pages used for memmap
[    0.000000]   DMA32 zone: 502649 pages, LIFO batch:31
[    0.000000]   Normal zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Setting APIC routing to flat
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] swsusp: Registered nosave memory region: 000000000009d000 - 000000000009e000
[    0.000000] swsusp: Registered nosave memory region: 000000000009e000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000d2000
[    0.000000] swsusp: Registered nosave memory region: 00000000000d2000 - 00000000000d4000
[    0.000000] swsusp: Registered nosave memory region: 00000000000d4000 - 00000000000e0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 7e000000:72000000)
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] PERCPU: Allocating 34656 bytes of per cpu data
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 505382
[    0.000000] Policy zone: DMA32
[    0.000000] Kernel command line: root=UUID=e407827b-d549-4d5d-b937-8736e76667b2 ro quiet splash
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] Extended CMOS year: 2000
[    0.000000] hpet clockevent registered
[    0.000000] TSC calibrated against HPET
[   16.912642] Marking TSC unstable due to TSCs unsynchronized
[   16.912644] time.c: Detected 1995.000 MHz processor.
[   16.913923] Console: colour VGA+ 80x25
[   16.913927] console [tty0] enabled
[   16.913944] Checking aperture...
[   16.913959] Calgary: detecting Calgary via BIOS EBDA area
[   16.913961] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[   16.935192] Memory: 2013816k/2054848k available (2466k kernel code, 40636k reserved, 1309k data, 316k init)
[   16.935223] SLUB: Genslabs=12, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   17.014573] Calibrating delay using timer specific routine.. 3995.41 BogoMIPS (lpj=7990837)
[   17.014607] Security Framework initialized
[   17.014613] SELinux:  Disabled at boot.
[   17.014624] AppArmor: AppArmor initialized
[   17.014627] Failure registering capabilities with primary security module.
[   17.014824] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
[   17.016146] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
[   17.016809] Mount-cache hash table entries: 256
[   17.016945] CPU: L1 I cache: 32K, L1 D cache: 32K
[   17.016947] CPU: L2 cache: 4096K
[   17.016949] CPU 0/0 -> Node 0
[   17.016951] using mwait in idle threads.
[   17.016952] CPU: Physical Processor ID: 0
[   17.016953] CPU: Processor Core ID: 0
[   17.016959] CPU0: Thermal monitoring enabled (TM2)
[   17.016972] SMP alternatives: switching to UP code
[   17.017669] Early unpacking initramfs... done
[   17.331520] ACPI: Core revision 20070126
[   17.331583] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   17.400576] Using local APIC timer interrupts.
[   17.450677] APIC timer calibration result 12468750
[   17.450678] Detected 12.468 MHz APIC timer.
[   17.450752] SMP alternatives: switching to SMP code
[   17.451350] Booting processor 1/2 APIC 0x1
[   17.462040] Initializing CPU#1
[   17.538824] Calibrating delay using timer specific routine.. 3990.06 BogoMIPS (lpj=7980125)
[   17.538830] CPU: L1 I cache: 32K, L1 D cache: 32K
[   17.538832] CPU: L2 cache: 4096K
[   17.538834] CPU 1/1 -> Node 0
[   17.538835] CPU: Physical Processor ID: 0
[   17.538836] CPU: Processor Core ID: 1
[   17.538842] CPU1: Thermal monitoring enabled (TM2)
[   17.539337] Intel(R) Core(TM)2 Duo CPU     T7300  @ 2.00GHz stepping 0a
[   17.539193] Brought up 2 CPUs
[   17.539276] CPU0 attaching sched-domain:
[   17.539278]  domain 0: span 03
[   17.539279]   groups: 01 02
[   17.539282]   domain 1: span 03
[   17.539283]    groups: 03
[   17.539285] CPU1 attaching sched-domain:
[   17.539286]  domain 0: span 03
[   17.539288]   groups: 02 01
[   17.539290]   domain 1: span 03
[   17.539291]    groups: 03
[   17.539497] net_namespace: 120 bytes
[   17.539864] Time: 20:24:02  Date: 05/11/08
[   17.539887] NET: Registered protocol family 16
[   17.540055] ACPI: bus type pci registered
[   17.540128] PCI: Using configuration type 1
[   17.541792] ACPI: EC: EC description table is found, configuring boot EC
[   17.547806] ACPI: EC: non-query interrupt received, switching to interrupt mode
[   17.622145] ACPI: Interpreter enabled
[   17.622147] ACPI: (supports S0 S3 S4 S5)
[   17.622161] ACPI: Using IOAPIC for interrupt routing
[   17.631475] ACPI: EC: GPE = 0x12, I/O: command/status = 0x66, data = 0x62
[   17.631477] ACPI: EC: driver started in poll mode
[   17.631648] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   17.633276] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[   17.633282] PCI quirk: region 1180-11bf claimed by ICH6 GPIO
[   17.634895] PCI: Transparent bridge - 0000:00:1e.0
[   17.635009] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   17.635213] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP0._PRT]
[   17.635345] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP1._PRT]
[   17.635473] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP2._PRT]
[   17.635601] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP3._PRT]
[   17.635732] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP4._PRT]
[   17.635862] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[   17.639772] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 *10 11)
[   17.639991] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11)
[   17.640205] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 *11)
[   17.640420] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11)
[   17.640634] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 *11)
[   17.640848] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 *11)
[   17.641062] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 *11)
[   17.641275] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 *11)
[   17.641450] ACPI: EC: non-query interrupt received, switching to interrupt mode
[   17.641535] ACPI: Power Resource [PUBS] (on)
[   17.641590] Linux Plug and Play Support v0.97 (c) Adam Belay
[   17.641616] pnp: PnP ACPI init
[   17.641622] ACPI: bus type pnp registered
[   17.642872] pnpacpi: exceeded the max number of mem resources: 12
[   17.646302] pnp: PnP ACPI: found 11 devices
[   17.646304] ACPI: ACPI bus type pnp unregistered
[   17.646511] PCI: Using ACPI for IRQ routing
[   17.646513] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   17.662581] NET: Registered protocol family 8
[   17.662582] NET: Registered protocol family 20
[   17.662612] PCI-GART: No AMD northbridge found.
[   17.662619] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   17.662622] hpet0: 3 64-bit timers, 14318180 Hz
[   17.663657] AppArmor: AppArmor Filesystem Enabled
[   17.666575] Time: hpet clocksource has been installed.
[   17.666587] Switched to high resolution mode on CPU 0
[   17.667286] Switched to high resolution mode on CPU 1
[   17.674577] system 00:00: iomem range 0x0-0x9ffff could not be reserved
[   17.674579] system 00:00: iomem range 0xc0000-0xc3fff has been reserved
[   17.674582] system 00:00: iomem range 0xc4000-0xc7fff has been reserved
[   17.674584] system 00:00: iomem range 0xc8000-0xcbfff has been reserved
[   17.674586] system 00:00: iomem range 0xcc000-0xcffff has been reserved
[   17.674588] system 00:00: iomem range 0xd0000-0xd3fff could not be reserved
[   17.674590] system 00:00: iomem range 0x0-0x0 could not be reserved
[   17.674592] system 00:00: iomem range 0x0-0x0 could not be reserved
[   17.674594] system 00:00: iomem range 0x0-0x0 could not be reserved
[   17.674596] system 00:00: iomem range 0xe0000-0xe3fff could not be reserved
[   17.674598] system 00:00: iomem range 0xe4000-0xe7fff could not be reserved
[   17.674601] system 00:00: iomem range 0xe8000-0xebfff could not be reserved
[   17.674606] system 00:02: ioport range 0x164e-0x164f has been reserved
[   17.674608] system 00:02: ioport range 0x1000-0x107f has been reserved
[   17.674610] system 00:02: ioport range 0x1180-0x11bf has been reserved
[   17.674613] system 00:02: ioport range 0x800-0x80f has been reserved
[   17.674615] system 00:02: ioport range 0x15e0-0x15ef has been reserved
[   17.674617] system 00:02: ioport range 0x1600-0x165f could not be reserved
[   17.674620] system 00:02: iomem range 0xf0000000-0xf3ffffff could not be reserved
[   17.674622] system 00:02: iomem range 0xfed1c000-0xfed1ffff could not be reserved
[   17.674625] system 00:02: iomem range 0xfed14000-0xfed17fff could not be reserved
[   17.674627] system 00:02: iomem range 0xfed18000-0xfed18fff could not be reserved
[   17.674629] system 00:02: iomem range 0xfed19000-0xfed19fff could not be reserved
[   17.674632] system 00:02: iomem range 0xfed45000-0xfed4bfff could not be reserved
[   17.675033] PCI: Bridge: 0000:00:1c.0
[   17.675038]   IO window: 2000-2fff
[   17.675050]   MEM window: fc000000-fdffffff
[   17.675054]   PREFETCH window: f8000000-f80fffff
[   17.675062] PCI: Bridge: 0000:00:1c.1
[   17.675067]   IO window: 3000-3fff
[   17.675078]   MEM window: dc000000-df3fffff
[   17.675085]   PREFETCH window: dfe00000-dfefffff
[   17.675090] PCI: Bridge: 0000:00:1c.2
[   17.675095]   IO window: 4000-4fff
[   17.675102]   MEM window: d8000000-d9ffffff
[   17.675110]   PREFETCH window: dfb00000-dfbfffff
[   17.675118] PCI: Bridge: 0000:00:1c.3
[   17.675121]   IO window: 5000-5fff
[   17.675131]   MEM window: d4000000-d5ffffff
[   17.675139]   PREFETCH window: df800000-df8fffff
[   17.675146] PCI: Bridge: 0000:00:1c.4
[   17.675151]   IO window: 6000-6fff
[   17.675157]   MEM window: d0000000-d1ffffff
[   17.675163]   PREFETCH window: df500000-df5fffff
[   17.675173] PCI: Bus 22, cardbus bridge: 0000:15:00.0
[   17.675175]   IO window: 00007000-000070ff
[   17.675183]   IO window: 00007400-000074ff
[   17.675189]   PREFETCH window: f4000000-f7ffffff
[   17.675196]   MEM window: 80000000-83ffffff
[   17.675202] PCI: Bridge: 0000:00:1e.0
[   17.675207]   IO window: 7000-afff
[   17.675217]   MEM window: f8300000-fbffffff
[   17.675221]   PREFETCH window: f4000000-f7ffffff
[   17.675275] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 20 (level, low) -> IRQ 20
[   17.675280] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   17.675313] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 21 (level, low) -> IRQ 21
[   17.675318] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   17.675348] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 22 (level, low) -> IRQ 22
[   17.675353] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   17.675392] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 23 (level, low) -> IRQ 23
[   17.675397] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[   17.675431] ACPI: PCI Interrupt 0000:00:1c.4[A] -> GSI 20 (level, low) -> IRQ 20
[   17.675438] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[   17.675454] PCI: Enabling device 0000:00:1e.0 (0005 -> 0007)
[   17.675464] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   17.675490] ACPI: PCI Interrupt 0000:15:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   17.675496] PCI: Setting latency timer of device 0000:15:00.0 to 64
[   17.675507] NET: Registered protocol family 2
[   17.710613] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[   17.711253] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[   17.712914] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   17.713488] TCP: Hash tables configured (established 262144 bind 65536)
[   17.713490] TCP reno registered
[   17.722671] checking if image is initramfs... it is
[   18.399953] Freeing initrd memory: 7506k freed
[   18.403652] Simple Boot Flag at 0x35 set to 0x1
[   18.404603] audit: initializing netlink socket (disabled)
[   18.404621] audit(1210537442.360:1): initialized
[   18.406585] VFS: Disk quotas dquot_6.5.1
[   18.406645] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   18.406754] io scheduler noop registered
[   18.406756] io scheduler anticipatory registered
[   18.406757] io scheduler deadline registered
[   18.406846] io scheduler cfq registered (default)
[   18.406857] Boot video device is 0000:00:02.0
[   18.410893] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   18.410976] assign_interrupt_mode Found MSI capability
[   18.411044] Allocate Port Service[0000:00:1c.0:pcie00]
[   18.411078] Allocate Port Service[0000:00:1c.0:pcie02]
[   18.411204] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   18.411284] assign_interrupt_mode Found MSI capability
[   18.411361] Allocate Port Service[0000:00:1c.1:pcie00]
[   18.411390] Allocate Port Service[0000:00:1c.1:pcie02]
[   18.411527] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   18.411601] assign_interrupt_mode Found MSI capability
[   18.411673] Allocate Port Service[0000:00:1c.2:pcie00]
[   18.411702] Allocate Port Service[0000:00:1c.2:pcie02]
[   18.411828] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[   18.411901] assign_interrupt_mode Found MSI capability
[   18.411971] Allocate Port Service[0000:00:1c.3:pcie00]
[   18.412000] Allocate Port Service[0000:00:1c.3:pcie02]
[   18.412126] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[   18.412210] assign_interrupt_mode Found MSI capability
[   18.412268] Allocate Port Service[0000:00:1c.4:pcie00]
[   18.412296] Allocate Port Service[0000:00:1c.4:pcie02]
[   18.434698] Real Time Clock Driver v1.12ac
[   18.434782] hpet_resources: 0xfed00000 is busy
[   18.434823] Linux agpgart interface v0.102
[   18.434825] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   18.435829] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   18.435884] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   18.435966] PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
[   18.444844] serio: i8042 KBD port at 0x60,0x64 irq 1
[   18.444848] serio: i8042 AUX port at 0x60,0x64 irq 12
[   18.458154] mice: PS/2 mouse device common for all mice
[   18.458187] cpuidle: using governor ladder
[   18.458189] cpuidle: using governor menu
[   18.458314] NET: Registered protocol family 1
[   18.458362] registered taskstats version 1
[   18.458484]   Magic number: 8:316:447
[   18.458552] /build/buildd/linux-2.6.24/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   18.458555] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   18.458556] EDD information not available.
[   18.458562] Freeing unused kernel memory: 316k freed
[   18.463227] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   19.625149] fuse init (API version 7.9)
[   19.640819] ACPI: SSDT 7D6E1D72, 02C4 (r1  PmRef  Cpu0Ist      100 INTL 20050513)
[   19.641110] ACPI: SSDT 7D6E20BB, 061E (r1  PmRef  Cpu0Cst      100 INTL 20050513)
[   19.644778] Monitor-Mwait will be used to enter C-1 state
[   19.644781] Monitor-Mwait will be used to enter C-2 state
[   19.644782] Monitor-Mwait will be used to enter C-3 state
[   19.644892] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   19.644896] ACPI: Processor [CPU0] (supports 8 throttling states)
[   19.645106] ACPI: SSDT 7D6E1CAA, 00C8 (r1  PmRef  Cpu1Ist      100 INTL 20050513)
[   19.645391] ACPI: SSDT 7D6E2036, 0085 (r1  PmRef  Cpu1Cst      100 INTL 20050513)
[   19.648411] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[   19.648416] ACPI: Processor [CPU1] (supports 8 throttling states)
[   19.650884] ACPI: Thermal Zone [THM0] (50 C)
[   19.652481] ACPI: Thermal Zone [THM1] (45 C)
[   19.856854] Intel(R) PRO/1000 Network Driver - version 7.3.20-k2-NAPI
[   19.856857] Copyright (c) 1999-2006 Intel Corporation.
[   19.856920] ACPI: PCI Interrupt 0000:00:19.0[A] -> GSI 20 (level, low) -> IRQ 20
[   19.856938] PCI: Setting latency timer of device 0000:00:19.0 to 64
[   19.886327] e1000: 0000:00:19.0: e1000_probe: (PCI Express:2.5Gb/s:Width x1) 00:15:58:84:18:9a
[   19.890586] usbcore: registered new interface driver usbfs
[   19.890606] usbcore: registered new interface driver hub
[   19.890629] usbcore: registered new device driver usb
[   19.891272] USB Universal Host Controller Interface driver v3.0
[   19.987356] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
[   19.987398] ACPI: PCI Interrupt 0000:00:1a.0[A] -> GSI 20 (level, low) -> IRQ 20
[   19.987412] PCI: Setting latency timer of device 0000:00:1a.0 to 64
[   19.987415] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[   19.987641] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[   19.987683] uhci_hcd 0000:00:1a.0: irq 20, io base 0x00001860
[   19.987796] usb usb1: configuration #1 chosen from 1 choice
[   19.987816] hub 1-0:1.0: USB hub found
[   19.987820] hub 1-0:1.0: 2 ports detected
[   20.009355] SCSI subsystem initialized
[   20.021899] libata version 3.00 loaded.
[   20.093195] ACPI: PCI Interrupt 0000:00:1a.1[B] -> GSI 21 (level, low) -> IRQ 21
[   20.093210] PCI: Setting latency timer of device 0000:00:1a.1 to 64
[   20.093216] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[   20.093237] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
[   20.093283] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00001880
[   20.093363] usb usb2: configuration #1 chosen from 1 choice
[   20.093380] hub 2-0:1.0: USB hub found
[   20.093384] hub 2-0:1.0: 2 ports detected
[   20.197133] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 16
[   20.197146] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   20.197152] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   20.197173] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 3
[   20.197209] uhci_hcd 0000:00:1d.0: irq 16, io base 0x000018a0
[   20.197302] usb usb3: configuration #1 chosen from 1 choice
[   20.197320] hub 3-0:1.0: USB hub found
[   20.197325] hub 3-0:1.0: 2 ports detected
[   20.301078] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 17 (level, low) -> IRQ 17
[   20.301093] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   20.301099] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   20.301120] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 4
[   20.301159] uhci_hcd 0000:00:1d.1: irq 17, io base 0x000018c0
[   20.301251] usb usb4: configuration #1 chosen from 1 choice
[   20.301270] hub 4-0:1.0: USB hub found
[   20.301274] hub 4-0:1.0: 2 ports detected
[   20.349751] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   20.349763] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   20.349769] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   20.349787] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 5
[   20.349823] uhci_hcd 0000:00:1d.2: irq 18, io base 0x000018e0
[   20.349913] usb usb5: configuration #1 chosen from 1 choice
[   20.349931] hub 5-0:1.0: USB hub found
[   20.349935] hub 5-0:1.0: 2 ports detected
[   20.356077] ACPI: PCI Interrupt 0000:15:00.1[B] -> GSI 17 (level, low) -> IRQ 17
[   20.356090] PCI: Setting latency timer of device 0000:15:00.1 to 64
[   20.357193] ACPI: PCI Interrupt 0000:00:1a.7[C] -> GSI 22 (level, low) -> IRQ 22
[   20.358202] PCI: Setting latency timer of device 0000:00:1a.7 to 64
[   20.358211] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[   20.358257] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 6
[   20.362194] ehci_hcd 0000:00:1a.7: debug port 1
[   20.362201] PCI: cache line size of 32 is not supported by device 0000:00:1a.7
[   20.362213] ehci_hcd 0000:00:1a.7: irq 22, io mem 0xfe226400
[   20.388978] usb 3-2: new low speed USB device using uhci_hcd and address 2
[   20.391784] Clocksource tsc unstable (delta = -149128272 ns)
[   20.401007] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   20.401101] usb usb6: configuration #1 chosen from 1 choice
[   20.401122] hub 6-0:1.0: USB hub found
[   20.401127] hub 6-0:1.0: 4 ports detected
[   20.409706] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[17]  MMIO=[f8301000-f83017ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[   20.426387] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 19 (level, low) -> IRQ 19
[   20.427305] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   20.427313] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   20.427364] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 7
[   20.431280] ehci_hcd 0000:00:1d.7: debug port 1
[   20.431289] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   20.431299] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xfe226800
[   20.449925] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   20.450013] usb usb7: configuration #1 chosen from 1 choice
[   20.450032] hub 7-0:1.0: USB hub found
[   20.450037] hub 7-0:1.0: 6 ports detected
[   20.550250] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 16 (level, low) -> IRQ 16
[   20.550294] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   20.550307] ACPI: PCI interrupt for device 0000:00:1f.2 disabled
[   20.553476] ata_piix 0000:00:1f.2: version 2.12
[   20.553484] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[   20.705980] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 16 (level, low) -> IRQ 16
[   20.706023] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   20.706140] scsi0 : ata_piix
[   20.706183] scsi1 : ata_piix
[   20.707228] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x1c30 irq 14
[   20.707231] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1c38 irq 15
[   20.841691] usb 3-2: device not accepting address 2, error -71
[   20.878140] ata1.00: ATA-7: HITACHI HTS541612J9SA00, SBDIC7JP, max UDMA/100
[   20.878143] ata1.00: 234441648 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   20.894305] ata1.00: configured for UDMA/100
[   21.214203] ata2.00: ATAPI: MATSHITADVD-RAM UJ-852, RB01, max UDMA/33
[   21.386981] ata2.00: configured for UDMA/33
[   21.387062] scsi 0:0:0:0: Direct-Access     ATA      HITACHI HTS54161 SBDI PQ: 0 ANSI: 5
[   21.388809] scsi 1:0:0:0: CD-ROM            MATSHITA DVD-RAM UJ-852   RB01 PQ: 0 ANSI: 5
[   21.393821] Driver 'sd' needs updating - please use bus_type methods
[   21.393880] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[   21.393891] sd 0:0:0:0: [sda] Write Protect is off
[   21.393893] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   21.393907] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   21.393948] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[   21.393956] sd 0:0:0:0: [sda] Write Protect is off
[   21.393958] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   21.393972] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   21.393975]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   21.421340] usb 3-2: new low speed USB device using uhci_hcd and address 4
[   21.424813]  sda1 sda2 sda3 sda4
[   21.425435] sd 0:0:0:0: [sda] Attached SCSI disk
[   21.429258] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   21.429272] sr 1:0:0:0: Attached scsi generic sg1 type 5
[   21.432202] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[   21.432205] Uniform CD-ROM driver Revision: 3.20
[   21.432241] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   21.603636] usb 3-2: configuration #1 chosen from 1 choice
[   21.605297] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00016c2000158970]
[   21.616234] usbcore: registered new interface driver hiddev
[   21.630932] input: Microsoft Microsoft 5-Button Mouse with IntelliEye(TM) as /devices/pci0000:00/0000:00:1d.0/usb3/3-2/3-2:1.0/input/input2
[   21.650403] input,hidraw0: USB HID v1.10 Mouse [Microsoft Microsoft 5-Button Mouse with IntelliEye(TM)] on usb-0000:00:1d.0-2
[   21.650414] usbcore: registered new interface driver usbhid
[   21.650417] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   22.031981] Attempting manual resume
[   22.031983] swsusp: Resume From Partition 8:2
[   22.031985] PM: Checking swsusp image.
[   22.032005] PM: Resume from disk failed.
[   22.037868] ReiserFS: sda3: found reiserfs format "3.6" with standard journal
[   22.037876] ReiserFS: sda3: using ordered data mode
[   22.047624] ReiserFS: sda3: journal params: device sda3, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[   22.048102] ReiserFS: sda3: checking transaction log (sda3)
[   22.088582] ReiserFS: sda3: Using r5 hash to sort names
[   29.562516] agpgart: Detected an Intel 965GM Chipset.
[   29.564224] agpgart: Detected 7676K stolen memory.
[   29.586430] agpgart: AGP aperture is 256M @ 0xe0000000
[   29.637404] input: Power Button (FF) as /devices/virtual/input/input3
[   29.661177] ACPI: Power Button (FF) [PWRF]
[   29.661253] input: Lid Switch as /devices/virtual/input/input4
[   29.665872] ACPI: Lid Switch [LID]
[   29.665931] input: Sleep Button (CM) as /devices/virtual/input/input5
[   29.693159] ACPI: Sleep Button (CM) [SLPB]
[   29.913847] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   29.969351] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   30.409698] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input6
[   30.416931] ath_hal: module license 'Proprietary' taints kernel.
[   30.425393] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   30.428719] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   30.430547] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:05/LNXVIDEO:01/input/input7
[   30.430819] ACPI: AC Adapter [AC] (on-line)
[   30.460676] ACPI: Video Device [VID1] (multi-head: yes  rom: no  post: no)
[   30.760761] wlan: 0.9.4
[   30.786391] iTCO_vendor_support: vendor-support=0
[   30.803282] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   30.803359] iTCO_wdt: Found a ICH8M-E TCO device (Version=2, TCOBASE=0x1060)
[   30.803400] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   30.852590] ACPI: Battery Slot [BAT0] (battery present)
[   30.875801] ricoh-mmc: Ricoh MMC Controller disabling driver
[   30.875804] ricoh-mmc: Copyright(c) Philip Langdale
[   30.875841] ricoh-mmc: Ricoh MMC controller found at 0000:15:00.3 [1180:0843] (rev 11)
[   30.875863] ricoh-mmc: Controller is now disabled.
[   30.933546] ath_pci: 0.9.4
[   30.933607] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   30.933621] PCI: Setting latency timer of device 0000:03:00.0 to 64
[   31.557303] input: PC Speaker as /devices/platform/pcspkr/input/input8
[   31.782969] ath_rate_sample: 1.2 (0.9.4)
[   31.783148] wifi0: 11a rates: 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   31.783154] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[   31.783158] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   31.783165] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
[   31.783168] wifi0: mac 10.3 phy 6.1 radio 10.2
[   31.783171] wifi0: Use hw queue 1 for WME_AC_BE traffic
[   31.783173] wifi0: Use hw queue 0 for WME_AC_BK traffic
[   31.783174] wifi0: Use hw queue 2 for WME_AC_VI traffic
[   31.783176] wifi0: Use hw queue 3 for WME_AC_VO traffic
[   31.783177] wifi0: Use hw queue 8 for CAB traffic
[   31.783178] wifi0: Use hw queue 9 for beacons
[   32.172452] Non-volatile memory driver v1.2
[   32.215108] wifi0: Atheros 5212: mem=0xdf3f0000, irq=17
[   32.230785] Yenta: CardBus bridge found at 0000:15:00.0 [17aa:20c6]
[   32.242373] sdhci: Secure Digital Host Controller Interface driver
[   32.242376] sdhci: Copyright(c) Pierre Ossman
[   32.357701] Yenta: ISA IRQ mask 0x0cb8, PCI irq 16
[   32.357707] Socket status: 30000006
[   32.357710] pcmcia: parent PCI bridge I/O window: 0x7000 - 0xafff
[   32.357712] pcmcia: parent PCI bridge Memory window: 0xf8300000 - 0xfbffffff
[   32.357714] pcmcia: parent PCI bridge Memory window: 0xf4000000 - 0xf7ffffff
[   32.358740] sdhci: SDHCI controller found at 0000:15:00.2 [1180:0822] (rev 21)
[   32.358771] ACPI: PCI Interrupt 0000:15:00.2[C] -> GSI 18 (level, low) -> IRQ 18
[   32.359766] sdhci:slot0: Will use DMA mode even though HW doesn't fully claim to support it.
[   32.359776] PCI: Setting latency timer of device 0000:15:00.2 to 64
[   32.359842] mmc0: SDHCI at 0xf8301800 irq 18 DMA
[   32.514223] sysfs: duplicate filename 'pcspkr' can not be created
[   32.514227] WARNING: at /build/buildd/linux-2.6.24/fs/sysfs/dir.c:424 sysfs_add_one()
[   32.514230] Pid: 3115, comm: modprobe Tainted: P        2.6.24-16-generic #1
[   32.514232] 
[   32.514232] Call Trace:
[   32.514242]  [<ffffffff802fe418>] sysfs_add_one+0xb8/0xf0
[   32.514245]  [<ffffffff802fea30>] create_dir+0x60/0xb0
[   32.514256]  [<ffffffff802feab1>] sysfs_create_dir+0x31/0x50
[   32.514260]  [<ffffffff80344912>] kobject_get+0x12/0x20
[   32.514262]  [<ffffffff80344f23>] kobject_add+0xb3/0x200
[   32.514265]  [<ffffffff80345108>] kobject_register+0x28/0x50
[   32.514269]  [<ffffffff803b9581>] bus_add_driver+0x91/0x220
[   32.514274]  [<ffffffff80263b6e>] sys_init_module+0x18e/0x1a90
[   32.514283]  [<ffffffff80251b50>] param_get_int+0x0/0x20
[   32.514288]  [<ffffffff8020c37e>] system_call+0x7e/0x83
[   32.514292] 
[   32.514294] kobject_add failed for pcspkr with -EEXIST, don't try to register things with the same name in the same directory.
[   32.514298] Pid: 3115, comm: modprobe Tainted: P        2.6.24-16-generic #1
[   32.514299] 
[   32.514300] Call Trace:
[   32.514302]  [<ffffffff80344fb9>] kobject_add+0x149/0x200
[   32.514306]  [<ffffffff80345108>] kobject_register+0x28/0x50
[   32.514309]  [<ffffffff803b9581>] bus_add_driver+0x91/0x220
[   32.514312]  [<ffffffff80263b6e>] sys_init_module+0x18e/0x1a90
[   32.514320]  [<ffffffff80251b50>] param_get_int+0x0/0x20
[   32.514324]  [<ffffffff8020c37e>] system_call+0x7e/0x83
[   32.514329] 
[   32.844422] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x81a0b1, caps: 0xa04793/0x300000
[   32.844427] serio: Synaptics pass-through port at isa0060/serio1/input0
[   32.886188] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input9
[   32.917213] thinkpad_acpi: ThinkPad ACPI Extras v0.17
[   32.917216] thinkpad_acpi: http://ibm-acpi.sf.net/
[   32.917218] thinkpad_acpi: ThinkPad BIOS 7LET37WW (1.07 ), EC 7KHT21WW-1.05
[   32.917220] thinkpad_acpi: Lenovo ThinkPad T61
[   32.917542] thinkpad_acpi: radio switch found; radios are enabled
[   32.919705] ACPI: PCI Interrupt 0000:00:1b.0[B] -> GSI 17 (level, low) -> IRQ 17
[   32.919710] hda_intel: probe_mask set to 0x1 for device 17aa:20ac
[   32.920682] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   32.921327] thinkpad_acpi: another device driver is already handling bay events
[   32.921330] thinkpad_acpi: disabling subdriver bay
[   32.924445] thinkpad_acpi: standard ACPI backlight interface available, not loading native one...
[   32.924745] input: ThinkPad Extra Buttons as /devices/virtual/input/input10
[   33.923584] lp: driver loaded but no devices found
[   34.024489] Adding 1534168k swap on /dev/sda2.  Priority:-1 extents:1 across:1534168k
[   37.669857] IBM TrackPoint firmware: 0x0e, buttons: 3/3
[   37.688582] input: TPPS/2 IBM TrackPoint as /devices/platform/i8042/serio1/serio2/input/input11
[   38.099265] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[   38.186002] ReiserFS: sda1: found reiserfs format "3.6" with standard journal
[   38.186008] ReiserFS: sda1: using ordered data mode
[   38.198681] ReiserFS: sda1: journal params: device sda1, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[   38.199128] ReiserFS: sda1: checking transaction log (sda1)
[   38.223530] ReiserFS: sda1: Using r5 hash to sort names
[   38.556928] ip_tables: (C) 2000-2006 Netfilter Core Team
[   39.520489] ACPI: ACPI Dock Station Driver 
[   39.571944] ACPI: \_SB_.PCI0.IDE0.PRIM.MSTR: found ejectable bay
[   39.571951] ACPI: \_SB_.PCI0.IDE0.PRIM.MSTR: Adding notify handler
[   39.571981] ACPI: Bay [\_SB_.PCI0.IDE0.PRIM.MSTR] Added
[   39.571997] ACPI: \_SB_.PCI0.SATA.SCND.MSTR: found ejectable bay
[   39.572002] ACPI: \_SB_.PCI0.SATA.SCND.MSTR: Adding notify handler
[   39.572021] ACPI: Error installing bay notify handler
[   39.572023] ACPI: Bay [\_SB_.PCI0.SATA.SCND.MSTR] Added
[   40.546100] ppdev: user-space parallel port driver
[   40.669025] audit(1210537472.226:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5236 profile="/usr/sbin/cupsd" namespace="default"
[   40.830486] input: /usr/sbin/thinkpad-keys as /devices/virtual/input/input12
[   41.076392] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   41.076403] vboxdrv: Successfully done.
[   41.077770] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   41.077776] vboxdrv: Successfully loaded version 1.5.6_OSE (interface 0x00050002).
[   42.515688] Bluetooth: Core ver 2.11
[   42.516593] NET: Registered protocol family 31
[   42.516600] Bluetooth: HCI device and connection manager initialized
[   42.516607] Bluetooth: HCI socket layer initialized
[   42.551219] Bluetooth: L2CAP ver 2.9
[   42.551227] Bluetooth: L2CAP socket layer initialized
[   42.650915] Bluetooth: RFCOMM socket layer initialized
[   42.650928] Bluetooth: RFCOMM TTY layer initialized
[   42.650929] Bluetooth: RFCOMM ver 1.8
[   45.005895] [drm] Initialized drm 1.1.0 20060810
[   45.008601] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[   45.008611] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   45.008673] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   67.631390] NET: Registered protocol family 10
[   67.631902] lo: Disabled Privacy Extensions
[   67.632895] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   78.389575] ath0: no IPv6 routers present
[   81.236694] NET: Registered protocol family 17
[   84.131985] CPU0 attaching NULL sched-domain.
[   84.131995] CPU1 attaching NULL sched-domain.
[   84.140595] CPU0 attaching sched-domain:
[   84.140598]  domain 0: span 03
[   84.140599]   groups: 01 02
[   84.140602]   domain 1: span 03
[   84.140603]    groups: 03
[   84.140605] CPU1 attaching sched-domain:
[   84.140606]  domain 0: span 03
[   84.140608]   groups: 02 01
[   84.140616]   domain 1: span 03
[   84.140617]    groups: 03
[   92.763047] process `skype' is using obsolete setsockopt SO_BSDCOMPAT
[   94.153779] ath0: no IPv6 routers present
[  492.700830] ACPI: PCI interrupt for device 0000:03:00.0 disabled
[  492.700868] ath_pci: driver unloaded
[  492.885177] ACPI: PCI interrupt for device 0000:00:19.0 disabled
[  493.863186] Syncing filesystems ... done.
[  493.885977] PM: Preparing system for mem sleep
[  493.886372] Freezing user space processes ... (elapsed 0.00 seconds) done.
[  493.886931] Freezing remaining freezable tasks ... (elapsed 0.00 seconds) done.
[  493.886965] PM: Entering mem sleep
[  493.886966] Suspending console(s)
[  493.886969] drm_sysfs_suspend
[  493.887389] ACPI: PCI interrupt for device 0000:00:02.0 disabled
[  494.135892] sd 0:0:0:0: [sda] Synchronizing SCSI cache
[  494.201305] sd 0:0:0:0: [sda] Stopping disk
[  495.675666] ACPI handle has no context!
[  495.675688] ACPI: PCI interrupt for device 0000:15:00.2 disabled
[  495.675695] ACPI handle has no context!
[  495.696019] ACPI handle has no context!
[  495.711321] ACPI: PCI interrupt for device 0000:00:1f.2 disabled
[  495.727067] ACPI: PCI interrupt for device 0000:00:1d.7 disabled
[  495.743969] ACPI: PCI interrupt for device 0000:00:1d.2 disabled
[  495.744004] ACPI: PCI interrupt for device 0000:00:1d.1 disabled
[  495.744039] ACPI: PCI interrupt for device 0000:00:1d.0 disabled
[  495.744831] ACPI: PCI interrupt for device 0000:00:1b.0 disabled
[  495.760539] ACPI: PCI interrupt for device 0000:00:1a.7 disabled
[  495.761446] ACPI: PCI interrupt for device 0000:00:1a.1 disabled
[  495.761501] ACPI: PCI interrupt for device 0000:00:1a.0 disabled
[  495.767369] Disabling non-boot CPUs ...
[  495.767387] CPU0 attaching NULL sched-domain.
[  495.767388] CPU1 attaching NULL sched-domain.
[  495.880478] CPU 1 is now offline
[  495.880481] SMP alternatives: switching to UP code
[  495.881778] CPU0 attaching sched-domain:
[  495.881781]  domain 0: span 01
[  495.881782]   groups: 01
[  495.881975] CPU1 is down
[  495.882119] Extended CMOS year: 2000
[    0.238001] Back to C!
[    0.238302] Extended CMOS year: 2000
[    0.238508] Enabling non-boot CPUs ...
[    0.238578] CPU0 attaching NULL sched-domain.
[    0.248736] SMP alternatives: switching to SMP code
[    0.249728] Booting processor 1/2 APIC 0x1
[    0.260710] Initializing CPU#1
[    0.341129] Calibrating delay using timer specific routine.. 3989.68 BogoMIPS (lpj=7979377)
[    0.341135] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.341136] CPU: L2 cache: 4096K
[    0.341139] CPU 1/1 -> Node 0
[    0.341140] CPU: Physical Processor ID: 0
[    0.341141] CPU: Processor Core ID: 1
[    0.341643] Intel(R) Core(TM)2 Duo CPU     T7300  @ 2.00GHz stepping 0a
[    0.341213] CPU0 attaching sched-domain:
[    0.341215]  domain 0: span 03
[    0.341216]   groups: 01 02
[    0.341218]   domain 1: span 03
[    0.341219]    groups: 03
[    0.341221] CPU1 attaching sched-domain:
[    0.341222]  domain 0: span 03
[    0.341223]   groups: 02 01
[    0.341225]   domain 1: span 03
[    0.341226]    groups: 03
[    0.342173] CPU1 is up
[    0.345667] Switched to high resolution mode on CPU 1
[    0.736357] ACPI: EC: missing write data confirmation, don't expect it any longer.
[    0.754373] PM: Writing back config space on device 0000:00:02.0 at offset 1 (was 900007, writing 900003)
[    0.766843] PM: Writing back config space on device 0000:00:02.1 at offset 1 (was 900000, writing 900007)
[    0.766897] PM: Writing back config space on device 0000:00:19.0 at offset 1 (was 100107, writing 100103)
[    0.766930] ACPI: PCI Interrupt 0000:00:1a.0[A] -> GSI 20 (level, low) -> IRQ 20
[    0.766940] PCI: Setting latency timer of device 0000:00:1a.0 to 64
[    0.767013] usb usb1: root hub lost power or was reset
[    0.767041] ACPI: PCI Interrupt 0000:00:1a.1[B] -> GSI 21 (level, low) -> IRQ 21
[    0.767050] PCI: Setting latency timer of device 0000:00:1a.1 to 64
[    0.767123] usb usb2: root hub lost power or was reset
[    0.781037] ACPI: PCI Interrupt 0000:00:1a.7[C] -> GSI 22 (level, low) -> IRQ 22
[    0.781047] PCI: Setting latency timer of device 0000:00:1a.7 to 64
[    0.796913] PM: Writing back config space on device 0000:00:1b.0 at offset 1 (was 100106, writing 100102)
[    0.796954] ACPI: PCI Interrupt 0000:00:1b.0[B] -> GSI 17 (level, low) -> IRQ 17
[    0.796964] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[    1.228737] PM: Writing back config space on device 0000:00:1c.0 at offset 7 (was 20002020, writing 2020)
[    1.228757] PM: Writing back config space on device 0000:00:1c.0 at offset 1 (was 100107, writing 100507)
[    1.228826] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    1.228876] PM: Writing back config space on device 0000:00:1c.1 at offset 1 (was 100107, writing 100507)
[    1.228943] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[    1.228982] PM: Writing back config space on device 0000:00:1c.2 at offset 7 (was 20004040, writing 4040)
[    1.229002] PM: Writing back config space on device 0000:00:1c.2 at offset 1 (was 100107, writing 100507)
[    1.229071] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[    1.229106] PM: Writing back config space on device 0000:00:1c.3 at offset 7 (was 20005050, writing 5050)
[    1.229126] PM: Writing back config space on device 0000:00:1c.3 at offset 1 (was 100107, writing 100507)
[    1.229194] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[    1.229230] PM: Writing back config space on device 0000:00:1c.4 at offset 7 (was 20006060, writing 6060)
[    1.229251] PM: Writing back config space on device 0000:00:1c.4 at offset 1 (was 100107, writing 100507)
[    1.229319] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[    1.229334] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 16
[    1.229340] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[    1.229419] usb usb3: root hub lost power or was reset
[    1.229444] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 17 (level, low) -> IRQ 17
[    1.229453] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[    1.229525] usb usb4: root hub lost power or was reset
[    1.229546] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[    1.229554] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[    1.229628] usb usb5: root hub lost power or was reset
[    1.244720] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 19 (level, low) -> IRQ 19
[    1.244728] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    1.244835] PM: Writing back config space on device 0000:00:1e.0 at offset 1 (was 100005, writing 100007)
[    1.244867] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[    1.260617] PM: Writing back config space on device 0000:00:1f.2 at offset 1 (was 2b00005, writing 2b80005)
[    1.260642] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 16 (level, low) -> IRQ 16
[    1.260651] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[    1.260767] PM: Writing back config space on device 0000:03:00.0 at offset 1 (was 100107, writing 100103)
[    1.261263] ata1.01: _GTF evaluation failed (AE 0x1001)
[    1.262403] ata2.01: _GTF evaluation failed (AE 0x1001)
[    1.276611] PM: Writing back config space on device 0000:15:00.1 at offset 4 (was 0, writing f8301000)
[    1.276621] PM: Writing back config space on device 0000:15:00.1 at offset 3 (was 800000, writing 804000)
[    1.276632] PM: Writing back config space on device 0000:15:00.1 at offset 1 (was 2100000, writing 2100006)
[    1.329665] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[17]  MMIO=[f8301000-f83017ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    1.348572] PM: Writing back config space on device 0000:15:00.2 at offset 4 (was 0, writing f8301800)
[    1.348579] PM: Writing back config space on device 0000:15:00.2 at offset 3 (was 800000, writing 804000)
[    1.348588] PM: Writing back config space on device 0000:15:00.2 at offset 1 (was 2100000, writing 2100006)
[    1.348617] ACPI: PCI Interrupt 0000:15:00.2[C] -> GSI 18 (level, low) -> IRQ 18
[    1.580385] ata2.00: ACPI cmd ef/03:42:00:00:00:a0 filtered out
[    1.580388] ata2.00: ACPI cmd ef/03:0c:00:00:00:a0 filtered out
[    1.581351] ata2.00: ACPI cmd e3/00:1f:00:00:00:a0 succeeded
[    1.582350] ata2.00: ACPI cmd e3/00:02:00:00:00:a0 succeeded
[    1.916698] ata2.00: configured for UDMA/33
[    2.639199] sd 0:0:0:0: [sda] Starting disk
[    2.744258] thinkpad_acpi: unknown LID-related HKEY event: 0x5010
[    2.768186] ata1.00: ACPI cmd ef/02:00:00:00:00:a0 succeeded
[    2.768189] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 filtered out
[    2.768191] ata1.00: ACPI cmd ef/03:45:00:00:00:a0 filtered out
[    2.768193] ata1.00: ACPI cmd ef/03:0c:00:00:00:a0 filtered out
[    2.768343] ata1.00: ACPI cmd ef/5f:00:00:00:00:a0 succeeded
[    2.768481] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 succeeded
[    2.771083] ata1.00: configured for UDMA/100
[    2.773611] ata1.00: configured for UDMA/100
[    2.773613] ata1: EH complete
[    2.774031] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[    2.774042] sd 0:0:0:0: [sda] Write Protect is off
[    2.774043] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.774057] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.774071] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[    2.774084] sd 0:0:0:0: [sda] Write Protect is off
[    2.774085] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.774097] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.995282] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[    2.996676] PM: Finishing wakeup.
[    2.996678] Restarting tasks ... <6>usb 3-2: USB disconnect, address 4
[    3.027456] done.
[    3.316515] usb 3-2: new low speed USB device using uhci_hcd and address 5
[    3.498834] usb 3-2: configuration #1 chosen from 1 choice
[    3.516954] input: Microsoft Microsoft 5-Button Mouse with IntelliEye(TM) as /devices/pci0000:00/0000:00:1d.0/usb3/3-2/3-2:1.0/input/input13
[    3.596681] input,hidraw0: USB HID v1.10 Mouse [Microsoft Microsoft 5-Button Mouse with IntelliEye(TM)] on usb-0000:00:1d.0-2
[    3.965572] Intel(R) PRO/1000 Network Driver - version 7.3.20-k2-NAPI
[    3.965576] Copyright (c) 1999-2006 Intel Corporation.
[    3.965633] ACPI: PCI Interrupt 0000:00:19.0[A] -> GSI 20 (level, low) -> IRQ 20
[    3.965650] PCI: Setting latency timer of device 0000:00:19.0 to 64
[    3.971898] e1000: 0000:00:19.0: e1000_probe: (PCI Express:2.5Gb/s:Width x1) 00:15:58:84:18:9a
[    4.007829] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
[    4.019751] ADDRCONF(NETDEV_UP): eth0: link is not ready
[    4.026273] ath_pci: 0.9.4
[    4.026338] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[    4.026356] PCI: Setting latency timer of device 0000:03:00.0 to 64
[    4.576083] wifi0: 11a rates: 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[    4.576093] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[    4.576096] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[    4.576103] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
[    4.576106] wifi0: mac 10.3 phy 6.1 radio 10.2
[    4.576110] wifi0: Use hw queue 1 for WME_AC_BE traffic
[    4.576112] wifi0: Use hw queue 0 for WME_AC_BK traffic
[    4.576113] wifi0: Use hw queue 2 for WME_AC_VI traffic
[    4.576115] wifi0: Use hw queue 3 for WME_AC_VO traffic
[    4.576116] wifi0: Use hw queue 8 for CAB traffic
[    4.576117] wifi0: Use hw queue 9 for beacons
[    4.581037] wifi0: Atheros 5212: mem=0xdf3f0000, irq=17
[    4.884247] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   17.084801] ADDRCONF(NETDEV_CHANGE): ath0: link becomes ready
[   27.215511] ath0: no IPv6 routers present
[   44.275560] ath0: no IPv6 routers present
[  974.712389] wifi0: rx FIFO overrun; resetting

```

Thanks a lot in advance!

---

### Post by pro003 on 2008-05-11
did you REBOOT your machine and checked the sound then....?

---

### Post by jackalparty on 2008-05-11
I hit what seems like a similar problem (two days after the sound stopped working) Alsamixer worked for me, somehow my channels got muted sooo
this may not help you at all but go to terminal enter alsamixer, go over to the muted channels and press M to unmute them and then the up-arrow key to raise the volume. Give it a shot and if that doesn't work Ill give you a couple more suggestions.

---

### Post by mr.snuff on 2008-05-11
Hey!

Thanks for the quick replies!

> did you REBOOT your machine and checked the sound then....?
Yes, I actually rebooted every time I tried a fix and after re-compiling of course.

> I hit what seems like a similar problem (two days after the sound stopped working) Alsamixer worked for me, somehow my channels got muted sooo
this may not help you at all but go to terminal enter alsamixer, go over to the muted channels and press M to unmute them and then the up-arrow key to raise the volume. Give it a shot and if that doesn't work Ill give you a couple more suggestions.

Actually, I checked alsamixer and everything should be fine. I changed the sound settings and levels but nothing worked. I have attached some screenshots of my current settings. In general, should the IEC958 channel be muted or not? Either way it doesn't work.

Thanks!

---

### Post by jackalparty on 2008-05-11
for me it was the internal, unmute the internal and use the up arrow to put it all the way up, that should fix it, if not post again and well look at some conf files.

do both of the internals

---

### Post by mr.snuff on 2008-05-11
Unfortunately, that didn't help. I attached some new images of how it looks now. I don't have to restart my computer after doing changes in alsamixer, right?

---

### Post by jackalparty on 2008-05-11
no you dont have to restart but hell try it and see, it looks good now. are you using a laptop.. accualy post your specs real fast and ill see if anyone of that sticks out.
along with that post your
/etc/asound.conf

.asoundrc
&
.asoundrc.asoundconf

which are in your home directory

and you tried something other than your music program??

go to system -- preferences -- sounds and test there

---

### Post by mr.snuff on 2008-05-11
Edit: Yes, I have a laptop. Lenovo Thinkpad T61

> **jackalparty said:**
> 
/etc/asound.conf

I don't have this file. locate asound.conf doesn't bring up a result either.

> **jackalparty said:**
> 
.asoundrc

```
# ALSA library configuration file

# Include settings that are under the control of asoundconf(1).
# (To disable these settings, comment out this line.)
</home/johannes/.asoundrc.asoundconf>
```


> **jackalparty said:**
> .asoundrc.asoundconf

```
# ALSA library configuration file managed by asoundconf(1).
#
# MANUAL CHANGES TO THIS FILE WILL BE OVERWRITTEN!
#
# Manual changes to the ALSA library configuration should be implemented
# by editing the ~/.asoundrc file, not by editing this file.
!defaults.pcm.card Intel
defaults.ctl.card Intel
defaults.pcm.device 0
defaults.pcm.subdevice -1
defaults.pcm.nonblock 1
defaults.pcm.ipc_key 5678293
defaults.pcm.ipc_gid audio
defaults.pcm.ipc_perm 0660
defaults.pcm.dmix.max_periods 0
defaults.pcm.dmix.rate 48000
defaults.pcm.dmix.format S16_LE
defaults.pcm.dmix.card defaults.pcm.card
defaults.pcm.dmix.device defaults.pcm.device
defaults.pcm.dsnoop.card defaults.pcm.card
defaults.pcm.dsnoop.device defaults.pcm.device
defaults.pcm.front.card defaults.pcm.card
defaults.pcm.front.device defaults.pcm.device
defaults.pcm.rear.card defaults.pcm.card
defaults.pcm.rear.device defaults.pcm.device
defaults.pcm.center_lfe.card defaults.pcm.card
defaults.pcm.center_lfe.device defaults.pcm.device
defaults.pcm.side.card defaults.pcm.card
defaults.pcm.side.device defaults.pcm.device
defaults.pcm.surround40.card defaults.pcm.card
defaults.pcm.surround40.device defaults.pcm.device
defaults.pcm.surround41.card defaults.pcm.card
defaults.pcm.surround41.device defaults.pcm.device
defaults.pcm.surround50.card defaults.pcm.card
defaults.pcm.surround50.device defaults.pcm.device
defaults.pcm.surround51.card defaults.pcm.card
defaults.pcm.surround51.device defaults.pcm.device
defaults.pcm.surround71.card defaults.pcm.card
defaults.pcm.surround71.device defaults.pcm.device
defaults.pcm.iec958.card defaults.pcm.card
defaults.pcm.iec958.device defaults.pcm.device
defaults.pcm.modem.card defaults.pcm.card
defaults.pcm.modem.device defaults.pcm.device
defaults.rawmidi.card 0
defaults.rawmidi.device 0
defaults.rawmidi.subdevice -1
defaults.hwdep.card 0
defaults.hwdep.device 0
defaults.timer.class 2
defaults.timer.sclass 0
defaults.timer.card 0
defaults.timer.device 0
defaults.timer.subdevice 0
defaults.namehint.showall off
defaults.namehint.basic on
defaults.namehint.extended off
```


> **jackalparty said:**
> 
and you tried something other than your music program??
go to system -- preferences -- sounds and test there
I always tested there so far.

Thanks for your help, I appreciate it!

---

### Post by jackalparty on 2008-05-11
make make the .asoundrc and stick it in the $HOME/.asoundrc
i dont think it needs to be executable but just it case go to terminal and chmod 777 .asoundrc just to be sure. restart and give it a shot, you might have to re alsamixer and then tell me if it works. 
PS how do i do those nifty boxes your using

EDIT -- you are going to have to comment out that line in the file, make sure you do that AND make a copy of the file in case we need to set it back




pcm.card0 {

  type hw

  card 0

  mmap_emulation true

}

pcm.!output {
type dmix
ipc_key 1234
ipc_key_add_uid 1
slave {
pcm "card0"
period_time 0
period_size 1024
buffer_size 8192
rate 44100
}
bindings {
0 0
1 1
}
}

#
# DSNOOP output device
#
pcm.!input {
type dsnoop
ipc_key 4321
ipc_key_add_uid 1
slave {
pcm "card0"
period_time 0
period_size 1024
rate 44100
}
}

#
# ASYM duplex device
#
pcm.!duplex {
type asym
playback.pcm "output"
capture.pcm "input"
}

#
# Make the duplex device default
#
pcm.!default {
type plug
slave.pcm "duplex"
}

#
# OSS Compability

pcm.!dsp0 {
type plug
slave.pcm "duplex"
}

ctl.!mixer0 {
type hw
card 0
}

---

### Post by 01mf02 on 2008-05-11
I think I had a similar problem - sound stopped working suddenly. To solve that, I resorted to disabling PulseAudio/ESD and using ALSA wherever possible.

---

### Post by jackalparty on 2008-05-11
yes, i cant believe i didn't think of that haha
go back to the sound preferences and make sure in devices that you are using the alsa driver.

---

### Post by mr.snuff on 2008-05-11
Ok, I changed .asoundrc so that it looks like the following and rebooted.
```
# ALSA library configuration file

# Include settings that are under the control of asoundconf(1).
# (To disable these settings, comment out this line.)
# </home/johannes/.asoundrc.asoundconf>
pcm.card0 {

type hw

card 0

mmap_emulation true

}

pcm.!output {
type dmix
ipc_key 1234
ipc_key_add_uid 1
slave {
pcm "card0"
period_time 0
period_size 1024
buffer_size 8192
rate 44100
}
bindings {
0 0
1 1
}
}

#
# DSNOOP output device
#
pcm.!input {
type dsnoop
ipc_key 4321
ipc_key_add_uid 1
slave {
pcm "card0"
period_time 0
period_size 1024
rate 44100
}
}

#
# ASYM duplex device
#
pcm.!duplex {
type asym
playback.pcm "output"
capture.pcm "input"
}

#
# Make the duplex device default
#
pcm.!default {
type plug
slave.pcm "duplex"
}

#
# OSS Compability

pcm.!dsp0 {
type plug
slave.pcm "duplex"
}

ctl.!mixer0 {
type hw
card 0
}

```

However, it didn't help. But now, when I try ALSA in the sound settings, I get the following error:
```
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Could not open audio device for playback.
```

I have attached a screenshot of my sound settings plus error message.

P.S. the nifty boxes are created when you use the quote or code options in the post editor.

---

### Post by jackalparty on 2008-05-11
well, set it back or accualy you can proly just reuncomment that line and it should be fine.
i guess this is over my head, when i hit hard problems i hit up the ubuntu irc which is irc.freenode.net and then channel #ubuntu
those guys can fix anything.

1 last thing you can try
"set everything to autodetect and see whathappens"

i know that 8.04 added a layer called pulseaudio which is what caused a lot of the sound problems

good luck buddy!

---

### Post by jackalparty on 2008-05-11
```
test
```

---

### Post by mr.snuff on 2008-05-11
Thanks for your help jackalparty!
I will check out the IRC or hope that someone in this forum knows a solution. It's really a weird problem since everything actually looks fine and seems to work. Only I don't hear anything :/

I tried the auto-detect but it doesn't help either.

Well, thanks anyway!

---

### Post by aquamammal on 2008-05-12
I'm seem to have the same problem as you, except that sounds just don't work for the internal files on my computer. Youtube still has sound. Is that the case for you?

---

### Post by mr.snuff on 2008-05-12
> **aquamammal said:**
> I'm seem to have the same problem as you, except that sounds just don't work for the internal files on my computer. Youtube still has sound. Is that the case for you?

No, even flash videos such as on youtube don't have any sound on my system. Basically, nothing has sound anymore.

---

### Post by shomon on 2008-06-19
I can't help but I can confirm I'm getting the same thing - looks like maybe flash is talking directly to the sound card rather than being polite and using pulse audio or alsa... In my case, pulseaudio. So I reboot, and it works, until I go into a youtube video or listen to music via firefox. And then no sound works at all and even killing pulseaudio doesn't get me anywhere.

Ale

---

### Post by styopa6 on 2008-06-24
I've had this problem on both of my machines with very different hardware that I've upgraded to Hardy.  What I've found is that if I run esd as root, or perform 'sudo esd' and keep that active, then I have no problems with any sound problems.  If I don't run esd as root, or under sudo privilages, then it exits with no errors displayed but does not fix the problem.  Definitely not the best solution, but it is what works for me.

---

### Post by mr.snuff on 2008-06-24
This whole problem seems to be very weird. For me, sound started working again but I can't really tell what the source of error was. The only thing I consciously did right before it started working again was uninstalling the linux backport modules (which I installed in an attempt to fix the sound problem in the first place). I still have no idea what caused the sound to break all of a sudden (it actually worked with Hardy for some time before it broke). 

For now, I'm happy that sound is working OK, although there are still some weird things going on sometimes. For example, after watching a video in my browser the sound in Skype is often not working anymore. After sudo killall pulseaudio it works in Skype but I might have to restart my browser in order to watch another video afterwards.

Oh well, let's hope for the best :)

---

### Post by alexvanzyl on 2008-09-02
I have a sound problem to but it between ubuntu and firefox, If the sound works in firefox and I want to listen to music with rhythmbox for example then I have no sound via that. If I use rhythmbox  first thing before starting firefox then firefox losses it sound. Any ideas what the problem my be.

---

### Post by jmpurser on 2009-05-16
> **jackalparty said:**
> I hit what seems like a similar problem (two days after the sound stopped working) Alsamixer worked for me, somehow my channels got muted sooo
this may not help you at all but go to terminal enter alsamixer, go over to the muted channels and press M to unmute them and then the up-arrow key to raise the volume. Give it a shot and if that doesn't work Ill give you a couple more suggestions.

Thank you.  This saved my bacon.  My sound quit working after I used a USB headphone set.

---

