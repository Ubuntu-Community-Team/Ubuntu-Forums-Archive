---
title: "Asus A8R32-MVP Deluxe (HDA ULI M5461) - No Sound"
date: 2007-01-25
forum: Multimedia &amp; Video
---

### Post by EyeScreaMan on 2007-01-25
Hello :)

I have Asus A8R32-MVP Deluxe motherboard:

```

root@pytong:~# cat /proc/asound/cards
 0 [M5461          ]: HDA-Intel - HDA ULI M5461
                      HDA ULI M5461 at 0xdfcfc000 irq 50

```

```

root@pytong:~# cat /proc/asound/pcm
00-02: ALC882 Analog : ALC882 Analog : capture 2
00-01: ALC882 Digital : ALC882 Digital : playback 1
00-00: ALC882 Analog : ALC882 Analog : playback 1 : capture 2

```

```

root@pytong:~# cat /proc/asound/modules
 0 snd_hda_intel

```

```

root@pytong:~# aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: M5461 [HDA ULI M5461], device 0: ALC882 Analog [ALC882 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: M5461 [HDA ULI M5461], device 1: ALC882 Digital [ALC882 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```



Here is all devices listing:

```

root@pytong:~# lspci -v 
00:00.0 Host bridge: ATI Technologies Inc Unknown device 5952
        Subsystem: ASUSTeK Computer Inc. Unknown device 8194
        Flags: bus master, 66MHz, medium devsel, latency 64

00:02.0 PCI bridge: ATI Technologies Inc RS480 PCI-X Root Port (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        I/O behind bridge: 0000e000-0000efff
        Memory behind bridge: dff00000-dfffffff
        Prefetchable memory behind bridge: 00000000c0000000-00000000cff00000
        Capabilities: [50] Power Management version 3
        Capabilities: [58] Express Root Port (Slot-) IRQ 0
        Capabilities: [80] Message Signalled Interrupts: 64bit- Queue=0/0 Enable+
        Capabilities: [b0] #0d [0000]
        Capabilities: [b8] HyperTransport: MSI Mapping

00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        I/O behind bridge: 0000d000-0000dfff
        Memory behind bridge: dfe00000-dfefffff
        Capabilities: [50] Power Management version 3
        Capabilities: [58] Express Root Port (Slot-) IRQ 0
        Capabilities: [80] Message Signalled Interrupts: 64bit- Queue=0/0 Enable+
        Capabilities: [b0] #0d [0000]
        Capabilities: [b8] HyperTransport: MSI Mapping

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
        Flags: fast devsel
        Capabilities: [80] HyperTransport: Host or Secondary Interface

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
        Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
        Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
        Flags: fast devsel

00:1a.0 PCI bridge: ALi Corporation M5249 HTT to PCI Bridge (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 0000c000-0000cfff
        Memory behind bridge: dfd00000-dfdfffff
        Capabilities: [c0] HyperTransport: MSI Mapping

00:1c.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03) (prog-if 10 [OHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 8056
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 201
        Memory at dfcf8000 (32-bit, non-prefetchable) [size=4K]

00:1c.1 USB Controller: ALi Corporation USB 1.1 Controller (rev 03) (prog-if 10 [OHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 8056
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 217
        Memory at dfcf9000 (32-bit, non-prefetchable) [size=4K]

00:1c.2 USB Controller: ALi Corporation USB 1.1 Controller (rev 03) (prog-if 10 [OHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 8056
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 193
        Memory at dfcfa000 (32-bit, non-prefetchable) [size=4K]

00:1c.3 USB Controller: ALi Corporation USB 2.0 Controller (rev 01) (prog-if 20 [EHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 8056
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 209
        Memory at dfcfbc00 (32-bit, non-prefetchable) [size=256]
        Capabilities: [50] Power Management version 2
        Capabilities: [58] Debug port
        Capabilities: [78] Message Signalled Interrupts: 64bit- Queue=0/0 Enable-

00:1d.0 Audio device: ALi Corporation High Definition Audio/AC'97 Host Controller (rev 02)
        Subsystem: ASUSTeK Computer Inc. Unknown device 817f
        Flags: bus master, medium devsel, latency 64, IRQ 50
        Memory at dfcfc000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
        Capabilities: [60] Message Signalled Interrupts: 64bit- Queue=0/0 Enable-

00:1e.0 ISA bridge: ALi Corporation Unknown device 1575
        Subsystem: ALi Corporation Unknown device 1575
        Flags: bus master, medium devsel, latency 64

00:1e.1 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
        Subsystem: ASUSTeK Computer Inc. Unknown device 8056
        Flags: medium devsel

00:1f.0 IDE interface: ALi Corporation M5229 IDE (rev c8) (prog-if fa)
        Subsystem: ASUSTeK Computer Inc. Unknown device 8056
        Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 193
        I/O ports at ff00 [size=16]
        Capabilities: [60] Power Management version 2
        Capabilities: [80] Message Signalled Interrupts: 64bit- Queue=0/0 Enable-

01:14.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 14)
        Subsystem: ASUSTeK Computer Inc. Marvell 88E8001 Gigabit Ethernet Controller (Asus)
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 233
        Memory at dfdfc000 (32-bit, non-prefetchable) [size=16K]
        I/O ports at c800 [size=256]
        Expansion ROM at dfdc0000 [disabled] [size=128K]
        Capabilities: [48] Power Management version 2
        Capabilities: [50] Vital Product Data

02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 20)
        Subsystem: ASUSTeK Computer Inc. Marvell 88E8053 Gigabit Ethernet controller PCIe (Asus)
        Flags: bus master, fast devsel, latency 0, IRQ 225
        Memory at dfefc000 (64-bit, non-prefetchable) [size=16K]
        I/O ports at d800 [size=256]
        Expansion ROM at dfec0000 [disabled] [size=128K]
        Capabilities: [48] Power Management version 2
        Capabilities: [50] Vital Product Data
        Capabilities: [5c] Message Signalled Interrupts: 64bit+ Queue=0/1 Enable+
        Capabilities: [e0] Express Legacy Endpoint IRQ 0

03:00.0 VGA compatible controller: ATI Technologies Inc R480 [Radeon X850XT Platinum (PCIE)] (prog-if 00 [VGA])
        Subsystem: ATI Technologies Inc Unknown device 0b12
        Flags: bus master, fast devsel, latency 0, IRQ 11
        Memory at c0000000 (64-bit, prefetchable) [size=256M]
        Memory at dffe0000 (64-bit, non-prefetchable) [size=64K]
        I/O ports at e800 [size=256]
        Expansion ROM at dffc0000 [disabled] [size=128K]
        Capabilities: [50] Power Management version 2
        Capabilities: [58] Express Endpoint IRQ 0
        Capabilities: [80] Message Signalled Interrupts: 64bit+ Queue=0/0 Enable-

03:00.1 Display controller: ATI Technologies Inc R480 [Radeon X850XT Platinum (PCIE)] (Secondary)
        Subsystem: ATI Technologies Inc Unknown device 0b13
        Flags: bus master, fast devsel, latency 0
        Memory at dfff0000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: [50] Power Management version 2
        Capabilities: [58] Express Endpoint IRQ 0

root@pytong:~# lspci -v 
00:00.0 Host bridge: ATI Technologies Inc Unknown device 5952
        Subsystem: ASUSTeK Computer Inc. Unknown device 8194
        Flags: bus master, 66MHz, medium devsel, latency 64

00:02.0 PCI bridge: ATI Technologies Inc RS480 PCI-X Root Port (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        I/O behind bridge: 0000e000-0000efff
        Memory behind bridge: dff00000-dfffffff
        Prefetchable memory behind bridge: 00000000c0000000-00000000cff00000
        Capabilities: [50] Power Management version 3
        Capabilities: [58] Express Root Port (Slot-) IRQ 0
        Capabilities: [80] Message Signalled Interrupts: 64bit- Queue=0/0 Enable+
        Capabilities: [b0] #0d [0000]
        Capabilities: [b8] HyperTransport: MSI Mapping

00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        I/O behind bridge: 0000d000-0000dfff
        Memory behind bridge: dfe00000-dfefffff
        Capabilities: [50] Power Management version 3
        Capabilities: [58] Express Root Port (Slot-) IRQ 0
        Capabilities: [80] Message Signalled Interrupts: 64bit- Queue=0/0 Enable+
        Capabilities: [b0] #0d [0000]
        Capabilities: [b8] HyperTransport: MSI Mapping

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
        Flags: fast devsel
        Capabilities: [80] HyperTransport: Host or Secondary Interface

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
        Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
        Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
        Flags: fast devsel

00:1a.0 PCI bridge: ALi Corporation M5249 HTT to PCI Bridge (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 0000c000-0000cfff
        Memory behind bridge: dfd00000-dfdfffff
        Capabilities: [c0] HyperTransport: MSI Mapping

00:1c.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03) (prog-if 10 [OHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 8056
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 201
        Memory at dfcf8000 (32-bit, non-prefetchable) [size=4K]

00:1c.1 USB Controller: ALi Corporation USB 1.1 Controller (rev 03) (prog-if 10 [OHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 8056
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 217
        Memory at dfcf9000 (32-bit, non-prefetchable) [size=4K]

00:1c.2 USB Controller: ALi Corporation USB 1.1 Controller (rev 03) (prog-if 10 [OHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 8056
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 193
        Memory at dfcfa000 (32-bit, non-prefetchable) [size=4K]

00:1c.3 USB Controller: ALi Corporation USB 2.0 Controller (rev 01) (prog-if 20 [EHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 8056
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 209
        Memory at dfcfbc00 (32-bit, non-prefetchable) [size=256]
        Capabilities: [50] Power Management version 2
        Capabilities: [58] Debug port
        Capabilities: [78] Message Signalled Interrupts: 64bit- Queue=0/0 Enable-

00:1d.0 Audio device: ALi Corporation High Definition Audio/AC'97 Host Controller (rev 02)
        Subsystem: ASUSTeK Computer Inc. Unknown device 817f
        Flags: bus master, medium devsel, latency 64, IRQ 50
        Memory at dfcfc000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
        Capabilities: [60] Message Signalled Interrupts: 64bit- Queue=0/0 Enable-

00:1e.0 ISA bridge: ALi Corporation Unknown device 1575
        Subsystem: ALi Corporation Unknown device 1575
        Flags: bus master, medium devsel, latency 64

00:1e.1 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
        Subsystem: ASUSTeK Computer Inc. Unknown device 8056
        Flags: medium devsel

00:1f.0 IDE interface: ALi Corporation M5229 IDE (rev c8) (prog-if fa)
        Subsystem: ASUSTeK Computer Inc. Unknown device 8056
        Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 193
        I/O ports at ff00 [size=16]
        Capabilities: [60] Power Management version 2
        Capabilities: [80] Message Signalled Interrupts: 64bit- Queue=0/0 Enable-

01:14.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 14)
        Subsystem: ASUSTeK Computer Inc. Marvell 88E8001 Gigabit Ethernet Controller (Asus)
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 233
        Memory at dfdfc000 (32-bit, non-prefetchable) [size=16K]
        I/O ports at c800 [size=256]
        Expansion ROM at dfdc0000 [disabled] [size=128K]
        Capabilities: [48] Power Management version 2
        Capabilities: [50] Vital Product Data

02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 20)
        Subsystem: ASUSTeK Computer Inc. Marvell 88E8053 Gigabit Ethernet controller PCIe (Asus)
        Flags: bus master, fast devsel, latency 0, IRQ 225
        Memory at dfefc000 (64-bit, non-prefetchable) [size=16K]
        I/O ports at d800 [size=256]
        Expansion ROM at dfec0000 [disabled] [size=128K]
        Capabilities: [48] Power Management version 2
        Capabilities: [50] Vital Product Data
        Capabilities: [5c] Message Signalled Interrupts: 64bit+ Queue=0/1 Enable+
        Capabilities: [e0] Express Legacy Endpoint IRQ 0

03:00.0 VGA compatible controller: ATI Technologies Inc R480 [Radeon X850XT Platinum (PCIE)] (prog-if 00 [VGA])
        Subsystem: ATI Technologies Inc Unknown device 0b12
        Flags: bus master, fast devsel, latency 0, IRQ 11
        Memory at c0000000 (64-bit, prefetchable) [size=256M]
        Memory at dffe0000 (64-bit, non-prefetchable) [size=64K]
        I/O ports at e800 [size=256]
        Expansion ROM at dffc0000 [disabled] [size=128K]
        Capabilities: [50] Power Management version 2
        Capabilities: [58] Express Endpoint IRQ 0
        Capabilities: [80] Message Signalled Interrupts: 64bit+ Queue=0/0 Enable-

03:00.1 Display controller: ATI Technologies Inc R480 [Radeon X850XT Platinum (PCIE)] (Secondary)
        Subsystem: ATI Technologies Inc Unknown device 0b13
        Flags: bus master, fast devsel, latency 0
        Memory at dfff0000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: [50] Power Management version 2
        Capabilities: [58] Express Endpoint IRQ 0

```

