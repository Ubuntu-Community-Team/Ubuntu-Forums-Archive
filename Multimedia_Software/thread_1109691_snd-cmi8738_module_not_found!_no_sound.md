---
title: "snd-cmi8738 module not found?! no sound"
date: 2009-03-29
forum: Multimedia Software
---

### Post by MaynardHSH on 2009-03-29
this is a weird thing and since a week ago or so i got no sound...i've followed a few guides about sound troubleshooting but none seem to work, and it seems that my card is not been recognized or something even tho with aplay -l it does 

> aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: CMI8738 [C-Media CMI8738], device 0: CMI8738-MC6 [C-Media PCI DAC/ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CMI8738 [C-Media CMI8738], device 1: CMI8738-MC6 [C-Media PCI 2nd DAC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CMI8738 [C-Media CMI8738], device 2: CMI8738-MC6 [C-Media PCI IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: modem [VIA 82XX modem], device 0: VIA 82XX modem [VIA 82XX modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: V8235 [VIA 8235], device 0: VIA 8235 [VIA 8235]
  Subdevices: 4/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 2: V8235 [VIA 8235], device 1: VIA 8235 [VIA 8235]



tried this one 
> sudo /sbin/modprobe snd-cmi8738
FATAL: Module snd_cmi8738 not found.


also this one and it shows a snd-cmipci but not a snd-cmi8738....there's even a snd-cmi8330

> find /lib/modules/`uname -r` | grep snd
/lib/modules/2.6.27-14-generic/kernel/sound/core/snd-rawmidi.ko
/lib/modules/2.6.27-14-generic/kernel/sound/core/snd-page-alloc.ko
/lib/modules/2.6.27-14-generic/kernel/sound/core/oss/snd-pcm-oss.ko
/lib/modules/2.6.27-14-generic/kernel/sound/core/oss/snd-mixer-oss.ko
/lib/modules/2.6.27-14-generic/kernel/sound/core/snd-pcm.ko
/lib/modules/2.6.27-14-generic/kernel/sound/core/snd.ko
/lib/modules/2.6.27-14-generic/kernel/sound/core/snd-hwdep.ko
/lib/modules/2.6.27-14-generic/kernel/sound/core/snd-timer.ko
/lib/modules/2.6.27-14-generic/kernel/sound/core/seq/snd-seq-virmidi.ko
/lib/modules/2.6.27-14-generic/kernel/sound/core/seq/snd-seq-midi-event.ko
/lib/modules/2.6.27-14-generic/kernel/sound/core/seq/snd-seq-midi-emul.ko
/lib/modules/2.6.27-14-generic/kernel/sound/core/seq/oss/snd-seq-oss.ko
/lib/modules/2.6.27-14-generic/kernel/sound/core/seq/snd-seq-dummy.ko
/lib/modules/2.6.27-14-generic/kernel/sound/core/seq/snd-seq.ko
/lib/modules/2.6.27-14-generic/kernel/sound/core/seq/snd-seq-device.ko
/lib/modules/2.6.27-14-generic/kernel/sound/core/seq/snd-seq-midi.ko
/lib/modules/2.6.27-14-generic/kernel/sound/i2c/other/snd-ak4117.ko
/lib/modules/2.6.27-14-generic/kernel/sound/i2c/other/snd-tea575x-tuner.ko
/lib/modules/2.6.27-14-generic/kernel/sound/i2c/other/snd-ak4xxx-adda.ko
/lib/modules/2.6.27-14-generic/kernel/sound/i2c/other/snd-pt2258.ko
/lib/modules/2.6.27-14-generic/kernel/sound/i2c/other/snd-ak4114.ko
/lib/modules/2.6.27-14-generic/kernel/sound/i2c/snd-i2c.ko
/lib/modules/2.6.27-14-generic/kernel/sound/i2c/snd-cs8427.ko
/lib/modules/2.6.27-14-generic/kernel/sound/i2c/snd-tea6330t.ko
/lib/modules/2.6.27-14-generic/kernel/sound/soc/snd-soc-core.ko
/lib/modules/2.6.27-14-generic/kernel/sound/oss/msnd_pinnacle.ko
/lib/modules/2.6.27-14-generic/kernel/sound/oss/msnd_classic.ko
/lib/modules/2.6.27-14-generic/kernel/sound/oss/msnd.ko
/lib/modules/2.6.27-14-generic/kernel/sound/synth/snd-util-mem.ko
/lib/modules/2.6.27-14-generic/kernel/sound/synth/emux/snd-emux-synth.ko
/lib/modules/2.6.27-14-generic/kernel/sound/usb/snd-usb-audio.ko
/lib/modules/2.6.27-14-generic/kernel/sound/usb/snd-usb-lib.ko
/lib/modules/2.6.27-14-generic/kernel/sound/usb/usx2y/snd-usb-usx2y.ko
/lib/modules/2.6.27-14-generic/kernel/sound/usb/caiaq/snd-usb-caiaq.ko
/lib/modules/2.6.27-14-generic/kernel/sound/pci/korg1212/snd-korg1212.ko
/lib/modules/2.6.27-14-generic/kernel/sound/pci/snd-als4000.ko
/lib/modules/2.6.27-14-generic/kernel/sound/pci/cs5535audio/snd-cs5535audio.ko
/lib/modules/2.6.27-14-generic/kernel/sound/pci/trident/snd-trident.ko
/lib/modules/2.6.27-14-generic/kernel/sound/pci/riptide/snd-riptide.ko
/lib/modules/2.6.27-14-generic/kernel/sound/pci/ac97/snd-ac97-codec.ko
/lib/modules/2.6.27-14-generic/kernel/sound/pci/emu10k1/snd-emu10k1.ko
/lib/modules/2.6.27-14-generic/kernel/sound/pci/emu10k1/snd-emu10k1x.ko
/lib/modules/2.6.27-14-generic/kernel/sound/pci/emu10k1/snd-emu10k1-synth.ko
/lib/modules/2.6.27-14-generic/kernel/sound/pci/hda/snd-hda-intel.ko
/lib/modules/2.6.27-14-generic/kernel/sound/pci/snd-azt3328.ko
/lib/modules/2.6.27-14-generic/kernel/sound/pci/snd-atiixp-modem.ko
/lib/modules/2.6.27-14-generic/kernel/sound/pci/snd-intel8x0m.ko
/lib/modules/2.6.27-14-generic/kernel/sound/pci/rme9652/snd-hdsp.ko
/lib/modules/2.6.27-14-generic/kernel/sound/pci/rme9652/snd-rme9652.ko
/lib/modules/2.6.27-14-generic/kernel/sound/pci/rme9652/snd-hdspm.ko
/lib/modules/2.6.27-14-generic/kernel/sound/pci/aw2/snd-aw2.ko
/lib/modules/2.6.27-14-generic/kernel/sound/pci/pcxhr/snd-pcxhr.ko
/lib/modules/2.6.27-14-generic/kernel/sound/pci/snd-sis7019.ko
/lib/modules/2.6.27-14-generic/kernel/sound/pci/snd-atiixp.ko
/lib/modules/2.6.27-14-generic/kernel/sound/pci/snd-ens1370.ko
/lib/modules/2.6.27-14-generic/kernel/sound/pci/snd-fm801.ko
/lib/modules/2.6.27-14-generic/kernel/sound/pci/snd-rme96.ko
/lib/modules/2.6.27-14-generic/kernel/sound/pci/mixart/snd-mixart.ko
/lib/modules/2.6.27-14-generic/kernel/sound/pci/snd-via82xx.ko
/lib/modules/2.6.27-14-generic/kernel/sound/pci/snd-ad1889.ko
/lib/modules/2.6.27-14-generic/kernel/sound/pci/cs46xx/snd-cs46xx.ko
/lib/modules/2.6.27-14-generic/kernel/sound/pci/snd-sonicvibes.ko
/lib/modules/2.6.27-14-generic/kernel/sound/pci/snd-es1968.ko
/lib/modules/2.6.27-14-generic/kernel/sound/pci/ice1712/snd-ice1724.ko
/lib/modules/2.6.27-14-generic/kernel/sound/pci/ice1712/snd-ice17xx-ak4xxx.ko
/lib/modules/2.6.27-14-generic/kernel/sound/pci/ice1712/snd-ice1712.ko
/lib/modules/2.6.27-14-generic/kernel/sound/pci/snd-bt87x.ko
/lib/modules/2.6.27-14-generic/kernel/sound/pci/snd-es1938.ko
/lib/modules/2.6.27-14-generic/kernel/sound/pci/snd-intel8x0.ko
/lib/modules/2.6.27-14-generic/kernel/sound/pci/vx222/snd-vx222.ko
/lib/modules/2.6.27-14-generic/kernel/sound/pci/oxygen/snd-hifier.ko
/lib/modules/2.6.27-14-generic/kernel/sound/pci/oxygen/snd-oxygen.ko
/lib/modules/2.6.27-14-generic/kernel/sound/pci/oxygen/snd-oxygen-lib.ko
/lib/modules/2.6.27-14-generic/kernel/sound/pci/oxygen/snd-virtuoso.ko
/lib/modules/2.6.27-14-generic/kernel/sound/pci/snd-cs5530.ko
/lib/modules/2.6.27-14-generic/kernel/sound/pci/snd-als300.ko
/lib/modules/2.6.27-14-generic/kernel/sound/pci/ca0106/snd-ca0106.ko
/lib/modules/2.6.27-14-generic/kernel/sound/pci/echoaudio/snd-darla20.ko
/lib/modules/2.6.27-14-generic/kernel/sound/pci/echoaudio/snd-gina24.ko
/lib/modules/2.6.27-14-generic/kernel/sound/pci/echoaudio/snd-echo3g.ko
/lib/modules/2.6.27-14-generic/kernel/sound/pci/echoaudio/snd-mia.ko
/lib/modules/2.6.27-14-generic/kernel/sound/pci/echoaudio/snd-mona.ko
/lib/modules/2.6.27-14-generic/kernel/sound/pci/echoaudio/snd-layla20.ko
/lib/modules/2.6.27-14-generic/kernel/sound/pci/echoaudio/snd-gina20.ko
/lib/modules/2.6.27-14-generic/kernel/sound/pci/echoaudio/snd-indigo.ko
/lib/modules/2.6.27-14-generic/kernel/sound/pci/echoaudio/snd-indigodj.ko
/lib/modules/2.6.27-14-generic/kernel/sound/pci/echoaudio/snd-indigoio.ko
/lib/modules/2.6.27-14-generic/kernel/sound/pci/echoaudio/snd-layla24.ko
/lib/modules/2.6.27-14-generic/kernel/sound/pci/echoaudio/snd-darla24.ko
/lib/modules/2.6.27-14-generic/kernel/sound/pci/ali5451/snd-ali5451.ko
/lib/modules/2.6.27-14-generic/kernel/sound/pci/nm256/snd-nm256.ko
/lib/modules/2.6.27-14-generic/kernel/sound/pci/snd-via82xx-modem.ko
/lib/modules/2.6.27-14-generic/kernel/sound/pci/snd-ens1371.ko
/lib/modules/2.6.27-14-generic/kernel/sound/pci/snd-rme32.ko
/lib/modules/2.6.27-14-generic/kernel/sound/pci/ymfpci/snd-ymfpci.ko
/lib/modules/2.6.27-14-generic/kernel/sound/pci/snd-cmipci.ko
/lib/modules/2.6.27-14-generic/kernel/sound/pci/snd-maestro3.ko
/lib/modules/2.6.27-14-generic/kernel/sound/pci/snd-cs4281.ko
/lib/modules/2.6.27-14-generic/kernel/sound/pci/au88x0/snd-au8830.ko
/lib/modules/2.6.27-14-generic/kernel/sound/pci/au88x0/snd-au8810.ko
/lib/modules/2.6.27-14-generic/kernel/sound/pci/au88x0/snd-au8820.ko
/lib/modules/2.6.27-14-generic/kernel/sound/drivers/snd-virmidi.ko
/lib/modules/2.6.27-14-generic/kernel/sound/drivers/snd-serial-u16550.ko
/lib/modules/2.6.27-14-generic/kernel/sound/drivers/opl3/snd-opl3-lib.ko
/lib/modules/2.6.27-14-generic/kernel/sound/drivers/opl3/snd-opl3-synth.ko
/lib/modules/2.6.27-14-generic/kernel/sound/drivers/vx/snd-vx-lib.ko
/lib/modules/2.6.27-14-generic/kernel/sound/drivers/snd-dummy.ko
/lib/modules/2.6.27-14-generic/kernel/sound/drivers/snd-portman2x4.ko
/lib/modules/2.6.27-14-generic/kernel/sound/drivers/opl4/snd-opl4-synth.ko
/lib/modules/2.6.27-14-generic/kernel/sound/drivers/opl4/snd-opl4-lib.ko
/lib/modules/2.6.27-14-generic/kernel/sound/drivers/snd-mtpav.ko
/lib/modules/2.6.27-14-generic/kernel/sound/drivers/pcsp/snd-pcsp.ko
/lib/modules/2.6.27-14-generic/kernel/sound/drivers/mpu401/snd-mpu401-uart.ko
/lib/modules/2.6.27-14-generic/kernel/sound/drivers/mpu401/snd-mpu401.ko
/lib/modules/2.6.27-14-generic/kernel/sound/drivers/snd-mts64.ko
/lib/modules/2.6.27-14-generic/kernel/sound/isa/snd-adlib.ko
/lib/modules/2.6.27-14-generic/kernel/sound/isa/sb/snd-sb16-csp.ko
/lib/modules/2.6.27-14-generic/kernel/sound/isa/sb/snd-sb-common.ko
/lib/modules/2.6.27-14-generic/kernel/sound/isa/sb/snd-emu8000-synth.ko
/lib/modules/2.6.27-14-generic/kernel/sound/isa/sb/snd-sb16-dsp.ko
/lib/modules/2.6.27-14-generic/kernel/sound/isa/sb/snd-es968.ko
/lib/modules/2.6.27-14-generic/kernel/sound/isa/sb/snd-sb8.ko
/lib/modules/2.6.27-14-generic/kernel/sound/isa/sb/snd-sbawe.ko
/lib/modules/2.6.27-14-generic/kernel/sound/isa/sb/snd-sb8-dsp.ko
/lib/modules/2.6.27-14-generic/kernel/sound/isa/sb/snd-sb16.ko
/lib/modules/2.6.27-14-generic/kernel/sound/isa/snd-sscape.ko
/lib/modules/2.6.27-14-generic/kernel/sound/isa/opti9xx/snd-opti93x.ko
/lib/modules/2.6.27-14-generic/kernel/sound/isa/opti9xx/snd-opti92x-cs4231.ko
/lib/modules/2.6.27-14-generic/kernel/sound/isa/opti9xx/snd-opti92x-ad1848.ko
/lib/modules/2.6.27-14-generic/kernel/sound/isa/opti9xx/snd-miro.ko
/lib/modules/2.6.27-14-generic/kernel/sound/isa/ad1816a/snd-ad1816a.ko
/lib/modules/2.6.27-14-generic/kernel/sound/isa/ad1848/snd-ad1848-lib.ko
/lib/modules/2.6.27-14-generic/kernel/sound/isa/ad1848/snd-ad1848.ko
/lib/modules/2.6.27-14-generic/kernel/sound/isa/snd-dt019x.ko
/lib/modules/2.6.27-14-generic/kernel/sound/isa/wavefront/snd-wavefront.ko
/lib/modules/2.6.27-14-generic/kernel/sound/isa/snd-opl3sa2.ko
/lib/modules/2.6.27-14-generic/kernel/sound/isa/snd-als100.ko
/lib/modules/2.6.27-14-generic/kernel/sound/isa/es1688/snd-es1688-lib.ko
/lib/modules/2.6.27-14-generic/kernel/sound/isa/es1688/snd-es1688.ko
/lib/modules/2.6.27-14-generic/kernel/sound/isa/snd-azt2320.ko
/lib/modules/2.6.27-14-generic/kernel/sound/isa/snd-sc6000.ko
/lib/modules/2.6.27-14-generic/kernel/sound/isa/cs423x/snd-cs4231.ko
/lib/modules/2.6.27-14-generic/kernel/sound/isa/cs423x/snd-cs4236-lib.ko
/lib/modules/2.6.27-14-generic/kernel/sound/isa/cs423x/snd-cs4232.ko
/lib/modules/2.6.27-14-generic/kernel/sound/isa/cs423x/snd-cs4231-lib.ko
/lib/modules/2.6.27-14-generic/kernel/sound/isa/cs423x/snd-cs4236.ko
/lib/modules/2.6.27-14-generic/kernel/sound/isa/snd-sgalaxy.ko
/lib/modules/2.6.27-14-generic/kernel/sound/isa/snd-cmi8330.ko
/lib/modules/2.6.27-14-generic/kernel/sound/isa/snd-es18xx.ko
/lib/modules/2.6.27-14-generic/kernel/sound/isa/gus/snd-interwave-stb.ko
/lib/modules/2.6.27-14-generic/kernel/sound/isa/gus/snd-gus-lib.ko
/lib/modules/2.6.27-14-generic/kernel/sound/isa/gus/snd-gusmax.ko
/lib/modules/2.6.27-14-generic/kernel/sound/isa/gus/snd-gusclassic.ko
/lib/modules/2.6.27-14-generic/kernel/sound/isa/gus/snd-interwave.ko
/lib/modules/2.6.27-14-generic/kernel/sound/isa/gus/snd-gusextreme.ko
/lib/modules/2.6.27-14-generic/kernel/sound/pcmcia/pdaudiocf/snd-pdaudiocf.ko
/lib/modules/2.6.27-14-generic/kernel/sound/pcmcia/vx/snd-vxpocket.ko
/lib/modules/2.6.27-14-generic/kernel/ubuntu/misc/media/snd-bt-sco.ko


so....i really dont understand, also when i log in it does play the sound in the log screen but then nothing else, no sound whatsoever...and i really dont want to format my pc again...

---

