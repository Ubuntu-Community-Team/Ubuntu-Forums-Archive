---
title: "Emu 1212m PCIexpress.. Drivers?!?"
date: 2010-08-14
forum: Multimedia Software
---

### Post by hansdevr on 2010-08-14
Anyone in the savvy about this great soundcard?!?

It's doing a great job with Cubase under WXP, but now I sure would like to get it working with Rosegarden... Anyone?!?

---

### Post by hansdevr on 2010-08-18
....bump...

---

### Post by cchhrriiss121212 on 2010-08-18
A bit more info please:
Where do you need help? Do you need a complete walkthrough or just hardware assistance?
Is it being recognised? Type aplay -l into a terminal to find out.

---

### Post by hansdevr on 2010-08-19
I will try that, but my initial feeling is that it isn't recognised. It does find my poxy motherboard sound interface, but the 1212M PCIe is not found. Also not selectable in system settings. I'm a linux newbie.

System: quad core AMD with 8 Gig and 1 Tb drive, ATI sapphire HD 3870, kubuntu AMD64 real time kernel OS.

---

### Post by cchhrriiss121212 on 2010-08-19
Well it is a supported soundcard, so this should be able to get working eventually. If you have no luck with aplay -l then also post the result of lspci -v.

---

### Post by hansdevr on 2010-08-19
Result of aplay:
```
aplay -l
**** Lijst van PLAYBACK hardware-apparaten ****
kaart 0: SB [HDA ATI SB], apparaat 0: AD198x Analog [AD198x Analog]
  Sub-apparaten: 1/1
  Sub-apparaat #0: subdevice #0
kaart 0: SB [HDA ATI SB], apparaat 1: AD198x Digital [AD198x Digital]
  Sub-apparaten: 1/1
  Sub-apparaat #0: subdevice #0
kaart 2: HDMI [HDA ATI HDMI], apparaat 3: ATI HDMI [ATI HDMI]
  Sub-apparaten: 1/1
  Sub-apparaat #0: subdevice #0
```
Sorry for output being in Dutch...

