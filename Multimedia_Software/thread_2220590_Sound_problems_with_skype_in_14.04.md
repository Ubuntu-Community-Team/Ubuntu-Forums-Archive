---
title: "Sound problems with skype in 14.04"
date: 2014-04-28
forum: Multimedia Software
---

### Post by raspatan on 2014-04-28
(UPDATED POST)

Hello! 

I have a new laptop since one month ago, a HP Pavilion 15. I'm using Xubuntu 14.04 LTS, installed myself with a liveCD (replacing annoying W8). My problem is that whenever I open skype, the sound crashes, or loops constantly, like being stuck, in these two cases:

- when I adjust the volume (either with multimedia keys, volume bar or in pulseaudio)

- when I'm in a call, the sound brakes if I talk but **not** if I don't talk (I can hear the other person). So this say something about a mic problem too. 

Reinstalling skype does not help.

I have gone through [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting) but because I do get sound, it might not be appropriate for me. My outputs are: ```
lucho@lucho-HP:~$ sudo aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Generic [HD-Audio Generic], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Generic_1 [HD-Audio Generic], device 0: ALC282 Analog [ALC282 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

```

```
lucho@lucho-HP:~$ find /lib/modules/`uname -r` | grep snd
/lib/modules/3.13.0-24-generic/kernel/sound/firewire/snd-firewire-lib.ko
/lib/modules/3.13.0-24-generic/kernel/sound/firewire/snd-isight.ko
/lib/modules/3.13.0-24-generic/kernel/sound/firewire/snd-firewire-speakers.ko
/lib/modules/3.13.0-24-generic/kernel/sound/firewire/snd-dice.ko
/lib/modules/3.13.0-24-generic/kernel/sound/firewire/snd-scs1x.ko
/lib/modules/3.13.0-24-generic/kernel/sound/core/snd.ko
/lib/modules/3.13.0-24-generic/kernel/sound/core/snd-timer.ko
/lib/modules/3.13.0-24-generic/kernel/sound/core/snd-compress.ko
/lib/modules/3.13.0-24-generic/kernel/sound/core/snd-hwdep.ko
/lib/modules/3.13.0-24-generic/kernel/sound/core/seq/snd-seq-midi.ko
/lib/modules/3.13.0-24-generic/kernel/sound/core/seq/snd-seq-device.ko
/lib/modules/3.13.0-24-generic/kernel/sound/core/seq/snd-seq-virmidi.ko
/lib/modules/3.13.0-24-generic/kernel/sound/core/seq/snd-seq-dummy.ko
/lib/modules/3.13.0-24-generic/kernel/sound/core/seq/snd-seq-midi-emul.ko
/lib/modules/3.13.0-24-generic/kernel/sound/core/seq/snd-seq-midi-event.ko
/lib/modules/3.13.0-24-generic/kernel/sound/core/seq/snd-seq.ko
/lib/modules/3.13.0-24-generic/kernel/sound/core/snd-page-alloc.ko
/lib/modules/3.13.0-24-generic/kernel/sound/core/snd-pcm.ko
/lib/modules/3.13.0-24-generic/kernel/sound/core/snd-hrtimer.ko
/lib/modules/3.13.0-24-generic/kernel/sound/core/snd-rawmidi.ko
/lib/modules/3.13.0-24-generic/kernel/sound/pcmcia/pdaudiocf/snd-pdaudiocf.ko
/lib/modules/3.13.0-24-generic/kernel/sound/pcmcia/vx/snd-vxpocket.ko
/lib/modules/3.13.0-24-generic/kernel/sound/spi/snd-at73c213.ko
/lib/modules/3.13.0-24-generic/kernel/sound/isa/sb/snd-sb-common.ko
/lib/modules/3.13.0-24-generic/kernel/sound/isa/sb/snd-sb16-dsp.ko
/lib/modules/3.13.0-24-generic/kernel/sound/synth/emux/snd-emux-synth.ko
/lib/modules/3.13.0-24-generic/kernel/sound/synth/snd-util-mem.ko
/lib/modules/3.13.0-24-generic/kernel/sound/drivers/snd-portman2x4.ko
/lib/modules/3.13.0-24-generic/kernel/sound/drivers/snd-serial-u16550.ko
/lib/modules/3.13.0-24-generic/kernel/sound/drivers/snd-dummy.ko
/lib/modules/3.13.0-24-generic/kernel/sound/drivers/opl3/snd-opl3-lib.ko
/lib/modules/3.13.0-24-generic/kernel/sound/drivers/opl3/snd-opl3-synth.ko
/lib/modules/3.13.0-24-generic/kernel/sound/drivers/snd-mts64.ko
/lib/modules/3.13.0-24-generic/kernel/sound/drivers/mpu401/snd-mpu401-uart.ko
/lib/modules/3.13.0-24-generic/kernel/sound/drivers/mpu401/snd-mpu401.ko
/lib/modules/3.13.0-24-generic/kernel/sound/drivers/snd-mtpav.ko
/lib/modules/3.13.0-24-generic/kernel/sound/drivers/pcsp/snd-pcsp.ko
/lib/modules/3.13.0-24-generic/kernel/sound/drivers/snd-virmidi.ko
/lib/modules/3.13.0-24-generic/kernel/sound/drivers/vx/snd-vx-lib.ko
/lib/modules/3.13.0-24-generic/kernel/sound/drivers/snd-aloop.ko
/lib/modules/3.13.0-24-generic/kernel/sound/i2c/snd-cs8427.ko
/lib/modules/3.13.0-24-generic/kernel/sound/i2c/other/snd-ak4113.ko
/lib/modules/3.13.0-24-generic/kernel/sound/i2c/other/snd-ak4114.ko
/lib/modules/3.13.0-24-generic/kernel/sound/i2c/other/snd-ak4117.ko
/lib/modules/3.13.0-24-generic/kernel/sound/i2c/other/snd-ak4xxx-adda.ko
/lib/modules/3.13.0-24-generic/kernel/sound/i2c/other/snd-pt2258.ko
/lib/modules/3.13.0-24-generic/kernel/sound/i2c/snd-i2c.ko
/lib/modules/3.13.0-24-generic/kernel/sound/usb/6fire/snd-usb-6fire.ko
/lib/modules/3.13.0-24-generic/kernel/sound/usb/snd-usbmidi-lib.ko
/lib/modules/3.13.0-24-generic/kernel/sound/usb/snd-usb-audio.ko
/lib/modules/3.13.0-24-generic/kernel/sound/usb/hiface/snd-usb-hiface.ko
/lib/modules/3.13.0-24-generic/kernel/sound/usb/usx2y/snd-usb-us122l.ko
/lib/modules/3.13.0-24-generic/kernel/sound/usb/usx2y/snd-usb-usx2y.ko
/lib/modules/3.13.0-24-generic/kernel/sound/usb/misc/snd-ua101.ko
/lib/modules/3.13.0-24-generic/kernel/sound/usb/caiaq/snd-usb-caiaq.ko
/lib/modules/3.13.0-24-generic/kernel/sound/soc/atmel/snd-soc-atmel-pcm.ko
/lib/modules/3.13.0-24-generic/kernel/sound/soc/snd-soc-core.ko
/lib/modules/3.13.0-24-generic/kernel/sound/soc/generic/snd-soc-simple-card.ko
/lib/modules/3.13.0-24-generic/kernel/sound/soc/codecs/snd-soc-si476x.ko
/lib/modules/3.13.0-24-generic/kernel/sound/pci/asihpi/snd-asihpi.ko
/lib/modules/3.13.0-24-generic/kernel/sound/pci/snd-via82xx-modem.ko
/lib/modules/3.13.0-24-generic/kernel/sound/pci/mixart/snd-mixart.ko
/lib/modules/3.13.0-24-generic/kernel/sound/pci/hda/snd-hda-codec-conexant.ko
/lib/modules/3.13.0-24-generic/kernel/sound/pci/hda/snd-hda-codec.ko
/lib/modules/3.13.0-24-generic/kernel/sound/pci/hda/snd-hda-codec-realtek.ko
/lib/modules/3.13.0-24-generic/kernel/sound/pci/hda/snd-hda-intel.ko
/lib/modules/3.13.0-24-generic/kernel/sound/pci/hda/snd-hda-codec-si3054.ko
/lib/modules/3.13.0-24-generic/kernel/sound/pci/hda/snd-hda-codec-cmedia.ko
/lib/modules/3.13.0-24-generic/kernel/sound/pci/hda/snd-hda-codec-hdmi.ko
/lib/modules/3.13.0-24-generic/kernel/sound/pci/hda/snd-hda-codec-ca0132.ko
/lib/modules/3.13.0-24-generic/kernel/sound/pci/hda/snd-hda-codec-via.ko
/lib/modules/3.13.0-24-generic/kernel/sound/pci/hda/snd-hda-codec-idt.ko
/lib/modules/3.13.0-24-generic/kernel/sound/pci/hda/snd-hda-codec-analog.ko
/lib/modules/3.13.0-24-generic/kernel/sound/pci/hda/snd-hda-codec-ca0110.ko
/lib/modules/3.13.0-24-generic/kernel/sound/pci/hda/snd-hda-codec-cirrus.ko
/lib/modules/3.13.0-24-generic/kernel/sound/pci/korg1212/snd-korg1212.ko
/lib/modules/3.13.0-24-generic/kernel/sound/pci/snd-ens1371.ko
/lib/modules/3.13.0-24-generic/kernel/sound/pci/ac97/snd-ac97-codec.ko
/lib/modules/3.13.0-24-generic/kernel/sound/pci/snd-es1968.ko
/lib/modules/3.13.0-24-generic/kernel/sound/pci/pcxhr/snd-pcxhr.ko
/lib/modules/3.13.0-24-generic/kernel/sound/pci/snd-cs4281.ko
/lib/modules/3.13.0-24-generic/kernel/sound/pci/snd-atiixp-modem.ko
/lib/modules/3.13.0-24-generic/kernel/sound/pci/snd-sonicvibes.ko
/lib/modules/3.13.0-24-generic/kernel/sound/pci/aw2/snd-aw2.ko
/lib/modules/3.13.0-24-generic/kernel/sound/pci/emu10k1/snd-emu10k1-synth.ko
/lib/modules/3.13.0-24-generic/kernel/sound/pci/emu10k1/snd-emu10k1.ko
/lib/modules/3.13.0-24-generic/kernel/sound/pci/emu10k1/snd-emu10k1x.ko
/lib/modules/3.13.0-24-generic/kernel/sound/pci/ali5451/snd-ali5451.ko
/lib/modules/3.13.0-24-generic/kernel/sound/pci/snd-fm801.ko
/lib/modules/3.13.0-24-generic/kernel/sound/pci/snd-intel8x0m.ko
/lib/modules/3.13.0-24-generic/kernel/sound/pci/snd-atiixp.ko
/lib/modules/3.13.0-24-generic/kernel/sound/pci/au88x0/snd-au8830.ko
/lib/modules/3.13.0-24-generic/kernel/sound/pci/au88x0/snd-au8810.ko
/lib/modules/3.13.0-24-generic/kernel/sound/pci/au88x0/snd-au8820.ko
/lib/modules/3.13.0-24-generic/kernel/sound/pci/riptide/snd-riptide.ko
/lib/modules/3.13.0-24-generic/kernel/sound/pci/snd-rme96.ko
/lib/modules/3.13.0-24-generic/kernel/sound/pci/ice1712/snd-ice17xx-ak4xxx.ko
/lib/modules/3.13.0-24-generic/kernel/sound/pci/ice1712/snd-ice1724.ko
/lib/modules/3.13.0-24-generic/kernel/sound/pci/ice1712/snd-ice1712.ko
/lib/modules/3.13.0-24-generic/kernel/sound/pci/ctxfi/snd-ctxfi.ko
/lib/modules/3.13.0-24-generic/kernel/sound/pci/rme9652/snd-hdsp.ko
/lib/modules/3.13.0-24-generic/kernel/sound/pci/rme9652/snd-hdspm.ko
/lib/modules/3.13.0-24-generic/kernel/sound/pci/rme9652/snd-rme9652.ko
/lib/modules/3.13.0-24-generic/kernel/sound/pci/snd-bt87x.ko
/lib/modules/3.13.0-24-generic/kernel/sound/pci/snd-als4000.ko
/lib/modules/3.13.0-24-generic/kernel/sound/pci/lola/snd-lola.ko
/lib/modules/3.13.0-24-generic/kernel/sound/pci/ymfpci/snd-ymfpci.ko
/lib/modules/3.13.0-24-generic/kernel/sound/pci/cs46xx/snd-cs46xx.ko
/lib/modules/3.13.0-24-generic/kernel/sound/pci/snd-maestro3.ko
/lib/modules/3.13.0-24-generic/kernel/sound/pci/snd-azt3328.ko
/lib/modules/3.13.0-24-generic/kernel/sound/pci/snd-ad1889.ko
/lib/modules/3.13.0-24-generic/kernel/sound/pci/snd-cs5530.ko
/lib/modules/3.13.0-24-generic/kernel/sound/pci/snd-ens1370.ko
/lib/modules/3.13.0-24-generic/kernel/sound/pci/snd-als300.ko
/lib/modules/3.13.0-24-generic/kernel/sound/pci/snd-cmipci.ko
/lib/modules/3.13.0-24-generic/kernel/sound/pci/vx222/snd-vx222.ko
/lib/modules/3.13.0-24-generic/kernel/sound/pci/lx6464es/snd-lx6464es.ko
/lib/modules/3.13.0-24-generic/kernel/sound/pci/cs5535audio/snd-cs5535audio.ko
/lib/modules/3.13.0-24-generic/kernel/sound/pci/snd-rme32.ko
/lib/modules/3.13.0-24-generic/kernel/sound/pci/snd-via82xx.ko
/lib/modules/3.13.0-24-generic/kernel/sound/pci/snd-intel8x0.ko
/lib/modules/3.13.0-24-generic/kernel/sound/pci/oxygen/snd-oxygen-lib.ko
/lib/modules/3.13.0-24-generic/kernel/sound/pci/oxygen/snd-virtuoso.ko
/lib/modules/3.13.0-24-generic/kernel/sound/pci/oxygen/snd-oxygen.ko
/lib/modules/3.13.0-24-generic/kernel/sound/pci/echoaudio/snd-echo3g.ko
/lib/modules/3.13.0-24-generic/kernel/sound/pci/echoaudio/snd-indigoio.ko
/lib/modules/3.13.0-24-generic/kernel/sound/pci/echoaudio/snd-layla20.ko
/lib/modules/3.13.0-24-generic/kernel/sound/pci/echoaudio/snd-layla24.ko
/lib/modules/3.13.0-24-generic/kernel/sound/pci/echoaudio/snd-gina20.ko
/lib/modules/3.13.0-24-generic/kernel/sound/pci/echoaudio/snd-gina24.ko
/lib/modules/3.13.0-24-generic/kernel/sound/pci/echoaudio/snd-indigo.ko
/lib/modules/3.13.0-24-generic/kernel/sound/pci/echoaudio/snd-mona.ko
/lib/modules/3.13.0-24-generic/kernel/sound/pci/echoaudio/snd-darla24.ko
/lib/modules/3.13.0-24-generic/kernel/sound/pci/echoaudio/snd-mia.ko
/lib/modules/3.13.0-24-generic/kernel/sound/pci/echoaudio/snd-indigoiox.ko
/lib/modules/3.13.0-24-generic/kernel/sound/pci/echoaudio/snd-indigodjx.ko
/lib/modules/3.13.0-24-generic/kernel/sound/pci/echoaudio/snd-indigodj.ko
/lib/modules/3.13.0-24-generic/kernel/sound/pci/echoaudio/snd-darla20.ko
/lib/modules/3.13.0-24-generic/kernel/sound/pci/snd-es1938.ko
/lib/modules/3.13.0-24-generic/kernel/sound/pci/ca0106/snd-ca0106.ko
/lib/modules/3.13.0-24-generic/kernel/sound/pci/nm256/snd-nm256.ko
/lib/modules/3.13.0-24-generic/kernel/sound/pci/trident/snd-trident.ko

```

