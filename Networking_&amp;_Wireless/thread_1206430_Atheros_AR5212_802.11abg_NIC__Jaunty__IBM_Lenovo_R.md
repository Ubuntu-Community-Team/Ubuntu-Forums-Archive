---
title: "Atheros AR5212 802.11abg NIC / Jaunty / IBM Lenovo R61 / Kernel Panic"
date: 2009-07-07
forum: Networking &amp; Wireless
---

### Post by ishii255 on 2009-07-07
I've been trying to fix this one for a while, I can't find anyone with the exact problem as me:

My laptop has a kernel panic if I leave it on for more than 12 hours or so with the madwifi driver. Here's my output, apologies if the solution is right in front of me, I'm a noob to wireless troubleshooting.

IBM Lenovo R61 Laptop // 2.6.28-13-generic i686

Here's a bunch of output that I don't know what to do with... Please and Thank You in advance.

```
03:00.0 Ethernet controller: Atheros Communications Inc. AR5212 802.11abg NIC (rev 01)
        Subsystem: IBM Device 058a
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at df2f0000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>
        Kernel driver in use: ath_pci
        Kernel modules: ath_pci, ath5k
```

```
ath0      Link encap:Ethernet  HWaddr 00:1c:26:4c:6a:27  
          inet addr:192.168.1.109  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:26ff:fe4c:6a27/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3867 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3469 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2862272 (2.8 MB)  TX bytes:590894 (590.8 KB)

eth0      Link encap:Ethernet  HWaddr 00:1a:6b:3a:13:a1  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Memory:fe200000-fe220000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1440 (1.4 KB)  TX bytes:1440 (1.4 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-1C-26-4C-6A-27-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:31562 errors:0 dropped:0 overruns:0 frame:11489
          TX packets:4025 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:5896136 (5.8 MB)  TX bytes:773830 (773.8 KB)
          Interrupt:17

```


```
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"POKeMON"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1D:7E:EE:16:81   
          Bit Rate:24 Mb/s   Tx-Power:8 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=34/70  Signal level=-64 dBm  Noise level=-98 dBm
          Rx invalid nwid:12871  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

```


```
Module                  Size  Used by
wlan_tkip              19328  2 
binfmt_misc            16776  1 
ppdev                  15620  0 
bridge                 56340  0 
stp                    10500  1 bridge
bnep                   20224  2 
input_polldev          11912  0 
lp                     17156  0 
parport                42220  2 ppdev,lp
joydev                 18368  0 
snd_hda_intel         434100  3 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82948  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
thinkpad_acpi          66560  0 
pcmcia                 44748  0 
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
wlan_scan_sta          20480  1 
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ath_rate_sample        19840  1 
led_class              12036  1 thinkpad_acpi
intel_agp              34108  0 
snd                    62628  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
nvidia               7233756  39 
psmouse                61972  0 
video                  25360  5 
nvram                  16396  1 thinkpad_acpi
pcspkr                 10496  0 
yenta_socket           32396  1 
rsrc_nonstatic         19328  1 yenta_socket
pcmcia_core            43540  3 pcmcia,yenta_socket,rsrc_nonstatic
iTCO_wdt               19108  0 
iTCO_vendor_support    11652  1 iTCO_wdt
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
ath_pci                99224  0 
wlan                  210288  5 wlan_tkip,wlan_scan_sta,ath_rate_sample,ath_pci
ath_hal               198864  3 ath_rate_sample,ath_pci
agpgart                42696  2 intel_agp,nvidia
serio_raw              13316  0 
output                 11008  1 video
ohci1394               38576  0 
ieee1394               94660  1 ohci1394
e1000e                121136  0 
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit

```

