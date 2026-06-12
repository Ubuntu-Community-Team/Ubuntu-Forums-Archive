---
title: "wireless connection disconnect after 2 hours reboot needed"
date: 2010-07-20
forum: Networking &amp; Wireless
---

### Post by JTJ_ on 2010-07-20
Edit bodhi.zazen:

Please do not post such long blocks of messages directly on the forums. Attach the output as .txt or use a pasetebin.
[ ]("http://pastebin.com/aAKLfEde")

---

### Post by cwscribner on 2010-07-20
Hardware issue maybe?  I know this isn't particularly helpful but this seems fairly isolated.  Try replicating this on another install.

---

### Post by JTJ_ on 2010-07-20
i already have tried on diff install same problem added info for someone that can help or knows a solution 
thanks

---

### Post by JTJ_ on 2010-07-21
j@ubuntu:~$ iwconfig
    
                                                 lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"SKY49983"  
          Mode:Managed  Frequency:2.412 GHz  Access Point:  00:24:01:A5:58:81   
          Bit Rate=1 Mb/s   Tx-Power=27 dBm   
          Retry  long limit:7   RTS thrff   Fragment thrff
          Power Managementff
          Link Quality=14/100  Signal level=14/100  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0                      

output of lsmod

   
                                                 @ubuntu:~$ lsmod
Module                  Size  Used by
aes_i586                7268  1 
aes_generic            26863  1 aes_i586
nls_utf8                1069  1 
isofs                  29250  1 
binfmt_misc             6587  1 
snd_hda_codec_realtek   203310  1 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
arc4                    1153  2 
vga16fb                11385  0 
vgastate                8961  1 vga16fb
snd_hda_intel          21941  4 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  4 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
rtl8180                26346  0 
snd_seq                47263  6  snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_mid  i_event
i915                  285076  3 
snd_timer              19098  2 snd_pcm,snd_seq
drm_kms_helper         29297  1 i915
mac80211              205146  1 rtl8180
snd_seq_device          5700  5  snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi  ,snd_seq
drm                   162377  4 i915,drm_kms_helper
eeprom_93cx6            1333  1 rtl8180
snd                    54148  19  snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,   snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_se   q_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_algo_bit            5028  1 i915
soundcore               6620  1 snd
cfg80211              126517  2 rtl8180,mac80211
video                  17375  1 i915
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
ppdev                   5259  0 
psmouse                63245  0 
output                  1871  1 video
intel_agp              24119  2 i915
parport_pc             25962  1 
agpgart                31724  2 drm,intel_agp
serio_raw               3978  0 
lp                      7028  0 
parport                32635  3 ppdev,parport_pc,lp
floppy                 53016  0 
r8169                  34076  0 
mii                     4381  1 r8169                      

output of dmesg

      
                                                 0.164095] CPU1: Intel Pentium(R) Dual-Core  CPU      E6300  @  2.80GHz stepping 0a
