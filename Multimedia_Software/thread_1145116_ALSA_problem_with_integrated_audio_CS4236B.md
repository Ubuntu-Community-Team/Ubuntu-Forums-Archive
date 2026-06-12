---
title: "ALSA problem with integrated audio CS4236B"
date: 2009-05-01
forum: Multimedia Software
---

### Post by David Brant on 2009-05-01
Hello.

My speaker icon displays the CS4236B ALSA Mixer. However, i can only play sounds with the OSS settings in system/preference/sound. All other settings (Autodetect, ALSA and PulseAudio) don't work or just hang.

I would like to get ALSA working if possible.

Ubunto SoundTroubleShooting suggested the following steps:

```
david@david-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: CS4236B [CS4236B], device 0: CS4231 [CS4236B]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

System recognises soundcard

```
david@david-desktop:~$ find /lib/modules/`uname -r` | grep snd
/lib/modules/2.6.27-7-generic/kernel/ubuntu/misc/media/snd-bt-sco.ko
/lib/modules/2.6.27-7-generic/kernel/sound/soc/snd-soc-core.ko
/lib/modules/2.6.27-7-generic/kernel/sound/i2c/snd-tea6330t.ko
/lib/modules/2.6.27-7-generic/kernel/sound/i2c/snd-cs8427.ko
/lib/modules/2.6.27-7-generic/kernel/sound/i2c/snd-i2c.ko
/lib/modules/2.6.27-7-generic/kernel/sound/i2c/other/snd-ak4117.ko
/lib/modules/2.6.27-7-generic/kernel/sound/i2c/other/snd-ak4114.ko
/lib/modules/2.6.27-7-generic/kernel/sound/i2c/other/snd-pt2258.ko
/lib/modules/2.6.27-7-generic/kernel/sound/i2c/other/snd-ak4xxx-adda.ko
/lib/modules/2.6.27-7-generic/kernel/sound/i2c/other/snd-tea575x-tuner.ko
/lib/modules/2.6.27-7-generic/kernel/sound/usb/caiaq/snd-usb-caiaq.ko
/lib/modules/2.6.27-7-generic/kernel/sound/usb/usx2y/snd-usb-usx2y.ko
/lib/modules/2.6.27-7-generic/kernel/sound/usb/snd-usb-lib.ko
/lib/modules/2.6.27-7-generic/kernel/sound/usb/snd-usb-audio.ko
/lib/modules/2.6.27-7-generic/kernel/sound/isa/es1688/snd-es1688.ko
/lib/modules/2.6.27-7-generic/kernel/sound/isa/es1688/snd-es1688-lib.ko
/lib/modules/2.6.27-7-generic/kernel/sound/isa/snd-sscape.ko
/lib/modules/2.6.27-7-generic/kernel/sound/isa/wavefront/snd-wavefront.ko
/lib/modules/2.6.27-7-generic/kernel/sound/isa/snd-adlib.ko
/lib/modules/2.6.27-7-generic/kernel/sound/isa/snd-es18xx.ko
/lib/modules/2.6.27-7-generic/kernel/sound/isa/snd-dt019x.ko
/lib/modules/2.6.27-7-generic/kernel/sound/isa/sb/snd-sb8-dsp.ko
/lib/modules/2.6.27-7-generic/kernel/sound/isa/sb/snd-sb16-dsp.ko
/lib/modules/2.6.27-7-generic/kernel/sound/isa/sb/snd-sb-common.ko
/lib/modules/2.6.27-7-generic/kernel/sound/isa/sb/snd-sb16.ko
/lib/modules/2.6.27-7-generic/kernel/sound/isa/sb/snd-sbawe.ko
/lib/modules/2.6.27-7-generic/kernel/sound/isa/sb/snd-sb16-csp.ko
/lib/modules/2.6.27-7-generic/kernel/sound/isa/sb/snd-emu8000-synth.ko
/lib/modules/2.6.27-7-generic/kernel/sound/isa/sb/snd-es968.ko
/lib/modules/2.6.27-7-generic/kernel/sound/isa/sb/snd-sb8.ko
/lib/modules/2.6.27-7-generic/kernel/sound/isa/gus/snd-gus-lib.ko
/lib/modules/2.6.27-7-generic/kernel/sound/isa/gus/snd-gusclassic.ko
/lib/modules/2.6.27-7-generic/kernel/sound/isa/gus/snd-interwave.ko
/lib/modules/2.6.27-7-generic/kernel/sound/isa/gus/snd-gusextreme.ko
/lib/modules/2.6.27-7-generic/kernel/sound/isa/gus/snd-gusmax.ko
/lib/modules/2.6.27-7-generic/kernel/sound/isa/gus/snd-interwave-stb.ko
/lib/modules/2.6.27-7-generic/kernel/sound/isa/ad1848/snd-ad1848.ko
/lib/modules/2.6.27-7-generic/kernel/sound/isa/ad1848/snd-ad1848-lib.ko
/lib/modules/2.6.27-7-generic/kernel/sound/isa/snd-als100.ko
**[COLOR="Red"]/lib/modules/2.6.27-7-generic/kernel/sound/isa/cs423x/snd-cs4236-lib.ko[/COLOR]**
/lib/modules/2.6.27-7-generic/kernel/sound/isa/cs423x/snd-cs4232.ko
/lib/modules/2.6.27-7-generic/kernel/sound/isa/cs423x/snd-cs4231.ko
/lib/modules/2.6.27-7-generic/kernel/sound/isa/cs423x/snd-cs4231-lib.ko
**[COLOR="Red"]/lib/modules/2.6.27-7-generic/kernel/sound/isa/cs423x/snd-cs4236.ko[/COLOR]**
/lib/modules/2.6.27-7-generic/kernel/sound/isa/ad1816a/snd-ad1816a.ko
/lib/modules/2.6.27-7-generic/kernel/sound/isa/snd-azt2320.ko
/lib/modules/2.6.27-7-generic/kernel/sound/isa/snd-sgalaxy.ko
/lib/modules/2.6.27-7-generic/kernel/sound/isa/snd-sc6000.ko
/lib/modules/2.6.27-7-generic/kernel/sound/isa/opti9xx/snd-miro.ko
/lib/modules/2.6.27-7-generic/kernel/sound/isa/opti9xx/snd-opti93x.ko
/lib/modules/2.6.27-7-generic/kernel/sound/isa/opti9xx/snd-opti92x-ad1848.ko
/lib/modules/2.6.27-7-generic/kernel/sound/isa/opti9xx/snd-opti92x-cs4231.ko
/lib/modules/2.6.27-7-generic/kernel/sound/isa/snd-cmi8330.ko
/lib/modules/2.6.27-7-generic/kernel/sound/isa/snd-opl3sa2.ko
/lib/modules/2.6.27-7-generic/kernel/sound/core/snd.ko
/lib/modules/2.6.27-7-generic/kernel/sound/core/snd-pcm.ko
/lib/modules/2.6.27-7-generic/kernel/sound/core/seq/snd-seq-dummy.ko
/lib/modules/2.6.27-7-generic/kernel/sound/core/seq/snd-seq.ko
/lib/modules/2.6.27-7-generic/kernel/sound/core/seq/snd-seq-virmidi.ko
/lib/modules/2.6.27-7-generic/kernel/sound/core/seq/snd-seq-midi.ko
/lib/modules/2.6.27-7-generic/kernel/sound/core/seq/snd-seq-device.ko
/lib/modules/2.6.27-7-generic/kernel/sound/core/seq/snd-seq-midi-emul.ko
/lib/modules/2.6.27-7-generic/kernel/sound/core/seq/oss/snd-seq-oss.ko
/lib/modules/2.6.27-7-generic/kernel/sound/core/seq/snd-seq-midi-event.ko
/lib/modules/2.6.27-7-generic/kernel/sound/core/snd-timer.ko
/lib/modules/2.6.27-7-generic/kernel/sound/core/snd-page-alloc.ko
/lib/modules/2.6.27-7-generic/kernel/sound/core/snd-hwdep.ko
/lib/modules/2.6.27-7-generic/kernel/sound/core/oss/snd-mixer-oss.ko
/lib/modules/2.6.27-7-generic/kernel/sound/core/oss/snd-pcm-oss.ko
/lib/modules/2.6.27-7-generic/kernel/sound/core/snd-rawmidi.ko
/lib/modules/2.6.27-7-generic/kernel/sound/pci/snd-rme96.ko
/lib/modules/2.6.27-7-generic/kernel/sound/pci/riptide/snd-riptide.ko
/lib/modules/2.6.27-7-generic/kernel/sound/pci/trident/snd-trident.ko
/lib/modules/2.6.27-7-generic/kernel/sound/pci/snd-ens1370.ko
/lib/modules/2.6.27-7-generic/kernel/sound/pci/snd-intel8x0.ko
/lib/modules/2.6.27-7-generic/kernel/sound/pci/mixart/snd-mixart.ko
/lib/modules/2.6.27-7-generic/kernel/sound/pci/snd-atiixp.ko
/lib/modules/2.6.27-7-generic/kernel/sound/pci/snd-sonicvibes.ko
/lib/modules/2.6.27-7-generic/kernel/sound/pci/pcxhr/snd-pcxhr.ko
/lib/modules/2.6.27-7-generic/kernel/sound/pci/ali5451/snd-ali5451.ko
/lib/modules/2.6.27-7-generic/kernel/sound/pci/aw2/snd-aw2.ko
/lib/modules/2.6.27-7-generic/kernel/sound/pci/snd-bt87x.ko
/lib/modules/2.6.27-7-generic/kernel/sound/pci/snd-intel8x0m.ko
/lib/modules/2.6.27-7-generic/kernel/sound/pci/snd-cmipci.ko
/lib/modules/2.6.27-7-generic/kernel/sound/pci/snd-sis7019.ko
/lib/modules/2.6.27-7-generic/kernel/sound/pci/snd-es1938.ko
/lib/modules/2.6.27-7-generic/kernel/sound/pci/snd-atiixp-modem.ko
/lib/modules/2.6.27-7-generic/kernel/sound/pci/snd-fm801.ko
/lib/modules/2.6.27-7-generic/kernel/sound/pci/snd-als4000.ko
/lib/modules/2.6.27-7-generic/kernel/sound/pci/oxygen/snd-virtuoso.ko
/lib/modules/2.6.27-7-generic/kernel/sound/pci/oxygen/snd-oxygen.ko
/lib/modules/2.6.27-7-generic/kernel/sound/pci/oxygen/snd-oxygen-lib.ko
/lib/modules/2.6.27-7-generic/kernel/sound/pci/oxygen/snd-hifier.ko
/lib/modules/2.6.27-7-generic/kernel/sound/pci/ca0106/snd-ca0106.ko
/lib/modules/2.6.27-7-generic/kernel/sound/pci/snd-cs4281.ko
/lib/modules/2.6.27-7-generic/kernel/sound/pci/emu10k1/snd-emu10k1x.ko
/lib/modules/2.6.27-7-generic/kernel/sound/pci/emu10k1/snd-emu10k1-synth.ko
/lib/modules/2.6.27-7-generic/kernel/sound/pci/emu10k1/snd-emu10k1.ko
/lib/modules/2.6.27-7-generic/kernel/sound/pci/snd-ens1371.ko
/lib/modules/2.6.27-7-generic/kernel/sound/pci/au88x0/snd-au8830.ko
/lib/modules/2.6.27-7-generic/kernel/sound/pci/au88x0/snd-au8810.ko
/lib/modules/2.6.27-7-generic/kernel/sound/pci/au88x0/snd-au8820.ko
/lib/modules/2.6.27-7-generic/kernel/sound/pci/nm256/snd-nm256.ko
/lib/modules/2.6.27-7-generic/kernel/sound/pci/snd-via82xx.ko
/lib/modules/2.6.27-7-generic/kernel/sound/pci/snd-via82xx-modem.ko
/lib/modules/2.6.27-7-generic/kernel/sound/pci/cs46xx/snd-cs46xx.ko
/lib/modules/2.6.27-7-generic/kernel/sound/pci/snd-es1968.ko
/lib/modules/2.6.27-7-generic/kernel/sound/pci/rme9652/snd-rme9652.ko
/lib/modules/2.6.27-7-generic/kernel/sound/pci/rme9652/snd-hdspm.ko
/lib/modules/2.6.27-7-generic/kernel/sound/pci/rme9652/snd-hdsp.ko
/lib/modules/2.6.27-7-generic/kernel/sound/pci/ac97/snd-ac97-codec.ko
/lib/modules/2.6.27-7-generic/kernel/sound/pci/cs5535audio/snd-cs5535audio.ko
/lib/modules/2.6.27-7-generic/kernel/sound/pci/snd-cs5530.ko
/lib/modules/2.6.27-7-generic/kernel/sound/pci/snd-maestro3.ko
/lib/modules/2.6.27-7-generic/kernel/sound/pci/vx222/snd-vx222.ko
/lib/modules/2.6.27-7-generic/kernel/sound/pci/echoaudio/snd-darla24.ko
/lib/modules/2.6.27-7-generic/kernel/sound/pci/echoaudio/snd-mia.ko
/lib/modules/2.6.27-7-generic/kernel/sound/pci/echoaudio/snd-indigoio.ko
/lib/modules/2.6.27-7-generic/kernel/sound/pci/echoaudio/snd-gina20.ko
/lib/modules/2.6.27-7-generic/kernel/sound/pci/echoaudio/snd-echo3g.ko
/lib/modules/2.6.27-7-generic/kernel/sound/pci/echoaudio/snd-layla24.ko
/lib/modules/2.6.27-7-generic/kernel/sound/pci/echoaudio/snd-gina24.ko
/lib/modules/2.6.27-7-generic/kernel/sound/pci/echoaudio/snd-indigodj.ko
/lib/modules/2.6.27-7-generic/kernel/sound/pci/echoaudio/snd-darla20.ko
/lib/modules/2.6.27-7-generic/kernel/sound/pci/echoaudio/snd-mona.ko
/lib/modules/2.6.27-7-generic/kernel/sound/pci/echoaudio/snd-indigo.ko
/lib/modules/2.6.27-7-generic/kernel/sound/pci/echoaudio/snd-layla20.ko
/lib/modules/2.6.27-7-generic/kernel/sound/pci/korg1212/snd-korg1212.ko
/lib/modules/2.6.27-7-generic/kernel/sound/pci/snd-azt3328.ko
/lib/modules/2.6.27-7-generic/kernel/sound/pci/ice1712/snd-ice1712.ko
/lib/modules/2.6.27-7-generic/kernel/sound/pci/ice1712/snd-ice1724.ko
/lib/modules/2.6.27-7-generic/kernel/sound/pci/ice1712/snd-ice17xx-ak4xxx.ko
/lib/modules/2.6.27-7-generic/kernel/sound/pci/snd-rme32.ko
/lib/modules/2.6.27-7-generic/kernel/sound/pci/hda/snd-hda-intel.ko
/lib/modules/2.6.27-7-generic/kernel/sound/pci/ymfpci/snd-ymfpci.ko
/lib/modules/2.6.27-7-generic/kernel/sound/pci/snd-als300.ko
/lib/modules/2.6.27-7-generic/kernel/sound/pci/snd-ad1889.ko
/lib/modules/2.6.27-7-generic/kernel/sound/pcmcia/pdaudiocf/snd-pdaudiocf.ko
/lib/modules/2.6.27-7-generic/kernel/sound/pcmcia/vx/snd-vxpocket.ko
/lib/modules/2.6.27-7-generic/kernel/sound/drivers/opl3/snd-opl3-synth.ko
/lib/modules/2.6.27-7-generic/kernel/sound/drivers/opl3/snd-opl3-lib.ko
/lib/modules/2.6.27-7-generic/kernel/sound/drivers/snd-serial-u16550.ko
/lib/modules/2.6.27-7-generic/kernel/sound/drivers/pcsp/snd-pcsp.ko
/lib/modules/2.6.27-7-generic/kernel/sound/drivers/opl4/snd-opl4-lib.ko
/lib/modules/2.6.27-7-generic/kernel/sound/drivers/opl4/snd-opl4-synth.ko
/lib/modules/2.6.27-7-generic/kernel/sound/drivers/snd-mts64.ko
/lib/modules/2.6.27-7-generic/kernel/sound/drivers/snd-virmidi.ko
/lib/modules/2.6.27-7-generic/kernel/sound/drivers/vx/snd-vx-lib.ko
/lib/modules/2.6.27-7-generic/kernel/sound/drivers/mpu401/snd-mpu401-uart.ko
/lib/modules/2.6.27-7-generic/kernel/sound/drivers/mpu401/snd-mpu401.ko
/lib/modules/2.6.27-7-generic/kernel/sound/drivers/snd-dummy.ko
/lib/modules/2.6.27-7-generic/kernel/sound/drivers/snd-mtpav.ko
/lib/modules/2.6.27-7-generic/kernel/sound/drivers/snd-portman2x4.ko
/lib/modules/2.6.27-7-generic/kernel/sound/oss/msnd_pinnacle.ko
/lib/modules/2.6.27-7-generic/kernel/sound/oss/msnd.ko
/lib/modules/2.6.27-7-generic/kernel/sound/oss/msnd_classic.ko
/lib/modules/2.6.27-7-generic/kernel/sound/synth/snd-util-mem.ko
/lib/modules/2.6.27-7-generic/kernel/sound/synth/emux/snd-emux-synth.ko
```

Sound modules are installed in kernel

```
david@david-desktop:~$ lspci -v | less

