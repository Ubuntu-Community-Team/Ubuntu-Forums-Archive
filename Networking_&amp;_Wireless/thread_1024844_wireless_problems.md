---
title: "wireless problems"
date: 2008-12-29
forum: Networking &amp; Wireless
---

### Post by brummy on 2008-12-29
hi guys im having problems getting my wireless to work on ubuntu 8.10

i have installed ndiswrapper and put my wireless inf file in it but it still wont work

i have a packard bell EASYNOTE MX37-U-041

any help would be appreciated

cheers brummy

---

### Post by brummy on 2008-12-30
please help really frustraing not having wirless

---

### Post by ieee488 on 2008-12-30
You making a big assumption that ndiswrapper will work.

I'd suggest reading the Sticky posts at the top of the 1st page of this Networking forum.

---

### Post by brummy on 2008-12-30
hi following the steps in the sticky and this is where i get to, does any one know what all this means, it say at the bottom that it cannot load the driver cheers



brummy@brummy-laptop:~$ dmesg | grep -e ndis -e wlan
[   12.361130] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[   13.144626] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'KeInitializeGuardedMutex'
[   13.144639] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'KeReleaseGuardedMutex'
[   13.144649] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'KeAcquireGuardedMutex'
[   13.144744] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateMdl'
[   13.144755] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisRetreatNetBufferDataStart'
[   13.144766] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSynchronizeWithInterruptEx'
[   13.144776] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeMdl'
[   13.144803] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisOpenConfigurationEx'
[   13.144817] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMAllocateNetBufferSGList'
[   13.144828] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSendNetBufferListsComplete'
[   13.144838] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMFreeNetBufferSGList'
[   13.144849] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterScatterGatherDma'
[   13.144865] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSetBusData'
[   13.144876] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMGetBusData'
[   13.144891] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAdvanceNetBufferDataStart'
[   13.144906] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateMemoryWithTagPriority'
[   13.144920] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeIoWorkItem'
[   13.144930] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateIoWorkItem'
[   13.144950] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterInterruptEx'
[   13.144961] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMResetComplete'
[   13.144998] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterMiniportDriver'
[   13.145009] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterMiniportDriver'
[   13.145019] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisQueueIoWorkItem'
[   13.145030] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterInterruptEx'
[   13.145051] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSetMiniportAttributes'
[   13.145065] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMIndicateStatusEx'
[   13.145075] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMOidRequestComplete'
[   13.145086] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisGetSystemUpTimeEx'
[   13.145096] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferList'
[   13.145107] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferList'
[   13.145122] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBuffer'
[   13.145132] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBuffer'
[   13.145147] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferPool'
[   13.145157] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferListPool'
[   13.145168] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferPool'
[   13.145178] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferListPool'
[   13.145189] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMIndicateReceiveNetBufferLists'
[   13.145200] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterScatterGatherDma'
[   13.145206] ndiswrapper (load_sys_files:206): couldn't prepare driver 'netathr'
[   13.145912] ndiswrapper (load_wrap_driver:108): couldn't load driver netathr; check system log for messages from 'loadndisdriver'
[   13.146017] usbcore: registered new interface driver ndiswrapper
brummy@brummy-laptop:~$

---

### Post by ieee488 on 2008-12-30
Do the steps in the 2nd Sticky *only* first, and report back.

---

### Post by brummy on 2008-12-30
ok here it is

**_Machine Brand and Model_** 
packard bell easynote EASYNOTE MX37-U-041 

_**wireles brand, model, chipset**_ 
root@brummy-laptop:~#  lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 671MX
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS968 [MuTIOL Media IO] (rev 01)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter (rev 02)
00:05.0 IDE interface: Silicon Integrated Systems [SiS] SATA Controller / IDE mode (rev 03)
00:06.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:07.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:0f.0 Audio device: Silicon Integrated Systems [SiS] Azalia Audio Controller
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter (rev 10)
02:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

_**ifconfig**_
root@brummy-laptop:~# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1f:c6:03:e6:47  
          inet addr:192.168.0.6  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:c6ff:fe03:e647/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4277 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3941 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4556660 (4.5 MB)  TX bytes:617443 (617.4 KB)
          Interrupt:19 Base address:0xdead 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:376 (376.0 B)  TX bytes:376 (376.0 B)

_**iwconfig**_
root@brummy-laptop:~# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

_**iwconfig wlan0**_
root@brummy-laptop:~# iwconfig wlan0
wlan0     No such device

