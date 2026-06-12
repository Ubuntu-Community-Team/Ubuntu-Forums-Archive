---
title: "external mic jack not working in xubuntu"
date: 2011-05-16
forum: Multimedia Software
---

### Post by fgadea on 2011-05-16
Hi guys. For the first time since I use xubuntu I have needed the external mic jack to do some recordings and it does not work. 
Here is the data I get with "amixer", "aplay -l", "lspci -v" and "modprobe snd + TABkey"
For my hardware setup please see my signature.
Thankyou for any help you can give me.


nan@parnaso:~$ **amixer**
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 30
  Mono: Playback 30 [100%] [0.00dB] [on]
Simple mixer control 'Headphone',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 30
  Mono:
  Front Left: Playback 30 [100%] [-1.50dB]
  Front Right: Playback 30 [100%] [-1.50dB]
Simple mixer control 'PCM',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 208 [82%] [-9.40dB] [on]
  Front Right: Playback 208 [82%] [-9.40dB] [on]
Simple mixer control 'Mic',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 30
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off]
Simple mixer control 'Mic Boost',0
  Capabilities: volume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 2 [67%]
  Front Right: 2 [67%]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'IEC958 Default PCM',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 14
  Front Left: Capture 11 [79%] [16.50dB] [on]
  Front Right: Capture 11 [79%] [16.50dB] [on]
Simple mixer control 'Digital',0
  Capabilities: cvolume
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 120
  Front Left: Capture 84 [70%] [12.00dB]
  Front Right: Capture 84 [70%] [12.00dB]
Simple mixer control 'Speaker',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 30
  Mono:
  Front Left: Playback 30 [100%] [-1.50dB]
  Front Right: Playback 30 [100%] [-1.50dB]
nan@parnaso:~$ aplay -l
**** Lista de PLAYBACK Dispositivos Hardware ****
tarjeta 0: Intel [HDA Intel], dispositivo 0: CONEXANT Analog [CONEXANT Analog]
  Subdispositivos: 0/1
  Subdispositivo #0: subdevice #0
tarjeta 0: Intel [HDA Intel], dispositivo 1: Conexant Digital [Conexant Digital]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0




**aplay -l**
**** Lista de PLAYBACK Dispositivos Hardware ****
tarjeta 0: Intel [HDA Intel], dispositivo 0: CONEXANT Analog [CONEXANT Analog]
  Subdispositivos: 0/1
  Subdispositivo #0: subdevice #0
tarjeta 0: Intel [HDA Intel], dispositivo 1: Conexant Digital [Conexant Digital]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0




**lspci -v**
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
    Subsystem: Hewlett-Packard Company Device 30a0
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: agpgart-intel
    Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
    Subsystem: Hewlett-Packard Company Device 30a0
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at d8100000 (32-bit, non-prefetchable) [size=512K]
    I/O ports at 1800 [size=8]
    Memory at c0000000 (32-bit, prefetchable) [size=256M]
    Memory at d8200000 (32-bit, non-prefetchable) [size=256K]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915

00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
    Subsystem: Hewlett-Packard Company Device 30a0
    Flags: bus master, fast devsel, latency 0
    Memory at d8180000 (32-bit, non-prefetchable) [size=512K]
    Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
    Subsystem: Hewlett-Packard Company Device 30a0
    Flags: bus master, fast devsel, latency 0, IRQ 22
    Memory at d8240000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: d6000000-d7ffffff
    Prefetchable memory behind bridge: 00000000d2000000-00000000d3ffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=04, sec-latency=0
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: d4000000-d5ffffff
    Prefetchable memory behind bridge: 00000000d0000000-00000000d1ffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
    Subsystem: Hewlett-Packard Company Device 30a0
    Flags: bus master, medium devsel, latency 0, IRQ 23
    I/O ports at 1820 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
    Subsystem: Hewlett-Packard Company Device 30a0
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at 1840 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
    Subsystem: Hewlett-Packard Company Device 30a0
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at 1860 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
    Subsystem: Hewlett-Packard Company Device 30a0
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at 1880 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02) (prog-if 20)
    Subsystem: Hewlett-Packard Company Device 30a0
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at d8444000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=05, subordinate=05, sec-latency=32
    I/O behind bridge: 00004000-00004fff
    Memory behind bridge: d8000000-d80fffff
    Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
    Subsystem: Hewlett-Packard Company Device 30a0
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: iTCO_wdt, intel-rng