00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 02)
        Flags: bus master, medium devsel, latency 64
        Memory at f0000000 (32-bit, prefetchable) [size=64M]
        Capabilities: <access denied>
        Kernel driver in use: agpgart-intel
        Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 02)
        Flags: bus master, 66MHz, medium devsel, latency 64
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
        I/O behind bridge: 0000e000-0000efff
        Memory behind bridge: fc000000-feffffff
        Prefetchable memory behind bridge: f6000000-f6ffffff
        Kernel modules: shpchp

00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
        Flags: bus master, medium devsel, latency 0

00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01) (prog-if 80 [Master])
        Flags: bus master, medium devsel, latency 32
        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
        I/O ports at ffa0 [size=16]
        Kernel driver in use: ata_piix
        Kernel modules: ata_piix

00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
        Flags: bus master, medium devsel, latency 64, IRQ 11
        I/O ports at cce0 [size=32]
        Kernel driver in use: uhci_hcd
        Kernel modules: uhci-hcd

00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
        Flags: medium devsel, IRQ 9
        Kernel modules: i2c-piix4

00:0d.0 Ethernet controller: Marvell Technology Group Ltd. 88W8361 [TopDog] 802.11n Wireless (rev 03)
        Subsystem: Belkin Device 800a
        Flags: bus master, 66MHz, medium devsel, latency 240, IRQ 10
        Memory at ff010000 (32-bit, non-prefetchable) [size=64K]
        Memory at ff000000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>
        Kernel driver in use: ndiswrapper

