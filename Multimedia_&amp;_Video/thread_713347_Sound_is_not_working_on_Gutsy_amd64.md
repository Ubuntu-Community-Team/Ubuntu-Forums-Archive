---
title: "Sound is not working on Gutsy amd64"
date: 2008-03-02
forum: Multimedia &amp; Video
---

### Post by edgarjs on 2008-03-02
Hello, I've just installed Ubuntu 7.10 on my amd pc. It works all fine except for the sound.

I've tried some steps and guides about trying to fix it but no one works... even, when I installed alsa utils, lib, and driver (1.0.16) it messed out more, now I cannot even enter the volume control because it says "No volume control GStreamer plugins and/or devices found".

lspci -v
```

00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a4)
        Subsystem: ASUSTeK Computer Inc. A8N-E Mainboard
        Flags: bus master, 66MHz, fast devsel, latency 0
        Capabilities: <access denied>

00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev f1)
        Subsystem: ASUSTeK Computer Inc. K8N4-E or A8N-E Mainboard
        Flags: bus master, 66MHz, fast devsel, latency 0

00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
        Subsystem: ASUSTeK Computer Inc. K8N4-E or A8N-E Mainboard
        Flags: 66MHz, fast devsel, IRQ 3
        I/O ports at fc00 [size=32]
        I/O ports at 4c00 [size=64]
        I/O ports at 4c40 [size=64]
        Capabilities: <access denied>

00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2) (prog-if 10 [OHCI])
        Subsystem: ASUSTeK Computer Inc. K8N4-E or A8N-E Mainboard
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
        Memory at fe02f000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a4) (prog-if 20 [EHCI])
        Subsystem: ASUSTeK Computer Inc. K8N4-E or A8N-E Mainboard
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
        Memory at fe02e000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f3) (prog-if 8a [Master SecP PriP])
        Subsystem: ASUSTeK Computer Inc. K8N4-E or A8N-E Mainboard
        Flags: bus master, 66MHz, fast devsel, latency 0
        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
        I/O ports at e800 [size=16]
        Capabilities: <access denied>

00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3) (prog-if 85 [Master SecO PriO])
        Subsystem: ASUSTeK Computer Inc. A8N-E Mainboard
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
        I/O ports at 09f0 [size=8]
        I/O ports at 0bf0 [size=4]
        I/O ports at 0970 [size=8]
        I/O ports at 0b70 [size=4]
        I/O ports at d400 [size=16]
        Memory at fe02c000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3) (prog-if 85 [Master SecO PriO])
        Subsystem: ASUSTeK Computer Inc. K8N4-E or A8N-E Mainboard
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
        I/O ports at 09e0 [size=8]
        I/O ports at 0be0 [size=4]
        I/O ports at 0960 [size=8]
        I/O ports at 0b60 [size=4]
        I/O ports at c000 [size=16]
        Memory at fe02b000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev f2) (prog-if 01 [Subtractive decode])
        Flags: bus master, 66MHz, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=128
        I/O behind bridge: 0000a000-0000afff
        Memory behind bridge: fdf00000-fdffffff

00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev f3)
        Subsystem: ASUSTeK Computer Inc. Unknown device 812a
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
        Memory at fe02a000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at bc00 [size=8]
        Capabilities: <access denied>

00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        Capabilities: <access denied>

00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        Capabilities: <access denied>

00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
        Capabilities: <access denied>

00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
        I/O behind bridge: 00009000-00009fff
        Memory behind bridge: f8000000-fbffffff
        Prefetchable memory behind bridge: 00000000c0000000-00000000dfffffff
        Capabilities: <access denied>

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
        Flags: fast devsel
        Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
        Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
        Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
        Flags: fast devsel
        Capabilities: <access denied>

01:01.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev c0) (prog-if 10 [OHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 81fe
        Flags: bus master, medium devsel, latency 32, IRQ 17
        Memory at fdfff000 (32-bit, non-prefetchable) [size=2K]
        I/O ports at ac00 [size=128]
        Capabilities: <access denied>

05:00.0 VGA compatible controller: nVidia Corporation GeForce 8500 GT (rev a1) (prog-if 00 [VGA])
        Flags: bus master, fast devsel, latency 0, IRQ 18
        Memory at fa000000 (32-bit, non-prefetchable) [size=16M]
        Memory at c0000000 (64-bit, prefetchable) [size=512M]
        Memory at f8000000 (64-bit, non-prefetchable) [size=32M]
        I/O ports at 9c00 [size=128]
        [virtual] Expansion ROM at fbfe0000 [disabled] [size=128K]
        Capabilities: <access denied>


```


lsmod:
```

Module                  Size  Used by
ipv6                  317192  10 
af_packet              28172  2 
rfcomm                 47656  2 
l2cap                  28672  11 rfcomm
bluetooth              63876  4 rfcomm,l2cap
ppdev                  11272  0 
powernow_k8            16608  1 
cpufreq_conservative     9608  0 
cpufreq_ondemand       10896  1 
cpufreq_userspace       6048  0 
cpufreq_powersave       3072  0 
cpufreq_stats           8160  0 
freq_table              6464  3 powernow_k8,cpufreq_ondemand,cpufreq_stats
sbs                    21520  0 
container               6400  0 
video                  21140  0 
ac                      7304  0 
dock                   12264  0 
button                 10400  0 
battery                12424  0 
sbp2                   27144  0 
lp                     15048  0 
parport_pc             41896  1 
nvidia               7013492  34 
parport                44172  3 ppdev,lp,parport_pc
psmouse                45596  0 
k8temp                  7680  0 
pcspkr                  4608  0 
serio_raw               9092  0 
shpchp                 38300  0 
pci_hotplug            36612  1 shpchp
i2c_nforce2             7808  0 
i2c_core               30208  2 nvidia,i2c_nforce2
evdev                  13056  3 
ext3                  146576  1 
jbd                    69360  1 ext3
mbcache                11272  1 ext3
sg                     41384  0 
sd_mod                 32512  4 
ide_cd                 35488  0 
cdrom                  41768  1 ide_cd
sata_nv                24068  3 
amd74xx                17328  0 [permanent]
ide_core              141200  2 ide_cd,amd74xx
ohci1394               38984  0 
ieee1394              109528  2 sbp2,ohci1394
ehci_hcd               40076  0 
forcedeth              55048  0 
ata_generic             9988  0 
libata                138928  2 sata_nv,ata_generic
scsi_mod              172856  4 sbp2,sg,sd_mod,libata
ohci_hcd               25092  0 
usbcore               161584  3 ehci_hcd,ohci_hcd
thermal                16528  0 
processor              36232  2 powernow_k8,thermal
fan                     6920  0 
fuse                   52528  3 
apparmor               47008  0 
commoncap               9472  1 apparmor

```

Any help will be great, thanks in advance.

---

### Post by edgarjs on 2008-03-03
Ok, it's solved now: here's the link (spanish):

[http://www.ubuntu-es.org/index.php?q=node/70976](http://www.ubuntu-es.org/index.php?q=node/70976)

It was a problem about alsa and the mother board m2n e sli from Asus

---