Output of lspci -v:
```
lspci -v
00:00.0 Host bridge: ATI Technologies Inc RD790 Northbridge only dual slot PCI-e_GFX and HT3 K8 part
        Subsystem: ATI Technologies Inc RD790 Northbridge only dual slot PCI-e_GFX and HT3 K8 part
        Flags: bus master, 66MHz, medium devsel, latency 0
        Memory at <ignored> (64-bit, non-prefetchable)
        Capabilities: <access denied>

00:02.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (external gfx0 port A)
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 00008000-00008fff
        Memory behind bridge: fe700000-fe7fffff
        Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
        Capabilities: <access denied>
        Kernel driver in use: pcieport
        Kernel modules: shpchp

00:04.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (PCI express gpp port A)
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        I/O behind bridge: 00009000-0000afff
        Memory behind bridge: fe800000-fe8fffff
        Capabilities: <access denied>
        Kernel driver in use: pcieport
        Kernel modules: shpchp

00:06.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (PCI express gpp port C)
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        I/O behind bridge: 0000b000-0000bfff
        Memory behind bridge: fe900000-fe9fffff
        Capabilities: <access denied>
        Kernel driver in use: pcieport
        Kernel modules: shpchp

00:07.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (PCI express gpp port D)
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
        I/O behind bridge: 0000c000-0000dfff
        Memory behind bridge: fea00000-feafffff
        Capabilities: <access denied>
        Kernel driver in use: pcieport
        Kernel modules: shpchp

00:0b.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (external gfx1 port A)
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=05, subordinate=06, sec-latency=0
        I/O behind bridge: 0000e000-0000efff
        Capabilities: <access denied>
        Kernel driver in use: pcieport
        Kernel modules: shpchp

00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA (prog-if 01)
        Subsystem: ASUSTeK Computer Inc. Device 81ef
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 22
        I/O ports at 7000 [size=8]
        I/O ports at 6000 [size=4]
        I/O ports at 5000 [size=8]
        I/O ports at 4000 [size=4]
        I/O ports at 3000 [size=16]
        Memory at fe6ff800 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>
        Kernel driver in use: ahci
        Kernel modules: ahci

00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0) (prog-if 10)
        Subsystem: ASUSTeK Computer Inc. Device 8288
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
        Memory at fe6fe000 (32-bit, non-prefetchable) [size=4K]
        Kernel driver in use: ohci_hcd

00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1) (prog-if 10)
        Subsystem: ASUSTeK Computer Inc. Device 8288
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
        Memory at fe6fd000 (32-bit, non-prefetchable) [size=4K]
        Kernel driver in use: ohci_hcd

00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2) (prog-if 10)
        Subsystem: ASUSTeK Computer Inc. Device 8288
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
        Memory at fe6fc000 (32-bit, non-prefetchable) [size=4K]
        Kernel driver in use: ohci_hcd

00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3) (prog-if 10)
        Subsystem: ASUSTeK Computer Inc. Device 8288
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
        Memory at fe6fb000 (32-bit, non-prefetchable) [size=4K]
        Kernel driver in use: ohci_hcd

00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4) (prog-if 10)
        Subsystem: ASUSTeK Computer Inc. Device 8288
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
        Memory at fe6fa000 (32-bit, non-prefetchable) [size=4K]
        Kernel driver in use: ohci_hcd

00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI) (prog-if 20)
        Subsystem: ASUSTeK Computer Inc. Device 8288
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
        Memory at fe6ff000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>
        Kernel driver in use: ehci_hcd

00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
        Subsystem: ASUSTeK Computer Inc. Device 8288
        Flags: 66MHz, medium devsel
        I/O ports at 0b00 [size=16]
        Capabilities: <access denied>
        Kernel modules: i2c-piix4

00:14.1 IDE interface: ATI Technologies Inc SB600 IDE (prog-if 8a [Master SecP PriP])
        Subsystem: ASUSTeK Computer Inc. Device 8288
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at ff00 [size=16]
        Kernel driver in use: pata_atiixp
        Kernel modules: pata_atiixp

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
        Subsystem: ASUSTeK Computer Inc. Device 8288
        Flags: bus master, slow devsel, latency 64, IRQ 16
        Memory at fe6f4000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel

00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
        Subsystem: ASUSTeK Computer Inc. Device 8288
        Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (prog-if 01)
        Flags: bus master, 66MHz, medium devsel, latency 64
        Bus: primary=00, secondary=07, subordinate=07, sec-latency=64
        Memory behind bridge: feb00000-febfffff

00:18.0 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
        Flags: fast devsel
        Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map
        Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller
        Flags: fast devsel
        Kernel modules: amd64_edac_mod

00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
        Flags: fast devsel
        Capabilities: <access denied>

00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control
        Flags: fast devsel

01:00.0 VGA compatible controller: ATI Technologies Inc Radeon HD 3870
        Subsystem: PC Partner Limited Device e620
        Flags: bus master, fast devsel, latency 0, IRQ 30
        Memory at d0000000 (64-bit, prefetchable) [size=256M]
        Memory at fe7f0000 (64-bit, non-prefetchable) [size=64K]
        I/O ports at 8000 [size=256]
        Expansion ROM at fe7c0000 [disabled] [size=128K]
        Capabilities: <access denied>
        Kernel driver in use: fglrx_pci
        Kernel modules: fglrx, radeon

01:00.1 Audio device: ATI Technologies Inc Radeon HD 3870 Audio device
        Subsystem: PC Partner Limited Device aa18
        Flags: bus master, fast devsel, latency 0, IRQ 19
        Memory at fe7ec000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel

02:00.0 IDE interface: Marvell Technology Group Ltd. 88SE6121 SATA II Controller (rev b1) (prog-if 8f [Master SecP SecO PriP PriO])
        Subsystem: Marvell Technology Group Ltd. 88SE6121 SATA II Controller
        Flags: bus master, fast devsel, latency 0, IRQ 16
        I/O ports at a800 [size=8]
        I/O ports at a400 [size=4]
        I/O ports at a000 [size=8]
        I/O ports at 9800 [size=4]
        I/O ports at 9400 [size=16]
        Memory at fe8ffc00 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>
        Kernel driver in use: pata_marvell
        Kernel modules: pata_marvell, ahci

03:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller (rev 12)
        Subsystem: ASUSTeK Computer Inc. Device 81f8
        Flags: bus master, fast devsel, latency 0, IRQ 29
        Memory at fe9fc000 (64-bit, non-prefetchable) [size=16K]
        I/O ports at b800 [size=256]
        Expansion ROM at fe9c0000 [disabled] [size=128K]
        Capabilities: <access denied>
        Kernel driver in use: sky2
        Kernel modules: sky2

04:00.0 IDE interface: Marvell Technology Group Ltd. 88SE6121 SATA II Controller (rev b2) (prog-if 8f [Master SecP SecO PriP PriO])
        Subsystem: Marvell Technology Group Ltd. 88SE6121 SATA II Controller
        Flags: bus master, fast devsel, latency 0, IRQ 19
        I/O ports at d800 [size=8]
        I/O ports at d400 [size=4]
        I/O ports at d000 [size=8]
        I/O ports at c800 [size=4]
        I/O ports at c400 [size=16]
        Memory at feaffc00 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>
        Kernel driver in use: pata_marvell
        Kernel modules: pata_marvell, ahci

05:00.0 PCI bridge: Pericom Semiconductor Device e111 (rev 02)
        Flags: bus master, fast devsel, latency 0
        Bus: primary=05, secondary=06, subordinate=06, sec-latency=64
        I/O behind bridge: 0000e000-0000efff
        Capabilities: <access denied>
        Kernel modules: shpchp

06:04.0 Multimedia audio controller: Creative Labs SB0400 Audigy2 Value
        Subsystem: Creative Labs Device 4007
        Flags: medium devsel, IRQ 19
        I/O ports at e800 [size=64]
        Capabilities: <access denied>
        Kernel modules: snd-emu10k1

07:08.0 FireWire (IEEE 1394): Agere Systems FW322/323 (rev 70) (prog-if 10)
        Subsystem: ASUSTeK Computer Inc. Device 8294
        Flags: bus master, medium devsel, latency 64, IRQ 22
        Memory at febff000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>
        Kernel driver in use: ohci1394
        Kernel modules: firewire-ohci, ohci1394
```