[    0.164105] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.168015] Brought up 2 CPUs
[    0.168017] Total of 2 processors activated (11150.30 BogoMIPS).
[    0.168436] CPU0 attaching sched-domain:
[    0.168439]  domain 0: span 0-1 level MC
[    0.168440]   groups: 0 1
[    0.168445] CPU1 attaching sched-domain:
[    0.168446]  domain 0: span 0-1 level MC
[    0.168448]   groups: 1 0
[    0.168526] devtmpfs: initialized
[    0.168526] regulator: core version 0.5
[    0.168526] Time: 16:14:08  Date: 07/20/10
[    0.168526] NET: Registered protocol family 16
[    0.168526] Trying to unpack rootfs image as initramfs...
[    0.168526] EISA bus registered
[    0.168526] ACPI: bus type pci registered
[    0.168526] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0  - 255
[    0.168526] PCI: Not using MMCONFIG.
[    0.168526] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=3
[    0.168526] PCI: Using configuration type 1 for base access
[    0.172080] bio: create slab <bio-0> at 0
[    0.172688] ACPI: EC: Look up EC in DSDT
[    0.175590] ACPI: Executed 1 blocks of module-level executable AML  code
[    0.179106] ACPI: Interpreter enabled
[    0.179116] ACPI: (supports S0 S1 S4 S5)
[    0.179135] ACPI: Using IOAPIC for interrupt routing
[    0.179176] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0  - 255
[    0.183228] PCI: MCFG area at e0000000 reserved in ACPI motherboard  resources
[    0.183230] PCI: Using MMCONFIG for extended config space
[    0.189803] ACPI Warning: Incorrect checksum in table [OEMB] - D4,  should be C7 (20090903/tbutils-314)
[    0.190568] ACPI: No dock devices found.
[    0.190684] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.190751] pci 0000:00:02.0: reg 10 32bit mmio:  [0xfe980000-0xfe9fffff]
[    0.190754] pci 0000:00:02.0: reg 14 io port: [0xcc00-0xcc07]
[    0.190758] pci 0000:00:02.0: reg 18 32bit mmio pref:  [0xd0000000-0xdfffffff]
[    0.190762] pci 0000:00:02.0: reg 1c 32bit mmio:  [0xfe800000-0xfe8fffff]
[    0.190825] pci 0000:00:1b.0: reg 10 64bit mmio:  [0xfe978000-0xfe97bfff]
[    0.190864] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.190868] pci 0000:00:1b.0: PME# disabled
[    0.190920] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.190924] pci 0000:00:1c.0: PME# disabled
[    0.190978] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.190981] pci 0000:00:1c.1: PME# disabled
[    0.191023] pci 0000:00:1d.0: reg 20 io port: [0xc880-0xc89f]
[    0.191065] pci 0000:00:1d.1: reg 20 io port: [0xc800-0xc81f]
[    0.191106] pci 0000:00:1d.2: reg 20 io port: [0xc480-0xc49f]
[    0.191149] pci 0000:00:1d.3: reg 20 io port: [0xc400-0xc41f]
[    0.191194] pci 0000:00:1d.7: reg 10 32bit mmio:  [0xfe977c00-0xfe977fff]
[    0.191238] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.191242] pci 0000:00:1d.7: PME# disabled
[    0.191351] pci 0000:00:1f.0: Force enabled HPET at 0xfed00000
[    0.191356] pci 0000:00:1f.0: quirk: region 0800-087f claimed by ICH6  ACPI/GPIO/TCO
[    0.191359] pci 0000:00:1f.0: quirk: region 0480-04bf claimed by ICH6  GPIO
[    0.191362] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at  0a00 (mask 00ff)
[    0.191402] pci 0000:00:1f.1: reg 10 io port: [0x00-0x07]
[    0.191407] pci 0000:00:1f.1: reg 14 io port: [0x00-0x03]
[    0.191412] pci 0000:00:1f.1: reg 18 io port: [0x8f0-0x8f7]
[    0.191418] pci 0000:00:1f.1: reg 1c io port: [0x8f8-0x8fb]
[    0.191423] pci 0000:00:1f.1: reg 20 io port: [0xffa0-0xffaf]
[    0.191458] pci 0000:00:1f.2: reg 10 io port: [0xc080-0xc087]
[    0.191463] pci 0000:00:1f.2: reg 14 io port: [0xc000-0xc003]
[    0.191467] pci 0000:00:1f.2: reg 18 io port: [0xbc00-0xbc07]
[    0.191472] pci 0000:00:1f.2: reg 1c io port: [0xb880-0xb883]
[    0.191477] pci 0000:00:1f.2: reg 20 io port: [0xb800-0xb80f]
[    0.191497] pci 0000:00:1f.2: PME# supported from D3hot
[    0.191500] pci 0000:00:1f.2: PME# disabled
[    0.191539] pci 0000:00:1f.3: reg 20 io port: [0x400-0x41f]
[    0.191637] pci 0000:02:00.0: reg 10 io port: [0xd800-0xd8ff]
[    0.191656] pci 0000:02:00.0: reg 18 64bit mmio pref:  [0xfdfff000-0xfdffffff]
[    0.191669] pci 0000:02:00.0: reg 20 64bit mmio pref:  [0xfdfe0000-0xfdfeffff]
[    0.191676] pci 0000:02:00.0: reg 30 32bit mmio pref:  [0xfeae0000-0xfeafffff]
[    0.191712] pci 0000:02:00.0: supports D1 D2
[    0.191713] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot  D3cold
[    0.191717] pci 0000:02:00.0: PME# disabled
[    0.191768] pci 0000:00:1c.1: bridge io port: [0xd000-0xdfff]
[    0.191771] pci 0000:00:1c.1: bridge 32bit mmio:  [0xfea00000-0xfeafffff]
[    0.191776] pci 0000:00:1c.1: bridge 64bit mmio pref:  [0xfdf00000-0xfdffffff]
[    0.191807] pci 0000:03:01.0: reg 10 io port: [0xe800-0xe8ff]
[    0.191813] pci 0000:03:01.0: reg 14 32bit mmio:  [0xfebffc00-0xfebffdff]
[    0.191851] pci 0000:03:01.0: supports D1 D2
[    0.191852] pci 0000:03:01.0: PME# supported from D1 D2 D3hot D3cold
[    0.191856] pci 0000:03:01.0: PME# disabled
[    0.191897] pci 0000:00:1e.0: transparent bridge
[    0.191900] pci 0000:00:1e.0: bridge io port: [0xe000-0xefff]
[    0.191903] pci 0000:00:1e.0: bridge 32bit mmio:  [0xfeb00000-0xfebfffff]
[    0.191918] pci_bus 0000:00: on NUMA node 0
[    0.191921] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.192023] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.192102] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[    0.192141] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P5._PRT]
[    0.194635] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12  14 15)
[    0.194719] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 *11 12  14 15)
[    0.194798] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *10 11 12  14 15)
[    0.194879] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 10 11 12  14 15)
[    0.194958] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12  14 15) *0, disabled.
[    0.195038] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12  14 15) *0, disabled.
[    0.195119] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12  14 15) *0, disabled.
[    0.195199] ACPI: PCI Interrupt Link [LNKH] (IRQs *3 4 5 6 7 10 11 12  14 15)
[    0.195281] vgaarb: device added:  PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=  none
[    0.195289] vgaarb: loaded
[    0.195388] SCSI subsystem initialized
[    0.195458] libata version 3.00 loaded.
[    0.195516] usbcore: registered new interface driver usbfs
[    0.195525] usbcore: registered new interface driver hub
[    0.195544] usbcore: registered new device driver usb
[    0.195634] ACPI: WMI: Mapper loaded
[    0.195635] PCI: Using ACPI for IRQ routing
[    0.195749] NetLabel: Initializing
[    0.195751] NetLabel:  domain hash size = 128
[    0.195752] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.195761] NetLabel:  unlabeled traffic allowed by default
[    0.195865] hpet clockevent registered
[    0.195867] HPET: 3 timers in total, 0 timers will be used for  per-cpu timer
[    0.195871] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.195875] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.200255] Switching to clocksource tsc
[    0.201609] AppArmor: AppArmor Filesystem Enabled
[    0.201621] pnp: PnP ACPI init
[    0.201635] ACPI: bus type pnp registered
[    0.205915] pnp: PnP ACPI: found 18 devices
[    0.205917] ACPI: ACPI bus type pnp unregistered
[    0.205920] PnPBIOS: Disabled by ACPI PNP
[    0.205931] system 00:01: iomem range 0xfed14000-0xfed19fff has been  reserved
[    0.205938] system 00:0b: ioport range 0xa00-0xa0f has been reserved
[    0.205940] system 00:0b: ioport range 0xa10-0xa1f has been reserved
[    0.205942] system 00:0b: ioport range 0xa20-0xa2f has been reserved
[    0.205944] system 00:0b: ioport range 0xa30-0xa3f has been reserved
[    0.205948] system 00:0c: ioport range 0x4d0-0x4d1 has been reserved
[    0.205950] system 00:0c: ioport range 0x800-0x87f has been reserved
[    0.205952] system 00:0c: ioport range 0x480-0x4bf has been reserved
[    0.205954] system 00:0c: iomem range 0xfed1c000-0xfed1ffff has been  reserved
[    0.205956] system 00:0c: iomem range 0xfed20000-0xfed8ffff has been  reserved
[    0.205960] system 00:0e: iomem range 0xffc00000-0xfff7ffff has been  reserved
[    0.205965] system 00:0f: iomem range 0xfec00000-0xfec00fff could not  be reserved
[    0.205967] system 00:0f: iomem range 0xfee00000-0xfee00fff has been  reserved
[    0.205971] system 00:10: iomem range 0xe0000000-0xefffffff has been  reserved
[    0.205975] system 00:11: iomem range 0x0-0x9ffff could not be  reserved
[    0.205977] system 00:11: iomem range 0xc0000-0xcffff could not be  reserved
[    0.205979] system 00:11: iomem range 0xe0000-0xfffff could not be  reserved
[    0.205981] system 00:11: iomem range 0x100000-0x7f6fffff could not  be reserved
[    0.240653] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:01
[    0.240657] pci 0000:00:1c.0:   IO window: 0x1000-0x1fff
[    0.240661] pci 0000:00:1c.0:   MEM window: 0x80000000-0x801fffff
[    0.240664] pci 0000:00:1c.0:   PREFETCH window:  0x00000080200000-0x000000803fffff
[    0.240670] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:02
[    0.240673] pci 0000:00:1c.1:   IO window: 0xd000-0xdfff
[    0.240676] pci 0000:00:1c.1:   MEM window: 0xfea00000-0xfeafffff
[    0.240680] pci 0000:00:1c.1:   PREFETCH window:  0x000000fdf00000-0x000000fdffffff
[    0.240685] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:03
[    0.240687] pci 0000:00:1e.0:   IO window: 0xe000-0xefff
[    0.240691] pci 0000:00:1e.0:   MEM window: 0xfeb00000-0xfebfffff
[    0.240694] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.240706] pci 0000:00:1c.0: enabling device (0104 -> 0107)
[    0.240713]   alloc irq_desc for 16 on node -1
[    0.240714]   alloc kstat_irqs on node -1
[    0.240720] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low)  -> IRQ 16
[    0.240725] pci 0000:00:1c.0: setting latency timer to 64
[    0.240731]   alloc irq_desc for 17 on node -1
[    0.240732]   alloc kstat_irqs on node -1
[    0.240735] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low)  -> IRQ 17
[    0.240738] pci 0000:00:1c.1: setting latency timer to 64
[    0.240743] pci 0000:00:1e.0: setting latency timer to 64
[    0.240747] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.240749] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.240750] pci_bus 0000:01: resource 0 io:  [0x1000-0x1fff]
[    0.240752] pci_bus 0000:01: resource 1 mem: [0x80000000-0x801fffff]
[    0.240754] pci_bus 0000:01: resource 2 pref mem  [0x80200000-0x803fffff]
[    0.240756] pci_bus 0000:02: resource 0 io:  [0xd000-0xdfff]
[    0.240758] pci_bus 0000:02: resource 1 mem: [0xfea00000-0xfeafffff]
[    0.240759] pci_bus 0000:02: resource 2 pref mem  [0xfdf00000-0xfdffffff]
[    0.240761] pci_bus 0000:03: resource 0 io:  [0xe000-0xefff]
[    0.240763] pci_bus 0000:03: resource 1 mem: [0xfeb00000-0xfebfffff]
[    0.240765] pci_bus 0000:03: resource 3 io:  [0x00-0xffff]
[    0.240767] pci_bus 0000:03: resource 4 mem: [0x000000-0xffffffff]
[    0.240797] NET: Registered protocol family 2
[    0.240883] IP route cache hash table entries: 32768 (order: 5,  131072 bytes)
[    0.241146] TCP established hash table entries: 131072 (order: 8,  1048576 bytes)
[    0.241622] TCP bind hash table entries: 65536 (order: 7, 524288  bytes)
[    0.241865] TCP: Hash tables configured (established 131072 bind  65536)
[    0.241867] TCP reno registered
[    0.241945] NET: Registered protocol family 1
[    0.241963] pci 0000:00:02.0: Boot video device
[    0.242188] cpufreq-nforce2: No nForce2 chipset.
[    0.242209] Scanning for low memory corruption every 60 seconds
[    0.242293] audit: initializing netlink socket (disabled)
[    0.242305] type=2000 audit(1279642448.239:1): initialized
[    0.249550] highmem bounce pool size: 64 pages
[    0.249555] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.250665] VFS: Disk quotas dquot_6.5.2
[    0.250707] Dquot-cache hash table entries: 1024 (order 0, 4096  bytes)
[    0.251133] fuse init (API version 7.13)
[    0.251193] msgmni has been set to 1689
[    0.251358] alg: No test for stdrng (krng)
[    0.251397] Block layer SCSI generic (bsg) driver version 0.4 loaded  (major 253)
[    0.251399] io scheduler noop registered
[    0.251401] io scheduler anticipatory registered
[    0.251402] io scheduler deadline registered
[    0.251431] io scheduler cfq registered (default)
[    0.251549]   alloc irq_desc for 24 on node -1
[    0.251550]   alloc kstat_irqs on node -1
[    0.251561] pcieport 0000:00:1c.0: irq 24 for MSI/MSI-X
[    0.251569] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.251664]   alloc irq_desc for 25 on node -1
[    0.251665]   alloc kstat_irqs on node -1
[    0.251671] pcieport 0000:00:1c.1: irq 25 for MSI/MSI-X
[    0.251677] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.251743] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.251804] pciehp: PCI Express Hot Plug Controller Driver version:  0.4
[    0.251888] input: Power Button as  /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.251895] ACPI: Power Button [PWRB]
[    0.251928] input: Power Button as  /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.251929] ACPI: Power Button [PWRF]
[    0.252142] processor LNXCPU:00: registered as cooling_device0
[    0.252169] processor LNXCPU:01: registered as cooling_device1
[    0.254691] thermal LNXTHERM:01: registered as thermal_zone0
[    0.254697] ACPI: Thermal Zone [THRM] (50 C)
[    0.255735] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.255821] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.256089] 00:06: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.256956] brd: module loaded
[    0.257291] loop: module loaded
[    0.257350] input: Macintosh mouse button emulation as  /devices/virtual/input/input2
[    0.257425] ata_piix 0000:00:1f.1: version 2.13
[    0.257438]   alloc irq_desc for 18 on node -1
[    0.257439]   alloc kstat_irqs on node -1
[    0.257445] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level,  low) -> IRQ 18
[    0.257475] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.257552] scsi0 : ata_piix
[    0.257608] isapnp: Scanning for PnP cards...
[    0.306510] scsi1 : ata_piix
[    0.307509] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0  irq 14
[    0.307512] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8  irq 15
[    0.307541]   alloc irq_desc for 19 on node -1
[    0.307543]   alloc kstat_irqs on node -1
[    0.307553] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level,  low) -> IRQ 19
[    0.307557] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    0.307600] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.318102] Freeing initrd memory: 8090k freed
[    0.351065] scsi2 : ata_piix
[    0.355581] scsi3 : ata_piix
[    0.356555] ata3: SATA max UDMA/133 cmd 0xc080 ctl 0xc000 bmdma  0xb800 irq 19
[    0.356558] ata4: SATA max UDMA/133 cmd 0xbc00 ctl 0xb880 bmdma  0xb808 irq 19
[    0.356820] Fixed MDIO Bus: probed
[    0.356845] PPP generic driver version 2.4.2
[    0.356903] tun: Universal TUN/TAP device driver, 1.6
[    0.356905] tun: (C) 1999-2004 Max Krasnyansky  <maxk@qualcomm.com>
[    0.356977] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI)  Driver
[    0.356999]   alloc irq_desc for 23 on node -1
[    0.357001]   alloc kstat_irqs on node -1
[    0.357007] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level,  low) -> IRQ 23
[    0.357021] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.357024] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.357048] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned  bus number 1
[    0.357064] ehci_hcd 0000:00:1d.7: using broken periodic workaround
[    0.357073] ehci_hcd 0000:00:1d.7: debug port 1
[    0.360965] ehci_hcd 0000:00:1d.7: cache line size of 32 is not  supported
[    0.360997] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfe977c00
[    0.375581] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.375645] usb usb1: configuration #1 chosen from 1 choice
[    0.375666] hub 1-0:1.0: USB hub found
[    0.375672] hub 1-0:1.0: 8 ports detected
[    0.375720] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.375730] uhci_hcd: USB Universal Host Controller Interface driver
[    0.375766] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level,  low) -> IRQ 23
[    0.375772] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.375774] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.375797] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned  bus number 2
[    0.375816] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000c880
[    0.375884] usb usb2: configuration #1 chosen from 1 choice
[    0.375905] hub 2-0:1.0: USB hub found
[    0.375910] hub 2-0:1.0: 2 ports detected
[    0.375943] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level,  low) -> IRQ 19
[    0.375947] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.375949] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.375973] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned  bus number 3
[    0.375991] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000c800
[    0.376054] usb usb3: configuration #1 chosen from 1 choice
[    0.376071] hub 3-0:1.0: USB hub found
[    0.376076] hub 3-0:1.0: 2 ports detected
[    0.376106] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level,  low) -> IRQ 18
[    0.376110] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.376112] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.376134] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned  bus number 4
[    0.376158] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000c480
[    0.376225] usb usb4: configuration #1 chosen from 1 choice
[    0.376243] hub 4-0:1.0: USB hub found
[    0.376247] hub 4-0:1.0: 2 ports detected
[    0.376277] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level,  low) -> IRQ 16
[    0.376282] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.376285] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.376306] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned  bus number 5
[    0.376330] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000c400
[    0.376392] usb usb5: configuration #1 chosen from 1 choice
[    0.376410] hub 5-0:1.0: USB hub found
[    0.376414] hub 5-0:1.0: 2 ports detected
[    0.376489] PNP: PS/2 Controller [PNP0303S2K,PNP0f03S2M] at 0x60,0x64 irq  1,12
[    0.376817] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.376822] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.376875] mice: PS/2 mouse device common for all mice
[    0.376951] rtc_cmos 00:03: RTC can wake from S4
[    0.376979] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.376999] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet  irqs
[    0.377072] device-mapper: uevent: version 1.0.3
[    0.377138] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01)  initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[    0.377181] device-mapper: multipath: version 1.1.0 loaded
[    0.377183] device-mapper: multipath round-robin: version 1.0.0  loaded
[    0.377259] EISA: Probing bus 0 at eisa.0
[    0.377263] Cannot allocate resource for EISA slot 1
[    0.377280] EISA: Detected 0 cards.
[    0.377330] cpuidle: using governor ladder
[    0.377331] cpuidle: using governor menu
[    0.377656] TCP cubic registered
[    0.377767] NET: Registered protocol family 10
[    0.378112] lo: Disabled Privacy Extensions
[    0.378356] NET: Registered protocol family 17
[    0.378392] Using IPI No-Shortcut mode
[    0.378446] PM: Resume from disk failed.
[    0.378456] registered taskstats version 1
[    0.378673]   Magic number: 2:374:237
[    0.378732] rtc_cmos 00:03: setting system clock to 2010-07-20  16:14:08 UTC (127964244
[    0.378734] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.378736] EDD information not available.
[    0.445811] input: AT Translated Set 2 keyboard as  /devices/platform/i8042/serio0/input/input3
[    0.492220] ata1.01: NODEV after polling detection
[    0.500172] ata1.00: ATAPI: HP  DVD Writer 400, AH14, max UDMA/33
[    0.516045] ata1.00: configured for UDMA/33
[    0.590030] ata4.01: ATA-7: MAXTOR STM3160215AS, 3.AAD, max UDMA/133
[    0.590032] ata4.01: 312581808 sectors, multi 16: LBA48 NCQ (depth  0/32)
[    0.621729] isapnp: No Plug & Play device found
[    0.630296] scsi 0:0:0:0: CD-ROM            HP       DVD Writer 400c   AH14 PQ: 0 ANSI: 5
[    0.632962] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda  tray
[    0.632965] Uniform CD-ROM driver Revision: 3.20
[    0.633065] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    0.633120] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    0.656696] ata4.01: configured for UDMA/133
[    0.656790] scsi 3:0:1:0: Direct-Access     ATA      MAXTOR STM316021  3.AA PQ: 0 ANSI: 5
[    0.656900] sd 3:0:1:0: [sda] 312581808 512-byte logical blocks: (160  GB/149 GiB)
[    0.656905] sd 3:0:1:0: Attached scsi generic sg1 type 0
[    0.656935] sd 3:0:1:0: [sda] Write Protect is off
[    0.656937] sd 3:0:1:0: [sda] Mode Sense: 00 3a 00 00
[    0.656954] sd 3:0:1:0: [sda] Write cache: enabled, read cache:  enabled, doesn't support DPO or FUA
[    0.657042]  sda: sda1 sda2
[    0.704883] sd 3:0:1:0: [sda] Attached SCSI disk
[    0.704893] Freeing unused kernel memory: 660k freed
[    0.705169] Write protecting the kernel text: 4680k
[    0.705197] Write protecting the kernel read-only data: 1840k
[    0.716477] udev: starting version 151
[    0.768318] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    0.768335] r8169 0000:02:00.0: PCI INT A -> GSI 17 (level, low)  -> IRQ 17
[    0.768370] r8169 0000:02:00.0: setting latency timer to 64
[    0.768413]   alloc irq_desc for 26 on node -1
[    0.768414]   alloc kstat_irqs on node -1
[    0.768426] r8169 0000:02:00.0: irq 26 for MSI/MSI-X
[    0.768919] eth0: RTL8102e at 0xf805c000, 00:30:67:3d:5a:3f, XID  04a00000 IRQ 26
[    0.797603] Floppy drive(s): fd0 is 1.44M
[    0.815047] FDC 0 is a post-1991 82077
[    1.227598] EXT4-fs (loop0): mounted filesystem with ordered data  mode
[   15.566004] udev: starting version 151
[   15.776081] type=1505 audit(1279638863.897:2):   operation="profile_load" pid=632 name="/sbin/dhclient3"
[   15.776587] type=1505 audit(1279638863.897:3):   operation="profile_load" pid=632  name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   15.776849] type=1505 audit(1279638863.897:4):   operation="profile_load" pid=632  name="/usr/lib/connman/scripts/dhclient-script"
[   15.909383] lp: driver loaded but no devices found
[   16.093084] Linux agpgart interface v0.103
[   16.110269] intel_rng: FWH not detected
[   16.112963] parport_pc 00:08: reported by Plug and Play ACPI
[   16.113448] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   16.115310] agpgart-intel 0000:00:00.0: Intel G33 Chipset
[   16.115813] agpgart-intel 0000:00:00.0: detected 7164K stolen memory
[   16.124633] agpgart-intel 0000:00:00.0: AGP aperture is 256M @  0xd0000000
[   16.208722] lp0: using parport0 (interrupt-driven).
[   16.302597] psmouse serio1: ID: 10 00 64
[   16.349436] input: GenPS/2 Genius Mouse as  /devices/platform/i8042/serio1/input/input4
[   16.420423] ppdev: user-space parallel port driver
[   16.490201] cfg80211: Calling CRDA to update world regulatory domain
[   16.608033] cfg80211: World regulatory domain updated:
[   16.608036]     (start_freq - end_freq @ bandwidth),  (max_antenna_gain, max_eirp)
[   16.608038]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi,  2000 mBm)
[   16.608040]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi,  2000 mBm)
[   16.608042]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi,  2000 mBm)
[   16.608044]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi,  2000 mBm)
[   16.608045]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi,  2000 mBm)
[   16.633588] [drm] Initialized drm 1.1.0 20060810
[   16.704858] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low)  -> IRQ 16
[   16.704863] i915 0000:00:02.0: setting latency timer to 64
[   16.708471]   alloc irq_desc for 27 on node -1
[   16.708474]   alloc kstat_irqs on node -1
[   16.708483] i915 0000:00:02.0: irq 27 for MSI/MSI-X
[   16.708489] [drm] set up 7M of stolen space
[   16.708817] [drm] initialized overlay support
[   16.713308] rtl8180 0000:03:01.0: PCI INT A -> GSI 16 (level, low)  -> IRQ 16
[   16.874401] fb0: inteldrmfb frame buffer device
[   16.874403] registered panic notifier
[   16.874895] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on  minor 0
[   16.874930] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level,  low) -> IRQ 16
[   16.874934] hda_intel: position_fix set to 1 for device 1565:820f
[   16.874952] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   16.887363] vga16fb: initializing
[   16.887366] vga16fb: mapped to 0xc00a0000
[   16.887368] vga16fb: not registering due to another framebuffer  present
[   16.897137] phy0: Selected rate control algorithm 'minstrel'
[   16.897679] phy0: hwaddr 00:23:cd:ca:c6:c4, RTL8185vD + rtl8225z2
[   16.932169] Console: switching to colour frame buffer device 160x64
[   16.967220] input: HDA Digital PCBeep as  /devices/pci0000:00/0000:00:1b.0/input/input5
[   17.509464] Adding 261112k swap on /host/ubuntu/disks/swap.disk.   Priority:-1 extents:1 across:261112k 
[   17.650723] type=1505 audit(1279638865.769:5):   operation="profile_load" pid=866  name="/usr/share/gdm/guest-session/Xsession"
[   17.652542] type=1505 audit(1279638865.773:6):   operation="profile_replace" pid=867 name="/sbin/dhclient3"
[   17.653040] type=1505 audit(1279638865.773:7):   operation="profile_replace" pid=867  name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   17.653306] type=1505 audit(1279638865.773::  operation="profile_replace"  pid=867 name="/usr/lib/connman/scripts/dhclient-script"
[   17.656158] type=1505 audit(1279638865.777:9):   operation="profile_load" pid=868 name="/usr/bin/evince"
[   17.663453] r8169: eth0: link down
[   17.663601] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   17.663618] type=1505 audit(1279638865.781:10):   operation="profile_load" pid=868 name="/usr/bin/evince-previewer"
[   17.667621] type=1505 audit(1279638865.785:11):   operation="profile_load" pid=868 name="/usr/bin/evince-thumbnailer"
[   19.195112] CPU0 attaching NULL sched-domain.
[   19.195117] CPU1 attaching NULL sched-domain.
[   19.216191] CPU0 attaching sched-domain:
[   19.216194]  domain 0: span 0-1 level MC
[   19.216196]   groups: 0 1
[   19.216203] CPU1 attaching sched-domain:
[   19.216204]  domain 0: span 0-1 level MC
[   19.216206]   groups: 1 0
[   21.692239] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   22.968720] hda-intel: IRQ timing workaround is activated for card  #0. Suggest a bigger bdl_pos_adj.
[   27.443460] ISO 9660 Extensions: Microsoft Joliet Level 3
[   27.596200] ISOFS: changing to secondary root
[   33.520071] wlan0: deauthenticating from 00:24:01:a5:58:81 by local  choice (reason=3)
[   33.584012] wlan0: direct probe to AP 00:24:01:a5:58:81 (try 1)
[   33.587438] wlan0: direct probe responded
[   33.587441] wlan0: authenticate with AP 00:24:01:a5:58:81 (try 1)
[   33.589114] wlan0: authenticated
[   33.589133] wlan0: associate with AP 00:24:01:a5:58:81 (try 1)
[   33.591462] wlan0: RX AssocResp from 00:24:01:a5:58:81 (capab=0x411  status=0 aid=2)
[   33.591465] wlan0: associated
[   33.591965] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   33.592012] cfg80211: Calling CRDA for country: TW
[   33.593886] cfg80211: Received country IE:
[   33.593888] cfg80211: Regulatory domain: TW
[   33.593889]     (start_freq - end_freq @ bandwidth),  (max_antenna_gain, max_eirp)
[   33.593891]     (2402000 KHz - 2494000 KHz @ 40000 KHz), (10000 mBi,  10000 mBm)
[   33.593893] cfg80211: CRDA thinks this should applied:
[   33.593894] cfg80211: Regulatory domain: TW
[   33.593895]     (start_freq - end_freq @ bandwidth),  (max_antenna_gain, max_eirp)
[   33.593897]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi,  2700 mBm)
[   33.593898]     (5270000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi,  1700 mBm)
[   33.593900]     (5735000 KHz - 5815000 KHz @ 40000 KHz), (300 mBi,  3000 mBm)
[   33.593902] cfg80211: We intersect both of these and get:
[   33.593903] cfg80211: Regulatory domain: 98
[   33.593904]     (start_freq - end_freq @ bandwidth),  (max_antenna_gain, max_eirp)
[   33.593906]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi,  2700 mBm)
[   33.593909] cfg80211: Disabling channel 2467 MHz on phy0 due to  Country IE
[   33.593911] cfg80211: Disabling channel 2472 MHz on phy0 due to  Country IE
[   33.593912] cfg80211: Disabling channel 2484 MHz on phy0 due to  Country IE
[   33.593915] cfg80211: Current regulatory domain updated by AP to: TW
[   33.593916]     (start_freq - end_freq @ bandwidth),  (max_antenna_gain, max_eirp)
[   33.593918]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi,  2700 mBm)
[   33.878904] padlock: VIA PadLock not detected.
[   43.771898] wlan0: no IPv6 routers present
jj@ubuntu:~$ 

