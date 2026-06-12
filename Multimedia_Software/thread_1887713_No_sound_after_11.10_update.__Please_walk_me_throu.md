---
title: "No sound after 11.10 update.  Please walk me through a solution."
date: 2011-11-27
forum: Multimedia Software
---

### Post by Amurko on 2011-11-27
So I've got no sound after upgrading to 11.10.  The icon for my sound is muted and I cannot drag the volume bar.

I'm loosely following the guide here to solve my sound problems but it doesn't seem to be helping.  I'll post the relevant outputs here.

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

So where do I go next?  I have no idea.

1) sudo aplay -l

Result:

```
**** List of PLAYBACK Hardware Devices ****
Home directory /home/xjdeng not ours.
card 0: Audigy2 [SB Audigy 2 ZS [SB0353]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 32/32
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
  Subdevice #31: subdevice #31
card 0: Audigy2 [SB Audigy 2 ZS [SB0353]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: Audigy2 [SB Audigy 2 ZS [SB0353]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Audigy2 [SB Audigy 2 ZS [SB0353]], device 4: p16v [p16v]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Phone [VOIP USB Phone], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

2) find /lib/modules/`uname -r` | grep snd

Result:

```
/lib/modules/3.0.0-13-generic/kernel/sound/firewire/snd-firewire-speakers.ko
/lib/modules/3.0.0-13-generic/kernel/sound/firewire/snd-isight.ko
/lib/modules/3.0.0-13-generic/kernel/sound/firewire/snd-firewire-lib.ko
/lib/modules/3.0.0-13-generic/kernel/sound/core/snd-hwdep.ko
/lib/modules/3.0.0-13-generic/kernel/sound/core/seq/snd-seq-dummy.ko
/lib/modules/3.0.0-13-generic/kernel/sound/core/seq/snd-seq-midi-emul.ko
/lib/modules/3.0.0-13-generic/kernel/sound/core/seq/snd-seq-midi-event.ko
/lib/modules/3.0.0-13-generic/kernel/sound/core/seq/snd-seq-midi.ko
/lib/modules/3.0.0-13-generic/kernel/sound/core/seq/snd-seq-virmidi.ko
/lib/modules/3.0.0-13-generic/kernel/sound/core/seq/snd-seq.ko
/lib/modules/3.0.0-13-generic/kernel/sound/core/seq/snd-seq-device.ko
/lib/modules/3.0.0-13-generic/kernel/sound/core/snd-page-alloc.ko
/lib/modules/3.0.0-13-generic/kernel/sound/core/snd-pcm.ko
/lib/modules/3.0.0-13-generic/kernel/sound/core/snd-rawmidi.ko
/lib/modules/3.0.0-13-generic/kernel/sound/core/snd-timer.ko
/lib/modules/3.0.0-13-generic/kernel/sound/core/snd.ko
/lib/modules/3.0.0-13-generic/kernel/sound/core/snd-hrtimer.ko
/lib/modules/3.0.0-13-generic/kernel/sound/drivers/snd-aloop.ko
/lib/modules/3.0.0-13-generic/kernel/sound/drivers/mpu401/snd-mpu401.ko
/lib/modules/3.0.0-13-generic/kernel/sound/drivers/mpu401/snd-mpu401-uart.ko
/lib/modules/3.0.0-13-generic/kernel/sound/drivers/opl3/snd-opl3-synth.ko
/lib/modules/3.0.0-13-generic/kernel/sound/drivers/opl3/snd-opl3-lib.ko
/lib/modules/3.0.0-13-generic/kernel/sound/drivers/pcsp/snd-pcsp.ko
/lib/modules/3.0.0-13-generic/kernel/sound/drivers/snd-dummy.ko
/lib/modules/3.0.0-13-generic/kernel/sound/drivers/snd-mtpav.ko
/lib/modules/3.0.0-13-generic/kernel/sound/drivers/snd-mts64.ko
/lib/modules/3.0.0-13-generic/kernel/sound/drivers/snd-portman2x4.ko
/lib/modules/3.0.0-13-generic/kernel/sound/drivers/snd-serial-u16550.ko
/lib/modules/3.0.0-13-generic/kernel/sound/drivers/snd-virmidi.ko
/lib/modules/3.0.0-13-generic/kernel/sound/drivers/vx/snd-vx-lib.ko
/lib/modules/3.0.0-13-generic/kernel/sound/pcmcia/pdaudiocf/snd-pdaudiocf.ko
/lib/modules/3.0.0-13-generic/kernel/sound/pcmcia/vx/snd-vxpocket.ko
/lib/modules/3.0.0-13-generic/kernel/sound/i2c/snd-cs8427.ko
/lib/modules/3.0.0-13-generic/kernel/sound/i2c/other/snd-ak4114.ko
/lib/modules/3.0.0-13-generic/kernel/sound/i2c/other/snd-ak4117.ko
/lib/modules/3.0.0-13-generic/kernel/sound/i2c/other/snd-ak4xxx-adda.ko
/lib/modules/3.0.0-13-generic/kernel/sound/i2c/other/snd-pt2258.ko
/lib/modules/3.0.0-13-generic/kernel/sound/i2c/other/snd-tea575x-tuner.ko
/lib/modules/3.0.0-13-generic/kernel/sound/i2c/other/snd-ak4113.ko
/lib/modules/3.0.0-13-generic/kernel/sound/i2c/snd-i2c.ko
/lib/modules/3.0.0-13-generic/kernel/sound/isa/sb/snd-sb16-dsp.ko
/lib/modules/3.0.0-13-generic/kernel/sound/isa/sb/snd-sb-common.ko
/lib/modules/3.0.0-13-generic/kernel/sound/pci/cs5535audio/snd-cs5535audio.ko
/lib/modules/3.0.0-13-generic/kernel/sound/pci/ac97/snd-ac97-codec.ko
/lib/modules/3.0.0-13-generic/kernel/sound/pci/ali5451/snd-ali5451.ko
/lib/modules/3.0.0-13-generic/kernel/sound/pci/asihpi/snd-asihpi.ko
/lib/modules/3.0.0-13-generic/kernel/sound/pci/au88x0/snd-au8820.ko
/lib/modules/3.0.0-13-generic/kernel/sound/pci/au88x0/snd-au8830.ko
/lib/modules/3.0.0-13-generic/kernel/sound/pci/au88x0/snd-au8810.ko
/lib/modules/3.0.0-13-generic/kernel/sound/pci/aw2/snd-aw2.ko
/lib/modules/3.0.0-13-generic/kernel/sound/pci/ca0106/snd-ca0106.ko
/lib/modules/3.0.0-13-generic/kernel/sound/pci/cs46xx/snd-cs46xx.ko
/lib/modules/3.0.0-13-generic/kernel/sound/pci/echoaudio/snd-darla24.ko
/lib/modules/3.0.0-13-generic/kernel/sound/pci/echoaudio/snd-echo3g.ko
/lib/modules/3.0.0-13-generic/kernel/sound/pci/echoaudio/snd-gina20.ko
/lib/modules/3.0.0-13-generic/kernel/sound/pci/echoaudio/snd-gina24.ko
/lib/modules/3.0.0-13-generic/kernel/sound/pci/echoaudio/snd-indigo.ko
/lib/modules/3.0.0-13-generic/kernel/sound/pci/echoaudio/snd-indigodj.ko
/lib/modules/3.0.0-13-generic/kernel/sound/pci/echoaudio/snd-indigodjx.ko
/lib/modules/3.0.0-13-generic/kernel/sound/pci/echoaudio/snd-indigoio.ko
/lib/modules/3.0.0-13-generic/kernel/sound/pci/echoaudio/snd-indigoiox.ko
/lib/modules/3.0.0-13-generic/kernel/sound/pci/echoaudio/snd-layla20.ko
/lib/modules/3.0.0-13-generic/kernel/sound/pci/echoaudio/snd-layla24.ko
/lib/modules/3.0.0-13-generic/kernel/sound/pci/echoaudio/snd-mia.ko
/lib/modules/3.0.0-13-generic/kernel/sound/pci/echoaudio/snd-mona.ko
/lib/modules/3.0.0-13-generic/kernel/sound/pci/echoaudio/snd-darla20.ko
/lib/modules/3.0.0-13-generic/kernel/sound/pci/ctxfi/snd-ctxfi.ko
/lib/modules/3.0.0-13-generic/kernel/sound/pci/korg1212/snd-korg1212.ko
/lib/modules/3.0.0-13-generic/kernel/sound/pci/emu10k1/snd-emu10k1.ko
/lib/modules/3.0.0-13-generic/kernel/sound/pci/emu10k1/snd-emu10k1x.ko
/lib/modules/3.0.0-13-generic/kernel/sound/pci/emu10k1/snd-emu10k1-synth.ko
/lib/modules/3.0.0-13-generic/kernel/sound/pci/hda/snd-hda-codec-ca0110.ko
/lib/modules/3.0.0-13-generic/kernel/sound/pci/hda/snd-hda-codec-cirrus.ko
/lib/modules/3.0.0-13-generic/kernel/sound/pci/hda/snd-hda-codec-cmedia.ko
/lib/modules/3.0.0-13-generic/kernel/sound/pci/hda/snd-hda-codec-conexant.ko
/lib/modules/3.0.0-13-generic/kernel/sound/pci/hda/snd-hda-codec-hdmi.ko
/lib/modules/3.0.0-13-generic/kernel/sound/pci/hda/snd-hda-codec-idt.ko
/lib/modules/3.0.0-13-generic/kernel/sound/pci/hda/snd-hda-codec-realtek.ko
/lib/modules/3.0.0-13-generic/kernel/sound/pci/hda/snd-hda-codec-si3054.ko
/lib/modules/3.0.0-13-generic/kernel/sound/pci/hda/snd-hda-codec-via.ko
/lib/modules/3.0.0-13-generic/kernel/sound/pci/hda/snd-hda-codec.ko
/lib/modules/3.0.0-13-generic/kernel/sound/pci/hda/snd-hda-intel.ko
/lib/modules/3.0.0-13-generic/kernel/sound/pci/hda/snd-hda-codec-analog.ko
/lib/modules/3.0.0-13-generic/kernel/sound/pci/ice1712/snd-ice1724.ko
/lib/modules/3.0.0-13-generic/kernel/sound/pci/ice1712/snd-ice17xx-ak4xxx.ko
/lib/modules/3.0.0-13-generic/kernel/sound/pci/ice1712/snd-ice1712.ko
/lib/modules/3.0.0-13-generic/kernel/sound/pci/lx6464es/snd-lx6464es.ko
/lib/modules/3.0.0-13-generic/kernel/sound/pci/lola/snd-lola.ko
/lib/modules/3.0.0-13-generic/kernel/sound/pci/snd-ad1889.ko
/lib/modules/3.0.0-13-generic/kernel/sound/pci/mixart/snd-mixart.ko
/lib/modules/3.0.0-13-generic/kernel/sound/pci/nm256/snd-nm256.ko
/lib/modules/3.0.0-13-generic/kernel/sound/pci/oxygen/snd-oxygen.ko
/lib/modules/3.0.0-13-generic/kernel/sound/pci/oxygen/snd-virtuoso.ko
/lib/modules/3.0.0-13-generic/kernel/sound/pci/oxygen/snd-oxygen-lib.ko
/lib/modules/3.0.0-13-generic/kernel/sound/pci/pcxhr/snd-pcxhr.ko
/lib/modules/3.0.0-13-generic/kernel/sound/pci/riptide/snd-riptide.ko
/lib/modules/3.0.0-13-generic/kernel/sound/pci/rme9652/snd-hdspm.ko
/lib/modules/3.0.0-13-generic/kernel/sound/pci/rme9652/snd-rme9652.ko
/lib/modules/3.0.0-13-generic/kernel/sound/pci/rme9652/snd-hdsp.ko
/lib/modules/3.0.0-13-generic/kernel/sound/pci/snd-als300.ko
/lib/modules/3.0.0-13-generic/kernel/sound/pci/snd-als4000.ko
/lib/modules/3.0.0-13-generic/kernel/sound/pci/snd-atiixp-modem.ko
/lib/modules/3.0.0-13-generic/kernel/sound/pci/snd-atiixp.ko
/lib/modules/3.0.0-13-generic/kernel/sound/pci/snd-azt3328.ko
/lib/modules/3.0.0-13-generic/kernel/sound/pci/snd-bt87x.ko
/lib/modules/3.0.0-13-generic/kernel/sound/pci/snd-cmipci.ko
/lib/modules/3.0.0-13-generic/kernel/sound/pci/snd-cs4281.ko
/lib/modules/3.0.0-13-generic/kernel/sound/pci/snd-cs5530.ko
/lib/modules/3.0.0-13-generic/kernel/sound/pci/snd-ens1370.ko
/lib/modules/3.0.0-13-generic/kernel/sound/pci/snd-ens1371.ko
/lib/modules/3.0.0-13-generic/kernel/sound/pci/snd-es1938.ko
/lib/modules/3.0.0-13-generic/kernel/sound/pci/snd-es1968.ko
/lib/modules/3.0.0-13-generic/kernel/sound/pci/snd-fm801.ko
/lib/modules/3.0.0-13-generic/kernel/sound/pci/snd-intel8x0.ko
/lib/modules/3.0.0-13-generic/kernel/sound/pci/snd-intel8x0m.ko
/lib/modules/3.0.0-13-generic/kernel/sound/pci/snd-maestro3.ko
/lib/modules/3.0.0-13-generic/kernel/sound/pci/snd-rme32.ko
/lib/modules/3.0.0-13-generic/kernel/sound/pci/snd-rme96.ko
/lib/modules/3.0.0-13-generic/kernel/sound/pci/snd-sonicvibes.ko
/lib/modules/3.0.0-13-generic/kernel/sound/pci/snd-via82xx-modem.ko
/lib/modules/3.0.0-13-generic/kernel/sound/pci/snd-via82xx.ko
/lib/modules/3.0.0-13-generic/kernel/sound/pci/trident/snd-trident.ko
/lib/modules/3.0.0-13-generic/kernel/sound/pci/vx222/snd-vx222.ko
/lib/modules/3.0.0-13-generic/kernel/sound/pci/ymfpci/snd-ymfpci.ko
/lib/modules/3.0.0-13-generic/kernel/sound/synth/snd-util-mem.ko
/lib/modules/3.0.0-13-generic/kernel/sound/synth/emux/snd-emux-synth.ko
/lib/modules/3.0.0-13-generic/kernel/sound/soc/snd-soc-core.ko
/lib/modules/3.0.0-13-generic/kernel/sound/soc/codecs/snd-soc-ad1836.ko
/lib/modules/3.0.0-13-generic/kernel/sound/soc/codecs/snd-soc-ad193x.ko
/lib/modules/3.0.0-13-generic/kernel/sound/soc/codecs/snd-soc-ad73311.ko
/lib/modules/3.0.0-13-generic/kernel/sound/soc/codecs/snd-soc-ads117x.ko
/lib/modules/3.0.0-13-generic/kernel/sound/soc/codecs/snd-soc-ak4104.ko
/lib/modules/3.0.0-13-generic/kernel/sound/soc/codecs/snd-soc-ak4535.ko
/lib/modules/3.0.0-13-generic/kernel/sound/soc/codecs/snd-soc-ak4641.ko
/lib/modules/3.0.0-13-generic/kernel/sound/soc/codecs/snd-soc-ak4642.ko
/lib/modules/3.0.0-13-generic/kernel/sound/soc/codecs/snd-soc-ak4671.ko
/lib/modules/3.0.0-13-generic/kernel/sound/soc/codecs/snd-soc-alc5623.ko
/lib/modules/3.0.0-13-generic/kernel/sound/soc/codecs/snd-soc-cs4270.ko
/lib/modules/3.0.0-13-generic/kernel/sound/soc/codecs/snd-soc-cs4271.ko
/lib/modules/3.0.0-13-generic/kernel/sound/soc/codecs/snd-soc-cs42l51.ko
/lib/modules/3.0.0-13-generic/kernel/sound/soc/codecs/snd-soc-cx20442.ko
/lib/modules/3.0.0-13-generic/kernel/sound/soc/codecs/snd-soc-da7210.ko
/lib/modules/3.0.0-13-generic/kernel/sound/soc/codecs/snd-soc-dfbmcs320.ko
/lib/modules/3.0.0-13-generic/kernel/sound/soc/codecs/snd-soc-l3.ko
/lib/modules/3.0.0-13-generic/kernel/sound/soc/codecs/snd-soc-lm4857.ko
/lib/modules/3.0.0-13-generic/kernel/sound/soc/codecs/snd-soc-max98088.ko
/lib/modules/3.0.0-13-generic/kernel/sound/soc/codecs/snd-soc-max98095.ko
/lib/modules/3.0.0-13-generic/kernel/sound/soc/codecs/snd-soc-max9850.ko
/lib/modules/3.0.0-13-generic/kernel/sound/soc/codecs/snd-soc-max9877.ko
/lib/modules/3.0.0-13-generic/kernel/sound/soc/codecs/snd-soc-pcm3008.ko
/lib/modules/3.0.0-13-generic/kernel/sound/soc/codecs/snd-soc-sgtl5000.ko
/lib/modules/3.0.0-13-generic/kernel/sound/soc/codecs/snd-soc-spdif.ko
/lib/modules/3.0.0-13-generic/kernel/sound/soc/codecs/snd-soc-ssm2602.ko
/lib/modules/3.0.0-13-generic/kernel/sound/soc/codecs/snd-soc-tlv320aic23.ko
/lib/modules/3.0.0-13-generic/kernel/sound/soc/codecs/snd-soc-tlv320aic26.ko
/lib/modules/3.0.0-13-generic/kernel/sound/soc/codecs/snd-soc-tlv320aic32x4.ko
/lib/modules/3.0.0-13-generic/kernel/sound/soc/codecs/snd-soc-tlv320aic3x.ko
/lib/modules/3.0.0-13-generic/kernel/sound/soc/codecs/snd-soc-tlv320dac33.ko
/lib/modules/3.0.0-13-generic/kernel/sound/soc/codecs/snd-soc-tpa6130a2.ko
/lib/modules/3.0.0-13-generic/kernel/sound/soc/codecs/snd-soc-uda134x.ko
/lib/modules/3.0.0-13-generic/kernel/sound/soc/codecs/snd-soc-uda1380.ko
/lib/modules/3.0.0-13-generic/kernel/sound/soc/codecs/snd-soc-wl1273.ko
/lib/modules/3.0.0-13-generic/kernel/sound/soc/codecs/snd-soc-wm-hubs.ko
/lib/modules/3.0.0-13-generic/kernel/sound/soc/codecs/snd-soc-wm1250-ev1.ko
/lib/modules/3.0.0-13-generic/kernel/sound/soc/codecs/snd-soc-wm2000.ko
/lib/modules/3.0.0-13-generic/kernel/sound/soc/codecs/snd-soc-wm8350.ko
/lib/modules/3.0.0-13-generic/kernel/sound/soc/codecs/snd-soc-wm8400.ko
/lib/modules/3.0.0-13-generic/kernel/sound/soc/codecs/snd-soc-wm8510.ko
/lib/modules/3.0.0-13-generic/kernel/sound/soc/codecs/snd-soc-wm8523.ko
/lib/modules/3.0.0-13-generic/kernel/sound/soc/codecs/snd-soc-wm8580.ko
/lib/modules/3.0.0-13-generic/kernel/sound/soc/codecs/snd-soc-wm8711.ko
/lib/modules/3.0.0-13-generic/kernel/sound/soc/codecs/snd-soc-wm8727.ko
/lib/modules/3.0.0-13-generic/kernel/sound/soc/codecs/snd-soc-wm8728.ko
/lib/modules/3.0.0-13-generic/kernel/sound/soc/codecs/snd-soc-wm8731.ko
/lib/modules/3.0.0-13-generic/kernel/sound/soc/codecs/snd-soc-wm8737.ko
/lib/modules/3.0.0-13-generic/kernel/sound/soc/codecs/snd-soc-wm8741.ko
/lib/modules/3.0.0-13-generic/kernel/sound/soc/codecs/snd-soc-wm8750.ko
/lib/modules/3.0.0-13-generic/kernel/sound/soc/codecs/snd-soc-wm8753.ko
/lib/modules/3.0.0-13-generic/kernel/sound/soc/codecs/snd-soc-wm8770.ko
/lib/modules/3.0.0-13-generic/kernel/sound/soc/codecs/snd-soc-wm8776.ko
/lib/modules/3.0.0-13-generic/kernel/sound/soc/codecs/snd-soc-wm8804.ko
/lib/modules/3.0.0-13-generic/kernel/sound/soc/codecs/snd-soc-wm8900.ko
/lib/modules/3.0.0-13-generic/kernel/sound/soc/codecs/snd-soc-wm8903.ko
/lib/modules/3.0.0-13-generic/kernel/sound/soc/codecs/snd-soc-wm8904.ko
/lib/modules/3.0.0-13-generic/kernel/sound/soc/codecs/snd-soc-wm8915.ko
/lib/modules/3.0.0-13-generic/kernel/sound/soc/codecs/snd-soc-wm8940.ko
/lib/modules/3.0.0-13-generic/kernel/sound/soc/codecs/snd-soc-wm8955.ko
/lib/modules/3.0.0-13-generic/kernel/sound/soc/codecs/snd-soc-wm8960.ko
/lib/modules/3.0.0-13-generic/kernel/sound/soc/codecs/snd-soc-wm8961.ko
/lib/modules/3.0.0-13-generic/kernel/sound/soc/codecs/snd-soc-wm8962.ko
/lib/modules/3.0.0-13-generic/kernel/sound/soc/codecs/snd-soc-wm8971.ko
/lib/modules/3.0.0-13-generic/kernel/sound/soc/codecs/snd-soc-wm8974.ko
/lib/modules/3.0.0-13-generic/kernel/sound/soc/codecs/snd-soc-wm8978.ko
/lib/modules/3.0.0-13-generic/kernel/sound/soc/codecs/snd-soc-wm8985.ko
/lib/modules/3.0.0-13-generic/kernel/sound/soc/codecs/snd-soc-wm8988.ko
/lib/modules/3.0.0-13-generic/kernel/sound/soc/codecs/snd-soc-wm8990.ko
/lib/modules/3.0.0-13-generic/kernel/sound/soc/codecs/snd-soc-wm8991.ko
/lib/modules/3.0.0-13-generic/kernel/sound/soc/codecs/snd-soc-wm8993.ko
/lib/modules/3.0.0-13-generic/kernel/sound/soc/codecs/snd-soc-wm8994.ko
/lib/modules/3.0.0-13-generic/kernel/sound/soc/codecs/snd-soc-wm8995.ko
/lib/modules/3.0.0-13-generic/kernel/sound/soc/codecs/snd-soc-wm9081.ko
/lib/modules/3.0.0-13-generic/kernel/sound/soc/codecs/snd-soc-wm9090.ko
/lib/modules/3.0.0-13-generic/kernel/sound/soc/codecs/snd-soc-88pm860x.ko
/lib/modules/3.0.0-13-generic/kernel/sound/usb/snd-usb-audio.ko
/lib/modules/3.0.0-13-generic/kernel/sound/usb/caiaq/snd-usb-caiaq.ko
/lib/modules/3.0.0-13-generic/kernel/sound/usb/misc/snd-ua101.ko
/lib/modules/3.0.0-13-generic/kernel/sound/usb/snd-usbmidi-lib.ko
/lib/modules/3.0.0-13-generic/kernel/sound/usb/usx2y/snd-usb-usx2y.ko
/lib/modules/3.0.0-13-generic/kernel/sound/usb/usx2y/snd-usb-us122l.ko

```

3) lspci -v | grep -A7 -i "audio"

Result:

```
00:08.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
	Subsystem: Creative Labs Device 1003
	Flags: bus master, medium devsel, latency 64, IRQ 16
	I/O ports at ec00 [size=64]
	Capabilities: <access denied>
	Kernel driver in use: EMU10K1_Audigy
	Kernel modules: snd-emu10k1

```

I also tried the following and still didn't solve the problem:

```
sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2
```

---

### Post by scotticussa on 2011-12-03
I just installed Ubuntu 11.10 as well and I was having the same issue.  I have the Audigy 2 sound card as well.

I found a site that claimed they might have a solution, and I tried it.  I had to fiddle with the settings but it worked!

Here is the sight, [http://www.futuredesktop.org/](http://www.futuredesktop.org/)  just scroll to the bottom and follow the directions.  OR I have the terminal inputs here, just copy and paste.

sudo apt-get install gnome-alsamixer

If that does not install you may have to try:

sudo apt-get -f install

first.  Once you get the gnome-alsamixer installed you will have to start it by typing in:

gnome-alsamixer

Once it opens, un-mute the master volume,
click on the second folder tab at the top,
then check the box next to "Audigy Analog/Digital Output Jack"

That might work for you.  It did for me.

---