00:0e.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 61)
        Subsystem: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
        Flags: bus master, medium devsel, latency 64, IRQ 11
        I/O ports at ccc0 [size=32]
        Capabilities: <access denied>
        Kernel driver in use: uhci_hcd
        Kernel modules: uhci-hcd

00:0e.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 61)
        Subsystem: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
        Flags: bus master, medium devsel, latency 64, IRQ 11
        I/O ports at cca0 [size=32]
        Capabilities: <access denied>
        Kernel driver in use: uhci_hcd
        Kernel modules: uhci-hcd

00:0e.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 63) (prog-if 20)
        Subsystem: VIA Technologies, Inc. USB 2.0
        Flags: bus master, medium devsel, latency 64, IRQ 10
        Memory at ff020800 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>
        Kernel driver in use: ehci_hcd
        Kernel modules: ehci-hcd

00:0e.3 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev 46) (prog-if 10)
        Subsystem: VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller
        Flags: bus master, medium devsel, latency 64, IRQ 11
        Memory at ff020000 (32-bit, non-prefetchable) [size=2K]
        I/O ports at cc00 [size=128]
        Capabilities: <access denied>
        Kernel driver in use: ohci1394
        Kernel modules: ohci1394

00:0f.0 PCI bridge: Digital Equipment Corporation DECchip 21152 (rev 03)
        Flags: bus master, medium devsel, latency 64
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=64
        I/O behind bridge: 0000d000-0000dfff
        Memory behind bridge: fa000000-fbffffff
        Prefetchable memory behind bridge: 00000000f5000000-00000000f5ffffff
        Capabilities: <access denied>
        Kernel modules: shpchp

