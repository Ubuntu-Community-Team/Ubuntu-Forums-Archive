---
title: "Ubuntu 10.10 and Lenovo B560 sound problems"
date: 2010-11-13
forum: Multimedia Software
---

### Post by kik on 2010-11-13
I have Lenovo B560 and Ubuntu 10.10 and there is no sound.
Someone fixed sound, but then wifi stoped working: [http://ubuntuforums.org/showthread.php?p=10111370](http://ubuntuforums.org/showthread.php?p=10111370)

> 
lspci -v:
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
	Subsystem: Lenovo Device 38af
	Flags: fast devsel, IRQ 7
	Memory at f2800000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel modules: snd-hda-intel
aplay -l: "aplay: device_list:235: no soundcards found..."
cat /proc/asound/modules: ""
grep 'audio' /etc/group: ```
audio:x:29:pulse
```
find /lib/modules/`uname -r` | grep snd
```

/lib/modules/2.6.35-22-generic/kernel/sound/core/snd.ko
/lib/modules/2.6.35-22-generic/kernel/sound/core/snd-pcm.ko
/lib/modules/2.6.35-22-generic/kernel/sound/core/snd-page-alloc.ko
/lib/modules/2.6.35-22-generic/kernel/sound/core/snd-hrtimer.ko
/lib/modules/2.6.35-22-generic/kernel/sound/core/snd-hwdep.ko
/lib/modules/2.6.35-22-generic/kernel/sound/core/snd-rawmidi.ko
/lib/modules/2.6.35-22-generic/kernel/sound/core/seq/snd-seq-midi-event.ko
/lib/modules/2.6.35-22-generic/kernel/sound/core/seq/snd-seq-midi-emul.ko
/lib/modules/2.6.35-22-generic/kernel/sound/core/seq/snd-seq-device.ko
/lib/modules/2.6.35-22-generic/kernel/sound/core/seq/snd-seq-virmidi.ko
/lib/modules/2.6.35-22-generic/kernel/sound/core/seq/snd-seq.ko
/lib/modules/2.6.35-22-generic/kernel/sound/core/seq/snd-seq-dummy.ko
/lib/modules/2.6.35-22-generic/kernel/sound/core/seq/snd-seq-midi.ko
/lib/modules/2.6.35-22-generic/kernel/sound/core/snd-timer.ko
/lib/modules/2.6.35-22-generic/kernel/sound/usb/snd-usb-audio.ko
/lib/modules/2.6.35-22-generic/kernel/sound/usb/usx2y/snd-usb-usx2y.ko
/lib/modules/2.6.35-22-generic/kernel/sound/usb/usx2y/snd-usb-us122l.ko
/lib/modules/2.6.35-22-generic/kernel/sound/usb/caiaq/snd-usb-caiaq.ko
/lib/modules/2.6.35-22-generic/kernel/sound/usb/snd-usbmidi-lib.ko
/lib/modules/2.6.35-22-generic/kernel/sound/usb/misc/snd-ua101.ko
/lib/modules/2.6.35-22-generic/kernel/sound/drivers/snd-mts64.ko
/lib/modules/2.6.35-22-generic/kernel/sound/drivers/snd-portman2x4.ko
/lib/modules/2.6.35-22-generic/kernel/sound/drivers/vx/snd-vx-lib.ko
/lib/modules/2.6.35-22-generic/kernel/sound/drivers/mpu401/snd-mpu401-uart.ko
/lib/modules/2.6.35-22-generic/kernel/sound/drivers/mpu401/snd-mpu401.ko
/lib/modules/2.6.35-22-generic/kernel/sound/drivers/snd-mtpav.ko
/lib/modules/2.6.35-22-generic/kernel/sound/drivers/snd-dummy.ko
/lib/modules/2.6.35-22-generic/kernel/sound/drivers/opl3/snd-opl3-lib.ko
/lib/modules/2.6.35-22-generic/kernel/sound/drivers/opl3/snd-opl3-synth.ko
/lib/modules/2.6.35-22-generic/kernel/sound/drivers/opl4/snd-opl4-synth.ko
/lib/modules/2.6.35-22-generic/kernel/sound/drivers/opl4/snd-opl4-lib.ko
/lib/modules/2.6.35-22-generic/kernel/sound/drivers/snd-virmidi.ko
/lib/modules/2.6.35-22-generic/kernel/sound/drivers/pcsp/snd-pcsp.ko
/lib/modules/2.6.35-22-generic/kernel/sound/drivers/snd-serial-u16550.ko
/lib/modules/2.6.35-22-generic/kernel/sound/synth/emux/snd-emux-synth.ko
/lib/modules/2.6.35-22-generic/kernel/sound/synth/snd-util-mem.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pcmcia/vx/snd-vxpocket.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pcmcia/pdaudiocf/snd-pdaudiocf.ko
/lib/modules/2.6.35-22-generic/kernel/sound/isa/es1688/snd-es1688-lib.ko
/lib/modules/2.6.35-22-generic/kernel/sound/isa/es1688/snd-es1688.ko
/lib/modules/2.6.35-22-generic/kernel/sound/isa/msnd
/lib/modules/2.6.35-22-generic/kernel/sound/isa/msnd/snd-msnd-pinnacle.ko
/lib/modules/2.6.35-22-generic/kernel/sound/isa/msnd/snd-msnd-classic.ko
/lib/modules/2.6.35-22-generic/kernel/sound/isa/msnd/snd-msnd-lib.ko
/lib/modules/2.6.35-22-generic/kernel/sound/isa/snd-sscape.ko
/lib/modules/2.6.35-22-generic/kernel/sound/isa/snd-azt2320.ko
/lib/modules/2.6.35-22-generic/kernel/sound/isa/opti9xx/snd-opti92x-ad1848.ko
/lib/modules/2.6.35-22-generic/kernel/sound/isa/opti9xx/snd-opti92x-cs4231.ko
/lib/modules/2.6.35-22-generic/kernel/sound/isa/opti9xx/snd-opti93x.ko
/lib/modules/2.6.35-22-generic/kernel/sound/isa/opti9xx/snd-miro.ko
/lib/modules/2.6.35-22-generic/kernel/sound/isa/snd-sgalaxy.ko
/lib/modules/2.6.35-22-generic/kernel/sound/isa/snd-cmi8330.ko
/lib/modules/2.6.35-22-generic/kernel/sound/isa/cs423x/snd-cs4236.ko
/lib/modules/2.6.35-22-generic/kernel/sound/isa/cs423x/snd-cs4231.ko
/lib/modules/2.6.35-22-generic/kernel/sound/isa/snd-es18xx.ko
/lib/modules/2.6.35-22-generic/kernel/sound/isa/ad1816a/snd-ad1816a.ko
/lib/modules/2.6.35-22-generic/kernel/sound/isa/wss/snd-wss-lib.ko
/lib/modules/2.6.35-22-generic/kernel/sound/isa/snd-opl3sa2.ko
/lib/modules/2.6.35-22-generic/kernel/sound/isa/snd-als100.ko
/lib/modules/2.6.35-22-generic/kernel/sound/isa/snd-sc6000.ko
/lib/modules/2.6.35-22-generic/kernel/sound/isa/wavefront/snd-wavefront.ko
/lib/modules/2.6.35-22-generic/kernel/sound/isa/gus/snd-interwave.ko
/lib/modules/2.6.35-22-generic/kernel/sound/isa/gus/snd-interwave-stb.ko
/lib/modules/2.6.35-22-generic/kernel/sound/isa/gus/snd-gusextreme.ko
/lib/modules/2.6.35-22-generic/kernel/sound/isa/gus/snd-gusclassic.ko
/lib/modules/2.6.35-22-generic/kernel/sound/isa/gus/snd-gus-lib.ko
/lib/modules/2.6.35-22-generic/kernel/sound/isa/gus/snd-gusmax.ko
/lib/modules/2.6.35-22-generic/kernel/sound/isa/snd-adlib.ko
/lib/modules/2.6.35-22-generic/kernel/sound/isa/sb/snd-sbawe.ko
/lib/modules/2.6.35-22-generic/kernel/sound/isa/sb/snd-sb16-dsp.ko
/lib/modules/2.6.35-22-generic/kernel/sound/isa/sb/snd-emu8000-synth.ko
/lib/modules/2.6.35-22-generic/kernel/sound/isa/sb/snd-sb8-dsp.ko
/lib/modules/2.6.35-22-generic/kernel/sound/isa/sb/snd-sb16-csp.ko
/lib/modules/2.6.35-22-generic/kernel/sound/isa/sb/snd-jazz16.ko
/lib/modules/2.6.35-22-generic/kernel/sound/isa/sb/snd-sb16.ko
/lib/modules/2.6.35-22-generic/kernel/sound/isa/sb/snd-sb-common.ko
/lib/modules/2.6.35-22-generic/kernel/sound/isa/sb/snd-sb8.ko
/lib/modules/2.6.35-22-generic/kernel/sound/isa/ad1848/snd-ad1848.ko
/lib/modules/2.6.35-22-generic/kernel/sound/soc/snd-soc-core.ko
/lib/modules/2.6.35-22-generic/kernel/sound/soc/codecs/snd-soc-wm8580.ko
/lib/modules/2.6.35-22-generic/kernel/sound/soc/codecs/snd-soc-wm8750.ko
/lib/modules/2.6.35-22-generic/kernel/sound/soc/codecs/snd-soc-wm8727.ko
/lib/modules/2.6.35-22-generic/kernel/sound/soc/codecs/snd-soc-ak4104.ko
/lib/modules/2.6.35-22-generic/kernel/sound/soc/codecs/snd-soc-wm8753.ko
/lib/modules/2.6.35-22-generic/kernel/sound/soc/codecs/snd-soc-wm8993.ko
/lib/modules/2.6.35-22-generic/kernel/sound/soc/codecs/snd-soc-wm8728.ko
/lib/modules/2.6.35-22-generic/kernel/sound/soc/codecs/snd-soc-wm8971.ko
/lib/modules/2.6.35-22-generic/kernel/sound/soc/codecs/snd-soc-wm8978.ko
/lib/modules/2.6.35-22-generic/kernel/sound/soc/codecs/snd-soc-wm8940.ko
/lib/modules/2.6.35-22-generic/kernel/sound/soc/codecs/snd-soc-wm8974.ko
/lib/modules/2.6.35-22-generic/kernel/sound/soc/codecs/snd-soc-twl4030.ko
/lib/modules/2.6.35-22-generic/kernel/sound/soc/codecs/snd-soc-ad193x.ko
/lib/modules/2.6.35-22-generic/kernel/sound/soc/codecs/snd-soc-wm2000.ko
/lib/modules/2.6.35-22-generic/kernel/sound/soc/codecs/snd-soc-uda1380.ko
/lib/modules/2.6.35-22-generic/kernel/sound/soc/codecs/snd-soc-wm-hubs.ko
/lib/modules/2.6.35-22-generic/kernel/sound/soc/codecs/snd-soc-wm8961.ko
/lib/modules/2.6.35-22-generic/kernel/sound/soc/codecs/snd-soc-wm8523.ko
/lib/modules/2.6.35-22-generic/kernel/sound/soc/codecs/snd-soc-ak4535.ko
/lib/modules/2.6.35-22-generic/kernel/sound/soc/codecs/snd-soc-wm8776.ko
/lib/modules/2.6.35-22-generic/kernel/sound/soc/codecs/snd-soc-tpa6130a2.ko
/lib/modules/2.6.35-22-generic/kernel/sound/soc/codecs/snd-soc-ak4671.ko
/lib/modules/2.6.35-22-generic/kernel/sound/soc/codecs/snd-soc-cs4270.ko
/lib/modules/2.6.35-22-generic/kernel/sound/soc/codecs/snd-soc-ad73311.ko
/lib/modules/2.6.35-22-generic/kernel/sound/soc/codecs/snd-soc-twl6040.ko
/lib/modules/2.6.35-22-generic/kernel/sound/soc/codecs/snd-soc-wm8990.ko
/lib/modules/2.6.35-22-generic/kernel/sound/soc/codecs/snd-soc-wm9081.ko
/lib/modules/2.6.35-22-generic/kernel/sound/soc/codecs/snd-soc-uda134x.ko
/lib/modules/2.6.35-22-generic/kernel/sound/soc/codecs/snd-soc-wm8955.ko
/lib/modules/2.6.35-22-generic/kernel/sound/soc/codecs/snd-soc-l3.ko
/lib/modules/2.6.35-22-generic/kernel/sound/soc/codecs/snd-soc-tlv320aic3x.ko
/lib/modules/2.6.35-22-generic/kernel/sound/soc/codecs/snd-soc-wm8510.ko
/lib/modules/2.6.35-22-generic/kernel/sound/soc/codecs/snd-soc-spdif.ko
/lib/modules/2.6.35-22-generic/kernel/sound/soc/codecs/snd-soc-tlv320aic26.ko
/lib/modules/2.6.35-22-generic/kernel/sound/soc/codecs/snd-soc-wm8994.ko
/lib/modules/2.6.35-22-generic/kernel/sound/soc/codecs/snd-soc-max9877.ko
/lib/modules/2.6.35-22-generic/kernel/sound/soc/codecs/snd-soc-wm8960.ko
/lib/modules/2.6.35-22-generic/kernel/sound/soc/codecs/snd-soc-tlv320aic23.ko
/lib/modules/2.6.35-22-generic/kernel/sound/soc/codecs/snd-soc-wm8350.ko
/lib/modules/2.6.35-22-generic/kernel/sound/soc/codecs/snd-soc-ads117x.ko
/lib/modules/2.6.35-22-generic/kernel/sound/soc/codecs/snd-soc-wm8711.ko
/lib/modules/2.6.35-22-generic/kernel/sound/soc/codecs/snd-soc-tlv320dac33.ko
/lib/modules/2.6.35-22-generic/kernel/sound/soc/codecs/snd-soc-wm8900.ko
/lib/modules/2.6.35-22-generic/kernel/sound/soc/codecs/snd-soc-wm8731.ko
/lib/modules/2.6.35-22-generic/kernel/sound/soc/codecs/snd-soc-wm8904.ko
/lib/modules/2.6.35-22-generic/kernel/sound/soc/codecs/snd-soc-ssm2602.ko
/lib/modules/2.6.35-22-generic/kernel/sound/soc/codecs/snd-soc-wm8903.ko
/lib/modules/2.6.35-22-generic/kernel/sound/soc/codecs/snd-soc-da7210.ko
/lib/modules/2.6.35-22-generic/kernel/sound/soc/codecs/snd-soc-wm8988.ko
/lib/modules/2.6.35-22-generic/kernel/sound/soc/codecs/snd-soc-wm8400.ko
/lib/modules/2.6.35-22-generic/kernel/sound/soc/codecs/snd-soc-ad1836.ko
/lib/modules/2.6.35-22-generic/kernel/sound/soc/codecs/snd-soc-pcm3008.ko
/lib/modules/2.6.35-22-generic/kernel/sound/soc/codecs/snd-soc-wm9090.ko
/lib/modules/2.6.35-22-generic/kernel/sound/soc/codecs/snd-soc-ak4642.ko
/lib/modules/2.6.35-22-generic/kernel/sound/i2c/snd-i2c.ko
/lib/modules/2.6.35-22-generic/kernel/sound/i2c/other/snd-pt2258.ko
/lib/modules/2.6.35-22-generic/kernel/sound/i2c/other/snd-tea575x-tuner.ko
/lib/modules/2.6.35-22-generic/kernel/sound/i2c/other/snd-ak4117.ko
/lib/modules/2.6.35-22-generic/kernel/sound/i2c/other/snd-ak4113.ko
/lib/modules/2.6.35-22-generic/kernel/sound/i2c/other/snd-ak4xxx-adda.ko
/lib/modules/2.6.35-22-generic/kernel/sound/i2c/other/snd-ak4114.ko
/lib/modules/2.6.35-22-generic/kernel/sound/i2c/snd-tea6330t.ko
/lib/modules/2.6.35-22-generic/kernel/sound/i2c/snd-cs8427.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/lx6464es/snd-lx6464es.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/snd-bt87x.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/snd-azt3328.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/ctxfi/snd-ctxfi.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/korg1212/snd-korg1212.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/snd-ens1371.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/snd-via82xx.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/ca0106/snd-ca0106.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/snd-rme96.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/snd-sonicvibes.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/snd-atiixp.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/trident/snd-trident.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/echoaudio/snd-gina20.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/echoaudio/snd-darla20.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/echoaudio/snd-indigodjx.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/echoaudio/snd-layla20.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/echoaudio/snd-mia.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/echoaudio/snd-indigo.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/echoaudio/snd-gina24.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/echoaudio/snd-echo3g.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/echoaudio/snd-mona.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/echoaudio/snd-darla24.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/echoaudio/snd-indigoio.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/echoaudio/snd-layla24.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/echoaudio/snd-indigodj.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/echoaudio/snd-indigoiox.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/cs46xx/snd-cs46xx.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/snd-es1968.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/snd-cs4281.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/nm256/snd-nm256.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/snd-maestro3.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/asihpi/snd-asihpi.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/ice1712/snd-ice1712.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/ice1712/snd-ice1724.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/ice1712/snd-ice17xx-ak4xxx.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/ali5451/snd-ali5451.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/snd-intel8x0.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/snd-ad1889.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/snd-intel8x0m.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/snd-ens1370.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/cs5535audio/snd-cs5535audio.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/emu10k1/snd-emu10k1x.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/emu10k1/snd-emu10k1-synth.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/emu10k1/snd-emu10k1.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/mixart/snd-mixart.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/snd-rme32.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/snd-atiixp-modem.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/ac97/snd-ac97-codec.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/hda/snd-hda-codec.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/hda/snd-hda-codec-conexant.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/hda/snd-hda-codec-ca0110.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/hda/snd-hda-intel.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/hda/snd-hda-codec-analog.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/hda/snd-hda-codec-atihdmi.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/hda/snd-hda-codec-si3054.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/hda/snd-hda-codec-realtek.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/hda/snd-hda-codec-via.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/hda/snd-hda-codec-cmedia.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/hda/snd-hda-codec-nvhdmi.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/hda/snd-hda-codec-intelhdmi.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/hda/snd-hda-codec-cirrus.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/hda/snd-hda-codec-idt.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/oxygen/snd-virtuoso.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/oxygen/snd-oxygen-lib.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/oxygen/snd-oxygen.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/oxygen/snd-hifier.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/rme9652/snd-hdspm.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/rme9652/snd-rme9652.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/rme9652/snd-hdsp.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/aw2/snd-aw2.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/pcxhr/snd-pcxhr.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/snd-fm801.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/snd-cmipci.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/vx222/snd-vx222.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/snd-sis7019.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/au88x0/snd-au8830.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/au88x0/snd-au8820.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/au88x0/snd-au8810.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/snd-es1938.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/snd-cs5530.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/ymfpci/snd-ymfpci.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/snd-via82xx-modem.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/riptide/snd-riptide.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/snd-als4000.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/snd-als300.ko

```
wget -O alsa-info.sh [http://alsa-project.org/alsa-info.sh](http://alsa-project.org/alsa-info.sh) && bash ./alsa-info.sh
```
upload=true&script=true&cardinfo=
!!################################
!!ALSA Information Script v 0.4.59
!!################################

!!Script ran on: Sat Nov 13 19:20:04 UTC 2010


!!Linux Distribution
!!------------------

Ubuntu 10.10 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 10.10"


!!DMI Information
!!---------------

Manufacturer:      LENOVO
Product Name:      INVALID


!!Kernel Information
!!------------------

Kernel release:    2.6.35-22-generic
Operating System:  GNU/Linux
Architecture:      i686
Processor:         unknown
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     1.0.23
Library version:    1.0.23
Utilities version:  1.0.23


!!Loaded ALSA modules
!!-------------------



!!Sound Servers on this system
!!----------------------------

Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - Yes

ESound Daemon:
      Installed - Yes (/usr/bin/esd)
      Running - No


!!Soundcards recognised by ALSA
!!-----------------------------

--- no soundcards ---


!!PCI Soundcards installed in the system
!!--------------------------------------

00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)


!!Advanced information - PCI Vendor/Device/Susbsystem ID's
!!--------------------------------------------------------

00:1b.0 0403: 8086:3b56 (rev 05)
	Subsystem: 17aa:38af


!!Modprobe options (Sound related)
!!--------------------------------

snd-atiixp-modem: index=-2
snd-intel8x0m: index=-2
snd-via82xx-modem: index=-2
snd-usb-audio: index=-2
snd-usb-caiaq: index=-2
snd-usb-ua101: index=-2
snd-usb-us122l: index=-2
snd-usb-usx2y: index=-2
snd-cmipci: mpu_port=0x330 fm_port=0x388
snd-pcsp: index=-2
snd-usb-audio: index=-2


!!Loaded sound module options
!!--------------------------


!!ALSA Device nodes
!!-----------------

crw-rw----+ 1 root audio 116, 3 Nov 13 17:24 /dev/snd/seq
crw-rw----+ 1 root audio 116, 2 Nov 13 17:24 /dev/snd/timer


!!Aplay/Arecord output
!!------------

APLAY

aplay: device_list:235: no soundcards found...

ARECORD

arecord: device_list:235: no soundcards found...

!!Amixer output
!!-------------


!!Alsactl output
!!-------------

--startcollapse--
--endcollapse--


!!All Loaded Modules
!!------------------

Module
rfcomm
sco
bnep
l2cap
btusb
bluetooth
nls_utf8
udf
crc_itu_t
hid_a4tech
usbhid
hid
dm_crypt
parport_pc
ppdev
aes_i586
aes_generic
binfmt_misc
snd_hda_intel
snd_hda_codec
snd_hwdep
snd_pcm
uvcvideo
joydev
snd_seq_midi
snd_rawmidi
videodev
snd_seq_midi_event
v4l1_compat
snd_seq
lib80211_crypt_tkip
snd_timer
snd_seq_device
lp
acer_wmi
led_class
psmouse
wl
snd
lib80211
intel_ips
serio_raw
soundcore
snd_page_alloc
parport
i915
drm_kms_helper
drm
ahci
intel_agp
i2c_algo_bit
video
atl1c
libahci
output
agpgart


!!ALSA/HDA dmesg
!!------------------

[    7.296394] last sysfs file: /sys/devices/virtual/bdi/1:12/uevent
[    7.296397] Modules linked in: intel_ips(+) serio_raw soundcore snd_page_alloc parport i915 drm_kms_helper drm ahci intel_agp i2c_algo_bit video atl1c libahci output agpgart
[    7.296410] 
--
[ 6236.015194]  [<c036cbc5>] __pci_register_driver+0x45/0xb0
[ 6236.015202]  [<f80b9017>] alsa_card_azx_init+0x17/0x19 [snd_hda_intel]
[ 6236.015208]  [<c0101132>] do_one_initcall+0x32/0x1a0
[ 6236.015214]  [<f80b9000>] ? alsa_card_azx_init+0x0/0x19 [snd_hda_intel]
[ 6236.015222]  [<c0180c2b>] sys_init_module+0x9b/0x1e0
--
[ 9148.110744]  [<c036cbc5>] __pci_register_driver+0x45/0xb0
[ 9148.110751]  [<f80b9017>] alsa_card_azx_init+0x17/0x19 [snd_hda_intel]
[ 9148.110758]  [<c0101132>] do_one_initcall+0x32/0x1a0
[ 9148.110764]  [<f80b9000>] ? alsa_card_azx_init+0x0/0x19 [snd_hda_intel]
[ 9148.110772]  [<c0180c2b>] sys_init_module+0x9b/0x1e0
```

Any suggestions?

---

### Post by jcparker500 on 2010-11-13
I have a Lenovo G560 with Ubuntu 10.10 64 bit also with no sound.  Sounds like the same issue.  When I go to Preferences - Sound there is nothing listed under the hardware tab.

Please keep in mind that I am brand new to Linux. I don't know anything about recompiling the kernel or things of that nature. I am actually running off of the CD to see if it has drivers for everything before I install it on my hard drive. I really want to use Ubuntu as I love the GUI and the speed, but sound is very important to me. Anyone know if there is a simple enough fix for this for a newbie?

Futher info - 

I ran a System Test and this is some of the output:

DistroRelease: Ubuntu 10.10
Package: alsa-base 1.0.23+dfsg-1ubuntu4
ProcVersionSignature: Ubuntu 2.6.35-22.33-generic 2.6.35.4
Uname: Linux 2.6.35-22-generic x86_64
NonfreeKernelModules: wl
AlsaDevices:
 total 0
 crw-rw----+ 1 root audio 116, 3 2010-11-13 12:33 seq
 crw-rw----+ 1 root audio 116, 2 2010-11-13 12:33 timer
AlsaVersion: Advanced Linux Sound Architecture Driver Version 1.0.23.
**AplayDevices: aplay: device_list:235: no soundcards found...**
Architecture: amd64
ArecordDevices: arecord: device_list:235: no soundcards found...
AudioDevicesInUse: Error: command ['fuser', '-v', '/dev/snd/seq', '/dev/snd/timer'] failed with exit code 1: Cannot stat file /proc/4485/fd/32: Stale NFS file handle
CheckboxCommand: cat /proc/asound/cards
CheckboxDescription:
 Detecting your sound device(s):

 $output

 Is this correct?
CheckboxTest: list_audio_devices
Date: Sat Nov 13 18:56:39 2010
LiveMediaBuild: Ubuntu 10.10 "Maverick Meerkat" - Release amd64 (20101007)
PackageArchitecture: all
ProcEnviron:
 SHELL=/bin/bash
 LANG=en_US.UTF-8
SourcePackage: alsa-driver

---

### Post by kik on 2010-11-13
Sound works with ubuntu 9.04 the same with 10.04.1 LTS (but other things don't work).
Sound settings with ubuntu 9.04:
> 
lspci -v:
00:1b.0 Audio device: Intel Corporation Ibex Peak High Definition Audio (rev 05)
	Subsystem: Lenovo Device 38af
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at f2800000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel
aplay -l: > **** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC269 Analog [ALC269 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
cat /proc/asound/modules: " 0 snd_hda_intel"
grep 'audio' /etc/group: ```
audio:x:29:pulse,ubuntu
```
find /lib/modules/`uname -r` | grep snd
```

/lib/modules/2.6.28-11-generic/kernel/sound/core/oss/snd-mixer-oss.ko
/lib/modules/2.6.28-11-generic/kernel/sound/core/oss/snd-pcm-oss.ko
/lib/modules/2.6.28-11-generic/kernel/sound/core/seq/oss/snd-seq-oss.ko
/lib/modules/2.6.28-11-generic/kernel/sound/core/seq/snd-seq-device.ko
/lib/modules/2.6.28-11-generic/kernel/sound/core/seq/snd-seq-dummy.ko
/lib/modules/2.6.28-11-generic/kernel/sound/core/seq/snd-seq-midi-emul.ko
/lib/modules/2.6.28-11-generic/kernel/sound/core/seq/snd-seq-midi-event.ko
/lib/modules/2.6.28-11-generic/kernel/sound/core/seq/snd-seq-midi.ko
/lib/modules/2.6.28-11-generic/kernel/sound/core/seq/snd-seq-virmidi.ko
/lib/modules/2.6.28-11-generic/kernel/sound/core/seq/snd-seq.ko
/lib/modules/2.6.28-11-generic/kernel/sound/core/snd-hwdep.ko
/lib/modules/2.6.28-11-generic/kernel/sound/core/snd-page-alloc.ko
/lib/modules/2.6.28-11-generic/kernel/sound/core/snd-pcm.ko
/lib/modules/2.6.28-11-generic/kernel/sound/core/snd-rawmidi.ko
/lib/modules/2.6.28-11-generic/kernel/sound/core/snd-timer.ko
/lib/modules/2.6.28-11-generic/kernel/sound/core/snd.ko
/lib/modules/2.6.28-11-generic/kernel/sound/drivers/mpu401/snd-mpu401-uart.ko
/lib/modules/2.6.28-11-generic/kernel/sound/drivers/mpu401/snd-mpu401.ko
/lib/modules/2.6.28-11-generic/kernel/sound/drivers/opl3/snd-opl3-lib.ko
/lib/modules/2.6.28-11-generic/kernel/sound/drivers/opl3/snd-opl3-synth.ko
/lib/modules/2.6.28-11-generic/kernel/sound/drivers/opl4/snd-opl4-lib.ko
/lib/modules/2.6.28-11-generic/kernel/sound/drivers/opl4/snd-opl4-synth.ko
/lib/modules/2.6.28-11-generic/kernel/sound/drivers/pcsp/snd-pcsp.ko
/lib/modules/2.6.28-11-generic/kernel/sound/drivers/snd-dummy.ko
/lib/modules/2.6.28-11-generic/kernel/sound/drivers/snd-mtpav.ko
/lib/modules/2.6.28-11-generic/kernel/sound/drivers/snd-mts64.ko
/lib/modules/2.6.28-11-generic/kernel/sound/drivers/snd-portman2x4.ko
/lib/modules/2.6.28-11-generic/kernel/sound/drivers/snd-serial-u16550.ko
/lib/modules/2.6.28-11-generic/kernel/sound/drivers/snd-virmidi.ko
/lib/modules/2.6.28-11-generic/kernel/sound/drivers/vx/snd-vx-lib.ko
/lib/modules/2.6.28-11-generic/kernel/sound/i2c/other/snd-ak4114.ko
/lib/modules/2.6.28-11-generic/kernel/sound/i2c/other/snd-ak4117.ko
/lib/modules/2.6.28-11-generic/kernel/sound/i2c/other/snd-ak4xxx-adda.ko
/lib/modules/2.6.28-11-generic/kernel/sound/i2c/other/snd-pt2258.ko
/lib/modules/2.6.28-11-generic/kernel/sound/i2c/other/snd-tea575x-tuner.ko
/lib/modules/2.6.28-11-generic/kernel/sound/i2c/snd-cs8427.ko
/lib/modules/2.6.28-11-generic/kernel/sound/i2c/snd-i2c.ko
/lib/modules/2.6.28-11-generic/kernel/sound/i2c/snd-tea6330t.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/ad1816a/snd-ad1816a.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/ad1848/snd-ad1848.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/cs423x/snd-cs4231.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/cs423x/snd-cs4232.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/cs423x/snd-cs4236-lib.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/cs423x/snd-cs4236.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/es1688/snd-es1688-lib.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/es1688/snd-es1688.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/gus/snd-gus-lib.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/gus/snd-gusclassic.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/gus/snd-gusextreme.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/gus/snd-gusmax.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/gus/snd-interwave-stb.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/gus/snd-interwave.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/opti9xx/snd-miro.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/opti9xx/snd-opti92x-ad1848.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/opti9xx/snd-opti92x-cs4231.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/opti9xx/snd-opti93x.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/sb/snd-emu8000-synth.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/sb/snd-es968.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/sb/snd-sb-common.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/sb/snd-sb16-csp.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/sb/snd-sb16-dsp.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/sb/snd-sb16.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/sb/snd-sb8-dsp.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/sb/snd-sb8.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/sb/snd-sbawe.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/snd-adlib.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/snd-als100.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/snd-azt2320.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/snd-cmi8330.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/snd-dt019x.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/snd-es18xx.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/snd-opl3sa2.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/snd-sc6000.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/snd-sgalaxy.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/snd-sscape.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/wavefront/snd-wavefront.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/wss/snd-wss-lib.ko
/lib/modules/2.6.28-11-generic/kernel/sound/oss/msnd.ko
/lib/modules/2.6.28-11-generic/kernel/sound/oss/msnd_classic.ko
/lib/modules/2.6.28-11-generic/kernel/sound/oss/msnd_pinnacle.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/ac97/snd-ac97-codec.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/ali5451/snd-ali5451.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/au88x0/snd-au8810.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/au88x0/snd-au8820.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/au88x0/snd-au8830.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/aw2/snd-aw2.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/ca0106/snd-ca0106.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/cs46xx/snd-cs46xx.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/cs5535audio/snd-cs5535audio.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/echoaudio/snd-darla20.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/echoaudio/snd-darla24.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/echoaudio/snd-echo3g.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/echoaudio/snd-gina20.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/echoaudio/snd-gina24.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/echoaudio/snd-indigo.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/echoaudio/snd-indigodj.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/echoaudio/snd-indigoio.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/echoaudio/snd-layla20.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/echoaudio/snd-layla24.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/echoaudio/snd-mia.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/echoaudio/snd-mona.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/emu10k1/snd-emu10k1-synth.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/emu10k1/snd-emu10k1.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/emu10k1/snd-emu10k1x.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/hda/snd-hda-intel.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/ice1712/snd-ice1712.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/ice1712/snd-ice1724.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/ice1712/snd-ice17xx-ak4xxx.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/korg1212/snd-korg1212.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/mixart/snd-mixart.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/nm256/snd-nm256.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/oxygen/snd-hifier.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/oxygen/snd-oxygen-lib.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/oxygen/snd-oxygen.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/oxygen/snd-virtuoso.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/pcxhr/snd-pcxhr.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/riptide/snd-riptide.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/rme9652/snd-hdsp.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/rme9652/snd-hdspm.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/rme9652/snd-rme9652.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/snd-ad1889.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/snd-als300.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/snd-als4000.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/snd-atiixp-modem.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/snd-atiixp.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/snd-azt3328.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/snd-bt87x.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/snd-cmipci.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/snd-cs4281.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/snd-cs5530.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/snd-ens1370.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/snd-ens1371.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/snd-es1938.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/snd-es1968.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/snd-fm801.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/snd-intel8x0.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/snd-intel8x0m.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/snd-maestro3.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/snd-rme32.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/snd-rme96.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/snd-sis7019.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/snd-sonicvibes.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/snd-via82xx-modem.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/snd-via82xx.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/trident/snd-trident.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/vx222/snd-vx222.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/ymfpci/snd-ymfpci.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pcmcia/pdaudiocf/snd-pdaudiocf.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pcmcia/vx/snd-vxpocket.ko
/lib/modules/2.6.28-11-generic/kernel/sound/soc/codecs/snd-soc-ad73311.ko
/lib/modules/2.6.28-11-generic/kernel/sound/soc/codecs/snd-soc-ak4535.ko
/lib/modules/2.6.28-11-generic/kernel/sound/soc/codecs/snd-soc-cs4270.ko
/lib/modules/2.6.28-11-generic/kernel/sound/soc/codecs/snd-soc-ssm2602.ko
/lib/modules/2.6.28-11-generic/kernel/sound/soc/codecs/snd-soc-tlv320aic23.ko
/lib/modules/2.6.28-11-generic/kernel/sound/soc/codecs/snd-soc-tlv320aic26.ko
/lib/modules/2.6.28-11-generic/kernel/sound/soc/codecs/snd-soc-tlv320aic3x.ko
/lib/modules/2.6.28-11-generic/kernel/sound/soc/codecs/snd-soc-uda1380.ko
/lib/modules/2.6.28-11-generic/kernel/sound/soc/codecs/snd-soc-wm8510.ko
/lib/modules/2.6.28-11-generic/kernel/sound/soc/codecs/snd-soc-wm8580.ko
/lib/modules/2.6.28-11-generic/kernel/sound/soc/codecs/snd-soc-wm8731.ko
/lib/modules/2.6.28-11-generic/kernel/sound/soc/codecs/snd-soc-wm8750.ko
/lib/modules/2.6.28-11-generic/kernel/sound/soc/codecs/snd-soc-wm8753.ko
/lib/modules/2.6.28-11-generic/kernel/sound/soc/codecs/snd-soc-wm8900.ko
/lib/modules/2.6.28-11-generic/kernel/sound/soc/codecs/snd-soc-wm8903.ko
/lib/modules/2.6.28-11-generic/kernel/sound/soc/codecs/snd-soc-wm8971.ko
/lib/modules/2.6.28-11-generic/kernel/sound/soc/codecs/snd-soc-wm8990.ko
/lib/modules/2.6.28-11-generic/kernel/sound/soc/snd-soc-core.ko
/lib/modules/2.6.28-11-generic/kernel/sound/synth/emux/snd-emux-synth.ko
/lib/modules/2.6.28-11-generic/kernel/sound/synth/snd-util-mem.ko
/lib/modules/2.6.28-11-generic/kernel/sound/usb/caiaq/snd-usb-caiaq.ko
/lib/modules/2.6.28-11-generic/kernel/sound/usb/snd-usb-audio.ko
/lib/modules/2.6.28-11-generic/kernel/sound/usb/snd-usb-lib.ko
/lib/modules/2.6.28-11-generic/kernel/sound/usb/usx2y/snd-usb-us122l.ko
/lib/modules/2.6.28-11-generic/kernel/sound/usb/usx2y/snd-usb-usx2y.ko

```

wget -O alsa-info.sh [http://alsa-project.org/alsa-info.sh](http://alsa-project.org/alsa-info.sh) && bash ./alsa-info.sh
```

upload=true&script=true&cardinfo=
!!################################
!!ALSA Information Script v 0.4.59
!!################################

!!Script ran on: Sat Nov 13 22:57:22 UTC 2010


!!Linux Distribution
!!------------------

Ubuntu 9.04 \n \l DISTRIB_ID=Ubuntu


!!DMI Information
!!---------------

Manufacturer:      LENOVO
Product Name:      INVALID


!!Kernel Information
!!------------------

Kernel release:    2.6.28-11-generic
Operating System:  GNU/Linux
Architecture:      i686
Processor:         unknown
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     1.0.18rc3
Library version:    1.0.18
Utilities version:  1.0.18


!!Loaded ALSA modules
!!-------------------

snd_hda_intel


!!Sound Servers on this system
!!----------------------------

Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - Yes

ESound Daemon:
      Installed - Yes (/usr/bin/esd)
      Running - No


!!Soundcards recognised by ALSA
!!-----------------------------

 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf2800000 irq 22


!!PCI Soundcards installed in the system
!!--------------------------------------

00:1b.0 Audio device: Intel Corporation Ibex Peak High Definition Audio (rev 05)


!!Advanced information - PCI Vendor/Device/Susbsystem ID's
!!--------------------------------------------------------

00:1b.0 0403: 8086:3b56 (rev 05)
	Subsystem: 17aa:38af


!!Modprobe options (Sound related)
!!--------------------------------

snd-atiixp-modem: index=-2
snd-intel8x0m: index=-2
snd-via82xx-modem: index=-2
snd-usb-audio: index=-2
snd-usb-us122l: index=-2
snd-usb-usx2y: index=-2
snd-usb-caiaq: index=-2
snd-cmipci: mpu_port=0x330 fm_port=0x388
snd-pcsp: index=-2


!!Loaded sound module options
!!--------------------------

!!Module: snd_hda_intel
	bdl_pos_adj : 1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
	enable_msi : 0
	id : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
	index : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	model : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
	position_fix : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	power_save : 0
	power_save_controller : Y
	probe_mask : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	single_cmd : N


!!HDA-Intel Codec information
!!---------------------------
--startcollapse--

Codec: Realtek ALC269
Address: 0
Vendor Id: 0x10ec0269
Subsystem Id: 0x17aa6008
Revision Id: 0x100100
No Modem Function Group found
Default PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=2, o=0, i=0, unsolicited=1, wake=0
  IO[0]: enable=0, dir=0, wake=0, sticky=0, data=0
  IO[1]: enable=0, dir=0, wake=0, sticky=0, data=0
Node 0x02 [Audio Output] wcaps 0x1d: Stereo Amp-Out
  Amp-Out caps: ofs=0x57, nsteps=0x57, stepsize=0x02, mute=0
  Amp-Out vals:  [0x4e 0x4e]
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x03 [Audio Output] wcaps 0x1d: Stereo Amp-Out
  Amp-Out caps: ofs=0x57, nsteps=0x57, stepsize=0x02, mute=0
  Amp-Out vals:  [0x00 0x00]
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x04 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x05 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x06 [Audio Output] wcaps 0x211: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0x5e0]: 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x07 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x08 [Audio Input] wcaps 0x10011b: Stereo Amp-In
  Amp-In caps: ofs=0x0b, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x8b 0x8b]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Connection: 1
     0x23
Node 0x09 [Audio Input] wcaps 0x10011b: Stereo Amp-In
  Amp-In caps: ofs=0x0b, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x8b 0x8b]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Connection: 1
     0x22
Node 0x0a [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x0b [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 5
     0x18 0x19 0x1a 0x1b 0x1d
Node 0x0c [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Connection: 2
     0x02 0x0b
Node 0x0d [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Connection: 2
     0x03 0x0b
Node 0x0e [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x0f [Audio Mixer] wcaps 0x20010a: Mono Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00] [0x80]
  Connection: 2
     0x02 0x0b
Node 0x10 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x11 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x12 [Pin Complex] wcaps 0x40000b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x2f, mute=0
  Amp-In vals:  [0x00 0x00]
  Pincap 0x00000020: IN
  Pin Default 0x99a30930: [Fixed] Mic at Int ATAPI
    Conn = ATAPI, Color = Unknown
    DefAssociation = 0x3, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
Node 0x13 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x14 [Pin Complex] wcaps 0x40018d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x00010014: OUT EAPD Detect
  EAPD 0x2: EAPD
  Pin Default 0x99130110: [Fixed] Speaker at Int ATAPI
    Conn = ATAPI, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 2
     0x0c* 0x0d
Node 0x15 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x16 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x17 [Pin Complex] wcaps 0x40010c: Mono Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80]
  Pincap 0x00000010: OUT
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
  Connection: 1
     0x0f
Node 0x18 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x2f, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x00001734: IN OUT Detect
    Vref caps: HIZ 50 GRD 80
  Pin Default 0x01a19820: [Jack] Mic at Ext Rear
    Conn = 1/8, Color = Pink
    DefAssociation = 0x2, Sequence = 0x0
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x0d
Node 0x19 [Pin Complex] wcaps 0x40008b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x2f, mute=0
  Amp-In vals:  [0x00 0x00]
  Pincap 0x00001724: IN Detect
    Vref caps: HIZ 50 GRD 80
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=00, enabled=0
Node 0x1a [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x2f, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000003c: IN OUT HP Detect
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
  Unsolicited: tag=00, enabled=0
  Connection: 2
     0x0c* 0x0d
Node 0x1b [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x2f, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x00000034: IN OUT Detect
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
  Unsolicited: tag=00, enabled=0
  Connection: 2
     0x0c* 0x0d
Node 0x1c [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x1d [Pin Complex] wcaps 0x400000: Mono
  Pincap 0x00000020: IN
  Pin Default 0x40179a2d: [N/A] Speaker at Ext N/A
    Conn = Analog, Color = Pink
    DefAssociation = 0x2, Sequence = 0xd
  Pin-ctls: 0x20: IN
Node 0x1e [Pin Complex] wcaps 0x400381: Stereo Digital
  Pincap 0x00000014: OUT Detect
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x06
Node 0x1f [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x20 [Vendor Defined Widget] wcaps 0xf00040: Mono
  Processing caps: benign=0, ncoeff=25
Node 0x21 [Pin Complex] wcaps 0x40018d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0000001c: OUT HP Detect
  Pin Default 0x0121401f: [Jack] HP Out at Ext Rear
    Conn = 1/8, Color = Green
    DefAssociation = 0x1, Sequence = 0xf
  Pin-ctls: 0xc0: OUT HP
  Unsolicited: tag=04, enabled=1
  Connection: 2
     0x0c* 0x0d
Node 0x22 [Audio Selector] wcaps 0x30010b: Stereo Amp-In
  Amp-In caps: N/A
  Amp-In vals:  [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x00 0x00]
  Connection: 7
     0x18* 0x19 0x1a 0x1b 0x1d 0x0b 0x12
Node 0x23 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 6
     0x18 0x19 0x1a 0x1b 0x1d 0x0b
--endcollapse--

```

---

### Post by sloom22 on 2011-05-27
I got everything working by upgrading to Linux Mint 11 (should be identical to Ubuntu 11.04). See [http://ubuntuforums.org/showthread.php?p=10867797](http://ubuntuforums.org/showthread.php?p=10867797) for details.

---

