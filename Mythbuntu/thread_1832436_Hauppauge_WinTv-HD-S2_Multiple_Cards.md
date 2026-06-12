---
title: "Hauppauge WinTv-HD-S2 Multiple Cards"
date: 2011-08-24
forum: Mythbuntu
---

### Post by b1acksun on 2011-08-24
Help - Have a really odd problem trying to use two Hauppauge WinTv-HD-S2 cards

Brief History & Background:
Had Mythbuntu box running Server and Frontend (10.04)
This box had 2 PCI Wintv-Nova 500's - worked fine had 3 real receiver's setup for 4 virtual cards.
H/W Asrock M3A790GMH/128M + 4GB + Nvidia Geforce 210 + AMD Phenom II X3 720 + 1TB Samsung + 500GB Hitachi + Network Link to 8TB Freenas Box via Samba - M/B Failure after 3 years.

Emergency purchase - Swapped out Asrock M/B for Gigabyte 870A-USB3L as I couldn't find the same board - had problems:
Restart did not work in that Mythbuntu gets stuck in a loop after the HDD heads all clunk as if power were removed from them. Mythbuntu just displays "Mythbuntu" and the first 4 dots underneath are brown.
Shutdown - gives a mix of graphics text then same action as restart without the clunk.
Went for the 11.04 upgrade - made no difference, so carried out a clean install, again no difference.

Moved property - not related to Mythbuntu issues. New place had no terrestrial Aeriel only Virgin Cable and an old Sky Dish - new Dish and cables installed max signal 100 - purchased two Hauppauge WinTv-HD-S2 cards.

Installed and tested Hauppauge WinTv-HD-S2 cards one at a time, seemed ok but still had the restart and shutdown issues.
tried operating 2 cards at a time - Mythbuntu would not start; would get a grub menu with countdown and no matter the selection it was no go, just a load of errors whizzing by then freeze.

Due to an issue I'd found with the Gigabyte board not been too happy with Samsung drives (tested by swapping out 12 drives 2 Samsung 250GB and 1 Samsung 500GB all caused same board errors eventually trashing sectors such as boot area's)

Purchased Asus M5A87 - swapped out Gigabyte M/B - no more Samsung drive issues; but still had "restart" problem; "shutdown", now actually shutdown!

Mythbuntu system now seemed to operate with a Hauppauge WinTv-HD-S2 card - Live TV and Recording seemed fine.

Carried out a clean install to 11.04 with all updates - result, no improvement

When both cards are installed together, the Mythbuntu system in a few cases will start and operate; recording and live TV for "a" card will not work.
After rebooting or powering down the system, Mythbuntu faults with a number of messages and often claims the network is not operational stopping on a TTY without CLI.
However while it's in this condition the mythtv Server side still appears to be operating, I can attach to it by Browser to see show listings, it records programmes at predetermined times.

This led to a walk on the darkside using a friends MS Windows 7 to check if the cards work ok at all (had no choice it had been weeks, couldn't think of anything else, ok it's no excuse should have asked for help first) - darkside result was yes, two Hauppauge WinTv-HD-S2 work together but for a small hiccup couldn't get network connectivity with the on board NIC, slammed a Realtek 8169 into the creation, everything was fine with MS Windows 7 setup - recording, livetv, switching source. Quickly erased the source of all evil and gathered the following from the Mythbuntu setup.

Now follows technical stuff, which I don't claim to fully understand:

bootlog - this also seems to be what's garbled to the screen before halting, however all the stuff on screen is not in the bootlog!

fsck from util-linux-ng 2.17.2
fsck from util-linux-ng 2.17.2
fsck from util-linux-ng 2.17.2
lircd-0.8.7[798]: lircd(default) ready, using /var/run/lirc/lircd

/sbin/fsck.xfs: XFS file system.
/sbin/fsck.xfs: XFS file system.
/dev/sda1: clean, 262069/30408704 files, 108920492/121608192 blocks
init: ureadahead-other main process (839) terminated with status 4