**_Check for modules:_**
root@brummy-laptop:~# lsmod
Module                  Size  Used by
ipv6                  263972  14 
af_packet              25728  2 
binfmt_misc            16904  1 
rfcomm                 44432  0 
sco                    18308  2 
bridge                 56980  0 
stp                    10628  1 bridge
bnep                   20480  2 
l2cap                  30464  6 rfcomm,bnep
bluetooth              61924  6 rfcomm,sco,bnep,l2cap
ppdev                  15620  0 
acpi_cpufreq           15500  1 
cpufreq_powersave       9856  0 
cpufreq_userspace      11396  0 
cpufreq_conservative    14600  0 
cpufreq_stats          13188  0 
cpufreq_ondemand       14988  1 
freq_table             12672  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
pci_slot               12680  0 
wmi                    14504  0 
container              11520  0 
sbs                    19464  0 
sbshc                  13440  1 sbs
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
parport_pc             39204  0 
lp                     17156  0 
parport                42604  3 ppdev,parport_pc,lp
joydev                 18368  0 
snd_hda_intel         384176  3 
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm                83204  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10884  0 
snd_seq_oss            38528  0 
snd_seq_midi           14336  0 
snd_rawmidi            29824  1 snd_seq_midi
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29960  2 snd_pcm,snd_seq
video                  25232  0 
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
asus_laptop            24568  0 
psmouse                45200  0 
output                 11008  1 video
ndiswrapper           196380  0 
battery                18436  0 
sis190                 25476  0 
evdev                  17696  10 
ac                     12292  0 
snd                    63268  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw              13444  0 
sis_agp                15232  1 
button                 14224  0 
led_class              12164  1 asus_laptop
pcspkr                 10624  0 
soundcore              15328  1 snd
agpgart                42184  1 sis_agp
mii                    13440  1 sis190
shpchp                 38036  0 
pci_hotplug            34976  1 shpchp
snd_page_alloc         16136  2 snd_hda_intel,snd_pcm
ext3                  133256  1 
jbd                    55828  1 ext3
mbcache                16004  1 ext3
sd_mod                 42392  3 
crc_t10dif              9984  1 sd_mod
sr_mod                 22212  0 
cdrom                  43168  1 sr_mod
sg                     39732  0 
sata_sis               13444  2 
ata_generic            12932  0 
ohci_hcd               32016  0 
ehci_hcd               43788  0 
pata_acpi              12160  0 
pata_sis               18436  1 sata_sis
usbcore               149360  4 ndiswrapper,ohci_hcd,ehci_hcd
libata                178208  4 sata_sis,ata_generic,pata_acpi,pata_sis
scsi_mod              155212  4 sd_mod,sr_mod,sg,libata
dock                   16656  1 libata
thermal                23708  0 
processor              42156  4 acpi_cpufreq,thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  3 

**_kernal boot msgs_**
 0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 60000000 (gap: 58000000:a6e00000)