and loaded modules:

```

root@pytong:~# lsmod
Module                  Size  Used by
binfmt_misc            13448  1 
cpufreq_userspace       5408  0 
cpufreq_stats           7744  0 
freq_table              6048  1 cpufreq_stats
cpufreq_powersave       2944  0 
cpufreq_ondemand        8876  0 
cpufreq_conservative     8712  0 
video                  17540  0 
tc1100_wmi              8324  0 
sbs                    16804  0 
sony_acpi               6412  0 
pcc_acpi               14080  0 
i2c_ec                  6272  1 sbs
hotkey                 11556  0 
dev_acpi               12292  0 
button                  7952  0 
battery                11652  0 
container               5632  0 
ac                      6788  0 
asus_acpi              17688  0 
ipv6                  272288  10 
af_packet              24584  2 
parport_pc             37796  0 
lp                     12964  0 
parport                39496  2 parport_pc,lp
joydev                 11200  0 
tsdev                   9152  0 
snd_hda_intel          20116  1 
snd_hda_codec         164608  1 snd_hda_intel
psmouse                41352  0 
snd_pcm_oss            47360  0 
snd_mixer_oss          19584  1 snd_pcm_oss
skge                   40336  0 
serio_raw               8452  0 
usbhid                 45152  0 
sk98lin               191700  0 
sky2                   43012  0 
snd_pcm                84612  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_timer              25348  1 snd_pcm
ati_agp                10636  0 
agpgart                34888  1 ati_agp
i2c_ali1535             7940  0 
i2c_ali15x3             8708  0 
i2c_core               23424  3 i2c_ec,i2c_ali1535,i2c_ali15x3
floppy                 63044  0 
evdev                  11392  2 
pcspkr                  4352  0 
snd                    58372  8 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              11232  1 snd
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
shpchp                 42144  0 
pci_hotplug            32828  1 shpchp
ext3                  142728  1 
jbd                    62228  1 ext3
ehci_hcd               34696  0 
ohci_hcd               22532  0 
usbcore               134912  4 usbhid,ehci_hcd,ohci_hcd
ide_generic             2432  0 
ide_cd                 33696  0 
cdrom                  38944  1 ide_cd
ide_disk               18560  3 
generic                 5764  0 
alim15x3               13324  0 [permanent]
thermal                15624  0 
processor              31560  1 thermal
fan                     6020  0 
fbcon                  41504  0 
tileblit                3840  1 fbcon
font                    9344  1 fbcon
bitblit                 7168  1 fbcon
softcursor              3328  1 bitblit
vesafb                  9244  0 
capability              5896  0 
commoncap               8704  1 capability

```

There is no sound at all. No matter the output (analog jack or digital SPDIF).

I have no idea what to do. Thanks for any help :)

---

