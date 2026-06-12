---
title: "Compiled driver for WUSB600N, but it won't load on start-up or on inserting"
date: 2011-01-04
forum: Networking &amp; Wireless
---

### Post by themusicalduck on 2011-01-04
I managed to find an older version of the rt3572 driver to compile to get this dongle to work fine, and it did. After that I added "module rt3572sta" (or whatever it is, not on Ubuntu to check now) to the end of /etc/modules.

However, when I boot up Ubuntu, most of the time the driver won't load. If I run 'modprobe rt3572sta' from the terminal, I get this message -
```
sudo modprobe rt3572sta
FATAL: Error inserting rt3572sta (/lib/modules/2.6.36-2.dmz.5-liquorix-686/kernel/drivers/net/wireless/rt3572sta.ko): Device or resource busy

```
Is it something to do with using multiple OS? Say the dongle is being flagged and locked as in use? I had a similar problem with a USB hard drive, but not sure why it would happen with a wifi dongle.

I'm on 10.10.

---

### Post by themusicalduck on 2011-01-04
bump

---

### Post by PatchesTheCaveman on 2011-01-04
Hi themusicalduck.  Happy New Year!

Please run the following commands and copy/paste the output:
```
lspci -vnn
lsmod
```

Also, please wait at least a day before you bump your post.  I would actually have helped you much earlier had you waited, as I start with the oldest new post and work my way up.

---

### Post by themusicalduck on 2011-01-04
Here is lspci -