```
lspci -v | grep -A7 -i "audio"
00:01.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Device 9840
    Subsystem: Hewlett-Packard Company Device 2170
    Flags: bus master, fast devsel, latency 0, IRQ 81
    Memory at f0440000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel

00:02.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Function 0
--
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD] FCH Azalia Controller (rev 02)
    Subsystem: Hewlett-Packard Company Device 2170
    Flags: bus master, slow devsel, latency 32, IRQ 82
    Memory at f0444000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel

00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD] FCH LPC Bridge (rev 11)
```

I am a bit afraid of reinstalling the sound drivers as the guide seems a bit outdated. The other guide available ([https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)) seems even more scary so I haven't done anything of it. I'm still new to linux. 

Thank you in advance, and hopefully I will not have to reinstall all over again. I can use synaptic if needed. Should I need to delete pulsaudio and replace it with something else?

Best.

---

### Post by raspatan on 2014-04-28
Updated post above so deleted this one.

---

### Post by dannyboy79 on 2014-04-29
try editing sudo gedit /etc/pulse/default.pa and adding &#8220;tsched=0&#8243; to the end of the line &#8220;load-module module-udev-detect&#8221;

---

### Post by raspatan on 2014-05-03
well, I did that and didn't work. But then, after a few days, it started working (although the video has some weird green-purple noise, perhaps due to AMD driver issues). Cannot tell why its working now. Some update? The tsched=0 adjustment? Well, thank you anyway!