init: ureadahead-other main process (844) terminated with status 4

Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
 * Starting AppArmor profiles       [80G 
[74G[ OK ]
Loading the saved-state of the serial devices... 
mount error(101): Network is unreachable
Refer to the mount.cifs manual page (e.g. man mount.cifs)
mountall: mount /home/name/storage/videos/Video [872] terminated with status 32
mount error(101): Network is unreachable
Refer to the mount.cifs manual page (e.g. man mount.cifs)
mountall: mount /home/name/storage/videos/VideoK [873] terminated with status 32
mount error(101): Network is unreachable
Refer to the mount.cifs manual page (e.g. man mount.cifs)
mountall: mount /home/name/storage/music/Audio [951] terminated with status 32
 * Loading LIRC modules       [80G 
[74G[ OK ]
 * Stopping System V initialisation compatibility[74G[ OK ]
mount error(101): Network is unreachable
Refer to the mount.cifs manual page (e.g. man mount.cifs)
mountall: mount /home/name/storage/pictures [954] terminated with status 32
 * Starting remote control daemon(s) : LIRC       [80G 
[74G[ OK ]
speech-dispatcher disabled; edit /etc/default/speech-dispatcher
 [33m*[39;49m Saved ALSA mixer settings detected; aumix will not touch mixer.
 * Starting System V runlevel compatibility[74G[ OK ]
 * Stopping automatic crash report generation[74G[[31mfail[39;49m]
 * Starting CPU interrupts balancing daemon[74G[ OK ]
 * Starting ACPI daemon[74G[ OK ]
 * Starting save kernel messages[74G[ OK ]
 * Starting NTP server ntpd       [80G 
[74G[ OK ]
 * Starting anac(h)ronistic cron[74G[ OK ]
 * Starting bluetooth       [80G 
[74G[ OK ]
 [33m*[39;49m PulseAudio configured for per-user sessions
 * Starting regular background program processing daemon[74G[ OK ]
 * Starting deferred execution scheduler[74G[ OK ]
saned disabled; edit /etc/default/saned
 * Stopping save kernel messages[74G[ OK ]
 * Enabling additional executable binary formats binfmt-support       [80G 
[74G[ OK ]
 * Stopping cold plug devices[74G[ OK ]
 * Stopping log initial device creation[74G[ OK ]
apache2: Could not reliably determine the server's fully qualified domain name, using ::1 for ServerName
 * Starting load fallback graphics devices[74G[ OK ]
 * Starting configure network device security[74G[ OK ]
 * Starting configure virtual network devices[74G[ OK ]
 * Stopping load fallback graphics devices[74G[ OK ]
 * Stopping configure virtual network devices[74G[ OK ]
mount error(101): Network is unreachable
Refer to the mount.cifs( manual page (e.g. man mount.cifs)
mountall: mount /home/name/storage/videos/Video [1176] terminated with status 32
mount error(101): Network is unreachable
Refer to the mount.cifs( manual page (e.g. man mount.cifs)
 * Starting Userspace bootsplash[74G[ OK ]
 * Starting GNOME Display Manager[74G[ OK ]
mountall: mount /home/name/storage/videos/VideoK [1178] terminated with status 32
mount error(101): Network is unreachable
Refer to the mount.cifs( manual page (e.g. man mount.cifs)
mountall: mount /home/name/storage/music/Audio [1180] terminated with status 32
mount error(101): Network is unreachable
Refer to the mount.cifs( manual page (e.g. man mount.cifs)
mountall: mount /home/name/storage/pictures [1184] terminated with status 32
 * Stopping Userspace bootsplash[74G[ OK ]
 * Starting web server apache2       [80G 
[74G[ OK ]
 * Stopping anac(h)ronistic cron[74G[ OK ]

Now follows technical stuff, which I don't claim to fully understand:

lspci with one card
00:00.0 Host bridge [0600]: ATI Technologies Inc RX780/RX790 Chipset Host Bridge [1002:5957]
00:02.0 PCI bridge [0604]: ATI Technologies Inc RD790 PCI to PCI bridge (external gfx0 port A) [1002:5978]
00:04.0 PCI bridge [0604]: ATI Technologies Inc RD790 PCI to PCI bridge (PCI express gpp port A) [1002:597a]
00:11.0 SATA controller [0106]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode] [1002:4391] (rev 40)
00:12.0 USB Controller [0c03]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397]
00:12.2 USB Controller [0c03]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396]
00:13.0 USB Controller [0c03]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397]
00:13.2 USB Controller [0c03]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396]
00:14.0 SMBus [0c05]: ATI Technologies Inc SBx00 SMBus Controller [1002:4385] (rev 42)
00:14.2 Audio device [0403]: ATI Technologies Inc SBx00 Azalia (Intel HDA) [1002:4383] (rev 40)
00:14.3 ISA bridge [0601]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 LPC host controller [1002:439d] (rev 40)
00:14.4 PCI bridge [0604]: ATI Technologies Inc SBx00 PCI to PCI Bridge [1002:4384] (rev 40)
00:14.5 USB Controller [0c03]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI2 Controller [1002:4399]
00:16.0 USB Controller [0c03]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397]
00:16.2 USB Controller [0c03]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396]
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration [1022:1200]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor Address Map [1022:1201]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller [1022:1202]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control [1022:1203]
00:18.4 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor Link Control [1022:1204]
01:00.0 VGA compatible controller [0300]: nVidia Corporation GT218 [GeForce 210] [10de:0a65] (rev a2)
01:00.1 Audio device [0403]: nVidia Corporation High Definition Audio Controller [10de:0be3] (rev a1)
02:00.0 USB Controller [0c03]: Device [1b21:1042]
03:05.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet [10ec:8169] (rev 10)
03:07.0 Multimedia video controller [0400]: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [14f1:8800] (rev 05)
03:07.1 Multimedia controller [0480]: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port] [14f1:8801] (rev 05)
03:07.2 Multimedia controller [0480]: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] [14f1:8802] (rev 05)
03:07.4 Multimedia controller [0480]: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [IR Port] [14f1:8804] (rev 05)

lspci with both cards
00:00.0 Host bridge [0600]: ATI Technologies Inc RX780/RX790 Chipset Host Bridge [1002:5957]
00:02.0 PCI bridge [0604]: ATI Technologies Inc RD790 PCI to PCI bridge (external gfx0 port A) [1002:5978]
00:04.0 PCI bridge [0604]: ATI Technologies Inc RD790 PCI to PCI bridge (PCI express gpp port A) [1002:597a]
00:11.0 SATA controller [0106]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode] [1002:4391] (rev 40)
00:12.0 USB Controller [0c03]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397]
00:12.2 USB Controller [0c03]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396]
00:13.0 USB Controller [0c03]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397]
00:13.2 USB Controller [0c03]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396]
00:14.0 SMBus [0c05]: ATI Technologies Inc SBx00 SMBus Controller [1002:4385] (rev 42)
00:14.2 Audio device [0403]: ATI Technologies Inc SBx00 Azalia (Intel HDA) [1002:4383] (rev 40)
00:14.3 ISA bridge [0601]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 LPC host controller [1002:439d] (rev 40)
00:14.4 PCI bridge [0604]: ATI Technologies Inc SBx00 PCI to PCI Bridge [1002:4384] (rev 40)
00:14.5 USB Controller [0c03]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI2 Controller [1002:4399]
00:16.0 USB Controller [0c03]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397]
00:16.2 USB Controller [0c03]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396]
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration [1022:1200]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor Address Map [1022:1201]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller [1022:1202]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control [1022:1203]
00:18.4 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor Link Control [1022:1204]
01:00.0 VGA compatible controller [0300]: nVidia Corporation GT218 [GeForce 210] [10de:0a65] (rev a2)
01:00.1 Audio device [0403]: nVidia Corporation High Definition Audio Controller [10de:0be3] (rev a1)
02:00.0 USB Controller [0c03]: Device [1b21:1042]
03:05.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet [10ec:8169] (rev 10)
03:06.0 Multimedia video controller [0400]: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [14f1:8800] (rev 05)
03:06.1 Multimedia controller [0480]: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port] [14f1:8801] (rev 05)
03:06.2 Multimedia controller [0480]: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] [14f1:8802] (rev 05)
03:06.4 Multimedia controller [0480]: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [IR Port] [14f1:8804] (rev 05)
03:07.0 Multimedia video controller [0400]: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [14f1:8800] (rev 05)
03:07.1 Multimedia controller [0480]: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port] [14f1:8801] (rev 05)
03:07.2 Multimedia controller [0480]: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] [14f1:8802] (rev 05)
03:07.4 Multimedia controller [0480]: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [IR Port] [14f1:8804] (rev 05)

dmesg with a single card
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.38-11-generic-pae (buildd@rothera) (gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu4) ) #48-Ubuntu SMP Fri Jul 29 20:51:21 UTC 2011 (Ubuntu 2.6.38-11.48-generic-pae 2.6.38.
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009ac00 (usable)
[    0.000000]  BIOS-e820: 000000000009ac00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e2000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000c7f90000 (usable)
[    0.000000]  BIOS-e820: 00000000c7f90000 - 00000000c7fa8000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000c7fa8000 - 00000000c7fd0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000c7fd0000 - 00000000c8000000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffa00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000138000000 (usable)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI present.
[    0.000000] DMI: System manufacturer System Product Name/M5A87, BIOS 0404    04/19/2011
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x138000 max_arch_pfn = 0x1000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000000 mask FFFF80000000 write-back
[    0.000000]   1 base 000080000000 mask FFFFC0000000 write-back
[    0.000000]   2 base 0000C0000000 mask FFFFF8000000 write-back
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] TOM2: 0000000138000000 aka 4992M
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 00000000c8000000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] found SMP MP-table at [c00ff780] ff780
[    0.000000] initial memory mapped : 0 - 01e00000
[    0.000000] init_memory_mapping: 0000000000000000-0000000037bfe000
[    0.000000]  0000000000 - 0000200000 page 4k
[    0.000000]  0000200000 - 0037a00000 page 2M
[    0.000000]  0037a00000 - 0037bfe000 page 4k
[    0.000000] kernel direct mapping tables up to 37bfe000 @ 1dfb000-1e00000
[    0.000000] RAMDISK: 36772000 - 373b1000
[    0.000000] ACPI: RSDP 000fb850 00024 (v02 ACPIAM)
[    0.000000] ACPI: XSDT c7f90100 0004C (v01 041911 XSDT1732 20110419 MSFT 00000097)
[    0.000000] ACPI: FACP c7f90290 000F4 (v03 041911 FACP1732 20110419 MSFT 00000097)
[    0.000000] ACPI: DSDT c7f90460 0CCC6 (v01  A1866 A1866001 00000001 INTL 20060113)
[    0.000000] ACPI: FACS c7fa8000 00040
[    0.000000] ACPI: APIC c7f90390 0008C (v01 041911 APIC1732 20110419 MSFT 00000097)
[    0.000000] ACPI: MCFG c7f90420 0003C (v01 041911 OEMMCFG  20110419 MSFT 00000097)
[    0.000000] ACPI: OEMB c7fa8040 00072 (v01 041911 OEMB1732 20110419 MSFT 00000097)
[    0.000000] ACPI: HPET c7f9f8b0 00038 (v01 041911 OEMHPET  20110419 MSFT 00000097)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 4100MB HIGHMEM available.
[    0.000000] 891MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 37bfe000
[    0.000000]   low ram: 0 - 37bfe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00037bfe
[    0.000000]   HighMem  0x00037bfe -> 0x00138000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009a
[    0.000000]     0: 0x00000100 -> 0x000c7f90
[    0.000000]     0: 0x00100000 -> 0x00138000
[    0.000000] On node 0 totalpages: 1048346
[    0.000000] free_area_init_node: node 0, pgdat c17bac40, node_mem_map f4072200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3946 pages, LIFO batch:0
[    0.000000]   Normal zone: 1752 pages used for memmap
[    0.000000]   Normal zone: 222502 pages, LIFO batch:31
[    0.000000]   HighMem zone: 8201 pages used for memmap
[    0.000000]   HighMem zone: 811913 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x84] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x85] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x86] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x87] disabled)
[    0.000000] ACPI: IOAPIC (id[0x03] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 3, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8300 base: 0xfed00000
[    0.000000] SMP: Allowing 8 CPUs, 5 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009a000 - 000000000009b000
[    0.000000] PM: Registered nosave memory: 000000000009b000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e2000
[    0.000000] PM: Registered nosave memory: 00000000000e2000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at c8000000 (gap: c8000000:37a00000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 13 pages/cpu @f7800000 s32320 r0 d20928 u262144
[    0.000000] pcpu-alloc: s32320 r0 d20928 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 1038361
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-11-generic-pae root=UUID=7b563ec5-ddf7-480e-989b-a13e3dd6217d ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] allocated 25558720 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (00037bfe:00138000)
[    0.000000] Memory: 4105020k/5111808k available (5351k kernel code, 88364k reserved, 2597k data, 720k init, 3280456k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
[    0.000000]     vmalloc : 0xf83fe000 - 0xffbfe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf7bfe000   ( 891 MB)
[    0.000000]       .init : 0xc17c4000 - 0xc1878000   ( 720 kB)
[    0.000000]       .data : 0xc1539e95 - 0xc17c35c0   (2597 kB)
[    0.000000]       .text : 0xc1000000 - 0xc1539e95   (5351 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU-based detection of stalled CPUs is disabled.
[    0.000000] NR_IRQS:2304 nr_irqs:744 16
[    0.000000] CPU 0 irqstacks, hard=f740a000 soft=f740c000
[    0.000000] Extended CMOS year: 2000
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2799.712 MHz processor.
[    0.004003] Calibrating delay loop (skipped), value calculated using timer frequency.. 5599.42 BogoMIPS (lpj=1119884
[    0.004008] pid_max: default: 32768 minimum: 301
[    0.004030] Security Framework initialized
[    0.004046] AppArmor: AppArmor initialized
[    0.004048] Yama: becoming mindful.
[    0.004102] Mount-cache hash table entries: 512
[    0.004219] Initializing cgroup subsys ns
[    0.004222] ns_cgroup deprecated: consider using the 'clone_children' flag without the ns_cgroup.
[    0.004225] Initializing cgroup subsys cpuacct
[    0.004230] Initializing cgroup subsys memory
[    0.004238] Initializing cgroup subsys devices
[    0.004241] Initializing cgroup subsys freezer
[    0.004243] Initializing cgroup subsys net_cls
[    0.004245] Initializing cgroup subsys blkio
[    0.004273] CPU: Physical Processor ID: 0
[    0.004275] CPU: Processor Core ID: 0
[    0.004277] mce: CPU supports 6 MCE banks
[    0.006372] ACPI: Core revision 20110112
[    0.012010] ftrace: allocating 24259 entries in 48 pages
[    0.016056] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.016312] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.059394] CPU0: AMD Phenom(tm) II X3 720 Processor stepping 02
[    0.060003] Performance Events: AMD PMU driver.
[    0.060003] ... version:                0
[    0.060003] ... bit width:              48
[    0.060003] ... generic registers:      4
[    0.060003] ... value mask:             0000ffffffffffff
[    0.060003] ... max period:             00007fffffffffff
[    0.060003] ... fixed-purpose events:   0
[    0.060003] ... event mask:             000000000000000f
[    0.060003] CPU 1 irqstacks, hard=f74ce000 soft=f74d8000
[    0.060003] Booting Node   0, Processors  #1
[    0.008000] Initializing CPU#1
[    0.148057] CPU 2 irqstacks, hard=f74e2000 soft=f74e4000
[    0.148059]  #2
[    0.008000] Initializing CPU#2
[    0.240019] Brought up 3 CPUs
[    0.240021] Total of 3 processors activated (16799.02 BogoMIPS).
[    0.241949] devtmpfs: initialized
[    0.241949] print_constraints: dummy: 
[    0.241949] Time: 11:04:32  Date: 08/20/11
[    0.241949] NET: Registered protocol family 16
[    0.241949] EISA bus registered
[    0.241949] node 0 link 0: io port [1000, ffffff]
[    0.241949] TOM: 00000000c8000000 aka 3200M
[    0.241949] Fam 10h mmconf [e0000000, efffffff]
[    0.241949] node 0 link 0: mmio [e0000000, efffffff] ==> none
[    0.241949] node 0 link 0: mmio [f0000000, ffffffff]
[    0.241949] node 0 link 0: mmio [a0000, bffff]
[    0.241949] node 0 link 0: mmio [c8000000, dfffffff]
[    0.241949] TOM2: 0000000138000000 aka 4992M
[    0.241949] bus: [00, 1f] on node 0 link 0
[    0.241949] bus: 00 index 0 [io  0x0000-0xffff]
[    0.241949] bus: 00 index 1 [mem 0xf0000000-0xffffffff]
[    0.241949] bus: 00 index 2 [mem 0x000a0000-0x000bffff]
[    0.241949] bus: 00 index 3 [mem 0xc8000000-0xdfffffff]
[    0.241949] bus: 00 index 4 [mem 0x138000000-0xfcffffffff]
[    0.241949] Extended Config Space enabled on 1 nodes
[    0.241949] Trying to unpack rootfs image as initramfs...
[    0.241949] ACPI: bus type pci registered
[    0.241949] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.241949] PCI: not using MMCONFIG
[    0.241949] PCI : PCI BIOS aera is rw and x. Use pci=nobios if you want it NX.
[    0.241949] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=3
[    0.241949] PCI: Using configuration type 1 for base access
[    0.241949] PCI: Using configuration type 1 for extended access
[    0.244550] bio: create slab <bio-0> at 0
[    0.244986] ACPI: EC: Look up EC in DSDT
[    0.246125] ACPI: Executed 3 blocks of module-level executable AML code
[    0.392295] ACPI: Interpreter enabled
[    0.392301] ACPI: (supports S0 S1 S3 S4 S5)
[    0.392321] ACPI: Using IOAPIC for interrupt routing
[    0.392343] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.392925] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI motherboard resources
[    0.392927] PCI: Using MMCONFIG for extended config space
[    0.396343] ACPI: No dock devices found.
[    0.396345] HEST: Table not found.
[    0.396348] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.396485] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.396622] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7]
[    0.396624] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff]
[    0.396626] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.396629] pci_root PNP0A03:00: host bridge window [mem 0x000d0000-0x000dffff]
[    0.396631] pci_root PNP0A03:00: host bridge window [mem 0xc8000000-0xdfffffff]
[    0.396633] pci_root PNP0A03:00: host bridge window [mem 0xf0000000-0xfebfffff]
[    0.396645] pci 0000:00:00.0: [1002:5957] type 0 class 0x000600
[    0.396681] pci 0000:00:02.0: [1002:5978] type 1 class 0x000604
[    0.396704] pci 0000:00:02.0: PME# supported from D0 D3hot D3cold
[    0.396706] pci 0000:00:02.0: PME# disabled
[    0.396718] pci 0000:00:04.0: [1002:597a] type 1 class 0x000604
[    0.396740] pci 0000:00:04.0: PME# supported from D0 D3hot D3cold
[    0.396743] pci 0000:00:04.0: PME# disabled
[    0.396768] pci 0000:00:11.0: [1002:4391] type 0 class 0x000106
[    0.396783] pci 0000:00:11.0: reg 10: [io  0xc000-0xc007]
[    0.396791] pci 0000:00:11.0: reg 14: [io  0xb000-0xb003]
[    0.396798] pci 0000:00:11.0: reg 18: [io  0xa000-0xa007]
[    0.396806] pci 0000:00:11.0: reg 1c: [io  0x9000-0x9003]
[    0.396813] pci 0000:00:11.0: reg 20: [io  0x8000-0x800f]
[    0.396821] pci 0000:00:11.0: reg 24: [mem 0xf3fffc00-0xf3ffffff]
[    0.396855] pci 0000:00:12.0: [1002:4397] type 0 class 0x000c03
[    0.396866] pci 0000:00:12.0: reg 10: [mem 0xf3ffe000-0xf3ffefff]
[    0.396918] pci 0000:00:12.2: [1002:4396] type 0 class 0x000c03
[    0.396932] pci 0000:00:12.2: reg 10: [mem 0xf3fff800-0xf3fff8ff]
[    0.396984] pci 0000:00:12.2: supports D1 D2
[    0.396985] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
[    0.396989] pci 0000:00:12.2: PME# disabled
[    0.397004] pci 0000:00:13.0: [1002:4397] type 0 class 0x000c03
[    0.397015] pci 0000:00:13.0: reg 10: [mem 0xf3ffd000-0xf3ffdfff]
[    0.397066] pci 0000:00:13.2: [1002:4396] type 0 class 0x000c03
[    0.397081] pci 0000:00:13.2: reg 10: [mem 0xf3fff400-0xf3fff4ff]
[    0.397132] pci 0000:00:13.2: supports D1 D2
[    0.397134] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    0.397137] pci 0000:00:13.2: PME# disabled
[    0.397153] pci 0000:00:14.0: [1002:4385] type 0 class 0x000c05
[    0.397209] pci 0000:00:14.2: [1002:4383] type 0 class 0x000403
[    0.397225] pci 0000:00:14.2: reg 10: [mem 0xf3ff4000-0xf3ff7fff 64bit]
[    0.397268] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    0.397272] pci 0000:00:14.2: PME# disabled
[    0.397281] pci 0000:00:14.3: [1002:439d] type 0 class 0x000601
[    0.397336] pci 0000:00:14.4: [1002:4384] type 1 class 0x000604
[    0.397366] pci 0000:00:14.5: [1002:4399] type 0 class 0x000c03
[    0.397376] pci 0000:00:14.5: reg 10: [mem 0xf3ffc000-0xf3ffcfff]
[    0.397427] pci 0000:00:16.0: [1002:4397] type 0 class 0x000c03
[    0.397437] pci 0000:00:16.0: reg 10: [mem 0xf3ff3000-0xf3ff3fff]
[    0.397488] pci 0000:00:16.2: [1002:4396] type 0 class 0x000c03
[    0.397503] pci 0000:00:16.2: reg 10: [mem 0xf3fff000-0xf3fff0ff]
[    0.397554] pci 0000:00:16.2: supports D1 D2
[    0.397556] pci 0000:00:16.2: PME# supported from D0 D1 D2 D3hot
[    0.397559] pci 0000:00:16.2: PME# disabled
[    0.397574] pci 0000:00:18.0: [1022:1200] type 0 class 0x000600
[    0.397588] pci 0000:00:18.1: [1022:1201] type 0 class 0x000600
[    0.397599] pci 0000:00:18.2: [1022:1202] type 0 class 0x000600
[    0.397611] pci 0000:00:18.3: [1022:1203] type 0 class 0x000600
[    0.397625] pci 0000:00:18.4: [1022:1204] type 0 class 0x000600
[    0.397670] pci 0000:01:00.0: [10de:0a65] type 0 class 0x000300
[    0.397679] pci 0000:01:00.0: reg 10: [mem 0xf4000000-0xf4ffffff]
[    0.397689] pci 0000:01:00.0: reg 14: [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.397699] pci 0000:01:00.0: reg 1c: [mem 0xce000000-0xcfffffff 64bit pref]
[    0.397706] pci 0000:01:00.0: reg 24: [io  0xdc00-0xdc7f]
[    0.397713] pci 0000:01:00.0: reg 30: [mem 0xf5e80000-0xf5efffff pref]
[    0.397753] pci 0000:01:00.1: [10de:0be3] type 0 class 0x000403
[    0.397762] pci 0000:01:00.1: reg 10: [mem 0xf5e7c000-0xf5e7ffff]
[    0.404042] pci 0000:00:02.0: PCI bridge to [bus 01-01]
[    0.404052] pci 0000:00:02.0:   bridge window [io  0xd000-0xdfff]
[    0.404055] pci 0000:00:02.0:   bridge window [mem 0xf4000000-0xf5efffff]
[    0.404058] pci 0000:00:02.0:   bridge window [mem 0xce000000-0xdfffffff 64bit pref]
[    0.404099] pci 0000:02:00.0: [1b21:1042] type 0 class 0x000c03
[    0.404117] pci 0000:02:00.0: reg 10: [mem 0xf5ff8000-0xf5ffffff 64bit]
[    0.404188] pci 0000:02:00.0: PME# supported from D3hot D3cold
[    0.404192] pci 0000:02:00.0: PME# disabled
[    0.412041] pci 0000:00:04.0: PCI bridge to [bus 02-02]
[    0.412046] pci 0000:00:04.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.412053] pci 0000:00:04.0:   bridge window [mem 0xf5f00000-0xf5ffffff]
[    0.412056] pci 0000:00:04.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.412085] pci 0000:03:05.0: [10ec:8169] type 0 class 0x000200
[    0.412104] pci 0000:03:05.0: reg 10: [io  0xe800-0xe8ff]
[    0.412114] pci 0000:03:05.0: reg 14: [mem 0xfebffc00-0xfebffcff]
[    0.412157] pci 0000:03:05.0: reg 30: [mem 0xfebc0000-0xfebdffff pref]
[    0.412178] pci 0000:03:05.0: supports D1 D2
[    0.412180] pci 0000:03:05.0: PME# supported from D1 D2 D3hot
[    0.412184] pci 0000:03:05.0: PME# disabled
[    0.412203] pci 0000:03:06.0: [14f1:8800] type 0 class 0x000400
[    0.412222] pci 0000:03:06.0: reg 10: [mem 0xfd000000-0xfdffffff]
[    0.412310] pci 0000:03:06.1: [14f1:8801] type 0 class 0x000480
[    0.412327] pci 0000:03:06.1: reg 10: [mem 0xfc000000-0xfcffffff]
[    0.412409] pci 0000:03:06.2: [14f1:8802] type 0 class 0x000480
[    0.412426] pci 0000:03:06.2: reg 10: [mem 0xfb000000-0xfbffffff]
[    0.412508] pci 0000:03:06.4: [14f1:8804] type 0 class 0x000480
[    0.412525] pci 0000:03:06.4: reg 10: [mem 0xfa000000-0xfaffffff]
[    0.412612] pci 0000:03:07.0: [14f1:8800] type 0 class 0x000400
[    0.412632] pci 0000:03:07.0: reg 10: [mem 0xf9000000-0xf9ffffff]
[    0.412722] pci 0000:03:07.1: [14f1:8801] type 0 class 0x000480
[    0.412739] pci 0000:03:07.1: reg 10: [mem 0xf8000000-0xf8ffffff]
[    0.412820] pci 0000:03:07.2: [14f1:8802] type 0 class 0x000480
[    0.412837] pci 0000:03:07.2: reg 10: [mem 0xf7000000-0xf7ffffff]
[    0.412919] pci 0000:03:07.4: [14f1:8804] type 0 class 0x000480
[    0.412937] pci 0000:03:07.4: reg 10: [mem 0xf6000000-0xf6ffffff]
[    0.413041] pci 0000:00:14.4: PCI bridge to [bus 03-03] (subtractive decode)
[    0.413045] pci 0000:00:14.4:   bridge window [io  0xe000-0xefff]
[    0.413048] pci 0000:00:14.4:   bridge window [mem 0xf6000000-0xfebfffff]
[    0.413052] pci 0000:00:14.4:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.413054] pci 0000:00:14.4:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.413056] pci 0000:00:14.4:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.413058] pci 0000:00:14.4:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.413061] pci 0000:00:14.4:   bridge window [mem 0x000d0000-0x000dffff] (subtractive decode)
[    0.413063] pci 0000:00:14.4:   bridge window [mem 0xc8000000-0xdfffffff] (subtractive decode)
[    0.413065] pci 0000:00:14.4:   bridge window [mem 0xf0000000-0xfebfffff] (subtractive decode)
[    0.413075] pci_bus 0000:00: on NUMA node 0
[    0.413079] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.413242] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE2._PRT]
[    0.413267] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE4._PRT]
[    0.413302] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0PC._PRT]
[    0.413435]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.413546]  pci0000:00: ACPI _OSC control (0x1d) granted
[    0.416793] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 14 15)
[    0.416841] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 7 9 10 11 14 15)
[    0.416888] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 *10 11 14 15)
[    0.416935] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 *9 10 11 14 15)
[    0.416971] ACPI: PCI Interrupt Link [LNKE] (IRQs *3 4 5 6 7 9 10 11 14 15)
[    0.416999] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 *7 9 10 11 14 15)
[    0.417027] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 *6 7 9 10 11 14 15)
[    0.417057] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 11 14 15) *0
[    0.417135] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.417141] vgaarb: loaded
[    0.417277] SCSI subsystem initialized
[    0.417292] libata version 3.00 loaded.
[    0.417292] usbcore: registered new interface driver usbfs
[    0.417292] usbcore: registered new interface driver hub
[    0.417292] usbcore: registered new device driver usb
[    0.417292] wmi: Mapper loaded
[    0.417292] PCI: Using ACPI for IRQ routing
[    0.417292] PCI: pci_cache_line_size set to 64 bytes
[    0.417292] reserve RAM buffer: 000000000009ac00 - 000000000009ffff 
[    0.417292] reserve RAM buffer: 00000000c7f90000 - 00000000c7ffffff 
[    0.417292] NetLabel: Initializing
[    0.417292] NetLabel:  domain hash size = 128
[    0.417292] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.417292] NetLabel:  unlabeled traffic allowed by default
[    0.417292] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.417292] hpet0: 3 comparators, 32-bit 14.318180 MHz counter
[    0.418364] Switching to clocksource hpet
[    0.418511] Switched to NOHz mode on CPU #0
[    0.418368] Switched to NOHz mode on CPU #2
[    0.419903] Switched to NOHz mode on CPU #1
[    0.420882] AppArmor: AppArmor Filesystem Enabled
[    0.420896] pnp: PnP ACPI init
[    0.420907] ACPI: bus type pnp registered
[    0.420993] pnp 00:00: [bus 00-ff]
[    0.420995] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.420998] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.420999] pnp 00:00: [io  0x0d00-0xffff window]
[    0.421001] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.421003] pnp 00:00: [mem 0x000d0000-0x000dffff window]
[    0.421005] pnp 00:00: [mem 0xc8000000-0xdfffffff window]
[    0.421007] pnp 00:00: [mem 0xf0000000-0xfebfffff window]
[    0.421039] pnp 00:00: Plug and Play ACPI device, IDs PNP0a03 (active)
[    0.421074] pnp 00:01: [dma 4]
[    0.421076] pnp 00:01: [io  0x0000-0x000f]
[    0.421078] pnp 00:01: [io  0x0081-0x0083]
[    0.421079] pnp 00:01: [io  0x0087]
[    0.421081] pnp 00:01: [io  0x0089-0x008b]
[    0.421082] pnp 00:01: [io  0x008f]
[    0.421084] pnp 00:01: [io  0x00c0-0x00df]
[    0.421107] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.421116] pnp 00:02: [io  0x0070-0x0071]
[    0.421124] pnp 00:02: [irq 8]
[    0.421146] pnp 00:02: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.421152] pnp 00:03: [io  0x0061]
[    0.421173] pnp 00:03: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.421179] pnp 00:04: [io  0x00f0-0x00ff]
[    0.421182] pnp 00:04: [irq 13]
[    0.421206] pnp 00:04: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.421324] pnp 00:05: [io  0x0000-0xffffffffffffffff disabled]
[    0.421326] pnp 00:05: [io  0x0000-0xffffffffffffffff disabled]
[    0.421328] pnp 00:05: [io  0x0290-0x029f]
[    0.421370] system 00:05: [io  0x0290-0x029f] has been reserved
[    0.421373] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.421402] pnp 00:06: [mem 0xfed00000-0xfed003ff]
[    0.421427] pnp 00:06: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.421615] pnp 00:07: [io  0x03f8-0x03ff]
[    0.421619] pnp 00:07: [irq 4]
[    0.421620] pnp 00:07: [dma 0 disabled]
[    0.421687] pnp 00:07: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.421743] pnp 00:08: [io  0x0060]
[    0.421744] pnp 00:08: [io  0x0064]
[    0.421746] pnp 00:08: [mem 0xfec00000-0xfec00fff]
[    0.421748] pnp 00:08: [mem 0xfee00000-0xfee00fff]
[    0.421789] system 00:08: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.421792] system 00:08: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.421794] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.421902] pnp 00:09: [io  0x0010-0x001f]
[    0.421904] pnp 00:09: [io  0x0022-0x003f]
[    0.421906] pnp 00:09: [io  0x0062-0x0063]
[    0.421907] pnp 00:09: [io  0x0065-0x006f]
[    0.421909] pnp 00:09: [io  0x0072-0x007f]
[    0.421910] pnp 00:09: [io  0x0080]
[    0.421912] pnp 00:09: [io  0x0084-0x0086]
[    0.421913] pnp 00:09: [io  0x0088]
[    0.421914] pnp 00:09: [io  0x008c-0x008e]
[    0.421916] pnp 00:09: [io  0x0090-0x009f]
[    0.421917] pnp 00:09: [io  0x00a2-0x00bf]
[    0.421919] pnp 00:09: [io  0x00b1]
[    0.421920] pnp 00:09: [io  0x00e0-0x00ef]
[    0.421922] pnp 00:09: [io  0x04d0-0x04d1]
[    0.421923] pnp 00:09: [io  0x040b]
[    0.421925] pnp 00:09: [io  0x04d6]
[    0.421926] pnp 00:09: [io  0x0c00-0x0c01]
[    0.421928] pnp 00:09: [io  0x0c14]
[    0.421929] pnp 00:09: [io  0x0c50-0x0c51]
[    0.421931] pnp 00:09: [io  0x0c52]
[    0.421932] pnp 00:09: [io  0x0c6c]
[    0.421933] pnp 00:09: [io  0x0c6f]
[    0.421935] pnp 00:09: [io  0x0cd0-0x0cd1]
[    0.421936] pnp 00:09: [io  0x0cd2-0x0cd3]
[    0.421939] pnp 00:09: [io  0x0cd4-0x0cd5]
[    0.421941] pnp 00:09: [io  0x0cd6-0x0cd7]
[    0.421942] pnp 00:09: [io  0x0cd8-0x0cdf]
[    0.421944] pnp 00:09: [io  0x0b00-0x0b3f]
[    0.421945] pnp 00:09: [io  0x0800-0x089f]
[    0.421947] pnp 00:09: [io  0x0000-0xffffffffffffffff disabled]
[    0.421949] pnp 00:09: [io  0x0b00-0x0b1f]
[    0.421950] pnp 00:09: [io  0x0b20-0x0b3f]
[    0.421952] pnp 00:09: [io  0x0900-0x090f]
[    0.421953] pnp 00:09: [io  0x0910-0x091f]
[    0.421955] pnp 00:09: [io  0xfe00-0xfefe]
[    0.421957] pnp 00:09: [io  0x0060]
[    0.421958] pnp 00:09: [io  0x0064]
[    0.421960] pnp 00:09: [mem 0x00000000-0xffffffffffffffff disabled]
[    0.421962] pnp 00:09: [mem 0xffb80000-0xffbfffff]
[    0.421963] pnp 00:09: [mem 0xfec10000-0xfec1001f]
[    0.421965] pnp 00:09: [mem 0xfed40000-0xfed44fff]
[    0.421967] pnp 00:09: [mem 0xfed80000-0xfed80fff]
[    0.421968] pnp 00:09: [mem 0x00000000-0xffffffffffffffff disabled]
[    0.422048] system 00:09: [io  0x04d0-0x04d1] has been reserved
[    0.422050] system 00:09: [io  0x040b] has been reserved
[    0.422052] system 00:09: [io  0x04d6] has been reserved
[    0.422054] system 00:09: [io  0x0c00-0x0c01] has been reserved
[    0.422056] system 00:09: [io  0x0c14] has been reserved
[    0.422058] system 00:09: [io  0x0c50-0x0c51] has been reserved
[    0.422060] system 00:09: [io  0x0c52] has been reserved
[    0.422062] system 00:09: [io  0x0c6c] has been reserved
[    0.422064] system 00:09: [io  0x0c6f] has been reserved
[    0.422066] system 00:09: [io  0x0cd0-0x0cd1] has been reserved
[    0.422068] system 00:09: [io  0x0cd2-0x0cd3] has been reserved
[    0.422070] system 00:09: [io  0x0cd4-0x0cd5] has been reserved
[    0.422072] system 00:09: [io  0x0cd6-0x0cd7] has been reserved
[    0.422074] system 00:09: [io  0x0cd8-0x0cdf] has been reserved
[    0.422076] system 00:09: [io  0x0b00-0x0b3f] has been reserved
[    0.422078] system 00:09: [io  0x0800-0x089f] has been reserved
[    0.422081] system 00:09: [io  0x0b00-0x0b1f] has been reserved
[    0.422083] system 00:09: [io  0x0b20-0x0b3f] has been reserved
[    0.422085] system 00:09: [io  0x0900-0x090f] has been reserved
[    0.422087] system 00:09: [io  0x0910-0x091f] has been reserved
[    0.422089] system 00:09: [io  0xfe00-0xfefe] has been reserved
[    0.422092] system 00:09: [mem 0xffb80000-0xffbfffff] has been reserved
[    0.422094] system 00:09: [mem 0xfec10000-0xfec1001f] has been reserved
[    0.422097] system 00:09: [mem 0xfed40000-0xfed44fff] has been reserved
[    0.422099] system 00:09: [mem 0xfed80000-0xfed80fff] has been reserved
[    0.422102] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.422125] pnp 00:0a: [mem 0xe0000000-0xefffffff]
[    0.422167] system 00:0a: [mem 0xe0000000-0xefffffff] has been reserved
[    0.422170] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.422244] pnp 00:0b: [mem 0x00000000-0x0009ffff]
[    0.422246] pnp 00:0b: [mem 0x000c0000-0x000cffff]
[    0.422247] pnp 00:0b: [mem 0x000e0000-0x000fffff]
[    0.422249] pnp 00:0b: [mem 0x00100000-0xc7ffffff]
[    0.422251] pnp 00:0b: [mem 0xfec00000-0xffffffff]
[    0.422294] system 00:0b: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.422296] system 00:0b: [mem 0x000c0000-0x000cffff] could not be reserved
[    0.422298] system 00:0b: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.422301] system 00:0b: [mem 0x00100000-0xc7ffffff] could not be reserved
[    0.422303] system 00:0b: [mem 0xfec00000-0xffffffff] could not be reserved
[    0.422305] system 00:0b: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.422375] pnp: PnP ACPI: found 12 devices
[    0.422377] ACPI: ACPI bus type pnp unregistered
[    0.422379] PnPBIOS: Disabled by ACPI PNP
[    0.458115] pci 0000:00:02.0: PCI bridge to [bus 01-01]
[    0.458118] pci 0000:00:02.0:   bridge window [io  0xd000-0xdfff]
[    0.458121] pci 0000:00:02.0:   bridge window [mem 0xf4000000-0xf5efffff]
[    0.458124] pci 0000:00:02.0:   bridge window [mem 0xce000000-0xdfffffff 64bit pref]
[    0.458127] pci 0000:00:04.0: PCI bridge to [bus 02-02]
[    0.458129] pci 0000:00:04.0:   bridge window [io  disabled]
[    0.458131] pci 0000:00:04.0:   bridge window [mem 0xf5f00000-0xf5ffffff]
[    0.458134] pci 0000:00:04.0:   bridge window [mem pref disabled]
[    0.458137] pci 0000:00:14.4: PCI bridge to [bus 03-03]
[    0.458140] pci 0000:00:14.4:   bridge window [io  0xe000-0xefff]
[    0.458144] pci 0000:00:14.4:   bridge window [mem 0xf6000000-0xfebfffff]
[    0.458147] pci 0000:00:14.4:   bridge window [mem pref disabled]
[    0.458164] pci 0000:00:02.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.458167] pci 0000:00:02.0: setting latency timer to 64
[    0.458174] pci 0000:00:04.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.458177] pci 0000:00:04.0: setting latency timer to 64
[    0.458183] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.458185] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.458187] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.458189] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
[    0.458191] pci_bus 0000:00: resource 8 [mem 0xc8000000-0xdfffffff]
[    0.458193] pci_bus 0000:00: resource 9 [mem 0xf0000000-0xfebfffff]
[    0.458195] pci_bus 0000:01: resource 0 [io  0xd000-0xdfff]
[    0.458197] pci_bus 0000:01: resource 1 [mem 0xf4000000-0xf5efffff]
[    0.458199] pci_bus 0000:01: resource 2 [mem 0xce000000-0xdfffffff 64bit pref]
[    0.458201] pci_bus 0000:02: resource 1 [mem 0xf5f00000-0xf5ffffff]
[    0.458203] pci_bus 0000:03: resource 0 [io  0xe000-0xefff]
[    0.458204] pci_bus 0000:03: resource 1 [mem 0xf6000000-0xfebfffff]
[    0.458206] pci_bus 0000:03: resource 4 [io  0x0000-0x0cf7]
[    0.458208] pci_bus 0000:03: resource 5 [io  0x0d00-0xffff]
[    0.458210] pci_bus 0000:03: resource 6 [mem 0x000a0000-0x000bffff]
[    0.458212] pci_bus 0000:03: resource 7 [mem 0x000d0000-0x000dffff]
[    0.458214] pci_bus 0000:03: resource 8 [mem 0xc8000000-0xdfffffff]
[    0.458216] pci_bus 0000:03: resource 9 [mem 0xf0000000-0xfebfffff]
[    0.458244] NET: Registered protocol family 2
[    0.458300] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.458478] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.458929] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.459156] TCP: Hash tables configured (established 131072 bind 65536)
[    0.459158] TCP reno registered
[    0.459161] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.459169] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.459241] NET: Registered protocol family 1
[    1.257083] Freeing initrd memory: 12540k freed
[    1.312063] pci 0000:01:00.0: Boot video device
[    1.312107] PCI: CLS 64 bytes, default 64
[    1.312334] cpufreq-nforce2: No nForce2 chipset.
[    1.312434] audit: initializing netlink socket (disabled)
[    1.312442] type=2000 audit(1313838272.308:1): initialized
[    1.320013] highmem bounce pool size: 64 pages
[    1.320017] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.321249] VFS: Disk quotas dquot_6.5.2
[    1.321291] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.321809] fuse init (API version 7.16)
[    1.321872] msgmni has been set to 1634
[    1.322134] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    1.322162] io scheduler noop registered
[    1.322164] io scheduler deadline registered
[    1.322178] io scheduler cfq registered (default)
[    1.322268] pcieport 0000:00:02.0: setting latency timer to 64
[    1.322295] pcieport 0000:00:02.0: irq 40 for MSI/MSI-X
[    1.322344] pcieport 0000:00:04.0: setting latency timer to 64
[    1.322363] pcieport 0000:00:04.0: irq 41 for MSI/MSI-X
[    1.322423] pcieport 0000:00:02.0: Signaling PME through PCIe PME interrupt
[    1.322425] pci 0000:01:00.0: Signaling PME through PCIe PME interrupt
[    1.322426] pci 0000:01:00.1: Signaling PME through PCIe PME interrupt
[    1.322429] pcie_pme 0000:00:02.0cie01: service driver pcie_pme loaded
[    1.322438] pcieport 0000:00:04.0: Signaling PME through PCIe PME interrupt
[    1.322440] pci 0000:02:00.0: Signaling PME through PCIe PME interrupt
[    1.322442] pcie_pme 0000:00:04.0cie01: service driver pcie_pme loaded
[    1.322455] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.322472] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.322581] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    1.322593] ACPI: Power Button [PWRB]
[    1.322651] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    1.322654] ACPI: Power Button [PWRF]
[    1.322767] ACPI: acpi_idle registered with cpuidle
[    1.324205] ERST: Table is not found!
[    1.324230] isapnp: Scanning for PnP cards...
[    1.324274] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.344623] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.677791] isapnp: No Plug & Play device found
[    1.752477] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.752694] Linux agpgart interface v0.103
[    1.753726] brd: module loaded
[    1.754115] loop: module loaded
[    1.754181] i2c-core: driver [adp5520] using legacy suspend method
[    1.754183] i2c-core: driver [adp5520] using legacy resume method
[    1.754500] Fixed MDIO Bus: probed
[    1.754521] PPP generic driver version 2.4.2
[    1.754545] tun: Universal TUN/TAP device driver, 1.6
[    1.754546] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.754606] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.754624] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.754635] ehci_hcd 0000:00:12.2: EHCI Host Controller
[    1.754659] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
[    1.756044] ehci_hcd 0000:00:12.2: QUIRK: Enable exception for AMD Hudson ASPM
[    1.756048] ehci_hcd 0000:00:12.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.756065] ehci_hcd 0000:00:12.2: debug port 1
[    1.756082] ehci_hcd 0000:00:12.2: irq 17, io mem 0xf3fff800
[    1.768027] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    1.768127] hub 1-0:1.0: USB hub found
[    1.768131] hub 1-0:1.0: 5 ports detected
[    1.768189] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.768200] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    1.768226] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
[    1.768263] ehci_hcd 0000:00:13.2: QUIRK: Enable exception for AMD Hudson ASPM
[    1.768267] ehci_hcd 0000:00:13.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.768285] ehci_hcd 0000:00:13.2: debug port 1
[    1.768296] ehci_hcd 0000:00:13.2: irq 17, io mem 0xf3fff400
[    1.780025] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    1.780118] hub 2-0:1.0: USB hub found
[    1.780121] hub 2-0:1.0: 5 ports detected
[    1.780180] ehci_hcd 0000:00:16.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.780191] ehci_hcd 0000:00:16.2: EHCI Host Controller
[    1.780219] ehci_hcd 0000:00:16.2: new USB bus registered, assigned bus number 3
[    1.780257] ehci_hcd 0000:00:16.2: QUIRK: Enable exception for AMD Hudson ASPM
[    1.780261] ehci_hcd 0000:00:16.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.780277] ehci_hcd 0000:00:16.2: debug port 1
[    1.780288] ehci_hcd 0000:00:16.2: irq 17, io mem 0xf3fff000
[    1.792027] ehci_hcd 0000:00:16.2: USB 2.0 started, EHCI 1.00
[    1.792114] hub 3-0:1.0: USB hub found
[    1.792117] hub 3-0:1.0: 4 ports detected
[    1.792175] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.792186] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.792196] ohci_hcd 0000:00:12.0: OHCI Host Controller
[    1.792222] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 4
[    1.792271] ohci_hcd 0000:00:12.0: irq 18, io mem 0xf3ffe000
[    1.852094] hub 4-0:1.0: USB hub found
[    1.852099] hub 4-0:1.0: 5 ports detected
[    1.852156] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.852166] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    1.852193] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5
[    1.856052] ohci_hcd 0000:00:13.0: irq 18, io mem 0xf3ffd000
[    1.916096] hub 5-0:1.0: USB hub found
[    1.916101] hub 5-0:1.0: 5 ports detected
[    1.916160] ohci_hcd 0000:00:14.5: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.916170] ohci_hcd 0000:00:14.5: OHCI Host Controller
[    1.916199] ohci_hcd 0000:00:14.5: new USB bus registered, assigned bus number 6
[    1.916241] ohci_hcd 0000:00:14.5: irq 18, io mem 0xf3ffc000
[    1.976094] hub 6-0:1.0: USB hub found
[    1.976099] hub 6-0:1.0: 2 ports detected
[    1.976155] ohci_hcd 0000:00:16.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.976165] ohci_hcd 0000:00:16.0: OHCI Host Controller
[    1.976190] ohci_hcd 0000:00:16.0: new USB bus registered, assigned bus number 7
[    1.976234] ohci_hcd 0000:00:16.0: irq 18, io mem 0xf3ff3000
[    2.036103] hub 7-0:1.0: USB hub found
[    2.036108] hub 7-0:1.0: 4 ports detected
[    2.036164] uhci_hcd: USB Universal Host Controller Interface driver
[    2.036217] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    2.038987] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.038993] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.039111] mousedev: PS/2 mouse device common for all mice
[    2.039200] rtc_cmos 00:02: RTC can wake from S4
[    2.056086] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    2.056105] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    2.056164] device-mapper: uevent: version 1.0.3
[    2.056221] device-mapper: ioctl: 4.19.1-ioctl (2011-01-07) initialised: [EMAIL="dm-devel@redhat.com"][/EMAIL]
[    2.056286] device-mapper: multipath: version 1.2.0 loaded
[    2.056288] device-mapper: multipath round-robin: version 1.0.0 loaded
[    2.056342] EISA: Probing bus 0 at eisa.0
[    2.056344] EISA: Cannot allocate resource for mainboard
[    2.056345] Cannot allocate resource for EISA slot 1
[    2.056347] Cannot allocate resource for EISA slot 2
[    2.056348] Cannot allocate resource for EISA slot 3
[    2.056350] Cannot allocate resource for EISA slot 4
[    2.056351] Cannot allocate resource for EISA slot 5
[    2.056352] Cannot allocate resource for EISA slot 6
[    2.056354] Cannot allocate resource for EISA slot 7
[    2.056355] Cannot allocate resource for EISA slot 8
[    2.056356] EISA: Detected 0 cards.
[    2.056407] cpuidle: using governor ladder
[    2.056408] cpuidle: using governor menu
[    2.056599] TCP cubic registered
[    2.056692] NET: Registered protocol family 10
[    2.057113] NET: Registered protocol family 17
[    2.057123] Registering the dns_resolver key type
[    2.057154] powernow-k8: Found 1 AMD Phenom(tm) II X3 720 Processor (3 cpu cores) (version 2.20.00)
[    2.057160] [Firmware Bug]: powernow-k8: No compatible ACPI _PSS objects found.
[    2.057161] [Firmware Bug]: powernow-k8: Try again with latest BIOS.
[    2.057183] Using IPI No-Shortcut mode
[    2.057240] PM: Hibernation image not present or could not be loaded.
[    2.057247] registered taskstats version 1
[    2.057495]   Magic number: 7:194:75
[    2.057554] rtc_cmos 00:02: setting system clock to 2011-08-20 11:04:33 UTC (1313838273)
[    2.057556] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.057557] EDD information not available.
[    2.057656] Freeing unused kernel memory: 720k freed
[    2.057896] Write protecting the kernel text: 5352k
[    2.057942] Write protecting the kernel read-only data: 2192k
[    2.057944] NX-protecting the kernel data: 4888k
[    2.072450] <30>udev[66]: starting version 167
[    2.106792] xhci_hcd 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.106813] xhci_hcd 0000:02:00.0: setting latency timer to 64
[    2.106816] xhci_hcd 0000:02:00.0: xHCI Host Controller
[    2.106873] xhci_hcd 0000:02:00.0: new USB bus registered, assigned bus number 8
[    2.117367] ahci 0000:00:11.0: version 3.0
[    2.117385] ahci 0000:00:11.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    2.117487] ahci 0000:00:11.0: AHCI 0001.0200 32 slots 6 ports 6 Gbps 0x3f impl SATA mode
[    2.117490] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part 
[    2.118966] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    2.118982] r8169 0000:03:05.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    2.119000] r8169 0000:03:05.0: (unregistered net_device): no PCI Express capability
[    2.119387] r8169 0000:03:05.0: eth0: RTL8169sb/8110sb at 0xf842ec00, 00:0c:76:a0:02:d9, XID 10000000 IRQ 20
[    2.119397] scsi0 : ahci
[    2.119498] scsi1 : ahci
[    2.119554] scsi2 : ahci
[    2.119608] scsi3 : ahci
[    2.119668] scsi4 : ahci
[    2.119719] scsi5 : ahci
[    2.119760] ata1: SATA max UDMA/133 abar m1024@0xf3fffc00 port 0xf3fffd00 irq 19
[    2.119763] ata2: SATA max UDMA/133 abar m1024@0xf3fffc00 port 0xf3fffd80 irq 19
[    2.119766] ata3: SATA max UDMA/133 abar m1024@0xf3fffc00 port 0xf3fffe00 irq 19
[    2.119768] ata4: SATA max UDMA/133 abar m1024@0xf3fffc00 port 0xf3fffe80 irq 19
[    2.119771] ata5: SATA max UDMA/133 abar m1024@0xf3fffc00 port 0xf3ffff00 irq 19
[    2.119774] ata6: SATA max UDMA/133 abar m1024@0xf3fffc00 port 0xf3ffff80 irq 19
[    2.129856] xhci_hcd 0000:02:00.0: irq 16, io mem 0xf5ff8000
[    2.129895] xhci_hcd 0000:02:00.0: irq 42 for MSI/MSI-X
[    2.129901] xhci_hcd 0000:02:00.0: irq 43 for MSI/MSI-X
[    2.129905] xhci_hcd 0000:02:00.0: irq 44 for MSI/MSI-X
[    2.129910] xhci_hcd 0000:02:00.0: irq 45 for MSI/MSI-X
[    2.129967] usb usb8: No SuperSpeed endpoint companion for config 1  interface 0 altsetting 0 ep 129: using minimum values
[    2.130046] xHCI xhci_add_endpoint called for root hub
[    2.130048] xHCI xhci_check_bandwidth called for root hub
[    2.130071] hub 8-0:1.0: USB hub found
[    2.130074] hub 8-0:1.0: 4 ports detected
[    2.252028] usb 5-2: new low speed USB device using ohci_hcd and address 2
[    2.312023] Refined TSC clocksource calibration: 2799.887 MHz.
[    2.312027] Switching to clocksource tsc
[    2.440072] ata5: SATA link down (SStatus 0 SControl 300)
[    2.448054] ata4: SATA link down (SStatus 0 SControl 300)
[    2.612025] ata6: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.612047] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.613351] ata6.00: ATAPI: TSSTcorp CDDVDW SH-S223C, SB02, max UDMA/100
[    2.620024] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.620043] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.621351] ata3.00: ATA-8: Hitachi HDS721010CLA332, JP4OA39C, max UDMA/133
[    2.621354] ata3.00: 1953525168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
[    2.622832] ata3.00: configured for UDMA/133
[    2.645708] ata1.00: ATA-7: ST3500630AS, 3.AAK, max UDMA/133
[    2.645711] ata1.00: 976773168 sectors, multi 0: LBA48 NCQ (depth 31/32)
[    2.660030] ata2.00: ATA-7: ST3750640AS, 3.AAE, max UDMA/133
[    2.660032] ata2.00: 1465149168 sectors, multi 0: LBA48 NCQ (depth 31/32)
[    2.688019] usb 5-3: new low speed USB device using ohci_hcd and address 3
[    2.704022] ata1.00: configured for UDMA/133
[    2.704147] scsi 0:0:0:0: Direct-Access     ATA      ST3500630AS      3.AA PQ: 0 ANSI: 5
[    2.704273] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.704296] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    2.704338] sd 0:0:0:0: [sda] Write Protect is off
[    2.704340] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.704354] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.718336] ata2.00: configured for UDMA/133
[    2.718434] scsi 1:0:0:0: Direct-Access     ATA      ST3750640AS      3.AA PQ: 0 ANSI: 5
[    2.718535] sd 1:0:0:0: [sdb] 1465149168 512-byte logical blocks: (750 GB/698 GiB)
[    2.718547] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    2.718564] sd 1:0:0:0: [sdb] Write Protect is off
[    2.718567] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    2.718581] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.718649] scsi 2:0:0:0: Direct-Access     ATA      Hitachi HDS72101 JP4O PQ: 0 ANSI: 5
[    2.718774] sd 2:0:0:0: Attached scsi generic sg2 type 0
[    2.718832] sd 2:0:0:0: [sdc] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    2.718887] sd 2:0:0:0: [sdc] Write Protect is off
[    2.718890] sd 2:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    2.718913] sd 2:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.758032]  sdb: sdb1
[    2.758186] sd 1:0:0:0: [sdb] Attached SCSI disk
[    2.759927] Alternate GPT is invalid, using primary GPT.
[    2.759941]  sdc: sdc1
[    2.760165] sd 2:0:0:0: [sdc] Attached SCSI disk
[    2.760416]  sda: sda1 sda2
[    2.760599] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.876087] input:   SCISSORS Keyboard as /devices/pci0000:00/0000:00:13.0/usb5/5-2/5-2:1.0/input/input2
[    2.876154] generic-usb 0003:0DC6:3401.0001: input,hidraw0: USB HID v1.00 Keyboard [  SCISSORS Keyboard] on usb-0000:00:13.0-2/input0
[    2.881215] input: USB Optical Mouse as /devices/pci0000:00/0000:00:13.0/usb5/5-3/5-3:1.0/input/input3
[    2.881325] generic-usb 0003:1BCF:0007.0002: input,hiddev0,hidraw1: USB HID v1.10 Mouse [USB Optical Mouse] on usb-0000:00:13.0-3/input0
[    2.881336] usbcore: registered new interface driver usbhid
[    2.881337] usbhid: USB HID core driver
[    3.213957] ata6.00: configured for UDMA/100
[    3.817006] scsi 5:0:0:0: CD-ROM            TSSTcorp CDDVDW SH-S223C  SB02 PQ: 0 ANSI: 5
[    3.820270] sr0: scsi3-mmc drive: 52x/52x writer dvd-ram cd/rw xa/form2 cdda tray
[    3.820273] cdrom: Uniform CD-ROM driver Revision: 3.20
[    3.820360] sr 5:0:0:0: Attached scsi CD-ROM sr0
[    3.820417] sr 5:0:0:0: Attached scsi generic sg3 type 5
[    4.115581] EXT3-fs (sda1): recovery required on readonly filesystem
[    4.115584] EXT3-fs (sda1): write access will be enabled during recovery
[    4.122626] EXT3-fs: barriers not enabled
[    4.360204] kjournald starting.  Commit interval 5 seconds
[    4.360330] EXT3-fs (sda1): orphan cleanup on readonly fs
[    4.360335] ext3_orphan_cleanup: deleting unreferenced inode 26558472
[    4.360351] ext3_orphan_cleanup: deleting unreferenced inode 26558476
[    4.360355] ext3_orphan_cleanup: deleting unreferenced inode 26558475
[    4.360359] ext3_orphan_cleanup: deleting unreferenced inode 26558474
[    4.360363] ext3_orphan_cleanup: deleting unreferenced inode 26558473
[    4.360366] EXT3-fs (sda1): 5 orphan inodes deleted
[    4.360368] EXT3-fs (sda1): recovery complete
[    4.373635] EXT3-fs (sda1): mounted filesystem with ordered data mode
[   25.112326] <30>udev[320]: starting version 167
[   25.126469] lp: driver loaded but no devices found
[   25.146822] Adding 1952764k swap on /dev/sda2.  Priority:-1 extents:1 across:1952764k 
[   25.154197] ACPI: resource piix4_smbus [io  0x0b00-0x0b07] conflicts with ACPI region SOR1 [io 0xb00-0xb0f]
[   25.154200] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   25.154806] SP5100 TCO timer: SP5100 TCO WatchDog Timer Driver v0.01
[   25.154861] SP5100 TCO timer: mmio address 0xb8fe00 already in use
[   25.215816] Linux video capture interface: v2.00
[   25.232372] <30>udev[346]: renamed network interface eth0 to eth1
[   25.242340] nvidia: module license 'NVIDIA' taints kernel.
[   25.242343] Disabling lock debugging due to kernel taint
[   25.251218] IR NEC protocol handler initialized
[   25.258068] IR RC5(x) protocol handler initialized
[   25.313466] cx88/0: cx2388x v4l2 driver version 0.0.8 loaded
[   25.313500] cx8800 0000:03:06.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   25.315177] cx88[0]: subsystem: 0070:6906, board: Hauppauge WinTV-HVR4000(Lite) DVB-S/S2 [card=69,autodetected], frontend(s): 1
[   25.315179] cx88[0]: TV tuner type -1, Radio tuner type -1
[   25.335714] cx88/2: cx2388x MPEG-TS Driver Manager version 0.0.8 loaded
[   25.345941] cx2388x alsa driver version 0.0.8 loaded
[   25.359414] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   25.370122] IR RC6 protocol handler initialized
[   25.371489] IR JVC protocol handler initialized
[   25.381142] IR Sony protocol handler initialized
[   25.381261] hda-intel: Enable sync_write for AMD chipset
[   25.393215] lirc_dev: IR Remote Control driver registered, major 250 
[   25.394233] IR LIRC bridge handler initialized
[   25.414657] type=1400 audit(1313838296.852:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=544 comm="apparmor_parser"
[   25.414684] type=1400 audit(1313838296.852:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=585 comm="apparmor_parser"
[   25.414940] type=1400 audit(1313838296.852:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=544 comm="apparmor_parser"
[   25.414969] type=1400 audit(1313838296.852:5): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=585 comm="apparmor_parser"
[   25.415122] type=1400 audit(1313838296.852:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=544 comm="apparmor_parser"
[   25.415156] type=1400 audit(1313838296.852:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=585 comm="apparmor_parser"
[   25.416829] type=1400 audit(1313838296.856:: apparmor="STATUS" operation="profile_load" name="/usr/sbin/ntpd" pid=654 comm="apparmor_parser"
[   25.419279] hda_codec: ALC887-VD: BIOS auto-probing.
[   25.429643] input: HDA ATI SB Headphone as /devices/pci0000:00/0000:00:14.2/sound/card0/input4
[   25.429854] HDA Intel 0000:01:00.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   25.429857] hda_intel: Disable MSI for Nvidia chipset
[   25.429884] HDA Intel 0000:01:00.1: setting latency timer to 64
[   25.442250] i2c-core: driver [tuner] using legacy suspend method
[   25.442252] i2c-core: driver [tuner] using legacy resume method
[   25.445766] type=1400 audit(1313838296.884:9): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/ntpd" pid=653 comm="apparmor_parser"
[   25.512229] tveeprom 0-0050: Hauppauge model 69100, rev B4C3, serial# 7793840
[   25.512233] tveeprom 0-0050: MAC address is 00:0d:fe:76:ec:b0
[   25.512235] tveeprom 0-0050: tuner model is Conexant CX24118A (idx 123, type 4)
[   25.512238] tveeprom 0-0050: TV standards ATSC/DVB Digital (eeprom 0x80)
[   25.512240] tveeprom 0-0050: audio processor is None (idx 0)
[   25.512241] tveeprom 0-0050: decoder processor is CX880 (idx 20)
[   25.512243] tveeprom 0-0050: has no radio, has IR receiver, has no IR transmitter
[   25.512245] cx88[0]: hauppauge eeprom: model=69100
[   25.536024] Registered IR keymap rc-rc5-hauppauge-new
[   25.536101] input: cx88 IR (Hauppauge WinTV-HVR400 as /devices/pci0000:00/0000:00:14.4/0000:03:06.0/rc/rc0/input5
[   25.536151] rc0: cx88 IR (Hauppauge WinTV-HVR400 as /devices/pci0000:00/0000:00:14.4/0000:03:06.0/rc/rc0
[   25.536279] rc rc0: lirc_dev: driver ir-lirc-codec (cx88xx) registered at minor = 0
[   25.536286] cx88[0]/0: found at 0000:03:06.0, rev: 5, irq: 21, latency: 64, mmio: 0xfd000000
[   25.536336] cx88[0]/0: registered device video0 [v4l2]
[   25.536359] cx88[0]/0: registered device vbi0
[   25.536421] cx8800 0000:03:07.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   25.538160] cx88[1]: subsystem: 0070:6906, board: Hauppauge WinTV-HVR4000(Lite) DVB-S/S2 [card=69,autodetected], frontend(s): 1
[   25.538162] cx88[1]: TV tuner type -1, Radio tuner type -1
[   25.717332] tveeprom 1-0050: Hauppauge model 69100, rev B4C3, serial# 7793859
[   25.717335] tveeprom 1-0050: MAC address is 00:0d:fe:76:ec:c3
[   25.717338] tveeprom 1-0050: tuner model is Conexant CX24118A (idx 123, type 4)
[   25.717340] tveeprom 1-0050: TV standards ATSC/DVB Digital (eeprom 0x80)
[   25.717343] tveeprom 1-0050: audio processor is None (idx 0)
[   25.717345] tveeprom 1-0050: decoder processor is CX880 (idx 20)
[   25.717347] tveeprom 1-0050: has no radio, has IR receiver, has no IR transmitter
[   25.717348] cx88[1]: hauppauge eeprom: model=69100
[   25.719800] Registered IR keymap rc-rc5-hauppauge-new
[   25.719880] input: cx88 IR (Hauppauge WinTV-HVR400 as /devices/pci0000:00/0000:00:14.4/0000:03:07.0/rc/rc1/input6
[   25.719931] rc1: cx88 IR (Hauppauge WinTV-HVR400 as /devices/pci0000:00/0000:00:14.4/0000:03:07.0/rc/rc1
[   25.720076] rc rc1: lirc_dev: driver ir-lirc-codec (cx88xx) registered at minor = 1
[   25.720083] cx88[1]/0: found at 0000:03:07.0, rev: 5, irq: 22, latency: 64, mmio: 0xf9000000
[   25.720144] cx88[1]/0: registered device video1 [v4l2]
[   25.720169] cx88[1]/0: registered device vbi1
[   25.720222] cx88[0]/2: cx2388x 8802 Driver Manager
[   25.720231] cx88-mpeg driver manager 0000:03:06.2: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   25.720239] cx88[0]/2: found at 0000:03:06.2, rev: 5, irq: 21, latency: 64, mmio: 0xfb000000
[   25.720256] cx88[1]/2: cx2388x 8802 Driver Manager
[   25.720262] cx88-mpeg driver manager 0000:03:07.2: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   25.720269] cx88[1]/2: found at 0000:03:07.2, rev: 5, irq: 22, latency: 64, mmio: 0xf7000000
[   25.720579] cx88_audio 0000:03:06.1: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   25.720596] cx88[0]/1: CX88x/0: ALSA support for cx2388x boards
[   25.720701] cx88_audio 0000:03:07.1: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   25.720716] cx88[1]/1: CX88x/1: ALSA support for cx2388x boards
[   25.733493] cx88/2: cx2388x dvb driver version 0.0.8 loaded
[   25.733496] cx88/2: registering cx8802 driver, type: dvb access: shared
[   25.733499] cx88[0]/2: subsystem: 0070:6906, board: Hauppauge WinTV-HVR4000(Lite) DVB-S/S2 [card=69]
[   25.733501] cx88[0]/2: cx2388x based DVB/ATSC card
[   25.733503] cx8802_alloc_frontends() allocating 1 frontend(s)
[   25.741685] DVB: registering new adapter (cx88[0])
[   25.741689] DVB: registering adapter 0 frontend 0 (Conexant CX24116/CX2411...
[   25.742995] cx88[1]/2: subsystem: 0070:6906, board: Hauppauge WinTV-HVR4000(Lite) DVB-S/S2 [card=69]
[   25.742998] cx88[1]/2: cx2388x based DVB/ATSC card
[   25.742999] cx8802_alloc_frontends() allocating 1 frontend(s)
[   25.744948] DVB: registering new adapter (cx88[1])
[   25.744950] DVB: registering adapter 1 frontend 0 (Conexant CX24116/CX2411...
[   25.800127] EXT3-fs (sda1): using internal journal
[   25.851160] SGI XFS with ACLs, security attributes, realtime, large block/inode numbers, no debug enabled
[   25.852148] SGI XFS Quota Management subsystem
[   25.856855] XFS mounting filesystem sdc1
[   25.971220] Ending clean XFS mount for filesystem: sdc1
[   26.002593] XFS mounting filesystem sdb1
[   26.151947] Ending clean XFS mount for filesystem: sdb1
[   26.216974] CIFS VFS: Error connecting to socket. Aborting operation
[   26.216980] CIFS VFS: cifs_mount failed w/return code = -101
[   26.221971] type=1400 audit(1313838297.660:10): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=901 comm="apparmor_parser"
[   26.222216] type=1400 audit(1313838297.660:11): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=902 comm="apparmor_parser"
[   26.236239] CIFS VFS: Error connecting to socket. Aborting operation
[   26.236243] CIFS VFS: cifs_mount failed w/return code = -101
[   26.266152] CIFS VFS: Error connecting to socket. Aborting operation
[   26.266157] CIFS VFS: cifs_mount failed w/return code = -101
[   26.267215] CIFS VFS: Error connecting to socket. Aborting operation
[   26.267219] CIFS VFS: cifs_mount failed w/return code = -101
[   26.341295] nvidia 0000:01:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   26.341304] nvidia 0000:01:00.0: setting latency timer to 64
[   26.341309] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=nonewns=io+mem
[   26.341441] NVRM: loading NVIDIA UNIX x86 Kernel Module  270.41.06  Mon Apr 18 14:54:25 PDT 2011





Hope this is data is useful in pointing to the problem.

---

### Post by b1acksun on 2011-08-24
dmesg with 2 cards
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.38-8-generic (buildd@vernadsky) (gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu3) ) #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 (Ubuntu 2.6.38-8.42-generic 2.6.38.2)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009ac00 (usable)
[    0.000000]  BIOS-e820: 000000000009ac00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e2000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000c7f90000 (usable)
[    0.000000]  BIOS-e820: 00000000c7f90000 - 00000000c7fa8000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000c7fa8000 - 00000000c7fd0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000c7fd0000 - 00000000c8000000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffa00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000138000000 (usable)
[    0.000000] Notice: NX (Execute Disable) protection cannot be enabled in hardware: non-PAE kernel!
[    0.000000] NX (Execute Disable) protection: approximated by x86 segment limits
[    0.000000] DMI present.
[    0.000000] DMI: System manufacturer System Product Name/M5A87, BIOS 0404    04/19/2011
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0xc7f90 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000000 mask FFFF80000000 write-back
[    0.000000]   1 base 000080000000 mask FFFFC0000000 write-back
[    0.000000]   2 base 0000C0000000 mask FFFFF8000000 write-back
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] TOM2: 0000000138000000 aka 4992M
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 00000000c8000000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] found SMP MP-table at [c00ff780] ff780
[    0.000000] initial memory mapped : 0 - 01c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 1bfb000-1c00000
[    0.000000] RAMDISK: 7f33b000 - 80000000
[    0.000000] Allocated new RAMDISK: 36b39000 - 377fd9b3
[    0.000000] Move RAMDISK from 000000007f33b000 - 000000007ffff9b2 to 36b39000 - 377fd9b2
[    0.000000] ACPI: RSDP 000fb850 00024 (v02 ACPIAM)
[    0.000000] ACPI: XSDT c7f90100 0004C (v01 041911 XSDT1732 20110419 MSFT 00000097)
[    0.000000] ACPI: FACP c7f90290 000F4 (v03 041911 FACP1732 20110419 MSFT 00000097)
[    0.000000] ACPI: DSDT c7f90460 0CCC6 (v01  A1866 A1866001 00000001 INTL 20060113)
[    0.000000] ACPI: FACS c7fa8000 00040
[    0.000000] ACPI: APIC c7f90390 0008C (v01 041911 APIC1732 20110419 MSFT 00000097)
[    0.000000] ACPI: MCFG c7f90420 0003C (v01 041911 OEMMCFG  20110419 MSFT 00000097)
[    0.000000] ACPI: OEMB c7fa8040 00072 (v01 041911 OEMB1732 20110419 MSFT 00000097)
[    0.000000] ACPI: HPET c7f9f8b0 00038 (v01 041911 OEMHPET  20110419 MSFT 00000097)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 2311MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x000c7f90
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009a
[    0.000000]     0: 0x00000100 -> 0x000c7f90
[    0.000000] On node 0 totalpages: 818970
[    0.000000] free_area_init_node: node 0, pgdat c1784100, node_mem_map f5238200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3946 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 4624 pages used for memmap
[    0.000000]   HighMem zone: 587138 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x84] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x85] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x86] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x87] disabled)
[    0.000000] ACPI: IOAPIC (id[0x03] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 3, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8300 base: 0xfed00000
[    0.000000] SMP: Allowing 8 CPUs, 5 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009a000 - 000000000009b000
[    0.000000] PM: Registered nosave memory: 000000000009b000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e2000
[    0.000000] PM: Registered nosave memory: 00000000000e2000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at c8000000 (gap: c8000000:37a00000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 13 pages/cpu @f4c00000 s28800 r0 d24448 u524288
[    0.000000] pcpu-alloc: s28800 r0 d24448 u524288 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 812570
[    0.000000] Kernel command line: file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash -- maybe-ubiquity
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] allocated 16381440 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:000c7f90)
[    0.000000] Memory: 3210552k/3276352k available (5188k kernel code, 65328k reserved, 2540k data, 700k init, 2367048k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc178d000 - 0xc183c000   ( 700 kB)
[    0.000000]       .data : 0xc15112a1 - 0xc178c480   (2540 kB)
[    0.000000]       .text : 0xc1000000 - 0xc15112a1   (5188 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU-based detection of stalled CPUs is disabled.
[    0.000000] NR_IRQS:2304 nr_irqs:744 16
[    0.000000] CPU 0 irqstacks, hard=f380a000 soft=f380c000
[    0.000000] Extended CMOS year: 2000
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2799.762 MHz processor.
[    0.004003] Calibrating delay loop (skipped), value calculated using timer frequency.. 5599.52 BogoMIPS (lpj=1119904
[    0.004008] pid_max: default: 32768 minimum: 301
[    0.004031] Security Framework initialized
[    0.004047] AppArmor: AppArmor initialized
[    0.004049] Yama: becoming mindful.
[    0.004104] Mount-cache hash table entries: 512
[    0.004222] Initializing cgroup subsys ns
[    0.004225] ns_cgroup deprecated: consider using the 'clone_children' flag without the ns_cgroup.
[    0.004229] Initializing cgroup subsys cpuacct
[    0.004233] Initializing cgroup subsys memory
[    0.004241] Initializing cgroup subsys devices
[    0.004244] Initializing cgroup subsys freezer
[    0.004246] Initializing cgroup subsys net_cls
[    0.004249] Initializing cgroup subsys blkio
[    0.004276] CPU: Physical Processor ID: 0
[    0.004278] CPU: Processor Core ID: 0
[    0.004281] mce: CPU supports 6 MCE banks
[    0.006259] ACPI: Core revision 20110112
[    0.012010] ftrace: allocating 23640 entries in 47 pages
[    0.016055] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.016311] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.059266] CPU0: AMD Phenom(tm) II X3 720 Processor stepping 02
[    0.060003] Performance Events: AMD PMU driver.
[    0.060003] ... version:                0
[    0.060003] ... bit width:              48
[    0.060003] ... generic registers:      4
[    0.060003] ... value mask:             0000ffffffffffff
[    0.060003] ... max period:             00007fffffffffff
[    0.060003] ... fixed-purpose events:   0
[    0.060003] ... event mask:             000000000000000f
[    0.060003] CPU 1 irqstacks, hard=f38ce000 soft=f38d8000
[    0.060003] Booting Node   0, Processors  #1
[    0.008000] Initializing CPU#1
[    0.148058] CPU 2 irqstacks, hard=f38e2000 soft=f38e4000
[    0.148060]  #2
[    0.008000] Initializing CPU#2
[    0.240019] Brought up 3 CPUs
[    0.240021] Total of 3 processors activated (16799.12 BogoMIPS).
[    0.241286] devtmpfs: initialized
[    0.241286] print_constraints: dummy: 
[    0.241286] Time: 11:14:08  Date: 08/20/11
[    0.241286] NET: Registered protocol family 16
[    0.241286] EISA bus registered
[    0.241286] node 0 link 0: io port [1000, ffffff]
[    0.241286] TOM: 00000000c8000000 aka 3200M
[    0.241286] Fam 10h mmconf [e0000000, efffffff]
[    0.241286] node 0 link 0: mmio [e0000000, efffffff] ==> none
[    0.241286] node 0 link 0: mmio [f0000000, ffffffff]
[    0.241286] node 0 link 0: mmio [a0000, bffff]
[    0.241286] node 0 link 0: mmio [c8000000, dfffffff]
[    0.241286] TOM2: 0000000138000000 aka 4992M
[    0.241286] bus: [00, 1f] on node 0 link 0
[    0.241286] bus: 00 index 0 [io  0x0000-0xffff]
[    0.241286] bus: 00 index 1 [mem 0xf0000000-0xffffffff]
[    0.241286] bus: 00 index 2 [mem 0x000a0000-0x000bffff]
[    0.241286] bus: 00 index 3 [mem 0xc8000000-0xdfffffff]
[    0.241286] Extended Config Space enabled on 1 nodes
[    0.241286] ACPI: bus type pci registered
[    0.241286] Trying to unpack rootfs image as initramfs...
[    0.241286] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.241286] PCI: not using MMCONFIG
[    0.241763] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=3
[    0.241765] PCI: Using configuration type 1 for base access
[    0.241766] PCI: Using configuration type 1 for extended access
[    0.242323] bio: create slab <bio-0> at 0
[    0.244987] ACPI: EC: Look up EC in DSDT
[    0.246126] ACPI: Executed 3 blocks of module-level executable AML code
[    2.274122] Freeing initrd memory: 13076k freed
[    2.352425] ACPI: Interpreter enabled
[    2.352430] ACPI: (supports S0 S1 S3 S4 S5)
[    2.352449] ACPI: Using IOAPIC for interrupt routing
[    2.352470] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    2.353040] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI motherboard resources
[    2.353042] PCI: Using MMCONFIG for extended config space
[    2.356421] ACPI: No dock devices found.
[    2.356423] HEST: Table not found.
[    2.356426] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    2.356558] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    2.356689] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7]
[    2.356691] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff]
[    2.356694] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff]
[    2.356696] pci_root PNP0A03:00: host bridge window [mem 0x000d0000-0x000dffff]
[    2.356698] pci_root PNP0A03:00: host bridge window [mem 0xc8000000-0xdfffffff]
[    2.356700] pci_root PNP0A03:00: host bridge window [mem 0xf0000000-0xfebfffff]
[    2.356712] pci 0000:00:00.0: [1002:5957] type 0 class 0x000600
[    2.356747] pci 0000:00:02.0: [1002:5978] type 1 class 0x000604
[    2.356770] pci 0000:00:02.0: PME# supported from D0 D3hot D3cold
[    2.356773] pci 0000:00:02.0: PME# disabled
[    2.356785] pci 0000:00:04.0: [1002:597a] type 1 class 0x000604
[    2.356807] pci 0000:00:04.0: PME# supported from D0 D3hot D3cold
[    2.356809] pci 0000:00:04.0: PME# disabled
[    2.356834] pci 0000:00:11.0: [1002:4391] type 0 class 0x000106
[    2.356849] pci 0000:00:11.0: reg 10: [io  0xc000-0xc007]
[    2.356857] pci 0000:00:11.0: reg 14: [io  0xb000-0xb003]
[    2.356864] pci 0000:00:11.0: reg 18: [io  0xa000-0xa007]
[    2.356871] pci 0000:00:11.0: reg 1c: [io  0x9000-0x9003]
[    2.356879] pci 0000:00:11.0: reg 20: [io  0x8000-0x800f]
[    2.356887] pci 0000:00:11.0: reg 24: [mem 0xf3fffc00-0xf3ffffff]
[    2.356921] pci 0000:00:12.0: [1002:4397] type 0 class 0x000c03
[    2.356931] pci 0000:00:12.0: reg 10: [mem 0xf3ffe000-0xf3ffefff]
[    2.356983] pci 0000:00:12.2: [1002:4396] type 0 class 0x000c03
[    2.356998] pci 0000:00:12.2: reg 10: [mem 0xf3fff800-0xf3fff8ff]
[    2.357049] pci 0000:00:12.2: supports D1 D2
[    2.357051] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
[    2.357054] pci 0000:00:12.2: PME# disabled
[    2.357070] pci 0000:00:13.0: [1002:4397] type 0 class 0x000c03
[    2.357080] pci 0000:00:13.0: reg 10: [mem 0xf3ffd000-0xf3ffdfff]
[    2.357132] pci 0000:00:13.2: [1002:4396] type 0 class 0x000c03
[    2.357146] pci 0000:00:13.2: reg 10: [mem 0xf3fff400-0xf3fff4ff]
[    2.357197] pci 0000:00:13.2: supports D1 D2
[    2.357199] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    2.357202] pci 0000:00:13.2: PME# disabled
[    2.357217] pci 0000:00:14.0: [1002:4385] type 0 class 0x000c05
[    2.357274] pci 0000:00:14.2: [1002:4383] type 0 class 0x000403
[    2.357290] pci 0000:00:14.2: reg 10: [mem 0xf3ff4000-0xf3ff7fff 64bit]
[    2.357333] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    2.357336] pci 0000:00:14.2: PME# disabled
[    2.357346] pci 0000:00:14.3: [1002:439d] type 0 class 0x000601
[    2.357401] pci 0000:00:14.4: [1002:4384] type 1 class 0x000604
[    2.357430] pci 0000:00:14.5: [1002:4399] type 0 class 0x000c03
[    2.357441] pci 0000:00:14.5: reg 10: [mem 0xf3ffc000-0xf3ffcfff]
[    2.357490] pci 0000:00:16.0: [1002:4397] type 0 class 0x000c03
[    2.357501] pci 0000:00:16.0: reg 10: [mem 0xf3ff3000-0xf3ff3fff]
[    2.357552] pci 0000:00:16.2: [1002:4396] type 0 class 0x000c03
[    2.357566] pci 0000:00:16.2: reg 10: [mem 0xf3fff000-0xf3fff0ff]
[    2.357618] pci 0000:00:16.2: supports D1 D2
[    2.357619] pci 0000:00:16.2: PME# supported from D0 D1 D2 D3hot
[    2.357623] pci 0000:00:16.2: PME# disabled
[    2.357637] pci 0000:00:18.0: [1022:1200] type 0 class 0x000600
[    2.357650] pci 0000:00:18.1: [1022:1201] type 0 class 0x000600
[    2.357661] pci 0000:00:18.2: [1022:1202] type 0 class 0x000600
[    2.357673] pci 0000:00:18.3: [1022:1203] type 0 class 0x000600
[    2.357686] pci 0000:00:18.4: [1022:1204] type 0 class 0x000600
[    2.357729] pci 0000:01:00.0: [10de:0a65] type 0 class 0x000300
[    2.357739] pci 0000:01:00.0: reg 10: [mem 0xf4000000-0xf4ffffff]
[    2.357749] pci 0000:01:00.0: reg 14: [mem 0xd0000000-0xdfffffff 64bit pref]
[    2.357759] pci 0000:01:00.0: reg 1c: [mem 0xce000000-0xcfffffff 64bit pref]
[    2.357766] pci 0000:01:00.0: reg 24: [io  0xdc00-0xdc7f]
[    2.357773] pci 0000:01:00.0: reg 30: [mem 0xf5e80000-0xf5efffff pref]
[    2.357812] pci 0000:01:00.1: [10de:0be3] type 0 class 0x000403
[    2.357822] pci 0000:01:00.1: reg 10: [mem 0xf5e7c000-0xf5e7ffff]
[    2.364166] pci 0000:00:02.0: PCI bridge to [bus 01-01]
[    2.364171] pci 0000:00:02.0:   bridge window [io  0xd000-0xdfff]
[    2.364174] pci 0000:00:02.0:   bridge window [mem 0xf4000000-0xf5efffff]
[    2.364178] pci 0000:00:02.0:   bridge window [mem 0xce000000-0xdfffffff 64bit pref]
[    2.364225] pci 0000:02:00.0: [1b21:1042] type 0 class 0x000c03
[    2.364243] pci 0000:02:00.0: reg 10: [mem 0xf5ff8000-0xf5ffffff 64bit]
[    2.364314] pci 0000:02:00.0: PME# supported from D3hot D3cold
[    2.364317] pci 0000:02:00.0: PME# disabled
[    2.372165] pci 0000:00:04.0: PCI bridge to [bus 02-02]
[    2.372169] pci 0000:00:04.0:   bridge window [io  0xf000-0x0000] (disabled)
[    2.372173] pci 0000:00:04.0:   bridge window [mem 0xf5f00000-0xf5ffffff]
[    2.372176] pci 0000:00:04.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    2.372212] pci 0000:03:05.0: [10ec:8169] type 0 class 0x000200
[    2.372231] pci 0000:03:05.0: reg 10: [io  0xe800-0xe8ff]
[    2.372241] pci 0000:03:05.0: reg 14: [mem 0xfebffc00-0xfebffcff]
[    2.372284] pci 0000:03:05.0: reg 30: [mem 0xfebc0000-0xfebdffff pref]
[    2.372305] pci 0000:03:05.0: supports D1 D2
[    2.372307] pci 0000:03:05.0: PME# supported from D1 D2 D3hot
[    2.372311] pci 0000:03:05.0: PME# disabled
[    2.372330] pci 0000:03:06.0: [14f1:8800] type 0 class 0x000400
[    2.372349] pci 0000:03:06.0: reg 10: [mem 0xfd000000-0xfdffffff]
[    2.372437] pci 0000:03:06.1: [14f1:8801] type 0 class 0x000480
[    2.372454] pci 0000:03:06.1: reg 10: [mem 0xfc000000-0xfcffffff]
[    2.372535] pci 0000:03:06.2: [14f1:8802] type 0 class 0x000480
[    2.372552] pci 0000:03:06.2: reg 10: [mem 0xfb000000-0xfbffffff]
[    2.372634] pci 0000:03:06.4: [14f1:8804] type 0 class 0x000480
[    2.372651] pci 0000:03:06.4: reg 10: [mem 0xfa000000-0xfaffffff]
[    2.372738] pci 0000:03:07.0: [14f1:8800] type 0 class 0x000400
[    2.372757] pci 0000:03:07.0: reg 10: [mem 0xf9000000-0xf9ffffff]
[    2.372845] pci 0000:03:07.1: [14f1:8801] type 0 class 0x000480
[    2.372862] pci 0000:03:07.1: reg 10: [mem 0xf8000000-0xf8ffffff]
[    2.372943] pci 0000:03:07.2: [14f1:8802] type 0 class 0x000480
[    2.372960] pci 0000:03:07.2: reg 10: [mem 0xf7000000-0xf7ffffff]
[    2.373042] pci 0000:03:07.4: [14f1:8804] type 0 class 0x000480
[    2.373059] pci 0000:03:07.4: reg 10: [mem 0xf6000000-0xf6ffffff]
[    2.373163] pci 0000:00:14.4: PCI bridge to [bus 03-03] (subtractive decode)
[    2.373167] pci 0000:00:14.4:   bridge window [io  0xe000-0xefff]
[    2.373170] pci 0000:00:14.4:   bridge window [mem 0xf6000000-0xfebfffff]
[    2.373174] pci 0000:00:14.4:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    2.373176] pci 0000:00:14.4:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    2.373178] pci 0000:00:14.4:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    2.373180] pci 0000:00:14.4:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    2.373182] pci 0000:00:14.4:   bridge window [mem 0x000d0000-0x000dffff] (subtractive decode)
[    2.373184] pci 0000:00:14.4:   bridge window [mem 0xc8000000-0xdfffffff] (subtractive decode)
[    2.373186] pci 0000:00:14.4:   bridge window [mem 0xf0000000-0xfebfffff] (subtractive decode)
[    2.373196] pci_bus 0000:00: on NUMA node 0
[    2.373200] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    2.373361] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE2._PRT]
[    2.373386] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE4._PRT]
[    2.373421] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0PC._PRT]
[    2.373552]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    2.373662]  pci0000:00: ACPI _OSC control (0x1d) granted
[    2.376983] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 14 15)
[    2.377029] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 7 9 10 11 14 15)
[    2.377076] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 *10 11 14 15)
[    2.377121] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 *9 10 11 14 15)
[    2.377156] ACPI: PCI Interrupt Link [LNKE] (IRQs *3 4 5 6 7 9 10 11 14 15)
[    2.377183] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 *7 9 10 11 14 15)
[    2.377210] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 *6 7 9 10 11 14 15)
[    2.377237] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 11 14 15) *0
[    2.377311] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    2.377316] vgaarb: loaded
[    2.377451] SCSI subsystem initialized
[    2.377468] libata version 3.00 loaded.
[    2.377468] usbcore: registered new interface driver usbfs
[    2.377468] usbcore: registered new interface driver hub
[    2.377468] usbcore: registered new device driver usb
[    2.377468] wmi: Mapper loaded
[    2.377468] PCI: Using ACPI for IRQ routing
[    2.377468] PCI: pci_cache_line_size set to 64 bytes
[    2.377468] reserve RAM buffer: 000000000009ac00 - 000000000009ffff 
[    2.377468] reserve RAM buffer: 00000000c7f90000 - 00000000c7ffffff 
[    2.377468] NetLabel: Initializing
[    2.377468] NetLabel:  domain hash size = 128
[    2.377468] NetLabel:  protocols = UNLABELED CIPSOv4
[    2.377468] NetLabel:  unlabeled traffic allowed by default
[    2.377468] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    2.377468] hpet0: 3 comparators, 32-bit 14.318180 MHz counter
[    2.378478] Switching to clocksource hpet
[    2.378499] Switched to NOHz mode on CPU #0
[    2.378487] Switched to NOHz mode on CPU #2
[    2.378481] Switched to NOHz mode on CPU #1
[    2.380996] AppArmor: AppArmor Filesystem Enabled
[    2.381011] pnp: PnP ACPI init
[    2.381021] ACPI: bus type pnp registered
[    2.381098] pnp 00:00: [bus 00-ff]
[    2.381100] pnp 00:00: [io  0x0cf8-0x0cff]
[    2.381102] pnp 00:00: [io  0x0000-0x0cf7 window]
[    2.381104] pnp 00:00: [io  0x0d00-0xffff window]
[    2.381106] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    2.381108] pnp 00:00: [mem 0x000d0000-0x000dffff window]
[    2.381110] pnp 00:00: [mem 0xc8000000-0xdfffffff window]
[    2.381112] pnp 00:00: [mem 0xf0000000-0xfebfffff window]
[    2.381143] pnp 00:00: Plug and Play ACPI device, IDs PNP0a03 (active)
[    2.381177] pnp 00:01: [dma 4]
[    2.381179] pnp 00:01: [io  0x0000-0x000f]
[    2.381181] pnp 00:01: [io  0x0081-0x0083]
[    2.381182] pnp 00:01: [io  0x0087]
[    2.381184] pnp 00:01: [io  0x0089-0x008b]
[    2.381185] pnp 00:01: [io  0x008f]
[    2.381187] pnp 00:01: [io  0x00c0-0x00df]
[    2.381209] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
[    2.381216] pnp 00:02: [io  0x0070-0x0071]
[    2.381224] pnp 00:02: [irq 8]
[    2.381246] pnp 00:02: Plug and Play ACPI device, IDs PNP0b00 (active)
[    2.381252] pnp 00:03: [io  0x0061]
[    2.381273] pnp 00:03: Plug and Play ACPI device, IDs PNP0800 (active)
[    2.381279] pnp 00:04: [io  0x00f0-0x00ff]
[    2.381282] pnp 00:04: [irq 13]
[    2.381305] pnp 00:04: Plug and Play ACPI device, IDs PNP0c04 (active)
[    2.381417] pnp 00:05: [io  0x0000-0xffffffff disabled]
[    2.381419] pnp 00:05: [io  0x0000-0xffffffff disabled]
[    2.381421] pnp 00:05: [io  0x0290-0x029f]
[    2.381462] system 00:05: [io  0x0290-0x029f] has been reserved
[    2.381464] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
[    2.381491] pnp 00:06: [mem 0xfed00000-0xfed003ff]
[    2.381514] pnp 00:06: Plug and Play ACPI device, IDs PNP0103 (active)
[    2.381696] pnp 00:07: [io  0x03f8-0x03ff]
[    2.381699] pnp 00:07: [irq 4]
[    2.381701] pnp 00:07: [dma 0 disabled]
[    2.381766] pnp 00:07: Plug and Play ACPI device, IDs PNP0501 (active)
[    2.381819] pnp 00:08: [io  0x0060]
[    2.381820] pnp 00:08: [io  0x0064]
[    2.381822] pnp 00:08: [mem 0xfec00000-0xfec00fff]
[    2.381824] pnp 00:08: [mem 0xfee00000-0xfee00fff]
[    2.381865] system 00:08: [mem 0xfec00000-0xfec00fff] could not be reserved
[    2.381868] system 00:08: [mem 0xfee00000-0xfee00fff] has been reserved
[    2.381870] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    2.381974] pnp 00:09: [io  0x0010-0x001f]
[    2.381977] pnp 00:09: [io  0x0022-0x003f]
[    2.381979] pnp 00:09: [io  0x0062-0x0063]
[    2.381980] pnp 00:09: [io  0x0065-0x006f]
[    2.381982] pnp 00:09: [io  0x0072-0x007f]
[    2.381983] pnp 00:09: [io  0x0080]
[    2.381985] pnp 00:09: [io  0x0084-0x0086]
[    2.381986] pnp 00:09: [io  0x0088]
[    2.381988] pnp 00:09: [io  0x008c-0x008e]
[    2.381989] pnp 00:09: [io  0x0090-0x009f]
[    2.381991] pnp 00:09: [io  0x00a2-0x00bf]
[    2.381992] pnp 00:09: [io  0x00b1]
[    2.381994] pnp 00:09: [io  0x00e0-0x00ef]
[    2.381995] pnp 00:09: [io  0x04d0-0x04d1]
[    2.381997] pnp 00:09: [io  0x040b]
[    2.381998] pnp 00:09: [io  0x04d6]
[    2.382000] pnp 00:09: [io  0x0c00-0x0c01]
[    2.382001] pnp 00:09: [io  0x0c14]
[    2.382003] pnp 00:09: [io  0x0c50-0x0c51]
[    2.382004] pnp 00:09: [io  0x0c52]
[    2.382006] pnp 00:09: [io  0x0c6c]
[    2.382007] pnp 00:09: [io  0x0c6f]
[    2.382008] pnp 00:09: [io  0x0cd0-0x0cd1]
[    2.382010] pnp 00:09: [io  0x0cd2-0x0cd3]
[    2.382012] pnp 00:09: [io  0x0cd4-0x0cd5]
[    2.382013] pnp 00:09: [io  0x0cd6-0x0cd7]
[    2.382015] pnp 00:09: [io  0x0cd8-0x0cdf]
[    2.382016] pnp 00:09: [io  0x0b00-0x0b3f]
[    2.382018] pnp 00:09: [io  0x0800-0x089f]
[    2.382019] pnp 00:09: [io  0x0000-0xffffffff disabled]
[    2.382021] pnp 00:09: [io  0x0b00-0x0b1f]
[    2.382022] pnp 00:09: [io  0x0b20-0x0b3f]
[    2.382024] pnp 00:09: [io  0x0900-0x090f]
[    2.382026] pnp 00:09: [io  0x0910-0x091f]
[    2.382027] pnp 00:09: [io  0xfe00-0xfefe]
[    2.382029] pnp 00:09: [io  0x0060]
[    2.382030] pnp 00:09: [io  0x0064]
[    2.382032] pnp 00:09: [mem 0x00000000-0xffffffff disabled]
[    2.382034] pnp 00:09: [mem 0xffb80000-0xffbfffff]
[    2.382035] pnp 00:09: [mem 0xfec10000-0xfec1001f]
[    2.382037] pnp 00:09: [mem 0xfed40000-0xfed44fff]
[    2.382039] pnp 00:09: [mem 0xfed80000-0xfed80fff]
[    2.382040] pnp 00:09: [mem 0x00000000-0xffffffff disabled]
[    2.382118] system 00:09: [io  0x04d0-0x04d1] has been reserved
[    2.382120] system 00:09: [io  0x040b] has been reserved
[    2.382122] system 00:09: [io  0x04d6] has been reserved
[    2.382124] system 00:09: [io  0x0c00-0x0c01] has been reserved
[    2.382126] system 00:09: [io  0x0c14] has been reserved
[    2.382128] system 00:09: [io  0x0c50-0x0c51] has been reserved
[    2.382130] system 00:09: [io  0x0c52] has been reserved
[    2.382132] system 00:09: [io  0x0c6c] has been reserved
[    2.382134] system 00:09: [io  0x0c6f] has been reserved
[    2.382136] system 00:09: [io  0x0cd0-0x0cd1] has been reserved
[    2.382138] system 00:09: [io  0x0cd2-0x0cd3] has been reserved
[    2.382140] system 00:09: [io  0x0cd4-0x0cd5] has been reserved
[    2.382143] system 00:09: [io  0x0cd6-0x0cd7] has been reserved
[    2.382145] system 00:09: [io  0x0cd8-0x0cdf] has been reserved
[    2.382147] system 00:09: [io  0x0b00-0x0b3f] has been reserved
[    2.382149] system 00:09: [io  0x0800-0x089f] has been reserved
[    2.382151] system 00:09: [io  0x0b00-0x0b1f] has been reserved
[    2.382153] system 00:09: [io  0x0b20-0x0b3f] has been reserved
[    2.382155] system 00:09: [io  0x0900-0x090f] has been reserved
[    2.382158] system 00:09: [io  0x0910-0x091f] has been reserved
[    2.382160] system 00:09: [io  0xfe00-0xfefe] has been reserved
[    2.382163] system 00:09: [mem 0xffb80000-0xffbfffff] has been reserved
[    2.382165] system 00:09: [mem 0xfec10000-0xfec1001f] has been reserved
[    2.382167] system 00:09: [mem 0xfed40000-0xfed44fff] has been reserved
[    2.382170] system 00:09: [mem 0xfed80000-0xfed80fff] has been reserved
[    2.382172] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    2.382195] pnp 00:0a: [mem 0xe0000000-0xefffffff]
[    2.382234] system 00:0a: [mem 0xe0000000-0xefffffff] has been reserved
[    2.382236] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
[    2.382310] pnp 00:0b: [mem 0x00000000-0x0009ffff]
[    2.382312] pnp 00:0b: [mem 0x000c0000-0x000cffff]
[    2.382313] pnp 00:0b: [mem 0x000e0000-0x000fffff]
[    2.382315] pnp 00:0b: [mem 0x00100000-0xc7ffffff]
[    2.382317] pnp 00:0b: [mem 0xfec00000-0xffffffff]
[    2.382358] system 00:0b: [mem 0x00000000-0x0009ffff] could not be reserved
[    2.382360] system 00:0b: [mem 0x000c0000-0x000cffff] could not be reserved
[    2.382363] system 00:0b: [mem 0x000e0000-0x000fffff] could not be reserved
[    2.382365] system 00:0b: [mem 0x00100000-0xc7ffffff] could not be reserved
[    2.382367] system 00:0b: [mem 0xfec00000-0xffffffff] could not be reserved
[    2.382370] system 00:0b: Plug and Play ACPI device, IDs PNP0c01 (active)
[    2.382438] pnp: PnP ACPI: found 12 devices
[    2.382439] ACPI: ACPI bus type pnp unregistered
[    2.382442] PnPBIOS: Disabled by ACPI PNP
[    2.418164] pci 0000:00:02.0: PCI bridge to [bus 01-01]
[    2.418167] pci 0000:00:02.0:   bridge window [io  0xd000-0xdfff]
[    2.418170] pci 0000:00:02.0:   bridge window [mem 0xf4000000-0xf5efffff]
[    2.418172] pci 0000:00:02.0:   bridge window [mem 0xce000000-0xdfffffff 64bit pref]
[    2.418176] pci 0000:00:04.0: PCI bridge to [bus 02-02]
[    2.418177] pci 0000:00:04.0:   bridge window [io  disabled]
[    2.418180] pci 0000:00:04.0:   bridge window [mem 0xf5f00000-0xf5ffffff]
[    2.418182] pci 0000:00:04.0:   bridge window [mem pref disabled]
[    2.418186] pci 0000:00:14.4: PCI bridge to [bus 03-03]
[    2.418189] pci 0000:00:14.4:   bridge window [io  0xe000-0xefff]
[    2.418193] pci 0000:00:14.4:   bridge window [mem 0xf6000000-0xfebfffff]
[    2.418196] pci 0000:00:14.4:   bridge window [mem pref disabled]
[    2.418209] pci 0000:00:02.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    2.418212] pci 0000:00:02.0: setting latency timer to 64
[    2.418218] pci 0000:00:04.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.418221] pci 0000:00:04.0: setting latency timer to 64
[    2.418227] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    2.418230] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    2.418232] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    2.418234] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
[    2.418236] pci_bus 0000:00: resource 8 [mem 0xc8000000-0xdfffffff]
[    2.418238] pci_bus 0000:00: resource 9 [mem 0xf0000000-0xfebfffff]
[    2.418240] pci_bus 0000:01: resource 0 [io  0xd000-0xdfff]
[    2.418242] pci_bus 0000:01: resource 1 [mem 0xf4000000-0xf5efffff]
[    2.418244] pci_bus 0000:01: resource 2 [mem 0xce000000-0xdfffffff 64bit pref]
[    2.418246] pci_bus 0000:02: resource 1 [mem 0xf5f00000-0xf5ffffff]
[    2.418248] pci_bus 0000:03: resource 0 [io  0xe000-0xefff]
[    2.418250] pci_bus 0000:03: resource 1 [mem 0xf6000000-0xfebfffff]
[    2.418252] pci_bus 0000:03: resource 4 [io  0x0000-0x0cf7]
[    2.418254] pci_bus 0000:03: resource 5 [io  0x0d00-0xffff]
[    2.418256] pci_bus 0000:03: resource 6 [mem 0x000a0000-0x000bffff]
[    2.418258] pci_bus 0000:03: resource 7 [mem 0x000d0000-0x000dffff]
[    2.418260] pci_bus 0000:03: resource 8 [mem 0xc8000000-0xdfffffff]
[    2.418262] pci_bus 0000:03: resource 9 [mem 0xf0000000-0xfebfffff]
[    2.418288] NET: Registered protocol family 2
[    2.418341] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    2.418512] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    2.418978] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    2.419213] TCP: Hash tables configured (established 131072 bind 65536)
[    2.419215] TCP reno registered
[    2.419217] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    2.419226] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    2.419301] NET: Registered protocol family 1
[    3.272053] pci 0000:01:00.0: Boot video device
[    3.272094] PCI: CLS 64 bytes, default 64
[    3.272294] cpufreq-nforce2: No nForce2 chipset.
[    3.272381] audit: initializing netlink socket (disabled)
[    3.272387] type=2000 audit(1313838851.268:1): initialized
[    3.279908] highmem bounce pool size: 64 pages
[    3.279912] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    3.281174] VFS: Disk quotas dquot_6.5.2
[    3.281217] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    3.281734] fuse init (API version 7.16)
[    3.281797] msgmni has been set to 1673
[    3.282007] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    3.282033] io scheduler noop registered
[    3.282034] io scheduler deadline registered
[    3.282047] io scheduler cfq registered (default)
[    3.282128] pcieport 0000:00:02.0: setting latency timer to 64
[    3.282154] pcieport 0000:00:02.0: irq 40 for MSI/MSI-X
[    3.282198] pcieport 0000:00:04.0: setting latency timer to 64
[    3.282217] pcieport 0000:00:04.0: irq 41 for MSI/MSI-X
[    3.282277] pcieport 0000:00:02.0: Signaling PME through PCIe PME interrupt
[    3.282279] pci 0000:01:00.0: Signaling PME through PCIe PME interrupt
[    3.282281] pci 0000:01:00.1: Signaling PME through PCIe PME interrupt
[    3.282283] pcie_pme 0000:00:02.0cie01: service driver pcie_pme loaded
[    3.282292] pcieport 0000:00:04.0: Signaling PME through PCIe PME interrupt
[    3.282294] pci 0000:02:00.0: Signaling PME through PCIe PME interrupt
[    3.282296] pcie_pme 0000:00:04.0cie01: service driver pcie_pme loaded
[    3.282310] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    3.282328] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    3.282431] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    3.282435] ACPI: Power Button [PWRB]
[    3.282469] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    3.282472] ACPI: Power Button [PWRF]
[    3.282580] ACPI: acpi_idle registered with cpuidle
[    3.283897] ERST: Table is not found!
[    3.283946] isapnp: Scanning for PnP cards...
[    3.283950] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    3.304311] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    3.637546] isapnp: No Plug & Play device found
[    3.712458] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    3.712674] Linux agpgart interface v0.103
[    3.713700] brd: module loaded
[    3.714087] loop: module loaded
[    3.714147] i2c-core: driver [adp5520] using legacy suspend method
[    3.714148] i2c-core: driver [adp5520] using legacy resume method
[    3.714443] Fixed MDIO Bus: probed
[    3.714469] PPP generic driver version 2.4.2
[    3.714494] tun: Universal TUN/TAP device driver, 1.6
[    3.714495] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    3.714549] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    3.714565] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    3.714575] ehci_hcd 0000:00:12.2: EHCI Host Controller
[    3.714599] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
[    3.716045] ehci_hcd 0000:00:12.2: QUIRK: Enable exception for AMD Hudson ASPM
[    3.716049] ehci_hcd 0000:00:12.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    3.716068] ehci_hcd 0000:00:12.2: debug port 1
[    3.716086] ehci_hcd 0000:00:12.2: irq 17, io mem 0xf3fff800
[    3.728024] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    3.728127] hub 1-0:1.0: USB hub found
[    3.728130] hub 1-0:1.0: 5 ports detected
[    3.728188] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    3.728200] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    3.728229] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
[    3.728266] ehci_hcd 0000:00:13.2: QUIRK: Enable exception for AMD Hudson ASPM
[    3.728270] ehci_hcd 0000:00:13.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    3.728287] ehci_hcd 0000:00:13.2: debug port 1
[    3.728298] ehci_hcd 0000:00:13.2: irq 17, io mem 0xf3fff400
[    3.740025] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    3.740119] hub 2-0:1.0: USB hub found
[    3.740122] hub 2-0:1.0: 5 ports detected
[    3.740180] ehci_hcd 0000:00:16.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    3.740190] ehci_hcd 0000:00:16.2: EHCI Host Controller
[    3.740219] ehci_hcd 0000:00:16.2: new USB bus registered, assigned bus number 3
[    3.744046] ehci_hcd 0000:00:16.2: QUIRK: Enable exception for AMD Hudson ASPM
[    3.744050] ehci_hcd 0000:00:16.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    3.744066] ehci_hcd 0000:00:16.2: debug port 1
[    3.744077] ehci_hcd 0000:00:16.2: irq 17, io mem 0xf3fff000
[    3.756025] ehci_hcd 0000:00:16.2: USB 2.0 started, EHCI 1.00
[    3.756112] hub 3-0:1.0: USB hub found
[    3.756115] hub 3-0:1.0: 4 ports detected
[    3.756172] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    3.756183] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    3.756193] ohci_hcd 0000:00:12.0: OHCI Host Controller
[    3.756221] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 4
[    3.756270] ohci_hcd 0000:00:12.0: irq 18, io mem 0xf3ffe000
[    3.816093] hub 4-0:1.0: USB hub found
[    3.816098] hub 4-0:1.0: 5 ports detected
[    3.816157] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    3.816166] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    3.816191] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5
[    3.820054] ohci_hcd 0000:00:13.0: irq 18, io mem 0xf3ffd000
[    3.880095] hub 5-0:1.0: USB hub found
[    3.880100] hub 5-0:1.0: 5 ports detected
[    3.880159] ohci_hcd 0000:00:14.5: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    3.880169] ohci_hcd 0000:00:14.5: OHCI Host Controller
[    3.880196] ohci_hcd 0000:00:14.5: new USB bus registered, assigned bus number 6
[    3.880238] ohci_hcd 0000:00:14.5: irq 18, io mem 0xf3ffc000
[    3.940109] hub 6-0:1.0: USB hub found
[    3.940114] hub 6-0:1.0: 2 ports detected
[    3.940172] ohci_hcd 0000:00:16.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    3.940182] ohci_hcd 0000:00:16.0: OHCI Host Controller
[    3.940207] ohci_hcd 0000:00:16.0: new USB bus registered, assigned bus number 7
[    3.940245] ohci_hcd 0000:00:16.0: irq 18, io mem 0xf3ff3000
[    4.000095] hub 7-0:1.0: USB hub found
[    4.000100] hub 7-0:1.0: 4 ports detected
[    4.000157] uhci_hcd: USB Universal Host Controller Interface driver
[    4.000210] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    4.002979] serio: i8042 KBD port at 0x60,0x64 irq 1
[    4.002985] serio: i8042 AUX port at 0x60,0x64 irq 12
[    4.003043] mousedev: PS/2 mouse device common for all mice
[    4.003120] rtc_cmos 00:02: RTC can wake from S4
[    4.003214] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    4.003234] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    4.003298] device-mapper: uevent: version 1.0.3
[    4.003359] device-mapper: ioctl: 4.19.1-ioctl (2011-01-07) initialised
[    4.003432] device-mapper: multipath: version 1.2.0 loaded
[    4.003434] device-mapper: multipath round-robin: version 1.0.0 loaded
[    4.003489] EISA: Probing bus 0 at eisa.0
[    4.003491] EISA: Cannot allocate resource for mainboard
[    4.003492] Cannot allocate resource for EISA slot 1
[    4.003493] Cannot allocate resource for EISA slot 2
[    4.003495] Cannot allocate resource for EISA slot 3
[    4.003496] Cannot allocate resource for EISA slot 4
[    4.003498] Cannot allocate resource for EISA slot 5
[    4.003499] Cannot allocate resource for EISA slot 6
[    4.003500] Cannot allocate resource for EISA slot 7
[    4.003501] Cannot allocate resource for EISA slot 8
[    4.003503] EISA: Detected 0 cards.
[    4.003555] cpuidle: using governor ladder
[    4.003556] cpuidle: using governor menu
[    4.003745] TCP cubic registered
[    4.003834] NET: Registered protocol family 10
[    4.004276] NET: Registered protocol family 17
[    4.004287] Registering the dns_resolver key type
[    4.004305] powernow-k8: Found 1 AMD Phenom(tm) II X3 720 Processor (3 cpu cores) (version 2.20.00)
[    4.004310] [Firmware Bug]: powernow-k8: No compatible ACPI _PSS objects found.
[    4.004310] [Firmware Bug]: powernow-k8: Try again with latest BIOS.
[    4.004331] Using IPI No-Shortcut mode
[    4.004391] PM: Hibernation image not present or could not be loaded.
[    4.004397] registered taskstats version 1
[    4.004642]   Magic number: 7:847:226
[    4.004693] rtc_cmos 00:02: setting system clock to 2011-08-20 11:14:12 UTC (1313838852)
[    4.004696] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    4.004697] EDD information not available.
[    4.004763] Freeing unused kernel memory: 700k freed
[    4.004963] Write protecting the kernel text: 5192k
[    4.004995] Write protecting the kernel read-only data: 2148k
[    4.024105] <30>udev[72]: starting version 167
[    4.083552] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    4.083575] r8169 0000:03:05.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    4.083597] r8169 0000:03:05.0: (unregistered net_device): no PCI Express capability
[    4.084074] r8169 0000:03:05.0: eth0: RTL8169sb/8110sb at 0xf8020c00, 00:0c:76:a0:02:d9, XID 10000000 IRQ 20
[    4.094578] [drm] Initialized drm 1.1.0 20060810
[    4.095461] ahci 0000:00:11.0: version 3.0
[    4.095475] ahci 0000:00:11.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    4.095570] ahci 0000:00:11.0: AHCI 0001.0200 32 slots 6 ports 6 Gbps 0x3f impl SATA mode
[    4.095573] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part 
[    4.100266] scsi0 : ahci
[    4.105976] scsi1 : ahci
[    4.106296] scsi2 : ahci
[    4.106374] scsi3 : ahci
[    4.106431] scsi4 : ahci
[    4.106489] scsi5 : ahci
[    4.106535] ata1: SATA max UDMA/133 abar m1024@0xf3fffc00 port 0xf3fffd00 irq 19
[    4.106538] ata2: SATA max UDMA/133 abar m1024@0xf3fffc00 port 0xf3fffd80 irq 19
[    4.106541] ata3: SATA max UDMA/133 irq_stat 0x00000040, connection status changed irq 19
[    4.106544] ata4: SATA max UDMA/133 abar m1024@0xf3fffc00 port 0xf3fffe80 irq 19
[    4.106547] ata5: SATA max UDMA/133 abar m1024@0xf3fffc00 port 0xf3ffff00 irq 19
[    4.106549] ata6: SATA max UDMA/133 abar m1024@0xf3fffc00 port 0xf3ffff80 irq 19
[    4.120159] nouveau 0000:01:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    4.120163] nouveau 0000:01:00.0: setting latency timer to 64
[    4.122103] [drm] nouveau 0000:01:00.0: Detected an NV50 generation card (0x0a8280a2)
[    4.124970] [drm] nouveau 0000:01:00.0: Attempting to load BIOS image from PRAMIN
[    4.198209] [drm] nouveau 0000:01:00.0: ... appears to be valid
[    4.198212] [drm] nouveau 0000:01:00.0: BIT BIOS found
[    4.198214] [drm] nouveau 0000:01:00.0: Bios version 70.18.2d.00
[    4.198216] [drm] nouveau 0000:01:00.0: Pointer to BIT loadval table invalid
[    4.198218] [drm] nouveau 0000:01:00.0: TMDS table version 2.0
[    4.198220] [drm] nouveau 0000:01:00.0: Found Display Configuration Block version 4.0
[    4.198222] [drm] nouveau 0000:01:00.0: Raw DCB entry 0: 02000300 00000000
[    4.198225] [drm] nouveau 0000:01:00.0: Raw DCB entry 1: 01000302 00020030
[    4.198226] [drm] nouveau 0000:01:00.0: Raw DCB entry 2: 02011362 00020010
[    4.198228] [drm] nouveau 0000:01:00.0: Raw DCB entry 3: 01022310 00000000
[    4.198230] [drm] nouveau 0000:01:00.0: Raw DCB entry 4: 0000000e 00000000
[    4.198232] [drm] nouveau 0000:01:00.0: DCB connector table: VHER 0x40 5 16 4
[    4.198234] [drm] nouveau 0000:01:00.0:   0: 0x00001030: type 0x30 idx 0 tag 0x07
[    4.198237] [drm] nouveau 0000:01:00.0:   1: 0x00002161: type 0x61 idx 1 tag 0x08
[    4.198239] [drm] nouveau 0000:01:00.0:   2: 0x00000200: type 0x00 idx 2 tag 0xff
[    4.198242] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 0 at offset 0xD0E7
[    4.216031] usb 5-2: new low speed USB device using ohci_hcd and address 2
[    4.240030] [drm] nouveau 0000:01:00.0: 0xD43D: Condition still not met after 20ms, skipping following opcodes
[    4.264024] [drm] nouveau 0000:01:00.0: 0xD441: Condition still not met after 20ms, skipping following opcodes
[    4.264046] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 1 at offset 0xD66C
[    4.272026] Refined TSC clocksource calibration: 2799.887 MHz.
[    4.272030] Switching to clocksource tsc
[    4.288018] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 2 at offset 0xE13E
[    4.288026] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 3 at offset 0xE173
[    4.337488] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 4 at offset 0xE326
[    4.337490] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table at offset 0xE38B
[    4.360029] [drm] nouveau 0000:01:00.0: 0xE38B: Condition still not met after 20ms, skipping following opcodes
[    4.444042] ata5: SATA link down (SStatus 0 SControl 300)
[    4.444100] ata4: SATA link down (SStatus 0 SControl 300)
[    4.592035] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    4.592059] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    4.616058] ata6: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    4.616683] ata6.00: ATAPI: TSSTcorp CDDVDW SH-S223C, SB02, max UDMA/100
[    4.618053] ata6.00: configured for UDMA/100
[    4.632304] ata2.00: ATA-7: ST3750640AS, 3.AAE, max UDMA/133
[    4.632306] ata2.00: 1465149168 sectors, multi 0: LBA48 NCQ (depth 31/32)
[    4.634088] ata1.00: ATA-7: ST3500630AS, 3.AAK, max UDMA/133
[    4.634091] ata1.00: 976773168 sectors, multi 0: LBA48 NCQ (depth 31/32)
[    4.690611] ata2.00: configured for UDMA/133
[    4.692021] usb 5-3: new low speed USB device using ohci_hcd and address 3
[    4.692389] ata1.00: configured for UDMA/133
[    4.692490] scsi 0:0:0:0: Direct-Access     ATA      ST3500630AS      3.AA PQ: 0 ANSI: 5
[    4.692614] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    4.692650] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    4.692723] scsi 1:0:0:0: Direct-Access     ATA      ST3750640AS      3.AA PQ: 0 ANSI: 5
[    4.692739] sd 0:0:0:0: [sda] Write Protect is off
[    4.692742] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.692755] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.692851] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    4.692913] sd 1:0:0:0: [sdb] 1465149168 512-byte logical blocks: (750 GB/698 GiB)
[    4.692952] sd 1:0:0:0: [sdb] Write Protect is off
[    4.692954] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    4.692970] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.730296]  sdb: sdb1
[    4.730490] sd 1:0:0:0: [sdb] Attached SCSI disk
[    4.748806]  sda: sda1 sda2
[    4.749015] sd 0:0:0:0: [sda] Attached SCSI disk
[    4.841103] [drm] nouveau 0000:01:00.0: 3 available performance level(s)
[    4.841106] [drm] nouveau 0000:01:00.0: 0: memory 135MHz core 135MHz shader 270MHz voltage 850mV
[    4.841109] [drm] nouveau 0000:01:00.0: 1: memory 324MHz core 405MHz shader 810MHz voltage 900mV
[    4.841112] [drm] nouveau 0000:01:00.0: 3: memory 400MHz core 589MHz shader 1402MHz voltage 1000mV
[    4.841124] [drm] nouveau 0000:01:00.0: c: memory 950MHz core 550MHz shader 1400MHz voltage 900mV
[    4.841202] [TTM] Zone  kernel: Available graphics memory: 428640 kiB.
[    4.841204] [TTM] Zone highmem: Available graphics memory: 1612164 kiB.
[    4.841206] [TTM] Initializing pool allocator.
[    4.841218] [drm] nouveau 0000:01:00.0: Detected 512MiB VRAM
[    4.850669] [drm] nouveau 0000:01:00.0: 512 MiB GART (aperture)
[    4.864280] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    4.864281] [drm] No driver support for vblank timestamp query.
[    4.936087] input:   SCISSORS Keyboard as /devices/pci0000:00/0000:00:13.0/usb5/5-2/5-2:1.0/input/input2
[    4.936155] generic-usb 0003:0DC6:3401.0001: input,hidraw0: USB HID v1.00 Keyboard [  SCISSORS Keyboard] on usb-0000:00:13.0-2/input0
[    4.941226] input: USB Optical Mouse as /devices/pci0000:00/0000:00:13.0/usb5/5-3/5-3:1.0/input/input3
[    4.941342] generic-usb 0003:1BCF:0007.0002: input,hiddev0,hidraw1: USB HID v1.10 Mouse [USB Optical Mouse] on usb-0000:00:13.0-3/input0
[    4.941353] usbcore: registered new interface driver usbhid
[    4.941354] usbhid: USB HID core driver
[    5.000029] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    5.000985] ata3.00: ATA-8: Hitachi HDS721010CLA332, JP4OA39C, max UDMA/133
[    5.000988] ata3.00: 1953525168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
[    5.002049] ata3.00: configured for UDMA/133
[    5.002156] scsi 2:0:0:0: Direct-Access     ATA      Hitachi HDS72101 JP4O PQ: 0 ANSI: 5
[    5.002282] sd 2:0:0:0: Attached scsi generic sg2 type 0
[    5.002373] sd 2:0:0:0: [sdc] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    5.002437] sd 2:0:0:0: [sdc] Write Protect is off
[    5.002439] sd 2:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    5.002464] sd 2:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.003719] scsi 5:0:0:0: CD-ROM            TSSTcorp CDDVDW SH-S223C  SB02 PQ: 0 ANSI: 5
[    5.004357] sr0: scsi3-mmc drive: 32x/40x writer dvd-ram cd/rw xa/form2 cdda tray
[    5.004359] cdrom: Uniform CD-ROM driver Revision: 3.20
[    5.004438] sr 5:0:0:0: Attached scsi CD-ROM sr0
[    5.004490] sr 5:0:0:0: Attached scsi generic sg3 type 5
[    5.027652] [drm] nouveau 0000:01:00.0: allocated 1280x1024 fb: 0x60000000, bo f3049400
[    5.030611] Console: switching to colour frame buffer device 160x64
[    5.032586] Alternate GPT is invalid, using primary GPT.
[    5.032600]  sdc: sdc1
[    5.032643] fb0: nouveaufb frame buffer device
[    5.032645] drm: registered panic notifier
[    5.032650] [drm] Initialized nouveau 0.0.16 20090420 for 0000:01:00.0 on minor 0
[    5.032797] sd 2:0:0:0: [sdc] Attached SCSI disk
[    5.977085] Btrfs loaded
[    5.981136] xor: automatically using best checksumming function: pIII_sse
[    6.000013]    pIII_sse  : 11256.000 MB/sec
[    6.000015] xor: using function: pIII_sse (11256.000 MB/sec)
[    6.001983] device-mapper: dm-raid45: initialized v0.2594b
[    6.090357] EXT3-fs: barriers not enabled
[    6.104165] kjournald starting.  Commit interval 5 seconds
[    6.104294] EXT3-fs (sda1): mounted filesystem with ordered data mode
[    6.870236] sr 5:0:0:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[    6.870240] sr 5:0:0:0: [sr0]  Sense Key : Illegal Request [current] 
[    6.870244] sr 5:0:0:0: [sr0]  Add. Sense: Illegal mode for this track
[    6.870248] sr 5:0:0:0: [sr0] CDB: Read(10): 28 00 00 05 5a 96 00 00 01 00
[    6.870254] end_request: I/O error, dev sr0, sector 1403480
[    6.870256] Buffer I/O error on device sr0, logical block 350870
[    7.704919] ISO 9660 Extensions: Microsoft Joliet Level 3
[    7.744071] ISO 9660 Extensions: RRIP_1991A
[    7.893603] aufs 2.1-standalone.tree-38-rcN-20110207
[    7.967658] squashfs: version 4.0 (2009/01/31) Phillip Lougher
[   49.548895] Adding 1952764k swap on /dev/sda2.  Priority:-1 extents:1 across:1952764k 
[   52.498504] <30>udev[1325]: starting version 167
[   56.064447] r8169 0000:03:05.0: eth0: link down
[   56.064757] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   56.819044] xhci_hcd 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   56.819065] xhci_hcd 0000:02:00.0: setting latency timer to 64
[   56.819069] xhci_hcd 0000:02:00.0: xHCI Host Controller
[   56.819151] xhci_hcd 0000:02:00.0: new USB bus registered, assigned bus number 8
[   56.845741] xhci_hcd 0000:02:00.0: irq 16, io mem 0xf5ff8000
[   56.845781] xhci_hcd 0000:02:00.0: irq 42 for MSI/MSI-X
[   56.845784] xhci_hcd 0000:02:00.0: irq 43 for MSI/MSI-X
[   56.845787] xhci_hcd 0000:02:00.0: irq 44 for MSI/MSI-X
[   56.845790] xhci_hcd 0000:02:00.0: irq 45 for MSI/MSI-X
[   56.845847] usb usb8: No SuperSpeed endpoint companion for config 1  interface 0 altsetting 0 ep 129: using minimum values
[   56.845928] xHCI xhci_add_endpoint called for root hub
[   56.845929] xHCI xhci_check_bandwidth called for root hub
[   56.845955] hub 8-0:1.0: USB hub found
[   56.845958] hub 8-0:1.0: 4 ports detected
[   57.476053] ACPI: resource piix4_smbus [io  0x0b00-0x0b07] conflicts with ACPI region SOR1 [io 0xb00-0xb0f]
[   57.476056] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   57.764538] Linux video capture interface: v2.00
[   57.829891] SP5100 TCO timer: SP5100 TCO WatchDog Timer Driver v0.01
[   57.829982] SP5100 TCO timer: mmio address 0xb8fe00 already in use
[   58.430343] r8169 0000:03:05.0: eth0: link up
[   58.430533] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   59.058378] IR NEC protocol handler initialized
[   59.442823] IR RC5(x) protocol handler initialized
[   59.684696] cx88/2: cx2388x MPEG-TS Driver Manager version 0.0.8 loaded
[   59.686066] cx88[0]: subsystem: 0070:6906, board: Hauppauge WinTV-HVR4000(Lite) DVB-S/S2 [card=69,autodetected], frontend(s): 1
[   59.686068] cx88[0]: TV tuner type -1, Radio tuner type -1
[   59.794814] cx88/0: cx2388x v4l2 driver version 0.0.8 loaded
[   60.066831] i2c-core: driver [tuner] using legacy suspend method
[   60.066834] i2c-core: driver [tuner] using legacy resume method
[   60.192051] IR RC6 protocol handler initialized
[   60.262743] tveeprom 4-0050: Hauppauge model 69100, rev B4C3, serial# 7793840
[   60.262746] tveeprom 4-0050: MAC address is 00:0d:fe:76:ec:b0
[   60.262749] tveeprom 4-0050: tuner model is Conexant CX24118A (idx 123, type 4)
[   60.262751] tveeprom 4-0050: TV standards ATSC/DVB Digital (eeprom 0x80)
[   60.262753] tveeprom 4-0050: audio processor is None (idx 0)
[   60.262755] tveeprom 4-0050: decoder processor is CX880 (idx 20)
[   60.262757] tveeprom 4-0050: has no radio, has IR receiver, has no IR transmitter
[   60.262758] cx88[0]: hauppauge eeprom: model=69100
[   60.509845] IR JVC protocol handler initialized
[   60.680310] cx2388x alsa driver version 0.0.8 loaded
[   60.696815] Registered IR keymap rc-hauppauge-new
[   60.696895] input: cx88 IR (Hauppauge WinTV-HVR400 as /devices/pci0000:00/0000:00:14.4/0000:03:06.2/rc/rc0/input4
[   60.696947] rc0: cx88 IR (Hauppauge WinTV-HVR400 as /devices/pci0000:00/0000:00:14.4/0000:03:06.2/rc/rc0
[   60.698311] cx88[0]/2: cx2388x 8802 Driver Manager
[   60.698330] cx88-mpeg driver manager 0000:03:06.2: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   60.698339] cx88[0]/2: found at 0000:03:06.2, rev: 5, irq: 21, latency: 64, mmio: 0xfb000000
[   60.699717] cx88[1]: subsystem: 0070:6906, board: Hauppauge WinTV-HVR4000(Lite) DVB-S/S2 [card=69,autodetected], frontend(s): 1
[   60.699720] cx88[1]: TV tuner type -1, Radio tuner type -1
[   60.876737] tveeprom 5-0050: Hauppauge model 69100, rev B4C3, serial# 7793859
[   60.876741] tveeprom 5-0050: MAC address is 00:0d:fe:76:ec:c3
[   60.876743] tveeprom 5-0050: tuner model is Conexant CX24118A (idx 123, type 4)
[   60.876745] tveeprom 5-0050: TV standards ATSC/DVB Digital (eeprom 0x80)
[   60.876747] tveeprom 5-0050: audio processor is None (idx 0)
[   60.876749] tveeprom 5-0050: decoder processor is CX880 (idx 20)
[   60.876751] tveeprom 5-0050: has no radio, has IR receiver, has no IR transmitter
[   60.876753] cx88[1]: hauppauge eeprom: model=69100
[   60.879196] Registered IR keymap rc-hauppauge-new
[   60.879312] input: cx88 IR (Hauppauge WinTV-HVR400 as /devices/pci0000:00/0000:00:14.4/0000:03:07.2/rc/rc1/input5
[   60.879393] rc1: cx88 IR (Hauppauge WinTV-HVR400 as /devices/pci0000:00/0000:00:14.4/0000:03:07.2/rc/rc1
[   60.879425] cx88[1]/2: cx2388x 8802 Driver Manager
[   60.879443] cx88-mpeg driver manager 0000:03:07.2: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   60.879452] cx88[1]/2: found at 0000:03:07.2, rev: 5, irq: 22, latency: 64, mmio: 0xf7000000
[   60.879496] cx8800 0000:03:06.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   60.879506] cx88[0]/0: found at 0000:03:06.0, rev: 5, irq: 21, latency: 64, mmio: 0xfd000000
[   60.879581] cx88[0]/0: registered device video0 [v4l2]
[   60.880237] cx88[0]/0: registered device vbi0
[   60.880293] cx8800 0000:03:07.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   60.880299] cx88[1]/0: found at 0000:03:07.0, rev: 5, irq: 22, latency: 64, mmio: 0xf9000000
[   60.880382] cx88[1]/0: registered device video1 [v4l2]
[   60.880426] cx88[1]/0: registered device vbi1
[   60.880504] cx88_audio 0000:03:06.1: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   60.880521] cx88[0]/1: CX88x/0: ALSA support for cx2388x boards
[   60.881043] cx88_audio 0000:03:07.1: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   60.881059] cx88[1]/1: CX88x/1: ALSA support for cx2388x boards
[   60.994952] IR Sony protocol handler initialized
[   61.206361] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   61.301199] lirc_dev: IR Remote Control driver registered, major 250 
[   61.764562] hda_codec: ALC887-VD: BIOS auto-probing.
[   61.771530] cx88/2: cx2388x dvb driver version 0.0.8 loaded
[   61.771533] cx88/2: registering cx8802 driver, type: dvb access: shared
[   61.771537] cx88[0]/2: subsystem: 0070:6906, board: Hauppauge WinTV-HVR4000(Lite) DVB-S/S2 [card=69]
[   61.771539] cx88[0]/2: cx2388x based DVB/ATSC card
[   61.771541] cx8802_alloc_frontends() allocating 1 frontend(s)
[   61.772381] rc rc0: lirc_dev: driver ir-lirc-codec (cx88xx) registered at minor = 0
[   61.772412] rc rc1: lirc_dev: driver ir-lirc-codec (cx88xx) registered at minor = 1
[   61.772414] IR LIRC bridge handler initialized
[   61.777166] input: HDA ATI SB Headphone as /devices/pci0000:00/0000:00:14.2/sound/card2/input6
[   61.777289] HDA Intel 0000:01:00.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   61.777292] hda_intel: Disable MSI for Nvidia chipset
[   61.777317] HDA Intel 0000:01:00.1: setting latency timer to 64
[   63.129476] DVB: registering new adapter (cx88[0])
[   63.129480] DVB: registering adapter 0 frontend 0 (Conexant CX24116/CX2411...
[   63.129711] cx88[1]/2: subsystem: 0070:6906, board: Hauppauge WinTV-HVR4000(Lite) DVB-S/S2 [card=69]
[   63.129714] cx88[1]/2: cx2388x based DVB/ATSC card
[   63.129715] cx8802_alloc_frontends() allocating 1 frontend(s)
[   63.131639] DVB: registering new adapter (cx88[1])
[   63.131641] DVB: registering adapter 1 frontend 0 (Conexant CX24116/CX2411...
[   63.265215] vmap allocation for size 4198400 failed: use vmalloc=<size> to increase size.
[   63.280906] vmap allocation for size 4198400 failed: use vmalloc=<size> to increase size.
[   68.672009] eth0: no IPv6 routers present
[   69.024425] lp: driver loaded but no devices found
[   69.253394] ppdev: user-space parallel port driver
[   94.251918] hda-intel: IRQ timing workaround is activated for card #3. Suggest a bigger bdl_pos_adj.
[  411.248332] EXT3-fs: barriers not enabled
[  411.266464] kjournald starting.  Commit interval 5 seconds
[  411.266854] EXT3-fs (sda1): using internal journal
[  411.266858] EXT3-fs (sda1): mounted filesystem with ordered data mode


bootlog - this also seems to be what's garbled to the screen before halting, however all the stuff on screen is not in the bootlog!

fsck from util-linux-ng 2.17.2
fsck from util-linux-ng 2.17.2
fsck from util-linux-ng 2.17.2
lircd-0.8.7[798]: lircd(default) ready, using /var/run/lirc/lircd

/sbin/fsck.xfs: XFS file system.
/sbin/fsck.xfs: XFS file system.
/dev/sda1: clean, 262069/30408704 files, 108920492/121608192 blocks
init: ureadahead-other main process (839) terminated with status 4

init: ureadahead-other main process (844) terminated with status 4

Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
 * Starting AppArmor profiles       [80G 
[74G[ OK ]
Loading the saved-state of the serial devices... 
mount error(101): Network is unreachable
Refer to the mount.cifs( manual page (e.g. man mount.cifs)
mountall: mount /home/name/storage/videos/Video [872] terminated with status 32
mount error(101): Network is unreachable
Refer to the mount.cifs( manual page (e.g. man mount.cifs)
mountall: mount /home/name/storage/videos/VideoK [873] terminated with status 32
mount error(101): Network is unreachable
Refer to the mount.cifs( manual page (e.g. man mount.cifs)
mountall: mount /home/name/storage/music/Audio [951] terminated with status 32
 * Loading LIRC modules       [80G 
[74G[ OK ]
 * Stopping System V initialisation compatibility[74G[ OK ]
mount error(101): Network is unreachable
Refer to the mount.cifs( manual page (e.g. man mount.cifs)
mountall: mount /home/name/storage/pictures [954] terminated with status 32
 * Starting remote control daemon(s) : LIRC       [80G 
[74G[ OK ]
speech-dispatcher disabled; edit /etc/default/speech-dispatcher
 [33m*[39;49m Saved ALSA mixer settings detected; aumix will not touch mixer.
 * Starting System V runlevel compatibility[74G[ OK ]
 * Stopping automatic crash report generation[74G[[31mfail[39;49m]
 * Starting CPU interrupts balancing daemon[74G[ OK ]
 * Starting ACPI daemon[74G[ OK ]
 * Starting save kernel messages[74G[ OK ]
 * Starting NTP server ntpd       [80G 
[74G[ OK ]
 * Starting anac(h)ronistic cron[74G[ OK ]
 * Starting bluetooth       [80G 
[74G[ OK ]
 [33m*[39;49m PulseAudio configured for per-user sessions
 * Starting regular background program processing daemon[74G[ OK ]
 * Starting deferred execution scheduler[74G[ OK ]
saned disabled; edit /etc/default/saned
 * Stopping save kernel messages[74G[ OK ]
 * Enabling additional executable binary formats binfmt-support       [80G 
[74G[ OK ]
 * Stopping cold plug devices[74G[ OK ]
 * Stopping log initial device creation[74G[ OK ]
apache2: Could not reliably determine the server's fully qualified domain name, using ::1 for ServerName
 * Starting load fallback graphics devices[74G[ OK ]
 * Starting configure network device security[74G[ OK ]
 * Starting configure virtual network devices[74G[ OK ]
 * Stopping load fallback graphics devices[74G[ OK ]
 * Stopping configure virtual network devices[74G[ OK ]
mount error(101): Network is unreachable
Refer to the mount.cifs( manual page (e.g. man mount.cifs)
mountall: mount /home/name/storage/videos/Video [1176] terminated with status 32
mount error(101): Network is unreachable
Refer to the mount.cifs( manual page (e.g. man mount.cifs)
 * Starting Userspace bootsplash[74G[ OK ]
 * Starting GNOME Display Manager[74G[ OK ]
mountall: mount /home/name/storage/videos/VideoK [1178] terminated with status 32
mount error(101): Network is unreachable
Refer to the mount.cifs( manual page (e.g. man mount.cifs)
mountall: mount /home/name/storage/music/Audio [1180] terminated with status 32
mount error(101): Network is unreachable
Refer to the mount.cifs( manual page (e.g. man mount.cifs)
mountall: mount /home/name/storage/pictures [1184] terminated with status 32
 * Stopping Userspace bootsplash[74G[ OK ]
 * Starting web server apache2       [80G 
[74G[ OK ]
 * Stopping anac(h)ronistic cron[74G[ OK ]


Hope this is data is useful in pointing to the problem.

---

### Post by b1acksun on 2011-09-23
Have placed the problems after plenty of double checking:
Network card onboard has no driver or it's not been loaded - replacing it with an RTL8169 resolved the network error messges - used MS Win7 to check board reliability; seems the release of MS Win7 we used also did not have drivers for the RTL8111E; in went the RTL8169, once online to the MS update site drivers for the RTL8111E were made available.

The issue with Xorg bailing out to command line after the 2nd HDS2 card was inserted into the mythbuntu box:-
We spotted a strange report by inspecting Xorgs log, it claimed no driver available for the Nvidia Geforce 210!
We removed the Geforce 210 and checked it on other Linux kits - no problem always fired up even on the myhtbuntu box with a different Linux distrobution.
We put back the original HDD with mythbuntu back into its original home and replaced the video card with an  Nvidia 7300 from another machine - everything came up even after rebooting and powering down several times.

Current status - mythbuntu box not crashing out and refusing to start - have what we think and hope is a configuration problem:
The software is not automatically switching over to alternative source cards when a card is busy - have to manually select with switch source option which never happened when I had my wintv nova500's - this is bad as it's most definitely a WG fail point.

---

