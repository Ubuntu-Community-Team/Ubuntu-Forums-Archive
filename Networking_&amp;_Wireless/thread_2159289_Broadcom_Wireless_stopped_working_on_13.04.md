---
title: "Broadcom Wireless stopped working on 13.04"
date: 2013-07-02
forum: Networking &amp; Wireless
---

### Post by tm2383 on 2013-07-02
Hi Folks,
I installed Ubuntu 13.04 64 bit yesterday with no problems. Everything was working fine, including wirless, which was detected during installation. Today it is not working. Despite several shut downs and restarts, it is still not working. The wireless icon does not list any wireless networks as being available. It is as if there is no wireless card installed. 
Software and updates says that proprietary driver is being used : Using Broadcom 802.11 linux STA wirless driver source from bcmwl-kernel-source-(ROPRIETARY)

I have provided the oupout below from some commands asked for in other posts Apologies if they are not needed!!

Any help would be appreciated.

Thanks,
Tim


lspci output:
```
tim@tim-Aspire-5551:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS880 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (int gfx)
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 1)
00:11.0 SATA controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode]
00:12.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: Advanced Micro Devices [AMD] nee ATI SBx00 SMBus Controller (rev 41)
00:14.1 IDE interface: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 IDE Controller (rev 40)
00:14.2 Audio device: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
00:14.4 PCI bridge: Advanced Micro Devices [AMD] nee ATI SBx00 PCI to PCI Bridge (rev 40)
00:14.5 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:05.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RS880M [Mobility Radeon HD 4225/4250]
01:05.1 Audio device: Advanced Micro Devices [AMD] nee ATI RS880 HDMI Audio [Radeon HD 4200 Series]
02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM57780 Gigabit Ethernet PCIe (rev 01)

```

iwconfig:
```
eth0      no wireless extensions.

lo        no wireless extensions.

```

iwgetid is blank

lspci -nn | grep 0280
```
 Broadcom Corporation BCM43225 802.11b/g/n [14e4:4357] (rev 01)

```

lsmod

```

Module                  Size  Used by
parport_pc             32866  0 
ppdev                  17106  0 
bnep                   18258  2 
rfcomm                 47863  0 
bluetooth             251354  10 bnep,rfcomm
radeon                965140  3 
ttm                    88251  1 radeon
uvcvideo               82296  0 
snd_hda_codec_hdmi     37407  1 
drm_kms_helper         49082  1 radeon
snd_hda_codec_realtek    46511  1 
drm                   291527  5 ttm,drm_kms_helper,radeon
snd_hda_intel          44665  10 
videobuf2_vmalloc      13056  1 uvcvideo
snd_hda_codec         190048  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
videobuf2_memops       13202  1 videobuf2_vmalloc
i2c_algo_bit           13564  1 radeon
videobuf2_core         40785  1 uvcvideo
kvm_amd                60389  0 
snd_hwdep              13613  1 snd_hda_codec
videodev              131329  2 uvcvideo,videobuf2_core
kvm                   452835  1 kvm_amd
snd_pcm               102477  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_seq_midi           13324  0 
snd_page_alloc         18798  2 snd_pcm,snd_hda_intel
edac_core              63023  0 
joydev                 17613  0 
shpchp                 37201  0 
snd_seq_midi_event     14899  1 snd_seq_midi
acer_wmi               32858  0 
sparse_keymap          13890  1 acer_wmi
snd_rawmidi            30417  1 snd_seq_midi
psmouse                97838  0 
edac_mce_amd           22792  0 
snd_seq                61930  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
sp5100_tco             13870  0 
k10temp                13173  0 
snd_timer              29989  2 snd_pcm,snd_seq
snd                    69533  30 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
serio_raw              13215  0 
soundcore              12680  1 snd
i2c_piix4              13459  0 
microcode              22923  0 
wmi                    19256  1 acer_wmi
lp                     17799  0 
mac_hid                13253  0 
video                  19467  1 acer_wmi
parport                46562  3 lp,ppdev,parport_pc
tg3                   165632  0 
pata_acpi              13038  0 
ptp                    18668  1 tg3
ahci                   30063  3 
pps_core               14080  1 ptp
libahci                32088  1 ahci
pata_atiixp            13242  0 
tim@tim-Aspire-5551:~$ 

```

