---
title: "No sound at all from the beginning :("
date: 2010-03-09
forum: Multimedia Software
---

### Post by go7hic on 2010-03-09
Hey everybody, i have just installed new ubuntu 9.10 a couple of days ago. Done all the updates. Everything is working fine, except sound. It's not working at all. I have new Panasonic CF-F8 laptop. I tried a lot of things and fixes, nothing worked. When I type "aplay -l" in terminal here's what it says:
=================================================================
go7hic@go7hic-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI [INTEL HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
==========================================================================

It means that it sees my hardware. (Of course that I checked the alsamixer and the sound is up :))
*Then I tried the /etc/modprobe.d/alsaconf.conf to play with the model option, and it didn't work. 
*My user is added to an audio group in "Users i Groups".
*Reinstalled whole the alsa from the beggining with the "ad1889" and "snd-hda-intel" drivers and it still didn't work.
When I type "lspci -v" here's what I got:

========================================================================================
go7hic@go7hic-laptop:~$ lspci -v
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
	Subsystem: Matsushita Electric Industrial Co., Ltd. Device 8338
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
	Subsystem: Matsushita Electric Industrial Co., Ltd. Device 8338
	Flags: bus master, fast devsel, latency 0, IRQ 29
	Memory at f0000000 (64-bit, non-prefetchable) [size=4M]
	Memory at e0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at e1c0 [size=8]
	Capabilities: <access denied>
	Kernel driver in use: i915
	Kernel modules: i915

00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
	Subsystem: Matsushita Electric Industrial Co., Ltd. Device 8338
	Flags: bus master, fast devsel, latency 0
	Memory at f0400000 (64-bit, non-prefetchable) [size=1M]
	Capabilities: <access denied>

00:19.0 Ethernet controller: Intel Corporation 82567LM Gigabit Network Connection (rev 03)
	Subsystem: Matsushita Electric Industrial Co., Ltd. Device 8338
	Flags: bus master, fast devsel, latency 0, IRQ 28
	Memory at f6a00000 (32-bit, non-prefetchable) [size=128K]
	Memory at f6a28000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at e100 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: e1000e
	Kernel modules: e1000e

00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
	Subsystem: Matsushita Electric Industrial Co., Ltd. Device 8338
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at e0e0 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
	Subsystem: Matsushita Electric Industrial Co., Ltd. Device 8338
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at e0c0 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20)
	Subsystem: Matsushita Electric Industrial Co., Ltd. Device 8338
	Flags: bus master, medium devsel, latency 0, IRQ 19
	Memory at f6a27000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
	Subsystem: Matsushita Electric Industrial Co., Ltd. Device 8338
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at f6a20000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: f5600000-f69fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 0000c000-0000cfff
	Memory behind bridge: f4200000-f55fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 0000b000-0000bfff
	Memory behind bridge: f2e00000-f41fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
	Subsystem: Matsushita Electric Industrial Co., Ltd. Device 8338
	Flags: bus master, medium devsel, latency 0, IRQ 23
	I/O ports at e0a0 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
	Subsystem: Matsushita Electric Industrial Co., Ltd. Device 8338
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at e080 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
	Subsystem: Matsushita Electric Industrial Co., Ltd. Device 8338
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at e060 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
	Subsystem: Matsushita Electric Industrial Co., Ltd. Device 8338
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at e040 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20)
	Subsystem: Matsushita Electric Industrial Co., Ltd. Device 8338
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at f6a26000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93) (prog-if 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=08, sec-latency=32
	I/O behind bridge: 00009000-0000afff
	Memory behind bridge: f0500000-f2dfffff
	Prefetchable memory behind bridge: 00000000bc000000-00000000bfffffff
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation ICH9M-E LPC Interface Controller (rev 03)
	Subsystem: Matsushita Electric Industrial Co., Ltd. Device 8338
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: iTCO_wdt

00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03) (prog-if 01)
	Subsystem: Matsushita Electric Industrial Co., Ltd. Device 8338
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 27
	I/O ports at e150 [size=8]
	I/O ports at e140 [size=4]
	I/O ports at e130 [size=8]
	I/O ports at e120 [size=4]
	I/O ports at e020 [size=32]
	Memory at f6a25000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: ahci