```
[    0.545533] pci 0000:00:1c.2:   IO window: 0x5000-0x5fff
[    0.545542] pci 0000:00:1c.2:   MEM window: 0xd8000000-0xd9ffffff
[    0.545551] pci 0000:00:1c.2:   PREFETCH window: 0x000000dfa00000-0x000000dfafffff
[    0.545566] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:05
[    0.545572] pci 0000:00:1c.3:   IO window: 0x6000-0x6fff
[    0.545581] pci 0000:00:1c.3:   MEM window: 0xd0000000-0xd1ffffff
[    0.545590] pci 0000:00:1c.3:   PREFETCH window: 0x000000df700000-0x000000df7fffff
[    0.545605] pci 0000:00:1c.4: PCI bridge, secondary bus 0000:0d
[    0.545609] pci 0000:00:1c.4:   IO window: 0x7000-0x7fff
[    0.545622] pci 0000:00:1c.4:   MEM window: 0xcc000000-0xcdffffff
[    0.545631] pci 0000:00:1c.4:   PREFETCH window: 0x000000df400000-0x000000df4fffff
[    0.545644] pci 0000:15:00.0: CardBus bridge, secondary bus 0000:16
[    0.545647] pci 0000:15:00.0:   IO window: 0x008000-0x0080ff
[    0.545656] pci 0000:15:00.0:   IO window: 0x008400-0x0084ff
[    0.545666] pci 0000:15:00.0:   PREFETCH window: 0xf4000000-0xf7ffffff
[    0.545674] pci 0000:15:00.0:   MEM window: 0x80000000-0x83ffffff
[    0.545683] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:15
[    0.545688] pci 0000:00:1e.0:   IO window: 0x8000-0xbfff
[    0.545701] pci 0000:00:1e.0:   MEM window: 0xf8100000-0xfbffffff
[    0.545707] pci 0000:00:1e.0:   PREFETCH window: 0x000000f4000000-0x000000f7ffffff
[    0.545731] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.545735] pci 0000:00:01.0: setting latency timer to 64
[    0.545747] pci 0000:00:1c.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.545754] pci 0000:00:1c.0: setting latency timer to 64
[    0.545771] pci 0000:00:1c.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.545778] pci 0000:00:1c.1: setting latency timer to 64
[    0.545797] pci 0000:00:1c.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    0.545802] pci 0000:00:1c.2: setting latency timer to 64
[    0.545814] pci 0000:00:1c.3: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    0.545821] pci 0000:00:1c.3: setting latency timer to 64
[    0.545837] pci 0000:00:1c.4: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.545844] pci 0000:00:1c.4: setting latency timer to 64
[    0.545854] pci 0000:00:1e.0: enabling device (0005 -> 0007)
[    0.545867] pci 0000:00:1e.0: setting latency timer to 64
[    0.545882] pci 0000:15:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.545892] pci 0000:15:00.0: setting latency timer to 64
[    0.545898] bus: 00 index 0 io port: [0x00-0xffff]
[    0.545901] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[    0.545903] bus: 01 index 0 io port: [0x2000-0x2fff]
[    0.545905] bus: 01 index 1 mmio: [0xd4000000-0xd6ffffff]
[    0.545907] bus: 01 index 2 mmio: [0xe0000000-0xefffffff]
[    0.545909] bus: 01 index 3 mmio: [0x0-0x0]
[    0.545911] bus: 02 index 0 io port: [0x3000-0x3fff]
[    0.545913] bus: 02 index 1 mmio: [0xfc000000-0xfdffffff]
[    0.545916] bus: 02 index 2 mmio: [0xf8000000-0xf80fffff]
[    0.545918] bus: 02 index 3 mmio: [0x0-0x0]
[    0.545920] bus: 03 index 0 io port: [0x4000-0x4fff]
[    0.545922] bus: 03 index 1 mmio: [0xdc100000-0xdf2fffff]
[    0.545924] bus: 03 index 2 mmio: [0xdfd00000-0xdfdfffff]
[    0.545926] bus: 03 index 3 mmio: [0x0-0x0]
[    0.545928] bus: 04 index 0 io port: [0x5000-0x5fff]
[    0.545930] bus: 04 index 1 mmio: [0xd8000000-0xd9ffffff]
[    0.545932] bus: 04 index 2 mmio: [0xdfa00000-0xdfafffff]
[    0.545934] bus: 04 index 3 mmio: [0x0-0x0]
[    0.545936] bus: 05 index 0 io port: [0x6000-0x6fff]
[    0.545938] bus: 05 index 1 mmio: [0xd0000000-0xd1ffffff]
[    0.545940] bus: 05 index 2 mmio: [0xdf700000-0xdf7fffff]
[    0.545942] bus: 05 index 3 mmio: [0x0-0x0]
[    0.545944] bus: 0d index 0 io port: [0x7000-0x7fff]
[    0.545946] bus: 0d index 1 mmio: [0xcc000000-0xcdffffff]
[    0.545948] bus: 0d index 2 mmio: [0xdf400000-0xdf4fffff]
[    0.545950] bus: 0d index 3 mmio: [0x0-0x0]
[    0.545952] bus: 15 index 0 io port: [0x8000-0xbfff]
[    0.545954] bus: 15 index 1 mmio: [0xf8100000-0xfbffffff]
[    0.545957] bus: 15 index 2 mmio: [0xf4000000-0xf7ffffff]
[    0.545959] bus: 15 index 3 io port: [0x00-0xffff]
[    0.545961] bus: 15 index 4 mmio: [0x000000-0xffffffff]
[    0.545963] bus: 16 index 0 io port: [0x8000-0x80ff]
[    0.545965] bus: 16 index 1 io port: [0x8400-0x84ff]
[    0.545967] bus: 16 index 2 mmio: [0xf4000000-0xf7ffffff]
[    0.545969] bus: 16 index 3 mmio: [0x80000000-0x83ffffff]
[    0.545976] NET: Registered protocol family 2
[    0.560060] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.560290] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.560593] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.560743] TCP: Hash tables configured (established 131072 bind 65536)
[    0.560745] TCP reno registered
[    0.564073] NET: Registered protocol family 1
[    0.564178] checking if image is initramfs... it is
[    1.167918] Freeing initrd memory: 7385k freed
[    1.167963] Simple Boot Flag at 0x35 set to 0x1
[    1.168146] cpufreq: No nForce2 chipset.
[    1.168284] audit: initializing netlink socket (disabled)
[    1.168301] type=2000 audit(1246952829.165:1): initialized
[    1.175523] highmem bounce pool size: 64 pages
[    1.175530] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.176836] VFS: Disk quotas dquot_6.5.1
[    1.176892] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.177502] fuse init (API version 7.10)
[    1.177587] msgmni has been set to 1698
[    1.177788] alg: No test for stdrng (krng)
[    1.177801] io scheduler noop registered
[    1.177803] io scheduler anticipatory registered
[    1.177805] io scheduler deadline registered
[    1.177818] io scheduler cfq registered (default)
[    1.178042] pci 0000:01:00.0: Boot video device
[    1.189059] pcieport-driver 0000:00:01.0: setting latency timer to 64
[    1.189097] pcieport-driver 0000:00:01.0: found MSI capability
[    1.189122] pcieport-driver 0000:00:01.0: irq 2303 for MSI/MSI-X
[    1.189132] pci_express 0000:00:01.0:pcie00: allocate port service
[    1.189145] pci_express 0000:00:01.0:pcie02: allocate port service
[    1.189157] pci_express 0000:00:01.0:pcie03: allocate port service
[    1.189220] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    1.189313] pcieport-driver 0000:00:1c.0: found MSI capability
[    1.189375] pcieport-driver 0000:00:1c.0: irq 2302 for MSI/MSI-X
[    1.189403] pci_express 0000:00:1c.0:pcie00: allocate port service
[    1.189415] pci_express 0000:00:1c.0:pcie02: allocate port service
[    1.189426] pci_express 0000:00:1c.0:pcie03: allocate port service
[    1.189564] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[    1.189661] pcieport-driver 0000:00:1c.1: found MSI capability
[    1.189725] pcieport-driver 0000:00:1c.1: irq 2301 for MSI/MSI-X
[    1.189756] pci_express 0000:00:1c.1:pcie00: allocate port service
[    1.189768] pci_express 0000:00:1c.1:pcie02: allocate port service
[    1.189779] pci_express 0000:00:1c.1:pcie03: allocate port service
[    1.189909] pcieport-driver 0000:00:1c.2: setting latency timer to 64
[    1.190002] pcieport-driver 0000:00:1c.2: found MSI capability
[    1.190069] pcieport-driver 0000:00:1c.2: irq 2300 for MSI/MSI-X
[    1.190094] pci_express 0000:00:1c.2:pcie00: allocate port service
[    1.190106] pci_express 0000:00:1c.2:pcie02: allocate port service
[    1.190118] pci_express 0000:00:1c.2:pcie03: allocate port service
[    1.190253] pcieport-driver 0000:00:1c.3: setting latency timer to 64
[    1.190350] pcieport-driver 0000:00:1c.3: found MSI capability
[    1.190412] pcieport-driver 0000:00:1c.3: irq 2299 for MSI/MSI-X
[    1.190442] pci_express 0000:00:1c.3:pcie00: allocate port service
[    1.190454] pci_express 0000:00:1c.3:pcie02: allocate port service
[    1.190467] pci_express 0000:00:1c.3:pcie03: allocate port service
[    1.190602] pcieport-driver 0000:00:1c.4: setting latency timer to 64
[    1.190693] pcieport-driver 0000:00:1c.4: found MSI capability
[    1.190759] pcieport-driver 0000:00:1c.4: irq 2298 for MSI/MSI-X
[    1.190785] pci_express 0000:00:1c.4:pcie00: allocate port service
[    1.190800] pci_express 0000:00:1c.4:pcie02: allocate port service
[    1.190812] pci_express 0000:00:1c.4:pcie03: allocate port service
[    1.190945] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.191705] pciehp 0000:00:01.0:pcie02: HPC vendor_id 8086 device_id 2a01 ss_vid 0 ss_did 0
[    1.191743] pciehp 0000:00:01.0:pcie02: service driver pciehp loaded
[    1.192470] pciehp 0000:00:1c.0:pcie02: HPC vendor_id 8086 device_id 283f ss_vid 0 ss_did 0
[    1.192525] pciehp 0000:00:1c.0:pcie02: service driver pciehp loaded
[    1.193263] pciehp 0000:00:1c.1:pcie02: HPC vendor_id 8086 device_id 2841 ss_vid 0 ss_did 0
[    1.193315] pciehp 0000:00:1c.1:pcie02: service driver pciehp loaded
[    1.194039] pciehp 0000:00:1c.2:pcie02: HPC vendor_id 8086 device_id 2843 ss_vid 0 ss_did 0
[    1.194098] pciehp 0000:00:1c.2:pcie02: service driver pciehp loaded
[    1.194825] pciehp 0000:00:1c.3:pcie02: HPC vendor_id 8086 device_id 2845 ss_vid 0 ss_did 0
[    1.194886] pciehp 0000:00:1c.3:pcie02: service driver pciehp loaded
[    1.195615] pciehp 0000:00:1c.4:pcie02: HPC vendor_id 8086 device_id 2847 ss_vid 0 ss_did 0
[    1.195674] pciehp 0000:00:1c.4:pcie02: service driver pciehp loaded
[    1.195683] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.196436] ACPI: AC Adapter [AC] (on-line)
[    1.197008] ACPI: Battery Slot [BAT0] (battery absent)
[    1.197085] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.197088] ACPI: Power Button (FF) [PWRF]
[    1.197131] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
[    1.197501] ACPI: Lid Switch [LID]
[    1.197542] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    1.197550] ACPI: Sleep Button (CM) [SLPB]
[    1.198122] ACPI: SSDT 7DEE1D72, 02C4 (r1  PmRef  Cpu0Ist      100 INTL 20050513)
[    1.198739] ACPI: SSDT 7DEE20BB, 061E (r1  PmRef  Cpu0Cst      100 INTL 20050513)
[    1.202178] Monitor-Mwait will be used to enter C-1 state
[    1.202181] Monitor-Mwait will be used to enter C-2 state
[    1.202184] Monitor-Mwait will be used to enter C-3 state
[    1.202198] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    1.202221] processor ACPI_CPU:00: registered as cooling_device0
[    1.202224] ACPI: Processor [CPU0] (supports 8 throttling states)
[    1.202557] ACPI: SSDT 7DEE1CAA, 00C8 (r1  PmRef  Cpu1Ist      100 INTL 20050513)
[    1.203132] ACPI: SSDT 7DEE2036, 0085 (r1  PmRef  Cpu1Cst      100 INTL 20050513)
[    1.205265] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    1.205283] processor ACPI_CPU:01: registered as cooling_device1
[    1.205287] ACPI: Processor [CPU1] (supports 8 throttling states)
[    1.212561] thermal LNXTHERM:01: registered as thermal_zone0
[    1.215690] ACPI: Thermal Zone [THM0] (57 C)
[    1.216770] thermal LNXTHERM:02: registered as thermal_zone1
[    1.218101] ACPI: Thermal Zone [THM1] (56 C)
[    1.218154] isapnp: Scanning for PnP cards...
[    1.575817] isapnp: No Plug & Play device found
[    1.584149] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.585138] brd: module loaded
[    1.585425] loop: module loaded
[    1.585486] Fixed MDIO Bus: probed
[    1.585491] PPP generic driver version 2.4.2
[    1.585544] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    1.585571] Driver 'sd' needs updating - please use bus_type methods
[    1.585580] Driver 'sr' needs updating - please use bus_type methods
[    1.585651] ata_piix 0000:00:1f.2: version 2.12
[    1.585669] ata_piix 0000:00:1f.2: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    1.585675] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[    1.740042] ata_piix 0000:00:1f.2: setting latency timer to 64
[    1.740140] scsi0 : ata_piix
[    1.740228] scsi1 : ata_piix
[    1.741390] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x1c30 irq 14
[    1.741393] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1c38 irq 15
[    1.912514] ata1.00: ATA-7: HITACHI HTS541680J9SA00, SB2IC7UP, max UDMA/100
[    1.912517] ata1.00: 156301488 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.928523] ata1.00: configured for UDMA/100
[    2.092457] ata2.00: ATAPI: HL-DT-STCD-RW/DVD DRIVE GCC-T10N, 1.04, max UDMA/33
[    2.108331] ata2.00: configured for UDMA/33
[    2.109235] scsi 0:0:0:0: Direct-Access     ATA      HITACHI HTS54168 SB2I PQ: 0 ANSI: 5
[    2.109323] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[    2.109339] sd 0:0:0:0: [sda] Write Protect is off
[    2.109341] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.109365] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.109424] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[    2.109438] sd 0:0:0:0: [sda] Write Protect is off
[    2.109440] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.109463] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.109467]  sda: sda1 sda2 < sda5 >
[    2.172470] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.172507] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.177049] scsi 1:0:0:0: CD-ROM            HL-DT-ST RW/DVD GCC-T10N  1.04 PQ: 0 ANSI: 5
[    2.188429] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    2.188432] Uniform CD-ROM driver Revision: 3.20
[    2.188511] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.188543] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.189178] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.189656] ehci_hcd 0000:00:1a.7: power state changed by ACPI to D0
[    2.189668] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    2.189692] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    2.189699] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    2.189749] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    2.193670] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    2.193687] ehci_hcd 0000:00:1a.7: irq 22, io mem 0xfe226400
[    2.208027] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    2.208089] usb usb1: configuration #1 chosen from 1 choice
[    2.208115] hub 1-0:1.0: USB hub found
[    2.208122] hub 1-0:1.0: 4 ports detected
[    2.208610] ehci_hcd 0000:00:1d.7: power state changed by ACPI to D0
[    2.208624] ehci_hcd 0000:00:1d.7: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    2.208637] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    2.208643] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    2.208684] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    2.212615] ehci_hcd 0000:00:1d.7: debug port 1
[    2.212628] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    2.212645] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xfe226800
[    2.228027] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    2.228076] usb usb2: configuration #1 chosen from 1 choice
[    2.228100] hub 2-0:1.0: USB hub found
[    2.228106] hub 2-0:1.0: 6 ports detected
[    2.228211] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.228227] uhci_hcd: USB Universal Host Controller Interface driver
[    2.228247] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    2.228258] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    2.228264] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    2.228301] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    2.228343] uhci_hcd 0000:00:1a.0: irq 20, io base 0x00001860
[    2.228417] usb usb3: configuration #1 chosen from 1 choice
[    2.228441] hub 3-0:1.0: USB hub found
[    2.228447] hub 3-0:1.0: 2 ports detected
[    2.229062] uhci_hcd 0000:00:1a.1: power state changed by ACPI to D0
[    2.229070] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    2.229080] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    2.229086] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    2.229129] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    2.229170] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00001880
[    2.229241] usb usb4: configuration #1 chosen from 1 choice
[    2.229264] hub 4-0:1.0: USB hub found
[    2.229270] hub 4-0:1.0: 2 ports detected
[    2.229819] uhci_hcd 0000:00:1d.0: power state changed by ACPI to D0
[    2.229827] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.229838] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    2.229843] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    2.229883] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    2.229923] uhci_hcd 0000:00:1d.0: irq 16, io base 0x000018a0
[    2.229993] usb usb5: configuration #1 chosen from 1 choice
[    2.230019] hub 5-0:1.0: USB hub found
[    2.230025] hub 5-0:1.0: 2 ports detected
[    2.230110] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    2.230117] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    2.230123] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    2.230165] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    2.230202] uhci_hcd 0000:00:1d.1: irq 17, io base 0x000018c0
[    2.230273] usb usb6: configuration #1 chosen from 1 choice
[    2.230296] hub 6-0:1.0: USB hub found
[    2.230302] hub 6-0:1.0: 2 ports detected
[    2.230907] uhci_hcd 0000:00:1d.2: power state changed by ACPI to D0
[    2.230916] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.230927] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    2.230933] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    2.230974] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    2.231017] uhci_hcd 0000:00:1d.2: irq 18, io base 0x000018e0
[    2.231086] usb usb7: configuration #1 chosen from 1 choice
[    2.231110] hub 7-0:1.0: USB hub found
[    2.231115] hub 7-0:1.0: 2 ports detected
[    2.231251] PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
[    2.239153] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.239158] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.241045] mice: PS/2 mouse device common for all mice
[    2.257081] rtc_cmos 00:07: RTC can wake from S4
[    2.257111] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
[    2.257148] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    2.257202] device-mapper: uevent: version 1.0.3
[    2.257299] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
[    2.257458] device-mapper: multipath: version 1.0.5 loaded
[    2.257460] device-mapper: multipath round-robin: version 1.0.0 loaded
[    2.257562] EISA: Probing bus 0 at eisa.0
[    2.257570] Cannot allocate resource for EISA slot 1
[    2.257572] Cannot allocate resource for EISA slot 2
[    2.257574] Cannot allocate resource for EISA slot 3
[    2.257577] Cannot allocate resource for EISA slot 4
[    2.257579] Cannot allocate resource for EISA slot 5
[    2.257581] Cannot allocate resource for EISA slot 6
[    2.257583] Cannot allocate resource for EISA slot 7
[    2.257585] Cannot allocate resource for EISA slot 8
[    2.257586] EISA: Detected 0 cards.
[    2.257766] cpuidle: using governor ladder
[    2.257882] cpuidle: using governor menu
[    2.258378] TCP cubic registered
[    2.258468] NET: Registered protocol family 10
[    2.258872] lo: Disabled Privacy Extensions
[    2.259197] NET: Registered protocol family 17
[    2.259212] Bluetooth: L2CAP ver 2.11
[    2.259213] Bluetooth: L2CAP socket layer initialized
[    2.259216] Bluetooth: SCO (Voice Link) ver 0.6
[    2.259218] Bluetooth: SCO socket layer initialized
[    2.259302] Bluetooth: RFCOMM socket layer initialized
[    2.259309] Bluetooth: RFCOMM TTY layer initialized
[    2.259311] Bluetooth: RFCOMM ver 1.10
[    2.260258] Using IPI No-Shortcut mode
[    2.260324] registered taskstats version 1
[    2.260421]   Magic number: 1:507:773
[    2.260426] hub 2-0:1.0: hash matches
[    2.260524] rtc_cmos 00:07: setting system clock to 2009-07-07 07:47:11 UTC (1246952831)
[    2.260527] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.260529] EDD information not available.
[    2.260819] Freeing unused kernel memory: 532k freed
[    2.260991] Write protecting the kernel text: 4112k
[    2.261065] Write protecting the kernel read-only data: 1524k
[    2.261310] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    2.458744] e1000e: Intel(R) PRO/1000 Network Driver - 0.3.3.3-k6
[    2.458746] e1000e: Copyright (c) 1999-2008 Intel Corporation.
[    2.458806] e1000e 0000:00:19.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    2.458820] e1000e 0000:00:19.0: setting latency timer to 64
[    2.459000] e1000e 0000:00:19.0: irq 2297 for MSI/MSI-X
[    2.600663] ohci1394 0000:15:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    2.600675] ohci1394 0000:15:00.1: setting latency timer to 64
[    2.653425] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[17]  MMIO=[f8101000-f81017ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    2.779870] 0000:00:19.0: eth0: (PCI Express:2.5GB/s:Width x1) 00:1a:6b:3a:13:a1
[    2.779873] 0000:00:19.0: eth0: Intel(R) PRO/1000 Network Connection
[    2.779907] 0000:00:19.0: eth0: MAC: 5, PHY: 6, PBA No: ffffff-0ff
[    2.992213] PM: Starting manual resume from disk
[    2.992216] PM: Resume from partition 8:5
[    2.992217] PM: Checking hibernation image.
[    2.992476] PM: Resume from disk failed.
[    3.043223] kjournald starting.  Commit interval 5 seconds
[    3.043232] EXT3-fs: mounted filesystem with ordered data mode.
[    3.972181] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00061b032a11da8e]
[    9.627646] udev: starting version 141
[   10.318907] Linux agpgart interface v0.103
[   10.319313] ath_hal: module license 'Proprietary' taints kernel.
[   10.320318] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   10.328970] wlan: 0.9.4
[   10.334069] ath_pci: 0.9.4
[   10.334112] ath_pci 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   10.334128] ath_pci 0000:03:00.0: setting latency timer to 64
[   10.371894] iTCO_vendor_support: vendor-support=0
[   10.373304] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05
[   10.373432] iTCO_wdt: Found a ICH8M-E TCO device (Version=2, TCOBASE=0x1060)
[   10.373516] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   10.399221] yenta_cardbus 0000:15:00.0: CardBus bridge found [17aa:20c6]
[   10.407288] input: PC Speaker as /devices/platform/pcspkr/input/input5
[   10.423198] Non-volatile memory driver v1.2
[   10.526154] yenta_cardbus 0000:15:00.0: ISA IRQ mask 0x0cb8, PCI irq 16
[   10.526161] yenta_cardbus 0000:15:00.0: Socket status: 30000006
[   10.526192] yenta_cardbus 0000:15:00.0: pcmcia: parent PCI bridge I/O window: 0x8000 - 0xbfff
[   10.526195] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x8000-0xbfff: clean.
[   10.527171] yenta_cardbus 0000:15:00.0: pcmcia: parent PCI bridge Memory window: 0xf8100000 - 0xfbffffff
[   10.527174] yenta_cardbus 0000:15:00.0: pcmcia: parent PCI bridge Memory window: 0xf4000000 - 0xf7ffffff
[   10.910238] acpi device:08: registered as cooling_device2
[   10.910558] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:06/device:07/input/input6
[   10.916156] ACPI: Video Device [VID1] (multi-head: yes  rom: no  post: no)
[   11.008671] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[   11.442701] nvidia 0000:01:00.0: power state changed by ACPI to D0
[   11.442713] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   11.442721] nvidia 0000:01:00.0: setting latency timer to 64
[   11.445236] NVRM: loading NVIDIA UNIX x86 Kernel Module  180.44  Mon Mar 23 14:59:10 PST 2009
[   11.461419] ath_rate_sample: 1.2 (0.9.4)
[   11.463099] wifi0: 11a rates: 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   11.463108] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[   11.463113] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   11.463124] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
[   11.463129] wifi0: mac 10.3 phy 6.1 radio 10.2
[   11.463133] wifi0: Use hw queue 1 for WME_AC_BE traffic
[   11.463135] wifi0: Use hw queue 0 for WME_AC_BK traffic
[   11.463137] wifi0: Use hw queue 2 for WME_AC_VI traffic
[   11.463139] wifi0: Use hw queue 3 for WME_AC_VO traffic
[   11.463141] wifi0: Use hw queue 8 for CAB traffic
[   11.463143] wifi0: Use hw queue 9 for beacons
[   11.470888] wifi0: Atheros 5212: mem=0xdf2f0000, irq=17
[   11.526203] thinkpad_acpi: ThinkPad ACPI Extras v0.21
[   11.526206] thinkpad_acpi: http://ibm-acpi.sf.net/
[   11.526208] thinkpad_acpi: ThinkPad BIOS 7LET44WW (1.14 ), EC 7KHT22WW-1.06
[   11.526210] thinkpad_acpi: Lenovo ThinkPad R61/R61i, model 7742CTO
[   11.527775] thinkpad_acpi: ACPI backlight control delay disabled
[   11.528350] thinkpad_acpi: radio switch found; radios are enabled
[   11.528464] thinkpad_acpi: This ThinkPad has standard ACPI backlight brightness control, supported by the ACPI video driver
[   11.528467] thinkpad_acpi: Disabling thinkpad-acpi brightness events by default...
[   11.535059] Registered led device: tpacpi::thinklight
[   11.535303] Registered led device: tpacpi::power
[   11.535320] Registered led device: tpacpi:orange:batt
[   11.535334] Registered led device: tpacpi:green:batt
[   11.535348] Registered led device: tpacpi::dock_active
[   11.535364] Registered led device: tpacpi::bay_active
[   11.535379] Registered led device: tpacpi::dock_batt
[   11.535394] Registered led device: tpacpi::unknown_led
[   11.535409] Registered led device: tpacpi::standby
[   11.537912] thinkpad_acpi: Standard ACPI backlight interface available, not loading native one.
[   11.538173] input: ThinkPad Extra Buttons as /devices/virtual/input/input7
[   11.617141] HDA Intel 0000:00:1b.0: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   11.617145] hda_intel: probe_mask set to 0x1 for device 17aa:20ac
[   11.617200] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   11.877802] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
[   11.879588] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   11.880428] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   11.881123] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   11.881900] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   11.885955] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x81a0b1, caps: 0xa04793/0x300000
[   11.885958] serio: Synaptics pass-through port at isa0060/serio1/input0
[   11.928823] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input8
[   12.000076] Clocksource tsc unstable (delta = -206551030 ns)
[   12.164332] lp: driver loaded but no devices found
[   12.262198] Adding 3229024k swap on /dev/sda5.  Priority:-1 extents:1 across:3229024k
[   12.795933] EXT3 FS on sda1, internal journal
[   13.129563] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[   13.903265] type=1505 audit(1246952843.139:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2086
[   13.943899] type=1505 audit(1246952843.179:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2090
[   13.943971] type=1505 audit(1246952843.179:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2090
[   13.944012] type=1505 audit(1246952843.179:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2090
[   13.944047] type=1505 audit(1246952843.183:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2090
[   14.056630] type=1505 audit(1246952843.295:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2095
[   14.056752] type=1505 audit(1246952843.295:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2095
[   14.080858] type=1505 audit(1246952843.319:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2099
[   14.610021] psmouse serio2: ID: 10 00 64<6>Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   17.927048] Bluetooth: BNEP filters: protocol multicast
[   17.939873] Bridge firewalling registered
[   18.297819] IBM TrackPoint firmware: 0x0e, buttons: 3/3
[   18.529638] input: TPPS/2 IBM TrackPoint as /devices/platform/i8042/serio1/serio2/input/input9
[   19.709486] ppdev: user-space parallel port driver
[   23.912428] e1000e 0000:00:19.0: irq 2297 for MSI/MSI-X
[   23.968245] e1000e 0000:00:19.0: irq 2297 for MSI/MSI-X
[   23.968871] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   34.864082] ath0: no IPv6 routers present
[  413.864045] CE: hpet increasing min_delta_ns to 15000 nsec
```