[    0.000000] PERCPU: Allocating 41628 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 4, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 357079
[    0.000000] Kernel command line: root=UUID=b5e8c466-40a7-42dd-a9e0-9f6120f14a95 ro quiet splash 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] TSC: Unable to calibrate against PIT
[    0.000000] TSC: using PMTIMER reference calibration
[    0.000000] Detected 1599.536 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] Memory: 1413532k/1441440k available (2576k kernel code, 26592k reserved, 1165k data, 424k init, 523936k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xf8800000 - 0xff3fe000   ( 107 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[    0.004000]       .init : 0xc04ad000 - 0xc0517000   ( 424 kB)
[    0.004000]       .data : 0xc03840da - 0xc04a7680   (1165 kB)
[    0.004000]       .text : 0xc0100000 - 0xc03840da   (2576 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.004000] hpet clockevent registered
[    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 3199.07 BogoMIPS (lpj=6398144)
[    0.004000] Security Framework initialized
[    0.004000] SELinux:  Disabled at boot.
[    0.004000] AppArmor: AppArmor initialized
[    0.004000] Mount-cache hash table entries: 512
[    0.004000] Initializing cgroup subsys ns
[    0.004000] Initializing cgroup subsys cpuacct
[    0.004000] Initializing cgroup subsys memory
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 1024K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 0
[    0.004000] using mwait in idle threads.
[    0.004000] Checking 'hlt' instruction... OK.
[    0.018445] ACPI: Core revision 20080609
[    0.024533] ACPI: Checking initramfs for custom DSDT
[    0.456196] ENABLING IO-APIC IRQs
[    0.456370] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.497961] CPU0: Intel(R) Pentium(R) Dual  CPU  T2330  @ 1.60GHz stepping 0d
[    0.500031] Booting processor 1/1 ip 6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 3199.06 BogoMIPS (lpj=6398124)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 1024K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.584555] CPU1: Intel(R) Pentium(R) Dual  CPU  T2330  @ 1.60GHz stepping 0d
[    0.584577] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.588058] Brought up 2 CPUs
[    0.588062] Total of 2 processors activated (6398.13 BogoMIPS).
[    0.588089] CPU0 attaching sched-domain:
[    0.588092]  domain 0: span 0-1 level MC
[    0.588096]   groups: 0 1
[    0.588104] CPU1 attaching sched-domain:
[    0.588107]  domain 0: span 0-1 level MC
[    0.588110]   groups: 1 0
[    0.588214] net_namespace: 840 bytes
[    0.588214] Booting paravirtualized kernel on bare hardware
[    0.588355] Time: 17:22:30  Date: 12/30/08
[    0.588390] NET: Registered protocol family 16
[    0.588415] EISA bus registered
[    0.588415] ACPI: bus type pci registered
[    0.588415] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.588415] PCI: Not using MMCONFIG.
[    0.589350] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=5
[    0.589353] PCI: Using configuration type 1 for base access
[    0.593594] ACPI: EC: EC description table is found, configuring boot EC
[    0.610554] ACPI: Interpreter enabled
[    0.610562] ACPI: (supports S0 S3 S4 S5)
[    0.610586] ACPI: Using IOAPIC for interrupt routing
[    0.610734] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.615325] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
[    0.615328] PCI: Using MMCONFIG for extended config space
[    0.624310] ACPI: EC: GPE = 0x19, I/O: command/status = 0x66, data = 0x62
[    0.624314] ACPI: EC: driver started in poll mode
[    0.624359] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.624359] PCI: 0000:00:00.0 reg 10 32bit mmio: [f0000000, f7ffffff]
[    0.624359] PCI: 0000:00:02.5 reg 20 io port: [ffe0, ffef]
[    0.624359] pci 0000:00:02.5: PME# supported from D3cold
[    0.624359] pci 0000:00:02.5: PME# disabled
[    0.624359] PCI: 0000:00:03.0 reg 10 32bit mmio: [fddff000, fddfffff]
[    0.624385] PCI: 0000:00:03.1 reg 10 32bit mmio: [fddfe000, fddfefff]
[    0.624467] PCI: 0000:00:03.3 reg 10 32bit mmio: [fddfd000, fddfdfff]
[    0.624520] pci 0000:00:03.3: PME# supported from D0 D3hot D3cold
[    0.624526] pci 0000:00:03.3: PME# disabled
[    0.624565] PCI: 0000:00:04.0 reg 10 32bit mmio: [fddfcc00, fddfcc7f]
[    0.624573] PCI: 0000:00:04.0 reg 14 io port: [cc00, cc7f]
[    0.624618] pci 0000:00:04.0: supports D1
[    0.624620] pci 0000:00:04.0: supports D2
[    0.624623] pci 0000:00:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.624628] pci 0000:00:04.0: PME# disabled
[    0.624661] PCI: 0000:00:05.0 reg 10 io port: [c800, c807]
[    0.624669] PCI: 0000:00:05.0 reg 14 io port: [c400, c403]
[    0.624678] PCI: 0000:00:05.0 reg 18 io port: [c000, c007]
[    0.624686] PCI: 0000:00:05.0 reg 1c io port: [bc00, bc03]
[    0.624694] PCI: 0000:00:05.0 reg 20 io port: [b800, b80f]
[    0.624703] PCI: 0000:00:05.0 reg 24 io port: [b400, b47f]
[    0.624727] pci 0000:00:05.0: PME# supported from D3cold
[    0.624732] pci 0000:00:05.0: PME# disabled
[    0.624811] pci 0000:00:06.0: PME# supported from D0 D3hot D3cold
[    0.624816] pci 0000:00:06.0: PME# disabled
[    0.624892] pci 0000:00:07.0: PME# supported from D0 D3hot D3cold
[    0.624898] pci 0000:00:07.0: PME# disabled
[    0.624942] PCI: 0000:00:0f.0 reg 10 32bit mmio: [fddf4000, fddf7fff]
[    0.624994] pci 0000:00:0f.0: PME# supported from D0 D3hot D3cold
[    0.624999] pci 0000:00:0f.0: PME# disabled
[    0.625066] PCI: 0000:01:00.0 reg 10 32bit mmio: [c0000000, cfffffff]
[    0.625074] PCI: 0000:01:00.0 reg 14 32bit mmio: [fdee0000, fdefffff]
[    0.625081] PCI: 0000:01:00.0 reg 18 io port: [dc00, dc7f]
[    0.625114] pci 0000:01:00.0: supports D1
[    0.625116] pci 0000:01:00.0: supports D2
[    0.625158] PCI: bridge 0000:00:01.0 io port: [d000, dfff]
[    0.625163] PCI: bridge 0000:00:01.0 32bit mmio: [fde00000, fdefffff]
[    0.625168] PCI: bridge 0000:00:01.0 32bit mmio pref: [c0000000, cfffffff]
[    0.625243] PCI: 0000:02:00.0 reg 10 64bit mmio: [fdff0000, fdffffff]
[    0.625381] PCI: bridge 0000:00:06.0 32bit mmio: [fdf00000, fdffffff]
[    0.625453] PCI: bridge 0000:00:07.0 io port: [e000, efff]
[    0.625458] PCI: bridge 0000:00:07.0 32bit mmio: [fe000000, febfffff]
[    0.625467] PCI: bridge 0000:00:07.0 64bit mmio pref: [de000000, dfffffff]
[    0.625488] bus 00 -> node 0
[    0.625499] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.636928] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 *10 11 12 14 15)
[    0.636928] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 *7 10 11 12 14 15)
[    0.636928] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 *4 5 7 10 11 12 14 15)
[    0.636938] ACPI: PCI Interrupt Link [LNKD] (IRQs *3 4 5 7 10 11 12 14 15)
[    0.637169] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 *11 12 14 15)
[    0.637399] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 *5 7 10 11 12 14 15)
[    0.637629] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 11 12 14 *15)
[    0.637860] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.640212] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.640227] pnp: PnP ACPI init
[    0.640227] ACPI: bus type pnp registered
[    0.644082] pnp: PnP ACPI: found 12 devices
[    0.644085] ACPI: ACPI bus type pnp unregistered
[    0.644090] PnPBIOS: Disabled by ACPI PNP
[    0.644113] PCI: Using ACPI for IRQ routing
[    0.648046] NET: Registered protocol family 8
[    0.648049] NET: Registered protocol family 20
[    0.648069] NetLabel: Initializing
[    0.648069] NetLabel:  domain hash size = 128
[    0.648069] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.648077] NetLabel:  unlabeled traffic allowed by default
[    0.648085] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.648092] hpet0: 3 32-bit timers, 14318180 Hz
[    0.650286] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    0.650290]    actual entries 65620
[    0.650431] AppArmor: AppArmor Filesystem Enabled
[    0.650456] ACPI: RTC can wake from S4
[    0.652044] Switched to high resolution mode on CPU 0
[    0.652598] Switched to high resolution mode on CPU 1
[    0.655954] system 00:06: ioport range 0x290-0x297 has been reserved
[    0.655958] system 00:06: ioport range 0xc00-0xc05 has been reserved
[    0.655961] system 00:06: ioport range 0xd00-0xd05 has been reserved
[    0.655965] system 00:06: ioport range 0x480-0x48f has been reserved
[    0.655969] system 00:06: ioport range 0x4d0-0x4d1 has been reserved
[    0.655972] system 00:06: ioport range 0x800-0x87f has been reserved
[    0.655976] system 00:06: ioport range 0x880-0x8ff has been reserved
[    0.655979] system 00:06: ioport range 0xc00-0xc7f could not be reserved
[    0.655983] system 00:06: ioport range 0x2000-0x20fe has been reserved
[    0.655989] system 00:06: iomem range 0xfff80000-0xffffffff has been reserved
[    0.655993] system 00:06: iomem range 0xffb80000-0xffbfffff has been reserved
[    0.655996] system 00:06: iomem range 0xffee0000-0xffefffff has been reserved
[    0.656006] system 00:06: iomem range 0xfed10000-0xfed3ffff has been reserved
[    0.656017] system 00:09: ioport range 0x250-0x253 has been reserved
[    0.656020] system 00:09: ioport range 0x256-0x25f has been reserved
[    0.656024] system 00:09: iomem range 0xfec00000-0xfec00fff has been reserved
[    0.656028] system 00:09: iomem range 0xfee00000-0xfee00fff could not be reserved
[    0.656036] system 00:0a: iomem range 0xe0000000-0xefffffff has been reserved
[    0.656044] system 00:0b: iomem range 0x0-0x9ffff could not be reserved
[    0.656048] system 00:0b: iomem range 0xc0000-0xcffff could not be reserved
[    0.656051] system 00:0b: iomem range 0xe0000-0xfffff could not be reserved
[    0.656055] system 00:0b: iomem range 0x100000-0x57ffffff could not be reserved
[    0.656059] system 00:0b: iomem range 0xe0000000-0xffffffff could not be reserved
[    0.691264] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.691269] pci 0000:00:01.0:   IO window: 0xd000-0xdfff
[    0.691276] pci 0000:00:01.0:   MEM window: 0xfde00000-0xfdefffff
[    0.691282] pci 0000:00:01.0:   PREFETCH window: 0x000000c0000000-0x000000cfffffff
[    0.691290] pci 0000:00:06.0: PCI bridge, secondary bus 0000:02
[    0.691293] pci 0000:00:06.0:   IO window: disabled
[    0.691300] pci 0000:00:06.0:   MEM window: 0xfdf00000-0xfdffffff
[    0.691305] pci 0000:00:06.0:   PREFETCH window: disabled
[    0.691313] pci 0000:00:07.0: PCI bridge, secondary bus 0000:03
[    0.691317] pci 0000:00:07.0:   IO window: 0xe000-0xefff
[    0.691324] pci 0000:00:07.0:   MEM window: 0xfe000000-0xfebfffff
[    0.691329] pci 0000:00:07.0:   PREFETCH window: 0x000000de000000-0x000000dfffffff
[    0.691348] pci 0000:00:01.0: setting latency timer to 64
[    0.691360] pci 0000:00:06.0: setting latency timer to 64
[    0.691372] pci 0000:00:07.0: setting latency timer to 64
[    0.691377] bus: 00 index 0 io port: [0, ffff]
[    0.691380] bus: 00 index 1 mmio: [0, ffffffff]
[    0.691383] bus: 01 index 0 io port: [d000, dfff]
[    0.691386] bus: 01 index 1 mmio: [fde00000, fdefffff]
[    0.691389] bus: 01 index 2 mmio: [c0000000, cfffffff]
[    0.691391] bus: 01 index 3 mmio: [0, 0]
[    0.691394] bus: 02 index 0 mmio: [0, 0]
[    0.691396] bus: 02 index 1 mmio: [fdf00000, fdffffff]
[    0.691399] bus: 02 index 2 mmio: [0, 0]
[    0.691401] bus: 02 index 3 mmio: [0, 0]
[    0.691404] bus: 03 index 0 io port: [e000, efff]
[    0.691406] bus: 03 index 1 mmio: [fe000000, febfffff]
[    0.691409] bus: 03 index 2 mmio: [de000000, dfffffff]
[    0.691412] bus: 03 index 3 mmio: [0, 0]
[    0.691425] NET: Registered protocol family 2
[    0.704073] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.704413] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.705211] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.705803] TCP: Hash tables configured (established 131072 bind 65536)
[    0.705809] TCP reno registered
[    0.709397] NET: Registered protocol family 1
[    0.709583] checking if image is initramfs... it is
[    1.580925] Freeing initrd memory: 8016k freed
[    1.581505] Simple Boot Flag at 0x71 set to 0x1
[    1.582527] audit: initializing netlink socket (disabled)
[    1.582569] type=2000 audit(1230657750.580:1): initialized
[    1.589967] highmem bounce pool size: 64 pages
[    1.589976] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.592802] VFS: Disk quotas dquot_6.5.1
[    1.592909] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.593053] msgmni has been set to 1754
[    1.593215] io scheduler noop registered
[    1.593219] io scheduler anticipatory registered
[    1.593223] io scheduler deadline registered
[    1.593239] io scheduler cfq registered (default)
[    1.652040] pci 0000:01:00.0: Boot video device
[    1.652185] pcieport-driver 0000:00:06.0: setting latency timer to 64
[    1.652251] pcieport-driver 0000:00:06.0: found MSI capability
[    1.652303] pci_express 0000:00:06.0:pcie00: allocate port service
[    1.652439] pcieport-driver 0000:00:07.0: setting latency timer to 64
[    1.652506] pcieport-driver 0000:00:07.0: found MSI capability
[    1.652554] pci_express 0000:00:07.0:pcie00: allocate port service
[    1.652941] isapnp: Scanning for PnP cards...
[    2.006433] isapnp: No Plug & Play device found
[    2.046032] hpet_resources: 0xfed00000 is busy
[    2.046154] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    2.049054] brd: module loaded
[    2.049142] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    2.049299] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    2.051573] i8042.c: Detected active multiplexing controller, rev 1.1.
[    2.052198] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.052206] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    2.052209] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    2.052212] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    2.052215] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    2.052656] mice: PS/2 mouse device common for all mice
[    2.052826] rtc_cmos 00:08: rtc core: registered rtc_cmos as rtc0
[    2.052852] rtc0: alarms up to one year, hpet irqs
[    2.052995] EISA: Probing bus 0 at eisa.0
[    2.053008] Cannot allocate resource for EISA slot 2
[    2.053034] EISA: Detected 0 cards.
[    2.053038] cpuidle: using governor ladder
[    2.053042] cpuidle: using governor menu
[    2.053701] TCP cubic registered
[    2.053743] Using IPI No-Shortcut mode
[    2.053983] registered taskstats version 1
[    2.054121]   Magic number: 4:917:391
[    2.054306] rtc_cmos 00:08: setting system clock to 2008-12-30 17:22:32 UTC (1230657752)
[    2.054311] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.054313] EDD information not available.
[    2.054609] Freeing unused kernel memory: 424k freed
[    2.054656] Write protecting the kernel text: 2580k
[    2.054690] Write protecting the kernel read-only data: 940k
[    2.086204] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    2.264309] fuse init (API version 7.9)
[    2.328675] ACPI: SSDT 57FBE390, 0244 (r1  PmRef  Cpu0Ist     3000 INTL 20051117)
[    2.329301] ACPI: SSDT 57FBE670, 05FF (r1  PmRef  Cpu0Cst     3001 INTL 20051117)
[    2.330054] Monitor-Mwait will be used to enter C-1 state
[    2.330058] Monitor-Mwait will be used to enter C-2 state
[    2.330251] ACPI: CPU0 (power states: C1[C1] C2[C2])
[    2.330324] processor ACPI0007:00: registered as cooling_device0
[    2.330817] ACPI: SSDT 57FBE2C0, 00C8 (r1  PmRef  Cpu1Ist     3000 INTL 20051117)
[    2.331376] ACPI: SSDT 57FBE5E0, 0085 (r1  PmRef  Cpu1Cst     3000 INTL 20051117)
[    2.332311] Marking TSC unstable due to TSC halts in idle
[    2.332436] ACPI: CPU1 (power states: C1[C1] C2[C2])
[    2.332498] processor ACPI0007:01: registered as cooling_device1
[    2.335641] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    2.337697] thermal LNXTHERM:01: registered as thermal_zone0
[    2.338814] ACPI: Thermal Zone [THRM] (59 C)
[    2.738678] No dock devices found.
[    2.767946] SCSI subsystem initialized
[    2.836530] libata version 3.00 loaded.
[    2.892826] usbcore: registered new interface driver usbfs
[    2.892865] usbcore: registered new interface driver hub
[    2.928810] usbcore: registered new device driver usb
[    2.936685] pata_sis 0000:00:02.5: version 0.5.2
[    2.936853] scsi0 : pata_sis
[    2.939132] scsi1 : pata_sis
[    2.940010] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xffe0 irq 14
[    2.940015] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xffe8 irq 15
[    3.052618] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[    3.112829] ata1.00: ATAPI: MATSHITADVD-RAM UJ870PC, 1.00, max UDMA/33
[    3.132838] ata1.00: configured for UDMA/33
[    3.132908] ata2: port disabled. ignoring.
[    3.135060] scsi 0:0:0:0: CD-ROM            MATSHITA DVD-RAM UJ870PC  1.00 PQ: 0 ANSI: 5
[    3.135274] ohci_hcd 0000:00:03.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    3.135299] ohci_hcd 0000:00:03.0: OHCI Host Controller
[    3.135367] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 1
[    3.135396] ohci_hcd 0000:00:03.0: irq 20, io mem 0xfddff000
[    3.190746] usb usb1: configuration #1 chosen from 1 choice
[    3.190797] hub 1-0:1.0: USB hub found
[    3.190811] hub 1-0:1.0: 4 ports detected
[    3.293272] ohci_hcd 0000:00:03.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    3.293298] ohci_hcd 0000:00:03.1: OHCI Host Controller
[    3.293337] ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 2
[    3.293363] ohci_hcd 0000:00:03.1: irq 21, io mem 0xfddfe000
[    3.350732] usb usb2: configuration #1 chosen from 1 choice
[    3.350771] hub 2-0:1.0: USB hub found
[    3.350786] hub 2-0:1.0: 4 ports detected
[    3.452862] ehci_hcd 0000:00:03.3: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    3.452890] ehci_hcd 0000:00:03.3: EHCI Host Controller
[    3.452933] ehci_hcd 0000:00:03.3: new USB bus registered, assigned bus number 3
[    3.452974] ehci_hcd 0000:00:03.3: debug port 1
[    3.452998] ehci_hcd 0000:00:03.3: irq 22, io mem 0xfddfd000
[    3.464521] ehci_hcd 0000:00:03.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.464715] usb usb3: configuration #1 chosen from 1 choice
[    3.464758] hub 3-0:1.0: USB hub found
[    3.464770] hub 3-0:1.0: 8 ports detected
[    3.570326] pata_acpi 0000:00:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    3.570377] pata_acpi 0000:00:05.0: PCI INT A disabled
[    3.581792] sata_sis 0000:00:05.0: version 1.0
[    3.581811] sata_sis 0000:00:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    3.581820] sata_sis 0000:00:05.0: Detected SiS 1183/966/966L/968/680 controller in PATA mode
[    3.582465] scsi2 : sata_sis
[    3.582564] scsi3 : sata_sis
[    3.583481] ata3: PATA max UDMA/133 cmd 0xc800 ctl 0xc400 bmdma 0xb800 irq 17
[    3.583485] ata4: PATA max UDMA/133 cmd 0xc000 ctl 0xbc00 bmdma 0xb808 irq 17
[    3.625540] scsi 0:0:0:0: Attached scsi generic sg0 type 5
[    3.673218] Driver 'sr' needs updating - please use bus_type methods
[    3.679262] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    3.679269] Uniform CD-ROM driver Revision: 3.20
[    3.679412] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    3.745093] ata3.00: ATA-7: ST980811AS, 3.ALC, max UDMA/133
[    3.745098] ata3.00: 156301488 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    3.761757] ata3.00: configured for UDMA/133
[    3.926986] scsi 2:0:0:0: Direct-Access     ATA      ST980811AS       3.AL PQ: 0 ANSI: 5
[    3.927192] scsi 2:0:0:0: Attached scsi generic sg1 type 0
[    3.951328] Driver 'sd' needs updating - please use bus_type methods
[    3.951467] sd 2:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[    3.951488] sd 2:0:0:0: [sda] Write Protect is off
[    3.951491] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.951524] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.951617] sd 2:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[    3.951636] sd 2:0:0:0: [sda] Write Protect is off
[    3.951639] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.951671] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.951676]  sda: sda1 sda2 < sda5 >
[    4.031713] sd 2:0:0:0: [sda] Attached SCSI disk
[    4.321646] PM: Starting manual resume from disk
[    4.321651] PM: Resume from partition 8:5
[    4.321653] PM: Checking hibernation image.
[    4.321835] PM: Resume from disk failed.
[    4.390209] kjournald starting.  Commit interval 5 seconds
[    4.390224] EXT3-fs: mounted filesystem with ordered data mode.
[   10.823790] udevd version 124 started
[   11.550794] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   11.602856] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   11.753494] Linux agpgart interface v0.103
[   11.928666] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   12.040357] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[   12.060036] ACPI: Power Button (FF) [PWRF]
[   12.060248] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input4
[   12.076047] ACPI: Power Button (CM) [PWRB]
[   12.076163] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input5
[   12.103382] agpgart-sis 0000:00:00.0: SiS chipset [1039/0671]
[   12.108046] ACPI: Sleep Button (CM) [SLPB]
[   12.108238] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input6
[   12.110307] ACPI: Lid Switch [LID]
[   12.114756] agpgart-sis 0000:00:00.0: AGP aperture is 128M @ 0xf0000000
[   12.204060] ACPI: AC Adapter [AC0] (on-line)
[   12.319493] sis190 Gigabit Ethernet driver 1.2 loaded.
[   12.319527] sis190 0000:00:04.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   12.319543] sis190 0000:00:04.0: setting latency timer to 64
[   12.319559] 0000:00:04.0: Read MAC address from EEPROM
[   12.319562] 0000:00:04.0: Error EEPROM read 0.
[   12.319566] 0000:00:04.0: Read MAC address from APC.
[   12.361130] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[   12.377011] 0000:00:04.0: Realtek PHY RTL8201 transceiver at address 1.
[   12.384153] ACPI: Battery Slot [BAT0] (battery present)
[   12.418871] asus-laptop: Asus Laptop Support version 0.42
[   12.425687] asus-laptop:   T12C model detected
[   12.426923] asus-laptop: Brightness ignored, must be controlled by ACPI video driver
[   12.473913] acpi device:0f: registered as cooling_device2
[   12.474194] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:0c/device:0d/input/input7
[   12.518112] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   12.920553] 0000:00:04.0: Using transceiver at address 1 as default.
[   12.952975] 0000:00:04.0: SiS 191 PCI Gigabit Ethernet adapter at f884cc00 (IRQ: 19), 00:1f:c6:03:e6:47
[   12.952980] eth0: GMII mode.
[   12.952989] eth0: Enabling Auto-negotiation.
[   13.073217] HDA Intel 0000:00:0f.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   13.073268] HDA Intel 0000:00:0f.0: setting latency timer to 64
[   13.106391] hda_codec: Unknown model for ALC660VD/ALC861VD, trying auto-probe from BIOS...
[   13.107632] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x3aa0b4, caps: 0xa04713/0x200000
[   13.144626] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'KeInitializeGuardedMutex'
[   13.144639] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'KeReleaseGuardedMutex'
[   13.144649] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'KeAcquireGuardedMutex'
[   13.144744] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateMdl'
[   13.144755] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisRetreatNetBufferDataStart'
[   13.144766] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSynchronizeWithInterruptEx'
[   13.144776] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeMdl'
[   13.144803] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisOpenConfigurationEx'
[   13.144817] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMAllocateNetBufferSGList'
[   13.144828] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSendNetBufferListsComplete'
[   13.144838] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMFreeNetBufferSGList'
[   13.144849] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterScatterGatherDma'
[   13.144865] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSetBusData'
[   13.144876] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMGetBusData'
[   13.144891] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAdvanceNetBufferDataStart'
[   13.144906] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateMemoryWithTagPriority'
[   13.144920] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeIoWorkItem'
[   13.144930] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateIoWorkItem'
[   13.144950] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterInterruptEx'
[   13.144961] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMResetComplete'
[   13.144998] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterMiniportDriver'
[   13.145009] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterMiniportDriver'
[   13.145019] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisQueueIoWorkItem'
[   13.145030] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterInterruptEx'
[   13.145051] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSetMiniportAttributes'
[   13.145065] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMIndicateStatusEx'
[   13.145075] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMOidRequestComplete'
[   13.145086] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisGetSystemUpTimeEx'
[   13.145096] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferList'
[   13.145107] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferList'
[   13.145122] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBuffer'
[   13.145132] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBuffer'
[   13.145147] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferPool'
[   13.145157] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferListPool'
[   13.145168] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferPool'
[   13.145178] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferListPool'
[   13.145189] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMIndicateReceiveNetBufferLists'
[   13.145200] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterScatterGatherDma'
[   13.145206] ndiswrapper (load_sys_files:206): couldn't prepare driver 'netathr'
[   13.145912] ndiswrapper (load_wrap_driver:108): couldn't load driver netathr; check system log for messages from 'loadndisdriver'
[   13.146017] usbcore: registered new interface driver ndiswrapper
[   13.148589] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input8
[   14.894286] lp: driver loaded but no devices found
[   15.135622] Adding 9767480k swap on /dev/sda5.  Priority:-1 extents:1 across:9767480k
[   15.695140] EXT3 FS on sda1, internal journal
[   16.789588] type=1505 audit(1230657767.136:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=3976
[   17.005221] type=1505 audit(1230657767.352:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=3981
[   17.005536] type=1505 audit(1230657767.352:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=3981
[   17.239127] ip_tables: (C) 2000-2006 Netfilter Core Team
[   17.972847] ACPI: WMI: Mapper loaded
[   18.988474] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   19.102490] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   19.102498] apm: disabled - APM is not SMP safe.
[   19.297829] ppdev: user-space parallel port driver
[   22.159460] Bluetooth: Core ver 2.13
[   22.161104] NET: Registered protocol family 31
[   22.161114] Bluetooth: HCI device and connection manager initialized
[   22.161122] Bluetooth: HCI socket layer initialized
[   22.206795] Bluetooth: L2CAP ver 2.11
[   22.206808] Bluetooth: L2CAP socket layer initialized
[   22.251071] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   22.251084] Bluetooth: BNEP filters: protocol multicast
[   22.318898] Bridge firewalling registered
[   22.363881] Bluetooth: SCO (Voice Link) ver 0.6
[   22.363889] Bluetooth: SCO socket layer initialized
[   22.374412] Bluetooth: RFCOMM socket layer initialized
[   22.374436] Bluetooth: RFCOMM TTY layer initialized
[   22.374440] Bluetooth: RFCOMM ver 1.10
[   36.576049] eth0: mii ext = 0000.
[   36.596036] eth0: mii lpa = 41e1 adv = 01e1.
[   36.596049] eth0: link on 100 Mbps Full Duplex mode.
[   36.624035] eth0: mii ext = 0000.
[   36.640034] eth0: mii lpa = 41e1 adv = 01e1.
[   36.640047] eth0: link on 100 Mbps Full Duplex mode.
[   36.895231] NET: Registered protocol family 17
[   38.531447] NET: Registered protocol family 10
[   38.532837] lo: Disabled Privacy Extensions
[   49.180120] eth0: no IPv6 routers present
[   55.659317] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
[   73.920189] CPU0 attaching NULL sched-domain.
[   73.920211] CPU1 attaching NULL sched-domain.
[   73.924225] CPU0 attaching sched-domain:
[   73.924236]  domain 0: span 0-1 level MC
[   73.924243]   groups: 0 1
[   73.924257] CPU1 attaching sched-domain:
[   73.924263]  domain 0: span 0-1 level MC
[   73.924268]   groups: 1 0

**_network config_**
root@brummy-laptop:~# sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 191 Gigabit Ethernet Adapter
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 02
       serial: 00:1f:c6:03:e6:47
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sis190 driverversion=1.2 duplex=full ip=192.168.0.6 latency=0 link=yes module=sis190 multicast=yes port=MII speed=100MB/s
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 72:65:4d:fa:da:3d
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

**_network scan_**
root@brummy-laptop:~# iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

**_network scan wlan0 _**
@brummy-laptop:~# iwlist scan wlan0
iwlist: unknown command `wlan0' (check 'iwlist --help')

**_ubuntu version_**
root@brummy-laptop:~# lsb_release -d
Description:	Ubuntu 8.10

_**kernal/archichet**_
root@brummy-laptop:~# uname -mr
2.6.27-11-generic i686

_**network restart**_
root@brummy-laptop:~# sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                                                         Ignoring unknown interface eth0=eth0.


i think this is everything from the 2nd sticky

---