01:00.0 VGA compatible controller: ATI Technologies Inc 3D Rage Pro AGP 1X/2X (rev 5c)
        Subsystem: Dell Device 0082
        Flags: bus master, stepping, medium devsel, latency 64, IRQ 11
        Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
        I/O ports at ec00 [size=256]
        Memory at fcfff000 (32-bit, non-prefetchable) [size=4K]
        [virtual] Expansion ROM at f6000000 [disabled] [size=128K]
        Capabilities: <access denied>
        Kernel modules: atyfb

02:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
        Subsystem: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+
        Flags: bus master, medium devsel, latency 64, IRQ 11
        I/O ports at dc00 [size=256]
        Memory at fafffc00 (32-bit, non-prefetchable) [size=256]
        Expansion ROM at fb000000 [disabled] [size=64K]
        Capabilities: <access denied>
        Kernel driver in use: 8139too
        Kernel modules: 8139cp, 8139too

(END) 
```

No reference to Audio device for built in soundcard even though BIOS has it enabled!

If i run utility to check if ALSA is running correct module

```
david@david-desktop:~$ wget -O alsa-info.sh http://alsa-project.org/alsa-info.sh && bash ./alsa-info.sh

--2009-05-01 15:29:52--  http://alsa-project.org/alsa-info.sh
Resolving alsa-project.org... 212.20.107.51
Connecting to alsa-project.org|212.20.107.51|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh [following]
--2009-05-01 15:29:52--  http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh
Resolving git.alsa-project.org... 212.20.107.51
Reusing existing connection to alsa-project.org:80.
HTTP request sent, awaiting response... 200 OK
Length: 26428 (26K) [text/plain]
Saving to: `alsa-info.sh'

100%[===================================================================================================>] 26,428      65.8K/s   in 0.4s    

2009-05-01 15:29:53 (65.8 KB/s) - `alsa-info.sh' saved [26428/26428]