---

### Post by carlosjordao on 2014-05-05
appending that seems to work for me. Thanks

---

### Post by raspatan on 2014-05-06
> **carlosjordao said:**
> appending that seems to work for me. Thanks

Hi Carlos, welcome to the forum. 

Good that it worked for you. Did you have a similar problem?

I marked the thread as unsolved again because the problem came back: sound crashing after opening Skype. So dannyboy's solution didn&#8217;t work for me. 

However, I think I have isolated the problem. Notice from my above outputs that I have one soundcard, HD-Audio Generic with two chips: Ati R6xx HDMI and Realtek ALC282 Analog. I have nothing loaded in the HDMI one, don't know why and how make it work. HDMI cable? So I can only test this problem with the Realtek. So: 

1) I start a song in gmusicbrowser
2) I go to alsamixer (in terminal). I select the second sound card (alsamixer has the HDMI one as default. Should I change this in alsa-base.conf?).
3) Moving around different items (master, speaker, mic, etc) does not crash the sound. 
4) Changing master volume does not crash the sound.
5) Changing other items' volume (Headphone, PCM, Mic...) does crash the sound (it is slow, looping, very buggy) (don't know the proper word in English for this, sorry).
6) runing pulseaudio -k && pulseaudio --start does not restore sound quality (after reopening gmusicbrowser songs are still playing buggy).
7) running pulseaudio -k && sudo alsa force-reload restart sound entirely, not needing to reopen gmusicbrowser.

[IMG]http://i59.tinypic.com/2qwgbhz.png[/IMG]

Two things: point number 5) only happens from time to time. Sometimes I just cannot crash the sound intentionally by doing 5). Sometimes it happens immediately. (reason why skype worked before?)

So, that is the problem. Skype crashes because it uses the mic? 

Is this a hardware issue? Should I reinstall alsa? Replace it with OSS? Notice that before using Xubuntu 14.04 I used Xubuntu 14.04 Beta2, and skype worked fine so hopefully this is not a hardware problem! 

Thank you!

---

### Post by raspatan on 2014-05-07
Is there a problem in my alsa configuration? Perhaps I need to disable the HDMI device (blacklist snd_hda_codec_hdmi), or put the other one as default? 

here is the content of my alsa-base.conf but I don't understand much of it. 

```
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-caiaq index=-2
options snd-usb-ua101 index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Keep snd-usb-audio from beeing loaded as first soundcard
options snd-usb-audio index=-2
```

---