00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
	Subsystem: Matsushita Electric Industrial Co., Ltd. Device 8338
	Flags: medium devsel, IRQ 10
	Memory at f6a24000 (64-bit, non-prefetchable) [size=256]
	I/O ports at e000 [size=32]
	Kernel modules: i2c-i801

02:00.0 IDE interface: Marvell Technology Group Ltd. 88SE6101 single-port PATA133 interface (rev c0) (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: Marvell Technology Group Ltd. 88SE6101 single-port PATA133 interface
	Flags: bus master, fast devsel, latency 0, IRQ 17
	I/O ports at c040 [size=8]
	I/O ports at c030 [size=4]
	I/O ports at c020 [size=8]
	I/O ports at c010 [size=4]
	I/O ports at c000 [size=16]
	Memory at f4200000 (32-bit, non-prefetchable) [size=512]
	Capabilities: <access denied>
	Kernel driver in use: pata_marvell

03:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
	Subsystem: Intel Corporation Device 1201
	Flags: bus master, fast devsel, latency 0, IRQ 30
	Memory at f2e00000 (64-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>
	Kernel driver in use: iwlagn
	Kernel modules: iwlagn

04:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ba)
	Subsystem: Matsushita Electric Industrial Co., Ltd. Device 8338
	Flags: bus master, medium devsel, latency 168, IRQ 22
	Memory at f2d01000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=04, secondary=05, subordinate=08, sec-latency=176
	Memory window 0: bc000000-bffff000 (prefetchable)
	Memory window 1: c0000000-c3fff000
	I/O window 0: 00009000-000090ff
	I/O window 1: 00009400-000094ff
	16-bit legacy interface ports at 0001
	Kernel driver in use: yenta_cardbus
	Kernel modules: yenta_socket

04:00.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 21) (prog-if 01)
	Subsystem: Matsushita Electric Industrial Co., Ltd. Device 8338
	Flags: bus master, medium devsel, latency 32, IRQ 23
	Memory at f2d00000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci

go7hic@go7hic-laptop:~$ sudo modprobe snd-
Display all 201 possibilities? (y or n)
go7hic@go7hic-laptop:~$ sudo modprobe snd-
Display all 201 possibilities? (y or n)
snd-ac97-codec           snd-hda-codec-si3054     snd-sbawe
snd-ad1816a              snd-hda-codec-via        snd-sb-common
snd-ad1848               snd-hda-intel            snd-sc6000
snd-ad1889               snd-hdsp                 snd-seq
snd-adlib                snd-hdspm                snd-seq-device
snd-ak4114               snd-hifier               snd-seq-dummy
snd-ak4117               snd-hrtimer              snd-seq-midi
snd-ak4xxx-adda          snd-hwdep                snd-seq-midi-emul
snd-ali5451              snd-i2c                  snd-seq-midi-event
snd-als100               snd-ice1712              snd-seq-oss
snd-als300               snd-ice1724              snd-seq-virmidi
snd-als4000              snd-ice17xx-ak4xxx       snd-serial-u16550
snd-atiixp               snd-indigo               snd-sgalaxy
snd-atiixp-modem         snd-indigodj             snd-sis7019
snd-au8810               snd-indigodjx            snd-soc-ad73311
snd-au8820               snd-indigoio             snd-soc-ak4104
snd-au8830               snd-indigoiox            snd-soc-ak4535
snd-aw2                  snd-intel8x0             snd-soc-core
snd-azt2320              snd-intel8x0m            snd-soc-cs4270
snd-azt3328              snd-interwave            snd-soc-l3
snd-bt87x                snd-interwave-stb        snd-soc-pcm3008
snd-ca0106               snd-korg1212             snd-soc-spdif
snd-cmi8330              snd-layla20              snd-soc-ssm2602
snd-cmipci               snd-layla24              snd-soc-tlv320aic23
snd-cs4231               snd-lx6464es             snd-soc-tlv320aic26
snd-cs4236               snd-maestro3             snd-soc-tlv320aic3x
snd-cs4281               snd-mia                  snd-soc-twl4030
snd-cs46xx               snd-miro                 snd-soc-uda134x
snd-cs5530               snd-mixart               snd-soc-uda1380
snd-cs5535audio          snd-mixer-oss            snd-soc-wm8350
snd-cs8427               snd-mona                 snd-soc-wm8400
snd-ctxfi                snd-mpu401               snd-soc-wm8510
snd-darla20              snd-mpu401-uart          snd-soc-wm8580
snd-darla24              snd-msnd-classic         snd-soc-wm8728
snd-dt019x               snd-msnd-lib             snd-soc-wm8731
snd-dummy                snd-msnd-pinnacle        snd-soc-wm8750
snd-echo3g               snd-mtpav                snd-soc-wm8753
snd-emu10k1              snd-mts64                snd-soc-wm8900
snd-emu10k1-synth        snd-nm256                snd-soc-wm8903
snd-emu10k1x             snd-opl3-lib             snd-soc-wm8940
snd-emu8000-synth        snd-opl3sa2              snd-soc-wm8960
snd-emux-synth           snd-opl3-synth           snd-soc-wm8971
snd-ens1370              snd-opl4-lib             snd-soc-wm8988
snd-ens1371              snd-opl4-synth           snd-soc-wm8990
snd-es1688               snd-opti92x-ad1848       snd-soc-wm9081
snd-es1688-lib           snd-opti92x-cs4231       snd-sonicvibes
snd-es18xx               snd-opti93x              snd-sscape
snd-es1938               snd-oxygen               snd-tea575x-tuner
snd-es1968               snd-oxygen-lib           snd-tea6330t
snd-es968                snd-page-alloc           snd-timer
snd-fm801                snd-pcm                  snd-trident
snd-gina20               snd-pcm-oss              snd-usb-audio
snd-gina24               snd-pcsp                 snd-usb-caiaq
snd-gusclassic           snd-pcxhr                snd-usb-lib
snd-gusextreme           snd-pdaudiocf            snd-usb-us122l
snd-gus-lib              snd-portman2x4           snd-usb-usx2y
snd-gusmax               snd-pt2258               snd-util-mem
snd-hda-codec            snd-rawmidi              snd-via82xx
snd-hda-codec-analog     snd-riptide              snd-via82xx-modem
snd-hda-codec-atihdmi    snd-rme32                snd-virmidi
snd-hda-codec-ca0110     snd-rme96                snd-virtuoso
snd-hda-codec-cmedia     snd-rme9652              snd-vx222
snd-hda-codec-conexant   snd-sb16                 snd-vx-lib
snd-hda-codec-idt        snd-sb16-csp             snd-vxpocket
snd-hda-codec-intelhdmi  snd-sb16-dsp             snd-wavefront
snd-hda-codec-nvhdmi     snd-sb8                  snd-wss-lib
snd-hda-codec-realtek    snd-sb8-dsp              snd-ymfpci
go7hic@go7hic-laptop:~$ sudo modprobe snd-hda-intel
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
=====================================================================================


Please help me guys, I can't live without sound :|

---

### Post by halj32 on 2010-03-09
have you tried turning the sound on..
When I do a fresh install I always find I have to right click on the sound icon and un mute & select device & turn the volume up.
I use a Dell laptop & a home build & this only happens in K/Ubuntu never in SuSE, Puppy or Sabayon

---

### Post by go7hic on 2010-03-09
> **go7hic said:**
> 
It means that it sees my hardware. (Of course that I checked the alsamixer and the sound is up :))

Yes I chose "Digital Stereo Output(IEC958)" hardware and the sound is not muted :)
Also checked all other hardware options, like analog stereo output and duplex. Nothing works (

---

### Post by go7hic on 2010-03-09
No one to help? :(

---