```
00:00.0 Memory controller [0580]: nVidia Corporation CK804 Memory Controller [10de:005e] (rev a3)
	Subsystem: Giga-byte Technology GA-K8N Ultra-9 Mainboard [1458:5000]
	Flags: bus master, 66MHz, fast devsel, latency 0
	Capabilities: <access denied>

00:01.0 ISA bridge [0601]: nVidia Corporation CK804 ISA Bridge [10de:0050] (rev a3)
	Subsystem: Giga-byte Technology GA-K8N Ultra-9 Mainboard [1458:0c11]
	Flags: bus master, 66MHz, fast devsel, latency 0

00:01.1 SMBus [0c05]: nVidia Corporation CK804 SMBus [10de:0052] (rev a2)
	Subsystem: Giga-byte Technology GA-K8N Ultra-9 Mainboard [1458:0c11]
	Flags: 66MHz, fast devsel, IRQ 10
	I/O ports at e400 [size=32]
	I/O ports at 1c00 [size=64]
	I/O ports at 1c40 [size=64]
	Capabilities: <access denied>
	Kernel driver in use: nForce2_smbus
	Kernel modules: i2c-nforce2

00:02.0 USB Controller [0c03]: nVidia Corporation CK804 USB Controller [10de:005a] (rev a2) (prog-if 10 [OHCI])
	Subsystem: Giga-byte Technology GA-K8N Ultra-9 Mainboard [1458:5004]
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
	Memory at f6002000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: ohci_hcd
	Kernel modules: ohci-hcd

00:02.1 USB Controller [0c03]: nVidia Corporation CK804 USB Controller [10de:005b] (rev a3) (prog-if 20 [EHCI])
	Subsystem: Giga-byte Technology GA-K8N Ultra-9 Mainboard [1458:5004]
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
	Memory at c0100000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd

00:04.0 Multimedia audio controller [0401]: nVidia Corporation CK804 AC'97 Audio Controller [10de:0059] (rev a2)
	Subsystem: Giga-byte Technology Device [1458:ae01]
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
	I/O ports at b400 [size=256]
	I/O ports at b800 [size=256]
	Memory at f6005000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: Intel ICH
	Kernel modules: snd-intel8x0

00:06.0 IDE interface [0101]: nVidia Corporation CK804 IDE [10de:0053] (rev a2) (prog-if 8a [Master SecP PriP])
	Subsystem: Giga-byte Technology GA-K8N Ultra-9 Mainboard [1458:5002]
	Flags: bus master, 66MHz, fast devsel, latency 0
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [size=1]
	I/O ports at f000 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: pata_amd
	Kernel modules: pata_amd

00:07.0 IDE interface [0101]: nVidia Corporation CK804 Serial ATA Controller [10de:0054] (rev a3) (prog-if 85 [Master SecO PriO])
	Subsystem: Giga-byte Technology GA-K8N Ultra-9 Mainboard [1458:b003]
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
	I/O ports at 09f0 [size=8]
	I/O ports at 0bf0 [size=4]
	I/O ports at 0970 [size=8]
	I/O ports at 0b70 [size=4]
	I/O ports at cc00 [size=16]
	Memory at f6000000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: sata_nv
	Kernel modules: sata_nv

00:08.0 IDE interface [0101]: nVidia Corporation CK804 Serial ATA Controller [10de:0055] (rev a3) (prog-if 85 [Master SecO PriO])
	Subsystem: Giga-byte Technology GA-K8N Ultra-9 Mainboard [1458:b003]
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
	I/O ports at 09e0 [size=8]
	I/O ports at 0be0 [size=4]
	I/O ports at 0960 [size=8]
	I/O ports at 0b60 [size=4]
	I/O ports at e000 [size=16]
	Memory at f6001000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: sata_nv
	Kernel modules: sata_nv

00:09.0 PCI bridge [0604]: nVidia Corporation CK804 PCI Bridge [10de:005c] (rev a2) (prog-if 01 [Subtractive decode])
	Flags: bus master, 66MHz, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
	I/O behind bridge: 00008000-00009fff
	Memory behind bridge: f4000000-f5ffffff
	Prefetchable memory behind bridge: c0000000-c00fffff

00:0a.0 Bridge [0680]: nVidia Corporation CK804 Ethernet Controller [10de:0057] (rev a3)
	Subsystem: Giga-byte Technology GA-K8N Ultra-9 Mainboard [1458:e000]
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
	Memory at f6003000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at e800 [size=8]
	Capabilities: <access denied>
	Kernel driver in use: forcedeth
	Kernel modules: forcedeth

00:0b.0 PCI bridge [0604]: nVidia Corporation CK804 PCIE Bridge [10de:005d] (rev a3) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 00005000-00005fff
	Capabilities: <access denied>
	Kernel modules: shpchp

00:0c.0 PCI bridge [0604]: nVidia Corporation CK804 PCIE Bridge [10de:005d] (rev a3) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 00007000-00007fff
	Capabilities: <access denied>
	Kernel modules: shpchp

00:0d.0 PCI bridge [0604]: nVidia Corporation CK804 PCIE Bridge [10de:005d] (rev a3) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	I/O behind bridge: 00006000-00006fff
	Capabilities: <access denied>
	Kernel modules: shpchp

00:0e.0 PCI bridge [0604]: nVidia Corporation CK804 PCIE Bridge [10de:005d] (rev a3) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
	I/O behind bridge: 0000a000-0000afff
	Memory behind bridge: f0000000-f3ffffff
	Prefetchable memory behind bridge: 00000000e0000000-00000000efffffff
	Capabilities: <access denied>
	Kernel modules: shpchp

00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
	Flags: fast devsel
	Capabilities: <access denied>

00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
	Flags: fast devsel

00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
	Flags: fast devsel

00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
	Flags: fast devsel
	Kernel driver in use: k8temp
	Kernel modules: k8temp

01:07.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
	Subsystem: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139]
	Flags: bus master, medium devsel, latency 64, IRQ 19
	I/O ports at 8000 [size=256]
	Memory at f5001000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: 8139too
	Kernel modules: 8139too

01:08.0 Multimedia audio controller [0401]: VIA Technologies Inc. VT1720/24 [Envy24PT/HT] PCI Multi-Channel Audio Controller [1412:1724] (rev 01)
	Subsystem: VIA Technologies Inc. Device [1412:3632]
	Flags: bus master, medium devsel, latency 32, IRQ 16
	I/O ports at 8400 [size=32]
	I/O ports at 8800 [size=128]
	Capabilities: <access denied>
	Kernel driver in use: ICE1724
	Kernel modules: snd-ice1724

01:09.0 RAID bus controller [0104]: Silicon Image, Inc. SiI 3114 [SATALink/SATARaid] Serial ATA Controller [1095:3114] (rev 02)
	Subsystem: Giga-byte Technology Device [1458:b004]
	Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 17
	I/O ports at 8c00 [size=8]
	I/O ports at 9000 [size=4]
	I/O ports at 9400 [size=8]
	I/O ports at 9800 [size=4]
	I/O ports at 9c00 [size=16]
	Memory at f5000000 (32-bit, non-prefetchable) [size=1K]
	[virtual] Expansion ROM at c0000000 [disabled] [size=512K]
	Capabilities: <access denied>
	Kernel driver in use: sata_sil
	Kernel modules: sata_sil

05:00.0 VGA compatible controller [0300]: nVidia Corporation GT200 [GeForce GTX 260] [10de:05e2] (rev a1) (prog-if 00 [VGA controller])
	Subsystem: ZOTAC International (MCO) Ltd. Device [19da:1109]
	Flags: bus master, fast devsel, latency 0, IRQ 18
	Memory at f2000000 (32-bit, non-prefetchable) [size=16M]
	Memory at e0000000 (64-bit, prefetchable) [size=256M]
	Memory at f0000000 (64-bit, non-prefetchable) [size=32M]
	I/O ports at a000 [size=128]
	[virtual] Expansion ROM at f3000000 [disabled] [size=512K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidiafb, nouveau, nvidia-current

```

and lsmod -