output of sudo lshw -c network 

   
                                                 -network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:30:67:3d:5a:3f
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom  ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169  driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes  port=MII speed=10MB/s
       resources: irq:26 ioport:d800(size=256)  memory:fdfff000-fdffffff(prefetchable)  memory:fdfe0000-fdfeffff(prefetchable)  memory:feae0000-feafffff(prefetchable)
  *-network
       description: Wireless interface
       product: RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:03:01.0
       logical name: wlan0
       version: 20
       serial: 00:23:cd:ca:c6:c4
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8180 ip=192.168.1.2  latency=64 maxlatency=64 mingnt=32 multicast=yes wireless=IEEE 802.11bg
       resources: irq:16 ioport:e800(size=256) memory:febffc00-febffdff                      

output of iwlist scan 

lo        Interface doesn't support scanning.

 
                                                 eth0      Interface doesn't support scanning.                      


                             wlan0     Scan completed :
          Cell 01 - Address: 00:24:01:A5:58:81
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=23/100  Signal level=23/100  
                    Encryption keyn
                    ESSID:"SKY49983"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000049e64eaf2
                    Extra: Last beacon: 20928ms ago
                    IE: Unknown: 0008534B593439393833
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown:  2D1A0E1017FFFF0000010000000000000000000000000C0000  000000
                    IE: Unknown:  3D1601050700000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown:  DD180050F2020101000003A4000027A4000042435E0062322F  00
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4304000000
                    IE: Unknown: 0706545720010D10
                    IE: Unknown:  DD1E00904C330E1017FFFF0000010000000000000000000000  000C0000000000
                    IE: Unknown:  DD1A00904C3401050700000000000000000000000000000000  000000

