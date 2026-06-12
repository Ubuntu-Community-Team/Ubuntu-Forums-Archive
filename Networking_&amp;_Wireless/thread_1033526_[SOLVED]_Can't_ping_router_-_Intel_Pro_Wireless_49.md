---
title: "[SOLVED] Can't ping router - Intel Pro Wireless 4965AGN"
date: 2009-01-07
forum: Networking &amp; Wireless
---

### Post by dresi on 2009-01-07
I just installed Ubuntu 8.10 and my wireless seems to be detected correctly (It automatically finds the Wifi link and asks me for a WPA key), but I am unable to ping the router. I can ping the computer itself but not the router or anything outside of that.

I wasn't sure what information you would need, I've tried searching the forums but this wireless deal is new to me so I'm not quite sure what to do.

I think all the details should be here below. If not I will post them as quickly as possible.

Thanks for any help.


1.
Asus G1s

2.
$ lspci
```

03:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
```

$ lsusb
```
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 003: ID 0b05:1726 ASUSTek Computer, Inc. Laptop OLED Display
Bus 003 Device 002: ID 04f2:b012 Chicony Electronics Co., Ltd 1.3 MPixel UVC webcam
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 002: ID 0b05:1712 ASUSTek Computer, Inc. BT-183 Bluetooth 2.0+EDR adapter
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 046d:c01e Logitech, Inc. MX518 Optical Mouse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

3.	
$ ifconfig
```

wlan0     Link encap:Ethernet  HWaddr 00:13:e8:f6:a0:87  
          inet addr:192.168.1.64  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:e8ff:fef6:a087/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:51 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3112 (3.1 KB)  TX bytes:5390 (5.3 KB)

	$ iwconfig
wlan0     IEEE 802.11abgn  ESSID:"TeliaGateway00-1F-9F-50-31-0D"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1F:9F:50:31:0D   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Encryption key:2910-6386-8076-C2BD-28E4-4196-1662-FEA0-B06A-38D2-5830-35A0-BC47-F7B2-8122-7431 [2]   Security mode:open
          Power Management:off
          Link Quality=100/100  Signal level:-53 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

4.
$ lsmod
```

Module                  Size  Used by
af_packet              25728  4 
binfmt_misc            16904  1 
rfcomm                 44432  2 
bridge                 56980  0 
stp                    10628  1 bridge
bnep                   20480  2 
sco                    18308  2 
l2cap                  30464  16 rfcomm,bnep
ppdev                  15620  0 
acpi_cpufreq           15500  1 
cpufreq_stats          13188  0 
cpufreq_userspace      11396  0 
cpufreq_conservative    14600  0 
cpufreq_powersave       9856  0 
cpufreq_ondemand       14988  1 
freq_table             12672  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
wmi                    14504  0 
pci_slot               12552  0 
container              11520  0 
sbs                    19464  0 
sbshc                  13440  1 sbs
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
sbp2                   29324  0 
parport_pc             39204  0 
lp                     17156  0 
parport                42604  3 ppdev,parport_pc,lp
loop                   23180  0 
joydev                 18368  0 
ipv6                  263972  10 
sdhci_pci              15360  0 
arc4                    9984  2 
ecb                    10880  2 
crypto_blkcipher       25476  1 ecb
sdhci                  23940  1 sdhci_pci
btusb                  19736  3 
mmc_core               58268  1 sdhci
snd_hda_intel         381488  3 
iwlagn                 99588  0 
pcspkr                 10624  0 
iTCO_wdt               18596  0 
psmouse                45200  0 
serio_raw              13444  0 
evdev                  17696  11 
iwlcore                92740  1 iwlagn
bluetooth              61924  11 rfcomm,bnep,sco,l2cap,btusb
uvcvideo               62728  0 
iTCO_vendor_support    11652  1 iTCO_wdt
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
compat_ioctl32          9344  1 uvcvideo
snd_pcm                83204  2 snd_hda_intel,snd_pcm_oss
videodev               41344  1 uvcvideo
rfkill                 17176  2 iwlcore
mac80211              216820  2 iwlagn,iwlcore
v4l1_compat            22404  2 uvcvideo,videodev
snd_seq_dummy          10884  0 
cfg80211               32392  3 iwlagn,iwlcore,mac80211
snd_seq_oss            38528  0 
video                  25104  0 
snd_seq_midi           14336  0 
snd_rawmidi            29824  1 snd_seq_midi
output                 11008  1 video
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    63268  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
battery                18436  0 
ac                     12292  0 
asus_laptop            24440  0 
soundcore              15328  1 snd
led_class              12164  2 iwlcore,asus_laptop
intel_agp              33724  0 
button                 14224  0 
snd_page_alloc         16136  2 snd_hda_intel,snd_pcm
agpgart                42184  1 intel_agp
shpchp                 37908  0 
pci_hotplug            35236  1 shpchp
ext3                  133256  1 
jbd                    55444  1 ext3
mbcache                16004  1 ext3
sr_mod                 22212  0 
cdrom                  43168  1 sr_mod
sd_mod                 42264  4 
crc_t10dif              9984  1 sd_mod
ata_piix               24580  0 
pata_acpi              12160  0 
sg                     39732  0 
usbhid                 35840  0 
hid                    50560  1 usbhid
ata_generic            12932  0 
ohci1394               37936  0 
ahci                   37132  3 
ieee1394               96324  2 sbp2,ohci1394
libata                177312  4 ata_piix,pata_acpi,ata_generic,ahci
scsi_mod              155212  5 sbp2,sr_mod,sd_mod,sg,libata
dock                   16656  1 libata
r8169                  35972  0 
ehci_hcd               43276  0 
uhci_hcd               30736  0 
usbcore               148848  6 btusb,uvcvideo,usbhid,ehci_hcd,uhci_hcd
thermal                23708  0 
processor              42156  4 acpi_cpufreq,thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  5 

```