Hope this helps...

---

### Post by hansdevr on 2010-08-20
...bump...

---

### Post by cchhrriiss121212 on 2010-08-20
> 06:04.0 Multimedia audio controller: Creative Labs SB0400 Audigy2 Value
        Subsystem: Creative Labs Device 4007
        Flags: medium devsel, IRQ 19
        I/O ports at e800 [size=64]
        Capabilities: <access denied>
        Kernel modules: snd-emu10k1
So this output shows that Ubuntu can see the device, but for some reason it is recognising it as a different model.

Type sudo modprobe snd-emu10k1 into a terminal, and then thy aplay -l again.

---

### Post by hansdevr on 2010-08-21
```
$ sudo modprobe snd-emu10k1
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
$ aplay -l
**** Lijst van PLAYBACK hardware-apparaten ****
kaart 0: SB [HDA ATI SB], apparaat 0: AD198x Analog [AD198x Analog]
  Sub-apparaten: 1/1
  Sub-apparaat #0: subdevice #0
kaart 0: SB [HDA ATI SB], apparaat 1: AD198x Digital [AD198x Digital]
  Sub-apparaten: 1/1
  Sub-apparaat #0: subdevice #0
kaart 2: HDMI [HDA ATI HDMI], apparaat 3: ATI HDMI [ATI HDMI]
  Sub-apparaten: 1/1
  Sub-apparaat #0: subdevice #0

```
No luck, I guess

---

### Post by cchhrriiss121212 on 2010-08-21
What output do you get when typing 
```
sudo modprobe snd-
```
then press tab?

The ALSA database is not clear on what module this card actually uses, so you might need to try a few out.

---