```
*-network               
       description: Ethernet interface
       product: 82566MM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:1a:6b:3a:13:a1
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=0.3.3.3-k6 firmware=0.3-0 latency=0 link=no module=e1000e multicast=yes port=twisted pair
  *-network
       description: Wireless interface
       product: AR5212 802.11abg NIC
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wifi0
       version: 01
       serial: 00:1c:26:4c:6a:27
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci ip=192.168.1.109 latency=0 module=ath_pci multicast=yes wireless=IEEE 802.11g
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 8a:64:c7:a8:08:6e
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

---

### Post by t0mppa on 2009-07-07
Is it just when you work with it over 12h or when it goes to suspension/hibernation? The latter is something I remember having read about quite a few times on this forum and in launchpad bug reports, but don't have links saved on this computer.

If it's just the former, have you tried using ath5k_pci as the driver instead? It's supposed to have bypassed the older ath_pci in reliability this spring according to the MadWifi crew.

---

### Post by superprash2003 on 2009-07-07
post output of** sudo iwlist scanning**

---

### Post by ishii255 on 2009-07-07
No. my computer does not suspend or hibernate when it is left on for long periods of time. And the ath5k driver (that ubuntu automatically installs when I disable madwifi using "Hardware Drivers") works sometimes, but makes my internet *very* slow when it is enabled. Perhaps I should try to fix that driver, instead of this kernel panic problem that I have...

Also,

```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wifi0     Interface doesn't support scanning.

