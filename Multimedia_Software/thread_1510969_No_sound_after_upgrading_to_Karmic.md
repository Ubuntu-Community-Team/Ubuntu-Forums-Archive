---
title: "No sound after upgrading to Karmic"
date: 2010-06-16
forum: Multimedia Software
---

### Post by jocampo on 2010-06-16
Hi all,

I must say that I searched other threads but have found no solution to my problem. Still, if someone knows about a useful link please feel free to reply and let me know. I am not trying to post a repetitive thread but so far I've had no luck.

Simple..I just upgraded to Karmic and since then, mouse and sound on my laptop stop working. I fixed the touchpad problem but no sound yet.

My laptop is a Presario CQ60.

Here's the audio relevant portion taken from lspci

```
00:07.0 Audio device: nVidia Corporation MCP72XE/MCP72P/MCP78U/MCP78S High Definition Audio (rev a1)
	Subsystem: Hewlett-Packard Company Device 360a
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0 (500ns min, 1250ns max)
	Interrupt: pin A routed to IRQ 19
	Region 0: Memory at c0000000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel
```


Thanks in advance,

---

### Post by dino99 on 2010-06-16
install paprefs and gnome-alsamixer (set your prefs: apps sound gnome-alsamixer)

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

---

### Post by jocampo on 2010-06-16
> **dino99 said:**
> install paprefs and gnome-alsamixer (set your prefs: apps sound gnome-alsamixer)

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

Great link!

I am at work now, will give a try later at home and keep you guys posted...

Thanks,

---

### Post by jocampo on 2010-06-16
OK...so...

I do have the sound modules ...

