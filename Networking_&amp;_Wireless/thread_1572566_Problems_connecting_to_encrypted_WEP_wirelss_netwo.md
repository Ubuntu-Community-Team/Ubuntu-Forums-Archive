---
title: "Problems connecting to encrypted WEP wirelss network"
date: 2010-09-11
forum: Networking &amp; Wireless
---

### Post by uranium165 on 2010-09-11
Hi

I am unable to connect to my home wireless network when WEP 128 bit encryption (open system passphrase) is turned on however I can connect when I disable the encryption?
Please help, spent ~20hrs trying to sort this to no avail

```

1- Compaq nx6110 running Ubuntu 10.04 LTS Lucid Lynx

2- lspci
02:04.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)

3a- ifconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:"101"  
          Mode:Managed  Frequency=2.462 GHz  Access Point: 00:0A:04:99:4D:4D   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

3b- iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:"101"  
          Mode:Managed  Frequency=2.462 GHz  Access Point: 00:0A:04:99:4D:4D   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

4- lsmod
Module                  Size  Used by
arc4                    1153  0 
lib80211_crypt_wep      2667  0 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
binfmt_misc             6587  1 
ppdev                   5259  0 
joydev                  8708  0 
snd_intel8x0           25588  2 
snd_ac97_codec        100646  1 snd_intel8x0
ac97_bus                1002  1 snd_ac97_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
pcmcia                 33024  0 
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
i915                  285076  3 
snd                    54148  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ipw2200               135216  0 
drm_kms_helper         29297  1 i915
yenta_socket           20408  1 
rsrc_nonstatic         10015  1 yenta_socket
libipw                 39896  1 ipw2200
intel_agp              24119  2 i915
soundcore               6620  1 snd
drm                   162377  4 i915,drm_kms_helper
i2c_algo_bit            5028  1 i915
lib80211                5046  3 lib80211_crypt_wep,ipw2200,libipw
pcmcia_core            32964  3 pcmcia,yenta_socket,rsrc_nonstatic
psmouse                63245  0 
serio_raw               3978  0 
snd_page_alloc          7076  2 snd_intel8x0,snd_pcm
agpgart                31724  2 intel_agp,drm
video                  17375  1 i915
output                  1871  1 video
lp                      7028  0 
parport                32635  2 ppdev,lp
b44                    25574  0 
ohci1394               26950  0 
ssb                    38671  1 b44
mii                     4381  1 b44
ieee1394               81181  1 ohci1394

5- dmesg
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 1f800000 (gap: 1f800000:c0800000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @c1400000 s36056 r0 d21288 u4194304
[    0.000000] pcpu-alloc: s36056 r0 d21288 u4194304 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 127867
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-24-generic root=UUID=eaeda3c3-00d9-4f3c-a36e-7e59715d1e9d ro quiet splash
[    0.000000] PID hash table entries: 2048 (order: 1, 8192 bytes)
[    0.000000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 2579520 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (00000000:00000000)
[    0.000000] Memory: 492364k/515904k available (4679k kernel code, 22892k reserved, 2116k data, 660k init, 0k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xdffd0000 - 0xff7fe000   ( 504 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xdf7d0000   ( 503 MB)
[    0.000000]       .init : 0xc07a3000 - 0xc0848000   ( 660 kB)
[    0.000000]       .data : 0xc0591d43 - 0xc07a2e88   (2116 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0591d43   (4679 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:2304 nr_irqs:256
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 800.043 MHz processor.
[    0.008007] Calibrating delay loop (skipped), value calculated using timer frequency.. 1600.08 BogoMIPS (lpj=3200172)
[    0.008043] Security Framework initialized
[    0.008087] AppArmor: AppArmor initialized
[    0.008102] Mount-cache hash table entries: 512
[    0.008339] Initializing cgroup subsys ns
[    0.008349] Initializing cgroup subsys cpuacct
[    0.008359] Initializing cgroup subsys memory
[    0.008378] Initializing cgroup subsys devices
[    0.008384] Initializing cgroup subsys freezer
[    0.008390] Initializing cgroup subsys net_cls
[    0.008433] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.008440] CPU: L2 cache: 2048K
[    0.008448] mce: CPU supports 5 MCE banks
[    0.008465] CPU0: Thermal monitoring enabled (TM2)
[    0.008482] Performance Events: p6 PMU driver.
[    0.008520] ... version:                0
[    0.008525] ... bit width:              32
[    0.008529] ... generic registers:      2
[    0.008535] ... value mask:             00000000ffffffff
[    0.008540] ... max period:             000000007fffffff
[    0.008545] ... fixed-purpose events:   0
[    0.008550] ... event mask:             0000000000000003
[    0.008558] Checking 'hlt' instruction... OK.
[    0.025678] SMP alternatives: switching to UP code
[    0.042069] Freeing SMP alternatives: 19k freed
[    0.042086] ACPI: Core revision 20090903
[    0.064037] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.064056] ftrace: allocating 21780 entries in 43 pages
[    0.068101] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.068500] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.109546] CPU0: Intel(R) Pentium(R) M processor 1.73GHz stepping 08
[    0.112001] Brought up 1 CPUs
[    0.112001] Total of 1 processors activated (1600.08 BogoMIPS).
[    0.112001] CPU0 attaching NULL sched-domain.
[    0.112001] devtmpfs: initialized
[    0.112001] HP Compaq Laptop series board detected. Selecting BIOS-method for reboots.
[    0.112001] regulator: core version 0.5
[    0.112001] Time: 13:00:54  Date: 09/11/10
[    0.112001] NET: Registered protocol family 16
[    0.112001] EISA bus registered
[    0.112001] ACPI: bus type pci registered
[    0.112001] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.112001] PCI: MCFG area at e0000000 reserved in E820
[    0.112001] PCI: Using MMCONFIG for extended config space
[    0.112001] PCI: Using configuration type 1 for base access
[    0.112127] bio: create slab <bio-0> at 0
[    0.114128] ACPI: EC: Look up EC in DSDT
[    0.160264] ACPI: Interpreter enabled
[    0.160307] ACPI: (supports S0 S3 S4 S5)
[    0.160349] ACPI: Using IOAPIC for interrupt routing
[    0.179986] ACPI: EC: GPE = 0x10, I/O: command/status = 0x66, data = 0x62
[    0.180135] ACPI: Power Resource [C1C5] (on)
[    0.180340] ACPI: Power Resource [C244] (off)
[    0.180534] ACPI: Power Resource [C245] (off)
[    0.180721] ACPI: Power Resource [C246] (off)
[    0.180907] ACPI: Power Resource [C247] (off)
[    0.181367] ACPI: No dock devices found.
[    0.191347] ACPI: PCI Root Bridge [C002] (0000:00)
[    0.191492] pci 0000:00:02.0: reg 10 32bit mmio: [0xd0400000-0xd047ffff]
[    0.191503] pci 0000:00:02.0: reg 14 io port: [0x7000-0x7007]
[    0.191513] pci 0000:00:02.0: reg 18 32bit mmio pref: [0xc0000000-0xcfffffff]
[    0.191524] pci 0000:00:02.0: reg 1c 32bit mmio: [0xd0480000-0xd04bffff]
[    0.191577] pci 0000:00:02.1: reg 10 32bit mmio: [0xd0500000-0xd057ffff]
[    0.191720] pci 0000:00:1d.0: reg 20 io port: [0x2000-0x201f]
[    0.191798] pci 0000:00:1d.1: reg 20 io port: [0x2020-0x203f]
[    0.191877] pci 0000:00:1d.2: reg 20 io port: [0x2040-0x205f]
[    0.191961] pci 0000:00:1d.3: reg 20 io port: [0x2060-0x207f]
[    0.192054] pci 0000:00:1d.7: reg 10 32bit mmio: [0xd0580000-0xd05803ff]
[    0.192129] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.192139] pci 0000:00:1d.7: PME# disabled
[    0.192277] pci 0000:00:1e.2: reg 10 io port: [0x2100-0x21ff]
[    0.192290] pci 0000:00:1e.2: reg 14 io port: [0x2200-0x223f]
[    0.192304] pci 0000:00:1e.2: reg 18 32bit mmio: [0xd0581000-0xd05811ff]
[    0.192317] pci 0000:00:1e.2: reg 1c 32bit mmio: [0xd0582000-0xd05820ff]
[    0.192366] pci 0000:00:1e.2: PME# supported from D0 D3hot D3cold
[    0.192375] pci 0000:00:1e.2: PME# disabled
[    0.192428] pci 0000:00:1e.3: reg 10 io port: [0x2400-0x24ff]
[    0.192441] pci 0000:00:1e.3: reg 14 io port: [0x2500-0x257f]
[    0.192502] pci 0000:00:1e.3: PME# supported from D0 D3hot D3cold
[    0.192510] pci 0000:00:1e.3: PME# disabled
[    0.192619] pci 0000:00:1f.0: Force enabled HPET at 0xfed00000
[    0.192632] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[    0.192642] pci 0000:00:1f.0: quirk: region 1100-113f claimed by ICH6 GPIO
[    0.192651] pci 0000:00:1f.0: LPC Generic IO decode 1 PIO at 0500-057f
[    0.192693] pci 0000:00:1f.1: reg 10 io port: [0x00-0x07]
[    0.192706] pci 0000:00:1f.1: reg 14 io port: [0x00-0x03]
[    0.192718] pci 0000:00:1f.1: reg 18 io port: [0x00-0x07]
[    0.192731] pci 0000:00:1f.1: reg 1c io port: [0x00-0x03]
[    0.192744] pci 0000:00:1f.1: reg 20 io port: [0x2580-0x258f]
[    0.192851] pci 0000:02:04.0: reg 10 32bit mmio: [0xd0000000-0xd0000fff]
[    0.192934] pci 0000:02:04.0: PME# supported from D0 D3hot D3cold
[    0.192944] pci 0000:02:04.0: PME# disabled
[    0.193010] pci 0000:02:06.0: reg 10 32bit mmio: [0xd0001000-0xd0001fff]
[    0.193045] pci 0000:02:06.0: supports D1 D2
[    0.193051] pci 0000:02:06.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.193061] pci 0000:02:06.0: PME# disabled
[    0.193123] pci 0000:02:06.2: reg 10 32bit mmio: [0xd0002000-0xd00027ff]
[    0.193139] pci 0000:02:06.2: reg 14 32bit mmio: [0xd0004000-0xd0007fff]
[    0.193217] pci 0000:02:06.2: supports D1 D2
[    0.193223] pci 0000:02:06.2: PME# supported from D0 D1 D2 D3hot
[    0.193232] pci 0000:02:06.2: PME# disabled
[    0.193311] pci 0000:02:0e.0: reg 10 32bit mmio: [0xd000e000-0xd000ffff]
[    0.193382] pci 0000:02:0e.0: supports D1 D2
[    0.193388] pci 0000:02:0e.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.193396] pci 0000:02:0e.0: PME# disabled
[    0.193443] pci 0000:00:1e.0: transparent bridge
[    0.193456] pci 0000:00:1e.0: bridge 32bit mmio: [0xd0000000-0xd03fffff]
[    0.193504] pci_bus 0000:00: on NUMA node 0
[    0.193515] ACPI: PCI Interrupt Routing Table [\_SB_.C002._PRT]
[    0.193996] ACPI: PCI Interrupt Routing Table [\_SB_.C002.C068._PRT]
[    0.250488] ACPI: PCI Interrupt Link [C0D8] (IRQs 10 *11)
[    0.250909] ACPI: PCI Interrupt Link [C0D9] (IRQs *10 11)
[    0.251325] ACPI: PCI Interrupt Link [C0DA] (IRQs *10 11)
[    0.251736] ACPI: PCI Interrupt Link [C0DB] (IRQs *10 11)
[    0.252166] ACPI: PCI Interrupt Link [C0EE] (IRQs *10 11)
[    0.252579] ACPI: PCI Interrupt Link [C0EF] (IRQs 10 *11)
[    0.252995] ACPI: PCI Interrupt Link [C0F0] (IRQs *10 11)
[    0.253392] ACPI: PCI Interrupt Link [C0F1] (IRQs 10 11) *0, disabled.
[    0.253713] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.253733] vgaarb: loaded
[    0.254000] SCSI subsystem initialized
[    0.254095] libata version 3.00 loaded.
[    0.254250] usbcore: registered new interface driver usbfs
[    0.254280] usbcore: registered new interface driver hub
[    0.254338] usbcore: registered new device driver usb
[    0.254681] ACPI: WMI: Mapper loaded
[    0.254688] PCI: Using ACPI for IRQ routing
[    0.254970] NetLabel: Initializing
[    0.254975] NetLabel:  domain hash size = 128
[    0.254979] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.255007] NetLabel:  unlabeled traffic allowed by default
[    0.255337] hpet clockevent registered
[    0.255344] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.255356] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.255368] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.260039] Switching to clocksource tsc
[    0.264454] AppArmor: AppArmor Filesystem Enabled
[    0.264477] pnp: PnP ACPI init
[    0.264500] ACPI: bus type pnp registered
[    0.282271] pnp: PnP ACPI: found 11 devices
[    0.282277] ACPI: ACPI bus type pnp unregistered
[    0.282285] PnPBIOS: Disabled by ACPI PNP
[    0.282306] system 00:00: iomem range 0x0-0x9ffff could not be reserved
[    0.282314] system 00:00: iomem range 0xe0000-0xfffff could not be reserved
[    0.282322] system 00:00: iomem range 0x100000-0x1f7fffff could not be reserved
[    0.282343] system 00:08: ioport range 0x500-0x57f has been reserved
[    0.282351] system 00:08: iomem range 0xffb00000-0xffbfffff has been reserved
[    0.282359] system 00:08: iomem range 0xfff00000-0xffffffff has been reserved
[    0.282372] system 00:09: ioport range 0x4d0-0x4d1 has been reserved
[    0.282380] system 00:09: ioport range 0x1000-0x107f has been reserved
[    0.282388] system 00:09: ioport range 0x1100-0x113f has been reserved
[    0.282395] system 00:09: ioport range 0x1200-0x121f has been reserved
[    0.282403] system 00:09: iomem range 0xe0000000-0xefffffff has been reserved
[    0.282411] system 00:09: iomem range 0xfec00000-0xfec000ff could not be reserved
[    0.282420] system 00:09: iomem range 0xfed20000-0xff41ffff could not be reserved
[    0.282428] system 00:09: iomem range 0xfed90000-0xfed9afff has been reserved
[    0.282441] system 00:0a: iomem range 0xfeda0000-0xfedbffff has been reserved
[    0.282449] system 00:0a: iomem range 0xfec01000-0xfec01fff has been reserved
[    0.317372] pci 0000:02:06.0: CardBus bridge, secondary bus 0000:03
[    0.317380] pci 0000:02:06.0:   IO window: 0x003000-0x0030ff
[    0.317390] pci 0000:02:06.0:   IO window: 0x003400-0x0034ff
[    0.317400] pci 0000:02:06.0:   PREFETCH window: 0x20000000-0x23ffffff
[    0.317411] pci 0000:02:06.0:   MEM window: 0x24000000-0x27ffffff
[    0.317421] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:02
[    0.317429] pci 0000:00:1e.0:   IO window: 0x3000-0x3fff
[    0.317440] pci 0000:00:1e.0:   MEM window: 0xd0000000-0xd03fffff
[    0.317450] pci 0000:00:1e.0:   PREFETCH window: 0x20000000-0x23ffffff
[    0.317474] pci 0000:00:1e.0: setting latency timer to 64
[    0.317497]   alloc irq_desc for 18 on node -1
[    0.317502]   alloc kstat_irqs on node -1
[    0.317513] pci 0000:02:06.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.317527] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.317534] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.317542] pci_bus 0000:02: resource 0 io:  [0x3000-0x3fff]
[    0.317549] pci_bus 0000:02: resource 1 mem: [0xd0000000-0xd03fffff]
[    0.317556] pci_bus 0000:02: resource 2 pref mem [0x20000000-0x23ffffff]
[    0.317563] pci_bus 0000:02: resource 3 io:  [0x00-0xffff]
[    0.317569] pci_bus 0000:02: resource 4 mem: [0x000000-0xffffffff]
[    0.317577] pci_bus 0000:03: resource 0 io:  [0x3000-0x30ff]
[    0.317583] pci_bus 0000:03: resource 1 io:  [0x3400-0x34ff]
[    0.317590] pci_bus 0000:03: resource 2 pref mem [0x20000000-0x23ffffff]
[    0.317597] pci_bus 0000:03: resource 3 mem: [0x24000000-0x27ffffff]
[    0.317666] NET: Registered protocol family 2
[    0.317861] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    0.318483] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    0.318690] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[    0.318892] TCP: Hash tables configured (established 16384 bind 16384)
[    0.318898] TCP reno registered
[    0.319032] NET: Registered protocol family 1
[    0.319066] pci 0000:00:02.0: Boot video device
[    0.319413] cpufreq-nforce2: No nForce2 chipset.
[    0.319474] Scanning for low memory corruption every 60 seconds
[    0.319709] audit: initializing netlink socket (disabled)
[    0.319737] type=2000 audit(1284210054.315:1): initialized
[    0.345661] Trying to unpack rootfs image as initramfs...
[    0.372560] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.379617] VFS: Disk quotas dquot_6.5.2
[    0.379754] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.381186] fuse init (API version 7.13)
[    0.381392] msgmni has been set to 962
[    0.384854] alg: No test for stdrng (krng)
[    0.384988] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.384995] io scheduler noop registered
[    0.385000] io scheduler anticipatory registered
[    0.385005] io scheduler deadline registered
[    0.385103] io scheduler cfq registered (default)
[    0.385310] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.385369] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.388066] ACPI: AC Adapter [C172] (off-line)
[    0.388279] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input0
[    0.388288] ACPI: Sleep Button [C1E8]
[    0.388397] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input1
[    0.388527] ACPI: Lid Switch [C1E9]
[    0.388642] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.388649] ACPI: Power Button [PWRF]
[    0.389098] fan PNP0C0B:00: registered as cooling_device0
[    0.389111] ACPI: Fan [C248] (off)
[    0.389489] fan PNP0C0B:01: registered as cooling_device1
[    0.389503] ACPI: Fan [C249] (off)
[    0.389879] fan PNP0C0B:02: registered as cooling_device2
[    0.389892] ACPI: Fan [C24A] (off)
[    0.390263] fan PNP0C0B:03: registered as cooling_device3
[    0.390276] ACPI: Fan [C24B] (off)
[    0.391489] Marking TSC unstable due to TSC halts in idle
[    0.391584] Switching to clocksource hpet
[    0.391738] processor LNXCPU:00: registered as cooling_device4
[    0.438081] thermal LNXTHERM:01: registered as thermal_zone0
[    0.438103] ACPI: Thermal Zone [TZ1] (30 C)
[    0.465005] thermal LNXTHERM:02: registered as thermal_zone1
[    0.465030] ACPI: Thermal Zone [TZ2] (23 C)
[    0.480847] thermal LNXTHERM:03: registered as thermal_zone2
[    0.480875] ACPI: Thermal Zone [TZ3] (23 C)
[    0.485457] thermal LNXTHERM:04: registered as thermal_zone3
[    0.485478] ACPI: Thermal Zone [TZ4] (65 C)
[    0.492819] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.493655]   alloc irq_desc for 22 on node -1
[    0.493661]   alloc kstat_irqs on node -1
[    0.493678] serial 0000:00:1e.3: PCI INT B -> GSI 22 (level, low) -> IRQ 22
[    0.493690] serial 0000:00:1e.3: PCI INT B disabled
[    0.497425] ACPI: Battery Slot [C173] (battery absent)
[    0.497447] isapnp: Scanning for PnP cards...
[    0.503028] brd: module loaded
[    0.506159] loop: module loaded
[    0.506353] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    0.506568] ata_piix 0000:00:1f.1: version 2.13
[    0.506591]   alloc irq_desc for 16 on node -1
[    0.506596]   alloc kstat_irqs on node -1
[    0.506607] ata_piix 0000:00:1f.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.506680] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.507946] scsi0 : ata_piix
[    0.510791] scsi1 : ata_piix
[    0.512156] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x2580 irq 14
[    0.512164] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x2588 irq 15
[    0.513076] Fixed MDIO Bus: probed
[    0.513164] PPP generic driver version 2.4.2
[    0.513257] tun: Universal TUN/TAP device driver, 1.6
[    0.513263] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.513449] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.513488]   alloc irq_desc for 23 on node -1
[    0.513493]   alloc kstat_irqs on node -1
[    0.513503] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.513529] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.513537] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.513613] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.513663] ehci_hcd 0000:00:1d.7: debug port 1
[    0.517542] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.562032] ata2: port disabled. ignoring.
[    0.565929] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xd0580000
[    0.588259] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.588462] usb usb1: configuration #1 chosen from 1 choice
[    0.588536] hub 1-0:1.0: USB hub found
[    0.588554] hub 1-0:1.0: 8 ports detected
[    0.588690] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.588725] uhci_hcd: USB Universal Host Controller Interface driver
[    0.588799] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.588814] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.588821] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.588893] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.588931] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00002000
[    0.589136] usb usb2: configuration #1 chosen from 1 choice
[    0.589196] hub 2-0:1.0: USB hub found
[    0.589211] hub 2-0:1.0: 2 ports detected
[    0.589300]   alloc irq_desc for 17 on node -1
[    0.589305]   alloc kstat_irqs on node -1
[    0.589317] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.589328] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.589336] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.589411] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.589462] uhci_hcd 0000:00:1d.1: irq 17, io base 0x00002020
[    0.589652] usb usb3: configuration #1 chosen from 1 choice
[    0.589712] hub 3-0:1.0: USB hub found
[    0.589727] hub 3-0:1.0: 2 ports detected
[    0.589811] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.589823] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.589830] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.589898] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.589946] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00002040
[    0.590156] usb usb4: configuration #1 chosen from 1 choice
[    0.590217] hub 4-0:1.0: USB hub found
[    0.590232] hub 4-0:1.0: 2 ports detected
[    0.590333]   alloc irq_desc for 19 on node -1
[    0.590339]   alloc kstat_irqs on node -1
[    0.590348] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.590360] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.590367] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.590435] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    0.590482] uhci_hcd 0000:00:1d.3: irq 19, io base 0x00002060
[    0.590675] usb usb5: configuration #1 chosen from 1 choice
[    0.590736] hub 5-0:1.0: USB hub found
[    0.590750] hub 5-0:1.0: 2 ports detected
[    0.590958] PNP: PS/2 Controller [PNP0303:C1C2,PNP0f13:C1C3] at 0x60,0x64 irq 1,12
[    0.592640] i8042.c: Detected active multiplexing controller, rev 1.1.
[    0.595914] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.595928] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    0.595993] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    0.596077] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    0.596170] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    0.596434] mice: PS/2 mouse device common for all mice
[    0.597788] rtc_cmos 00:05: RTC can wake from S4
[    0.597883] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    0.597924] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.598250] device-mapper: uevent: version 1.0.3
[    0.600735] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.604510] ACPI: Battery Slot [C174] (battery present)
[    0.604540] device-mapper: multipath: version 1.1.0 loaded
[    0.604547] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.604826] EISA: Probing bus 0 at eisa.0
[    0.604837] Cannot allocate resource for EISA slot 1
[    0.604843] Cannot allocate resource for EISA slot 2
[    0.604849] Cannot allocate resource for EISA slot 3
[    0.604869] Cannot allocate resource for EISA slot 7
[    0.604879] EISA: Detected 0 cards.
[    0.609532] cpuidle: using governor ladder
[    0.609713] cpuidle: using governor menu
[    0.610714] TCP cubic registered
[    0.611111] NET: Registered protocol family 10
[    0.612142] lo: Disabled Privacy Extensions
[    0.612884] NET: Registered protocol family 17
[    0.618968] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    0.624922] Using IPI No-Shortcut mode
[    0.625005] PM: Resume from disk failed.
[    0.625015] registered taskstats version 1
[    0.626318]   Magic number: 10:184:28
[    0.626448] rtc_cmos 00:05: setting system clock to 2010-09-11 13:00:55 UTC (1284210055)
[    0.626452] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.626454] EDD information not available.
[    0.781033] ata1.00: ATA-6: ST94813A, 3.04, max UDMA/100
[    0.781038] ata1.00: 78140160 sectors, multi 16: LBA48 
[    0.781083] ata1.01: ATAPI: HL-DT-STCD-RW/DVD DRIVE GCC-4244N, 1.02, max MWDMA2
[    0.796657] ata1.00: configured for UDMA/100
[    0.812545] ata1.01: configured for MWDMA2
[    1.035428] Freeing initrd memory: 7775k freed
[    1.129690] isapnp: No Plug & Play device found
[    1.129918] scsi 0:0:0:0: Direct-Access     ATA      ST94813A         3.04 PQ: 0 ANSI: 5
[    1.130174] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.132586] sd 0:0:0:0: [sda] 78140160 512-byte logical blocks: (40.0 GB/37.2 GiB)
[    1.132642] sd 0:0:0:0: [sda] Write Protect is off
[    1.132645] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.132674] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.132851]  sda: sda1 sda2 <
[    1.147824] scsi 0:0:1:0: CD-ROM            HL-DT-ST RW/DVD GCC-4244N 1.02 PQ: 0 ANSI: 5
[    1.174899]  sda5 >
[    1.177691] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.185590] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    1.185593] Uniform CD-ROM driver Revision: 3.20
[    1.185682] sr 0:0:1:0: Attached scsi CD-ROM sr0
[    1.185741] sr 0:0:1:0: Attached scsi generic sg1 type 5
[    1.185797] Freeing unused kernel memory: 660k freed
[    1.186283] Write protecting the kernel text: 4680k
[    1.186323] Write protecting the kernel read-only data: 1840k
[    1.202956] udev: starting version 151
[    1.472730] ohci1394 0000:02:06.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    1.532071] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[22]  MMIO=[d0002000-d00027ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    1.532244] b44 0000:02:0e.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.592138] ssb: Sonics Silicon Backplane found on PCI device 0000:02:0e.0
[    1.592321] b44.c:v2.0
[    1.612917] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:14:c2:e4:c7:22
[    1.630694] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[    1.630700] EXT4-fs (sda1): write access will be enabled during recovery
[    2.746689] EXT4-fs (sda1): orphan cleanup on readonly fs
[    2.746700] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 2097392
[    2.746780] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 2097391
[    2.746795] EXT4-fs (sda1): 2 orphan inodes deleted
[    2.746799] EXT4-fs (sda1): recovery complete
[    2.799126] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    2.804173] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[718b500029f507a6]
[   14.641062] udev: starting version 151
[   14.725100] Adding 1467384k swap on /dev/sda5.  Priority:-1 extents:1 across:1467384k 
[   14.869095] lp: driver loaded but no devices found
[   14.869155] intel_rng: FWH not detected
[   14.907824] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input5
[   14.907892] ACPI: Video Device [C055] (multi-head: yes  rom: no  post: no)
[   15.081894] Linux agpgart interface v0.103
[   15.154831] lib80211: common routines for IEEE802.11 drivers
[   15.154836] lib80211_crypt: registered algorithm 'NULL'
[   15.270762] [drm] Initialized drm 1.1.0 20060810
[   15.276362] agpgart-intel 0000:00:00.0: Intel 915GM Chipset
[   15.276904] agpgart-intel 0000:00:00.0: detected 7932K stolen memory
[   15.297135] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   15.297140] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   15.297195] yenta_cardbus 0000:02:06.0: CardBus bridge found [103c:099c]
[   15.297299] yenta_cardbus 0000:02:06.0: Enabling burst memory read transactions
[   15.297306] yenta_cardbus 0000:02:06.0: Using INTVAL to route CSC interrupts to PCI
[   15.297309] yenta_cardbus 0000:02:06.0: Routing CardBus interrupts to PCI
[   15.297316] yenta_cardbus 0000:02:06.0: TI: mfunc 0x01aa1b22, devctl 0x64
[   15.301400] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xc0000000
[   15.330993] type=1505 audit(1284210070.201:2):  operation="profile_load" pid=581 name="/sbin/dhclient3"
[   15.331693] type=1505 audit(1284210070.201:3):  operation="profile_load" pid=581 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   15.337072] type=1505 audit(1284210070.209:4):  operation="profile_load" pid=581 name="/usr/lib/connman/scripts/dhclient-script"
[   15.351306] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   15.351310] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   15.444395] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   15.444405] i915 0000:00:02.0: setting latency timer to 64
[   15.462748] [drm] set up 7M of stolen space
[   15.565894] yenta_cardbus 0000:02:06.0: ISA IRQ mask 0x0cf8, PCI irq 18
[   15.565900] yenta_cardbus 0000:02:06.0: Socket status: 30000006
[   15.565904] pci_bus 0000:02: Raising subordinate bus# of parent bus (#02) from #03 to #06
[   15.565916] yenta_cardbus 0000:02:06.0: pcmcia: parent PCI bridge I/O window: 0x3000 - 0x3fff
[   15.565921] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3000-0x3fff: clean.
[   15.566172] yenta_cardbus 0000:02:06.0: pcmcia: parent PCI bridge Memory window: 0xd0000000 - 0xd03fffff
[   15.566176] yenta_cardbus 0000:02:06.0: pcmcia: parent PCI bridge Memory window: 0x20000000 - 0x23ffffff
[   15.573644]   alloc irq_desc for 21 on node -1
[   15.573648]   alloc kstat_irqs on node -1
[   15.573657] ipw2200 0000:02:04.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   15.578461] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   15.578534] ipw2200 0000:02:04.0: firmware: requesting ipw2200-bss.fw
[   15.814661] type=1505 audit(1284210070.685:5):  operation="profile_load" pid=705 name="/usr/share/gdm/guest-session/Xsession"
[   15.817256] type=1505 audit(1284210070.689:6):  operation="profile_replace" pid=706 name="/sbin/dhclient3"
[   15.817953] type=1505 audit(1284210070.689:7):  operation="profile_replace" pid=706 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   15.818336] type=1505 audit(1284210070.689:8):  operation="profile_replace" pid=706 name="/usr/lib/connman/scripts/dhclient-script"
[   15.829968] type=1505 audit(1284210070.701:9):  operation="profile_load" pid=707 name="/usr/bin/evince"
[   15.863249] type=1505 audit(1284210070.733:10):  operation="profile_load" pid=707 name="/usr/bin/evince-previewer"
[   15.864953] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x25a0b1, caps: 0xa04793/0x300000
[   15.864962] serio: Synaptics pass-through port at isa0060/serio4/input0
[   15.875918] type=1505 audit(1284210070.745:11):  operation="profile_load" pid=707 name="/usr/bin/evince-thumbnailer"
[   15.961766] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
[   15.963462] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: clean.
[   15.965013] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   15.965609] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   15.966376] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   15.976637] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input6
[   16.006278] [drm] initialized overlay support
[   16.262431] ipw2200: Detected geography ZZR (14 802.11bg channels, 0 802.11a channels)
[   16.329055] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   16.617368] ppdev: user-space parallel port driver
[   16.773710] fb0: inteldrmfb frame buffer device
[   16.773715] registered panic notifier
[   16.773725] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   16.773777] Intel ICH 0000:00:1e.2: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   16.773800] Intel ICH 0000:00:1e.2: setting latency timer to 64
[   16.780702] vga16fb: initializing
[   16.780707] vga16fb: mapped to 0xc00a0000
[   16.780712] vga16fb: not registering due to another framebuffer present
[   16.912699] Console: switching to colour frame buffer device 128x48
[   17.700050] intel8x0_measure_ac97_clock: measured 55371 usecs (2668 samples)
[   17.700054] intel8x0: clocking to 48000
[   27.292023] eth1: no IPv6 routers present
[   39.891910] lib80211_crypt: registered algorithm 'WEP'
[ 1212.000236] b44: eth0: Link is up at 100 Mbps, full duplex.
[ 1212.000244] b44: eth0: Flow control is off for TX and off for RX.
[ 1212.000409] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 1222.580069] eth0: no IPv6 routers present

6- sudo lshw -C network
  *-network:0             
       description: Wireless interface
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 4
       bus info: pci@0000:02:04.0
       logical name: eth1
       version: 05
       serial: 00:15:00:4d:63:f3
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) latency=64 link=no maxlatency=24 mingnt=3 multicast=yes wireless=unassociated
       resources: irq:21 memory:d0000000-d0000fff
  *-network:1
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: e
       bus info: pci@0000:02:0e.0
       logical name: eth0
       version: 02
       serial: 00:14:c2:e4:c7:22
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.1.173 latency=64 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:16 memory:d000e000-d000ffff

7- iwlist scan
          Cell 01 - Address: 00:1F:33:EE:A4:60
                    ESSID:"NETGEAR"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=27/100  Signal level=-83 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 412ms ago
          Cell 02 - Address: 00:14:7F:B8:BF:FC
                    ESSID:"BTHomeHub-0B47"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.442 GHz (Channel 7)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=27/100  Signal level=-83 dBm  
                    Extra: Last beacon: 256ms ago
          Cell 03 - Address: 00:0A:04:99:4D:4D
                    ESSID:"101"
                    Protocol:IEEE 802.11b
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Quality=79/100  Signal level=-27 dBm  
                    Extra: Last beacon: 24ms ago
          Cell 04 - Address: 00:14:6C:1F:CA:54
                    ESSID:"COUPER"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 9 Mb/s; 11 Mb/s
                              6 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=31/100  Signal level=-81 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    Extra: Last beacon: 164ms ago
          Cell 05 - Address: 00:1E:74:9F:B3:FF
                    ESSID:"SKY46078"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=48/100  Signal level=-72 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 908ms ago

8- lsb_release -d
Description:	Ubuntu 10.04.1 LTS

9- uname -mr
2.6.32-24-generic i686

10- sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                                                                    Ignoring unknown interface eth0=eth0.




```

---

### Post by ramjet_1953 on 2010-11-07
Check-out this post and try the fix that worked for me.

[http://ubuntuforums.org/showthread.php?t=1496856&highlight=Intel+2200BG](http://ubuntuforums.org/showthread.php?t=1496856&highlight=Intel+2200BG)

Last time I looked it was the last post in this thread.

Regards,
Roger:)

---

