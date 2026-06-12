---
title: "Pinnacle PCTV Hybrid Pro Card"
date: 2009-05-01
forum: Multimedia Software
---

### Post by Robertsche on 2009-05-01
Hello, Im a new user of Ubuntu, I have installed Ubuntu 9.04, i want to install my Tv card (Pinnacle PCTV Hybrid Pro Card) and work it with Kaffeine. I hopeanyone can help me. Here I few commands that i have do 
robert@robert-laptop:~$ lsmod
Module                  Size  Used by
ndiswrapper           193436  0 
nls_iso8859_1          12032  1 
nls_cp437              13696  1 
vfat                   18816  1 
fat                    58272  1 vfat
usb_storage            82880  1 
isofs                  39844  1 
udf                    87716  0 
crc_itu_t              10112  1 udf
binfmt_misc            16776  1 
bridge                 56340  0 
stp                    10500  1 bridge
bnep                   20224  2 
input_polldev          11912  0 
video                  25360  0 
output                 11008  1 video
lp                     17156  0 
tuner_simple           22544  1 
tuner_types            22400  1 tuner_simple
tuner                  32836  0 
cx8802                 24068  0 
cx88_alsa              18824  1 
cx8800                 38148  0 
cx88xx                 79272  3 cx8802,cx88_alsa,cx8800
ir_common              52228  1 cx88xx
i2c_algo_bit           14084  1 cx88xx
videodev               41600  3 tuner,cx8800,cx88xx
v4l1_compat            21764  1 videodev
compat_ioctl32          9344  1 cx8800
videobuf_dvb           15236  2 cx8802,cx88xx
dvb_core               92032  1 videobuf_dvb
tveeprom               20100  1 cx88xx
v4l2_common            20992  2 tuner,cx8800
videobuf_dma_sg        20484  4 cx8802,cx88_alsa,cx8800,cx88xx
videobuf_core          26500  5 cx8802,cx8800,cx88xx,videobuf_dvb,videobuf_dma_sg
btcx_risc              13064  4 cx8802,cx88_alsa,cx8800,cx88xx
pcmcia                 44748  0 
ppdev                  15620  0 
snd_intel8x0           37532  3 
snd_ac97_codec        112292  1 snd_intel8x0
ac97_bus                9856  1 snd_ac97_codec
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82948  4 cx88_alsa,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
yenta_socket           32396  2 
rsrc_nonstatic         19328  1 yenta_socket
pcmcia_core            43540  3 pcmcia,yenta_socket,rsrc_nonstatic
snd                    62628  19 cx88_alsa,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
pcspkr                 10496  0 
snd_page_alloc         16904  2 snd_intel8x0,snd_pcm
parport_pc             40100  1 
i2c_sis96x             12420  0 
sis_agp                15360  1 
parport                42220  3 lp,ppdev,parport_pc
shpchp                 40212  0 
agpgart                42696  1 sis_agp
hid_bright              9984  0 
sis900                 28288  0 
mii                    13312  1 sis900
usbhid                 42336  1 hid_bright
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit

robert@robert-laptop:~$ lspci -v
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 650/M650 Host (rev 01)
    Flags: bus master, medium devsel, latency 32
    Memory at e0000000 (32-bit, non-prefetchable) [size=64M]
    Capabilities: <access denied>
    Kernel driver in use: agpgart-sis
    Kernel modules: sis-agp

00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
    Flags: bus master, fast devsel, latency 64
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 0000a000-0000afff
    Memory behind bridge: dfe00000-dfefffff
    Prefetchable memory behind bridge: cfc00000-dfcfffff
    Kernel modules: shpchp

00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS961 [MuTIOL Media IO]
    Flags: bus master, medium devsel, latency 0

00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
    Flags: medium devsel
    I/O ports at 0c00 [size=32]
    Kernel driver in use: sis96x_smbus
    Kernel modules: i2c-sis96x

