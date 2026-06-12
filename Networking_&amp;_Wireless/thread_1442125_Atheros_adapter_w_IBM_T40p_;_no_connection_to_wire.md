---
title: "Atheros adapter w IBM T40p ; no connection to wireless access point"
date: 2010-03-29
forum: Networking &amp; Wireless
---

### Post by zorrocket on 2010-03-29
Hello,

I am new to Ubuntu, and would like to use it on my old laptop (thinkpad T40p 2373-G1G). Overall, it runs smoothly. My main problem for now is to establish a wireless connection with a router. The network manager displays a list of SSIDs, including mine, which I left unprotected for now, to leave out any issues due to encryption, etc... After I select my SSID, the network manager's panel icon spins for a minute, then nothing. To me, it seems that the association with the access point fails, but I don't know why.
My router works fine, as several other network devices are using it without a problem. Any suggestions welcome. :)

I have the following information about my system.

lshw -C network returns :

  *-network:1
       description: Wireless interface
       product: AR5211 802.11ab NIC
       vendor: Atheros Communications Inc.
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: wmaster0
       version: 01
       serial: 00:05:4e:xx:xx:xx
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k latency=168 maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11ab
       resources: irq:11 memory:c0210000-c021ffff

iwconfig wlan0 returns:

wlan0     IEEE 802.11ab  ESSID:"guest"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

lsmod returns:

Module                  Size  Used by
binfmt_misc             8356  1 
joydev                 10240  0 
pcmcia                 36808  0 
ath_pci               197044  0 
arc4                    1660  2 
wlan                  228464  1 ath_pci
ecb                     2524  2 
snd_intel8x0           30168  2 
snd_ac97_codec        101216  1 snd_intel8x0
ac97_bus                1532  1 snd_ac97_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
iptable_filter          3100  0 
ath_hal               397504  1 ath_pci
ppdev                   6688  0 
yenta_socket           24296  2 
rsrc_nonstatic         11644  1 yenta_socket
pcmcia_core            36528  3 pcmcia,yenta_socket,rsrc_nonstatic
snd_seq_dummy           2656  0 
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
thinkpad_acpi          66916  0 
nvram                   7528  1 thinkpad_acpi
ath5k                 124772  0 
mac80211              181140  1 ath5k
led_class               4096  2 thinkpad_acpi,ath5k
ath                     8060  1 ath5k
cfg80211               93052  3 ath5k,mac80211,ath
parport_pc             31940  1 
nsc_ircc               20976  0 
irda                  189564  1 nsc_ircc
crc_ccitt               1852  1 irda
psmouse                56500  0 
serio_raw               5280  0 
shpchp                 32272  0 
snd_seq_oss            28576  0 
snd_seq_midi            6464  0 
snd_rawmidi            22176  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    59204  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_intel8x0,snd_pcm
lp                      8964  0 
parport                35340  3 ppdev,parport_pc,lp
usbhid                 38208  0 
video                  19380  0 
output                  2780  1 video
floppy                 54916  0 
radeon                636000  2 
ttm                    36212  1 radeon
drm                   160032  4 radeon,ttm
i2c_algo_bit            5760  1 radeon
e1000                 119072  0 
intel_agp              27676  1 
agpgart                34988  3 ttm,drm,intel_agp

dmesg returns :