00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
    Subsystem: Hewlett-Packard Company Device 30a0
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at 1810 [size=16]
    Kernel driver in use: ata_piix

00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02) (prog-if 01)
    Subsystem: Hewlett-Packard Company Device 30a0
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 26
    I/O ports at 18d0 [size=8]
    I/O ports at 18c4 [size=4]
    I/O ports at 18c8 [size=8]
    I/O ports at 18c0 [size=4]
    I/O ports at 18b0 [size=16]
    Memory at d8444400 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ahci

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
    Subsystem: Hewlett-Packard Company Device 30a0
    Flags: medium devsel, IRQ 4
    I/O ports at 18e0 [size=32]
    Kernel modules: i2c-i801

02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
    Subsystem: Hewlett-Packard Company Device 135b
    Flags: bus master, fast devsel, latency 0, IRQ 27
    Memory at d6000000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: iwl3945
    Kernel modules: iwl3945

05:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 02)
    Subsystem: Hewlett-Packard Company Device 30a0
    Flags: bus master, medium devsel, latency 64, IRQ 20
    Memory at d8000000 (32-bit, non-prefetchable) [size=4K]
    I/O ports at 4000 [size=64]
    Capabilities: <access denied>
    Kernel driver in use: e100
    Kernel modules: e100

05:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (prog-if 10)
    Subsystem: Hewlett-Packard Company Device 30a0
    Flags: bus master, medium devsel, latency 64, IRQ 20
    Memory at d8001000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: ohci1394
    Kernel modules: firewire-ohci, ohci1394

05:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
    Subsystem: Hewlett-Packard Company Device 30a0
    Flags: medium devsel, IRQ 21
    Memory at d8001800 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci-pci

05:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
    Subsystem: Hewlett-Packard Company Device 30a0
    Flags: medium devsel, IRQ 11
    Memory at d8001c00 (32-bit, non-prefetchable) [disabled] [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ricoh-mmc
    Kernel modules: ricoh_mmc

05:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
    Subsystem: Hewlett-Packard Company Device 30a0
    Flags: medium devsel, IRQ 11
    Memory at d8002000 (32-bit, non-prefetchable) [disabled] [size=256]
    Capabilities: <access denied>

05:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff) (prog-if ff)
    !!! Unknown header type 7f