jj@ubuntu:~$ 


output of lsb_Release 
jj@ubuntu:~$ lsb_release -d
Description:    Ubuntu 10.04.1 LTS
jj@ubuntu:~$ 

                                                                                                       

                                                                motherboard 
     Quote:
                                                 asrock lga775                                  
output of lspci
j@ubuntu:~$ lspci
     
                                                 00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express  DRAM Controller (rev 10)
00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express  Integrated Graphics Controller (rev 10)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition  Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1  (rev 01)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2  (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI  Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI  Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI  Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI  Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI  Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC  Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE  Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA IDE  Controller (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev  01)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd.  RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
03:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185  IEEE 802.11a/b/g Wireless LAN Controller (rev 20)                                 
output of lsusb
     Quote:
                                                 Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub                                 
output of ifconfig 
   
                                                 ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:30:67:3d:5a:3f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:26 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:36 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2416 (2.4 KB)  TX bytes:2416 (2.4 KB)

wlan0     Link encap:Ethernet  HWaddr 00:23:cd:ca:c6:c4  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::223:cdff:feca:c6c4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:74688 errors:0 dropped:0 overruns:0 frame:0
          TX packets:51725 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:100731215 (100.7 MB)  TX bytes:5598195 (5.5 MB)
                                  
out put of iwconfig

                                                 ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:30:67:3d:5a:3f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:26 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:36 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2416 (2.4 KB)  TX bytes:2416 (2.4 KB)

wlan0     Link encap:Ethernet  HWaddr 00:23:cd:ca:c6:c4  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::223:cdff:feca:c6c4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:74688 errors:0 dropped:0 overruns:0 frame:0
          TX packets:51725 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:100731215 (100.7 MB)  TX bytes:5598195 (5.5 MB)                                 
jj@ubuntu:~$ iwconfig
 
                                                 lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"SKY49983"  
          Mode:Managed  Frequency:2.412 GHz  Access Point:  00:24:01:A5:58:81   
          Bit Rate=1 Mb/s   Tx-Power=27 dBm   
          Retry  long limit:7   RTS thrff   Fragment thrff
          Power Managementff
          Link Quality=14/100  Signal level=14/100  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0                                 
output of lsmod

                                      @ubuntu:~$ lsmod
Module                  Size  Used by
aes_i586                7268  1 
aes_generic            26863  1 aes_i586
nls_utf8                1069  1 
isofs                  29250  1 
binfmt_misc             6587  1 
snd_hda_codec_realtek   203310  1 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
arc4                    1153  2 
vga16fb                11385  0 
vgastate                8961  1 vga16fb
snd_hda_intel          21941  4 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  4 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
rtl8180                26346  0 
snd_seq                47263  6  snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_mid  i_event
i915                  285076  3 
snd_timer              19098  2 snd_pcm,snd_seq
drm_kms_helper         29297  1 i915
mac80211              205146  1 rtl8180
snd_seq_device          5700  5  snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi  ,snd_seq
drm                   162377  4 i915,drm_kms_helper
eeprom_93cx6            1333  1 rtl8180
snd                    54148  19  snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,   snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_se   q_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_algo_bit            5028  1 i915
soundcore               6620  1 snd
cfg80211              126517  2 rtl8180,mac80211
video                  17375  1 i915
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
ppdev                   5259  0 
psmouse                63245  0 
output                  1871  1 video
intel_agp              24119  2 i915
parport_pc             25962  1 
agpgart                31724  2 drm,intel_agp
serio_raw               3978  0 
lp                      7028  0 
parport                32635  3 ppdev,parport_pc,lp
floppy                 53016  0 
r8169                  34076  0 
mii                     4381  1 r8169                                 
output of dmesg

   
                                                 0.164095] CPU1: Intel Pentium(R) Dual-Core  CPU      E6300  @  2.80GHz stepping 0a