ALSA Information Script v 0.4.56
--------------------------------

This script will collect information about your ALSA installation and sound related hardware, to help diagnose your problem.

By default, the collected information will be AUTOMATICALLY uploaded to a www.alsa-project.org site.
If you do not wish for this to occur, run the script with the --no-upload argument

Do you want to run this script? [y/n] : y
													Uploading information to www.alsa-project.org ...  Done!

Your ALSA information is located at 
Please inform the person helping you.
```

Not very informative is it!!!

From the ALSA project homepage, it says i must turn on the sound support soundcore module. To check this i get the following:

```
david@david-desktop:~$ modinfo soundcore
filename:       /lib/modules/2.6.27-7-generic/kernel/sound/soundcore.ko
alias:          char-major-14-*
license:        GPL
author:         Alan Cox
description:    Core sound module
srcversion:     E4F49ED9C4CFD1A5A923330
depends:        
vermagic:       2.6.27-7-generic SMP mod_unload modversions 586 
```

Does this mean i have the module?
If so, what do i do now?

Finally several other thread suggested commands reveal the following:

```
david@david-desktop:~$ cat /proc/asound/cards
 0 [CS4236B        ]: CS4236B - CS4236B
                      CS4236B at 0x534, irq 5, dma 1&3
```

```
david@david-desktop:~$ ls -la /dev/snd
total 0
drwxr-xr-x   2 root root     180 2009-04-30 12:22 .
drwxr-xr-x  14 root root   13960 2009-04-30 17:10 ..
crw-rw----   1 root audio 116, 8 2009-04-30 12:22 controlC0
crw-rw----   1 root audio 116, 5 2009-04-30 12:22 hwC0D0
crw-rw----   1 root audio 116, 4 2009-04-30 12:22 midiC0D0
crw-rw----   1 root audio 116, 7 2009-04-30 12:22 pcmC0D0c
crw-rw----   1 root audio 116, 6 2009-04-30 12:22 pcmC0D0p
crw-rw----+  1 root audio 116, 3 2009-04-30 12:22 seq
crw-rw----+  1 root audio 116, 2 2009-04-30 12:22 timer
```

```
david@david-desktop:~$ lsof |grep snd
gconf-hel 4896      david  mem       REG        8,5   357520  502142 /usr/lib/libsndfile.so.1.0.17
mixer_app 4987      david   22r      CHR      116,8            12794 /dev/snd/controlC0