```
jocampo@roble:~$ find /lib/modules/`uname -r` | grep snd
/lib/modules/2.6.28-17-generic/kernel/sound/drivers/snd-serial-u16550.ko
/lib/modules/2.6.28-17-generic/kernel/sound/drivers/snd-virmidi.ko
/lib/modules/2.6.28-17-generic/kernel/sound/drivers/vx/snd-vx-lib.ko
/lib/modules/2.6.28-17-generic/kernel/sound/drivers/snd-portman2x4.ko
/lib/modules/2.6.28-17-generic/kernel/sound/drivers/mpu401/snd-mpu401.ko
/lib/modules/2.6.28-17-generic/kernel/sound/drivers/mpu401/snd-mpu401-uart.ko
/lib/modules/2.6.28-17-generic/kernel/sound/drivers/pcsp/snd-pcsp.ko
/lib/modules/2.6.28-17-generic/kernel/sound/drivers/snd-mtpav.ko
/lib/modules/2.6.28-17-generic/kernel/sound/drivers/snd-mts64.ko
/lib/modules/2.6.28-17-generic/kernel/sound/drivers/snd-dummy.ko
/lib/modules/2.6.28-17-generic/kernel/sound/drivers/opl3/snd-opl3-lib.ko
/lib/modules/2.6.28-17-generic/kernel/sound/drivers/opl3/snd-opl3-synth.ko
/lib/modules/2.6.28-17-generic/kernel/sound/usb/usx2y/snd-usb-usx2y.ko
/lib/modules/2.6.28-17-generic/kernel/sound/usb/usx2y/snd-usb-us122l.ko
/lib/modules/2.6.28-17-generic/kernel/sound/usb/snd-usb-lib.ko
/lib/modules/2.6.28-17-generic/kernel/sound/usb/caiaq/snd-usb-caiaq.ko
/lib/modules/2.6.28-17-generic/kernel/sound/usb/snd-usb-audio.ko
/lib/modules/2.6.28-17-generic/kernel/sound/pcmcia/vx/snd-vxpocket.ko
/lib/modules/2.6.28-17-generic/kernel/sound/pcmcia/pdaudiocf/snd-pdaudiocf.ko
/lib/modules/2.6.28-17-generic/kernel/sound/pci/ca0106/snd-ca0106.ko
/lib/modules/2.6.28-17-generic/kernel/sound/pci/snd-ad1889.ko
/lib/modules/2.6.28-17-generic/kernel/sound/pci/ali5451/snd-ali5451.ko
/lib/modules/2.6.28-17-generic/kernel/sound/pci/korg1212/snd-korg1212.ko
/lib/modules/2.6.28-17-generic/kernel/sound/pci/mixart/snd-mixart.ko
/lib/modules/2.6.28-17-generic/kernel/sound/pci/aw2/snd-aw2.ko
/lib/modules/2.6.28-17-generic/kernel/sound/pci/au88x0/snd-au8830.ko
/lib/modules/2.6.28-17-generic/kernel/sound/pci/au88x0/snd-au8810.ko
/lib/modules/2.6.28-17-generic/kernel/sound/pci/au88x0/snd-au8820.ko
/lib/modules/2.6.28-17-generic/kernel/sound/pci/snd-via82xx-modem.ko
/lib/modules/2.6.28-17-generic/kernel/sound/pci/snd-via82xx.ko
/lib/modules/2.6.28-17-generic/kernel/sound/pci/rme9652/snd-hdsp.ko
/lib/modules/2.6.28-17-generic/kernel/sound/pci/rme9652/snd-hdspm.ko
/lib/modules/2.6.28-17-generic/kernel/sound/pci/rme9652/snd-rme9652.ko
/lib/modules/2.6.28-17-generic/kernel/sound/pci/emu10k1/snd-emu10k1-synth.ko
/lib/modules/2.6.28-17-generic/kernel/sound/pci/emu10k1/snd-emu10k1x.ko
/lib/modules/2.6.28-17-generic/kernel/sound/pci/emu10k1/snd-emu10k1.ko
/lib/modules/2.6.28-17-generic/kernel/sound/pci/hda/snd-hda-intel.ko
/lib/modules/2.6.28-17-generic/kernel/sound/pci/snd-intel8x0.ko
/lib/modules/2.6.28-17-generic/kernel/sound/pci/snd-als300.ko
/lib/modules/2.6.28-17-generic/kernel/sound/pci/snd-intel8x0m.ko
/lib/modules/2.6.28-17-generic/kernel/sound/pci/pcxhr/snd-pcxhr.ko
/lib/modules/2.6.28-17-generic/kernel/sound/pci/snd-cs4281.ko
/lib/modules/2.6.28-17-generic/kernel/sound/pci/snd-azt3328.ko
/lib/modules/2.6.28-17-generic/kernel/sound/pci/echoaudio/snd-indigo.ko
/lib/modules/2.6.28-17-generic/kernel/sound/pci/echoaudio/snd-gina20.ko
/lib/modules/2.6.28-17-generic/kernel/sound/pci/echoaudio/snd-gina24.ko
/lib/modules/2.6.28-17-generic/kernel/sound/pci/echoaudio/snd-darla24.ko
/lib/modules/2.6.28-17-generic/kernel/sound/pci/echoaudio/snd-darla20.ko
/lib/modules/2.6.28-17-generic/kernel/sound/pci/echoaudio/snd-layla20.ko
/lib/modules/2.6.28-17-generic/kernel/sound/pci/echoaudio/snd-indigodj.ko
/lib/modules/2.6.28-17-generic/kernel/sound/pci/echoaudio/snd-indigoio.ko
/lib/modules/2.6.28-17-generic/kernel/sound/pci/echoaudio/snd-echo3g.ko
/lib/modules/2.6.28-17-generic/kernel/sound/pci/echoaudio/snd-layla24.ko
/lib/modules/2.6.28-17-generic/kernel/sound/pci/echoaudio/snd-mona.ko
/lib/modules/2.6.28-17-generic/kernel/sound/pci/echoaudio/snd-mia.ko
/lib/modules/2.6.28-17-generic/kernel/sound/pci/snd-fm801.ko
/lib/modules/2.6.28-17-generic/kernel/sound/pci/snd-maestro3.ko
/lib/modules/2.6.28-17-generic/kernel/sound/pci/snd-ens1371.ko
/lib/modules/2.6.28-17-generic/kernel/sound/pci/snd-ens1370.ko
/lib/modules/2.6.28-17-generic/kernel/sound/pci/snd-als4000.ko
/lib/modules/2.6.28-17-generic/kernel/sound/pci/snd-sonicvibes.ko
/lib/modules/2.6.28-17-generic/kernel/sound/pci/snd-es1968.ko
/lib/modules/2.6.28-17-generic/kernel/sound/pci/nm256/snd-nm256.ko
/lib/modules/2.6.28-17-generic/kernel/sound/pci/riptide/snd-riptide.ko
/lib/modules/2.6.28-17-generic/kernel/sound/pci/snd-bt87x.ko
/lib/modules/2.6.28-17-generic/kernel/sound/pci/snd-atiixp.ko
/lib/modules/2.6.28-17-generic/kernel/sound/pci/snd-cmipci.ko
/lib/modules/2.6.28-17-generic/kernel/sound/pci/ice1712/snd-ice17xx-ak4xxx.ko
/lib/modules/2.6.28-17-generic/kernel/sound/pci/ice1712/snd-ice1724.ko
/lib/modules/2.6.28-17-generic/kernel/sound/pci/ice1712/snd-ice1712.ko
/lib/modules/2.6.28-17-generic/kernel/sound/pci/snd-es1938.ko
/lib/modules/2.6.28-17-generic/kernel/sound/pci/oxygen/snd-hifier.ko
/lib/modules/2.6.28-17-generic/kernel/sound/pci/oxygen/snd-oxygen-lib.ko
/lib/modules/2.6.28-17-generic/kernel/sound/pci/oxygen/snd-virtuoso.ko
/lib/modules/2.6.28-17-generic/kernel/sound/pci/oxygen/snd-oxygen.ko
/lib/modules/2.6.28-17-generic/kernel/sound/pci/snd-atiixp-modem.ko
/lib/modules/2.6.28-17-generic/kernel/sound/pci/snd-rme96.ko
/lib/modules/2.6.28-17-generic/kernel/sound/pci/trident/snd-trident.ko
/lib/modules/2.6.28-17-generic/kernel/sound/pci/ac97/snd-ac97-codec.ko
/lib/modules/2.6.28-17-generic/kernel/sound/pci/snd-cs5530.ko
/lib/modules/2.6.28-17-generic/kernel/sound/pci/snd-rme32.ko
/lib/modules/2.6.28-17-generic/kernel/sound/pci/cs46xx/snd-cs46xx.ko
/lib/modules/2.6.28-17-generic/kernel/sound/pci/vx222/snd-vx222.ko
/lib/modules/2.6.28-17-generic/kernel/sound/pci/ymfpci/snd-ymfpci.ko
/lib/modules/2.6.28-17-generic/kernel/sound/core/seq/snd-seq-dummy.ko
/lib/modules/2.6.28-17-generic/kernel/sound/core/seq/snd-seq.ko
/lib/modules/2.6.28-17-generic/kernel/sound/core/seq/snd-seq-virmidi.ko
/lib/modules/2.6.28-17-generic/kernel/sound/core/seq/snd-seq-midi.ko
/lib/modules/2.6.28-17-generic/kernel/sound/core/seq/snd-seq-midi-emul.ko
/lib/modules/2.6.28-17-generic/kernel/sound/core/seq/oss/snd-seq-oss.ko
/lib/modules/2.6.28-17-generic/kernel/sound/core/seq/snd-seq-midi-event.ko
/lib/modules/2.6.28-17-generic/kernel/sound/core/seq/snd-seq-device.ko
/lib/modules/2.6.28-17-generic/kernel/sound/core/snd-hwdep.ko
/lib/modules/2.6.28-17-generic/kernel/sound/core/snd.ko
/lib/modules/2.6.28-17-generic/kernel/sound/core/snd-timer.ko
/lib/modules/2.6.28-17-generic/kernel/sound/core/oss/snd-pcm-oss.ko
/lib/modules/2.6.28-17-generic/kernel/sound/core/oss/snd-mixer-oss.ko
/lib/modules/2.6.28-17-generic/kernel/sound/core/snd-pcm.ko
/lib/modules/2.6.28-17-generic/kernel/sound/core/snd-page-alloc.ko
/lib/modules/2.6.28-17-generic/kernel/sound/core/snd-rawmidi.ko
/lib/modules/2.6.28-17-generic/kernel/sound/soc/snd-soc-core.ko
/lib/modules/2.6.28-17-generic/kernel/sound/soc/codecs/snd-soc-tlv320aic26.ko
/lib/modules/2.6.28-17-generic/kernel/sound/soc/codecs/snd-soc-wm8990.ko
/lib/modules/2.6.28-17-generic/kernel/sound/soc/codecs/snd-soc-tlv320aic3x.ko
/lib/modules/2.6.28-17-generic/kernel/sound/soc/codecs/snd-soc-wm8753.ko
/lib/modules/2.6.28-17-generic/kernel/sound/soc/codecs/snd-soc-tlv320aic23.ko
/lib/modules/2.6.28-17-generic/kernel/sound/soc/codecs/snd-soc-wm8900.ko
/lib/modules/2.6.28-17-generic/kernel/sound/soc/codecs/snd-soc-wm8750.ko
/lib/modules/2.6.28-17-generic/kernel/sound/soc/codecs/snd-soc-wm8971.ko
/lib/modules/2.6.28-17-generic/kernel/sound/soc/codecs/snd-soc-wm8510.ko
/lib/modules/2.6.28-17-generic/kernel/sound/soc/codecs/snd-soc-ad73311.ko
/lib/modules/2.6.28-17-generic/kernel/sound/soc/codecs/snd-soc-wm8580.ko
/lib/modules/2.6.28-17-generic/kernel/sound/soc/codecs/snd-soc-ssm2602.ko
/lib/modules/2.6.28-17-generic/kernel/sound/soc/codecs/snd-soc-ak4535.ko
/lib/modules/2.6.28-17-generic/kernel/sound/soc/codecs/snd-soc-wm8731.ko
/lib/modules/2.6.28-17-generic/kernel/sound/soc/codecs/snd-soc-cs4270.ko
/lib/modules/2.6.28-17-generic/kernel/sound/soc/codecs/snd-soc-uda1380.ko
/lib/modules/2.6.28-17-generic/kernel/sound/soc/codecs/snd-soc-wm8903.ko
/lib/modules/2.6.28-17-generic/kernel/sound/isa/sb/snd-sb-common.ko
/lib/modules/2.6.28-17-generic/kernel/sound/isa/sb/snd-sb16-dsp.ko
/lib/modules/2.6.28-17-generic/kernel/sound/synth/emux/snd-emux-synth.ko
/lib/modules/2.6.28-17-generic/kernel/sound/synth/snd-util-mem.ko
/lib/modules/2.6.28-17-generic/kernel/sound/i2c/snd-cs8427.ko
/lib/modules/2.6.28-17-generic/kernel/sound/i2c/snd-i2c.ko
/lib/modules/2.6.28-17-generic/kernel/sound/i2c/other/snd-ak4117.ko
/lib/modules/2.6.28-17-generic/kernel/sound/i2c/other/snd-tea575x-tuner.ko
/lib/modules/2.6.28-17-generic/kernel/sound/i2c/other/snd-pt2258.ko
/lib/modules/2.6.28-17-generic/kernel/sound/i2c/other/snd-ak4114.ko
/lib/modules/2.6.28-17-generic/kernel/sound/i2c/other/snd-ak4xxx-adda.ko
jocampo@roble:~$ 

```

My sound card is being recognized
```


00:07.0 Audio device: nVidia Corporation MCP72XE/MCP72P/MCP78U/MCP78S High Definition Audio (rev a1)
        Subsystem: Hewlett-Packard Company Device 360a
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 19
        Memory at c0000000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel
```

Kind of lost in what is my next step. I believe I do need to load the right module for my sound card. It was working before so my assumption is that current modules are not the right ones? ...

---

### Post by jocampo on 2010-06-17
Bump

---

### Post by jocampo on 2010-06-18
Well... this is the 1st time I had no luck getting advices from Ubuntu Forum ... lol ... 

I tried above suggestions with no luck so, I decided reinstall from scratch. Because /home and root are in different partitions was a bit easier. This time I installed Lucid Lynx instead... working like a charm!

Not sure if mark the thread as fixed though ...

---