[    0.164105] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.168015] Brought up 2 CPUs
[    0.168017] Total of 2 processors activated (11150.30 BogoMIPS).
[    0.168436] CPU0 attaching sched-domain:
[    0.168439]  domain 0: span 0-1 level MC
[    0.168440]   groups: 0 1
[    0.168445] CPU1 attaching sched-domain:
[    0.168446]  domain 0: span 0-1 level MC
[    0.168448]   groups: 1 0
[    0.168526] devtmpfs: initialized
[    0.168526] regulator: core version 0.5
[    0.168526] Time: 16:14:08  Date: 07/20/10
[    0.168526] NET: Registered protocol family 16
[    0.168526] Trying to unpack rootfs image as initramfs...
[    0.168526] EISA bus registered
[    0.168526] ACPI: bus type pci registered
[    0.168526] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0  - 255
[    0.168526] PCI: Not using MMCONFIG.
[    0.168526] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=3
[    0.168526] PCI: Using configuration type 1 for base access
[    0.172080] bio: create slab <bio-0> at 0
[    0.172688] ACPI: EC: Look up EC in DSDT
[    0.175590] ACPI: Executed 1 blocks of module-level executable AML  code
[    0.179106] ACPI: Interpreter enabled
[    0.179116] ACPI: (supports S0 S1 S4 S5)
[    0.179135] ACPI: Using IOAPIC for interrupt routing
[    0.179176] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0  - 255
[    0.183228] PCI: MCFG area at e0000000 reserved in ACPI motherboard  resources
[    0.183230] PCI: Using MMCONFIG for extended config space
[    0.189803] ACPI Warning: Incorrect checksum in table [OEMB] - D4,  should be C7 (20090903/tbutils-314)
[    0.190568] ACPI: No dock devices found.
[    0.190684] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.190751] pci 0000:00:02.0: reg 10 32bit mmio:  [0xfe980000-0xfe9fffff]
[    0.190754] pci 0000:00:02.0: reg 14 io port: [0xcc00-0xcc07]
[    0.190758] pci 0000:00:02.0: reg 18 32bit mmio pref:  [0xd0000000-0xdfffffff]
[    0.190762] pci 0000:00:02.0: reg 1c 32bit mmio:  [0xfe800000-0xfe8fffff]
[    0.190825] pci 0000:00:1b.0: reg 10 64bit mmio:  [0xfe978000-0xfe97bfff]
[    0.190864] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.190868] pci 0000:00:1b.0: PME# disabled
[    0.190920] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.190924] pci 0000:00:1c.0: PME# disabled
[    0.190978] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.190981] pci 0000:00:1c.1: PME# disabled
[    0.191023] pci 0000:00:1d.0: reg 20 io port: [0xc880-0xc89f]
[    0.191065] pci 0000:00:1d.1: reg 20 io port: [0xc800-0xc81f]
[    0.191106] pci 0000:00:1d.2: reg 20 io port: [0xc480-0xc49f]
[    0.191149] pci 0000:00:1d.3: reg 20 io port: [0xc400-0xc41f]
[    0.191194] pci 0000:00:1d.7: reg 10 32bit mmio:  [0xfe977c00-0xfe977fff]
[    0.191238] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.191242] pci 0000:00:1d.7: PME# disabled
[    0.191351] pci 0000:00:1f.0: Force enabled HPET at 0xfed00000
[    0.191356] pci 0000:00:1f.0: quirk: region 0800-087f claimed by ICH6  ACPI/GPIO/TCO
[    0.191359] pci 0000:00:1f.0: quirk: region 0480-04bf claimed by ICH6  GPIO
[    0.191362] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at  0a00 (mask 00ff)
[    0.191402] pci 0000:00:1f.1: reg 10 io port: [0x00-0x07]
[    0.191407] pci 0000:00:1f.1: reg 14 io port: [0x00-0x03]
[    0.191412] pci 0000:00:1f.1: reg 18 io port: [0x8f0-0x8f7]
[    0.191418] pci 0000:00:1f.1: reg 1c io port: [0x8f8-0x8fb]
[    0.191423] pci 0000:00:1f.1: reg 20 io port: [0xffa0-0xffaf]
[    0.191458] pci 0000:00:1f.2: reg 10 io port: [0xc080-0xc087]
[    0.191463] pci 0000:00:1f.2: reg 14 io port: [0xc000-0xc003]
[    0.191467] pci 0000:00:1f.2: reg 18 io port: [0xbc00-0xbc07]
[    0.191472] pci 0000:00:1f.2: reg 1c io port: [0xb880-0xb883]
[    0.191477] pci 0000:00:1f.2: reg 20 io port: [0xb800-0xb80f]
[    0.191497] pci 0000:00:1f.2: PME# supported from D3hot
[    0.191500] pci 0000:00:1f.2: PME# disabled
[    0.191539] pci 0000:00:1f.3: reg 20 io port: [0x400-0x41f]
[    0.191637] pci 0000:02:00.0: reg 10 io port: [0xd800-0xd8ff]
[    0.191656] pci 0000:02:00.0: reg 18 64bit mmio pref:  [0xfdfff000-0xfdffffff]
[    0.191669] pci 0000:02:00.0: reg 20 64bit mmio pref:  [0xfdfe0000-0xfdfeffff]
[    0.191676] pci 0000:02:00.0: reg 30 32bit mmio pref:  [0xfeae0000-0xfeafffff]
[    0.191712] pci 0000:02:00.0: supports D1 D2
[    0.191713] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot  D3cold
[    0.191717] pci 0000:02:00.0: PME# disabled
[    0.191768] pci 0000:00:1c.1: bridge io port: [0xd000-0xdfff]
[    0.191771] pci 0000:00:1c.1: bridge 32bit mmio:  [0xfea00000-0xfeafffff]
[    0.191776] pci 0000:00:1c.1: bridge 64bit mmio pref:  [0xfdf00000-0xfdffffff]
[    0.191807] pci 0000:03:01.0: reg 10 io port: [0xe800-0xe8ff]
[    0.191813] pci 0000:03:01.0: reg 14 32bit mmio:  [0xfebffc00-0xfebffdff]
[    0.191851] pci 0000:03:01.0: supports D1 D2
[    0.191852] pci 0000:03:01.0: PME# supported from D1 D2 D3hot D3cold
[    0.191856] pci 0000:03:01.0: PME# disabled
[    0.191897] pci 0000:00:1e.0: transparent bridge
[    0.191900] pci 0000:00:1e.0: bridge io port: [0xe000-0xefff]
[    0.191903] pci 0000:00:1e.0: bridge 32bit mmio:  [0xfeb00000-0xfebfffff]
[    0.191918] pci_bus 0000:00: on NUMA node 0
[    0.191921] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.192023] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.192102] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[    0.192141] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P5._PRT]
[    0.194635] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12  14 15)
[    0.194719] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 *11 12  14 15)
[    0.194798] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *10 11 12  14 15)
[    0.194879] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 10 11 12  14 15)
[    0.194958] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12  14 15) *0, disabled.
[    0.195038] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12  14 15) *0, disabled.
[    0.195119] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12  14 15) *0, disabled.
[    0.195199] ACPI: PCI Interrupt Link [LNKH] (IRQs *3 4 5 6 7 10 11 12  14 15)
[    0.195281] vgaarb: device added:  PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=  none
[    0.195289] vgaarb: loaded
[    0.195388] SCSI subsystem initialized
[    0.195458] libata version 3.00 loaded.
[    0.195516] usbcore: registered new interface driver usbfs
[    0.195525] usbcore: registered new interface driver hub
[    0.195544] usbcore: registered new device driver usb
[    0.195634] ACPI: WMI: Mapper loaded
[    0.195635] PCI: Using ACPI for IRQ routing
[    0.195749] NetLabel: Initializing
[    0.195751] NetLabel:  domain hash size = 128
[    0.195752] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.195761] NetLabel:  unlabeled traffic allowed by default
[    0.195865] hpet clockevent registered
[    0.195867] HPET: 3 timers in total, 0 timers will be used for  per-cpu timer
[    0.195871] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.195875] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.200255] Switching to clocksource tsc
[    0.201609] AppArmor: AppArmor Filesystem Enabled
[    0.201621] pnp: PnP ACPI init
[    0.201635] ACPI: bus type pnp registered
[    0.205915] pnp: PnP ACPI: found 18 devices
[    0.205917] ACPI: ACPI bus type pnp unregistered
[    0.205920] PnPBIOS: Disabled by ACPI PNP
[    0.205931] system 00:01: iomem range 0xfed14000-0xfed19fff has been  reserved
[    0.205938] system 00:0b: ioport range 0xa00-0xa0f has been reserved
[    0.205940] system 00:0b: ioport range 0xa10-0xa1f has been reserved
[    0.205942] system 00:0b: ioport range 0xa20-0xa2f has been reserved
[    0.205944] system 00:0b: ioport range 0xa30-0xa3f has been reserved
[    0.205948] system 00:0c: ioport range 0x4d0-0x4d1 has been reserved
[    0.205950] system 00:0c: ioport range 0x800-0x87f has been reserved
[    0.205952] system 00:0c: ioport range 0x480-0x4bf has been reserved
[    0.205954] system 00:0c: iomem range 0xfed1c000-0xfed1ffff has been  reserved
[    0.205956] system 00:0c: iomem range 0xfed20000-0xfed8ffff has been  reserved
[    0.205960] system 00:0e: iomem range 0xffc00000-0xfff7ffff has been  reserved
[    0.205965] system 00:0f: iomem range 0xfec00000-0xfec00fff could not  be reserved
[    0.205967] system 00:0f: iomem range 0xfee00000-0xfee00fff has been  reserved
[    0.205971] system 00:10: iomem range 0xe0000000-0xefffffff has been  reserved
[    0.205975] system 00:11: iomem range 0x0-0x9ffff could not be  reserved
[    0.205977] system 00:11: iomem range 0xc0000-0xcffff could not be  reserved
[    0.205979] system 00:11: iomem range 0xe0000-0xfffff could not be  reserved
[    0.205981] system 00:11: iomem range 0x100000-0x7f6fffff could not  be reserved
[    0.240653] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:01
[    0.240657] pci 0000:00:1c.0:   IO window: 0x1000-0x1fff
[    0.240661] pci 0000:00:1c.0:   MEM window: 0x80000000-0x801fffff
[    0.240664] pci 0000:00:1c.0:   PREFETCH window:  0x00000080200000-0x000000803fffff
[    0.240670] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:02
[    0.240673] pci 0000:00:1c.1:   IO window: 0xd000-0xdfff
[    0.240676] pci 0000:00:1c.1:   MEM window: 0xfea00000-0xfeafffff
[    0.240680] pci 0000:00:1c.1:   PREFETCH window:  0x000000fdf00000-0x000000fdffffff
[    0.240685] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:03
[    0.240687] pci 0000:00:1e.0:   IO window: 0xe000-0xefff
[    0.240691] pci 0000:00:1e.0:   MEM window: 0xfeb00000-0xfebfffff
[    0.240694] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.240706] pci 0000:00:1c.0: enabling device (0104 -> 0107)
[    0.240713]   alloc irq_desc for 16 on node -1
[    0.240714]   alloc kstat_irqs on node -1
[    0.240720] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low)  -> IRQ 16
[    0.240725] pci 0000:00:1c.0: setting latency timer to 64
[    0.240731]   alloc irq_desc for 17 on node -1
[    0.240732]   alloc kstat_irqs on node -1
[    0.240735] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low)  -> IRQ 17
[    0.240738] pci 0000:00:1c.1: setting latency timer to 64
[    0.240743] pci 0000:00:1e.0: setting latency timer to 64
[    0.240747] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.240749] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.240750] pci_bus 0000:01: resource 0 io:  [0x1000-0x1fff]
[    0.240752] pci_bus 0000:01: resource 1 mem: [0x80000000-0x801fffff]
[    0.240754] pci_bus 0000:01: resource 2 pref mem  [0x80200000-0x803fffff]
[    0.240756] pci_bus 0000:02: resource 0 io:  [0xd000-0xdfff]
[    0.240758] pci_bus 0000:02: resource 1 mem: [0xfea00000-0xfeafffff]
[    0.240759] pci_bus 0000:02: resource 2 pref mem  [0xfdf00000-0xfdffffff]
[    0.240761] pci_bus 0000:03: resource 0 io:  [0xe000-0xefff]
[    0.240763] pci_bus 0000:03: resource 1 mem: [0xfeb00000-0xfebfffff]
[    0.240765] pci_bus 0000:03: resource 3 io:  [0x00-0xffff]
[    0.240767] pci_bus 0000:03: resource 4 mem: [0x000000-0xffffffff]
[    0.240797] NET: Registered protocol family 2
[    0.240883] IP route cache hash table entries: 32768 (order: 5,  131072 bytes)
[    0.241146] TCP established hash table entries: 131072 (order: 8,  1048576 bytes)
[    0.241622] TCP bind hash table entries: 65536 (order: 7, 524288  bytes)
[    0.241865] TCP: Hash tables configured (established 131072 bind  65536)
[    0.241867] TCP reno registered
[    0.241945] NET: Registered protocol family 1
[    0.241963] pci 0000:00:02.0: Boot video device
[    0.242188] cpufreq-nforce2: No nForce2 chipset.
[    0.242209] Scanning for low memory corruption every 60 seconds
[    0.242293] audit: initializing netlink socket (disabled)
[    0.242305] type=2000 audit(1279642448.239:1): initialized
[    0.249550] highmem bounce pool size: 64 pages
[    0.249555] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.250665] VFS: Disk quotas dquot_6.5.2
[    0.250707] Dquot-cache hash table entries: 1024 (order 0, 4096  bytes)
[    0.251133] fuse init (API version 7.13)
[    0.251193] msgmni has been set to 1689
[    0.251358] alg: No test for stdrng (krng)
[    0.251397] Block layer SCSI generic (bsg) driver version 0.4 loaded  (major 253)
[    0.251399] io scheduler noop registered
[    0.251401] io scheduler anticipatory registered
[    0.251402] io scheduler deadline registered
[    0.251431] io scheduler cfq registered (default)
[    0.251549]   alloc irq_desc for 24 on node -1
[    0.251550]   alloc kstat_irqs on node -1
[    0.251561] pcieport 0000:00:1c.0: irq 24 for MSI/MSI-X
[    0.251569] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.251664]   alloc irq_desc for 25 on node -1
[    0.251665]   alloc kstat_irqs on node -1
[    0.251671] pcieport 0000:00:1c.1: irq 25 for MSI/MSI-X
[    0.251677] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.251743] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.251804] pciehp: PCI Express Hot Plug Controller Driver version:  0.4
[    0.251888] input: Power Button as  /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.251895] ACPI: Power Button [PWRB]
[    0.251928] input: Power Button as  /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.251929] ACPI: Power Button [PWRF]
[    0.252142] processor LNXCPU:00: registered as cooling_device0
[    0.252169] processor LNXCPU:01: registered as cooling_device1
[    0.254691] thermal LNXTHERM:01: registered as thermal_zone0
[    0.254697] ACPI: Thermal Zone [THRM] (50 C)
[    0.255735] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.255821] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.256089] 00:06: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.256956] brd: module loaded
[    0.257291] loop: module loaded
[    0.257350] input: Macintosh mouse button emulation as  /devices/virtual/input/input2
[    0.257425] ata_piix 0000:00:1f.1: version 2.13
[    0.257438]   alloc irq_desc for 18 on node -1
[    0.257439]   alloc kstat_irqs on node -1
[    0.257445] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level,  low) -> IRQ 18
[    0.257475] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.257552] scsi0 : ata_piix
[    0.257608] isapnp: Scanning for PnP cards...
[    0.306510] scsi1 : ata_piix
[    0.307509] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0  irq 14
[    0.307512] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8  irq 15
[    0.307541]   alloc irq_desc for 19 on node -1
[    0.307543]   alloc kstat_irqs on node -1
[    0.307553] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level,  low) -> IRQ 19
[    0.307557] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    0.307600] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.318102] Freeing initrd memory: 8090k freed
[    0.351065] scsi2 : ata_piix
[    0.355581] scsi3 : ata_piix
[    0.356555] ata3: SATA max UDMA/133 cmd 0xc080 ctl 0xc000 bmdma  0xb800 irq 19
[    0.356558] ata4: SATA max UDMA/133 cmd 0xbc00 ctl 0xb880 bmdma  0xb808 irq 19
[    0.356820] Fixed MDIO Bus: probed
[    0.356845] PPP generic driver version 2.4.2
[    0.356903] tun: Universal TUN/TAP device driver, 1.6
[    0.356905] tun: (C) 1999-2004 Max Krasnyansky  <maxk@qualcomm.com>
[    0.356977] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI)  Driver
[    0.356999]   alloc irq_desc for 23 on node -1
[    0.357001]   alloc kstat_irqs on node -1
[    0.357007] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level,  low) -> IRQ 23
[    0.357021] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.357024] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.357048] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned  bus number 1
[    0.357064] ehci_hcd 0000:00:1d.7: using broken periodic workaround
[    0.357073] ehci_hcd 0000:00:1d.7: debug port 1
[    0.360965] ehci_hcd 0000:00:1d.7: cache line size of 32 is not  supported
[    0.360997] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfe977c00
[    0.375581] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.375645] usb usb1: configuration #1 chosen from 1 choice
[    0.375666] hub 1-0:1.0: USB hub found
[    0.375672] hub 1-0:1.0: 8 ports detected
[    0.375720] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.375730] uhci_hcd: USB Universal Host Controller Interface driver
[    0.375766] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level,  low) -> IRQ 23
[    0.375772] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.375774] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.375797] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned  bus number 2
[    0.375816] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000c880
[    0.375884] usb usb2: configuration #1 chosen from 1 choice
[    0.375905] hub 2-0:1.0: USB hub found
[    0.375910] hub 2-0:1.0: 2 ports detected
[    0.375943] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level,  low) -> IRQ 19
[    0.375947] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.375949] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.375973] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned  bus number 3
[    0.375991] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000c800
[    0.376054] usb usb3: configuration #1 chosen from 1 choice
[    0.376071] hub 3-0:1.0: USB hub found
[    0.376076] hub 3-0:1.0: 2 ports detected
[    0.376106] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level,  low) -> IRQ 18
[    0.376110] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.376112] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.376134] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned  bus number 4
[    0.376158] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000c480
[    0.376225] usb usb4: configuration #1 chosen from 1 choice
[    0.376243] hub 4-0:1.0: USB hub found
[    0.376247] hub 4-0:1.0: 2 ports detected
[    0.376277] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level,  low) -> IRQ 16
[    0.376282] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.376285] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.376306] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned  bus number 5
[    0.376330] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000c400
[    0.376392] usb usb5: configuration #1 chosen from 1 choice
[    0.376410] hub 5-0:1.0: USB hub found
[    0.376414] hub 5-0:1.0: 2 ports detected
[    0.376489] PNP: PS/2 Controller [PNP0303S2K,PNP0f03S2M] at 0x60,0x64 irq  1,12
[    0.376817] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.376822] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.376875] mice: PS/2 mouse device common for all mice
[    0.376951] rtc_cmos 00:03: RTC can wake from S4
[    0.376979] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.376999] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet  irqs
[    0.377072] device-mapper: uevent: version 1.0.3
[    0.377138] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01)  initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[    0.377181] device-mapper: multipath: version 1.1.0 loaded
[    0.377183] device-mapper: multipath round-robin: version 1.0.0  loaded
[    0.377259] EISA: Probing bus 0 at eisa.0
[    0.377263] Cannot allocate resource for EISA slot 1
[    0.377280] EISA: Detected 0 cards.
[    0.377330] cpuidle: using governor ladder
[    0.377331] cpuidle: using governor menu
[    0.377656] TCP cubic registered
[    0.377767] NET: Registered protocol family 10
[    0.378112] lo: Disabled Privacy Extensions
[    0.378356] NET: Registered protocol family 17
[    0.378392] Using IPI No-Shortcut mode
[    0.378446] PM: Resume from disk failed.
[    0.378456] registered taskstats version 1
[    0.378673]   Magic number: 2:374:237
[    0.378732] rtc_cmos 00:03: setting system clock to 2010-07-20  16:14:08 UTC (127964244
[    0.378734] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.378736] EDD information not available.
[    0.445811] input: AT Translated Set 2 keyboard as  /devices/platform/i8042/serio0/input/input3
[    0.492220] ata1.01: NODEV after polling detection
[    0.500172] ata1.00: ATAPI: HP  DVD Writer 400, AH14, max UDMA/33
[    0.516045] ata1.00: configured for UDMA/33
[    0.590030] ata4.01: ATA-7: MAXTOR STM3160215AS, 3.AAD, max UDMA/133
[    0.590032] ata4.01: 312581808 sectors, multi 16: LBA48 NCQ (depth  0/32)
[    0.621729] isapnp: No Plug & Play device found
[    0.630296] scsi 0:0:0:0: CD-ROM            HP       DVD Writer 400c   AH14 PQ: 0 ANSI: 5
[    0.632962] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda  tray
[    0.632965] Uniform CD-ROM driver Revision: 3.20
[    0.633065] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    0.633120] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    0.656696] ata4.01: configured for UDMA/133
[    0.656790] scsi 3:0:1:0: Direct-Access     ATA      MAXTOR STM316021  3.AA PQ: 0 ANSI: 5
[    0.656900] sd 3:0:1:0: [sda] 312581808 512-byte logical blocks: (160  GB/149 GiB)
[    0.656905] sd 3:0:1:0: Attached scsi generic sg1 type 0
[    0.656935] sd 3:0:1:0: [sda] Write Protect is off
[    0.656937] sd 3:0:1:0: [sda] Mode Sense: 00 3a 00 00
[    0.656954] sd 3:0:1:0: [sda] Write cache: enabled, read cache:  enabled, doesn't support DPO or FUA
[    0.657042]  sda: sda1 sda2
[    0.704883] sd 3:0:1:0: [sda] Attached SCSI disk
[    0.704893] Freeing unused kernel memory: 660k freed
[    0.705169] Write protecting the kernel text: 4680k
[    0.705197] Write protecting the kernel read-only data: 1840k
[    0.716477] udev: starting version 151
[    0.768318] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    0.768335] r8169 0000:02:00.0: PCI INT A -> GSI 17 (level, low)  -> IRQ 17
[    0.768370] r8169 0000:02:00.0: setting latency timer to 64
[    0.768413]   alloc irq_desc for 26 on node -1
[    0.768414]   alloc kstat_irqs on node -1
[    0.768426] r8169 0000:02:00.0: irq 26 for MSI/MSI-X
[    0.768919] eth0: RTL8102e at 0xf805c000, 00:30:67:3d:5a:3f, XID  04a00000 IRQ 26
[    0.797603] Floppy drive(s): fd0 is 1.44M
[    0.815047] FDC 0 is a post-1991 82077
[    1.227598] EXT4-fs (loop0): mounted filesystem with ordered data  mode
[   15.566004] udev: starting version 151
[   15.776081] type=1505 audit(1279638863.897:2):   operation="profile_load" pid=632 name="/sbin/dhclient3"
[   15.776587] type=1505 audit(1279638863.897:3):   operation="profile_load" pid=632  name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   15.776849] type=1505 audit(1279638863.897:4):   operation="profile_load" pid=632  name="/usr/lib/connman/scripts/dhclient-script"
[   15.909383] lp: driver loaded but no devices found
[   16.093084] Linux agpgart interface v0.103
[   16.110269] intel_rng: FWH not detected
[   16.112963] parport_pc 00:08: reported by Plug and Play ACPI
[   16.113448] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   16.115310] agpgart-intel 0000:00:00.0: Intel G33 Chipset
[   16.115813] agpgart-intel 0000:00:00.0: detected 7164K stolen memory
[   16.124633] agpgart-intel 0000:00:00.0: AGP aperture is 256M @  0xd0000000
[   16.208722] lp0: using parport0 (interrupt-driven).
[   16.302597] psmouse serio1: ID: 10 00 64
[   16.349436] input: GenPS/2 Genius Mouse as  /devices/platform/i8042/serio1/input/input4
[   16.420423] ppdev: user-space parallel port driver
[   16.490201] cfg80211: Calling CRDA to update world regulatory domain
[   16.608033] cfg80211: World regulatory domain updated:
[   16.608036]     (start_freq - end_freq @ bandwidth),  (max_antenna_gain, max_eirp)
[   16.608038]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi,  2000 mBm)
[   16.608040]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi,  2000 mBm)
[   16.608042]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi,  2000 mBm)
[   16.608044]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi,  2000 mBm)
[   16.608045]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi,  2000 mBm)
[   16.633588] [drm] Initialized drm 1.1.0 20060810
[   16.704858] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low)  -> IRQ 16
[   16.704863] i915 0000:00:02.0: setting latency timer to 64
[   16.708471]   alloc irq_desc for 27 on node -1
[   16.708474]   alloc kstat_irqs on node -1
[   16.708483] i915 0000:00:02.0: irq 27 for MSI/MSI-X
[   16.708489] [drm] set up 7M of stolen space
[   16.708817] [drm] initialized overlay support
[   16.713308] rtl8180 0000:03:01.0: PCI INT A -> GSI 16 (level, low)  -> IRQ 16
[   16.874401] fb0: inteldrmfb frame buffer device
[   16.874403] registered panic notifier
[   16.874895] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on  minor 0
[   16.874930] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level,  low) -> IRQ 16
[   16.874934] hda_intel: position_fix set to 1 for device 1565:820f
[   16.874952] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   16.887363] vga16fb: initializing
[   16.887366] vga16fb: mapped to 0xc00a0000
[   16.887368] vga16fb: not registering due to another framebuffer  present
[   16.897137] phy0: Selected rate control algorithm 'minstrel'
[   16.897679] phy0: hwaddr 00:23:cd:ca:c6:c4, RTL8185vD + rtl8225z2
[   16.932169] Console: switching to colour frame buffer device 160x64
[   16.967220] input: HDA Digital PCBeep as  /devices/pci0000:00/0000:00:1b.0/input/input5
[   17.509464] Adding 261112k swap on /host/ubuntu/disks/swap.disk.   Priority:-1 extents:1 across:261112k 
[   17.650723] type=1505 audit(1279638865.769:5):   operation="profile_load" pid=866  name="/usr/share/gdm/guest-session/Xsession"
[   17.652542] type=1505 audit(1279638865.773:6):   operation="profile_replace" pid=867 name="/sbin/dhclient3"
[   17.653040] type=1505 audit(1279638865.773:7):   operation="profile_replace" pid=867  name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   17.653306] type=1505 audit(1279638865.773::  operation="profile_replace"  pid=867 name="/usr/lib/connman/scripts/dhclient-script"
[   17.656158] type=1505 audit(1279638865.777:9):   operation="profile_load" pid=868 name="/usr/bin/evince"
[   17.663453] r8169: eth0: link down
[   17.663601] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   17.663618] type=1505 audit(1279638865.781:10):   operation="profile_load" pid=868 name="/usr/bin/evince-previewer"
[   17.667621] type=1505 audit(1279638865.785:11):   operation="profile_load" pid=868 name="/usr/bin/evince-thumbnailer"
[   19.195112] CPU0 attaching NULL sched-domain.
[   19.195117] CPU1 attaching NULL sched-domain.
[   19.216191] CPU0 attaching sched-domain:
[   19.216194]  domain 0: span 0-1 level MC
[   19.216196]   groups: 0 1
[   19.216203] CPU1 attaching sched-domain:
[   19.216204]  domain 0: span 0-1 level MC
[   19.216206]   groups: 1 0
[   21.692239] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   22.968720] hda-intel: IRQ timing workaround is activated for card  #0. Suggest a bigger bdl_pos_adj.
[   27.443460] ISO 9660 Extensions: Microsoft Joliet Level 3
[   27.596200] ISOFS: changing to secondary root
[   33.520071] wlan0: deauthenticating from 00:24:01:a5:58:81 by local  choice (reason=3)
[   33.584012] wlan0: direct probe to AP 00:24:01:a5:58:81 (try 1)
[   33.587438] wlan0: direct probe responded
[   33.587441] wlan0: authenticate with AP 00:24:01:a5:58:81 (try 1)
[   33.589114] wlan0: authenticated
[   33.589133] wlan0: associate with AP 00:24:01:a5:58:81 (try 1)
[   33.591462] wlan0: RX AssocResp from 00:24:01:a5:58:81 (capab=0x411  status=0 aid=2)
[   33.591465] wlan0: associated
[   33.591965] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   33.592012] cfg80211: Calling CRDA for country: TW
[   33.593886] cfg80211: Received country IE:
[   33.593888] cfg80211: Regulatory domain: TW
[   33.593889]     (start_freq - end_freq @ bandwidth),  (max_antenna_gain, max_eirp)
[   33.593891]     (2402000 KHz - 2494000 KHz @ 40000 KHz), (10000 mBi,  10000 mBm)
[   33.593893] cfg80211: CRDA thinks this should applied:
[   33.593894] cfg80211: Regulatory domain: TW
[   33.593895]     (start_freq - end_freq @ bandwidth),  (max_antenna_gain, max_eirp)
[   33.593897]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi,  2700 mBm)
[   33.593898]     (5270000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi,  1700 mBm)
[   33.593900]     (5735000 KHz - 5815000 KHz @ 40000 KHz), (300 mBi,  3000 mBm)
[   33.593902] cfg80211: We intersect both of these and get:
[   33.593903] cfg80211: Regulatory domain: 98
[   33.593904]     (start_freq - end_freq @ bandwidth),  (max_antenna_gain, max_eirp)
[   33.593906]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi,  2700 mBm)
[   33.593909] cfg80211: Disabling channel 2467 MHz on phy0 due to  Country IE
[   33.593911] cfg80211: Disabling channel 2472 MHz on phy0 due to  Country IE
[   33.593912] cfg80211: Disabling channel 2484 MHz on phy0 due to  Country IE
[   33.593915] cfg80211: Current regulatory domain updated by AP to: TW
[   33.593916]     (start_freq - end_freq @ bandwidth),  (max_antenna_gain, max_eirp)
[   33.593918]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi,  2700 mBm)
[   33.878904] padlock: VIA PadLock not detected.
[   43.771898] wlan0: no IPv6 routers present
jj@ubuntu:~$ 
                                
