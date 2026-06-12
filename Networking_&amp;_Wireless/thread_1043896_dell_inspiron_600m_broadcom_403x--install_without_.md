---
title: "dell inspiron 600m broadcom 403x--install without working internet?"
date: 2009-01-18
forum: Networking &amp; Wireless
---

### Post by grandiloq on 2009-01-18
So, I am trying to install Ubuntu on a Dell Inspiron 600m laptop.  No wireless.  Ubuntu wants to use fwcutter to get, I think, the proper firmware, or maybe it's the driver.  I have searched here and elsewhere and it seems that this is necessary.  Problem is Ubuntu is not detecting my wired connection--it's possible the network adapter is dead, I haven't used it in a long time.  I can't check it in Windows because my hard drive died, and I am running Ubuntu from an external hard drive.  Without an internet connection, fwcutter just quits without finishing and my wireless remains undetected.

So, is there any way to get what I need without an internet connection? I have access to the internet from another computer running Windows.  Can I download what I need and copy it to my laptop?

The crazy thing is, if I run Puppy Linux--minimal distro--from a CD, wireless works fine (a little slow, I think, though I might be imagining that).

Please note that I am a total ignoramus about Linux, and was seeking Ubuntu as a "user-friendly" variant--so I'm going to need handholding, step-by-step stuff (though pointing me elsewhere is great too!).  Thanks a bunch for any help/direction.

Info:
```
jeff@jeff-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV250 [Mobility FireGL 9000] (rev 02)
02:01.0 CardBus bridge: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller (rev 20)
02:01.1 CardBus bridge: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller (rev 20)
02:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

```

```
jeff@jeff-laptop:~$ lsusb
Bus 004 Device 002: ID 067b:2506 Prolific Technology, Inc. 
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
	
```

```
jeff@jeff-laptop:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:246 errors:0 dropped:0 overruns:0 frame:0
          TX packets:246 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15408 (15.4 KB)  TX bytes:15408 (15.4 KB)
```

```
jeff@jeff-laptop:~$ iwconfig
lo        no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.
```

```
jeff@jeff-laptop:~$ lsmod
Module                  Size  Used by
ipv6                  263972  8 
nls_iso8859_1          12032  1 
nls_cp437              13696  1 
vfat                   18816  1 
fat                    57376  1 vfat
af_packet              25728  2 
rfkill_input           12672  0 
binfmt_misc            16904  1 
radeon                147616  2 
drm                    86056  3 radeon
sco                    18308  2 
bridge                 56980  0 
stp                    10628  1 bridge
bnep                   20480  2 
rfcomm                 44432  0 
l2cap                  30464  6 bnep,rfcomm
bluetooth              61924  6 sco,bnep,rfcomm,l2cap
ppdev                  15620  0 
speedstep_centrino     15360  0 
cpufreq_ondemand       14988  1 
cpufreq_stats          13188  0 
cpufreq_userspace      11396  0 
freq_table             12672  3 speedstep_centrino,cpufreq_ondemand,cpufreq_stats
cpufreq_powersave       9856  0 
cpufreq_conservative    14600  0 
container              11520  0 
pci_slot               12552  0 
sbs                    19464  0 
wmi                    14504  0 
sbshc                  13440  1 sbs
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
lp                     17156  0 
pata_pcmcia            18944  2 
pcmcia                 43052  1 pata_pcmcia
joydev                 18368  0 
arc4                    9984  2 
ecb                    10880  2 
crypto_blkcipher       25476  1 ecb
b43                   131356  0 
rfkill                 17176  2 rfkill_input,b43
mac80211              216820  1 b43
cfg80211               32392  1 mac80211
led_class              12164  1 b43
input_polldev          11912  1 b43
psmouse                45200  0 
yenta_socket           31756  6 
snd_intel8x0           37532  3 
rsrc_nonstatic         19072  1 yenta_socket
serio_raw              13444  0 
snd_ac97_codec        111652  1 snd_intel8x0
pcmcia_core            43412  4 pata_pcmcia,pcmcia,yenta_socket,rsrc_nonstatic
ac97_bus                9856  1 snd_ac97_codec
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
video                  25104  0 
output                 11008  1 video
snd_pcm                83204  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
ndiswrapper           196380  0 
parport_pc             39204  1 
parport                42604  3 ppdev,lp,parport_pc
snd_seq_dummy          10884  0 
evdev                  17696  10 
dcdbas                 15008  0 
snd_seq_oss            38528  0 
snd_seq_midi           14336  0 
button                 14224  0 
snd_rawmidi            29824  1 snd_seq_midi
battery                18436  0 
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
ac                     12292  0 
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
intel_agp              33724  1 
snd                    63268  16 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
agpgart                42184  2 drm,intel_agp
pcspkr                 10624  0 
shpchp                 37908  0 
pci_hotplug            35236  1 shpchp
soundcore              15328  1 snd
iTCO_wdt               18596  0 
iTCO_vendor_support    11652  1 iTCO_wdt
snd_page_alloc         16136  2 snd_intel8x0,snd_pcm
ext3                  133256  1 
jbd                    55444  1 ext3
mbcache                16004  1 ext3
sd_mod                 42264  5 
crc_t10dif              9984  1 sd_mod
usb_storage            81728  2 
libusual               27156  1 usb_storage
sr_mod                 22212  0 
cdrom                  43168  1 sr_mod
sg                     39732  0 
ata_piix               24580  0 
ata_generic            12932  0 
pata_acpi              12160  0 
libata                177312  4 pata_pcmcia,ata_piix,ata_generic,pata_acpi
ehci_hcd               43276  0 
uhci_hcd               30736  0 
ssb                    40580  1 b43
scsi_mod              155212  5 sd_mod,usb_storage,sr_mod,sg,libata
usbcore               148848  6 ndiswrapper,usb_storage,libusual,ehci_hcd,uhci_hcd
dock                   16656  1 libata
thermal                23708  0 
processor              42156  2 thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  3 

```