[    0.096658] pci 0000:00:1f.5: reg 10 io port: [0x1c00-0x1cff]
[    0.096665] pci 0000:00:1f.5: reg 14 io port: [0x18c0-0x18ff]
[    0.096672] pci 0000:00:1f.5: reg 18 32bit mmio: [0xc0000c00-0xc0000dff]
[    0.096680] pci 0000:00:1f.5: reg 1c 32bit mmio: [0xc0000800-0xc00008ff]
[    0.096710] pci 0000:00:1f.5: PME# supported from D0 D3hot D3cold
[    0.096715] pci 0000:00:1f.5: PME# disabled
[    0.096746] pci 0000:00:1f.6: reg 10 io port: [0x2400-0x24ff]
[    0.096753] pci 0000:00:1f.6: reg 14 io port: [0x2000-0x207f]
[    0.096791] pci 0000:00:1f.6: PME# supported from D0 D3hot D3cold
[    0.096796] pci 0000:00:1f.6: PME# disabled
[    0.096835] pci 0000:01:00.0: reg 10 32bit mmio: [0xe0000000-0xe7ffffff]
[    0.096842] pci 0000:01:00.0: reg 14 io port: [0x3000-0x30ff]
[    0.096848] pci 0000:01:00.0: reg 18 32bit mmio: [0xc0100000-0xc010ffff]
[    0.096864] pci 0000:01:00.0: reg 30 32bit mmio: [0x000000-0x01ffff]
[    0.096884] pci 0000:01:00.0: supports D1 D2
[    0.096920] pci 0000:00:01.0: bridge io port: [0x3000-0x3fff]
[    0.096925] pci 0000:00:01.0: bridge 32bit mmio: [0xc0100000-0xc01fffff]
[    0.096929] pci 0000:00:01.0: bridge 32bit mmio pref: [0xe0000000-0xe7ffffff]
[    0.096966] pci 0000:02:00.0: reg 10 32bit mmio: [0xb0000000-0xb0000fff]
[    0.096986] pci 0000:02:00.0: supports D1 D2
[    0.096989] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.096994] pci 0000:02:00.0: PME# disabled
[    0.097030] pci 0000:02:00.1: reg 10 32bit mmio: [0xb1000000-0xb1000fff]
[    0.097050] pci 0000:02:00.1: supports D1 D2
[    0.097052] pci 0000:02:00.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.097058] pci 0000:02:00.1: PME# disabled
[    0.097105] pci 0000:02:01.0: reg 10 32bit mmio: [0xc0220000-0xc023ffff]
[    0.097113] pci 0000:02:01.0: reg 14 32bit mmio: [0xc0200000-0xc020ffff]
[    0.097120] pci 0000:02:01.0: reg 18 io port: [0x8000-0x803f]
[    0.097141] pci 0000:02:01.0: reg 30 32bit mmio: [0x000000-0x00ffff]
[    0.097165] pci 0000:02:01.0: PME# supported from D0 D3hot D3cold
[    0.097170] pci 0000:02:01.0: PME# disabled
[    0.097205] pci 0000:02:02.0: reg 10 32bit mmio: [0xc0210000-0xc021ffff]
[    0.097288] pci 0000:00:1e.0: transparent bridge
[    0.097293] pci 0000:00:1e.0: bridge io port: [0x4000-0x8fff]
[    0.097298] pci 0000:00:1e.0: bridge 32bit mmio: [0xc0200000-0xcfffffff]
[    0.097304] pci 0000:00:1e.0: bridge 32bit mmio pref: [0xe8000000-0xefffffff]
[    0.097345] pci_bus 0000:00: on NUMA node 0
[    0.097351] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.097410] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    0.097442] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[    0.101497] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11)
[    0.101709] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11)
[    0.101918] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 *11)
[    0.102125] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11)
[    0.102313] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11) *0, disabled.
[    0.102501] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11) *0, disabled.
[    0.102693] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11) *0, disabled.
[    0.102902] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 *11)
[    0.103171] SCSI subsystem initialized
[    0.103247] libata version 3.00 loaded.
[    0.103348] usbcore: registered new interface driver usbfs
[    0.103380] usbcore: registered new interface driver hub
[    0.103411] usbcore: registered new device driver usb
[    0.103574] ACPI: WMI: Mapper loaded
[    0.103577] PCI: Using ACPI for IRQ routing
[    0.103896] Bluetooth: Core ver 2.15
[    0.103928] NET: Registered protocol family 31
[    0.103931] Bluetooth: HCI device and connection manager initialized
[    0.103935] Bluetooth: HCI socket layer initialized
[    0.103938] NetLabel: Initializing
[    0.103940] NetLabel:  domain hash size = 128
[    0.103942] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.103960] NetLabel:  unlabeled traffic allowed by default
[    0.106413] pnp: PnP ACPI init
[    0.106452] ACPI: bus type pnp registered
[    0.111817] pnp: PnP ACPI: found 13 devices
[    0.111821] ACPI: ACPI bus type pnp unregistered
[    0.111827] PnPBIOS: Disabled by ACPI PNP
[    0.111844] system 00:00: iomem range 0x0-0x9ffff could not be reserved
[    0.111849] system 00:00: iomem range 0xc0000-0xc3fff could not be reserved
[    0.111853] system 00:00: iomem range 0xc4000-0xc7fff could not be reserved
[    0.111857] system 00:00: iomem range 0xc8000-0xcbfff could not be reserved
[    0.111861] system 00:00: iomem range 0xcc000-0xcffff could not be reserved
[    0.111865] system 00:00: iomem range 0xd0000-0xd3fff could not be reserved
[    0.111869] system 00:00: iomem range 0xdc000-0xdffff could not be reserved
[    0.111873] system 00:00: iomem range 0xe0000-0xe3fff could not be reserved
[    0.111877] system 00:00: iomem range 0xe4000-0xe7fff could not be reserved
[    0.111881] system 00:00: iomem range 0xe8000-0xebfff could not be reserved
[    0.111885] system 00:00: iomem range 0xec000-0xeffff could not be reserved
[    0.111889] system 00:00: iomem range 0xf0000-0xfffff could not be reserved
[    0.111893] system 00:00: iomem range 0x100000-0x3fffffff could not be reserved
[    0.111898] system 00:00: iomem range 0xfec00000-0xffffffff could not be reserved
[    0.111908] system 00:02: ioport range 0x1000-0x107f has been reserved
[    0.111912] system 00:02: ioport range 0x1180-0x11bf has been reserved
[    0.111916] system 00:02: ioport range 0x15e0-0x15ef has been reserved
[    0.111919] system 00:02: ioport range 0x1600-0x162f has been reserved
[    0.111923] system 00:02: ioport range 0x1632-0x167f has been reserved
[    0.111927] system 00:02: ioport range 0x1630-0x1631 has been reserved
[    0.146660] AppArmor: AppArmor Filesystem Enabled
[    0.146700] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.146704] pci 0000:00:01.0:   IO window: 0x3000-0x3fff
[    0.146709] pci 0000:00:01.0:   MEM window: 0xc0100000-0xc01fffff
[    0.146714] pci 0000:00:01.0:   PREFETCH window: 0xe0000000-0xe7ffffff
[    0.146723] pci 0000:02:00.0: CardBus bridge, secondary bus 0000:03
[    0.146727] pci 0000:02:00.0:   IO window: 0x004000-0x0040ff
[    0.146732] pci 0000:02:00.0:   IO window: 0x004400-0x0044ff
[    0.146738] pci 0000:02:00.0:   PREFETCH window: 0xe8000000-0xebffffff
[    0.146743] pci 0000:02:00.0:   MEM window: 0xc4000000-0xc7ffffff
[    0.146749] pci 0000:02:00.1: CardBus bridge, secondary bus 0000:07
[    0.146752] pci 0000:02:00.1:   IO window: 0x004800-0x0048ff
[    0.146758] pci 0000:02:00.1:   IO window: 0x004c00-0x004cff
[    0.146763] pci 0000:02:00.1:   PREFETCH window: 0xec000000-0xefffffff
[    0.146769] pci 0000:02:00.1:   MEM window: 0xc8000000-0xcbffffff
[    0.146774] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:02
[    0.146779] pci 0000:00:1e.0:   IO window: 0x4000-0x8fff
[    0.146785] pci 0000:00:1e.0:   MEM window: 0xc0200000-0xcfffffff
[    0.146790] pci 0000:00:1e.0:   PREFETCH window: 0xe8000000-0xefffffff
[    0.146807] pci 0000:00:1e.0: setting latency timer to 64
[    0.147190] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[    0.147194] PCI: setting IRQ 11 as level-triggered
[    0.147200] pci 0000:02:00.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[    0.147556] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
[    0.147561] pci 0000:02:00.1: PCI INT B -> Link[LNKB] -> GSI 11 (level, low) -> IRQ 11
[    0.147571] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.147575] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.147579] pci_bus 0000:01: resource 0 io:  [0x3000-0x3fff]
[    0.147582] pci_bus 0000:01: resource 1 mem: [0xc0100000-0xc01fffff]
[    0.147586] pci_bus 0000:01: resource 2 pref mem [0xe0000000-0xe7ffffff]
[    0.147590] pci_bus 0000:02: resource 0 io:  [0x4000-0x8fff]
[    0.147593] pci_bus 0000:02: resource 1 mem: [0xc0200000-0xcfffffff]
[    0.147597] pci_bus 0000:02: resource 2 pref mem [0xe8000000-0xefffffff]
[    0.147600] pci_bus 0000:02: resource 3 io:  [0x00-0xffff]
[    0.147604] pci_bus 0000:02: resource 4 mem: [0x000000-0xffffffff]
[    0.147608] pci_bus 0000:03: resource 0 io:  [0x4000-0x40ff]
[    0.147611] pci_bus 0000:03: resource 1 io:  [0x4400-0x44ff]
[    0.147614] pci_bus 0000:03: resource 2 pref mem [0xe8000000-0xebffffff]
[    0.147618] pci_bus 0000:03: resource 3 mem: [0xc4000000-0xc7ffffff]
[    0.147622] pci_bus 0000:07: resource 0 io:  [0x4800-0x48ff]
[    0.147625] pci_bus 0000:07: resource 1 io:  [0x4c00-0x4cff]
[    0.147629] pci_bus 0000:07: resource 2 pref mem [0xec000000-0xefffffff]
[    0.147632] pci_bus 0000:07: resource 3 mem: [0xc8000000-0xcbffffff]
[    0.147689] NET: Registered protocol family 2
[    0.147832] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.148349] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.150201] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.151342] TCP: Hash tables configured (established 131072 bind 65536)
[    0.151346] TCP reno registered
[    0.151528] NET: Registered protocol family 1
[    0.151643] Trying to unpack rootfs image as initramfs...
[    0.424464] Freeing initrd memory: 7473k freed
[    0.436661] Simple Boot Flag at 0x35 set to 0x1
[    0.436774] cpufreq-nforce2: No nForce2 chipset.
[    0.436830] Scanning for low memory corruption every 60 seconds
[    0.436996] audit: initializing netlink socket (disabled)
[    0.437040] type=2000 audit(1269892172.436:1): initialized
[    0.448571] highmem bounce pool size: 64 pages
[    0.448579] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.450620] VFS: Disk quotas dquot_6.5.2
[    0.450703] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.451523] fuse init (API version 7.12)
[    0.451639] msgmni has been set to 1732
[    0.451893] alg: No test for stdrng (krng)
[    0.451908] io scheduler noop registered
[    0.451911] io scheduler anticipatory registered
[    0.451913] io scheduler deadline registered
[    0.451981] io scheduler cfq registered (default)
[    0.452095] pci 0000:01:00.0: Boot video device
[    0.452224] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.452254] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.452760] ACPI: AC Adapter [AC] (on-line)
[    0.452853] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    0.452858] ACPI: Power Button [PWRF]
[    0.452918] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
[    0.453371] ACPI: Lid Switch [LID]
[    0.453436] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    0.453442] ACPI: Sleep Button [SLPB]
[    0.455838] Marking TSC unstable due to TSC halts in idle
[    0.455860] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    0.455890] processor LNXCPU:00: registered as cooling_device0
[    0.455895] ACPI: Processor [CPU0] (supports 8 throttling states)
[    0.456024] Switched to high resolution mode on CPU 0
[    0.462185] thermal LNXTHERM:01: registered as thermal_zone0
[    0.462195] ACPI: Thermal Zone [THM0] (54 C)
[    0.462251] isapnp: Scanning for PnP cards...
[    0.815741] isapnp: No Plug & Play device found
[    0.817226] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.818229] serial 00:0a: activated
[    0.818324] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a NS16550A
[    0.818445] serial 0000:00:1f.6: PCI INT B -> Link[LNKB] -> GSI 11 (level, low) -> IRQ 11
[    0.818453] serial 0000:00:1f.6: PCI INT B disabled
[    0.819626] brd: module loaded
[    0.820294] loop: module loaded
[    0.820391] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    0.820532] ata_piix 0000:00:1f.1: version 2.13
[    0.820542] ata_piix 0000:00:1f.1: enabling device (0005 -> 0007)
[    0.820924] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[    0.820929] ata_piix 0000:00:1f.1: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[    0.820981] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.821075] scsi0 : ata_piix
[    0.821253] scsi1 : ata_piix
[    0.822310] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1860 irq 14
[    0.822314] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1868 irq 15
[    0.823421] Fixed MDIO Bus: probed
[    0.823478] PPP generic driver version 2.4.2
[    0.823593] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.854359] ACPI: Battery Slot [BAT0] (battery present)
[    0.859299] ehci_hcd 0000:00:1d.7: power state changed by ACPI to D0
[    0.859660] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 11
[    0.859665] ehci_hcd 0000:00:1d.7: PCI INT D -> Link[LNKH] -> GSI 11 (level, low) -> IRQ 11
[    0.859685] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.859690] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.859735] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.863642] ehci_hcd 0000:00:1d.7: debug port 1
[    0.863649] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.863659] ehci_hcd 0000:00:1d.7: irq 11, io mem 0xc0000000
[    0.876038] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.876149] usb usb1: configuration #1 chosen from 1 choice
[    0.876186] hub 1-0:1.0: USB hub found
[    0.876197] hub 1-0:1.0: 6 ports detected
[    0.876267] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.876295] uhci_hcd: USB Universal Host Controller Interface driver
[    0.876702] uhci_hcd 0000:00:1d.0: power state changed by ACPI to D0
[    0.876710] uhci_hcd 0000:00:1d.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[    0.876717] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.876721] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.876763] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.876786] uhci_hcd 0000:00:1d.0: irq 11, io base 0x00001800
[    0.876898] usb usb2: configuration #1 chosen from 1 choice
[    0.876933] hub 2-0:1.0: USB hub found
[    0.876942] hub 2-0:1.0: 2 ports detected
[    0.877606] uhci_hcd 0000:00:1d.1: power state changed by ACPI to D0
[    0.877964] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[    0.877969] uhci_hcd 0000:00:1d.1: PCI INT B -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
[    0.877976] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.877980] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.878018] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.878040] uhci_hcd 0000:00:1d.1: irq 11, io base 0x00001820
[    0.878140] usb usb3: configuration #1 chosen from 1 choice
[    0.878172] hub 3-0:1.0: USB hub found
[    0.878180] hub 3-0:1.0: 2 ports detected
[    0.878231] uhci_hcd 0000:00:1d.2: PCI INT C -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[    0.878238] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.878242] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.878276] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.878298] uhci_hcd 0000:00:1d.2: irq 11, io base 0x00001840
[    0.878407] usb usb4: configuration #1 chosen from 1 choice
[    0.878442] hub 4-0:1.0: USB hub found
[    0.878451] hub 4-0:1.0: 2 ports detected
[    0.878563] PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
[    0.884637] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.884644] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.884716] mice: PS/2 mouse device common for all mice
[    0.884843] rtc_cmos 00:06: RTC can wake from S4
[    0.884883] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    0.884904] rtc0: alarms up to one month, y3k, 114 bytes nvram
[    0.885063] device-mapper: uevent: version 1.0.3
[    0.885185] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.885285] device-mapper: multipath: version 1.1.0 loaded
[    0.885289] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.885453] EISA: Probing bus 0 at eisa.0
[    0.885459] Cannot allocate resource for EISA slot 1
[    0.885463] Cannot allocate resource for EISA slot 2
[    0.885466] Cannot allocate resource for EISA slot 3
[    0.885468] Cannot allocate resource for EISA slot 4
[    0.885471] Cannot allocate resource for EISA slot 5
[    0.885474] Cannot allocate resource for EISA slot 6
[    0.885476] Cannot allocate resource for EISA slot 7
[    0.885479] Cannot allocate resource for EISA slot 8
[    0.885482] EISA: Detected 0 cards.
[    0.885580] cpuidle: using governor ladder
[    0.885665] cpuidle: using governor menu
[    0.886386] TCP cubic registered
[    0.886617] NET: Registered protocol family 10
[    0.887215] lo: Disabled Privacy Extensions
[    0.887660] NET: Registered protocol family 17
[    0.887681] Bluetooth: L2CAP ver 2.13
[    0.887683] Bluetooth: L2CAP socket layer initialized
[    0.887687] Bluetooth: SCO (Voice Link) ver 0.6
[    0.887689] Bluetooth: SCO socket layer initialized
[    0.887735] Bluetooth: RFCOMM TTY layer initialized
[    0.887739] Bluetooth: RFCOMM socket layer initialized
[    0.887742] Bluetooth: RFCOMM ver 1.11
[    0.887914] P-state transition latency capped at 20 uS
[    0.888236] Using IPI No-Shortcut mode
[    0.888318] PM: Resume from disk failed.
[    0.888333] registered taskstats version 1
[    0.888485]   Magic number: 2:963:850
[    0.888600] rtc_cmos 00:06: setting system clock to 2010-03-29 19:49:33 UTC (1269892173)
[    0.888604] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.888617] EDD information not available.
[    0.890644] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    0.984338] ata2.01: NODEV after polling detection
[    0.992958] ata1.00: HPA unlocked: 71973874 -> 78140160, native 78140160
[    0.992965] ata1.00: ATA-5: IC25N040ATCS05-0, CS4OA61A, max UDMA/100
[    0.992969] ata1.00: 78140160 sectors, multi 16: LBA 
[    0.993162] ata2.00: ATAPI: UJDA745 DVD/CDRW, 1.02, max UDMA/33
[    1.008824] ata2.00: configured for UDMA/33
[    1.008968] ata1.00: configured for UDMA/100
[    1.009131] scsi 0:0:0:0: Direct-Access     ATA      IC25N040ATCS05-0 CS4O PQ: 0 ANSI: 5
[    1.009285] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.009332] sd 0:0:0:0: [sda] 78140160 512-byte logical blocks: (40.0 GB/37.2 GiB)
[    1.009388] sd 0:0:0:0: [sda] Write Protect is off
[    1.009392] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.009421] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.009594]  sda:
[    1.012726] scsi 1:0:0:0: CD-ROM            MATSHITA UJDA745 DVD/CDRW 1.02 PQ: 0 ANSI: 5
[    1.019664] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    1.019669] Uniform CD-ROM driver Revision: 3.20
[    1.019773] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.019826] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.027929]  sda1 sda2 < sda5 >
[    1.050850] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.050871] Freeing unused kernel memory: 540k freed
[    1.051331] Write protecting the kernel text: 4580k
[    1.051379] Write protecting the kernel read-only data: 1840k
[    1.285038] Linux agpgart interface v0.103
[    1.306532] agpgart-intel 0000:00:00.0: Intel 855PM Chipset
[    1.363162] Intel(R) PRO/1000 Network Driver - version 7.3.21-k3-NAPI
[    1.363168] Copyright (c) 1999-2006 Intel Corporation.
[    1.363248] e1000 0000:02:01.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[    1.442537] usb 3-2: new low speed USB device using uhci_hcd and address 2
[    1.454374] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[    1.681510] e1000: 0000:02:01.0: e1000_probe: (PCI:33MHz:32-bit) 00:11:25:b0:0d:3e
[    1.692615] [drm] Initialized drm 1.1.0 20060810
[    1.732144] [drm] radeon default to kernel modesetting DISABLED.
[    1.732329] pci 0000:01:00.0: power state changed by ACPI to D0
[    1.732343] pci 0000:01:00.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[    1.733139] [drm] Initialized radeon 1.31.0 20080528 for 0000:01:00.0 on minor 0
[    1.737429] Floppy drive(s): fd0 is 1.44M
[    1.746344] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:03/device:04/input/input5
[    1.746404] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[    1.755079] FDC 0 is a National Semiconductor PC87306
[    1.769928] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
[    1.805338] usb 3-2: configuration #1 chosen from 1 choice
[    1.819089] usbcore: registered new interface driver hiddev
[    1.832595] input: USB Optical Mouse as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.0/input/input6
[    1.832709] generic-usb 0003:04B3:310C.0001: input,hidraw0: USB HID v1.11 Mouse [USB Optical Mouse] on usb-0000:00:1d.1-2/input0
[    1.832729] usbcore: registered new interface driver usbhid
[    1.832738] usbhid: v2.6:USB HID core driver
[    2.658292] PM: Starting manual resume from disk
[    2.658297] PM: Resume from partition 8:5
[    2.658300] PM: Checking hibernation image.
[    2.658452] PM: Resume from disk failed.
[    2.686084] EXT4-fs (sda1): barriers enabled
[    2.710244] kjournald2 starting: pid 352, dev sda1:8, commit interval 5 seconds
[    2.710285] EXT4-fs (sda1): delayed allocation enabled
[    2.710289] EXT4-fs: file extents enabled
[    2.716205] EXT4-fs: mballoc enabled
[    2.716226] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    3.607173] type=1505 audit(1269892176.215:2): operation="profile_load" pid=376 name=/usr/share/gdm/guest-session/Xsession
[    3.631082] type=1505 audit(1269892176.239:3): operation="profile_load" pid=377 name=/sbin/dhclient3
[    3.631872] type=1505 audit(1269892176.239:4): operation="profile_load" pid=377 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    3.632336] type=1505 audit(1269892176.243:5): operation="profile_load" pid=377 name=/usr/lib/connman/scripts/dhclient-script
[    3.717664] type=1505 audit(1269892176.327:6): operation="profile_load" pid=378 name=/usr/bin/evince
[    3.731230] type=1505 audit(1269892176.339:7): operation="profile_load" pid=378 name=/usr/bin/evince-previewer
[    3.739106] type=1505 audit(1269892176.347:8): operation="profile_load" pid=378 name=/usr/bin/evince-thumbnailer
[    3.758308] type=1505 audit(1269892176.367:9): operation="profile_load" pid=380 name=/usr/lib/cups/backend/cups-pdf
[   20.438489] udev: starting version 147
[   20.476345] Adding 1646620k swap on /dev/sda5.  Priority:-1 extents:1 across:1646620k 
[   20.615712] intel_rng: FWH not detected
[   20.688929] lp: driver loaded but no devices found
[   20.876931] EXT4-fs (sda1): internal journal on sda1:8
[   21.025998] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   21.095979] irda_init()
[   21.096041] NET: Registered protocol family 23
[   21.102392] nsc-ircc 00:0c: activated
[   21.102398] nsc_ircc_pnp_probe() : From PnP, found firbase 0x2F8 ; irq 3 ; dma 1.
[   21.102565] nsc-ircc, chip->init
[   21.102574] nsc-ircc, Found chip at base=0x02e
[   21.102598] nsc-ircc, driver loaded (Dag Brattli)
[   21.103499] IrDA: Registered device irda0
[   21.103502] nsc-ircc, Using dongle: IBM31T1100 or Temic TFDS6000/TFDS6500
[   21.121789] parport_pc 00:0b: reported by Plug and Play ACPI
[   21.121834] parport0: PC-style at 0x3bc, irq 7 [PCSPP,TRISTATE]
[   21.151021] cfg80211: Calling CRDA to update world regulatory domain
[   21.206029] lp0: using parport0 (interrupt-driven).
[   21.221953] ath5k 0000:02:02.0: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[   21.222027] ath5k 0000:02:02.0: registered as 'phy0'
[   21.429761] Non-volatile memory driver v1.3
[   21.433620] cfg80211: World regulatory domain updated:
[   21.433625]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   21.433629]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   21.433633]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   21.433637]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   21.433640]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   21.433644]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   21.444562] thinkpad_acpi: ThinkPad ACPI Extras v0.23
[   21.444566] thinkpad_acpi: http://ibm-acpi.sf.net/
[   21.444569] thinkpad_acpi: ThinkPad BIOS 1RETDRWW (3.23 ), EC 1RHT71WW-3.04
[   21.444572] thinkpad_acpi: IBM ThinkPad T40p, model 2373G1G
[   21.466477] ip_tables: (C) 2000-2006 Netfilter Core Team
[   21.503986] ppdev: user-space parallel port driver
[   21.505032] Registered led device: tpacpi::thinklight
[   21.505088] Registered led device: tpacpi::power
[   21.505108] Registered led device: tpacpi::standby
[   21.526134] ath: EEPROM regdomain: 0x61
[   21.526140] ath: EEPROM indicates we should expect a direct regpair map
[   21.526146] ath: Country alpha2 being used: 00
[   21.526148] ath: Regpair used: 0x61
[   21.534213] input: ThinkPad Extra Buttons as /devices/virtual/input/input7
[   21.640625] Intel ICH 0000:00:1f.5: PCI INT B -> Link[LNKB] -> GSI 11 (level, low) -> IRQ 11
[   21.640684] Intel ICH 0000:00:1f.5: setting latency timer to 64
[   21.752101] phy0: Selected rate control algorithm 'minstrel'
[   21.753144] Registered led device: ath5k-phy0::rx
[   21.753165] Registered led device: ath5k-phy0::tx
[   21.753170] ath5k phy0: Atheros AR5211 chip found (MAC: 0x42, PHY: 0x30)
[   21.753174] ath5k phy0: RF5111 5GHz radio found (0x17)
[   21.753177] ath5k phy0: RF2111 2GHz radio found (0x23)
[   21.755606] yenta_cardbus 0000:02:00.0: CardBus bridge found [1014:0512]
[   21.755629] yenta_cardbus 0000:02:00.0: Using INTVAL to route CSC interrupts to PCI
[   21.755633] yenta_cardbus 0000:02:00.0: Routing CardBus interrupts to PCI
[   21.755639] yenta_cardbus 0000:02:00.0: TI: mfunc 0x01d21022, devctl 0x64
[   21.984512] yenta_cardbus 0000:02:00.0: ISA IRQ mask 0x0430, PCI irq 11
[   21.984518] yenta_cardbus 0000:02:00.0: Socket status: 30000006
[   21.984529] yenta_cardbus 0000:02:00.0: pcmcia: parent PCI bridge I/O window: 0x4000 - 0x8fff
[   21.984534] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x4000-0x8fff: clean.
[   21.985929] yenta_cardbus 0000:02:00.0: pcmcia: parent PCI bridge Memory window: 0xc0200000 - 0xcfffffff
[   21.985933] yenta_cardbus 0000:02:00.0: pcmcia: parent PCI bridge Memory window: 0xe8000000 - 0xefffffff
[   22.011525] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   22.016434] yenta_cardbus 0000:02:00.1: CardBus bridge found [1014:0512]
[   22.016457] yenta_cardbus 0000:02:00.1: Using INTVAL to route CSC interrupts to PCI
[   22.016461] yenta_cardbus 0000:02:00.1: Routing CardBus interrupts to PCI
[   22.016467] yenta_cardbus 0000:02:00.1: TI: mfunc 0x01d21022, devctl 0x64
[   22.227075] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x2c6ab1, caps: 0x884793/0x0
[   22.227085] serio: Synaptics pass-through port at isa0060/serio1/input0
[   22.236521] __ratelimit: 6 callbacks suppressed
[   22.236526] type=1505 audit(1269892194.847:12): operation="profile_replace" pid=893 name=/usr/share/gdm/guest-session/Xsession
[   22.239869] type=1505 audit(1269892194.847:13): operation="profile_replace" pid=895 name=/sbin/dhclient3
[   22.240758] type=1505 audit(1269892194.851:14): operation="profile_replace" pid=895 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   22.241195] type=1505 audit(1269892194.851:15): operation="profile_replace" pid=895 name=/usr/lib/connman/scripts/dhclient-script
[   22.251111] yenta_cardbus 0000:02:00.1: ISA IRQ mask 0x0430, PCI irq 11
[   22.251118] yenta_cardbus 0000:02:00.1: Socket status: 30000006
[   22.251131] yenta_cardbus 0000:02:00.1: pcmcia: parent PCI bridge I/O window: 0x4000 - 0x8fff
[   22.251137] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x4000-0x8fff: clean.
[   22.252562] yenta_cardbus 0000:02:00.1: pcmcia: parent PCI bridge Memory window: 0xc0200000 - 0xcfffffff
[   22.252567] yenta_cardbus 0000:02:00.1: pcmcia: parent PCI bridge Memory window: 0xe8000000 - 0xefffffff
[   22.281982] type=1505 audit(1269892194.891:16): operation="profile_replace" pid=899 name=/usr/bin/evince
[   22.300307] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input8
[   22.319730] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   22.341419] type=1505 audit(1269892194.951:17): operation="profile_replace" pid=899 name=/usr/bin/evince-previewer
[   22.365639] type=1505 audit(1269892194.975:18): operation="profile_replace" pid=899 name=/usr/bin/evince-thumbnailer
[   22.402143] type=1505 audit(1269892195.011:19): operation="profile_replace" pid=914 name=/usr/lib/cups/backend/cups-pdf
[   22.403084] type=1505 audit(1269892195.011:20): operation="profile_replace" pid=914 name=/usr/sbin/cupsd
[   22.406970] type=1505 audit(1269892195.015:21): operation="profile_replace" pid=915 name=/usr/sbin/tcpdump
[   22.630100] intel8x0_measure_ac97_clock: measured 99939 usecs (4807 samples)
[   22.630106] intel8x0: clocking to 48000
[   22.872910] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x100-0x3af: clean.
[   22.873914] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   22.874350] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x820-0x8ff: clean.
[   22.874721] pcmcia_socket pcmcia_socket1: cs: IO port probe 0xc00-0xcf7: clean.
[   22.875259] pcmcia_socket pcmcia_socket1: cs: IO port probe 0xa00-0xaff: clean.
[   22.885817] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
[   22.886829] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   22.887265] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   22.887636] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   22.888199] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   24.035661] agpgart-intel 0000:00:00.0: AGP 2.0 bridge
[   24.035683] agpgart-intel 0000:00:00.0: putting AGP V2 device into 4x mode
[   24.035723] pci 0000:01:00.0: putting AGP V2 device into 4x mode
[   24.288168] [drm] Setting GART location based on new memory map
[   24.288180] [drm] Loading R200 Microcode
[   24.288236] [drm] writeback test succeeded in 2 usecs
[   26.240165] psmouse serio2: ID: 10 00 64
[   32.276060] IBM TrackPoint firmware: 0x0e, buttons: 3/3
[   32.764209] input: TPPS/2 IBM TrackPoint as /devices/platform/i8042/serio1/serio2/input/input9
[   63.883336] wlan0: direct probe to AP 00:0f:66:36:b8:b9 try 1
[   64.080047] wlan0: direct probe to AP 00:0f:66:36:b8:b9 try 2
[   64.280046] wlan0: direct probe to AP 00:0f:66:36:b8:b9 try 3
[   64.480045] wlan0: direct probe to AP 00:0f:66:36:b8:b9 timed out
[   76.383324] wlan0: direct probe to AP 00:0f:66:36:b8:b9 try 1
[   76.580045] wlan0: direct probe to AP 00:0f:66:36:b8:b9 try 2
[   76.780046] wlan0: direct probe to AP 00:0f:66:36:b8:b9 try 3
[   76.980041] wlan0: direct probe to AP 00:0f:66:36:b8:b9 timed out
[   85.144049] Clocksource tsc unstable (delta = -298302123 ns)
[   99.798201] thinkpad_acpi: deprecated sysfs attribute: access by process with PID 1740
[   99.798207] thinkpad_acpi: WARNING: sysfs attribute hotkey_enable is deprecated and will be removed. Hotkey reporting is always enabled
[   99.799049] thinkpad_acpi: deprecated sysfs attribute: access by process with PID 1740
[   99.799053] thinkpad_acpi: WARNING: sysfs attribute bluetooth_enable is deprecated and will be removed. Please switch to generic rfkill before year 2010
[  101.299913] wlan0: direct probe to AP 00:0f:66:36:b8:b9 try 1
[  101.496087] wlan0: direct probe to AP 00:0f:66:36:b8:b9 try 2
[  101.696065] wlan0: direct probe to AP 00:0f:66:36:b8:b9 try 3
[  101.896077] wlan0: direct probe to AP 00:0f:66:36:b8:b9 timed out
[  113.737064] wlan0: direct probe to AP 00:0f:66:36:b8:b9 try 1
[  113.936074] wlan0: direct probe to AP 00:0f:66:36:b8:b9 try 2
[  114.136075] wlan0: direct probe to AP 00:0f:66:36:b8:b9 try 3
[  114.340778] wlan0: direct probe to AP 00:0f:66:36:b8:b9 timed out
[  146.117667] wlan0: direct probe to AP 00:0f:66:45:fe:9c try 1
[  146.318076] wlan0: direct probe to AP 00:0f:66:45:fe:9c try 2
[  146.518605] wlan0: direct probe to AP 00:0f:66:45:fe:9c try 3
[  146.718553] wlan0: direct probe to AP 00:0f:66:45:fe:9c timed out
[  159.176400] e1000: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  159.176817] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  161.183092] wlan0: direct probe to AP 00:0f:66:45:fe:9c try 1
[  161.380074] wlan0: direct probe to AP 00:0f:66:45:fe:9c try 2
[  161.588224] wlan0: direct probe to AP 00:0f:66:45:fe:9c try 3
[  161.792199] wlan0: direct probe to AP 00:0f:66:45:fe:9c timed out
[  169.200028] eth0: no IPv6 routers present
[  173.652342] wlan0: direct probe to AP 00:0f:66:45:fe:9c try 1
[  173.852042] wlan0: direct probe to AP 00:0f:66:45:fe:9c try 2
[  174.052052] wlan0: direct probe to AP 00:0f:66:45:fe:9c try 3
[  174.256045] wlan0: direct probe to AP 00:0f:66:45:fe:9c timed out
[  186.047941] wlan0: direct probe to AP 00:0f:66:45:fe:9c try 1
[  186.244058] wlan0: direct probe to AP 00:0f:66:45:fe:9c try 2
[  186.444055] wlan0: direct probe to AP 00:0f:66:45:fe:9c try 3
[  186.652041] wlan0: direct probe to AP 00:0f:66:45:fe:9c timed out
[  255.060127] cfg80211: Found new beacon on frequency: 5240 MHz (Ch 48) on phy0

END

---