output of sudo lshw -c network 

     
                                                 -network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:30:67:3d:5a:3f
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom  ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169  driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes  port=MII speed=10MB/s
       resources: irq:26 ioport:d800(size=256)  memory:fdfff000-fdffffff(prefetchable)  memory:fdfe0000-fdfeffff(prefetchable)  memory:feae0000-feafffff(prefetchable)
  *-network
       description: Wireless interface
       product: RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:03:01.0
       logical name: wlan0
       version: 20
       serial: 00:23:cd:ca:c6:c4
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8180 ip=192.168.1.2  latency=64 maxlatency=64 mingnt=32 multicast=yes wireless=IEEE 802.11bg
       resources: irq:16 ioport:e800(size=256) memory:febffc00-febffdff                                 
output of iwlist scan 

lo        Interface doesn't support scanning.

 
                                                 eth0      Interface doesn't support scanning.                                 
 
                                                 wlan0     Scan completed :
          Cell 01 - Address: 00:24:01:A5:58:81
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=23/100  Signal level=23/100  
                    Encryption keyn
                    ESSID:"SKY49983"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000049e64eaf2
                    Extra: Last beacon: 20928ms ago
                    IE: Unknown: 0008534B593439393833
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown:  2D1A0E1017FFFF0000010000000000000000000000000C0000  000000
                    IE: Unknown:  3D1601050700000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown:  DD180050F2020101000003A4000027A4000042435E0062322F  00
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4304000000
                    IE: Unknown: 0706545720010D10
                    IE: Unknown:  DD1E00904C330E1017FFFF0000010000000000000000000000  000C0000000000
                    IE: Unknown:  DD1A00904C3401050700000000000000000000000000000000  000000