### Post by hansdevr on 2010-08-21
```
Display all 170 possibilities? (y or n)
snd-ac97-codec           snd-es1938               snd-intel8x0m            snd-seq                  snd-soc-wm8731
snd-ad1889               snd-es1968               snd-korg1212             snd-seq-device           snd-soc-wm8750
snd-ak4114               snd-fm801                snd-layla20              snd-seq-dummy            snd-soc-wm8753
snd-ak4117               snd-gina20               snd-layla24              snd-seq-midi             snd-soc-wm8776
snd-ak4xxx-adda          snd-gina24               snd-lx6464es             snd-seq-midi-emul        snd-soc-wm8900
snd-ali5451              snd-hda-codec            snd-maestro3             snd-seq-midi-event       snd-soc-wm8903
snd-als300               snd-hda-codec-analog     snd-mia                  snd-seq-oss              snd-soc-wm8940
snd-als4000              snd-hda-codec-atihdmi    snd-mixart               snd-seq-virmidi          snd-soc-wm8960
snd-atiixp               snd-hda-codec-ca0110     snd-mixer-oss            snd-serial-u16550        snd-soc-wm8961
snd-atiixp-modem         snd-hda-codec-cirrus     snd-mona                 snd-soc-ad1836           snd-soc-wm8971
snd-au8810               snd-hda-codec-cmedia     snd-mpu401               snd-soc-ad1938           snd-soc-wm8974
snd-au8820               snd-hda-codec-conexant   snd-mpu401-uart          snd-soc-ad73311          snd-soc-wm8988
snd-au8830               snd-hda-codec-idt        snd-mtpav                snd-soc-ak4104           snd-soc-wm8990
snd-aw2                  snd-hda-codec-intelhdmi  snd-mts64                snd-soc-ak4535           snd-soc-wm8993
snd-azt3328              snd-hda-codec-nvhdmi     snd-nm256                snd-soc-ak4642           snd-soc-wm9081
snd-bt87x                snd-hda-codec-realtek    snd-opl3-lib             snd-soc-core             snd-soc-wm-hubs
snd-ca0106               snd-hda-codec-si3054     snd-opl3-synth           snd-soc-cs4270           snd-sonicvibes
snd-cmipci               snd-hda-codec-via        snd-oxygen               snd-soc-l3               snd-tea575x-tuner
snd-cs4281               snd-hda-intel            snd-oxygen-lib           snd-soc-max9877          snd-timer
snd-cs46xx               snd-hdsp                 snd-page-alloc           snd-soc-pcm3008          snd-trident
snd-cs5530               snd-hdspm                snd-pcm                  snd-soc-spdif            snd-usb-audio
snd-cs5535audio          snd-hifier               snd-pcm-oss              snd-soc-ssm2602          snd-usb-caiaq
snd-cs8427               snd-hrtimer              snd-pcsp                 snd-soc-tlv320aic23      snd-usb-lib
snd-ctxfi                snd-hwdep                snd-pcxhr                snd-soc-tlv320aic26      snd-usb-us122l
snd-darla20              snd-i2c                  snd-pdaudiocf            snd-soc-tlv320aic3x      snd-usb-usx2y
snd-darla24              snd-ice1712              snd-portman2x4           snd-soc-twl4030          snd-util-mem
snd-dummy                snd-ice1724              snd-pt2258               snd-soc-uda134x          snd-via82xx
snd-echo3g               snd-ice17xx-ak4xxx       snd-rawmidi              snd-soc-uda1380          snd-via82xx-modem
snd-emu10k1              snd-indigo               snd-riptide              snd-soc-wm8350           snd-virmidi
snd-emu10k1-synth        snd-indigodj             snd-rme32                snd-soc-wm8400           snd-virtuoso
snd-emu10k1x             snd-indigodjx            snd-rme96                snd-soc-wm8510           snd-vx222
snd-emux-synth           snd-indigoio             snd-rme9652              snd-soc-wm8523           snd-vx-lib
snd-ens1370              snd-indigoiox            snd-sb16-dsp             snd-soc-wm8580           snd-vxpocket
snd-ens1371              snd-intel8x0             snd-sb-common            snd-soc-wm8728           snd-ymfpci

```

It's in the list....

---

### Post by cchhrriiss121212 on 2010-08-22
The ALSA database [lists your card]("http://www.alsa-project.org/main/index.php/Matrix:Vendor-Creative_Labs") as using either the CA0102 or the emu10k1-fpga (I assume this is different from emu10k1) module. But I can't seem to find where to get these from in Ubuntu. 
Could you try loading ca0106?

---