[COLOR=#000000][FONT=Lucida Grande][B]lspci -vnn
```
00:00.0 Host bridge [0600]: Advanced Micro Devices [AMD] RS880 Host Bridge [1022:9601]
    Subsystem: Acer Incorporated [ALI] Device [1025:036e]
    Flags: bus master, 66MHz, medium devsel, latency 0
    Capabilities: <access denied>

00:01.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (int gfx) [1022:9602] (prog-if 00 [Normal decode])
    Flags: bus master, 66MHz, medium devsel, latency 64
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 00006000-00006fff
    Memory behind bridge: d2100000-d22fffff
    Prefetchable memory behind bridge: 00000000c0000000-00000000cfffffff
    Capabilities: <access denied>

00:04.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 0) [1022:9604] (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=07, sec-latency=0
    I/O behind bridge: 00002000-00005fff
    Memory behind bridge: d1100000-d20fffff
    Prefetchable memory behind bridge: 00000000d0000000-00000000d0ffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport

00:05.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 1) [1022:9605] (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=08, subordinate=08, sec-latency=0
    Memory behind bridge: d1000000-d10fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport

00:11.0 SATA controller [0106]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode] [1002:4391] (prog-if 01 [AHCI 1.0])
    Subsystem: Acer Incorporated [ALI] Device [1025:036e]
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 42
    I/O ports at 7038 [size=8]
    I/O ports at 704c [size=4]
    I/O ports at 7030 [size=8]
    I/O ports at 7048 [size=4]
    I/O ports at 7010 [size=16]
    Memory at d2307000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ahci

00:12.0 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397] (prog-if 10 [OHCI])
    Subsystem: Acer Incorporated [ALI] Device [1025:036e]
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
    Memory at d2306000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:12.2 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396] (prog-if 20 [EHCI])
    Subsystem: Acer Incorporated [ALI] Device [1025:036e]
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
    Memory at d2307500 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci-pci

00:13.0 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397] (prog-if 10 [OHCI])
    Subsystem: Acer Incorporated [ALI] Device [1025:036e]
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
    Memory at d2305000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:13.2 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396] (prog-if 20 [EHCI])
    Subsystem: Acer Incorporated [ALI] Device [1025:036e]
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
    Memory at d2307400 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci-pci

00:14.0 SMBus [0c05]: Advanced Micro Devices [AMD] nee ATI SBx00 SMBus Controller [1002:4385] (rev 41)
    Subsystem: Acer Incorporated [ALI] Device [1025:036e]
    Flags: 66MHz, medium devsel
    Kernel driver in use: piix4_smbus

00:14.1 IDE interface [0101]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 IDE Controller [1002:439c] (rev 40) (prog-if 8a [Master SecP PriP])
    Subsystem: Acer Incorporated [ALI] Device [1025:036e]
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at 7000 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: pata_atiixp

00:14.2 Audio device [0403]: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA) [1002:4383] (rev 40)
    Subsystem: Acer Incorporated [ALI] Device [1025:036e]
    Flags: bus master, slow devsel, latency 64, IRQ 16
    Memory at d2300000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel

00:14.3 ISA bridge [0601]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 LPC host controller [1002:439d] (rev 40)
    Subsystem: Acer Incorporated [ALI] Device [1025:036e]
    Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge [0604]: Advanced Micro Devices [AMD] nee ATI SBx00 PCI to PCI Bridge [1002:4384] (rev 40) (prog-if 01 [Subtractive decode])
    Flags: bus master, 66MHz, medium devsel, latency 64
    Bus: primary=00, secondary=09, subordinate=09, sec-latency=64

00:14.5 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI2 Controller [1002:4399] (prog-if 10 [OHCI])
    Subsystem: Acer Incorporated [ALI] Device [1025:036e]
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
    Memory at d2304000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration [1022:1200]
    Flags: fast devsel
    Capabilities: <access denied>

00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor Address Map [1022:1201]
    Flags: fast devsel

00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller [1022:1202]
    Flags: fast devsel

00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control [1022:1203]
    Flags: fast devsel
    Capabilities: <access denied>
    Kernel driver in use: k10temp

00:18.4 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor Link Control [1022:1204]
    Flags: fast devsel

01:05.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI RS880M [Mobility Radeon HD 4225/4250] [1002:9712] (prog-if 00 [VGA controller])
    Subsystem: Acer Incorporated [ALI] Device [1025:036e]
    Flags: bus master, fast devsel, latency 0, IRQ 18
    Memory at c0000000 (32-bit, prefetchable) [size=256M]
    I/O ports at 6000 [size=256]
    Memory at d2200000 (32-bit, non-prefetchable) [size=64K]
    Memory at d2100000 (32-bit, non-prefetchable) [size=1M]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: radeon

01:05.1 Audio device [0403]: Advanced Micro Devices [AMD] nee ATI RS880 HDMI Audio [Radeon HD 4200 Series] [1002:970f]
    Subsystem: Acer Incorporated [ALI] Device [1025:036e]
    Flags: bus master, fast devsel, latency 0, IRQ 19
    Memory at d2210000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel

02:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM57780 Gigabit Ethernet PCIe [14e4:1692] (rev 01)
    Subsystem: Acer Incorporated [ALI] Device [1025:036e]
    Flags: bus master, fast devsel, latency 0, IRQ 43
    Memory at d1100000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: tg3

08:00.0 Network controller [0280]: Broadcom Corporation BCM43225 802.11b/g/n [14e4:4357] (rev 01)
    Subsystem: Foxconn International, Inc. T77H103.00 Wireless Half-size Mini PCIe Card [105b:e021]
    Flags: bus master, fast devsel, latency 0, IRQ 5
    Memory at d1000000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>

```

lsusb
```
Bus 002 Device 002: ID 0402:9665 ALi Corp. Gateway Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

lsmod

```
Module                  Size  Used by
parport_pc             32866  0 
ppdev                  17106  0 
bnep                   18258  2 
rfcomm                 47863  0 
bluetooth             251354  10 bnep,rfcomm
radeon                965140  3 
ttm                    88251  1 radeon
uvcvideo               82296  0 
snd_hda_codec_hdmi     37407  1 
drm_kms_helper         49082  1 radeon
snd_hda_codec_realtek    46511  1 
drm                   291527  5 ttm,drm_kms_helper,radeon
snd_hda_intel          44665  10 
videobuf2_vmalloc      13056  1 uvcvideo
snd_hda_codec         190048  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
videobuf2_memops       13202  1 videobuf2_vmalloc
i2c_algo_bit           13564  1 radeon
videobuf2_core         40785  1 uvcvideo
kvm_amd                60389  0 
snd_hwdep              13613  1 snd_hda_codec
videodev              131329  2 uvcvideo,videobuf2_core
kvm                   452835  1 kvm_amd
snd_pcm               102477  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_seq_midi           13324  0 
snd_page_alloc         18798  2 snd_pcm,snd_hda_intel
edac_core              63023  0 
joydev                 17613  0 
shpchp                 37201  0 
snd_seq_midi_event     14899  1 snd_seq_midi
acer_wmi               32858  0 
sparse_keymap          13890  1 acer_wmi
snd_rawmidi            30417  1 snd_seq_midi
psmouse                97838  0 
edac_mce_amd           22792  0 
snd_seq                61930  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
sp5100_tco             13870  0 
k10temp                13173  0 
snd_timer              29989  2 snd_pcm,snd_seq
snd                    69533  30 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
serio_raw              13215  0 

```

[/B][/FONT][/COLOR]
route -n

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

```

rfkill list

```
0: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```

---

### Post by Hadaka on 2013-07-02
Hi, give this a try..
```
echo "blacklist acer_wmi" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
boot
then do..
```
sudo modprobe -rf wl
sudo modprobe wl
```
is it alive?

---

### Post by tm2383 on 2013-07-03
Thanks for the reply. In the end, I opted for a reinstall. Everything seems to be working perfectly now, so hopefully, that's the end of the problem. Thanks again for taking the time to reply.

Tim

---

### Post by Hadaka on 2013-07-03
Great ! glad its working.
please mark your thread solved.
thanks.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