5.
$ dmesg
```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-7-generic (buildd@rothera) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu10) ) #1 SMP Fri Oct 24 06:42:44 UTC 2008 (Ubuntu 2.6.27-7.14-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007ffb0000 (usable)
[    0.000000]  BIOS-e820: 000000007ffb0000 - 000000007ffbe000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007ffbe000 - 000000007fff0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007fff0000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] last_pfn = 0x7ffb0 max_arch_pfn = 0x100000
[    0.000000] kernel direct mapping tables up to 38000000 @ 7000-c000
[    0.000000] RAMDISK: 37827000 - 37fefda8
[    0.000000] DMI 2.4 present.
[    0.000000] ACPI: RSDP 000F81D0, 0024 (r2 ACPIAM)
[    0.000000] ACPI: XSDT 7FFB0100, 007C (r1 _ASUS_ Notebook 12000725 MSFT       97)
[    0.000000] ACPI: FACP 7FFB0290, 00F4 (r3 A_M_I_ OEMFACP  12000725 MSFT       97)
[    0.000000] ACPI: DSDT 7FFB0680, AE02 (r1  G1S00 G1S00000        0 INTL 20051117)
[    0.000000] ACPI: FACS 7FFBE000, 0040
[    0.000000] ACPI: APIC 7FFB0390, 005C (r1 A_M_I_ OEMAPIC  12000725 MSFT       97)
[    0.000000] ACPI: MCFG 7FFB0430, 003C (r1 A_M_I_ OEMMCFG  12000725 MSFT       97)
[    0.000000] ACPI: SLIC 7FFB0470, 0176 (r1 _ASUS_ Notebook 12000725 MSFT       97)
[    0.000000] ACPI: DBGP 7FFB03F0, 0034 (r1 A_M_I_ OEMDBGP  12000725 MSFT       97)
[    0.000000] ACPI: BOOT 7FFB05F0, 0028 (r1 A_M_I_ OEMBOOT  12000725 MSFT       97)
[    0.000000] ACPI: ECDT 7FFB0620, 0054 (r1 A_M_I_ OEMECDT  12000725 MSFT       97)
[    0.000000] ACPI: OEMB 7FFBE040, 0060 (r1 A_M_I_ AMI_OEM  12000725 MSFT       97)
[    0.000000] ACPI: HPET 7FFBB490, 0038 (r1 A_M_I_ OEMHPET  12000725 MSFT       97)
[    0.000000] ACPI: ATKG 7FFBE2A0, 8024 (r1 A_M_I_  OEMATKG  5000702 MSFT       97)
[    0.000000] ACPI: SSDT 7FFC6E20, 04E6 (r1  PmRef    CpuPm     3000 INTL 20051117)
[    0.000000] 1151MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 38000000
[    0.000000]   low ram: 00000000 - 38000000
[    0.000000]   bootmap 00008000 - 0000f000
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 0038000000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00005c0a20]    TEXT DATA BSS ==> [0000100000 - 00005c0a20]
[    0.000000]   #4 [0037827000 - 0037fefda8]          RAMDISK ==> [0037827000 - 0037fefda8]
[    0.000000]   #5 [00005c1000 - 00005c4000]    INIT_PG_TABLE ==> [00005c1000 - 00005c4000]
[    0.000000]   #6 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #7 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
[    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
[    0.000000] found SMP MP-table at [c00ff780] 000ff780
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00038000
[    0.000000]   HighMem  0x00038000 -> 0x0007ffb0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0007ffb0
[    0.000000] On node 0 totalpages: 524111
[    0.000000] free_area_init_node: node 0, pgdat c048a500, node_mem_map c1000000
[    0.000000]   DMA zone: 3963 pages, LIFO batch:0
[    0.000000]   Normal zone: 223300 pages, LIFO batch:31
[    0.000000]   HighMem zone: 292240 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e4000
[    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:7ee00000)
[    0.000000] PERCPU: Allocating 41628 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 2, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 519503
[    0.000000] Kernel command line: root=UUID=f63549ec-4a83-4ebf-b4ad-8a85841cdb16 ro quiet splash 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Extended CMOS year: 2000
[    0.000000] TSC: PIT calibration confirmed by PMTIMER.
[    0.000000] TSC: using PMTIMER calibration value
[    0.000000] Detected 2393.993 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] Memory: 2063300k/2096832k available (2572k kernel code, 32232k reserved, 1160k data, 424k init, 1179328k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xf8800000 - 0xff3fe000   ( 107 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[    0.004000]       .init : 0xc04ab000 - 0xc0515000   ( 424 kB)
[    0.004000]       .data : 0xc038329a - 0xc04a5680   (1160 kB)
[    0.004000]       .text : 0xc0100000 - 0xc038329a   (2572 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.004000] hpet clockevent registered
[    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 4787.98 BogoMIPS (lpj=9575972)
[    0.004000] Security Framework initialized
[    0.004000] SELinux:  Disabled at boot.
[    0.004000] AppArmor: AppArmor initialized
[    0.004000] Mount-cache hash table entries: 512
[    0.004000] Initializing cgroup subsys ns
[    0.004000] Initializing cgroup subsys cpuacct
[    0.004000] Initializing cgroup subsys memory
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 4096K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 0
[    0.004000] using mwait in idle threads.
[    0.004000] Checking 'hlt' instruction... OK.
[    0.017568] ACPI: Core revision 20080609
[    0.021161] ACPI: Checking initramfs for custom DSDT
[    0.308201] ENABLING IO-APIC IRQs
[    0.308372] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.351177] CPU0: Intel(R) Core(TM)2 Duo CPU     T7700  @ 2.40GHz stepping 0b
[    0.352022] Booting processor 1/1 ip 6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 4787.95 BogoMIPS (lpj=9575917)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 4096K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.436558] CPU1: Intel(R) Core(TM)2 Duo CPU     T7700  @ 2.40GHz stepping 0b
[    0.436572] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.440045] Brought up 2 CPUs
[    0.440048] Total of 2 processors activated (9575.94 BogoMIPS).
[    0.440067] CPU0 attaching sched-domain:
[    0.440069]  domain 0: span 0-1 level MC
[    0.440071]   groups: 0 1
[    0.440076] CPU1 attaching sched-domain:
[    0.440078]  domain 0: span 0-1 level MC
[    0.440080]   groups: 1 0
[    0.440144] net_namespace: 840 bytes
[    0.440144] Booting paravirtualized kernel on bare hardware
[    0.440243] Time: 19:18:21  Date: 01/07/09
[    0.440265] NET: Registered protocol family 16
[    0.440280] EISA bus registered
[    0.440280] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.440280] ACPI: bus type pci registered
[    0.440280] PCI: MCFG configuration 0: base c0000000 segment 0 buses 0 - 255
[    0.440280] PCI: Not using MMCONFIG.
[    0.440280] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=8
[    0.440280] PCI: Using configuration type 1 for base access
[    0.441332] ACPI: EC: EC description table is found, configuring boot EC
[    0.456786] ACPI: Interpreter enabled
[    0.456790] ACPI: (supports S0 S1 S3 S4 S5)
[    0.456796] ACPI: Using IOAPIC for interrupt routing
[    0.457548] PCI: MCFG configuration 0: base c0000000 segment 0 buses 0 - 255
[    0.461005] PCI: MCFG area at c0000000 reserved in ACPI motherboard resources
[    0.461007] PCI: Using MMCONFIG for extended config space
[    0.469868] ACPI: EC: GPE = 0x1c, I/O: command/status = 0x66, data = 0x62
[    0.469868] ACPI: EC: driver started in poll mode
[    0.472091] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.472114] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.472114] pci 0000:00:01.0: PME# disabled
[    0.472162] PCI: 0000:00:1a.0 reg 20 io port: [e080, e09f]
[    0.472208] PCI: 0000:00:1a.1 reg 20 io port: [e000, e01f]
[    0.472261] PCI: 0000:00:1a.7 reg 10 32bit mmio: [febff400, febff7ff]
[    0.472306] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.472310] pci 0000:00:1a.7: PME# disabled
[    0.472342] PCI: 0000:00:1b.0 reg 10 64bit mmio: [febf8000, febfbfff]
[    0.472378] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.472382] pci 0000:00:1b.0: PME# disabled
[    0.472429] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.472432] pci 0000:00:1c.0: PME# disabled
[    0.472479] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.472483] pci 0000:00:1c.1: PME# disabled
[    0.472530] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.472533] pci 0000:00:1c.2: PME# disabled
[    0.472582] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.472585] pci 0000:00:1c.3: PME# disabled
[    0.472632] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.472636] pci 0000:00:1c.4: PME# disabled
[    0.472671] PCI: 0000:00:1d.0 reg 20 io port: [dc00, dc1f]
[    0.472717] PCI: 0000:00:1d.1 reg 20 io port: [d880, d89f]
[    0.472763] PCI: 0000:00:1d.2 reg 20 io port: [d800, d81f]
[    0.472814] PCI: 0000:00:1d.7 reg 10 32bit mmio: [febff000, febff3ff]
[    0.472859] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.472864] pci 0000:00:1d.7: PME# disabled
[    0.472973] pci 0000:00:1f.0: quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
[    0.472976] pci 0000:00:1f.0: quirk: region 0500-053f claimed by ICH6 GPIO
[    0.472998] PCI: 0000:00:1f.1 reg 10 io port: [0, 7]
[    0.473004] PCI: 0000:00:1f.1 reg 14 io port: [0, 3]
[    0.473010] PCI: 0000:00:1f.1 reg 18 io port: [8f0, 8f7]
[    0.473017] PCI: 0000:00:1f.1 reg 1c io port: [8f8, 8fb]
[    0.473023] PCI: 0000:00:1f.1 reg 20 io port: [ffa0, ffaf]
[    0.473072] PCI: 0000:00:1f.2 reg 10 io port: [ec00, ec07]
[    0.473077] PCI: 0000:00:1f.2 reg 14 io port: [e880, e883]
[    0.473083] PCI: 0000:00:1f.2 reg 18 io port: [e800, e807]
[    0.473088] PCI: 0000:00:1f.2 reg 1c io port: [e480, e483]
[    0.473093] PCI: 0000:00:1f.2 reg 20 io port: [e400, e41f]
[    0.473099] PCI: 0000:00:1f.2 reg 24 32bit mmio: [febff800, febfffff]
[    0.473121] pci 0000:00:1f.2: PME# supported from D3hot
[    0.473124] pci 0000:00:1f.2: PME# disabled
[    0.473157] PCI: 0000:01:00.0 reg 10 32bit mmio: [fc000000, fcffffff]
[    0.473163] PCI: 0000:01:00.0 reg 14 32bit mmio: [e0000000, efffffff]
[    0.473175] PCI: 0000:01:00.0 reg 1c 64bit mmio: [fa000000, fbffffff]
[    0.473181] PCI: 0000:01:00.0 reg 24 io port: [9c00, 9c7f]
[    0.473186] PCI: 0000:01:00.0 reg 30 32bit mmio: [fdee0000, fdefffff]
[    0.473233] PCI: bridge 0000:00:01.0 io port: [9000, 9fff]
[    0.473236] PCI: bridge 0000:00:01.0 32bit mmio: [f7e00000, fdefffff]
[    0.473240] PCI: bridge 0000:00:01.0 64bit mmio pref: [d5d00000, f5cfffff]
[    0.473297] PCI: 0000:02:00.0 reg 10 io port: [a800, a8ff]
[    0.473319] PCI: 0000:02:00.0 reg 18 64bit mmio: [fdfff000, fdffffff]
[    0.473342] PCI: 0000:02:00.0 reg 30 32bit mmio: [fdfc0000, fdfdffff]
[    0.473363] pci 0000:02:00.0: supports D1
[    0.473364] pci 0000:02:00.0: supports D2
[    0.473366] pci 0000:02:00.0: PME# supported from D1 D2 D3hot D3cold
[    0.473371] pci 0000:02:00.0: PME# disabled
[    0.473404] PCI: bridge 0000:00:1c.0 io port: [a000, afff]
[    0.473408] PCI: bridge 0000:00:1c.0 32bit mmio: [fdf00000, fdffffff]
[    0.473485] PCI: 0000:03:00.0 reg 10 64bit mmio: [fe0fe000, fe0fffff]
[    0.473564] pci 0000:03:00.0: PME# supported from D0 D3hot D3cold
[    0.473571] pci 0000:03:00.0: PME# disabled
[    0.473606] PCI: bridge 0000:00:1c.1 32bit mmio: [fe000000, fe0fffff]
[    0.473649] PCI: bridge 0000:00:1c.2 io port: [b000, bfff]
[    0.473653] PCI: bridge 0000:00:1c.2 32bit mmio: [fe100000, fe8fffff]
[    0.473658] PCI: bridge 0000:00:1c.2 64bit mmio pref: [f5d00000, f7cfffff]
[    0.473758] PCI: 0000:07:00.0 reg 10 io port: [cc00, cc07]
[    0.473767] PCI: 0000:07:00.0 reg 14 io port: [c880, c883]
[    0.473776] PCI: 0000:07:00.0 reg 18 io port: [c800, c807]
[    0.473785] PCI: 0000:07:00.0 reg 1c io port: [c480, c483]
[    0.473793] PCI: 0000:07:00.0 reg 20 io port: [c400, c40f]
[    0.473802] PCI: 0000:07:00.0 reg 24 32bit mmio: [fe9fe000, fe9fffff]
[    0.473833] pci 0000:07:00.0: PME# supported from D3hot
[    0.473839] pci 0000:07:00.0: PME# disabled
[    0.473872] PCI: bridge 0000:00:1c.4 io port: [c000, cfff]
[    0.473876] PCI: bridge 0000:00:1c.4 32bit mmio: [fe900000, fe9fffff]
[    0.473913] PCI: 0000:08:01.0 reg 10 32bit mmio: [feaff800, feafffff]
[    0.473956] pci 0000:08:01.0: PME# supported from D0 D3hot D3cold
[    0.473960] pci 0000:08:01.0: PME# disabled
[    0.473988] PCI: 0000:08:01.1 reg 10 32bit mmio: [feaff400, feaff4ff]
[    0.474031] pci 0000:08:01.1: supports D1
[    0.474032] pci 0000:08:01.1: supports D2
[    0.474034] pci 0000:08:01.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.474038] pci 0000:08:01.1: PME# disabled
[    0.474066] PCI: 0000:08:01.2 reg 10 32bit mmio: [feaff000, feaff0ff]
[    0.474109] pci 0000:08:01.2: supports D1
[    0.474110] pci 0000:08:01.2: supports D2
[    0.474112] pci 0000:08:01.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.474116] pci 0000:08:01.2: PME# disabled
[    0.474144] PCI: 0000:08:01.3 reg 10 32bit mmio: [feafec00, feafecff]
[    0.474186] pci 0000:08:01.3: supports D1
[    0.474188] pci 0000:08:01.3: supports D2
[    0.474189] pci 0000:08:01.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.474193] pci 0000:08:01.3: PME# disabled
[    0.474238] pci 0000:00:1e.0: transparent bridge
[    0.474243] PCI: bridge 0000:00:1e.0 32bit mmio: [fea00000, feafffff]
[    0.474276] bus 00 -> node 0
[    0.474283] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.474539] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.474688] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P2._PRT]
[    0.474832] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P3._PRT]
[    0.474978] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[    0.475133] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P5._PRT]
[    0.475274] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P6._PRT]
[    0.475395] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P9._PRT]
[    0.496175] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12)
[    0.496349] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 10 12)
[    0.496521] ACPI: PCI Interrupt Link [LNKC] (IRQs *3)
[    0.496690] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 *7 10 12)
[    0.496861] ACPI: PCI Interrupt Link [LNKE] (IRQs *6)

[    0.497030] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 *4 5 6 7 10 12)
[    0.497201] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 *10 12)
[    0.497372] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 10 12)
[    0.500343] ACPI Warning (tbutils-0217): Incorrect checksum in table [ATKG] - AA, should be 59 [20080609]
[    0.500355] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.500364] pnp: PnP ACPI init
[    0.500364] ACPI: bus type pnp registered
[    0.500651] pnp: PnP ACPI: found 13 devices
[    0.500651] ACPI: ACPI bus type pnp unregistered
[    0.500651] PnPBIOS: Disabled by ACPI PNP
[    0.500651] PCI: Using ACPI for IRQ routing
[    0.508039] NET: Registered protocol family 8
[    0.508041] NET: Registered protocol family 20
[    0.508053] NetLabel: Initializing
[    0.508053] NetLabel:  domain hash size = 128
[    0.508053] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.508059] NetLabel:  unlabeled traffic allowed by default
[    0.508064] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.508068] hpet0: 3 64-bit timers, 14318180 Hz
[    0.509454] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    0.509456]    actual entries 65620
[    0.509529] AppArmor: AppArmor Filesystem Enabled
[    0.509547] ACPI: RTC can wake from S4
[    0.512038] Switched to high resolution mode on CPU 0
[    0.512591] Switched to high resolution mode on CPU 1
[    0.516017] system 00:01: iomem range 0xfed14000-0xfed19fff has been reserved
[    0.516027] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[    0.516029] system 00:08: ioport range 0x800-0x87f has been reserved
[    0.516032] system 00:08: ioport range 0x400-0x41f has been reserved
[    0.516034] system 00:08: ioport range 0x500-0x53f has been reserved
[    0.516037] system 00:08: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    0.516039] system 00:08: iomem range 0xfed20000-0xfed3ffff has been reserved
[    0.516042] system 00:08: iomem range 0xfed45000-0xfed89fff has been reserved
[    0.516044] system 00:08: iomem range 0xffb00000-0xffbfffff could not be reserved
[    0.516047] system 00:08: iomem range 0xfff00000-0xffffffff could not be reserved
[    0.516053] system 00:0a: ioport range 0x250-0x253 has been reserved
[    0.516055] system 00:0a: ioport range 0x256-0x25f has been reserved
[    0.516058] system 00:0a: iomem range 0xfec00000-0xfec00fff has been reserved
[    0.516060] system 00:0a: iomem range 0xfee00000-0xfee00fff could not be reserved
[    0.516065] system 00:0b: iomem range 0xc0000000-0xcfffffff has been reserved
[    0.516070] system 00:0c: iomem range 0x0-0x9ffff could not be reserved
[    0.516072] system 00:0c: iomem range 0xc0000-0xcffff could not be reserved
[    0.516075] system 00:0c: iomem range 0xe0000-0xfffff could not be reserved
[    0.516077] system 00:0c: iomem range 0x100000-0x7fffffff could not be reserved
[    0.551060] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.551063] pci 0000:00:01.0:   IO window: 0x9000-0x9fff
[    0.551067] pci 0000:00:01.0:   MEM window: 0xf7e00000-0xfdefffff
[    0.551070] pci 0000:00:01.0:   PREFETCH window: 0x000000d5d00000-0x000000f5cfffff
[    0.551074] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
[    0.551077] pci 0000:00:1c.0:   IO window: 0xa000-0xafff
[    0.551082] pci 0000:00:1c.0:   MEM window: 0xfdf00000-0xfdffffff
[    0.551085] pci 0000:00:1c.0:   PREFETCH window: disabled
[    0.551091] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:03
[    0.551093] pci 0000:00:1c.1:   IO window: disabled
[    0.551097] pci 0000:00:1c.1:   MEM window: 0xfe000000-0xfe0fffff
[    0.551101] pci 0000:00:1c.1:   PREFETCH window: disabled
[    0.551106] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:04
[    0.551109] pci 0000:00:1c.2:   IO window: 0xb000-0xbfff
[    0.551114] pci 0000:00:1c.2:   MEM window: 0xfe100000-0xfe8fffff
[    0.551118] pci 0000:00:1c.2:   PREFETCH window: 0x000000f5d00000-0x000000f7cfffff
[    0.551123] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:06
[    0.551125] pci 0000:00:1c.3:   IO window: disabled
[    0.551129] pci 0000:00:1c.3:   MEM window: disabled
[    0.551133] pci 0000:00:1c.3:   PREFETCH window: disabled
[    0.551138] pci 0000:00:1c.4: PCI bridge, secondary bus 0000:07
[    0.551141] pci 0000:00:1c.4:   IO window: 0xc000-0xcfff
[    0.551146] pci 0000:00:1c.4:   MEM window: 0xfe900000-0xfe9fffff
[    0.551149] pci 0000:00:1c.4:   PREFETCH window: disabled
[    0.551155] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:08
[    0.551156] pci 0000:00:1e.0:   IO window: disabled
[    0.551161] pci 0000:00:1e.0:   MEM window: 0xfea00000-0xfeafffff

[    0.551165] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.551176] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.551180] pci 0000:00:01.0: setting latency timer to 64
[    0.551186] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.551190] pci 0000:00:1c.0: setting latency timer to 64
[    0.551197] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.551201] pci 0000:00:1c.1: setting latency timer to 64
[    0.551208] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.551212] pci 0000:00:1c.2: setting latency timer to 64
[    0.551219] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.551222] pci 0000:00:1c.3: setting latency timer to 64
[    0.551229] pci 0000:00:1c.4: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.551233] pci 0000:00:1c.4: setting latency timer to 64
[    0.551239] pci 0000:00:1e.0: setting latency timer to 64
[    0.551242] bus: 00 index 0 io port: [0, ffff]
[    0.551244] bus: 00 index 1 mmio: [0, ffffffff]
[    0.551246] bus: 01 index 0 io port: [9000, 9fff]
[    0.551247] bus: 01 index 1 mmio: [f7e00000, fdefffff]
[    0.551249] bus: 01 index 2 mmio: [d5d00000, f5cfffff]
[    0.551251] bus: 01 index 3 mmio: [0, 0]
[    0.551253] bus: 02 index 0 io port: [a000, afff]
[    0.551254] bus: 02 index 1 mmio: [fdf00000, fdffffff]
[    0.551256] bus: 02 index 2 mmio: [0, 0]
[    0.551257] bus: 02 index 3 mmio: [0, 0]
[    0.551259] bus: 03 index 0 mmio: [0, 0]
[    0.551261] bus: 03 index 1 mmio: [fe000000, fe0fffff]
[    0.551262] bus: 03 index 2 mmio: [0, 0]
[    0.551264] bus: 03 index 3 mmio: [0, 0]
[    0.551265] bus: 04 index 0 io port: [b000, bfff]
[    0.551267] bus: 04 index 1 mmio: [fe100000, fe8fffff]
[    0.551269] bus: 04 index 2 mmio: [f5d00000, f7cfffff]
[    0.551270] bus: 04 index 3 mmio: [0, 0]
[    0.551272] bus: 06 index 0 mmio: [0, 0]
[    0.551274] bus: 06 index 1 mmio: [0, 0]
[    0.551275] bus: 06 index 2 mmio: [0, 0]
[    0.551276] bus: 06 index 3 mmio: [0, 0]
[    0.551278] bus: 07 index 0 io port: [c000, cfff]
[    0.551280] bus: 07 index 1 mmio: [fe900000, fe9fffff]
[    0.551281] bus: 07 index 2 mmio: [0, 0]
[    0.551283] bus: 07 index 3 mmio: [0, 0]
[    0.551284] bus: 08 index 0 mmio: [0, 0]
[    0.551286] bus: 08 index 1 mmio: [fea00000, feafffff]
[    0.551288] bus: 08 index 2 mmio: [0, 0]
[    0.551289] bus: 08 index 3 io port: [0, ffff]
[    0.551291] bus: 08 index 4 mmio: [0, ffffffff]
[    0.551297] NET: Registered protocol family 2
[    0.564040] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.564226] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.564508] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.564649] TCP: Hash tables configured (established 131072 bind 65536)
[    0.564652] TCP reno registered
[    0.568054] NET: Registered protocol family 1
[    0.568138] checking if image is initramfs... it is
[    1.137887] Freeing initrd memory: 7971k freed
[    1.138050] Simple Boot Flag at 0x52 set to 0x1
[    1.138834] audit: initializing netlink socket (disabled)
[    1.138855] type=2000 audit(1231355901.137:1): initialized
[    1.143752] highmem bounce pool size: 64 pages
[    1.143757] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.145658] VFS: Disk quotas dquot_6.5.1
[    1.145728] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.145811] msgmni has been set to 1743
[    1.145906] io scheduler noop registered
[    1.145908] io scheduler anticipatory registered
[    1.145910] io scheduler deadline registered
[    1.145919] io scheduler cfq registered (default)
[    1.176453] pci 0000:01:00.0: Boot video device
[    1.176558] pcieport-driver 0000:00:01.0: setting latency timer to 64
[    1.176592] pcieport-driver 0000:00:01.0: found MSI capability
[    1.176621] pci_express 0000:00:01.0:pcie00: allocate port service
[    1.176652] pci_express 0000:00:01.0:pcie02: allocate port service
[    1.176681] pci_express 0000:00:01.0:pcie03: allocate port service
[    1.176755] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    1.176787] pcieport-driver 0000:00:1c.0: found MSI capability
[    1.176819] pci_express 0000:00:1c.0:pcie00: allocate port service
[    1.176849] pci_express 0000:00:1c.0:pcie02: allocate port service
[    1.176880] pci_express 0000:00:1c.0:pcie03: allocate port service
[    1.176958] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[    1.176990] pcieport-driver 0000:00:1c.1: found MSI capability
[    1.177025] pci_express 0000:00:1c.1:pcie00: allocate port service
[    1.177058] pci_express 0000:00:1c.1:pcie02: allocate port service
[    1.177087] pci_express 0000:00:1c.1:pcie03: allocate port service
[    1.177163] pcieport-driver 0000:00:1c.2: setting latency timer to 64
[    1.177195] pcieport-driver 0000:00:1c.2: found MSI capability
[    1.177227] pci_express 0000:00:1c.2:pcie00: allocate port service
[    1.177259] pci_express 0000:00:1c.2:pcie02: allocate port service
[    1.177288] pci_express 0000:00:1c.2:pcie03: allocate port service
[    1.177365] pcieport-driver 0000:00:1c.3: setting latency timer to 64
[    1.177397] pcieport-driver 0000:00:1c.3: found MSI capability
[    1.177429] pci_express 0000:00:1c.3:pcie00: allocate port service
[    1.177459] pci_express 0000:00:1c.3:pcie02: allocate port service
[    1.177490] pci_express 0000:00:1c.3:pcie03: allocate port service
[    1.177568] pcieport-driver 0000:00:1c.4: setting latency timer to 64
[    1.177600] pcieport-driver 0000:00:1c.4: found MSI capability
[    1.177632] pci_express 0000:00:1c.4:pcie00: allocate port service
[    1.177666] pci_express 0000:00:1c.4:pcie02: allocate port service
[    1.177695] pci_express 0000:00:1c.4:pcie03: allocate port service
[    1.177959] isapnp: Scanning for PnP cards...
[    1.530934] isapnp: No Plug & Play device found
[    1.557181] hpet_resources: 0xfed00000 is busy
[    1.557259] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.559015] brd: module loaded
[    1.559069] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.559166] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    1.561477] i8042.c: Detected active multiplexing controller, rev 1.1.
[    1.562413] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.562418] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    1.562420] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    1.562422] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    1.562424] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    1.562679] mice: PS/2 mouse device common for all mice
[    1.562778] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    1.562799] rtc0: alarms up to one month, y3k, hpet irqs
[    1.562901] EISA: Probing bus 0 at eisa.0
[    1.562926] EISA: Detected 0 cards.
[    1.562929] cpuidle: using governor ladder
[    1.562931] cpuidle: using governor menu
[    1.563338] TCP cubic registered
[    1.563360] Using IPI No-Shortcut mode
[    1.563495] registered taskstats version 1
[    1.563609]   Magic number: 9:779:343
[    1.563637] tty tty60: hash matches
[    1.563675] rtc_cmos 00:03: setting system clock to 2009-01-07 19:18:23 UTC (1231355903)
[    1.563678] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.563680] EDD information not available.
[    1.563884] Freeing unused kernel memory: 424k freed
[    1.563915] Write protecting the kernel text: 2576k
[    1.563936] Write protecting the kernel read-only data: 936k
[    1.595038] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    1.656741] fuse init (API version 7.9)
[    1.831938] ACPI: SSDT 7FFC63A0, 02C8 (r1  PmRef  Cpu0Ist     3000 INTL 20051117)
[    1.832412] ACPI: SSDT 7FFC6700, 0712 (r1  PmRef  Cpu0Cst     3001 INTL 20051117)
[    1.833438] Monitor-Mwait will be used to enter C-1 state
[    1.833441] Monitor-Mwait will be used to enter C-2 state
[    1.837110] ACPI: CPU0 (power states: C1[C1] C2[C2])
[    1.837153] processor ACPI0007:00: registered as cooling_device0
[    1.837157] ACPI: Processor [P001] (supports 8 throttling states)
[    1.837467] ACPI: SSDT 7FFC62D0, 00C8 (r1  PmRef  Cpu1Ist     3000 INTL 20051117)
[    1.837902] ACPI: SSDT 7FFC6670, 0085 (r1  PmRef  Cpu1Cst     3000 INTL 20051117)
[    1.839085] ACPI: CPU1 (power states: C1[C1] C2[C2])
[    1.839122] processor ACPI0007:01: registered as cooling_device1
[    1.839125] ACPI: Processor [P002] (supports 8 throttling states)
[    1.841139] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    1.845009] Marking TSC unstable due to TSC halts in idle
[    1.860579] thermal LNXTHERM:01: registered as thermal_zone0
[    1.861577] ACPI: Thermal Zone [THRM] (70 C)
[    2.105356] usbcore: registered new interface driver usbfs
[    2.105374] usbcore: registered new interface driver hub
[    2.105414] usbcore: registered new device driver usb
[    2.114382] USB Universal Host Controller Interface driver v3.0
[    2.114423] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.114433] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    2.114437] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    2.114468] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    2.114503] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000e080
[    2.114619] usb usb1: configuration #1 chosen from 1 choice
[    2.114640] hub 1-0:1.0: USB hub found
[    2.114646] hub 1-0:1.0: 2 ports detected
[    2.241664] No dock devices found.
[    2.254105] SCSI subsystem initialized
[    2.291402] libata version 3.00 loaded.
[    2.321229] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    2.321239] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    2.321244] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    2.321264] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
[    2.321302] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000e000
[    2.321380] usb usb2: configuration #1 chosen from 1 choice
[    2.321404] hub 2-0:1.0: USB hub found
[    2.321409] hub 2-0:1.0: 2 ports detected
[    2.425280] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.425294] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    2.425298] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    2.425319] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 3
[    2.429228] ehci_hcd 0000:00:1a.7: debug port 1
[    2.429234] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    2.429246] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xfebff400
[    2.440037] usb 1-1: new full speed USB device using uhci_hcd and address 2
[    2.449082] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    2.449180] usb usb3: configuration #1 chosen from 1 choice
[    2.449203] hub 3-0:1.0: USB hub found
[    2.449209] hub 3-0:1.0: 4 ports detected
[    2.508049] hub 1-0:1.0: unable to enumerate USB device on port 1
[    2.656527] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    2.656535] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    2.656538] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    2.656561] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 4
[    2.656589] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000dc00
[    2.656661] usb usb4: configuration #1 chosen from 1 choice
[    2.656683] hub 4-0:1.0: USB hub found
[    2.656689] hub 4-0:1.0: 2 ports detected
[    2.768194] usb 3-1: new high speed USB device using ehci_hcd and address 2
[    2.864380] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.864385] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    2.864388] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    2.864406] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 5
[    2.864431] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000d880
[    2.864498] usb usb5: configuration #1 chosen from 1 choice
[    2.864518] hub 5-0:1.0: USB hub found
[    2.864523] hub 5-0:1.0: 2 ports detected
[    2.913844] usb 3-1: configuration #1 chosen from 1 choice
[    2.968403] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.968409] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    2.968412] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    2.968430] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 6
[    2.968451] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000d800
[    2.968520] usb usb6: configuration #1 chosen from 1 choice
[    2.968542] hub 6-0:1.0: USB hub found
[    2.968547] hub 6-0:1.0: 2 ports detected
[    3.000185] Clocksource tsc unstable (delta = -244905065 ns)
[    3.024182] usb 3-2: new high speed USB device using ehci_hcd and address 3
[    3.156434] usb 3-2: config 1 interface 0 altsetting 0 endpoint 0x81 has an invalid bInterval 0, changing to 9
[    3.156437] usb 3-2: config 1 interface 0 altsetting 0 endpoint 0x2 has an invalid bInterval 0, changing to 9
[    3.157001] usb 3-2: configuration #1 chosen from 1 choice
[    3.176203] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    3.176215] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    3.176218] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.176237] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 7
[    3.180141] ehci_hcd 0000:00:1d.7: debug port 1
[    3.180147] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    3.180151] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfebff000
[    3.268196] usb 4-1: new low speed USB device using uhci_hcd and address 2
[    3.280180] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.280299] usb usb7: configuration #1 chosen from 1 choice
[    3.280342] hub 7-0:1.0: USB hub found
[    3.280355] hub 7-0:1.0: 6 ports detected
[    3.336210] hub 4-0:1.0: unable to enumerate USB device on port 1
[    3.489078] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    3.489092] r8169 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.489105] r8169 0000:02:00.0: setting latency timer to 64
[    3.489409] eth0: RTL8168b/8111b at 0xf8858000, 00:1e:8c:22:ca:48, XID 38000000 IRQ 217
[    3.490569] ahci 0000:00:1f.2: version 3.0
[    3.490580] ahci 0000:00:1f.2: PCI INT B -> GSI 20 (level, low) -> IRQ 20
[    3.490654] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0x7 impl SATA mode
[    3.490657] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part ems 
[    3.490661] ahci 0000:00:1f.2: setting latency timer to 64
[    3.491017] scsi0 : ahci
[    3.491119] scsi1 : ahci
[    3.491202] scsi2 : ahci
[    3.491327] ata1: SATA max UDMA/133 abar m2048@0xfebff800 port 0xfebff900 irq 216
[    3.491330] ata2: SATA max UDMA/133 abar m2048@0xfebff800 port 0xfebff980 irq 216
[    3.491333] ata3: SATA max UDMA/133 abar m2048@0xfebff800 port 0xfebffa00 irq 216
[    3.656315] usbcore: registered new interface driver hiddev
[    3.808197] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    3.809810] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 filtered out
[    3.810163] ata1.00: ACPI cmd ef/10:06:00:00:00:a0 succeeded
[    3.810169] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
[    3.811377] ata1.00: ATA-8: Hitachi HTS542525K9SA00, BBFOC31P, max UDMA/133
[    3.811382] ata1.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    3.813195] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 filtered out
[    3.813521] ata1.00: ACPI cmd ef/10:06:00:00:00:a0 succeeded
[    3.813526] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
[    3.814616] ata1.00: configured for UDMA/133
[    3.896195] usb 4-1: new low speed USB device using uhci_hcd and address 3
[    4.073309] usb 4-1: configuration #1 chosen from 1 choice
[    4.148186] ata2: SATA link down (SStatus 0 SControl 300)
[    4.312190] usb 6-2: new full speed USB device using uhci_hcd and address 2
[    4.484197] ata3: SATA link down (SStatus 0 SControl 300)
[    4.500322] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS54252 BBFO PQ: 0 ANSI: 5
[    4.500433] ahci 0000:07:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    4.516205] ahci 0000:07:00.0: AHCI 0001.0000 32 slots 1 ports 3 Gbps 0x1 impl SATA mode
[    4.516211] ahci 0000:07:00.0: flags: 64bit ncq pm led clo pmp pio slum part 
[    4.516220] ahci 0000:07:00.0: setting latency timer to 64
[    4.516402] scsi3 : ahci
[    4.516443] ata4: SATA max UDMA/133 abar m8192@0xfe9fe000 port 0xfe9fe100 irq 16
[    4.552654] usb 6-2: configuration #1 chosen from 1 choice
[    4.571952] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1d.0/usb4/4-1/4-1:1.0/input/input2
[    4.572146] input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.0-1
[    4.572165] usbcore: registered new interface driver usbhid
[    4.572168] usbhid: v2.6:USB HID core driver
[    4.836206] ata4: SATA link down (SStatus 0 SControl 300)
[    4.853342] ohci1394 0000:08:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    4.906014] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[16]  MMIO=[feaff800-feafffff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    4.910286] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[    4.914001] pata_acpi 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    4.914029] pata_acpi 0000:00:1f.1: setting latency timer to 64
[    4.914039] pata_acpi 0000:00:1f.1: PCI INT A disabled
[    4.917315] ata_piix 0000:00:1f.1: version 2.12
[    4.917322] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    4.917350] ata_piix 0000:00:1f.1: setting latency timer to 64
[    4.917833] scsi4 : ata_piix
[    4.918083] scsi5 : ata_piix
[    4.918724] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    4.918726] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    4.924084] Driver 'sd' needs updating - please use bus_type methods
[    4.924161] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[    4.924177] sd 0:0:0:0: [sda] Write Protect is off
[    4.924179] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.924205] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.924267] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[    4.924281] sd 0:0:0:0: [sda] Write Protect is off
[    4.924284] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.924310] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.924313]  sda: sda1 sda2 < sda5 sda6 sda7 >
[    5.002064] sd 0:0:0:0: [sda] Attached SCSI disk
[    5.080518] ata5.00: ATAPI: HL-DT-ST DVDRAM GSA-T20L, NR02, max UDMA/33
[    5.096446] ata5.00: configured for UDMA/33
[    5.096512] ata6: port disabled. ignoring.
[    5.100258] scsi 4:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-T20L  NR02 PQ: 0 ANSI: 5
[    5.100364] scsi 4:0:0:0: Attached scsi generic sg1 type 5
[    5.119795] Driver 'sr' needs updating - please use bus_type methods
[    5.131281] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    5.131284] Uniform CD-ROM driver Revision: 3.20
[    5.131352] sr 4:0:0:0: Attached scsi CD-ROM sr0
[    5.351834] PM: Starting manual resume from disk
[    5.351838] PM: Resume from partition 8:7
[    5.351839] PM: Checking hibernation image.
[    5.352019] PM: Resume from disk failed.
[    5.395109] kjournald starting.  Commit interval 5 seconds
[    5.395136] EXT3-fs: mounted filesystem with ordered data mode.
[    6.180503] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00e0180003b7cb39]
[   11.522655] udevd version 124 started
[   11.769058] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   11.823004] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   11.858957] Linux agpgart interface v0.103
[   11.923565] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[   11.940028] ACPI: Power Button (FF) [PWRF]
[   11.940149] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input4
[   11.972036] ACPI: Sleep Button (CM) [SLPB]
[   11.972094] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input5
[   11.973690] ACPI: Lid Switch [LID]
[   12.069436] asus-laptop: Asus Laptop Support version 0.42
[   12.073640] asus-laptop:   G1S model detected
[   12.077061] Registered led device: asus::mail
[   12.077088] Registered led device: asus::touchpad
[   12.077113] Registered led device: asus::gaming
[   12.077352] ACPI: AC Adapter [AC0] (on-line)
[   12.123906] ACPI: Battery Slot [BAT0] (battery present)
[   12.302707] acpi device:07: registered as cooling_device2
[   12.302867] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:02/device:03/input/input6
[   12.332047] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   12.534585] Linux video capture interface: v2.00
[   12.677817] iTCO_vendor_support: vendor-support=0
[   12.857883] uvcvideo: Found UVC 1.00 device USB2.0 1.3M UVC WebCam  (04f2:b012)
[   12.868050] input: USB2.0 1.3M UVC WebCam  as /devices/pci0000:00/0000:00:1a.7/usb3/3-1/3-1:1.0/input/input7
[   12.868091] usbcore: registered new interface driver uvcvideo
[   12.868094] USB Video Class driver (v0.1.0)
[   12.890954] Bluetooth: Core ver 2.13
[   12.891218] NET: Registered protocol family 31
[   12.891220] Bluetooth: HCI device and connection manager initialized
[   12.891223] Bluetooth: HCI socket layer initialized
[   12.994164] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.03 (30-Apr-2008)
[   13.004043] iTCO_wdt: failed to reset NO_REBOOT flag, reboot disabled by hardware
[   13.004456] iTCO_wdt: No card detected
[   13.008081] input: PC Speaker as /devices/platform/pcspkr/input/input8
[   13.028477] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27ks
[   13.028480] iwlagn: Copyright(c) 2003-2008 Intel Corporation
[   13.028540] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   13.028548] iwlagn 0000:03:00.0: setting latency timer to 64
[   13.028567] iwlagn: Detected Intel Wireless WiFi Link 4965AGN REV=0x4
[   13.072680] iwlagn: Tunable channels: 13 802.11bg, 19 802.11a channels
[   13.075136] iwlagn 0000:03:00.0: PCI INT A disabled
[   13.075460] phy0: Selected rate control algorithm 'iwl-agn-rs'
[   13.096606] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   13.096634] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   13.123325] Bluetooth: Generic Bluetooth USB driver ver 0.3
[   13.124194] usbcore: registered new interface driver btusb
[   13.132784] sdhci: Secure Digital Host Controller Interface driver
[   13.132787] sdhci: Copyright(c) Pierre Ossman
[   13.205113] sdhci-pci 0000:08:01.1: SDHCI controller found [1180:0822] (rev 22)
[   13.205127] sdhci-pci 0000:08:01.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   13.208198] mmc0: SDHCI controller on PCI [0000:08:01.1] using PIO
[   13.667249] Synaptics Touchpad, model: 1, fw: 6.1, id: 0xa3a0b3, caps: 0xa04713/0x10008
[   13.708390] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input9
[   13.774306] NET: Registered protocol family 10
[   13.774715] lo: Disabled Privacy Extensions
[   14.451476] loop: module loaded
[   14.486781] lp: driver loaded but no devices found
[   14.651478] Adding 4192924k swap on /dev/sda7.  Priority:-1 extents:1 across:4192924k
[   15.183714] EXT3 FS on sda6, internal journal
[   16.119386] type=1505 audit(1231352317.756:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4498
[   16.250436] type=1505 audit(1231352317.888:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4503
[   16.250586] type=1505 audit(1231352317.888:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4503
[   16.450548] ip_tables: (C) 2000-2006 Netfilter Core Team
[   16.484154] r8169: eth0: link down
[   16.484320] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   17.200779] ACPI: WMI: Mapper loaded
[   17.774689] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   17.819107] apm: BIOS not found.
[   17.975997] ppdev: user-space parallel port driver
[   19.673828] Bluetooth: L2CAP ver 2.11
[   19.673842] Bluetooth: L2CAP socket layer initialized
[   19.712125] Bluetooth: SCO (Voice Link) ver 0.6
[   19.712139] Bluetooth: SCO socket layer initialized
[   19.743024] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   19.743037] Bluetooth: BNEP filters: protocol multicast
[   19.796666] Bridge firewalling registered
[   19.796914] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.
[   19.841658] Bluetooth: RFCOMM socket layer initialized
[   19.841682] Bluetooth: RFCOMM TTY layer initialized
[   19.841689] Bluetooth: RFCOMM ver 1.10
[   21.731780] mtrr: base(0xe0000000) is not aligned on a size(0xff00000) boundary
[   24.009295] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   24.009391] iwlagn 0000:03:00.0: restoring config space at offset 0x1 (was 0x100102, writing 0x100106)
[   24.011555] firmware: requesting iwlwifi-4965-2.ucode
[   24.300686] Registered led device: iwl-phy0:radio
[   24.301540] Registered led device: iwl-phy0:assoc
[   24.302312] Registered led device: iwl-phy0:RX
[   24.303050] Registered led device: iwl-phy0:TX
[   24.331949] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   24.396779] NET: Registered protocol family 17
[   50.164203] CPU0 attaching NULL sched-domain.
[   50.164222] CPU1 attaching NULL sched-domain.
[   50.176150] CPU0 attaching sched-domain:
[   50.176162]  domain 0: span 0-1 level MC
[   50.176169]   groups: 0 1
[   50.176182] CPU1 attaching sched-domain:
[   50.176187]  domain 0: span 0-1 level MC
[   50.176193]   groups: 1 0
[   51.114743] wlan0: authenticate with AP 00:1f:9f:50:31:0d
[   51.116572] wlan0: authenticated
[   51.116585] wlan0: associate with AP 00:1f:9f:50:31:0d
[   51.119531] wlan0: RX AssocResp from 00:1f:9f:50:31:0d (capab=0x411 status=0 aid=1)
[   51.119542] wlan0: associated
[   51.126839] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   61.296203] wlan0: no IPv6 routers present
[  115.352292] type=1503 audit(1231352416.988:5): operation="inode_permission" requested_mask="r::" denied_mask="r::" fsuid=7 name="/proc/6116/net/" pid=6116 profile="/usr/sbin/cupsd"
[  116.412701] type=1503 audit(1231352418.051:6): operation="inode_permission" requested_mask="r::" denied_mask="r::" fsuid=7 name="/proc/6120/net/" pid=6120 profile="/usr/sbin/cupsd"
[  116.412769] type=1503 audit(1231352418.051:7): operation="socket_create" family="ax25" sock_type="dgram" protocol=0 pid=6120 profile="/usr/sbin/cupsd"
[  116.412784] type=1503 audit(1231352418.051:8): operation="socket_create" family="netrom" sock_type="seqpacket" protocol=0 pid=6120 profile="/usr/sbin/cupsd"
[  116.412803] type=1503 audit(1231352418.051:9): operation="socket_create" family="rose" sock_type="dgram" protocol=0 pid=6120 profile="/usr/sbin/cupsd"
[  116.412817] type=1503 audit(1231352418.051:10): operation="socket_create" family="ipx" sock_type="dgram" protocol=0 pid=6120 profile="/usr/sbin/cupsd"
[  116.412836] type=1503 audit(1231352418.051:11): operation="socket_create" family="appletalk" sock_type="dgram" protocol=0 pid=6120 profile="/usr/sbin/cupsd"
[  116.412851] type=1503 audit(1231352418.051:12): operation="socket_create" family="econet" sock_type="dgram" protocol=0 pid=6120 profile="/usr/sbin/cupsd"
[  116.412865] type=1503 audit(1231352418.051:13): operation="socket_create" family="ash" sock_type="dgram" protocol=0 pid=6120 profile="/usr/sbin/cupsd"
[  116.412880] type=1503 audit(1231352418.051:14): operation="socket_create" family="x25" sock_type="seqpacket" protocol=0 pid=6120 profile="/usr/sbin/cupsd"
[  987.285221] r8169: eth0: link down
[  987.286006] ADDRCONF(NETDEV_UP): eth0: link is not ready
```


6.
$ sudo lshw -C network
```

 *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:1e:8c:22:ca:48
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half ip=192.168.1.68 latency=0 link=no module=r8169 multicast=yes port=twisted pair
  *-network
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 61
       serial: 00:13:e8:f6:a0:87
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn ip=192.168.1.64 latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 22:29:56:5a:61:3e
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```

7.
$ iwlist scan
```

wlan0     Scan completed :
          Cell 01 - Address: 00:1F:9F:50:31:0D
                    ESSID:"TeliaGateway00-1F-9F-50-31-0D"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=80/100  Signal level:-51 dBm  Noise level=-83 dBm
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=0000000086f7918b
                    Extra: Last beacon: 48ms ago
```

8.
$ lsb_release -d
```

Description:	Ubuntu 8.10
```

9.
$ uname -mr
```

2.6.27-7-generic i686
```

10.
$ sudo /etc/init.d/networking restart
```

 * Reconfiguring network interfaces...                                                                      Ignoring unknown interface wlan0=wlan0.
```

---

### Post by dresi on 2009-01-07
I gave up and did a reinstall.... for some reason that cleared my problem.

I find it odd since I did everything the same. But anyway, fixed.

---