ath0      Scan completed :
          Cell 01 - Address: 00:1D:7E:EE:16:81
                    ESSID:"POKeMON"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=59/70  Signal level=-36 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: 00:14:A5:8B:A5:BC
                    ESSID:"Cableone.net_C5EC"
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality=4/70  Signal level=-91 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
          Cell 03 - Address: 00:14:A5:98:DB:B9
                    ESSID:"Rudy08"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=18/70  Signal level=-77 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
          Cell 04 - Address: 00:14:A5:C5:9A:20
                    ESSID:"sandwich"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=1/70  Signal level=-94 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
          Cell 05 - Address: 00:1A:73:9E:DC:C9
                    ESSID:"Cableonet.net_D476"
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality=6/70  Signal level=-89 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100

pan0      Interface doesn't support scanning.

```

---

### Post by ishii255 on 2009-07-08
Anyone?

---

### Post by t0mppa on 2009-07-08
In that case, I'm out of ideas as I've never run into this sort of trouble myself.

---

### Post by ishii255 on 2009-07-08
I know man, I can't find anyone else on the net with the same problem as me. I will just try messing around with ath5k and see if I can get it working as well as the madwifi driver...

---

### Post by Zetheroo on 2009-08-13
Hi ... I also have the R61 and the same wireless chipset and since Intrepid have been experiencing Kernel Panics.

I am going to compile the madwifi drivers myself on my fresh install of Jaunty to see if its any better as the default ath5k drivers are useless ... even when that card is working its really slow and drops in an out.

---

### Post by Zetheroo on 2009-08-14
Ok, so initially I had the ath5k driver going and it was very slow to connect and I could not Skype call because of the drop-outs. I would also get a Kernel Panic every other day or more.

Then I installed jaunty backports and had the madwifi drivers running which caused the system to freeze within a minute of logging in ...

and now I have removed jaunty backports and the system stays on ... but is back to square one ... 

I think I might just buy an Intel wifi card and put that in here... its just too much hassle otherwise ... but this is really a big letdown for me as I have been using Ubuntu as my primary OS for 3 years ... :(

---