00:02.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 07) (prog-if 10)
    Subsystem: Silicon Integrated Systems [SiS] USB 1.1 Controller
    Flags: bus master, medium devsel, latency 64, IRQ 11
    Memory at dfffa000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:02.3 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 07) (prog-if 10)
    Subsystem: Silicon Integrated Systems [SiS] USB 1.1 Controller
    Flags: bus master, medium devsel, latency 64, IRQ 11
    Memory at dfffb000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev d0) (prog-if 80 [Master])
    Subsystem: Silicon Integrated Systems [SiS] 5513 [IDE]
    Flags: bus master, fast devsel, latency 128
    [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
    [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
    [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
    [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
    I/O ports at ff00 [size=16]
    Kernel driver in use: pata_sis

00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
    Subsystem: Elitegroup Computer Systems Device b731
    Flags: medium devsel, IRQ 11
    I/O ports at d400 [size=256]
    I/O ports at d000 [size=128]
    Capabilities: <access denied>
    Kernel modules: snd-intel8x0m

00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
    Subsystem: Elitegroup Computer Systems Device 0f05
    Flags: bus master, medium devsel, latency 64, IRQ 11
    I/O ports at dc00 [size=256]
    I/O ports at d800 [size=128]
    Capabilities: <access denied>
    Kernel driver in use: Intel ICH
    Kernel modules: snd-intel8x0

00:03.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
    Subsystem: Elitegroup Computer Systems Device 0f05
    Flags: bus master, medium devsel, latency 64, IRQ 11
    I/O ports at cc00 [size=256]
    Memory at dfff9000 (32-bit, non-prefetchable) [size=4K]
    Expansion ROM at dffc0000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: sis900
    Kernel modules: sis900

00:0a.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller
    Subsystem: Silicon Integrated Systems [SiS] Device b731
    Flags: bus master, medium devsel, latency 168, IRQ 11
    Memory at 18000000 (32-bit, non-prefetchable) [size=4K]
    Bus: primary=00, secondary=02, subordinate=05, sec-latency=176
    Memory window 0: 10000000-13fff000 (prefetchable)
    Memory window 1: 14000000-17fff000
    I/O window 0: 00001000-000010ff
    I/O window 1: 00001400-000014ff
    16-bit legacy interface ports at 0001
    Kernel driver in use: yenta_cardbus
    Kernel modules: yenta_socket

01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 65x/M650/740 PCI/AGP VGA Display Adapter
    Subsystem: Elitegroup Computer Systems Device 0f05
    Flags: 66MHz, medium devsel, IRQ 11
    BIST result: 00
    Memory at d0000000 (32-bit, prefetchable) [size=128M]
    Memory at dfee0000 (32-bit, non-prefetchable) [size=128K]
    I/O ports at ac00 [size=128]
    Capabilities: <access denied>
    Kernel modules: sisfb

02:00.0 Multimedia video controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
    Subsystem: Yuan Yuan Enterprise Co., Ltd. Device 1788
    Flags: bus master, medium devsel, latency 64, IRQ 11
    Memory at 14000000 (32-bit, non-prefetchable) [size=16M]
    Capabilities: <access denied>
    Kernel driver in use: cx8800
    Kernel modules: cx8800

02:00.1 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port] (rev 05)
    Subsystem: Yuan Yuan Enterprise Co., Ltd. Device 1788
    Flags: bus master, medium devsel, latency 64, IRQ 11
    Memory at 15000000 (32-bit, non-prefetchable) [size=16M]
    Capabilities: <access denied>
    Kernel driver in use: cx88_audio
    Kernel modules: cx88-alsa

02:00.2 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)
    Subsystem: Yuan Yuan Enterprise Co., Ltd. Device 1788
    Flags: medium devsel, IRQ 11
    Memory at 16000000 (32-bit, non-prefetchable) [disabled] [size=16M]
    Capabilities: <access denied>
    Kernel modules: cx8802
robert@robert-laptop:~$ dmesg  | grep cx88
[   21.271764] cx88/0: cx2388x v4l2 driver version 0.0.6 loaded
[   21.273583] cx8800 0000:02:00.0: enabling device (0000 -> 0002)
[   21.273609] cx8800 0000:02:00.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[   21.274699] cx88[0]: subsystem: 12ab:1788, board: KWorld LTV883RF [card=16,insmod option], frontend(s): 0
[   21.274707] cx88[0]: TV tuner type 65, Radio tuner type -1
[   21.288433] cx88/2: cx2388x MPEG-TS Driver Manager version 0.0.6 loaded
[   21.481291] tuner' 1-0061: chip found @ 0xc2 (cx88[0])
[   21.606050] input: cx88 IR (KWorld LTV883RF) as /devices/pci0000:00/0000:00:0a.0/0000:02:00.0/input/input9
[   21.609369] cx88[0]/0: found at 0000:02:00.0, rev: 5, irq: 11, latency: 0, mmio: 0x14000000
[   21.609384] cx8800 0000:02:00.0: setting latency timer to 64
[   21.609704] cx88[0]/0: registered device video0 [v4l2]
[   21.609954] cx88[0]/0: registered device vbi0
[   21.610203] cx88[0]/0: registered device radio0
[   21.613725] cx88_audio 0000:02:00.1: enabling device (0000 -> 0002)
[   21.613747] cx88_audio 0000:02:00.1: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[   21.613759] cx88_audio 0000:02:00.1: setting latency timer to 64
[   21.613808] cx88[0]/1: CX88x/0: ALSA support for cx2388x boards
[   21.616920] cx88[0]/2: cx2388x 8802 Driver Manager


When I start Kaffeine i donthave the option for look tv. 
Please help me!!!!!

Thanks to all!!!

---

### Post by xc3RnbFO8P on 2009-05-01
Try this:
> cd /lib/firmware
> sudo wget [http://85.10.198.106/firmware/firmware.tgz](http://85.10.198.106/firmware/firmware.tgz)
> sudo tar xvzf firmware.tgz
restart the computer and check if some drivers are loaded (or start Kaffeine).

---