```
jeff@jeff-laptop:~$ dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-7-generic (buildd@rothera) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu10) ) #1 SMP Fri Oct 24 06:42:44 UTC 2008 (Ubuntu 2.6.27-7.14-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001ffae000 (usable)
[    0.000000]  BIOS-e820: 000000001ffae000 - 0000000020000000 (reserved)
[    0.000000]  BIOS-e820: 00000000feda0000 - 00000000fee00000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] last_pfn = 0x1ffae max_arch_pfn = 0x100000
[    0.000000] kernel direct mapping tables up to 1ffae000 @ 7000-d000
[    0.000000] RAMDISK: 1f7d1000 - 1ff9d1af
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP 000FDF00, 0014 (r0 DELL  )
[    0.000000] ACPI: RSDT 1FFF0000, 0028 (r1 DELL    CPi R   27D5061D ASL        61)
[    0.000000] ACPI: FACP 1FFF0400, 0074 (r1 DELL    CPi R   27D5061D ASL        61)
[    0.000000] ACPI: DSDT 1FFF0C00, 2E0C (r1 INT430 SYSFexxx     1001 MSFT  100000E)
[    0.000000] ACPI: FACS 1FFFF800, 0040
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 511MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 1ffae000
[    0.000000]   low ram: 00000000 - 1ffae000
[    0.000000]   bootmap 00002000 - 00005ff8
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 001ffae000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00005c0a20]    TEXT DATA BSS ==> [0000100000 - 00005c0a20]
[    0.000000]   #4 [001f7d1000 - 001ff9d1af]          RAMDISK ==> [001f7d1000 - 001ff9d1af]
[    0.000000]   #5 [00005c1000 - 00005c4000]    INIT_PG_TABLE ==> [00005c1000 - 00005c4000]
[    0.000000]   #6 [000009f000 - 0000100000]    BIOS reserved ==> [000009f000 - 0000100000]
[    0.000000]   #7 [0000007000 - 0000009000]          PGTABLE ==> [0000007000 - 0000009000]
[    0.000000]   #8 [0000002000 - 0000006000]          BOOTMAP ==> [0000002000 - 0000006000]
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x0001ffae
[    0.000000]   HighMem  0x0001ffae -> 0x0001ffae
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0001ffae
[    0.000000] On node 0 totalpages: 130893
[    0.000000] free_area_init_node: node 0, pgdat c048a500, node_mem_map c1000000
[    0.000000]   DMA zone: 3963 pages, LIFO batch:0
[    0.000000]   Normal zone: 125778 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] mapped APIC to ffffb000 (01482000)
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:deda0000)
[    0.000000] PERCPU: Allocating 41628 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 1, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 129741
[    0.000000] Kernel command line: root=UUID=a84c3f16-91bc-4b71-a831-b3414b272db3 ro quiet splash 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] TSC: PIT calibration confirmed by PMTIMER.
[    0.000000] TSC: using PIT calibration value
[    0.000000] Detected 1495.138 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.004000] Memory: 505412k/523960k available (2572k kernel code, 17968k reserved, 1160k data, 424k init, 0k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xe0800000 - 0xff3fe000   ( 491 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xdffae000   ( 511 MB)
[    0.004000]       .init : 0xc04ab000 - 0xc0515000   ( 424 kB)
[    0.004000]       .data : 0xc038329a - 0xc04a5680   (1160 kB)
[    0.004000]       .text : 0xc0100000 - 0xc038329a   (2572 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.004013] Calibrating delay loop (skipped), value calculated using timer frequency.. 2990.27 BogoMIPS (lpj=5980552)
[    0.004038] Security Framework initialized
[    0.004049] SELinux:  Disabled at boot.
[    0.004081] AppArmor: AppArmor initialized
[    0.004092] Mount-cache hash table entries: 512
[    0.004309] Initializing cgroup subsys ns
[    0.004315] Initializing cgroup subsys cpuacct
[    0.004319] Initializing cgroup subsys memory
[    0.004339] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004343] CPU: L2 cache: 1024K
[    0.004356] Checking 'hlt' instruction... OK.
[    0.020631] SMP alternatives: switching to UP code
[    0.027625] Freeing SMP alternatives: 11k freed
[    0.027629] ACPI: Core revision 20080609
[    0.029357] ACPI: Checking initramfs for custom DSDT
[    0.479195] ACPI: setting ELCR to 0200 (from 0800)
[    0.480093] weird, boot CPU (#0) not listedby the BIOS.
[    0.480097] SMP motherboard not detected.
[    0.480101] Local APIC not detected. Using dummy APIC emulation.
[    0.480104] SMP disabled
[    0.480183] Brought up 1 CPUs
[    0.480186] Total of 1 processors activated (2990.27 BogoMIPS).
[    0.480201] CPU0 attaching sched-domain:
[    0.480205]  domain 0: span 0 level CPU
[    0.480209]   groups: 0
[    0.480520] net_namespace: 840 bytes
[    0.480539] Booting paravirtualized kernel on bare hardware
[    0.480843] Time: 11:10:40  Date: 01/18/09
[    0.480880] NET: Registered protocol family 16
[    0.481270] EISA bus registered
[    0.481289] ACPI: bus type pci registered
[    0.516730] PCI: PCI BIOS revision 2.10 entry at 0xfc96e, last bus=2
[    0.516733] PCI: Using configuration type 1 for base access
[    0.518530] ACPI: EC: Look up EC in DSDT
[    0.530900] ACPI: Interpreter enabled
[    0.530906] ACPI: (supports S0 S1 S3 S4 S5)
[    0.530928] ACPI: Using PIC for interrupt routing
[    0.556194] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.556282] PCI: 0000:00:00.0 reg 10 32bit mmio: [e0000000, e7ffffff]
[    0.556393] PCI: 0000:00:1d.0 reg 20 io port: [bf80, bf9f]
[    0.556445] PCI: 0000:00:1d.1 reg 20 io port: [bf40, bf5f]
[    0.556497] PCI: 0000:00:1d.2 reg 20 io port: [bf20, bf3f]
[    0.556557] PCI: 0000:00:1d.7 reg 10 32bit mmio: [f4fffc00, f4ffffff]
[    0.556610] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.556617] pci 0000:00:1d.7: PME# disabled
[    0.556693] HPET not enabled in BIOS. You might try hpet=force boot option
[    0.556701] pci 0000:00:1f.0: quirk: region 0800-087f claimed by ICH4 ACPI/GPIO/TCO
[    0.556707] pci 0000:00:1f.0: quirk: region 0880-08bf claimed by ICH4 GPIO
[    0.556727] PCI: 0000:00:1f.1 reg 10 io port: [1f0, 1f7]
[    0.556734] PCI: 0000:00:1f.1 reg 14 io port: [3f4, 3f7]
[    0.556742] PCI: 0000:00:1f.1 reg 18 io port: [170, 177]
[    0.556749] PCI: 0000:00:1f.1 reg 1c io port: [374, 377]
[    0.556757] PCI: 0000:00:1f.1 reg 20 io port: [bfa0, bfaf]
[    0.556765] PCI: 0000:00:1f.1 reg 24 32bit mmio: [0, 3ff]
[    0.556807] PCI: 0000:00:1f.5 reg 10 io port: [b800, b8ff]
[    0.556814] PCI: 0000:00:1f.5 reg 14 io port: [bc40, bc7f]
[    0.556821] PCI: 0000:00:1f.5 reg 18 32bit mmio: [f4fff800, f4fff9ff]
[    0.556829] PCI: 0000:00:1f.5 reg 1c 32bit mmio: [f4fff400, f4fff4ff]
[    0.556856] pci 0000:00:1f.5: PME# supported from D0 D3hot D3cold
[    0.556861] pci 0000:00:1f.5: PME# disabled
[    0.556889] PCI: 0000:00:1f.6 reg 10 io port: [b400, b4ff]
[    0.556896] PCI: 0000:00:1f.6 reg 14 io port: [b080, b0ff]
[    0.556931] pci 0000:00:1f.6: PME# supported from D0 D3hot D3cold
[    0.556936] pci 0000:00:1f.6: PME# disabled
[    0.556970] PCI: 0000:01:00.0 reg 10 32bit mmio: [e8000000, efffffff]
[    0.556976] PCI: 0000:01:00.0 reg 14 io port: [c000, c0ff]
[    0.556983] PCI: 0000:01:00.0 reg 18 32bit mmio: [fcff0000, fcffffff]
[    0.556999] PCI: 0000:01:00.0 reg 30 32bit mmio: [0, 1ffff]
[    0.557015] pci 0000:01:00.0: supports D1
[    0.557017] pci 0000:01:00.0: supports D2
[    0.557049] PCI: bridge 0000:00:01.0 io port: [c000, cfff]
[    0.557053] PCI: bridge 0000:00:01.0 32bit mmio: [fc000000, fdffffff]
[    0.557058] PCI: bridge 0000:00:01.0 32bit mmio pref: [e8000000, efffffff]
[    0.557094] PCI: 0000:02:01.0 reg 10 32bit mmio: [0, fff]
[    0.557110] pci 0000:02:01.0: supports D1
[    0.557112] pci 0000:02:01.0: supports D2
[    0.557115] pci 0000:02:01.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.557120] pci 0000:02:01.0: PME# disabled
[    0.557148] PCI: 0000:02:01.1 reg 10 32bit mmio: [0, fff]
[    0.557164] pci 0000:02:01.1: supports D1
[    0.557166] pci 0000:02:01.1: supports D2
[    0.557169] pci 0000:02:01.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.557174] pci 0000:02:01.1: PME# disabled
[    0.557199] PCI: 0000:02:03.0 reg 10 32bit mmio: [faffe000, faffffff]
[    0.557264] pci 0000:00:1e.0: transparent bridge
[    0.557269] PCI: bridge 0000:00:1e.0 io port: [d000, efff]
[    0.557274] PCI: bridge 0000:00:1e.0 32bit mmio: [f6000000, fbffffff]
[    0.557317] bus 00 -> node 0
[    0.557325] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.557799] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    0.557919] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
[    0.573719] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 *11)
[    0.573887] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *11
[    0.574053] ACPI: PCI Interrupt Link [LNKC] (IRQs 9 10 *11)
[    0.574217] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 7 9 10 *11)
[    0.574359] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.574531] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    0.574745] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.574799] pnp: PnP ACPI init
[    0.574809] ACPI: bus type pnp registered
[    0.588623] pnp 00:02: io resource (0x800-0x805) overlaps 0000:00:1f.0 BAR 7 (0x800-0x87f), disabling
[    0.588628] pnp 00:02: io resource (0x808-0x80f) overlaps 0000:00:1f.0 BAR 7 (0x800-0x87f), disabling
[    0.588760] pnp 00:03: io resource (0x806-0x807) overlaps 0000:00:1f.0 BAR 7 (0x800-0x87f), disabling
[    0.588765] pnp 00:03: io resource (0x810-0x85f) overlaps 0000:00:1f.0 BAR 7 (0x800-0x87f), disabling
[    0.588770] pnp 00:03: io resource (0x860-0x87f) overlaps 0000:00:1f.0 BAR 7 (0x800-0x87f), disabling
[    0.624137] pnp: PnP ACPI: found 14 devices
[    0.624140] ACPI: ACPI bus type pnp unregistered
[    0.624146] PnPBIOS: Disabled by ACPI PNP
[    0.624595] PCI: Using ACPI for IRQ routing
[    0.624730] NET: Registered protocol family 8
[    0.624730] NET: Registered protocol family 20
[    0.624730] NetLabel: Initializing
[    0.624730] NetLabel:  domain hash size = 128
[    0.624730] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.624730] NetLabel:  unlabeled traffic allowed by default
[    0.624730] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    0.624730]    actual entries 65620
[    0.624730] AppArmor: AppArmor Filesystem Enabled
[    0.624730] system 00:00: iomem range 0x0-0x9fbff could not be reserved
[    0.624730] system 00:00: iomem range 0x9fc00-0x9ffff could not be reserved
[    0.624730] system 00:00: iomem range 0xc0000-0xcffff could not be reserved
[    0.624730] system 00:00: iomem range 0xe0000-0xfffff could not be reserved
[    0.624730] system 00:00: iomem range 0x100000-0x1ffeffff could not be reserved
[    0.624730] system 00:00: iomem range 0x1fff0000-0x1fffffff could not be reserved
[    0.624730] system 00:00: iomem range 0xfeda0000-0xfedfffff could not be reserved
[    0.624730] system 00:00: iomem range 0xffb00000-0xffbfffff could not be reserved
[    0.624730] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
[    0.624730] system 00:03: ioport range 0xf400-0xf4fe has been reserved
[    0.624730] system 00:03: ioport range 0x880-0x8bf has been reserved
[    0.624730] system 00:03: ioport range 0x8c0-0x8df has been reserved
[    0.624730] system 00:03: ioport range 0x8e0-0x8ff has been reserved
[    0.624730] system 00:08: ioport range 0x900-0x97f has been reserved
[    0.660925] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.660929] pci 0000:00:01.0:   IO window: 0xc000-0xcfff
[    0.660934] pci 0000:00:01.0:   MEM window: 0xfc000000-0xfdffffff
[    0.660939] pci 0000:00:01.0:   PREFETCH window: 0x000000e8000000-0x000000efffffff
[    0.660955] pci 0000:02:01.0: CardBus bridge, secondary bus 0000:03
[    0.660959] pci 0000:02:01.0:   IO window: 0x00d000-0x00d0ff
[    0.660964] pci 0000:02:01.0:   IO window: 0x00d400-0x00d4ff
[    0.660969] pci 0000:02:01.0:   PREFETCH window: 0x30000000-0x33ffffff
[    0.660975] pci 0000:02:01.0:   MEM window: 0x3c000000-0x3fffffff
[    0.660980] pci 0000:02:01.1: CardBus bridge, secondary bus 0000:07
[    0.660983] pci 0000:02:01.1:   IO window: 0x00d800-0x00d8ff
[    0.660988] pci 0000:02:01.1:   IO window: 0x00dc00-0x00dcff
[    0.660993] pci 0000:02:01.1:   PREFETCH window: 0x34000000-0x37ffffff
[    0.660999] pci 0000:02:01.1:   MEM window: 0x40000000-0x43ffffff
[    0.661004] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:02
[    0.661008] pci 0000:00:1e.0:   IO window: 0xd000-0xefff
[    0.661014] pci 0000:00:1e.0:   MEM window: 0xf6000000-0xfbffffff
[    0.661020] pci 0000:00:1e.0:   PREFETCH window: 0x00000030000000-0x00000037ffffff
[    0.661040] pci 0000:00:1e.0: setting latency timer to 64
[    0.661049] pci 0000:02:01.0: enabling device (0000 -> 0003)
[    0.661313] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[    0.661317] PCI: setting IRQ 11 as level-triggered
[    0.661323] pci 0000:02:01.0: PCI INT A -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
[    0.661335] pci 0000:02:01.1: enabling device (0000 -> 0003)
[    0.661341] pci 0000:02:01.1: PCI INT A -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
[    0.661348] bus: 00 index 0 io port: [0, ffff]
[    0.661351] bus: 00 index 1 mmio: [0, ffffffff]
[    0.661354] bus: 01 index 0 io port: [c000, cfff]
[    0.661357] bus: 01 index 1 mmio: [fc000000, fdffffff]
[    0.661360] bus: 01 index 2 mmio: [e8000000, efffffff]
[    0.661363] bus: 01 index 3 mmio: [0, 0]
[    0.661366] bus: 02 index 0 io port: [d000, efff]
[    0.661369] bus: 02 index 1 mmio: [f6000000, fbffffff]
[    0.661372] bus: 02 index 2 mmio: [30000000, 37ffffff]
[    0.661375] bus: 02 index 3 io port: [0, ffff]
[    0.661378] bus: 02 index 4 mmio: [0, ffffffff]
[    0.661381] bus: 03 index 0 io port: [d000, d0ff]
[    0.661384] bus: 03 index 1 io port: [d400, d4ff]
[    0.661387] bus: 03 index 2 mmio: [30000000, 33ffffff]
[    0.661390] bus: 03 index 3 mmio: [3c000000, 3fffffff]
[    0.661393] bus: 07 index 0 io port: [d800, d8ff]
[    0.661396] bus: 07 index 1 io port: [dc00, dcff]
[    0.661399] bus: 07 index 2 mmio: [34000000, 37ffffff]
[    0.661402] bus: 07 index 3 mmio: [40000000, 43ffffff]
[    0.661416] NET: Registered protocol family 2
[    0.661604] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    0.661929] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    0.662068] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[    0.662205] TCP: Hash tables configured (established 16384 bind 16384)
[    0.662209] TCP reno registered
[    0.662316] NET: Registered protocol family 1
[    0.662466] checking if image is initramfs... it is
[    1.164088] Switched to high resolution mode on CPU 0
[    1.601934] Freeing initrd memory: 7984k freed
[    1.602817] audit: initializing netlink socket (disabled)
[    1.602843] type=2000 audit(1232277040.600:1): initialized
[    1.611379] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.614737] VFS: Disk quotas dquot_6.5.1
[    1.614876] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.615031] msgmni has been set to 1003
[    1.615220] io scheduler noop registered
[    1.615224] io scheduler anticipatory registered
[    1.615228] io scheduler deadline registered
[    1.615249] io scheduler cfq registered (default)
[    1.615350] pci 0000:01:00.0: Boot video device
[    1.615811] isapnp: Scanning for PnP cards...
[    1.968558] isapnp: No Plug & Play device found
[    2.022001] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    2.022147] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    2.022578] serial8250: ttyS3 at I/O 0x2e8 (irq = 3) is a 16550A
[    2.023211] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    2.023767] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 5
[    2.023771] PCI: setting IRQ 5 as level-triggered
[    2.023777] serial 0000:00:1f.6: PCI INT B -> Link[LNKB] -> GSI 5 (level, low) -> IRQ 5
[    2.023786] serial 0000:00:1f.6: PCI INT B disabled
[    2.026163] brd: module loaded
[    2.026263] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    2.026436] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    2.031395] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.031404] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.031860] mice: PS/2 mouse device common for all mice
[    2.032060] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    2.032079] rtc0: alarms up to one day
[    2.032236] EISA: Probing bus 0 at eisa.0
[    2.032265] EISA: Detected 0 cards.
[    2.032270] cpuidle: using governor ladder
[    2.032273] cpuidle: using governor menu
[    2.033100] TCP cubic registered
[    2.033143] Using IPI No-Shortcut mode
[    2.033440] registered taskstats version 1
[    2.033589]   Magic number: 9:103:176
[    2.033662] tty ttyr2: hash matches
[    2.033798] acpi device:0c: hash matches
[    2.033842] rtc_cmos 00:06: setting system clock to 2009-01-18 11:10:41 UTC (1232277041)
[    2.033846] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.033849] EDD information not available.
[    2.034224] Freeing unused kernel memory: 424k freed
[    2.034286] Write protecting the kernel text: 2576k
[    2.034324] Write protecting the kernel read-only data: 936k
[    2.037960] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    2.265440] fuse init (API version 7.9)
[    2.419870] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3] C4[C3])
[    2.419949] processor ACPI0007:00: registered as cooling_device0
[    2.419955] ACPI: Processor [CPU0] (supports 8 throttling states)
[    2.427763] thermal LNXTHERM:01: registered as thermal_zone0
[    2.430987] ACPI: Thermal Zone [THM] (40 C)
[    3.111626] ACPI: ACPI Dock Station Driver
[    3.287874] usbcore: registered new interface driver usbfs
[    3.287911] usbcore: registered new interface driver hub
[    3.296796] usbcore: registered new device driver usb
[    3.327884] SCSI subsystem initialized
[    3.328380] b43-pci-bridge 0000:02:03.0: PCI INT A -> Link[LNKB] -> GSI 5 (level, low) -> IRQ 5
[    3.331742] ssb: Sonics Silicon Backplane found on PCI device 0000:02:03.0
[    3.336678] USB Universal Host Controller Interface driver v3.0
[    3.337030] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[    3.337035] uhci_hcd 0000:00:1d.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[    3.337047] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    3.337052] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    3.337112] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[    3.337142] uhci_hcd 0000:00:1d.0: irq 11, io base 0x0000bf80
[    3.337414] usb usb1: configuration #1 chosen from 1 choice
[    3.337451] hub 1-0:1.0: USB hub found
[    3.337460] hub 1-0:1.0: 2 ports detected
[    3.405556] libata version 3.00 loaded.
[    3.440554] uhci_hcd 0000:00:1d.1: PCI INT B -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
[    3.440569] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    3.440574] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    3.440610] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[    3.440643] uhci_hcd 0000:00:1d.1: irq 11, io base 0x0000bf40
[    3.440796] usb usb2: configuration #1 chosen from 1 choice
[    3.440833] hub 2-0:1.0: USB hub found
[    3.440844] hub 2-0:1.0: 2 ports detected
[    3.648742] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[    3.648750] uhci_hcd 0000:00:1d.2: PCI INT C -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[    3.648763] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    3.648768] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    3.648807] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[    3.648838] uhci_hcd 0000:00:1d.2: irq 11, io base 0x0000bf20
[    3.648988] usb usb3: configuration #1 chosen from 1 choice
[    3.649025] hub 3-0:1.0: USB hub found
[    3.649035] hub 3-0:1.0: 2 ports detected
[    3.752809] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 11
[    3.752816] ehci_hcd 0000:00:1d.7: PCI INT D -> Link[LNKH] -> GSI 11 (level, low) -> IRQ 11
[    3.752838] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    3.752842] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.752891] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
[    3.756807] ehci_hcd 0000:00:1d.7: debug port 1
[    3.756815] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    3.756827] ehci_hcd 0000:00:1d.7: irq 11, io mem 0xf4fffc00
[    3.760714] usb 2-1: new full speed USB device using uhci_hcd and address 2
[    3.772051] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.772304] usb usb4: configuration #1 chosen from 1 choice
[    3.772344] hub 4-0:1.0: USB hub found
[    3.772355] hub 4-0:1.0: 6 ports detected
[    3.828161] hub 2-0:1.0: unable to enumerate USB device on port 1
[    3.957532] Marking TSC unstable due to TSC halts in idle
[    3.981556] pata_acpi 0000:00:1f.1: enabling device (0005 -> 0007)
[    3.981568] pata_acpi 0000:00:1f.1: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[    3.981617] pata_acpi 0000:00:1f.1: setting latency timer to 64
[    3.981636] pata_acpi 0000:00:1f.1: PCI INT A disabled
[    3.997299] ata_piix 0000:00:1f.1: version 2.12
[    3.997319] ata_piix 0000:00:1f.1: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[    3.997372] ata_piix 0000:00:1f.1: setting latency timer to 64
[    3.997725] scsi0 : ata_piix
[    3.997878] scsi1 : ata_piix
[    3.999103] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xbfa0 irq 14
[    3.999108] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xbfa8 irq 15
[    3.999152] ata1: port disabled. ignoring.
[    4.092054] usb 4-3: new high speed USB device using ehci_hcd and address 2
[    4.160355] ata2.00: ATAPI: SAMSUNG CDRW/DVD SN-324F, U203, max UDMA/33
[    4.176278] ata2.00: configured for UDMA/33
[    4.176902] scsi 1:0:0:0: CD-ROM            SAMSUNG  CDRW/DVD SN-324F U203 PQ: 0 ANSI: 5
[    4.191569] scsi 1:0:0:0: Attached scsi generic sg0 type 5
[    4.214967] Driver 'sr' needs updating - please use bus_type methods
[    4.217042] sr0: scsi3-mmc drive: 2x/24x writer cd/rw xa/form2 cdda tray
[    4.217048] Uniform CD-ROM driver Revision: 3.20
[    4.217176] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    4.226672] usb 4-3: configuration #1 chosen from 1 choice
[    4.261978] usbcore: registered new interface driver libusual
[    4.277846] Initializing USB Mass Storage driver...
[    4.279589] scsi2 : SCSI emulation for USB Mass Storage devices
[    4.279735] usbcore: registered new interface driver usb-storage
[    4.279740] USB Mass Storage support registered.
[    4.279880] usb-storage: device found at 2
[    4.279883] usb-storage: waiting for device to settle before scanning
[    5.660033] Clocksource tsc unstable (delta = -93442559 ns)
[    9.276262] usb-storage: device scan complete
[    9.277023] scsi 2:0:0:0: Direct-Access     IBM-DJSA -210             JS2A PQ: 0 ANSI: 0
[    9.281578] scsi 2:0:0:0: Attached scsi generic sg1 type 0
[    9.295309] Driver 'sd' needs updating - please use bus_type methods
[    9.296353] sd 2:0:0:0: [sda] 19640880 512-byte hardware sectors (10056 MB)
[    9.297359] sd 2:0:0:0: [sda] Write Protect is off
[    9.297363] sd 2:0:0:0: [sda] Mode Sense: 03 00 00 00
[    9.297367] sd 2:0:0:0: [sda] Assuming drive cache: write through
[    9.298230] sd 2:0:0:0: [sda] 19640880 512-byte hardware sectors (10056 MB)
[    9.299103] sd 2:0:0:0: [sda] Write Protect is off
[    9.299107] sd 2:0:0:0: [sda] Mode Sense: 03 00 00 00
[    9.299111] sd 2:0:0:0: [sda] Assuming drive cache: write through
[    9.299116]  sda: sda1 sda2 < sda5 >
[    9.358167] sd 2:0:0:0: [sda] Attached SCSI disk
[    9.831809] PM: Starting manual resume from disk
[    9.831815] PM: Resume from partition 8:5
[    9.831817] PM: Checking hibernation image.
[    9.832384] PM: Resume from disk failed.
[    9.933194] kjournald starting.  Commit interval 5 seconds
[    9.933211] EXT3-fs: mounted filesystem with ordered data mode.
[   21.286149] udevd version 124 started
[   22.714279] iTCO_vendor_support: vendor-support=0
[   22.845351] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.03 (30-Apr-2008)
[   22.845891] iTCO_wdt: Found a ICH4-M TCO device (Version=1, TCOBASE=0x0860)
[   22.846133] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   22.912981] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   22.934726] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   22.951577] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   23.024346] Linux agpgart interface v0.103
[   23.211171] agpgart-intel 0000:00:00.0: Intel 855PM Chipset
[   23.218755] agpgart-intel 0000:00:00.0: AGP aperture is 128M @ 0xe0000000
[   23.235999] intel_rng: FWH not detected
[   23.437639] ACPI: AC Adapter [AC] (off-line)
[   23.957388] ACPI: Battery Slot [BAT0] (battery present)
[   23.957598] ACPI: Battery Slot [BAT1] (battery absent)
[   23.957745] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input3
[   23.958265] ACPI: Lid Switch [LID]
[   23.958370] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input4
[   23.968050] ACPI: Power Button (CM) [PBTN]
[   23.968259] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input5
[   23.980073] ACPI: Sleep Button (CM) [SBTN]
[   24.243666] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   25.138290] parport_pc 00:0c: reported by Plug and Play ACPI
[   25.138342] parport0: PC-style at 0x378 (0x778), irq 7, dma 1 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   25.365658] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[   25.509308] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:1e/device:1f/input/input6
[   25.537136] usbcore: registered new interface driver ndiswrapper
[   25.540400] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   25.932739] Intel ICH 0000:00:1f.5: PCI INT B -> Link[LNKB] -> GSI 5 (level, low) -> IRQ 5
[   25.932769] Intel ICH 0000:00:1f.5: setting latency timer to 64
[   26.352397] input: PS/2 Mouse as /devices/platform/i8042/serio1/input/input7
[   26.398671] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input8
[   26.766223] intel8x0_measure_ac97_clock: measured 61516 usecs
[   26.766228] intel8x0: clocking to 48000
[   26.767577] Yenta: CardBus bridge found at 0000:02:01.0 [1028:011e]
[   26.767599] Yenta O2: res at 0x94/0xD4: 00/ea
[   26.767602] Yenta O2: enabling read prefetch/write burst
[   26.768764] b43-phy0: Broadcom 4306 WLAN found
[   26.819452] phy0: Selected rate control algorithm 'pid'
[   26.892653] Yenta: ISA IRQ mask 0x0418, PCI irq 11
[   26.892659] Socket status: 30000810
[   26.892664] Yenta: Raising subordinate bus# of parent bus (#02) from #02 to #06
[   26.892673] pcmcia: parent PCI bridge I/O window: 0xd000 - 0xefff
[   26.892677] cs: IO port probe 0xd000-0xefff: clean.
[   26.893277] pcmcia: parent PCI bridge Memory window: 0xf6000000 - 0xfbffffff
[   26.893281] pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x37ffffff
[   26.899467] Yenta: CardBus bridge found at 0000:02:01.1 [1028:011e]
[   27.024734] Yenta: ISA IRQ mask 0x0418, PCI irq 11
[   27.024740] Socket status: 30000410
[   27.024744] Yenta: Raising subordinate bus# of parent bus (#02) from #06 to #0a
[   27.024753] pcmcia: parent PCI bridge I/O window: 0xd000 - 0xefff
[   27.024757] cs: IO port probe 0xd000-0xefff: clean.
[   27.025404] pcmcia: parent PCI bridge Memory window: 0xf6000000 - 0xfbffffff
[   27.025408] pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x37ffffff
[   27.185528] Broadcom 43xx driver loaded [ Features: PLR, Firmware-ID: FW13 ]
[   27.532058] pccard: PCMCIA card inserted into slot 0
[   27.660092] pccard: PCMCIA card inserted into slot 1
[   29.252087] cs: memory probe 0xf6000000-0xfbffffff: excluding 0xf6000000-0xf65fffff 0xf6c00000-0xf71fffff 0xf7e00000-0xf83fffff 0xf9c00000-0xfa1fffff 0xfae00000-0xfb3fffff
[   29.290398] pcmcia: registering new device pcmcia0.0
[   29.544230] cs: memory probe 0xf6000000-0xfbffffff: excluding 0xf6000000-0xf71fffff 0xf7e00000-0xf83fffff 0xf9c00000-0xfa1fffff 0xfae00000-0xfb3fffff
[   29.556472] pcmcia: registering new device pcmcia1.0
[   29.595415] cs: IO port probe 0x100-0x3af: excluding 0x300-0x307
[   29.596482] cs: IO port probe 0x3e0-0x4ff: clean.
[   29.596962] cs: IO port probe 0x820-0x8ff: clean.
[   29.597021] cs: IO port probe 0xc00-0xcf7: clean.
[   29.597575] cs: IO port probe 0xa00-0xaff: clean.
[   29.599402] cs: IO port probe 0x100-0x3af: excluding 0x300-0x307
[   29.600476] cs: IO port probe 0x3e0-0x4ff: clean.
[   29.600928] cs: IO port probe 0x820-0x8ff: clean.
[   29.600986] cs: IO port probe 0xc00-0xcf7: clean.
[   29.601541] cs: IO port probe 0xa00-0xaff: clean.
[   29.749235] scsi3 : pata_pcmcia
[   29.749654] ata3: PATA max PIO0 cmd 0xd100 ctl 0xd10e irq 3
[   29.912625] ata3.00: CFA: SanDisk SDCFH2-4096, HDX 4.22, max PIO4
[   29.912630] ata3.00: 8027712 sectors, multi 0: LBA 
[   29.920639] ata3.00: configured for PIO0
[   29.936449] ata3.00: configured for PIO0
[   29.936454] ata3: EH complete
[   29.936490] isa bounce pool size: 16 pages
[   29.936618] scsi 3:0:0:0: Direct-Access     ATA      SanDisk SDCFH2-4 HDX  PQ: 0 ANSI: 5
[   29.937215] sd 3:0:0:0: [sdb] 8027712 512-byte hardware sectors (4110 MB)
[   29.937244] sd 3:0:0:0: [sdb] Write Protect is off
[   29.937247] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   29.937293] sd 3:0:0:0: [sdb] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[   29.937446] sd 3:0:0:0: [sdb] 8027712 512-byte hardware sectors (4110 MB)
[   29.937475] sd 3:0:0:0: [sdb] Write Protect is off
[   29.937479] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   29.937532] sd 3:0:0:0: [sdb] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[   29.937537]  sdb: sdb1
[   29.942516] sd 3:0:0:0: [sdb] Attached SCSI removable disk
[   29.943063] sd 3:0:0:0: Attached scsi generic sg2 type 0
[   31.303395] lp0: using parport0 (interrupt-driven).
[   31.463810] Adding 465844k swap on /dev/sda5.  Priority:-1 extents:1 across:465844k
[   31.503060] EXT3 FS on sda1, internal journal
[   32.179382] type=1505 audit(1232277072.040:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4111
[   32.445069] type=1505 audit(1232277072.308:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4116
[   32.445490] type=1505 audit(1232277072.308:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4116
[   32.681391] ip_tables: (C) 2000-2006 Netfilter Core Team
[   33.519394] ACPI: WMI: Mapper loaded
[   34.889574] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   34.988433] apm: BIOS not found.
[   35.211134] ppdev: user-space parallel port driver
[   38.169245] Bluetooth: Core ver 2.13
[   38.173267] NET: Registered protocol family 31
[   38.173288] Bluetooth: HCI device and connection manager initialized
[   38.173298] Bluetooth: HCI socket layer initialized
[   38.266786] Bluetooth: L2CAP ver 2.11
[   38.266802] Bluetooth: L2CAP socket layer initialized
[   38.345823] Bluetooth: RFCOMM socket layer initialized
[   38.346379] Bluetooth: RFCOMM TTY layer initialized
[   38.346395] Bluetooth: RFCOMM ver 1.10
[   38.365959] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   38.365976] Bluetooth: BNEP filters: protocol multicast
[   38.505858] Bridge firewalling registered
[   38.507959] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.
[   38.596542] Bluetooth: SCO (Voice Link) ver 0.6
[   38.596563] Bluetooth: SCO socket layer initialized
[   40.981078] pci 0000:01:00.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[   41.406115] [drm] Initialized drm 1.1.0 20060810
[   41.538230] [drm] Initialized radeon 1.29.0 20080528 on minor 0
[   41.834266] agpgart-intel 0000:00:00.0: AGP 2.0 bridge
[   41.834305] agpgart-intel 0000:00:00.0: putting AGP V2 device into 4x mode
[   41.834346] pci 0000:01:00.0: putting AGP V2 device into 4x mode
[   42.191052] [drm] Setting GART location based on new memory map
[   42.191084] [drm] Loading R200 Microcode
[   42.191149] [drm] writeback test succeeded in 2 usecs
[   42.663095] input: b43-phy0 as /devices/virtual/input/input9
[   42.728079] firmware: requesting b43/ucode5.fw
[   42.760466] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   42.760487] b43-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the latest firmware (version 4).
[   42.817412] input: b43-phy0 as /devices/virtual/input/input10
[   42.864062] firmware: requesting b43/ucode5.fw
[   42.867840] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   42.867853] b43-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the latest firmware (version 4).
[   43.006170] NET: Registered protocol family 17
[  161.976210] ppdev0: registered pardevice
[  162.024282] ppdev0: unregistered pardevice
[  162.412448] ppdev0: registered pardevice
[  162.460479] ppdev0: unregistered pardevice
[  163.539650] ppdev0: registered pardevice
[  163.588169] ppdev0: unregistered pardevice
[  163.791942] type=1503 audit(1232277203.652:5): operation="inode_permission" requested_mask="r::" denied_mask="r::" fsuid=7 name="/proc/5845/net/" pid=5845 profile="/usr/sbin/cupsd"
[  164.036305] NET: Registered protocol family 10
[  164.040822] lo: Disabled Privacy Extensions
[  164.055268] type=1503 audit(1232277203.916:6): operation="socket_create" family="ax25" sock_type="dgram" protocol=0 pid=5845 profile="/usr/sbin/cupsd"
[  164.055304] type=1503 audit(1232277203.916:7): operation="socket_create" family="netrom" sock_type="seqpacket" protocol=0 pid=5845 profile="/usr/sbin/cupsd"
[  164.055325] type=1503 audit(1232277203.916:8): operation="socket_create" family="rose" sock_type="dgram" protocol=0 pid=5845 profile="/usr/sbin/cupsd"
[  164.055347] type=1503 audit(1232277203.916:9): operation="socket_create" family="ipx" sock_type="dgram" protocol=0 pid=5845 profile="/usr/sbin/cupsd"
[  164.055368] type=1503 audit(1232277203.916:10): operation="socket_create" family="appletalk" sock_type="dgram" protocol=0 pid=5845 profile="/usr/sbin/cupsd"
[  164.055391] type=1503 audit(1232277203.916:11): operation="socket_create" family="econet" sock_type="dgram" protocol=0 pid=5845 profile="/usr/sbin/cupsd"
[  164.055412] type=1503 audit(1232277203.916:12): operation="socket_create" family="ash" sock_type="dgram" protocol=0 pid=5845 profile="/usr/sbin/cupsd"
[  164.055434] type=1503 audit(1232277203.916:13): operation="socket_create" family="x25" sock_type="seqpacket" protocol=0 pid=5845 profile="/usr/sbin/cupsd"
[  164.055563] type=1503 audit(1232277203.916:14): operation="inode_permission" requested_mask="::r" denied_mask="::r" fsuid=7 name="/proc/5845/net/dev" pid=5845 profile="/usr/sbin/cupsd"

```