```
Module                  Size  Used by
nls_utf8                1037  1 
udf                    81129  1 
crc_itu_t               1375  1 udf
binfmt_misc             6277  1 
vboxnetadp              6398  0 
vboxnetflt             18993  0 
vboxdrv               213096  2 vboxnetadp,vboxnetflt
ipv6                  272359  22 
nvidia               9380267  52 
ext3                  118557  1 
jbd                    46200  1 ext3
fuse                   63839  5 
snd_intel8x0           24191  2 
snd_ice1724            99909  2 
snd_ice17xx_ak4xxx      2519  1 snd_ice1724
snd_ak4xxx_adda         7716  2 snd_ice1724,snd_ice17xx_ak4xxx
snd_ac97_codec         95516  2 snd_ice1724,snd_intel8x0
snd_ak4114              7008  1 snd_ice1724
snd_pt2258              2755  1 snd_ice1724
snd_i2c                 4173  2 snd_ice1724,snd_pt2258
ac97_bus                 942  1 snd_ac97_codec
snd_ak4113              6607  1 snd_ice1724
snd_pcm_oss            34233  0 
snd_mixer_oss          13916  1 snd_pcm_oss
joydev                  8455  0 
snd_pcm                68824  6 snd_ice1724,snd_intel8x0,snd_ak4114,snd_ac97_codec,snd_ak4113,snd_pcm_oss
snd_seq_dummy           1342  0 
snd_seq_oss            26340  0 
snd_seq_midi            4684  0 
snd_rawmidi            18738  2 snd_ice1724,snd_seq_midi
agpgart                30383  1 nvidia
snd_seq_midi_event      5879  2 snd_seq_oss,snd_seq_midi
snd_seq                46815  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
usbhid                 35215  0 
snd_timer              18151  2 snd_pcm,snd_seq
i2c_nforce2             4725  0 
ppdev                   5584  0 
rtc_cmos                8119  0 
parport_pc             29615  1 
rtc_core               13575  1 rtc_cmos
rtc_lib                 2221  1 rtc_core
hid                    67029  1 usbhid
snd_seq_device          5640  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
i2c_core               21325  2 nvidia,i2c_nforce2
snd                    54041  25 snd_ice1724,snd_intel8x0,snd_ak4xxx_adda,snd_ak4114,snd_ac97_codec,snd_pt2258,snd_i2c,snd_ak4113,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
processor              25962  0 
shpchp                 24685  0 
pci_hotplug            25430  1 shpchp
evdev                   7218  11 
k8temp                  3023  0 
rt2870sta             404830  0 
soundcore               6602  1 snd
snd_page_alloc          7176  2 snd_intel8x0,snd_pcm
crc_ccitt               1343  1 rt2870sta
lp                      7789  0 
parport                31193  3 ppdev,parport_pc,lp
ext4                  314482  1 
mbcache                 5934  2 ext3,ext4
jbd2                   70829  1 ext4
crc16                   1343  1 ext4
sr_mod                 14451  1 
cdrom                  34262  1 sr_mod
sg                     19843  0 
sd_mod                 31248  6 
ata_generic             2523  0 
ohci_hcd               21636  0 
pata_acpi               2487  0 
pata_amd                8450  1 
ssb                    43520  1 ohci_hcd
sata_nv                18567  4 
sata_sil                6645  0 
mmc_core               64997  1 ssb
libata                169620  5 ata_generic,pata_acpi,sata_sil,sata_nv,pata_amd
8139too                18462  0 
ehci_hcd               34634  0 
pcmcia                 35527  1 ssb
floppy                 52147  0 
thermal                10456  0 
mii                     4321  1 8139too
forcedeth              47857  0 
button                  4494  0 
pcmcia_core            13470  1 pcmcia
```

> Also, please wait at least a day before you bump your post. I would actually have helped you much earlier had you waited, as I start with the oldest new post and work my way up.

I appreciate that. I usually figure if it's off the front page and a few hours old I could bump it, then it's likely to be seen by different people. Seeing as it's a different timeframe as it were (whereas in 24 hours, it's just the same time as yesterday and may be seen by some of the same people).

Thanks for getting to my post though.

---

### Post by themusicalduck on 2011-01-04
I found the problem!

I ran dmesg after plugging in the dongle and it gave an error about 'rt2870' being already registered, which is the wrong driver for it to use.

It turns out I had 'rt2870sta' listed in the file /etc/modules from when I installed the last dongle I was using and that was interfering with the driver for the new one.

Thanks for the help anyway.

---

### Post by PatchesTheCaveman on 2011-01-04
Did you follow this process to modify the rt3572sta driver so it works properly on Ubuntu:
[http://ubuntuforums.org/showpost.php?p=10311422&postcount=39](http://ubuntuforums.org/showpost.php?p=10311422&postcount=39)

It might not work properly without those modifications.

---

### Post by themusicalduck on 2011-01-04
Yeah, I added the tweaks before compiling and everything seems to be working fine so far. Thanks.

---