jj@ubuntu:~$ 


output of lsb_Release 
jj@ubuntu:~$ lsb_release -d
Description:    Ubuntu 10.04.1 LTS
jj@ubuntu:~$ 
                                
output of uname -mr 

     
                                                 j@ubuntu:~$ uname -mr
2.6.32-24-generic i686

output of  sudo /etc/init.d/networking restart
      
                                                 sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                           Ignoring unknown interface wlan0=wlan0.
                                                                          [ OK ]
jj@ubuntu:~$                      




[/QUOTE]







a note to all who read this i had to remove the smilies the forum auto-posts so just ignore errors where the smilie isnt there as ive had to delete the smiles that were :D

also the output of /var/log/messages is located here [http://pastebin.com/aAKLfEde](http://pastebin.com/aAKLfEde)

---

### Post by alarme on 2010-07-21
Hi,

can you post the output of:

route
cat /etc/resolv.conf

?

maybe is an issue related with DHCP renewal

---

### Post by JTJ_ on 2010-07-21
jj@ubuntu:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     2      0        0 wlan0
link-local      *               255.255.0.0     U     1000   0        0 wlan0
cat /etdefault         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
jj@ubuntu:~$ cat /etc/resolv.conf
# Generated by NetworkManager
nameserver 192.168.1.1

---

### Post by Iowan on 2010-07-21
Threads merged. Some of the duplicate information removed.

---