### Post by hansdevr on 2010-08-23
> **cchhrriiss121212 said:**
>  
Could you try loading ca0106?
Errrrr... how does one go about doing that?!?

---

### Post by cchhrriiss121212 on 2010-08-23
> **hansdevr said:**
> Errrrr... how does one go about doing that?!?
Sorry, just do what you did earlier with the new module in place of emu10k1:
```
sudo modprobe snd-ca0106
```

---

### Post by david.garcia.rojo on 2010-09-18
> **cchhrriiss121212 said:**
> Sorry, just do what you did earlier with the new module in place of emu10k1:
```
sudo modprobe snd-ca0106
```

Hi!

I've exactly the same problem.
I'm on Ubuntu Studio 64.

I think that the system detect the sound card correctly when I load emu10k1 even if the name is not the same.

In alsa doc, they says to load emu10k1. I think that fpga and ca012 are part of this module.

but aplay -l doesn't list the card. Maybe it's bug from alsa or libasound something else...
Maybe it(s due to pcie...

I've tried to compile alsa like they said in the wiki.
I'm going to search for errors in logs... If they exists...

I'm very interested to found a solution.

---

### Post by david.garcia.rojo on 2010-09-18
I've found that on sys.log

> Sep 18 15:39:13 SANJI kernel: [    7.907615] EMU10K1_Audigy 0000:06:04.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Sep 18 15:39:13 SANJI kernel: [    7.913701] Audigy2 value: Special config.
Sep 18 15:39:13 SANJI kernel: [    8.014571] hda_codec: ALC889: BIOS auto-probing.
Sep 18 15:39:13 SANJI kernel: [    8.015980] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input6
Sep 18 15:39:13 SANJI kernel: [    8.022130]   alloc irq_desc for 37 on node -1
Sep 18 15:39:13 SANJI kernel: [    8.022132]   alloc kstat_irqs on node -1
Sep 18 15:39:13 SANJI kernel: [    8.022138] HDA Intel 0000:04:00.1: PCI INT B -> GSI 37 (level, low) -> IRQ 37
Sep 18 15:39:13 SANJI kernel: [    8.022179] HDA Intel 0000:04:00.1: setting latency timer to 64
Sep 18 15:39:13 SANJI kernel: [    8.129901] EXT4-fs (sda4): mounted filesystem with ordered data mode
Sep 18 15:39:13 SANJI kernel: [    8.927699] type=1505 audit(1284817153.711:5):  operation="profile_load" pid=1228 name="/usr/share/gdm/guest-session/Xsession"
Sep 18 15:39:13 SANJI kernel: [    8.928618] type=1505 audit(1284817153.711:6):  operation="profile_replace" pid=1229 name="/sbin/dhclient3"
Sep 18 15:39:13 SANJI kernel: [    8.928974] type=1505 audit(1284817153.711:7):  operation="profile_replace" pid=1229 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Sep 18 15:39:13 SANJI kernel: [    8.929197] type=1505 audit(1284817153.711:8):  operation="profile_replace" pid=1229 name="/usr/lib/connman/scripts/dhclient-script"
Sep 18 15:39:13 SANJI kernel: [    8.939032] AC'97 0 does not respond - RESET
Sep 18 15:39:13 SANJI kernel: [    8.939042] AC'97 0 access is not valid [0x0], removing mixer.
Sep 18 15:39:13 SANJI kernel: [    8.940264] EMU10K1_Audigy 0000:06:04.0: PCI INT A disabled
Sep 18 15:39:13 SANJI kernel: [    8.940271] EMU10K1_Audigy: probe of 0000:06:04.0 failed with error -5
Sep 18 15:39:13 SANJI kernel: [    8.968143] type=1505 audit(1284817153.751:9):  operation="profile_load" pid=1230 name="/usr/bin/evince"
Sep 18 15:39:13 SANJI kernel: [    8.972615] type=1505 audit(1284817153.751:10):  operation="profile_load" pid=1230 name="/usr/bin/evince-previewer"
Sep 18 15:39:13 SANJI kernel: [    8.975421] type=1505 audit(1284817153.751:11):  operation="profile_load" pid=1230 name="/usr/bin/evince-thumbnailer"


---

### Post by SirBartholomew on 2011-04-01
Did anybody get to the bottom of this? I'm trying to get my emu 1212m working and having the same problems.

---

### Post by bcschmerker on 2011-04-22
> **david.garcia.rojo said:**
> I've found that on sys.logYe might want to replace QUOTE with CODE, and /QUOTE with /CODE, as some of the characters in the data have been interpreted as emoticons. :-S

> **SirBartholomew said:**
> Did anybody get to the bottom of this? I'm trying to get my emu 1212m working and having the same problems.As of April 2011, I am uncertain about the status of support for the [E-MU®/Creative® 1010e](http://us.store.creative.com/) (Chipset uncertain, PCI-Express x4), which requires a different chipset from the earlier 1010 (CA0104 chipset, PCI 2.0; emu10k1x driver).  The 1212e, 1616e, 2020e, and 2424e are all dependent on functional drivers for the 1010e, which is the device that ties all the hardware to the host computer.

It is known that the [Advanced LinUX Sound Architecture Project](http://www.alsa-project.org/) has been dealing with major architectural issues in the CA20K1 PCI and CA20K2 PCI-Express chipsets (used in the Creative® Sound Blaster® X-Fi series, incl. the Titanium and Titanuim HD, plus the [Auzen X-Fi Forte 7.1 and Home Theater 7.1](http://www.auzentech.com/)) in the absence of support from Creative Technology, Ltd.; as of April 2011, they are still having problems with basic multichannel sound on both chipsets (whereas the CA0102 in my own SB0350 Sound Blaster® Audigy2 ZS runs good on the emu10k1 driver).

---

### Post by SirBartholomew on 2011-04-22
For some reason ubuntu recognizes my card as the creative card but alsa doesn't recognize it at all. I'm going to try the tutorial that is stickyed here on the top of multimedia and video. Searching around the net it would be the only thing I haven't tryed because I didn't see it until recently and haven't tried working with it in a few weeks. I only need 2 channels for recording because I just use it to take the recordings I make and put them into cd's and mp3s. I have a little usb with rca ins that works fine but it would still be nice to beable to mess around with the 1212m.

---

### Post by nightfever on 2011-04-28
I'm having no luck getting sound from a 1212m as well.
I've tried Fedora and IT WORKS.
So... what should we do?

---

### Post by SirBartholomew on 2011-04-28
Was it the newest version of fedora you were using?

---

### Post by nightfever on 2011-04-28
> **SirBartholomew said:**
> Was it the newest version of fedora you were using?
I've tried it a while ago, I think it was 14

---

### Post by nightfever on 2011-04-28
Allright, I did a clean 11.04 installation and recompiled alsa stuff.
But now:

```
root@bogdan-945PL-S3P:~# modprobe snd-emu10k1
FATAL: Error inserting snd (/lib/modules/2.6.38-8-generic/kernel/sound/acore/snd.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd
WARNING: Error inserting snd_util_mem (/lib/modules/2.6.38-8-generic/kernel/sound/synth/snd-util-mem.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_page_alloc (/lib/modules/2.6.38-8-generic/kernel/sound/acore/snd-page-alloc.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_timer (/lib/modules/2.6.38-8-generic/kernel/sound/acore/snd-timer.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_seq_device (/lib/modules/2.6.38-8-generic/kernel/sound/acore/seq/snd-seq-device.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_pcm (/lib/modules/2.6.38-8-generic/kernel/sound/acore/snd-pcm.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting ac97_bus (/lib/modules/2.6.38-8-generic/kernel/sound/misc/ac97_bus.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_ac97_codec (/lib/modules/2.6.38-8-generic/kernel/sound/pci/ac97/snd-ac97-codec.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_rawmidi (/lib/modules/2.6.38-8-generic/kernel/sound/acore/snd-rawmidi.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_emu10k1 (/lib/modules/2.6.38-8-generic/kernel/sound/pci/emu10k1/snd-emu10k1.ko): Unknown symbol in module, or unknown parameter (see dmesg)
root@bogdan-945PL-S3P:~# 

```

dmesg shows some errors:

```
[  630.789076] snd: Unknown symbol unregister_sound_special (err 0)
[  630.789495] snd: Unknown symbol register_sound_special_device (err 0)
[  630.791959] snd_hwdep: Unknown symbol snd_info_register (err 0)
[  630.792147] snd_hwdep: Unknown symbol snd_info_create_module_entry (err 0)
[  630.792479] snd_hwdep: Unknown symbol snd_info_free_entry (err 0)
[  630.792665] snd_hwdep: Unknown symbol snd_unregister_oss_device (err 0)
[  630.792848] snd_hwdep: Unknown symbol snd_register_oss_device (err 0)
[  630.793017] snd_hwdep: Unknown symbol snd_ctl_register_ioctl (err 0)
[  630.793176] snd_hwdep: Unknown symbol snd_card_file_add (err 0)
[  630.793347] snd_hwdep: Unknown symbol __snd_printk (err 0)
[  630.793506] snd_hwdep: Unknown symbol snd_iprintf (err 0)
[  630.793664] snd_hwdep: Unknown symbol snd_major (err 0)
[  630.793922] snd_hwdep: Unknown symbol snd_unregister_device (err 0)
[  630.794107] snd_hwdep: Unknown symbol snd_device_new (err 0)
[  630.794279] snd_hwdep: Unknown symbol snd_ctl_unregister_ioctl (err 0)
[  630.794480] snd_hwdep: Unknown symbol snd_lookup_oss_minor_data (err 0)
[  630.794649] snd_hwdep: Unknown symbol snd_lookup_minor_data (err 0)
[  630.794816] snd_hwdep: Unknown symbol snd_card_file_remove (err 0)
[  630.794975] snd_hwdep: Unknown symbol snd_register_device_for_dev (err 0)
[ 1229.319985] snd: Unknown symbol unregister_sound_special (err 0)
[ 1229.320450] snd: Unknown symbol register_sound_special_device (err 0)
[ 1229.322965] snd_hwdep: Unknown symbol snd_info_register (err 0)
[ 1229.323129] snd_hwdep: Unknown symbol snd_info_create_module_entry (err 0)
[ 1229.323337] snd_hwdep: Unknown symbol snd_info_free_entry (err 0)
[ 1229.323525] snd_hwdep: Unknown symbol snd_unregister_oss_device (err 0)
[ 1229.323709] snd_hwdep: Unknown symbol snd_register_oss_device (err 0)
[ 1229.323880] snd_hwdep: Unknown symbol snd_ctl_register_ioctl (err 0)
[ 1229.324082] snd_hwdep: Unknown symbol snd_card_file_add (err 0)
[ 1229.324273] snd_hwdep: Unknown symbol __snd_printk (err 0)
[ 1229.324434] snd_hwdep: Unknown symbol snd_iprintf (err 0)
[ 1229.324595] snd_hwdep: Unknown symbol snd_major (err 0)
[ 1229.324855] snd_hwdep: Unknown symbol snd_unregister_device (err 0)
[ 1229.325044] snd_hwdep: Unknown symbol snd_device_new (err 0)
[ 1229.325218] snd_hwdep: Unknown symbol snd_ctl_unregister_ioctl (err 0)
[ 1229.325419] snd_hwdep: Unknown symbol snd_lookup_oss_minor_data (err 0)
[ 1229.325590] snd_hwdep: Unknown symbol snd_lookup_minor_data (err 0)
[ 1229.325761] snd_hwdep: Unknown symbol snd_card_file_remove (err 0)
[ 1229.325923] snd_hwdep: Unknown symbol snd_register_device_for_dev (err 0)
root@bogdan-945PL-S3P:~# 

```

---

### Post by SirBartholomew on 2011-04-28
Still no joy on ubuntu???

---

### Post by aeuo on 2011-05-01
I have the same problem after alsa compilation as nightfever.
I have tried to compile alsa-drivers, libs, utils using gcc-4.4 & gcc-4.5 distributed with ubuntu 11.04, no result.
Please help...

---

### Post by aeuo on 2011-05-01
this link [https://help.ubuntu.com/community/HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto") does not help as the location of kernel modules are the same...

---

### Post by nightfever on 2011-05-02
I've managed to get sound out of my card by using a tool called "alsa upgrade" (it's here somewhere).
But I now get fast playback.
I've tried with .asoundrc file and no luck.
Any ideas?

---

### Post by lidex on 2011-05-03
Can you post this output please:
```
head -n 1 /proc/asound/card*/codec#*
```

---

### Post by hansdevr on 2011-05-15
Hi, just checked in again.. Still no luck with the E-mu 1212m PCIe...

What a waste, though!! I have been forced to create a windows partition, or else my money would have been wasted..

I'm dying to give the Linux DAW's a spin, but as long as it's a no go with the E-mu card, I'm stuck with Windows.... :(

---

### Post by david.garcia.rojo on 2011-11-05
> **hansdevr said:**
> Hi, just checked in again.. Still no luck with the E-mu 1212m PCIe...

What a waste, though!! I have been forced to create a windows partition, or else my money would have been wasted..

I'm dying to give the Linux DAW's a spin, but as long as it's a no go with the E-mu card, I'm stuck with Windows.... :(


Me too I'm now on ubuntu 11.10.
kernel change, alsa version change, alsa firmware is installed but I've exactly the same problem!!!!!!!!

It's incredible! I've googled for hours:
Every posts I've read have no solution and lots of posts no response!!!!

There is a bug when the module is loaded:

EMU10K1_Audigy 0000:06:04.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Audigy2 value: Special config.
AC'97 0 does not respond - RESET
AC'97 0 access is not valid [0x0], removing mixer.
EMU10K1_Audigy 0000:06:04.0: PCI INT A disabled
EMU10K1_Audigy: probe of 0000:06:04.0 failed with error -5

The device is not created and alsa cannot find it!

The device could work as it isn't a 1102:0004 model:
lspci -nn | grep audio
04:00.1 Audio device [0403]: ATI Technologies Inc HD48x0 audio [1002:aa30]
06:04.0 Multimedia audio controller [0401]: Creative Labs SB0400 Audigy2 Value [1102:0008]

so ubuntu see it but cannot use it.

Please correct this bug.

---

### Post by SirBartholomew on 2011-11-05
Yeah I keep crossing my fingers someone gets this fixed I bought this card about a year ago looked it up and it seemed like it was supported. Now it's just sitting there. I don't even have a copy of windows to create a partition to be able to use it.

---

### Post by david.garcia.rojo on 2011-11-20
Hi,

I've open a bug in launchpad.
If someone have the same problem, please add information to launchpad.
It could help this problem be solved.

[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/887309](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/887309)

---

### Post by hansdevr on 2011-12-14
Great! Thanks for handling that! Being a musician, I must admit I´m not into the tech side of stuff. But I still want to see a working card on my Kubuntu system!! I am dying to give Rosegarden and Ardour a spin!

---

### Post by hansdevr on 2013-01-01
> **hansdevr said:**
> Great! Thanks for handling that! Being a musician, I must admit I´m not into the tech side of stuff. But I still want to see a working card on my Kubuntu system!! I am dying to give Rosegarden and Ardour a spin!

So, now it is 2013.... Are there any drivers for Kubuntu for the 1212m already?!?

---

### Post by hansdevr on 2013-04-30
> **hansdevr said:**
> So, now it is 2013.... Are there any drivers for Kubuntu for the 1212m already?!?

Almost halfway 2013... (K)ubuntu 13.04 officially released... Still no sign of the 1212m...

Is everyone sleeping?!? There must be hundreds of dedicated (K)ubuntu users like me, waiting for these drivers...

---

### Post by SirBartholomew on 2013-04-30
Yeah, right now probably not much of a chance of getting these drivers. I'm over on the linuxmusicians forums and there is a lot of people there that really know what they are doing and you have a lot better chance of getting help there. I just picked up a M audio 1010 used for around 200 and got rid of the emu board I was trying to get to work. That has worked out well for me.

---

### Post by hansdevr on 2013-05-13
> **SirBartholomew said:**
> Yeah, right now probably not much of a chance of getting these drivers. I'm over on the linuxmusicians forums and there is a lot of people there that really know what they are doing and you have a lot better chance of getting help there. I just picked up a M audio 1010 used for around 200 and got rid of the emu board I was trying to get to work. That has worked out well for me.

Thanks for the tip. I'll definitely be checking those forums out!

---