```

Now i'm really stuck and confused. Any further help or tips would be greatly appreciated.

Dave

---

### Post by David Brant on 2009-05-08
Had no luck over the last week trying to get ALSA working, so decided to plumb for OSS, even though the Crystal CS4236 isn't listed in the OSS devices list.

```
ali5455	pci10b9,5455	ALI M5455
allegro	pci125d,1988	ESS Allegro ES1988
allegro	pci125d,1990	ESS Canyon 3D ES1990
allegro	pci125d,1992	ESS Canyon 3D-2 ES1992
allegro	pci125d,1998	ESS Maestro3 ES1998
allegro	pci125d,199a	ESS Maestro3 ES199A
als300	pci4005,300	Avance Logic ALS300
als300	pci4005,308	Avance Logic ALS300+
als4000	pci4005,4000	Avance Logic ALS4000
apci97	pci1102,8938	Creative Ectiva EV1938
apci97	pci1274,1371	Creative AudioPCI97 (ES1371/ES1373)
apci97	pci1274,5880	Creative Sound Blaster PCI128 (5880B)
apci97	pci1274,8001	Creative Sound Blaster PCI128 (CT5880)
apci97	pci1274,8002	Creative Sound Blaster PCI128 (5880A)
atiaudio	pci1002,4341	ATI IXP200
atiaudio	pci1002,4361	ATI IXP300
atiaudio	pci1002,4370	ATI IXP400
audigyls	pci1102,7	Sound Blaster Audigy LS / Live7.1
audioloop	AUDIOLOOP	OSS loopback audio driver
audiopci	pci1274,5000	Creative AudioPCI (ES1370)
cmi8788	pci13f6,8788	CMedia CMI8788
cmpci	pci13f6,100	C-Media CM8338A
cmpci	pci13f6,100	MIDIMan DiO 2448
cmpci	pci13f6,101	CMedia CM8338B
cmpci	pci13f6,111	CMedia CM8738/CM8768
cmpci	pci14af,20	Guillemot Maxi Sound MUSE
cs4280	pci1013,6001	Crystal CS4610
cs4280	pci1013,6003	Crystal CS4280 
cs4280	pci1013,6004	Crystal CS4615
cs4280	pcs153b,112e	Terratec DMX Xfire 1024
cs4280	pcs1681,50	Hercules Game Theater XP
cs4280	pcs1681,51	Hercules Game Theater XP+
cs4280	pcs5053,3357	TurtleBeach SantaCruz / VideoLogic SonicFury
cs4281	pci1013,6005	Crystal CS4281
digi32	pciea60,9896	RME Digi32
digi32	pciea60,9897	RME Digi32 Pro
digi32	pciea60,9898	RME Digi32/8
digi96	pci10ee,3fc0	RME Digi96
digi96	pci10ee,3fc1	RME Digi96/8
digi96	pci10ee,3fc2	RME Digi96/8 PRO
digi96	pci10ee,3fc3	RME Digi96/8 PAD
emu10k1x	pci1102,6	Creative Sound Blaster 5.1 (Dell)
envy24ht	pci1412,1724	Generic ENVY24HT based sound card
envy24ht	pcs1412,3630	M Audio Revolution 7.1
envy24ht	pcs1412,3631	M Audio Revolution 5.1
envy24ht	pcs1412,6321	M Audio Audiophile 192
envy24ht	pcs153b,1145	Terratec Aureon 7.1 Space
envy24ht	pcs153b,1147	Terratec Aureon 7.1 Sky
envy24ht	pcs153b,1149	Terratec PHASE 28
envy24ht	pcs153b,1153	Terratec Aureon 7.1 Universe
envy24ht	pcs3031,4553	Ego Systems Juli@ (BETA)
envy24ht	pcs4933,4553	Audiotrak Prodigy 7.1
envy24	pci1412,1712	Generic ENVY24 based device
envy24	pcs1412,d630	M Audio Delta 1010
envy24	pcs1412,d631	M Audio Delta DiO 2496
envy24	pcs1412,d632	M Audio Delta 66
envy24	pcs1412,d633	M Audio Delta 44
envy24	pcs1412,d634	M Audio Audiophile 2496
envy24	pcs1412,d635	M Audio Delta TDIF
envy24	pcs1412,d638	M Audio Delta 410
envy24	pcs1412,d63b	M Audio Delta 1010LT
envy24	pcs153b,1115	Terratec EWS88MT
envy24	pcs153b,112b	Terratec EWS88D
envy24	pcs153b,1130	Terratec EWX 24/96
envy24	pcs153b,1138	Terratec DMX 6Fire
fm801	pci1319,801	ForteMedia FM 801
fm801	pcs1489,7008	Genius Sound Maker Live
geode	pci100b,503	National Semiconductor Geode SC1200
geode	pci1078,103	National Semiconductor Geode CS5530
hdaudio	pci8086,2668	Intel High Definition Audio (ICH6)
hdaudio	pci8086,27d8	Intel High Definition Audio (ICH7)
hdaudio	pci8086,269a	Intel High Definition Audio (ESB2)
hdaudio	pci8086,284b	Intel High Definition Audio (ICH8)
hdaudio	pci8086,293e	Intel High Definition Audio (P35)
hdaudio	pci8086,293f	Intel High Definition Audio (ICH9)
hdaudio	pci10de,26c	Nvidia High Definition Audio (MCP51)
hdaudio	pci10de,371	Nvidia High Definition Audio (MCP55)
hdaudio	pci10de,3e4	Nvidia High Definition Audio (MCP61)
hdaudio	pci10de,3f0	Nvidia High Definition Audio (MCP61)
hdaudio	pci10de,44a	Nvidia High Definition Audio (MCP65)
hdaudio	pci10de,55c	Nvidia High Definition Audio (MCP67)
hdaudio	pci1002,437b	ATI High Definition Audio (SB450)
hdaudio	pci1002,4383	ATI High Definition Audio (SB600)
hdaudio	pci1106,3288	VIA High Definition Audio
hdaudio	pci1039,7502	SiS High Definition Audio
hdaudio	pci10b9,5461	ULI High Definition Audio
hdsp	pci10ee,3fc5	RME Hammerfall (not supported yet)
ich	pci1022,7445	AMD 786
ich	pci1022,746d	AMD 8111 
ich	pci1039,7012	SiS 7012 
ich	pci10de,1b1	Nvidia nForce
ich	pci10de,3a	Nvidia MCP4
ich	pci10de,6a	Nvidia nForce2
ich	pci10de,8a	Nvidia CK8
ich	pci10de,da	Nvidia nForce3
ich	pci10de,ea	Nvidia CK8S
ich	pci10de,59	Nvidia nForce4
ich	pci10de,26b	Nvidia MCP51
ich	pci8086,2415	Intel AC97 (ICH)
ich	pci8086,2425	Intel AC97 (ICH1)
ich	pci8086,2445	Intel AC97 (ICH2)
ich	pci8086,2485	Intel AC97 (ICH3)
ich	pci8086,24c5	Intel AC97 (ICH4)
ich	pci8086,24d5	Intel AC97 (ICH5)
ich	pci8086,25a6	Intel AC97 (ESB)
ich	pci8086,266e	Intel AC97 (ICH6)
ich	pci8086,27de	Intel AC97 (ICH7)
ich	pci8086,7195	Intel 440MX (440MX)
imux	IMUX	OSS Input Multiplexer 
lynxone	pci10b5,1142	LynxONE Studio Interface
lynxtwo	pci1621,20	LynxTWO-A Studio Interface
lynxtwo	pci1621,21	LynxTWO-B Studio Interface
lynxtwo	pci1621,22	LynxTWO-C Studio Interface
lynxtwo	pci1621,23	Lynx-L22 Studio Interface
lynxtwo	pci1621,24	Lynx AES16 Studio Interface
lynxtwo	pci1621,25	Lynx AES16-SRC Studio Interface
maestro	pci125d,1968	ESS Maestro-2 
maestro	pci125d,1978	ESS Maestro-2E 
maestro	pci1285,100	ESS Maestro-1 
neomagic	pci10c8,8005	Neomagic NM2200AV
ossusb	usbif,class1	Generic USB audio device (BETA)
ossusb	usbif41e,3000	Creative Sound Blaster Extigy (BETA)
ossusb	usbif41e,3010	Creative Sound Blaster MP3+ USB
ossusb	usbif41e,3020	Creative Audigy2 NX USB (BETA)
ossusb	usbif46d,8b2	Logitec Quickcam Pro 4000 (mic) (BETA)
ossusb	usbif46d,a01	Logitec USB Headset
ossusb	usbif471,311	Philips ToUcam Pro (mic) (BETA)
ossusb	usbif672,1041	Labtec LCS1040 Speaker System (BETA)
ossusb	usbifd8c,c	C-Media USB audio adapter - model1
ossusb	usbifd8c,103	C-Media USB audio adapter - model2
ossusb	usbifd8c,102	C-Media 2/4/6/8ch USB audio adapter (BETA)
ossusb	usbif6f8,c000	Hercules Gamesurround MUSE Pocket
ossusb	usbif763,2001	M Audio USB AudioSport Quatro (BETA)
ossusb	usbif763,2002	M Audio USB AudioSport Duo (BETA)
ossusb	usbif763,2007	M Audio Sonica Theater USB (BETA)
ossusb	usbif763,200d	M Audio OmniStudio USB (BETA)
ossusb	usbif763,2805	M Audio Sonica USB (BETA)
riptide	pci127a,4310	Conexant Riptide 
riptide	pci127a,4320	Conexant Riptide
s3vibes	pci5333,ca00	S3 Sonic Vibes
sblive	pci1102,2	Creative Sound Blaster Live 
sblive	pcs1102,8040	Creative Sound Blaster Live 1024/Platinum
sblive	pcs1102,8061	Creative Sound Blaster Live 5.1/Platinum IR
sblive	pci1102,4	Creative Sound Blaster Audigy/Audigy2
sblive	pcs1102,51	Creative Sound Blaster Audigy Platinum
sblive	pci1102,8	Creative Sound Blaster Audigy2 Value/Audigy4
sblive	pci1102,2001	Creative Sound Blaster Audigy2 ZS PCMCIA
sbxfi	pci1102,5	Creative SB X-Fi (EARLY BETA)
softoss	SOFTOSS	OSS Virtual mixer/synth driver
solo	pci125d,1969	ESS Solo-1 
sonorus	pci1057,1801	Sonorus STUDI/O
trident	pci1023,2000	Trident 4DWave-DX
trident	pci1023,2001	Trident 4DWave-NX
trident	pci1023,2002	Trident 4DWave-CX
trident	pci1039,7018	SiS 7018 
trident	pci10b9,5451	ALI M5451
via8233	pci1106,3059	VIA VT8233/8235/8237 
via8233	pci1106,4551	VIA VT5432B 
via8233	pci1106,7059	VIA VT8233A 
via8233	pcs1462,3800	MSI K7T266
via8233	pcs1462,4720	MSI KT3 Ultra 
via97	pci1106,3058	VIA VT82C686 
vmix	VMIX	OSS Transparent Virtual Mixing Architecture
vortex	pci12eb,1	Aureal Vortex (AU8820)
vortex	pci12eb,2	Aureal Vortex2 (AU8830)
vortex	AU8810		Aureal Vortex Advantage (AU8810)  *** NOT SUPPORTED ***
ymf7xx	pci1073,10	Yamaha DS-XG YMF744 
ymf7xx	pci1073,12	Yamaha DS-XG YMF754
ymf7xx	pci1073,4	Yamaha DS-XG YMF724
ymf7xx	pci1073,5	Yamaha DS-XG YMF734
ymf7xx	pci1073,a	Yamaha DS-XG YMF740
ymf7xx	pci1073,c	Yamaha DS-XG YMF740C
ymf7xx	pci1073,d	Yamaha DS-XG YMF724F
```

The following thread produced a result! :)

[http://ubuntuforums.org/showthread.php?t=873749](http://ubuntuforums.org/showthread.php?t=873749)

Many thanks to Temüjin

I'm still not sure what it is i'm running with (OSS or ALSA) because i have to set everything to OSS in sysyem/preference/sounds to satisfy desktop sounds, music and flash even though i can run with the ALSA or OSS mixer. I selected ALSA, only because it has more options.

---