```
jeff@jeff-laptop:~$ sudo lshw -C network
[sudo] password for jeff: 
  *-network               
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32 module=ssb
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:90:96:c4:7c:5e
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: pan0
       serial: 66:f3:88:ca:4e:26
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```

```
jeff@jeff-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

pan0      Interface doesn't support scanning.

```

```

jeff@jeff-laptop:~$ lsb_release -d
Description:	Ubuntu 8.10

```

```
jeff@jeff-laptop:~$ uname -mr
2.6.27-7-generic i686

```

```

jeff@jeff-laptop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                               [ OK ] 
```

---

### Post by diablo75 on 2009-01-19
Doesn't look like it's detecting an interface.  Is it possible that your BIOS has the ability to enable/disable it?

---

### Post by grandiloq on 2009-01-19
BIOS does have that ability, but it is not disabled there.  If I boot Puppy Linux, wireless works.  There is a key combo--fn F2--that turns the card on or off, and I've tried hitting it. But it doesn't make any difference when I'm in Ubuntu.

Ubuntu actually seems to see it, and wants to install the firmware using fwcutter--using the "Install Hardware drivers" or whatever it's called--but can't because I'm not connected to the internet.  I actually tried Kubuntu and GOS live CDs too, just to see, but the exact same thing happened.  What's the deal with Puppy Linux, I wonder, are they using some kind of weird driver for it?

---

### Post by grandiloq on 2009-01-19
OK then, it seems that if I follow the directions here:
[http://linuxwireless.org/en/users/Drivers/b43]("http://linuxwireless.org/en/users/Drivers/b43")
I should be able to get it done if I download the driver to disk first, and simply point the script to its local path rather than to its URL, correct?

(because my main hurdle at the moment is that the machine I'm trying to update the firmware on cannot connect to the internet, wired OR wireless--otherwise things are working fine)

---

