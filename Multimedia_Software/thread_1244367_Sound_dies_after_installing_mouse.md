---
title: "Sound dies after installing mouse"
date: 2009-08-19
forum: Multimedia Software
---

### Post by InvertedSaint on 2009-08-19
G'day. I've been using a bit of Linux at uni, and decided to give Ubuntu a go at home. Yesterday (The day of install) I had everything working, except the mouse (It's a G5 and has a bunch of extra buttons. All cured with appending some stuff to /etc/X11/xorg.conf).
Now, I know that sound was working when I got home today, but at some point, I've managed to kill it.

Here is the output of the commands recommended on the help page ([https://help.ubuntu.com/community/SoundTroubleshooting):]("https://help.ubuntu.com/community/SoundTroubleshooting%29:")

aplay -l
```
aplay: device_list:217: no soundcards found...
```find /lib/modules/`uname -r` | grep snd
```

/lib/modules/2.6.28-15-generic/kernel/sound/acore/snd-pcm.ko
/lib/modules/2.6.28-15-generic/kernel/sound/acore/seq/snd-seq-dummy.ko
/lib/modules/2.6.28-15-generic/kernel/sound/acore/seq/snd-seq-midi-event.ko
/lib/modules/2.6.28-15-generic/kernel/sound/acore/seq/oss/snd-seq-oss.ko
/lib/modules/2.6.28-15-generic/kernel/sound/acore/seq/snd-seq.ko
/lib/modules/2.6.28-15-generic/kernel/sound/acore/seq/snd-seq-midi.ko
/lib/modules/2.6.28-15-generic/kernel/sound/acore/seq/snd-seq-device.ko
/lib/modules/2.6.28-15-generic/kernel/sound/acore/seq/snd-seq-virmidi.ko
/lib/modules/2.6.28-15-generic/kernel/sound/acore/seq/snd-seq-midi-emul.ko
/lib/modules/2.6.28-15-generic/kernel/sound/acore/oss/snd-mixer-oss.ko
/lib/modules/2.6.28-15-generic/kernel/sound/acore/oss/snd-pcm-oss.ko
/lib/modules/2.6.28-15-generic/kernel/sound/acore/snd-page-alloc.ko
/lib/modules/2.6.28-15-generic/kernel/sound/acore/snd-rawmidi.ko
/lib/modules/2.6.28-15-generic/kernel/sound/acore/snd.ko
/lib/modules/2.6.28-15-generic/kernel/sound/acore/snd-hwdep.ko
/lib/modules/2.6.28-15-generic/kernel/sound/acore/snd-hrtimer.ko
/lib/modules/2.6.28-15-generic/kernel/sound/acore/snd-timer.ko
/lib/modules/2.6.28-15-generic/kernel/sound/pci/mixart/snd-mixart.ko
/lib/modules/2.6.28-15-generic/kernel/sound/pci/hda/snd-hda-codec-conexant.ko
/lib/modules/2.6.28-15-generic/kernel/sound/pci/hda/snd-hda-codec-realtek.ko
/lib/modules/2.6.28-15-generic/kernel/sound/pci/hda/snd-hda-intel.ko
/lib/modules/2.6.28-15-generic/kernel/sound/pci/hda/snd-hda-codec-atihdmi.ko
/lib/modules/2.6.28-15-generic/kernel/sound/pci/hda/snd-hda-codec-via.ko
/lib/modules/2.6.28-15-generic/kernel/sound/pci/hda/snd-hda-codec-nvhdmi.ko
/lib/modules/2.6.28-15-generic/kernel/sound/pci/hda/snd-hda-codec-analog.ko
/lib/modules/2.6.28-15-generic/kernel/sound/pci/hda/snd-hda-codec-intelhdmi.ko
/lib/modules/2.6.28-15-generic/kernel/sound/pci/hda/snd-hda-codec-idt.ko
/lib/modules/2.6.28-15-generic/kernel/sound/pci/hda/snd-hda-codec-si3054.ko
/lib/modules/2.6.28-15-generic/kernel/sound/pci/hda/snd-hda-codec-cmedia.ko
/lib/modules/2.6.28-15-generic/kernel/sound/pci/hda/snd-hda-codec.ko
/lib/modules/2.6.28-15-generic/kernel/sound/pci/snd-ad1889.ko
/lib/modules/2.6.28-15-generic/kernel/sound/pci/au88x0/snd-au8810.ko
/lib/modules/2.6.28-15-generic/kernel/sound/pci/au88x0/snd-au8820.ko
/lib/modules/2.6.28-15-generic/kernel/sound/pci/au88x0/snd-au8830.ko
/lib/modules/2.6.28-15-generic/kernel/sound/pci/snd-intel8x0m.ko
/lib/modules/2.6.28-15-generic/kernel/sound/pci/nm256/snd-nm256.ko
/lib/modules/2.6.28-15-generic/kernel/sound/pci/snd-ens1371.ko
/lib/modules/2.6.28-15-generic/kernel/sound/pci/snd-ens1370.ko
/lib/modules/2.6.28-15-generic/kernel/sound/pci/snd-cs5530.ko
/lib/modules/2.6.28-15-generic/kernel/sound/pci/snd-sonicvibes.ko
/lib/modules/2.6.28-15-generic/kernel/sound/pci/korg1212/snd-korg1212.ko
/lib/modules/2.6.28-15-generic/kernel/sound/pci/cs46xx/snd-cs46xx.ko
/lib/modules/2.6.28-15-generic/kernel/sound/pci/snd-via82xx.ko
/lib/modules/2.6.28-15-generic/kernel/sound/pci/snd-maestro3.ko
/lib/modules/2.6.28-15-generic/kernel/sound/pci/snd-bt87x.ko
/lib/modules/2.6.28-15-generic/kernel/sound/pci/snd-es1938.ko
/lib/modules/2.6.28-15-generic/kernel/sound/pci/snd-fm801.ko
/lib/modules/2.6.28-15-generic/kernel/sound/pci/ymfpci/snd-ymfpci.ko
/lib/modules/2.6.28-15-generic/kernel/sound/pci/snd-rme96.ko
/lib/modules/2.6.28-15-generic/kernel/sound/pci/asihpi/snd-asihpi.ko
/lib/modules/2.6.28-15-generic/kernel/sound/pci/ali5451/snd-ali5451.ko
/lib/modules/2.6.28-15-generic/kernel/sound/pci/snd-cmipci.ko
/lib/modules/2.6.28-15-generic/kernel/sound/pci/snd-atiixp.ko
/lib/modules/2.6.28-15-generic/kernel/sound/pci/snd-cs4281.ko
/lib/modules/2.6.28-15-generic/kernel/sound/pci/aw2/snd-aw2.ko
/lib/modules/2.6.28-15-generic/kernel/sound/pci/vx222/snd-vx222.ko
/lib/modules/2.6.28-15-generic/kernel/sound/pci/snd-als4000.ko
/lib/modules/2.6.28-15-generic/kernel/sound/pci/trident/snd-trident.ko
/lib/modules/2.6.28-15-generic/kernel/sound/pci/snd-via82xx-modem.ko
/lib/modules/2.6.28-15-generic/kernel/sound/pci/oxygen/snd-oxygen-lib.ko
/lib/modules/2.6.28-15-generic/kernel/sound/pci/oxygen/snd-hifier.ko
/lib/modules/2.6.28-15-generic/kernel/sound/pci/oxygen/snd-oxygen.ko
/lib/modules/2.6.28-15-generic/kernel/sound/pci/oxygen/snd-virtuoso.ko
/lib/modules/2.6.28-15-generic/kernel/sound/pci/snd-rme32.ko
/lib/modules/2.6.28-15-generic/kernel/sound/pci/snd-es1968.ko
/lib/modules/2.6.28-15-generic/kernel/sound/pci/echoaudio/snd-mona.ko
/lib/modules/2.6.28-15-generic/kernel/sound/pci/echoaudio/snd-layla24.ko
/lib/modules/2.6.28-15-generic/kernel/sound/pci/echoaudio/snd-gina20.ko
/lib/modules/2.6.28-15-generic/kernel/sound/pci/echoaudio/snd-indigoiox.ko
/lib/modules/2.6.28-15-generic/kernel/sound/pci/echoaudio/snd-indigodj.ko
/lib/modules/2.6.28-15-generic/kernel/sound/pci/echoaudio/snd-layla20.ko
/lib/modules/2.6.28-15-generic/kernel/sound/pci/echoaudio/snd-echo3g.ko
/lib/modules/2.6.28-15-generic/kernel/sound/pci/echoaudio/snd-indigoio.ko
/lib/modules/2.6.28-15-generic/kernel/sound/pci/echoaudio/snd-gina24.ko
/lib/modules/2.6.28-15-generic/kernel/sound/pci/echoaudio/snd-darla24.ko
/lib/modules/2.6.28-15-generic/kernel/sound/pci/echoaudio/snd-indigodjx.ko
/lib/modules/2.6.28-15-generic/kernel/sound/pci/echoaudio/snd-darla20.ko
/lib/modules/2.6.28-15-generic/kernel/sound/pci/echoaudio/snd-indigo.ko
/lib/modules/2.6.28-15-generic/kernel/sound/pci/echoaudio/snd-mia.ko
/lib/modules/2.6.28-15-generic/kernel/sound/pci/snd-als300.ko
/lib/modules/2.6.28-15-generic/kernel/sound/pci/snd-intel8x0.ko
/lib/modules/2.6.28-15-generic/kernel/sound/pci/emu10k1/snd-emu10k1x.ko
/lib/modules/2.6.28-15-generic/kernel/sound/pci/emu10k1/snd-emu10k1-synth.ko
/lib/modules/2.6.28-15-generic/kernel/sound/pci/emu10k1/snd-emu10k1.ko
/lib/modules/2.6.28-15-generic/kernel/sound/pci/cs5535audio/snd-cs5535audio.ko
/lib/modules/2.6.28-15-generic/kernel/sound/pci/snd-atiixp-modem.ko
/lib/modules/2.6.28-15-generic/kernel/sound/pci/pdplus/snd-pdplus.ko
/lib/modules/2.6.28-15-generic/kernel/sound/pci/snd-sis7019.ko
/lib/modules/2.6.28-15-generic/kernel/sound/pci/rme9652/snd-hdspm.ko
/lib/modules/2.6.28-15-generic/kernel/sound/pci/rme9652/snd-rme9652.ko
/lib/modules/2.6.28-15-generic/kernel/sound/pci/rme9652/snd-hdsp.ko
/lib/modules/2.6.28-15-generic/kernel/sound/pci/snd-azt3328.ko
/lib/modules/2.6.28-15-generic/kernel/sound/pci/ac97/snd-ac97-codec.ko
/lib/modules/2.6.28-15-generic/kernel/sound/pci/ice1712/snd-ice1712.ko
/lib/modules/2.6.28-15-generic/kernel/sound/pci/ice1712/snd-ice17xx-ak4xxx.ko
/lib/modules/2.6.28-15-generic/kernel/sound/pci/ice1712/snd-ice1724.ko
/lib/modules/2.6.28-15-generic/kernel/sound/pci/ca0106/snd-ca0106.ko
/lib/modules/2.6.28-15-generic/kernel/sound/pci/riptide/snd-riptide.ko
/lib/modules/2.6.28-15-generic/kernel/sound/pci/pcxhr/snd-pcxhr.ko
/lib/modules/2.6.28-15-generic/kernel/sound/synth/snd-util-mem.ko
/lib/modules/2.6.28-15-generic/kernel/sound/synth/emux/snd-emux-synth.ko
/lib/modules/2.6.28-15-generic/kernel/sound/soc/codecs/snd-soc-tlv320aic23.ko
/lib/modules/2.6.28-15-generic/kernel/sound/soc/codecs/snd-soc-wm8750.ko
/lib/modules/2.6.28-15-generic/kernel/sound/soc/codecs/snd-soc-wm8971.ko
/lib/modules/2.6.28-15-generic/kernel/sound/soc/codecs/snd-soc-wm8731.ko
/lib/modules/2.6.28-15-generic/kernel/sound/soc/codecs/snd-soc-ak4535.ko
/lib/modules/2.6.28-15-generic/kernel/sound/soc/codecs/snd-soc-tlv320aic3x.ko
/lib/modules/2.6.28-15-generic/kernel/sound/soc/codecs/snd-soc-wm8990.ko
/lib/modules/2.6.28-15-generic/kernel/sound/soc/codecs/snd-soc-wm8900.ko
/lib/modules/2.6.28-15-generic/kernel/sound/soc/codecs/snd-soc-tlv320aic26.ko
/lib/modules/2.6.28-15-generic/kernel/sound/soc/codecs/snd-soc-wm8510.ko
/lib/modules/2.6.28-15-generic/kernel/sound/soc/codecs/snd-soc-wm8903.ko
/lib/modules/2.6.28-15-generic/kernel/sound/soc/codecs/snd-soc-uda1380.ko
/lib/modules/2.6.28-15-generic/kernel/sound/soc/codecs/snd-soc-wm8580.ko
/lib/modules/2.6.28-15-generic/kernel/sound/soc/codecs/snd-soc-cs4270.ko
/lib/modules/2.6.28-15-generic/kernel/sound/soc/codecs/snd-soc-wm8753.ko
/lib/modules/2.6.28-15-generic/kernel/sound/soc/codecs/snd-soc-ssm2602.ko
/lib/modules/2.6.28-15-generic/kernel/sound/soc/codecs/snd-soc-ad73311.ko
/lib/modules/2.6.28-15-generic/kernel/sound/soc/snd-soc-core.ko
/lib/modules/2.6.28-15-generic/kernel/sound/drivers/vx/snd-vx-lib.ko
/lib/modules/2.6.28-15-generic/kernel/sound/drivers/snd-virmidi.ko
/lib/modules/2.6.28-15-generic/kernel/sound/drivers/snd-mtpav.ko
/lib/modules/2.6.28-15-generic/kernel/sound/drivers/snd-dummy.ko
/lib/modules/2.6.28-15-generic/kernel/sound/drivers/pcsp/snd-pcsp.ko
/lib/modules/2.6.28-15-generic/kernel/sound/drivers/snd-portman2x4.ko
/lib/modules/2.6.28-15-generic/kernel/sound/drivers/snd-aloop.ko
/lib/modules/2.6.28-15-generic/kernel/sound/drivers/snd-serial-u16550.ko
/lib/modules/2.6.28-15-generic/kernel/sound/drivers/mpu401/snd-mpu401.ko
/lib/modules/2.6.28-15-generic/kernel/sound/drivers/mpu401/snd-mpu401-uart.ko
/lib/modules/2.6.28-15-generic/kernel/sound/drivers/snd-mts64.ko
/lib/modules/2.6.28-15-generic/kernel/sound/drivers/opl3/snd-opl3-lib.ko
/lib/modules/2.6.28-15-generic/kernel/sound/drivers/opl3/snd-opl3-synth.ko
/lib/modules/2.6.28-15-generic/kernel/sound/drivers/opl4/snd-opl4-synth.ko
/lib/modules/2.6.28-15-generic/kernel/sound/drivers/opl4/snd-opl4-lib.ko
/lib/modules/2.6.28-15-generic/kernel/sound/oss/msnd_pinnacle.ko
/lib/modules/2.6.28-15-generic/kernel/sound/oss/msnd_classic.ko
/lib/modules/2.6.28-15-generic/kernel/sound/oss/msnd.ko
/lib/modules/2.6.28-15-generic/kernel/sound/core/snd-pcm.ko
/lib/modules/2.6.28-15-generic/kernel/sound/core/seq/snd-seq-dummy.ko
/lib/modules/2.6.28-15-generic/kernel/sound/core/seq/snd-seq-midi-event.ko
/lib/modules/2.6.28-15-generic/kernel/sound/core/seq/oss/snd-seq-oss.ko
/lib/modules/2.6.28-15-generic/kernel/sound/core/seq/snd-seq.ko
/lib/modules/2.6.28-15-generic/kernel/sound/core/seq/snd-seq-midi.ko
/lib/modules/2.6.28-15-generic/kernel/sound/core/seq/snd-seq-device.ko
/lib/modules/2.6.28-15-generic/kernel/sound/core/seq/snd-seq-virmidi.ko
/lib/modules/2.6.28-15-generic/kernel/sound/core/seq/snd-seq-midi-emul.ko
/lib/modules/2.6.28-15-generic/kernel/sound/core/oss/snd-mixer-oss.ko
/lib/modules/2.6.28-15-generic/kernel/sound/core/oss/snd-pcm-oss.ko
/lib/modules/2.6.28-15-generic/kernel/sound/core/snd-page-alloc.ko
/lib/modules/2.6.28-15-generic/kernel/sound/core/snd-rawmidi.ko
/lib/modules/2.6.28-15-generic/kernel/sound/core/snd.ko
/lib/modules/2.6.28-15-generic/kernel/sound/core/snd-hwdep.ko
/lib/modules/2.6.28-15-generic/kernel/sound/core/snd-timer.ko
/lib/modules/2.6.28-15-generic/kernel/sound/usb/caiaq/snd-usb-caiaq.ko
/lib/modules/2.6.28-15-generic/kernel/sound/usb/snd-usb-audio.ko
/lib/modules/2.6.28-15-generic/kernel/sound/usb/usx2y/snd-usb-usx2y.ko
/lib/modules/2.6.28-15-generic/kernel/sound/usb/usx2y/snd-usb-us122l.ko
/lib/modules/2.6.28-15-generic/kernel/sound/usb/snd-usb-lib.ko
/lib/modules/2.6.28-15-generic/kernel/sound/i2c/snd-i2c.ko
/lib/modules/2.6.28-15-generic/kernel/sound/i2c/snd-cs8427.ko
/lib/modules/2.6.28-15-generic/kernel/sound/i2c/other/snd-ak4114.ko
/lib/modules/2.6.28-15-generic/kernel/sound/i2c/other/snd-pt2258.ko
/lib/modules/2.6.28-15-generic/kernel/sound/i2c/other/snd-tea575x-tuner.ko
/lib/modules/2.6.28-15-generic/kernel/sound/i2c/other/snd-ak4117.ko
/lib/modules/2.6.28-15-generic/kernel/sound/i2c/other/snd-ak4xxx-adda.ko
/lib/modules/2.6.28-15-generic/kernel/sound/i2c/snd-tea6330t.ko
/lib/modules/2.6.28-15-generic/kernel/sound/isa/sb/snd-sb16-csp.ko
/lib/modules/2.6.28-15-generic/kernel/sound/isa/sb/snd-sb8.ko
/lib/modules/2.6.28-15-generic/kernel/sound/isa/sb/snd-es968.ko
/lib/modules/2.6.28-15-generic/kernel/sound/isa/sb/snd-sb16.ko
/lib/modules/2.6.28-15-generic/kernel/sound/isa/sb/snd-sb8-dsp.ko
/lib/modules/2.6.28-15-generic/kernel/sound/isa/sb/snd-sb-common.ko
/lib/modules/2.6.28-15-generic/kernel/sound/isa/sb/snd-emu8000-synth.ko
/lib/modules/2.6.28-15-generic/kernel/sound/isa/sb/snd-sbawe.ko
/lib/modules/2.6.28-15-generic/kernel/sound/isa/sb/snd-sb16-dsp.ko
/lib/modules/2.6.28-15-generic/kernel/sound/isa/snd-opl3sa2.ko
/lib/modules/2.6.28-15-generic/kernel/sound/isa/snd-als100.ko
/lib/modules/2.6.28-15-generic/kernel/sound/isa/snd-es18xx.ko
/lib/modules/2.6.28-15-generic/kernel/sound/isa/msnd
/lib/modules/2.6.28-15-generic/kernel/sound/isa/msnd/snd-msnd-lib.ko
/lib/modules/2.6.28-15-generic/kernel/sound/isa/msnd/snd-msnd-classic.ko
/lib/modules/2.6.28-15-generic/kernel/sound/isa/msnd/snd-msnd-pinnacle.ko
/lib/modules/2.6.28-15-generic/kernel/sound/isa/wss/snd-wss-lib.ko
/lib/modules/2.6.28-15-generic/kernel/sound/isa/cs423x/snd-cs4232.ko
/lib/modules/2.6.28-15-generic/kernel/sound/isa/cs423x/snd-cs4236.ko
/lib/modules/2.6.28-15-generic/kernel/sound/isa/cs423x/snd-cs4236-lib.ko
/lib/modules/2.6.28-15-generic/kernel/sound/isa/cs423x/snd-cs4231.ko
/lib/modules/2.6.28-15-generic/kernel/sound/isa/opti9xx/snd-miro.ko
/lib/modules/2.6.28-15-generic/kernel/sound/isa/opti9xx/snd-opti93x.ko
/lib/modules/2.6.28-15-generic/kernel/sound/isa/opti9xx/snd-opti92x-ad1848.ko
/lib/modules/2.6.28-15-generic/kernel/sound/isa/opti9xx/snd-opti92x-cs4231.ko
/lib/modules/2.6.28-15-generic/kernel/sound/isa/snd-cmi8330.ko
/lib/modules/2.6.28-15-generic/kernel/sound/isa/snd-sscape.ko
/lib/modules/2.6.28-15-generic/kernel/sound/isa/wavefront/snd-wavefront.ko
/lib/modules/2.6.28-15-generic/kernel/sound/isa/es1688/snd-es1688-lib.ko
/lib/modules/2.6.28-15-generic/kernel/sound/isa/es1688/snd-es1688.ko
/lib/modules/2.6.28-15-generic/kernel/sound/isa/ad1848/snd-ad1848.ko
/lib/modules/2.6.28-15-generic/kernel/sound/isa/snd-adlib.ko
/lib/modules/2.6.28-15-generic/kernel/sound/isa/ad1816a/snd-ad1816a.ko
/lib/modules/2.6.28-15-generic/kernel/sound/isa/gus/snd-gusextreme.ko
/lib/modules/2.6.28-15-generic/kernel/sound/isa/gus/snd-gusclassic.ko
/lib/modules/2.6.28-15-generic/kernel/sound/isa/gus/snd-gusmax.ko
/lib/modules/2.6.28-15-generic/kernel/sound/isa/gus/snd-interwave.ko
/lib/modules/2.6.28-15-generic/kernel/sound/isa/gus/snd-interwave-stb.ko
/lib/modules/2.6.28-15-generic/kernel/sound/isa/gus/snd-gus-lib.ko
/lib/modules/2.6.28-15-generic/kernel/sound/isa/snd-sc6000.ko
/lib/modules/2.6.28-15-generic/kernel/sound/isa/snd-dt019x.ko
/lib/modules/2.6.28-15-generic/kernel/sound/isa/snd-sgalaxy.ko
/lib/modules/2.6.28-15-generic/kernel/sound/isa/snd-azt2320.ko
/lib/modules/2.6.28-15-generic/kernel/sound/pcmcia/vx/snd-vxpocket.ko
/lib/modules/2.6.28-15-generic/kernel/sound/pcmcia/pdaudiocf/snd-pdaudiocf.ko

```lspci -v | less
```

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller
 (rev 02)
        Subsystem: Giga-byte Technology Device a002
        Flags: bus master, fast devsel, latency 0, IRQ 9
        Memory at fa200000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel modules: snd-hda-intel

```In typing this, I realised "lspci -v" has a line "Capabilities: <access denied>". That's probably something important ><.
Any help is appreciated.

Edit: Nope. With "sudo lspci -v | less" I can get
```

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
        Subsystem: Giga-byte Technology Device a002
        Flags: bus master, fast devsel, latency 0, IRQ 9
        Memory at fa200000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
        Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
        Capabilities: [100] Virtual Channel <?>
        Capabilities: [130] Root Complex Link <?>
        Kernel modules: snd-hda-intel

```

---

### Post by InvertedSaint on 2009-08-22
Anyone?

---

### Post by InvertedSaint on 2009-09-09
Seriously, why will no-one answer? :(

---