nan@parnaso:~$ **modprobe snd**
Display all 202 possibilities? (y or n)
snd                      snd-hda-codec-si3054     snd-sb-common
snd-ac97-codec           snd-hda-codec-via        snd-sc6000
snd-ad1816a              snd-hda-intel            snd-seq
snd-ad1848               snd-hdsp                 snd-seq-device
snd-ad1889               snd-hdspm                snd-seq-dummy
snd-adlib                snd-hifier               snd-seq-midi
snd-ak4114               snd-hrtimer              snd-seq-midi-emul
snd-ak4117               snd-hwdep                snd-seq-midi-event
snd-ak4xxx-adda          snd-i2c                  snd-seq-oss
snd-ali5451              snd-ice1712              snd-seq-virmidi
snd-als100               snd-ice1724              snd-serial-u16550
snd-als300               snd-ice17xx-ak4xxx       snd-sgalaxy
snd-als4000              snd-indigo               snd-sis7019
snd-atiixp               snd-indigodj             snd-soc-ad73311
snd-atiixp-modem         snd-indigodjx            snd-soc-ak4104
snd-au8810               snd-indigoio             snd-soc-ak4535
snd-au8820               snd-indigoiox            snd-soc-core
snd-au8830               snd-intel8x0             snd-soc-cs4270
snd-aw2                  snd-intel8x0m            snd-soc-l3
snd-azt2320              snd-interwave            snd-soc-pcm3008
snd-azt3328              snd-interwave-stb        snd-soc-spdif
snd-bt87x                snd-korg1212             snd-soc-ssm2602
snd-ca0106               snd-layla20              snd-soc-tlv320aic23
snd-cmi8330              snd-layla24              snd-soc-tlv320aic26
snd-cmipci               snd-lx6464es             snd-soc-tlv320aic3x
snd-cs4231               snd-maestro3             snd-soc-twl4030
snd-cs4236               snd-mia                  snd-soc-uda134x
snd-cs4281               snd-miro                 snd-soc-uda1380
snd-cs46xx               snd-mixart               snd-soc-wm8350
snd-cs5530               snd-mixer-oss            snd-soc-wm8400
snd-cs5535audio          snd-mona                 snd-soc-wm8510
snd-cs8427               snd-mpu401               snd-soc-wm8580
snd-ctxfi                snd-mpu401-uart          snd-soc-wm8728
snd-darla20              snd-msnd-classic         snd-soc-wm8731
snd-darla24              snd-msnd-lib             snd-soc-wm8750
snd-dt019x               snd-msnd-pinnacle        snd-soc-wm8753
snd-dummy                snd-mtpav                snd-soc-wm8900
snd-echo3g               snd-mts64                snd-soc-wm8903
snd-emu10k1              snd-nm256                snd-soc-wm8940
snd-emu10k1-synth        snd-opl3-lib             snd-soc-wm8960
snd-emu10k1x             snd-opl3sa2              snd-soc-wm8971
snd-emu8000-synth        snd-opl3-synth           snd-soc-wm8988
snd-emux-synth           snd-opl4-lib             snd-soc-wm8990
snd-ens1370              snd-opl4-synth           snd-soc-wm9081
snd-ens1371              snd-opti92x-ad1848       snd-sonicvibes
snd-es1688               snd-opti92x-cs4231       snd-sscape
snd-es1688-lib           snd-opti93x              snd-tea575x-tuner
snd-es18xx               snd-oxygen               snd-tea6330t
snd-es1938               snd-oxygen-lib           snd-timer
snd-es1968               snd-page-alloc           snd-trident
snd-es968                snd-pcm                  snd-usb-audio
snd-fm801                snd-pcm-oss              snd-usb-caiaq
snd-gina20               snd-pcsp                 snd-usb-lib
snd-gina24               snd-pcxhr                snd-usb-us122l
snd-gusclassic           snd-pdaudiocf            snd-usb-usx2y
snd-gusextreme           snd-portman2x4           snd-util-mem
snd-gus-lib              snd-pt2258               snd-via82xx
snd-gusmax               snd-rawmidi              snd-via82xx-modem
snd-hda-codec            snd-riptide              snd-virmidi
snd-hda-codec-analog     snd-rme32                snd-virtuoso
snd-hda-codec-atihdmi    snd-rme96                snd-vx222
snd-hda-codec-ca0110     snd-rme9652              snd-vx-lib
snd-hda-codec-cmedia     snd-sb16                 snd-vxpocket
snd-hda-codec-conexant   snd-sb16-csp             snd-wavefront
snd-hda-codec-idt        snd-sb16-dsp             snd-wss-lib
snd-hda-codec-intelhdmi  snd-sb8                  snd-ymfpci
snd-hda-codec-nvhdmi     snd-sb8-dsp              
snd-hda-codec-realtek    snd-sbawe

---

### Post by fgadea on 2011-05-17
I would appreciate too if someone could help me understand all that stuff I posted (I did so because I see those who understand something ask to do it).

As I read in other posts the external mic jack would be the capture device, which in my machine appears to be on?

Does anyone knows a comprehensive guide to sound in linux for recent linux users (or in my case, a not tech guy willing to learn without bothering all the time)

Please help! this is important for me. 

Thank you

---

### Post by buntumaddy on 2011-10-11
Were you able to find a solution to this? I am in the same boat with a Thinkpad T520 and 10.10.

---

### Post by fgadea on 2011-10-11
> **buntumaddy said:**
> Were you able to find a solution to this? I am in the same boat with a Thinkpad T520 and 10.10.

Not yet. But this week I installed Puredyne. Weekend will be the test time. If I have good news I'll let you know.

---

