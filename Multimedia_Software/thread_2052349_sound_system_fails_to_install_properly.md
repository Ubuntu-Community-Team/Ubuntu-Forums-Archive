---
title: "sound system fails to install properly"
date: 2012-09-03
forum: Multimedia Software
---

### Post by goodbye-windows(tm) on 2012-09-03
Hi All,

I recently upgraded my old P4 mobo with an Asus M5A78L-M LX and an FX4100 processor. It flies, with a fully loaded/configured system running Xubuntu 12.04, it boots in 35 seconds and shuts down in 7 seconds.

There is a problem however.......

The sound system failed to totally install. I have no sound output and google voice tells me I have no audio output and no mic connected and refuses to install their voice chat software. Same with skype.

I installed the alsa mixer, no difference.

Attached are the screenshots of my volume control output devices, the input devices and  and the configuration tab(s).

I do have an old ac97 audio front panel connections, but these wires were not connected during the install. The mobo supports ac97 legacy sound or HDaudio, depending on the setting in the bios.....same 10 pin connector for both sound systems but bios must be configured properly to make the sound work.

When the first install didn't have any sound, I changed the bios setting to ac97 and installed again (on a second HDD). Both installs show exactly the same problem, as stated above. I have both drives installed, so I can boot from either drive to test with.

I believe I need to totally uninstall the sound system and reinstall, but don't have any idea how to make sure I uninstall everything and also eliminate configuration files that might get reused during the reinstall.

I should also say my nephew bought the same mobo and processor, and had no problems with his hardware upgrade, also running Xubuntu 12.04.

 Any help would be appreciated.

TY.

Art

---

### Post by opensshd on 2012-09-03
Need more info :)

Anything here help? [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

If still stuck, come back and post output from
```
lspci -v | grep -A7 -i "audio"
```

---

### Post by goodbye-windows(tm) on 2012-09-03
ty openssh.

I can't give the output of the command yet. The command gives no output. I added a 'sudo', but I'm not able to use sudo as I am not a member of the admin group, need to change that soon.

I also should have mentioned that the sound card is not a pci plug in pcb, it is integrated on the mobo. 

I will look over the url you gave, and many tnx for the nudge towards appropriate info.

Regards,

Art

---

### Post by goodbye-windows(tm) on 2012-09-03
> **opensshd said:**
> Need more info :)

Anything here help? [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

If still stuck, come back and post output from
```
lspci -v | grep -A7 -i "audio"
```

There is no output from the command above. Even if done as root, there is no output.

```
artie@superuser-System-Product-Name:~$ lspci -v | grep -A7 -i "audio"
artie@superuser-System-Product-Name:~$ sudo lspci -v | grep -A7 -i "audio"
[sudo] password for artie: 
artie@superuser-System-Product-Name:~$
```

I am looking at the troubleshooting link now.

Art

---

### Post by goodbye-windows(tm) on 2012-09-03
OK, the troubleshooting link is interesting. It says I have no soundcard at all.

I didn't bother to run all the preliminary checks since they presume you have some minimal audio output....which I DON'T.

Here's the output of the various commands on the troubleshooting link:

```


xyz@xyz-System-Product-Name:~$ sudo aplay -l
[sudo] password for xyz: 
aplay: device_list:252: no soundcards found...
xyz@xyz-System-Product-Name:~$ 


xyz@xyz-System-Product-Name:~$ find /lib/modules/`uname -r` | grep snd
/lib/modules/3.2.0-29-generic/kernel/sound/synth/emux/snd-emux-synth.ko
/lib/modules/3.2.0-29-generic/kernel/sound/synth/snd-util-mem.ko
/lib/modules/3.2.0-29-generic/kernel/sound/drivers/snd-portman2x4.ko
/lib/modules/3.2.0-29-generic/kernel/sound/drivers/snd-aloop.ko
/lib/modules/3.2.0-29-generic/kernel/sound/drivers/opl3/snd-opl3-synth.ko
/lib/modules/3.2.0-29-generic/kernel/sound/drivers/opl3/snd-opl3-lib.ko
/lib/modules/3.2.0-29-generic/kernel/sound/drivers/snd-mts64.ko
/lib/modules/3.2.0-29-generic/kernel/sound/drivers/snd-virmidi.ko
/lib/modules/3.2.0-29-generic/kernel/sound/drivers/pcsp/snd-pcsp.ko
/lib/modules/3.2.0-29-generic/kernel/sound/drivers/snd-dummy.ko
/lib/modules/3.2.0-29-generic/kernel/sound/drivers/mpu401/snd-mpu401-uart.ko
/lib/modules/3.2.0-29-generic/kernel/sound/drivers/mpu401/snd-mpu401.ko
/lib/modules/3.2.0-29-generic/kernel/sound/drivers/snd-mtpav.ko
/lib/modules/3.2.0-29-generic/kernel/sound/drivers/vx/snd-vx-lib.ko
/lib/modules/3.2.0-29-generic/kernel/sound/drivers/snd-serial-u16550.ko
/lib/modules/3.2.0-29-generic/kernel/sound/firewire/snd-firewire-lib.ko
/lib/modules/3.2.0-29-generic/kernel/sound/firewire/snd-firewire-speakers.ko
/lib/modules/3.2.0-29-generic/kernel/sound/firewire/snd-isight.ko
/lib/modules/3.2.0-29-generic/kernel/sound/pcmcia/pdaudiocf/snd-pdaudiocf.ko
/lib/modules/3.2.0-29-generic/kernel/sound/pcmcia/vx/snd-vxpocket.ko
/lib/modules/3.2.0-29-generic/kernel/sound/usb/usx2y/snd-usb-us122l.ko
/lib/modules/3.2.0-29-generic/kernel/sound/usb/usx2y/snd-usb-usx2y.ko
/lib/modules/3.2.0-29-generic/kernel/sound/usb/snd-usb-audio.ko
/lib/modules/3.2.0-29-generic/kernel/sound/usb/snd-usbmidi-lib.ko
/lib/modules/3.2.0-29-generic/kernel/sound/usb/caiaq/snd-usb-caiaq.ko
/lib/modules/3.2.0-29-generic/kernel/sound/usb/6fire/snd-usb-6fire.ko
/lib/modules/3.2.0-29-generic/kernel/sound/usb/misc/snd-ua101.ko
/lib/modules/3.2.0-29-generic/kernel/sound/i2c/snd-i2c.ko
/lib/modules/3.2.0-29-generic/kernel/sound/i2c/snd-cs8427.ko
/lib/modules/3.2.0-29-generic/kernel/sound/i2c/other/snd-pt2258.ko
/lib/modules/3.2.0-29-generic/kernel/sound/i2c/other/snd-ak4114.ko
/lib/modules/3.2.0-29-generic/kernel/sound/i2c/other/snd-ak4113.ko
/lib/modules/3.2.0-29-generic/kernel/sound/i2c/other/snd-ak4117.ko
/lib/modules/3.2.0-29-generic/kernel/sound/i2c/other/snd-ak4xxx-adda.ko
/lib/modules/3.2.0-29-generic/kernel/sound/i2c/other/snd-tea575x-tuner.ko
/lib/modules/3.2.0-29-generic/kernel/sound/isa/sb/snd-sb16-dsp.ko
/lib/modules/3.2.0-29-generic/kernel/sound/isa/sb/snd-sb-common.ko
/lib/modules/3.2.0-29-generic/kernel/sound/pci/snd-cs5530.ko
/lib/modules/3.2.0-29-generic/kernel/sound/pci/snd-via82xx-modem.ko
/lib/modules/3.2.0-29-generic/kernel/sound/pci/asihpi/snd-asihpi.ko
/lib/modules/3.2.0-29-generic/kernel/sound/pci/snd-maestro3.ko
/lib/modules/3.2.0-29-generic/kernel/sound/pci/oxygen/snd-oxygen.ko
/lib/modules/3.2.0-29-generic/kernel/sound/pci/oxygen/snd-virtuoso.ko
/lib/modules/3.2.0-29-generic/kernel/sound/pci/oxygen/snd-oxygen-lib.ko
/lib/modules/3.2.0-29-generic/kernel/sound/pci/snd-fm801.ko
/lib/modules/3.2.0-29-generic/kernel/sound/pci/snd-als4000.ko
/lib/modules/3.2.0-29-generic/kernel/sound/pci/snd-azt3328.ko
/lib/modules/3.2.0-29-generic/kernel/sound/pci/snd-rme32.ko
/lib/modules/3.2.0-29-generic/kernel/sound/pci/aw2/snd-aw2.ko
/lib/modules/3.2.0-29-generic/kernel/sound/pci/rme9652/snd-hdspm.ko
/lib/modules/3.2.0-29-generic/kernel/sound/pci/rme9652/snd-rme9652.ko
/lib/modules/3.2.0-29-generic/kernel/sound/pci/rme9652/snd-hdsp.ko
/lib/modules/3.2.0-29-generic/kernel/sound/pci/cs46xx/snd-cs46xx.ko
/lib/modules/3.2.0-29-generic/kernel/sound/pci/snd-es1938.ko
/lib/modules/3.2.0-29-generic/kernel/sound/pci/au88x0/snd-au8830.ko
/lib/modules/3.2.0-29-generic/kernel/sound/pci/au88x0/snd-au8820.ko
/lib/modules/3.2.0-29-generic/kernel/sound/pci/au88x0/snd-au8810.ko
/lib/modules/3.2.0-29-generic/kernel/sound/pci/echoaudio/snd-indigodjx.ko
/lib/modules/3.2.0-29-generic/kernel/sound/pci/echoaudio/snd-indigoio.ko
/lib/modules/3.2.0-29-generic/kernel/sound/pci/echoaudio/snd-gina24.ko
/lib/modules/3.2.0-29-generic/kernel/sound/pci/echoaudio/snd-mia.ko
/lib/modules/3.2.0-29-generic/kernel/sound/pci/echoaudio/snd-echo3g.ko
/lib/modules/3.2.0-29-generic/kernel/sound/pci/echoaudio/snd-darla24.ko
/lib/modules/3.2.0-29-generic/kernel/sound/pci/echoaudio/snd-indigodj.ko
/lib/modules/3.2.0-29-generic/kernel/sound/pci/echoaudio/snd-gina20.ko
/lib/modules/3.2.0-29-generic/kernel/sound/pci/echoaudio/snd-mona.ko
/lib/modules/3.2.0-29-generic/kernel/sound/pci/echoaudio/snd-indigo.ko
/lib/modules/3.2.0-29-generic/kernel/sound/pci/echoaudio/snd-layla20.ko
/lib/modules/3.2.0-29-generic/kernel/sound/pci/echoaudio/snd-indigoiox.ko
/lib/modules/3.2.0-29-generic/kernel/sound/pci/echoaudio/snd-darla20.ko
/lib/modules/3.2.0-29-generic/kernel/sound/pci/echoaudio/snd-layla24.ko
/lib/modules/3.2.0-29-generic/kernel/sound/pci/ymfpci/snd-ymfpci.ko
/lib/modules/3.2.0-29-generic/kernel/sound/pci/snd-atiixp-modem.ko
/lib/modules/3.2.0-29-generic/kernel/sound/pci/snd-intel8x0m.ko
/lib/modules/3.2.0-29-generic/kernel/sound/pci/snd-rme96.ko
/lib/modules/3.2.0-29-generic/kernel/sound/pci/snd-atiixp.ko
/lib/modules/3.2.0-29-generic/kernel/sound/pci/mixart/snd-mixart.ko
/lib/modules/3.2.0-29-generic/kernel/sound/pci/pcxhr/snd-pcxhr.ko
/lib/modules/3.2.0-29-generic/kernel/sound/pci/snd-cmipci.ko
/lib/modules/3.2.0-29-generic/kernel/sound/pci/snd-bt87x.ko
/lib/modules/3.2.0-29-generic/kernel/sound/pci/ali5451/snd-ali5451.ko
/lib/modules/3.2.0-29-generic/kernel/sound/pci/trident/snd-trident.ko
/lib/modules/3.2.0-29-generic/kernel/sound/pci/snd-als300.ko
/lib/modules/3.2.0-29-generic/kernel/sound/pci/snd-via82xx.ko
/lib/modules/3.2.0-29-generic/kernel/sound/pci/vx222/snd-vx222.ko
/lib/modules/3.2.0-29-generic/kernel/sound/pci/ac97/snd-ac97-codec.ko
/lib/modules/3.2.0-29-generic/kernel/sound/pci/snd-es1968.ko
/lib/modules/3.2.0-29-generic/kernel/sound/pci/snd-ens1370.ko
/lib/modules/3.2.0-29-generic/kernel/sound/pci/snd-sonicvibes.ko
/lib/modules/3.2.0-29-generic/kernel/sound/pci/nm256/snd-nm256.ko
/lib/modules/3.2.0-29-generic/kernel/sound/pci/riptide/snd-riptide.ko
/lib/modules/3.2.0-29-generic/kernel/sound/pci/snd-intel8x0.ko
/lib/modules/3.2.0-29-generic/kernel/sound/pci/snd-ens1371.ko
/lib/modules/3.2.0-29-generic/kernel/sound/pci/emu10k1/snd-emu10k1-synth.ko
/lib/modules/3.2.0-29-generic/kernel/sound/pci/emu10k1/snd-emu10k1x.ko
/lib/modules/3.2.0-29-generic/kernel/sound/pci/emu10k1/snd-emu10k1.ko
/lib/modules/3.2.0-29-generic/kernel/sound/pci/korg1212/snd-korg1212.ko
/lib/modules/3.2.0-29-generic/kernel/sound/pci/ca0106/snd-ca0106.ko
/lib/modules/3.2.0-29-generic/kernel/sound/pci/ctxfi/snd-ctxfi.ko
/lib/modules/3.2.0-29-generic/kernel/sound/pci/snd-cs4281.ko
/lib/modules/3.2.0-29-generic/kernel/sound/pci/hda/snd-hda-codec-cmedia.ko
/lib/modules/3.2.0-29-generic/kernel/sound/pci/hda/snd-hda-codec-si3054.ko
/lib/modules/3.2.0-29-generic/kernel/sound/pci/hda/snd-hda-codec.ko
/lib/modules/3.2.0-29-generic/kernel/sound/pci/hda/snd-hda-codec-cirrus.ko
/lib/modules/3.2.0-29-generic/kernel/sound/pci/hda/snd-hda-codec-ca0110.ko
/lib/modules/3.2.0-29-generic/kernel/sound/pci/hda/snd-hda-codec-analog.ko
/lib/modules/3.2.0-29-generic/kernel/sound/pci/hda/snd-hda-codec-ca0132.ko
/lib/modules/3.2.0-29-generic/kernel/sound/pci/hda/snd-hda-codec-idt.ko
/lib/modules/3.2.0-29-generic/kernel/sound/pci/hda/snd-hda-codec-realtek.ko
/lib/modules/3.2.0-29-generic/kernel/sound/pci/hda/snd-hda-intel.ko
/lib/modules/3.2.0-29-generic/kernel/sound/pci/hda/snd-hda-codec-conexant.ko
/lib/modules/3.2.0-29-generic/kernel/sound/pci/hda/snd-hda-codec-hdmi.ko
/lib/modules/3.2.0-29-generic/kernel/sound/pci/hda/snd-hda-codec-via.ko
/lib/modules/3.2.0-29-generic/kernel/sound/pci/cs5535audio/snd-cs5535audio.ko
/lib/modules/3.2.0-29-generic/kernel/sound/pci/lx6464es/snd-lx6464es.ko
/lib/modules/3.2.0-29-generic/kernel/sound/pci/lola/snd-lola.ko
/lib/modules/3.2.0-29-generic/kernel/sound/pci/snd-ad1889.ko
/lib/modules/3.2.0-29-generic/kernel/sound/pci/ice1712/snd-ice1724.ko
/lib/modules/3.2.0-29-generic/kernel/sound/pci/ice1712/snd-ice1712.ko
/lib/modules/3.2.0-29-generic/kernel/sound/pci/ice1712/snd-ice17xx-ak4xxx.ko
/lib/modules/3.2.0-29-generic/kernel/sound/core/snd-pcm.ko
/lib/modules/3.2.0-29-generic/kernel/sound/core/snd-rawmidi.ko
/lib/modules/3.2.0-29-generic/kernel/sound/core/snd.ko
/lib/modules/3.2.0-29-generic/kernel/sound/core/snd-hrtimer.ko
/lib/modules/3.2.0-29-generic/kernel/sound/core/snd-hwdep.ko
/lib/modules/3.2.0-29-generic/kernel/sound/core/oss/snd-mixer-oss.ko
/lib/modules/3.2.0-29-generic/kernel/sound/core/snd-page-alloc.ko
/lib/modules/3.2.0-29-generic/kernel/sound/core/snd-timer.ko
/lib/modules/3.2.0-29-generic/kernel/sound/core/seq/snd-seq-midi-event.ko
/lib/modules/3.2.0-29-generic/kernel/sound/core/seq/snd-seq-midi-emul.ko
/lib/modules/3.2.0-29-generic/kernel/sound/core/seq/snd-seq-virmidi.ko
/lib/modules/3.2.0-29-generic/kernel/sound/core/seq/snd-seq.ko
/lib/modules/3.2.0-29-generic/kernel/sound/core/seq/snd-seq-midi.ko
/lib/modules/3.2.0-29-generic/kernel/sound/core/seq/snd-seq-dummy.ko
/lib/modules/3.2.0-29-generic/kernel/sound/core/seq/snd-seq-device.ko
/lib/modules/3.2.0-29-generic/kernel/sound/soc/snd-soc-core.ko
/lib/modules/3.2.0-29-generic/kernel/sound/soc/codecs/snd-soc-wm8770.ko
/lib/modules/3.2.0-29-generic/kernel/sound/soc/codecs/snd-soc-sta32x.ko
/lib/modules/3.2.0-29-generic/kernel/sound/soc/codecs/snd-soc-wm8782.ko
/lib/modules/3.2.0-29-generic/kernel/sound/soc/codecs/snd-soc-ssm2602.ko
/lib/modules/3.2.0-29-generic/kernel/sound/soc/codecs/snd-soc-wm2000.ko
/lib/modules/3.2.0-29-generic/kernel/sound/soc/codecs/snd-soc-wm8350.ko
/lib/modules/3.2.0-29-generic/kernel/sound/soc/codecs/snd-soc-wm8985.ko
/lib/modules/3.2.0-29-generic/kernel/sound/soc/codecs/snd-soc-wm8974.ko
/lib/modules/3.2.0-29-generic/kernel/sound/soc/codecs/snd-soc-max9877.ko
/lib/modules/3.2.0-29-generic/kernel/sound/soc/codecs/snd-soc-ad193x.ko
/lib/modules/3.2.0-29-generic/kernel/sound/soc/codecs/snd-soc-l3.ko
/lib/modules/3.2.0-29-generic/kernel/sound/soc/codecs/snd-soc-wm8961.ko
/lib/modules/3.2.0-29-generic/kernel/sound/soc/codecs/snd-soc-88pm860x.ko
/lib/modules/3.2.0-29-generic/kernel/sound/soc/codecs/snd-soc-da7210.ko
/lib/modules/3.2.0-29-generic/kernel/sound/soc/codecs/snd-soc-wm8991.ko
/lib/modules/3.2.0-29-generic/kernel/sound/soc/codecs/snd-soc-wm8955.ko
/lib/modules/3.2.0-29-generic/kernel/sound/soc/codecs/snd-soc-wm8900.ko
/lib/modules/3.2.0-29-generic/kernel/sound/soc/codecs/snd-soc-ad73311.ko
/lib/modules/3.2.0-29-generic/kernel/sound/soc/codecs/snd-soc-wm8523.ko
/lib/modules/3.2.0-29-generic/kernel/sound/soc/codecs/snd-soc-uda134x.ko
/lib/modules/3.2.0-29-generic/kernel/sound/soc/codecs/snd-soc-wm8960.ko
/lib/modules/3.2.0-29-generic/kernel/sound/soc/codecs/snd-soc-wm8904.ko
/lib/modules/3.2.0-29-generic/kernel/sound/soc/codecs/snd-soc-ad1836.ko
/lib/modules/3.2.0-29-generic/kernel/sound/soc/codecs/snd-soc-rt5631.ko
/lib/modules/3.2.0-29-generic/kernel/sound/soc/codecs/snd-soc-pcm3008.ko
/lib/modules/3.2.0-29-generic/kernel/sound/soc/codecs/snd-soc-wm8962.ko
/lib/modules/3.2.0-29-generic/kernel/sound/soc/codecs/snd-soc-wm8737.ko
/lib/modules/3.2.0-29-generic/kernel/sound/soc/codecs/snd-soc-ads117x.ko
/lib/modules/3.2.0-29-generic/kernel/sound/soc/codecs/snd-soc-wm8580.ko
/lib/modules/3.2.0-29-generic/kernel/sound/soc/codecs/snd-soc-tlv320aic23.ko
/lib/modules/3.2.0-29-generic/kernel/sound/soc/codecs/snd-soc-wm8510.ko
/lib/modules/3.2.0-29-generic/kernel/sound/soc/codecs/snd-soc-wm8995.ko
/lib/modules/3.2.0-29-generic/kernel/sound/soc/codecs/snd-soc-wm8971.ko
/lib/modules/3.2.0-29-generic/kernel/sound/soc/codecs/snd-soc-wm9081.ko
/lib/modules/3.2.0-29-generic/kernel/sound/soc/codecs/snd-soc-wm8903.ko
/lib/modules/3.2.0-29-generic/kernel/sound/soc/codecs/snd-soc-wm8978.ko
/lib/modules/3.2.0-29-generic/kernel/sound/soc/codecs/snd-soc-wm8990.ko
/lib/modules/3.2.0-29-generic/kernel/sound/soc/codecs/snd-soc-wm8728.ko
/lib/modules/3.2.0-29-generic/kernel/sound/soc/codecs/snd-soc-wm8804.ko
/lib/modules/3.2.0-29-generic/kernel/sound/soc/codecs/snd-soc-ak4671.ko
/lib/modules/3.2.0-29-generic/kernel/sound/soc/codecs/snd-soc-dfbmcs320.ko
/lib/modules/3.2.0-29-generic/kernel/sound/soc/codecs/snd-soc-jz4740-codec.ko
/lib/modules/3.2.0-29-generic/kernel/sound/soc/codecs/snd-soc-wm8711.ko
/lib/modules/3.2.0-29-generic/kernel/sound/soc/codecs/snd-soc-wm8940.ko
/lib/modules/3.2.0-29-generic/kernel/sound/soc/codecs/snd-soc-wm8741.ko
/lib/modules/3.2.0-29-generic/kernel/sound/soc/codecs/snd-soc-spdif.ko
/lib/modules/3.2.0-29-generic/kernel/sound/soc/codecs/snd-soc-adav80x.ko
/lib/modules/3.2.0-29-generic/kernel/sound/soc/codecs/snd-soc-wm9090.ko
/lib/modules/3.2.0-29-generic/kernel/sound/soc/codecs/snd-soc-wm1250-ev1.ko
/lib/modules/3.2.0-29-generic/kernel/sound/soc/codecs/snd-soc-cx20442.ko
/lib/modules/3.2.0-29-generic/kernel/sound/soc/codecs/snd-soc-max98095.ko
/lib/modules/3.2.0-29-generic/kernel/sound/soc/codecs/snd-soc-lm4857.ko
/lib/modules/3.2.0-29-generic/kernel/sound/soc/codecs/snd-soc-tlv320dac33.ko
/lib/modules/3.2.0-29-generic/kernel/sound/soc/codecs/snd-soc-wm8983.ko
/lib/modules/3.2.0-29-generic/kernel/sound/soc/codecs/snd-soc-max98088.ko
/lib/modules/3.2.0-29-generic/kernel/sound/soc/codecs/snd-soc-wm8731.ko
/lib/modules/3.2.0-29-generic/kernel/sound/soc/codecs/snd-soc-tlv320aic3x.ko
/lib/modules/3.2.0-29-generic/kernel/sound/soc/codecs/snd-soc-uda1380.ko
/lib/modules/3.2.0-29-generic/kernel/sound/soc/codecs/snd-soc-wm8400.ko
/lib/modules/3.2.0-29-generic/kernel/sound/soc/codecs/snd-soc-wm8750.ko
/lib/modules/3.2.0-29-generic/kernel/sound/soc/codecs/snd-soc-ak4642.ko
/lib/modules/3.2.0-29-generic/kernel/sound/soc/codecs/snd-soc-wm8994.ko
/lib/modules/3.2.0-29-generic/kernel/sound/soc/codecs/snd-soc-alc5623.ko
/lib/modules/3.2.0-29-generic/kernel/sound/soc/codecs/snd-soc-adau1373.ko
/lib/modules/3.2.0-29-generic/kernel/sound/soc/codecs/snd-soc-wl1273.ko
/lib/modules/3.2.0-29-generic/kernel/sound/soc/codecs/snd-soc-max9850.ko
/lib/modules/3.2.0-29-generic/kernel/sound/soc/codecs/snd-soc-tpa6130a2.ko
/lib/modules/3.2.0-29-generic/kernel/sound/soc/codecs/snd-soc-wm-hubs.ko
/lib/modules/3.2.0-29-generic/kernel/sound/soc/codecs/snd-soc-wm8988.ko
/lib/modules/3.2.0-29-generic/kernel/sound/soc/codecs/snd-soc-cs4270.ko
/lib/modules/3.2.0-29-generic/kernel/sound/soc/codecs/snd-soc-wm8993.ko
/lib/modules/3.2.0-29-generic/kernel/sound/soc/codecs/snd-soc-cs42l51.ko
/lib/modules/3.2.0-29-generic/kernel/sound/soc/codecs/snd-soc-wm8753.ko
/lib/modules/3.2.0-29-generic/kernel/sound/soc/codecs/snd-soc-ak4535.ko
/lib/modules/3.2.0-29-generic/kernel/sound/soc/codecs/snd-soc-tlv320aic32x4.ko
/lib/modules/3.2.0-29-generic/kernel/sound/soc/codecs/snd-soc-wm8727.ko
/lib/modules/3.2.0-29-generic/kernel/sound/soc/codecs/snd-soc-wm8996.ko
/lib/modules/3.2.0-29-generic/kernel/sound/soc/codecs/snd-soc-wm8776.ko
/lib/modules/3.2.0-29-generic/kernel/sound/soc/codecs/snd-soc-ak4104.ko
/lib/modules/3.2.0-29-generic/kernel/sound/soc/codecs/snd-soc-cs4271.ko
/lib/modules/3.2.0-29-generic/kernel/sound/soc/codecs/snd-soc-tlv320aic26.ko
/lib/modules/3.2.0-29-generic/kernel/sound/soc/codecs/snd-soc-ak4641.ko
/lib/modules/3.2.0-29-generic/kernel/sound/soc/codecs/snd-soc-sgtl5000.ko
/lib/modules/3.2.0-29-generic/kernel/sound/soc/codecs/snd-soc-wm5100.ko
xyz@xyz-System-Product-Name:~$ 


xyz@xyz-System-Product-Name:~$ sudo apt-get install linux-restricted-modules-`uname -r` linux-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-restricted-modules-3.2.0-29-generic
E: Couldn't find any package by regex 'linux-restricted-modules-3.2.0-29-generic'
xyz@xyz-System-Product-Name:~$ 


xyz@xyz-System-Product-Name:~$ lspci -v | grep -A7 -i "audio"
xyz@xyz-System-Product-Name:~$ 


xyz@xyz-System-Product-Name:~$ sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2
sudo: aptitude: command not found


```


I have no idea where to go from here-

There are some comments on the link page about some of the info being outdated. But, I avoided those sections that were marked as outdated.

TY.

Art

---

### Post by opensshd on 2012-09-04
Ok, yah by the pictures you posted I guessed it was not seeing your sound hardware. Can you post output from dmesg as well please?

---

### Post by goodbye-windows(tm) on 2012-09-04
```

artie@superuser-System-Product-Name:~$ dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.2.0-29-generic (buildd@allspice) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #46-Ubuntu SMP Fri Jul 27 17:03:23 UTC 2012 (Ubuntu 3.2.0-29.46-generic 3.2.24)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-29-generic root=UUID=bd19ac4a-a165-4b4a-85ef-98b8298911d9 ro quiet splash vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000cfe80000 (usable)
[    0.000000]  BIOS-e820: 00000000cfe80000 - 00000000cfe98000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000cfe98000 - 00000000cfec0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000cfec0000 - 00000000cff00000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffe00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000220000000 (usable)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI present.
[    0.000000] DMI: System manufacturer System Product Name/M5A78L-M LX PLUS, BIOS 0601    11/30/2011
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] No AGP bridge found
[    0.000000] last_pfn = 0x220000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000000 mask FFFF80000000 write-back
[    0.000000]   1 base 000080000000 mask FFFFC0000000 write-back
[    0.000000]   2 base 0000C0000000 mask FFFFF0000000 write-back
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] TOM2: 0000000230000000 aka 8960M
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 00000000d0000000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0xcfe80 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [ffff8800000ff780] ff780
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] Base memory trampoline at [ffff88000009a000] 9a000 size 20480
[    0.000000] Using GB pages for direct mapping
[    0.000000] init_memory_mapping: 0000000000000000-00000000cfe80000
[    0.000000]  0000000000 - 00c0000000 page 1G
[    0.000000]  00c0000000 - 00cfe00000 page 2M
[    0.000000]  00cfe00000 - 00cfe80000 page 4k
[    0.000000] kernel direct mapping tables up to cfe80000 @ 1fffd000-20000000
[    0.000000] init_memory_mapping: 0000000100000000-0000000220000000
[    0.000000]  0100000000 - 0200000000 page 1G
[    0.000000]  0200000000 - 0220000000 page 2M
[    0.000000] kernel direct mapping tables up to 220000000 @ cfe7e000-cfe80000
[    0.000000] RAMDISK: 364da000 - 37265000
[    0.000000] ACPI: RSDP 00000000000fb490 00024 (v02 ACPIAM)
[    0.000000] ACPI: XSDT 00000000cfe80100 00054 (v01 113011 XSDT1533 20111130 MSFT 00000097)
[    0.000000] ACPI: FACP 00000000cfe80290 000F4 (v03 113011 FACP1533 20111130 MSFT 00000097)
[    0.000000] ACPI Warning: Optional field Pm2ControlBlock has zero address or length: 0x0000000000000000/0x1 (20110623/tbfadt-560)
[    0.000000] ACPI: DSDT 00000000cfe80460 0D6DD (v01  A1969 A1969001 00000001 INTL 20060113)
[    0.000000] ACPI: FACS 00000000cfe98000 00040
[    0.000000] ACPI: APIC 00000000cfe80390 0008C (v01 113011 APIC1533 20111130 MSFT 00000097)
[    0.000000] ACPI: MCFG 00000000cfe80420 0003C (v01 113011 OEMMCFG  20111130 MSFT 00000097)
[    0.000000] ACPI: OEMB 00000000cfe98040 00072 (v01 113011 OEMB1533 20111130 MSFT 00000097)
[    0.000000] ACPI: HPET 00000000cfe8f460 00038 (v01 113011 OEMHPET  20111130 MSFT 00000097)
[    0.000000] ACPI: SSDT 00000000cfe8f4a0 00E10 (v01 A M I  POWERNOW 00000001 AMD  00000001)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000220000000
[    0.000000] Initmem setup node 0 0000000000000000-0000000220000000
[    0.000000]   NODE_DATA [000000021fffb000 - 000000021fffffff]
[    0.000000]  [ffffea0000000000-ffffea00087fffff] PMD -> [ffff880217a00000-ffff88021f5fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00220000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x000cfe80
[    0.000000]     0: 0x00100000 -> 0x00220000
[    0.000000] On node 0 totalpages: 2031119
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 5 pages reserved
[    0.000000]   DMA zone: 3914 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 16320 pages used for memmap
[    0.000000]   DMA32 zone: 831168 pages, LIFO batch:31
[    0.000000]   Normal zone: 18432 pages used for memmap
[    0.000000]   Normal zone: 1161216 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x04] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x05] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x86] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x87] disabled)
[    0.000000] ACPI: IOAPIC (id[0x06] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 6, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8300 base: 0xfed00000
[    0.000000] SMP: Allowing 8 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e4000
[    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000cfe80000 - 00000000cfe98000
[    0.000000] PM: Registered nosave memory: 00000000cfe98000 - 00000000cfec0000
[    0.000000] PM: Registered nosave memory: 00000000cfec0000 - 00000000cff00000
[    0.000000] PM: Registered nosave memory: 00000000cff00000 - 00000000ffe00000
[    0.000000] PM: Registered nosave memory: 00000000ffe00000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at cff00000 (gap: cff00000:2ff00000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff88021fc00000 s83072 r8192 d23424 u262144
[    0.000000] pcpu-alloc: s83072 r8192 d23424 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 1996298
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-29-generic root=UUID=bd19ac4a-a165-4b4a-85ef-98b8298911d9 ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Node 0: aperture @ 0 size 32 MB
[    0.000000] Your BIOS doesn't leave a aperture memory hole
[    0.000000] Please enable the IOMMU option in the BIOS setup
[    0.000000] This costs you 64 MB of RAM
[    0.000000] Mapping aperture over 65536 KB of RAM @ c4000000
[    0.000000] PM: Registered nosave memory: 00000000c4000000 - 00000000c8000000
[    0.000000] Memory: 7835320k/8912896k available (6555k kernel code, 788420k absent, 289156k reserved, 6645k data, 920k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:16640 nr_irqs:744 16
[    0.000000] Extended CMOS year: 2000
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 65011712 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration failed
[    0.000000] TSC: PIT calibration matches HPET. 1 loops
[    0.000000] Detected 2712.140 MHz processor.
[    0.012004] Calibrating delay loop (skipped), value calculated using timer frequency.. 5424.28 BogoMIPS (lpj=10848560)
[    0.012008] pid_max: default: 32768 minimum: 301
[    0.012029] Security Framework initialized
[    0.016005] AppArmor: AppArmor initialized
[    0.016006] Yama: becoming mindful.
[    0.016594] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.018817] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.019808] Mount-cache hash table entries: 256
[    0.019916] Initializing cgroup subsys cpuacct
[    0.019921] Initializing cgroup subsys memory
[    0.019928] Initializing cgroup subsys devices
[    0.019929] Initializing cgroup subsys freezer
[    0.019931] Initializing cgroup subsys blkio
[    0.019936] Initializing cgroup subsys perf_event
[    0.019960] tseg: 0000000000
[    0.019972] CPU: Physical Processor ID: 0
[    0.019973] CPU: Processor Core ID: 0
[    0.019974] mce: CPU supports 6 MCE banks
[    0.021151] ACPI: Core revision 20110623
[    0.028010] ftrace: allocating 26998 entries in 106 pages
[    0.036412] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.078201] CPU0: AMD Phenom(tm) II X6 1045T Processor stepping 00
[    0.080004] Performance Events: AMD PMU driver.
[    0.080004] ... version:                0
[    0.080004] ... bit width:              48
[    0.080004] ... generic registers:      4
[    0.080004] ... value mask:             0000ffffffffffff
[    0.080004] ... max period:             00007fffffffffff
[    0.080004] ... fixed-purpose events:   0
[    0.080004] ... event mask:             000000000000000f
[    0.080004] NMI watchdog enabled, takes one hw-pmu counter.
[    0.080004] Booting Node   0, Processors  #1
[    0.080004] smpboot cpu 1: start_ip = 9a000
[    0.168024] NMI watchdog enabled, takes one hw-pmu counter.
[    0.168083]  #2
[    0.168084] smpboot cpu 2: start_ip = 9a000
[    0.260036] NMI watchdog enabled, takes one hw-pmu counter.
[    0.260088]  #3
[    0.260089] smpboot cpu 3: start_ip = 9a000
[    0.352053] NMI watchdog enabled, takes one hw-pmu counter.
[    0.352109]  #4
[    0.352110] smpboot cpu 4: start_ip = 9a000
[    0.444046] NMI watchdog enabled, takes one hw-pmu counter.
[    0.444108]  #5
[    0.444109] smpboot cpu 5: start_ip = 9a000
[    0.536045] NMI watchdog enabled, takes one hw-pmu counter.
[    0.536059] Brought up 6 CPUs
[    0.536061] Total of 6 processors activated (32546.12 BogoMIPS).
[    0.540202] devtmpfs: initialized
[    0.544977] EVM: security.selinux
[    0.544979] EVM: security.SMACK64
[    0.544980] EVM: security.capability
[    0.545040] PM: Registering ACPI NVS region at cfe98000 (163840 bytes)
[    0.545040] print_constraints: dummy: 
[    0.545040] RTC time: 16:51:34, date: 09/04/12
[    0.545040] NET: Registered protocol family 16
[    0.545040] node 0 link 0: io port [1000, ffffff]
[    0.545040] TOM: 00000000d0000000 aka 3328M
[    0.545040] Fam 10h mmconf [mem 0xe0000000-0xefffffff]
[    0.545040] node 0 link 0: mmio [a0000, bffff]
[    0.545040] node 0 link 0: mmio [d0000000, efffffff] ==> [d0000000, dfffffff]
[    0.545040] node 0 link 0: mmio [f0000000, fe9fffff]
[    0.545040] node 0 link 0: mmio [fea00000, febfffff]
[    0.545040] node 0 link 0: mmio [fec00000, ffdfffff]
[    0.545040] TOM2: 0000000230000000 aka 8960M
[    0.545040] bus: [00, 1f] on node 0 link 0
[    0.545040] bus: 00 index 0 [io  0x0000-0xffff]
[    0.545040] bus: 00 index 1 [mem 0x000a0000-0x000bffff]
[    0.545040] bus: 00 index 2 [mem 0xd0000000-0xdfffffff]
[    0.545040] bus: 00 index 3 [mem 0xf0000000-0xffffffff]
[    0.545040] bus: 00 index 4 [mem 0x230000000-0xfcffffffff]
[    0.545040] Extended Config Space enabled on 1 nodes
[    0.545040] ACPI: bus type pci registered
[    0.545040] Trying to unpack rootfs image as initramfs...
[    0.545040] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.545040] PCI: not using MMCONFIG
[    0.545040] PCI: Using configuration type 1 for base access
[    0.545040] PCI: Using configuration type 1 for extended access
[    0.545637] bio: create slab <bio-0> at 0
[    0.545637] ACPI: Added _OSI(Module Device)
[    0.545637] ACPI: Added _OSI(Processor Device)
[    0.545637] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.545637] ACPI: Added _OSI(Processor Aggregator Device)
[    0.545637] ACPI: EC: Look up EC in DSDT
[    0.549279] ACPI: Executed 3 blocks of module-level executable AML code
[    0.624582] ACPI: Interpreter enabled
[    0.624588] ACPI: (supports S0 S1 S3 S4 S5)
[    0.624604] ACPI: Using IOAPIC for interrupt routing
[    0.624626] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.625646] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI motherboard resources
[    0.749087] Freeing initrd memory: 13868k freed
[    0.780819] ACPI: No dock devices found.
[    0.780822] HEST: Table not found.
[    0.780825] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.780886] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.780996] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7]
[    0.780998] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff]
[    0.781000] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.781002] pci_root PNP0A03:00: host bridge window [mem 0x000d0000-0x000dffff]
[    0.781004] pci_root PNP0A03:00: host bridge window [mem 0xcff00000-0xdfffffff]
[    0.781006] pci_root PNP0A03:00: host bridge window [mem 0xf0000000-0xfebfffff]
[    0.781018] pci 0000:00:00.0: [1022:9600] type 0 class 0x000600
[    0.781059] pci 0000:00:01.0: [1043:9602] type 1 class 0x000604
[    0.781090] pci 0000:00:04.0: [1022:9604] type 1 class 0x000604
[    0.781119] pci 0000:00:04.0: PME# supported from D0 D3hot D3cold
[    0.781122] pci 0000:00:04.0: PME# disabled
[    0.781153] pci 0000:00:11.0: [1002:4390] type 0 class 0x000101
[    0.781171] pci 0000:00:11.0: reg 10: [io  0xc000-0xc007]
[    0.781180] pci 0000:00:11.0: reg 14: [io  0xb000-0xb003]
[    0.781189] pci 0000:00:11.0: reg 18: [io  0xa000-0xa007]
[    0.781198] pci 0000:00:11.0: reg 1c: [io  0x9000-0x9003]
[    0.781207] pci 0000:00:11.0: reg 20: [io  0x8000-0x800f]
[    0.781216] pci 0000:00:11.0: reg 24: [mem 0xfe9ffc00-0xfe9fffff]
[    0.781235] pci 0000:00:11.0: set SATA to AHCI mode
[    0.781279] pci 0000:00:12.0: [1002:4397] type 0 class 0x000c03
[    0.781291] pci 0000:00:12.0: reg 10: [mem 0xfe9fe000-0xfe9fefff]
[    0.781352] pci 0000:00:12.1: [1002:4398] type 0 class 0x000c03
[    0.781364] pci 0000:00:12.1: reg 10: [mem 0xfe9fd000-0xfe9fdfff]
[    0.781430] pci 0000:00:12.2: [1002:4396] type 0 class 0x000c03
[    0.781448] pci 0000:00:12.2: reg 10: [mem 0xfe9ff800-0xfe9ff8ff]
[    0.781526] pci 0000:00:12.2: supports D1 D2
[    0.781528] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
[    0.781531] pci 0000:00:12.2: PME# disabled
[    0.781552] pci 0000:00:13.0: [1002:4397] type 0 class 0x000c03
[    0.781564] pci 0000:00:13.0: reg 10: [mem 0xfe9fc000-0xfe9fcfff]
[    0.781625] pci 0000:00:13.1: [1002:4398] type 0 class 0x000c03
[    0.781638] pci 0000:00:13.1: reg 10: [mem 0xfe9fb000-0xfe9fbfff]
[    0.781703] pci 0000:00:13.2: [1002:4396] type 0 class 0x000c03
[    0.781721] pci 0000:00:13.2: reg 10: [mem 0xfe9ff400-0xfe9ff4ff]
[    0.781799] pci 0000:00:13.2: supports D1 D2
[    0.781801] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    0.781804] pci 0000:00:13.2: PME# disabled
[    0.781826] pci 0000:00:14.0: [1002:4385] type 0 class 0x000c05
[    0.781920] pci 0000:00:14.1: [1002:439c] type 0 class 0x000101
[    0.781935] pci 0000:00:14.1: reg 10: [io  0x0000-0x0007]
[    0.781944] pci 0000:00:14.1: reg 14: [io  0x0000-0x0003]
[    0.781953] pci 0000:00:14.1: reg 18: [io  0x0000-0x0007]
[    0.781961] pci 0000:00:14.1: reg 1c: [io  0x0000-0x0003]
[    0.781970] pci 0000:00:14.1: reg 20: [io  0xff00-0xff0f]
[    0.782023] pci 0000:00:14.3: [1002:439d] type 0 class 0x000601
[    0.782095] pci 0000:00:14.4: [1002:4384] type 1 class 0x000604
[    0.782134] pci 0000:00:14.5: [1002:4399] type 0 class 0x000c03
[    0.782147] pci 0000:00:14.5: reg 10: [mem 0xfe9fa000-0xfe9fafff]
[    0.782211] pci 0000:00:18.0: [1022:1200] type 0 class 0x000600
[    0.782224] pci 0000:00:18.1: [1022:1201] type 0 class 0x000600
[    0.782234] pci 0000:00:18.2: [1022:1202] type 0 class 0x000600
[    0.782245] pci 0000:00:18.3: [1022:1203] type 0 class 0x000600
[    0.782258] pci 0000:00:18.4: [1022:1204] type 0 class 0x000600
[    0.782295] pci 0000:01:05.0: [1002:9616] type 0 class 0x000300
[    0.782302] pci 0000:01:05.0: reg 10: [mem 0xd0000000-0xdfffffff pref]
[    0.782306] pci 0000:01:05.0: reg 14: [io  0xd000-0xd0ff]
[    0.782310] pci 0000:01:05.0: reg 18: [mem 0xfebe0000-0xfebeffff]
[    0.782319] pci 0000:01:05.0: reg 24: [mem 0xfea00000-0xfeafffff]
[    0.782334] pci 0000:01:05.0: supports D1 D2
[    0.782369] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.782372] pci 0000:00:01.0:   bridge window [io  0xd000-0xdfff]
[    0.782374] pci 0000:00:01.0:   bridge window [mem 0xfea00000-0xfebfffff]
[    0.782377] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.782413] pci 0000:02:00.0: [10ec:8168] type 0 class 0x000200
[    0.782425] pci 0000:02:00.0: reg 10: [io  0xe800-0xe8ff]
[    0.782444] pci 0000:02:00.0: reg 18: [mem 0xfdfff000-0xfdffffff 64bit pref]
[    0.782457] pci 0000:02:00.0: reg 20: [mem 0xfdff8000-0xfdffbfff 64bit pref]
[    0.782508] pci 0000:02:00.0: supports D1 D2
[    0.782509] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.782513] pci 0000:02:00.0: PME# disabled
[    0.788076] pci 0000:00:04.0: PCI bridge to [bus 02-02]
[    0.788080] pci 0000:00:04.0:   bridge window [io  0xe000-0xefff]
[    0.788085] pci 0000:00:04.0:   bridge window [mem 0xfdf00000-0xfdffffff 64bit pref]
[    0.788146] pci 0000:00:14.4: PCI bridge to [bus 03-03] (subtractive decode)
[    0.788154] pci 0000:00:14.4:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.788156] pci 0000:00:14.4:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.788158] pci 0000:00:14.4:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.788160] pci 0000:00:14.4:   bridge window [mem 0x000d0000-0x000dffff] (subtractive decode)
[    0.788162] pci 0000:00:14.4:   bridge window [mem 0xcff00000-0xdfffffff] (subtractive decode)
[    0.788164] pci 0000:00:14.4:   bridge window [mem 0xf0000000-0xfebfffff] (subtractive decode)
[    0.788177] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.788324] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.788348] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE4._PRT]
[    0.788390] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0PC._PRT]
[    0.788428]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.788430]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
[    0.788431] ACPI _OSC control for PCIe not granted, disabling ASPM
[    0.790927] ACPI: PCI Interrupt Link [LNKA] (IRQs 4 7 *10 12 14 15)
[    0.790953] ACPI: PCI Interrupt Link [LNKB] (IRQs 4 7 *10 11 12 14 15)
[    0.790978] ACPI: PCI Interrupt Link [LNKC] (IRQs 4 7 10 *11 12 14 15)
[    0.791002] ACPI: PCI Interrupt Link [LNKD] (IRQs 4 7 10 *11 12 14 15)
[    0.791026] ACPI: PCI Interrupt Link [LNKE] (IRQs 4 7 10 11 12 14 15) *0, disabled.
[    0.791050] ACPI: PCI Interrupt Link [LNKF] (IRQs 4 7 10 11 12 14 15) *0, disabled.
[    0.791074] ACPI: PCI Interrupt Link [LNKG] (IRQs *11)
[    0.791096] ACPI: PCI Interrupt Link [LNKH] (IRQs 4 7 10 11 12 14 15) *0, disabled.
[    0.791175] vgaarb: device added: PCI:0000:01:05.0,decodes=io+mem,owns=io+mem,locks=none
[    0.791175] vgaarb: loaded
[    0.791175] vgaarb: bridge control possible 0000:01:05.0
[    0.791175] i2c-core: driver [aat2870] using legacy suspend method
[    0.791175] i2c-core: driver [aat2870] using legacy resume method
[    0.791175] SCSI subsystem initialized
[    0.791175] libata version 3.00 loaded.
[    0.791175] usbcore: registered new interface driver usbfs
[    0.791175] usbcore: registered new interface driver hub
[    0.791175] usbcore: registered new device driver usb
[    0.791175] PCI: Using ACPI for IRQ routing
[    0.800208] PCI: pci_cache_line_size set to 64 bytes
[    0.800266] reserve RAM buffer: 000000000009f000 - 000000000009ffff 
[    0.800268] reserve RAM buffer: 00000000cfe80000 - 00000000cfffffff 
[    0.800344] NetLabel: Initializing
[    0.800346] NetLabel:  domain hash size = 128
[    0.800347] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.800355] NetLabel:  unlabeled traffic allowed by default
[    0.800384] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.800384] hpet0: 4 comparators, 32-bit 14.318180 MHz counter
[    0.802100] Switching to clocksource hpet
[    0.804840] AppArmor: AppArmor Filesystem Enabled
[    0.804856] pnp: PnP ACPI init
[    0.804867] ACPI: bus type pnp registered
[    0.804940] pnp 00:00: [bus 00-ff]
[    0.804942] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.804943] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.804945] pnp 00:00: [io  0x0d00-0xffff window]
[    0.804947] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.804948] pnp 00:00: [mem 0x000d0000-0x000dffff window]
[    0.804950] pnp 00:00: [mem 0xcff00000-0xdfffffff window]
[    0.804951] pnp 00:00: [mem 0xf0000000-0xfebfffff window]
[    0.804987] pnp 00:00: Plug and Play ACPI device, IDs PNP0a03 (active)
[    0.805037] pnp 00:01: [mem 0x00000000-0xffffffffffffffff disabled]
[    0.805039] pnp 00:01: [mem 0x00000000-0xffffffffffffffff disabled]
[    0.805070] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.805095] pnp 00:02: [dma 4]
[    0.805096] pnp 00:02: [io  0x0000-0x000f]
[    0.805098] pnp 00:02: [io  0x0081-0x0083]
[    0.805099] pnp 00:02: [io  0x0087]
[    0.805100] pnp 00:02: [io  0x0089-0x008b]
[    0.805101] pnp 00:02: [io  0x008f]
[    0.805103] pnp 00:02: [io  0x00c0-0x00df]
[    0.805121] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.805128] pnp 00:03: [io  0x0070-0x0071]
[    0.805135] pnp 00:03: [irq 8]
[    0.805152] pnp 00:03: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.805157] pnp 00:04: [io  0x0061]
[    0.805175] pnp 00:04: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.805181] pnp 00:05: [io  0x00f0-0x00ff]
[    0.805184] pnp 00:05: [irq 13]
[    0.805202] pnp 00:05: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.805646] pnp 00:06: [io  0x0378-0x037f]
[    0.805650] pnp 00:06: [irq 7]
[    0.805652] pnp 00:06: [dma 0 disabled]
[    0.805813] pnp 00:06: Plug and Play ACPI device, IDs PNP0400 (active)
[    0.805836] pnp 00:07: [mem 0xfed00000-0xfed003ff]
[    0.805856] pnp 00:07: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.806176] pnp 00:08: [io  0x03f8-0x03ff]
[    0.806180] pnp 00:08: [irq 4]
[    0.806181] pnp 00:08: [dma 0 disabled]
[    0.806239] pnp 00:08: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.806284] pnp 00:09: [io  0x0060]
[    0.806285] pnp 00:09: [io  0x0064]
[    0.806287] pnp 00:09: [mem 0xfec00000-0xfec00fff]
[    0.806288] pnp 00:09: [mem 0xfee00000-0xfee00fff]
[    0.806320] system 00:09: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.806322] system 00:09: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.806324] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.806428] pnp 00:0a: [io  0x0010-0x001f]
[    0.806429] pnp 00:0a: [io  0x0022-0x003f]
[    0.806431] pnp 00:0a: [io  0x0062-0x0063]
[    0.806433] pnp 00:0a: [io  0x0065-0x006f]
[    0.806435] pnp 00:0a: [io  0x0072-0x007f]
[    0.806436] pnp 00:0a: [io  0x0080]
[    0.806437] pnp 00:0a: [io  0x0084-0x0086]
[    0.806438] pnp 00:0a: [io  0x0088]
[    0.806439] pnp 00:0a: [io  0x008c-0x008e]
[    0.806441] pnp 00:0a: [io  0x0090-0x009f]
[    0.806442] pnp 00:0a: [io  0x00a2-0x00bf]
[    0.806443] pnp 00:0a: [io  0x00b1]
[    0.806444] pnp 00:0a: [io  0x00e0-0x00ef]
[    0.806446] pnp 00:0a: [io  0x04d0-0x04d1]
[    0.806447] pnp 00:0a: [io  0x040b]
[    0.806448] pnp 00:0a: [io  0x04d6]
[    0.806449] pnp 00:0a: [io  0x0c00-0x0c01]
[    0.806451] pnp 00:0a: [io  0x0c14]
[    0.806452] pnp 00:0a: [io  0x0c50-0x0c51]
[    0.806453] pnp 00:0a: [io  0x0c52]
[    0.806454] pnp 00:0a: [io  0x0c6c]
[    0.806455] pnp 00:0a: [io  0x0c6f]
[    0.806457] pnp 00:0a: [io  0x0cd0-0x0cd1]
[    0.806458] pnp 00:0a: [io  0x0cd2-0x0cd3]
[    0.806459] pnp 00:0a: [io  0x0cd4-0x0cd5]
[    0.806460] pnp 00:0a: [io  0x0cd6-0x0cd7]
[    0.806462] pnp 00:0a: [io  0x0cd8-0x0cdf]
[    0.806463] pnp 00:0a: [io  0x0b00-0x0b3f]
[    0.806464] pnp 00:0a: [io  0x0800-0x089f]
[    0.806466] pnp 00:0a: [io  0x0000-0xffffffffffffffff disabled]
[    0.806467] pnp 00:0a: [io  0x0b00-0x0b0f]
[    0.806468] pnp 00:0a: [io  0x0b20-0x0b3f]
[    0.806470] pnp 00:0a: [io  0x0900-0x090f]
[    0.806471] pnp 00:0a: [io  0x0910-0x091f]
[    0.806472] pnp 00:0a: [io  0xfe00-0xfefe]
[    0.806473] pnp 00:0a: [io  0x0060]
[    0.806475] pnp 00:0a: [io  0x0064]
[    0.806476] pnp 00:0a: [mem 0xcff00000-0xcfffffff]
[    0.806477] pnp 00:0a: [mem 0xffb80000-0xffbfffff]
[    0.806479] pnp 00:0a: [mem 0xfec10000-0xfec1001f]
[    0.806480] pnp 00:0a: [mem 0xfed40000-0xfed44fff]
[    0.806534] system 00:0a: [io  0x04d0-0x04d1] has been reserved
[    0.806536] system 00:0a: [io  0x040b] has been reserved
[    0.806538] system 00:0a: [io  0x04d6] has been reserved
[    0.806540] system 00:0a: [io  0x0c00-0x0c01] has been reserved
[    0.806541] system 00:0a: [io  0x0c14] has been reserved
[    0.806543] system 00:0a: [io  0x0c50-0x0c51] has been reserved
[    0.806545] system 00:0a: [io  0x0c52] has been reserved
[    0.806546] system 00:0a: [io  0x0c6c] has been reserved
[    0.806548] system 00:0a: [io  0x0c6f] has been reserved
[    0.806550] system 00:0a: [io  0x0cd0-0x0cd1] has been reserved
[    0.806552] system 00:0a: [io  0x0cd2-0x0cd3] has been reserved
[    0.806553] system 00:0a: [io  0x0cd4-0x0cd5] has been reserved
[    0.806555] system 00:0a: [io  0x0cd6-0x0cd7] has been reserved
[    0.806557] system 00:0a: [io  0x0cd8-0x0cdf] has been reserved
[    0.806559] system 00:0a: [io  0x0b00-0x0b3f] has been reserved
[    0.806560] system 00:0a: [io  0x0800-0x089f] has been reserved
[    0.806562] system 00:0a: [io  0x0b00-0x0b0f] has been reserved
[    0.806564] system 00:0a: [io  0x0b20-0x0b3f] has been reserved
[    0.806566] system 00:0a: [io  0x0900-0x090f] has been reserved
[    0.806568] system 00:0a: [io  0x0910-0x091f] has been reserved
[    0.806570] system 00:0a: [io  0xfe00-0xfefe] has been reserved
[    0.806572] system 00:0a: [mem 0xcff00000-0xcfffffff] has been reserved
[    0.806574] system 00:0a: [mem 0xffb80000-0xffbfffff] has been reserved
[    0.806576] system 00:0a: [mem 0xfec10000-0xfec1001f] has been reserved
[    0.806578] system 00:0a: [mem 0xfed40000-0xfed44fff] has been reserved
[    0.806580] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.806671] pnp 00:0b: [io  0x0000-0xffffffffffffffff disabled]
[    0.806673] pnp 00:0b: [io  0x0230-0x023f]
[    0.806674] pnp 00:0b: [io  0x0290-0x029f]
[    0.806676] pnp 00:0b: [io  0x0300-0x030f]
[    0.806678] pnp 00:0b: [io  0x0a30-0x0a3f]
[    0.806711] system 00:0b: [io  0x0230-0x023f] has been reserved
[    0.806713] system 00:0b: [io  0x0290-0x029f] has been reserved
[    0.806715] system 00:0b: [io  0x0300-0x030f] has been reserved
[    0.806717] system 00:0b: [io  0x0a30-0x0a3f] has been reserved
[    0.806719] system 00:0b: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.806740] pnp 00:0c: [mem 0xe0000000-0xefffffff]
[    0.806770] system 00:0c: [mem 0xe0000000-0xefffffff] has been reserved
[    0.806772] system 00:0c: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.807795] pnp 00:0d: [mem 0x00000000-0x0009ffff]
[    0.807798] pnp 00:0d: [mem 0x000c0000-0x000cffff]
[    0.807799] pnp 00:0d: [mem 0x000e0000-0x000fffff]
[    0.807801] pnp 00:0d: [mem 0x00100000-0xcfefffff]
[    0.807803] pnp 00:0d: [mem 0xfec00000-0xffffffff]
[    0.807875] system 00:0d: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.807877] system 00:0d: [mem 0x000c0000-0x000cffff] could not be reserved
[    0.807880] system 00:0d: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.807882] system 00:0d: [mem 0x00100000-0xcfefffff] could not be reserved
[    0.807884] system 00:0d: [mem 0xfec00000-0xffffffff] could not be reserved
[    0.807887] system 00:0d: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.807970] pnp: PnP ACPI: found 14 devices
[    0.807972] ACPI: ACPI bus type pnp unregistered
[    0.814596] PCI: max bus depth: 1 pci_try_num: 2
[    0.814610] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.814612] pci 0000:00:01.0:   bridge window [io  0xd000-0xdfff]
[    0.814614] pci 0000:00:01.0:   bridge window [mem 0xfea00000-0xfebfffff]
[    0.814617] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.814620] pci 0000:00:04.0: PCI bridge to [bus 02-02]
[    0.814622] pci 0000:00:04.0:   bridge window [io  0xe000-0xefff]
[    0.814625] pci 0000:00:04.0:   bridge window [mem 0xfdf00000-0xfdffffff 64bit pref]
[    0.814627] pci 0000:00:14.4: PCI bridge to [bus 03-03]
[    0.814649] pci 0000:00:04.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.814652] pci 0000:00:04.0: setting latency timer to 64
[    0.814658] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.814660] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.814661] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.814663] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
[    0.814664] pci_bus 0000:00: resource 8 [mem 0xcff00000-0xdfffffff]
[    0.814666] pci_bus 0000:00: resource 9 [mem 0xf0000000-0xfebfffff]
[    0.814667] pci_bus 0000:01: resource 0 [io  0xd000-0xdfff]
[    0.814669] pci_bus 0000:01: resource 1 [mem 0xfea00000-0xfebfffff]
[    0.814671] pci_bus 0000:01: resource 2 [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.814673] pci_bus 0000:02: resource 0 [io  0xe000-0xefff]
[    0.814675] pci_bus 0000:02: resource 2 [mem 0xfdf00000-0xfdffffff 64bit pref]
[    0.814677] pci_bus 0000:03: resource 4 [io  0x0000-0x0cf7]
[    0.814678] pci_bus 0000:03: resource 5 [io  0x0d00-0xffff]
[    0.814680] pci_bus 0000:03: resource 6 [mem 0x000a0000-0x000bffff]
[    0.814682] pci_bus 0000:03: resource 7 [mem 0x000d0000-0x000dffff]
[    0.814684] pci_bus 0000:03: resource 8 [mem 0xcff00000-0xdfffffff]
[    0.814685] pci_bus 0000:03: resource 9 [mem 0xf0000000-0xfebfffff]
[    0.814715] NET: Registered protocol family 2
[    0.814893] IP route cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.815977] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.818143] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.818405] TCP: Hash tables configured (established 524288 bind 65536)
[    0.818407] TCP reno registered
[    0.818420] UDP hash table entries: 4096 (order: 5, 131072 bytes)
[    0.818469] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
[    0.818575] NET: Registered protocol family 1
[    0.818585] pci 0000:00:01.0: MSI quirk detected; subordinate MSI disabled
[    0.818602] pci 0000:00:12.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.920039] pci 0000:00:12.0: PCI INT A disabled
[    0.920051] pci 0000:00:12.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.000041] pci 0000:00:12.1: PCI INT A disabled
[    1.000061] pci 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.000111] pci 0000:00:12.2: PCI INT B disabled
[    1.000121] pci 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.080037] pci 0000:00:13.0: PCI INT A disabled
[    1.080047] pci 0000:00:13.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.160038] pci 0000:00:13.1: PCI INT A disabled
[    1.160056] pci 0000:00:13.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.160112] pci 0000:00:13.2: PCI INT B disabled
[    1.160126] pci 0000:00:14.5: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.240037] pci 0000:00:14.5: PCI INT C disabled
[    1.240052] pci 0000:01:05.0: Boot video device
[    1.240056] PCI: CLS 64 bytes, default 64
[    1.241228] PCI-DMA: Disabling AGP.
[    1.241332] PCI-DMA: aperture base @ c4000000 size 65536 KB
[    1.241333] PCI-DMA: using GART IOMMU.
[    1.241335] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
[    1.244605] IBS: LVT offset 1 assigned
[    1.244629] perf: AMD IBS detected (0x0000001f)
[    1.244754] audit: initializing netlink socket (disabled)
[    1.244763] type=2000 audit(1346777494.240:1): initialized
[    1.276235] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.310126] VFS: Disk quotas dquot_6.5.2
[    1.310172] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.310605] fuse init (API version 7.17)
[    1.310674] msgmni has been set to 15459
[    1.311095] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    1.311127] io scheduler noop registered
[    1.311129] io scheduler deadline registered
[    1.311149] io scheduler cfq registered (default)
[    1.311330] pcieport 0000:00:04.0: setting latency timer to 64
[    1.311360] pcieport 0000:00:04.0: irq 40 for MSI/MSI-X
[    1.311435] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.311453] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.311557] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    1.311561] ACPI: Power Button [PWRB]
[    1.311594] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    1.311596] ACPI: Power Button [PWRF]
[    1.311881] ACPI: acpi_idle registered with cpuidle
[    1.492282] ERST: Table is not found!
[    1.492284] GHES: HEST is not enabled!
[    1.492370] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.512811] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.549031] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.596278] Linux agpgart interface v0.103
[    1.597468] brd: module loaded
[    1.598048] loop: module loaded
[    1.598243] ahci 0000:00:11.0: version 3.0
[    1.598263] ahci 0000:00:11.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    1.598375] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[    1.598378] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part ccc 
[    1.598836] scsi0 : ahci
[    1.598907] scsi1 : ahci
[    1.598971] scsi2 : ahci
[    1.599029] scsi3 : ahci
[    1.599105] ata1: SATA max UDMA/133 abar m1024@0xfe9ffc00 port 0xfe9ffd00 irq 22
[    1.599108] ata2: SATA max UDMA/133 abar m1024@0xfe9ffc00 port 0xfe9ffd80 irq 22
[    1.599111] ata3: SATA max UDMA/133 abar m1024@0xfe9ffc00 port 0xfe9ffe00 irq 22
[    1.599114] ata4: SATA max UDMA/133 abar m1024@0xfe9ffc00 port 0xfe9ffe80 irq 22
[    1.599247] pata_acpi 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.599270] pata_acpi 0000:00:14.1: setting latency timer to 64
[    1.599568] Fixed MDIO Bus: probed
[    1.599585] tun: Universal TUN/TAP device driver, 1.6
[    1.599586] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.599645] PPP generic driver version 2.4.2
[    1.599732] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.599807] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.599820] ehci_hcd 0000:00:12.2: EHCI Host Controller
[    1.599865] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
[    1.599873] ehci_hcd 0000:00:12.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.599898] ehci_hcd 0000:00:12.2: debug port 1
[    1.599915] ehci_hcd 0000:00:12.2: irq 17, io mem 0xfe9ff800
[    1.608047] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    1.608161] hub 1-0:1.0: USB hub found
[    1.608165] hub 1-0:1.0: 6 ports detected
[    1.608306] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.608319] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    1.608364] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
[    1.608370] ehci_hcd 0000:00:13.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.608390] ehci_hcd 0000:00:13.2: debug port 1
[    1.608409] ehci_hcd 0000:00:13.2: irq 19, io mem 0xfe9ff400
[    1.620046] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    1.620145] hub 2-0:1.0: USB hub found
[    1.620148] hub 2-0:1.0: 6 ports detected
[    1.620252] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.620322] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.620335] ohci_hcd 0000:00:12.0: OHCI Host Controller
[    1.620376] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 3
[    1.620398] ohci_hcd 0000:00:12.0: irq 16, io mem 0xfe9fe000
[    1.680119] hub 3-0:1.0: USB hub found
[    1.680124] hub 3-0:1.0: 3 ports detected
[    1.680263] ohci_hcd 0000:00:12.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.680276] ohci_hcd 0000:00:12.1: OHCI Host Controller
[    1.680320] ohci_hcd 0000:00:12.1: new USB bus registered, assigned bus number 4
[    1.680334] ohci_hcd 0000:00:12.1: irq 16, io mem 0xfe9fd000
[    1.740116] hub 4-0:1.0: USB hub found
[    1.740121] hub 4-0:1.0: 3 ports detected
[    1.740261] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.740274] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    1.740310] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5
[    1.740331] ohci_hcd 0000:00:13.0: irq 18, io mem 0xfe9fc000
[    1.800116] hub 5-0:1.0: USB hub found
[    1.800121] hub 5-0:1.0: 3 ports detected
[    1.800262] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.800275] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    1.800317] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 6
[    1.800332] ohci_hcd 0000:00:13.1: irq 18, io mem 0xfe9fb000
[    1.860141] hub 6-0:1.0: USB hub found
[    1.860147] hub 6-0:1.0: 3 ports detected
[    1.860290] ohci_hcd 0000:00:14.5: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.860303] ohci_hcd 0000:00:14.5: OHCI Host Controller
[    1.860349] ohci_hcd 0000:00:14.5: new USB bus registered, assigned bus number 7
[    1.860363] ohci_hcd 0000:00:14.5: irq 18, io mem 0xfe9fa000
[    1.916146] ata3: SATA link down (SStatus 0 SControl 300)
[    1.916185] ata2: SATA link down (SStatus 0 SControl 300)
[    1.920129] hub 7-0:1.0: USB hub found
[    1.920134] hub 7-0:1.0: 2 ports detected
[    1.920209] uhci_hcd: USB Universal Host Controller Interface driver
[    1.920265] usbcore: registered new interface driver libusual
[    1.920294] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    1.920676] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.920682] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.920842] mousedev: PS/2 mouse device common for all mice
[    1.920966] rtc_cmos 00:03: RTC can wake from S4
[    1.921057] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    1.921082] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    1.921143] device-mapper: uevent: version 1.0.3
[    1.921200] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
[    1.921293] cpuidle: using governor ladder
[    1.921463] cpuidle: using governor menu
[    1.921464] EFI Variables Facility v0.08 2004-May-17
[    1.921641] TCP cubic registered
[    1.921715] NET: Registered protocol family 10
[    1.922042] NET: Registered protocol family 17
[    1.922045] Registering the dns_resolver key type
[    1.922177] PM: Hibernation image not present or could not be loaded.
[    1.922185] registered taskstats version 1
[    1.944452]   Magic number: 12:354:893
[    1.944589] rtc_cmos 00:03: setting system clock to 2012-09-04 16:51:36 UTC (1346777496)
[    1.944638] powernow-k8: Found 1 AMD Phenom(tm) II X6 1045T Processor (6 cpu cores) (version 2.20.00)
[    1.944671] powernow-k8: Core Performance Boosting: on.
[    1.944709] powernow-k8:    0 : pstate 0 (2700 MHz)
[    1.944710] powernow-k8:    1 : pstate 1 (2000 MHz)
[    1.944712] powernow-k8:    2 : pstate 2 (1400 MHz)
[    1.944713] powernow-k8:    3 : pstate 3 (800 MHz)
[    1.945542] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.945544] EDD information not available.
[    2.088087] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.088113] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.088662] ata1.00: ATA-8: V4-CT032V4SSD2, S5FAMM22, max UDMA/100
[    2.088665] ata1.00: 62533296 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    2.089393] ata1.00: configured for UDMA/100
[    2.089575] scsi 0:0:0:0: Direct-Access     ATA      V4-CT032V4SSD2   S5FA PQ: 0 ANSI: 5
[    2.089741] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.089781] sd 0:0:0:0: [sda] 62533296 512-byte logical blocks: (32.0 GB/29.8 GiB)
[    2.090024] sd 0:0:0:0: [sda] Write Protect is off
[    2.090028] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.090076] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.090115] ata4.00: ATAPI: HL-DT-STDVDRRW GSA-H30L, S856, max UDMA/33
[    2.091038]  sda: sda1 sda2 < sda5 >
[    2.091643] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.093044] ata4.00: configured for UDMA/33
[    2.097456] scsi 3:0:0:0: CD-ROM            HL-DT-ST DVDRRW GSA-H30L  S856 PQ: 0 ANSI: 5
[    2.101331] sr0: scsi3-mmc drive: 40x/40x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.101334] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.101446] sr 3:0:0:0: Attached scsi CD-ROM sr0
[    2.101526] sr 3:0:0:0: Attached scsi generic sg1 type 5
[    2.102757] Freeing unused kernel memory: 920k freed
[    2.102925] Write protecting the kernel read-only data: 12288k
[    2.107144] Freeing unused kernel memory: 1616k freed
[    2.110601] Freeing unused kernel memory: 1200k freed
[    2.125756] udevd[144]: starting version 175
[    2.146256] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    2.146278] r8169 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.146318] r8169 0000:02:00.0: setting latency timer to 64
[    2.146385] r8169 0000:02:00.0: irq 41 for MSI/MSI-X
[    2.146752] r8169 0000:02:00.0: eth0: RTL8168evl/8111evl at 0xffffc90000c24000, c8:60:00:5b:2b:45, XID 0c900800 IRQ 41
[    2.146755] r8169 0000:02:00.0: eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[    2.149954] scsi4 : pata_atiixp
[    2.150054] scsi5 : pata_atiixp
[    2.150540] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xff00 irq 14
[    2.150542] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xff08 irq 15
[    2.180065] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    2.184051] usb 3-1: new full-speed USB device number 2 using ohci_hcd
[    2.244059] Refined TSC clocksource calibration: 2712.176 MHz.
[    2.244068] Switching to clocksource tsc
[    2.351090] hub 3-1:1.0: USB hub found
[    2.353048] hub 3-1:1.0: 3 ports detected
[    2.359674] ata6.01: ATA-7: MAXTOR STM3320620AS, 3.AAE, max UDMA/133
[    2.359677] ata6.01: 625142448 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    2.426312] ata6.01: configured for UDMA/100
[    2.426452] scsi 5:0:1:0: Direct-Access     ATA      MAXTOR STM332062 3.AA PQ: 0 ANSI: 5
[    2.426623] sd 5:0:1:0: Attached scsi generic sg2 type 0
[    2.426627] sd 5:0:1:0: [sdb] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    2.426716] sd 5:0:1:0: [sdb] Write Protect is off
[    2.426719] sd 5:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[    2.426763] sd 5:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.487454]  sdb: sdb1 sdb2 < sdb5 > sdb3
[    2.487917] sd 5:0:1:0: [sdb] Attached SCSI disk
[    2.653036] usb 3-1.1: new low-speed USB device number 3 using ohci_hcd
[    2.865026] usb 3-1.2: new low-speed USB device number 4 using ohci_hcd
[    2.942173] ADDRCONF(NETDEV_UP): eth0: link is not ready
[    2.949271] udevd[370]: starting version 175
[    2.955353] Adding 8122364k swap on /dev/sda5.  Priority:-1 extents:1 across:8122364k SS
[    3.007965] MCE: In-kernel MCE decoding enabled.
[    3.008197] wmi: Mapper loaded
[    3.008644] EDAC MC: Ver: 2.1.0
[    3.008986] AMD64 EDAC driver v3.4.0
[    3.010393] lp: driver loaded but no devices found
[    3.011172] EDAC amd64: DRAM ECC disabled.
[    3.011180] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
[    3.011181]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
[    3.011182]  (Note that use of the override may cause unknown side effects.)
[    3.012236] parport_pc 00:06: reported by Plug and Play ACPI
[    3.012290] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[    3.031745] ppdev: user-space parallel port driver
[    3.045279] ACPI: resource piix4_smbus [io  0x0b00-0x0b07] conflicts with ACPI region SOR1 [io 0xb00-0xb0f]
[    3.045282] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    3.045561] SP5100 TCO timer: SP5100 TCO WatchDog Timer Driver v0.01
[    3.045635] SP5100 TCO timer: mmio address 0xfec000f0 already in use
[    3.059242] input: Microsoft Internet Keyboard Pro as /devices/pci0000:00/0000:00:12.0/usb3/3-1/3-1.1/3-1.1:1.0/input/input2
[    3.059357] generic-usb 0003:045E:002B.0001: input,hidraw0: USB HID v1.10 Keyboard [Microsoft Internet Keyboard Pro] on usb-0000:00:12.0-1.1/input0
[    3.063097] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    3.066738] [drm] Initialized drm 1.1.0 20060810
[    3.072976] [drm] radeon defaulting to kernel modesetting.
[    3.072978] [drm] radeon kernel modesetting enabled.
[    3.073109] input: Microsoft Internet Keyboard Pro as /devices/pci0000:00/0000:00:12.0/usb3/3-1/3-1.1/3-1.1:1.1/input/input3
[    3.073156] radeon 0000:01:05.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    3.073161] radeon 0000:01:05.0: setting latency timer to 64
[    3.073207] generic-usb 0003:045E:002B.0002: input,hidraw1: USB HID v1.10 Device [Microsoft Internet Keyboard Pro] on usb-0000:00:12.0-1.1/input1
[    3.073321] [drm] initializing kernel modesetting (RS780 0x1002:0x9616 0x1043:0x8388).
[    3.073342] [drm] register mmio base: 0xFEBE0000
[    3.073343] [drm] register mmio size: 65536
[    3.073944] ATOM BIOS: B27722_RS780C
[    3.073957] radeon 0000:01:05.0: VRAM: 256M 0x00000000C0000000 - 0x00000000CFFFFFFF (256M used)
[    3.073960] radeon 0000:01:05.0: GTT: 512M 0x00000000A0000000 - 0x00000000BFFFFFFF
[    3.080801] [drm] Detected VRAM RAM=256M, BAR=256M
[    3.080805] [drm] RAM width 32bits DDR
[    3.080874] [TTM] Zone  kernel: Available graphics memory: 3959438 kiB.
[    3.080876] [TTM] Zone   dma32: Available graphics memory: 2097152 kiB.
[    3.080877] [TTM] Initializing pool allocator.
[    3.080901] [drm] radeon: 256M of VRAM memory ready
[    3.080903] [drm] radeon: 512M of GTT memory ready.
[    3.080916] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    3.080917] [drm] Driver supports precise vblank timestamp query.
[    3.080935] [drm] radeon: irq initialized.
[    3.080938] [drm] GART: num cpu pages 131072, num gpu pages 131072
[    3.081575] [drm] Loading RS780 Microcode
[    3.084299] input: Microsoft Microsoft 5-Button Mouse with IntelliEye(TM) as /devices/pci0000:00/0000:00:12.0/usb3/3-1/3-1.2/3-1.2:1.0/input/input4
[    3.084439] generic-usb 0003:045E:0039.0003: input,hidraw2: USB HID v1.10 Mouse [Microsoft Microsoft 5-Button Mouse with IntelliEye(TM)] on usb-0000:00:12.0-1.2/input0
[    3.084458] usbcore: registered new interface driver usbhid
[    3.084459] usbhid: USB HID core driver
[    3.108207] lp0: using parport0 (interrupt-driven).
[    3.153081] [drm] PCIE GART of 512M enabled (table at 0x00000000C0040000).
[    3.153154] radeon 0000:01:05.0: WB enabled
[    3.158462] type=1400 audit(1346777497.710:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=666 comm="apparmor_parser"
[    3.158569] type=1400 audit(1346777497.710:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=662 comm="apparmor_parser"
[    3.158882] type=1400 audit(1346777497.710:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=666 comm="apparmor_parser"
[    3.159092] type=1400 audit(1346777497.710:5): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=662 comm="apparmor_parser"
[    3.159128] type=1400 audit(1346777497.710:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=666 comm="apparmor_parser"
[    3.159387] type=1400 audit(1346777497.710:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=662 comm="apparmor_parser"
[    3.185182] [drm] ring test succeeded in 1 usecs
[    3.185283] [drm] radeon: ib pool ready.
[    3.185343] [drm] ib test succeeded in 0 usecs
[    3.185535] [drm] Radeon Display Connectors
[    3.185537] [drm] Connector 0:
[    3.185538] [drm]   VGA
[    3.185540] [drm]   DDC: 0x7e40 0x7e40 0x7e44 0x7e44 0x7e48 0x7e48 0x7e4c 0x7e4c
[    3.185541] [drm]   Encoders:
[    3.185542] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
[    3.185543] [drm] Connector 1:
[    3.185544] [drm]   DVI-D
[    3.185545] [drm]   HPD1
[    3.185547] [drm]   DDC: 0x7e50 0x7e50 0x7e54 0x7e54 0x7e58 0x7e58 0x7e5c 0x7e5c
[    3.185548] [drm]   Encoders:
[    3.185549] [drm]     DFP3: INTERNAL_KLDSCP_LVTMA
[    3.185575] [drm] radeon: power management initialized
[    3.367975] [drm] fb mappable at 0xD0142000
[    3.367976] [drm] vram apper at 0xD0000000
[    3.367977] [drm] size 7299072
[    3.367978] [drm] fb depth is 24
[    3.367979] [drm]    pitch is 6912
[    3.368096] fbcon: radeondrmfb (fb0) is primary device
[    3.368214] Console: switching to colour frame buffer device 210x65
[    3.368242] fb0: radeondrmfb frame buffer device
[    3.368243] drm: registered panic notifier
[    3.368248] [drm] Initialized radeon 2.12.0 20080528 for 0000:01:05.0 on minor 0
[    3.417679] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[    3.514318] init: failsafe main process (817) killed by TERM signal
[    3.574040] Bluetooth: Core ver 2.16
[    3.574078] NET: Registered protocol family 31
[    3.574080] Bluetooth: HCI device and connection manager initialized
[    3.574083] Bluetooth: HCI socket layer initialized
[    3.574084] Bluetooth: L2CAP socket layer initialized
[    3.574089] Bluetooth: SCO socket layer initialized
[    3.577249] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    3.577251] Bluetooth: BNEP filters: protocol multicast
[    3.582258] type=1400 audit(1346777498.134:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=886 comm="apparmor_parser"
[    3.582750] type=1400 audit(1346777498.134:9): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=886 comm="apparmor_parser"
[    3.584965] Bluetooth: RFCOMM TTY layer initialized
[    3.584969] Bluetooth: RFCOMM socket layer initialized
[    3.584971] Bluetooth: RFCOMM ver 1.11
[    3.725209] r8169 0000:02:00.0: eth0: link down
[    3.725217] r8169 0000:02:00.0: eth0: link down
[    3.726023] ADDRCONF(NETDEV_UP): eth0: link is not ready
[    3.726279] ADDRCONF(NETDEV_UP): eth0: link is not ready
[    4.151433] type=1400 audit(1346777498.702:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=931 comm="apparmor_parser"
[    4.791182] radeon 0000:01:05.0: texture bo too small (1680 1050 26 0 -> 7299072 have 7258112)
[    4.791185] radeon 0000:01:05.0: alignments 1728 64 8 256
[    4.791187] [drm:radeon_cs_ioctl] *ERROR* Invalid command stream !
[    5.297419] r8169 0000:02:00.0: eth0: link up
[    5.298101] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   15.712029] eth0: no IPv6 routers present
artie@superuser-System-Product-Name:~$ 


```



TY

Art

---

### Post by opensshd on 2012-09-04
Art, I am not seeing anything in there referring to a sound device. 

If this is onboard sound, is it disabled in the BIOS perhaps?

---

### Post by opensshd on 2012-09-04
I would try enabling HDaudio from BIOS and reboot... see if anything changes in that dmesg with: 

dmesg|grep -i snd

---

### Post by goodbye-windows(tm) on 2012-09-04
OK, here is the output with the bios set for HDaudio.

```

artie@superuser-System-Product-Name:~$ dmesg|grep -i snd
[    3.188086] snd_hda_intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16

artie@superuser-System-Product-Name:~$ sudo dmesg|grep -i snd
[sudo] password for artie: 
[    3.188086] snd_hda_intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
artie@superuser-System-Product-Name:~$

```

Here is the output with bios set for ac97.

```

artie@superuser-System-Product-Name:~$ dmesg|grep -i snd


artie@superuser-System-Product-Name:~$ sudo dmesg|grep -i snd
[sudo] password for artie: 
artie@superuser-System-Product-Name:~$


```

Note that i am trying to use the ac97 on my system as my case is old and I do not have hardware necessary to use HDaudio.

I have also done installs with the bios pre-set to HDaudio and with the bios pre-set to ac97. Both installs look identical when the audio settings are examined with the gui (as pictured in my first post).

Regards,

Art

---

### Post by opensshd on 2012-09-04
I'm confused when you say you don't have necessary hardware to use HDaudio.

How do you mean? What hardware should you need?

---

### Post by goodbye-windows(tm) on 2012-09-04
My front panel connectors are (on my very old case) ac97, which means there are just 5 wire connections to the mobo. It's the old standard audio type. The existing front panel connections are not compatible with the newer HDaudio hardware on the pcb.

To use HDaudio, I would have to buy and retrofit a (more modern) front panel connector set that is designed for HDaudio. 

I don't want or need fancy audio connections.

I'd gladly buy the HDaudio and retrofit hardware, but I'm not sure the soundcard would be recognized even if the front panel connectors were HDaudio type.

The mobo does support ac97 (called 'legacy'), or HDaudio. To change the internal mobo connector to HDaudio capable, you change the bios setting.  There is a single audio connector on the mobo, but it either supports ac97 or HDaudio, depending on how the bios is set.

The sound did work when I first installed the new mobo. And, my nephew bought the same board and also runs xubuntu 12.04, and his works great, no proprietary drivers needed.

Hope this helps.

Regards,

Art

---

### Post by opensshd on 2012-09-04
Are there no audio connectors in the back, directly connected to the mobo?

---

### Post by opensshd on 2012-09-04
Found another link that may contain some help:

[https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

Curious, does it work if you boot from a liveOS? What changed after it worked to the point it stopped working?

---

### Post by opensshd on 2012-09-04
I've also seen some reports about ac97 not being detected after adding it (physically, but also may apply to 'adding' it in BIOS) and rebooting - but rebooting a second time will cause the device to be detected.

Might be worth a try?

---

### Post by goodbye-windows(tm) on 2012-09-04
> **opensshd said:**
> Are there no audio connectors in the back, directly connected to the mobo?

Yes, the connectors are there on the back, but are inconvenient as I do a lot of voice chats on the internet.

---

### Post by goodbye-windows(tm) on 2012-09-04
> **opensshd said:**
> Found another link that may contain some help:

[https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

Curious, does it work if you boot from a liveOS? What changed after it worked to the point it stopped working?

Not sure if it works with the live cd, will try it in a few minutes.

TY

Art

---

### Post by opensshd on 2012-09-04
It would be definitely worth seeing if those plugs in the back work with an HDaudio driver if for nothing else than troubleshooting the audio. There are extension cables you can get for audio (i.e double female 3.5mm stereo audio cable) if your motherboards pin layout is somehow not compatible with your case wiring.

---

### Post by goodbye-windows(tm) on 2012-09-04
> **goodbye-windows(tm) said:**
> Not sure if it works with the live cd........



I had quite a time testing the audio from the live cd, it won't play youtube videos because there is no adobe flash player, flash player won't install.

Then, it seems I need some sort of mp3 support, which I think is the restricted drivers.

I was however able to test it, and it did not work. The mp3 player thought it was sending sound somewhere, but nothing heard from the back panel or the front panel audio connectors.

I also loaded critical mass, a game with music and sound effects....nothing. Again, not sure if there are other resources necessary to play sounds.

I'm off to the other support link to continue troubleshooting.

More later.

Art

---

### Post by opensshd on 2012-09-04
If you will post your motherboard make and model information, I'll look up some photos of it on the internet. Also any pics you can attach, or can find similar examples of from the internet, of your case wiring would be very helpful.

I can double check that they are not compatible if you like. :)

---

### Post by opensshd on 2012-09-04
Ok, just rereading through the thread. Have identified your motherboard. 
Just to clarify, why are you choosing ac97 instead of HDaudio? Because of the connections to the motherboard from the case?

Also, when you say initially in the thread, 'didn't completely install' how do you mean? Was the installation of the OS interrupted or something?

Looking at that motherboard and considering you are putting 12.04 on it, I am fairly certain your issue lies in BIOS settings.

If Ubuntu 12.04 does not see any devices when you choose ac97 in your BIOS, I highly doubt you will find any driver to help that. Just speaking from experience, might be mistaken, of course. But it does see an audio device when you use HDaudio... 

Again, if you could clarify why you require using legacy mode on that onboard audio chip? Just a bit confused here, you said you did not hook up case wiring to the motherboard when you installed it?

Anyway, if this legacy mode behavior is anomalous, possible remedies I can think of might be a BIOS update... Also, just noticed you said you have no root access...

Sorry, I must read too many threads to keep them all separate in my head after about ten minutes :) God forbid I have to remember stuff longer than that I'm too easy to confuse as it is ><

---

### Post by goodbye-windows(tm) on 2012-09-04
> Ok, just rereading through the thread. Have identified your motherboard. 

OK, the mobo is a current model and is fully spec'd. I can send the manual for it via private email if you like. It's on sale right now for $110 dollars including the FX4100 6 core processor so it gets allota bang for the buck.

> Just to clarify, why are you choosing ac97 instead of HDaudio? Because of the connections to the motherboard from the case?


Yes, exactly. The manual says you need to use an asus only HD module if you select HDaudio in the bios. I didn't price it and it might be difficult to modify my case to properly mount it. So, my preference was the ac97 selection. Ac97 is available in 5, 7 or 9 pin versions. It's a long story and I have research the different versions. My case has 7 wires coming from the front panel connector pcb, but it is 100 percent compatible with the later 5 pin ac97 implementation which the asus mobo uses.

I'd buy the HDaudio add on in a heartbeat, if it would solve this issue. But, it doesn't sound like the HDaudio add on will make the software recognize the sound card.

My nephew has the same mobo and processor and the same ac97 case wiring, his works in Xubuntu 12.04 just fine.

> Also, when you say initially in the thread, 'didn't completely install' how do you mean? Was the installation of the OS interrupted or something?


By that I mean there were no indications of a sound card being present, based on the display in the stock pulse audio control panel. There were no errors, oddities or indication(s) that there were any issues with the install.

> Looking at that motherboard and considering you are putting 12.04 on it, I am fairly certain your issue lies in BIOS settings.

If Ubuntu 12.04 does not see any devices when you choose ac97 in your BIOS, I highly doubt you will find any driver to help that. Just speaking from experience, might be mistaken, of course. But it does see an audio device when you use HDaudio... 

Yes, I noticed that there was an audio device listed when HDaudio is selected. But, I think the HDaudio plug on the mobo must mate with an outboard HDaudio front panel pcb, which contains the front panel connectors and a controller chip. I think part of the chips function is to provide audio switching between front and rear panel connectors and to provide more jacks so that the 8 channel HDaudio has adequate I/O for the fancy (8 channel) sound systems.

Again, my nephews machine uses the same processor, mobo and the same 7 wire ac97 implementation that I have. And, we both run Xubuntu 12.04.

> Again, if you could clarify why you require using legacy mode on that onboard audio chip? Just a bit confused here, you said you did not hook up case wiring to the motherboard when you installed it?


OK, do you think my sound would work if I had the HDaudio add on available from Asus??? The thing about the case wiring not being hooked up initially is that it took me awhile to figure out how to wire the 7 wire ac97 onto the 5 wire mobo audio connector. The answer turns out to be simple, but it took me awhile to figure that out. My initial system testing was done with bare bones connections to the mobo, but when the front panel audio connections were hooked up to the mobo, it did work. But, it stopped working several days later (for no obvious reason).

> Anyway, if this legacy mode behavior is anomalous, possible remedies I can think of might be a BIOS update... Also, just noticed you said you have no root access...

Yes, initially there was no root access. But, at the time of the setup, I was using the superusers account anyway. So, I merely authenticated myself using the superusers password. I did fix the root access (sudo) access by making my own user account a member of the admin group. So, I have full access now.

> Sorry, I must read too many threads to keep them all separate in my head after about ten minutes :) God forbid I have to remember stuff longer than that I'm too easy to confuse as it is ><

I thought I was the only one in the world with issues like that!!! Appreciate your guidance.

If I choose HDaudio in the bios, can I hookup the legacy ac97 front panel wires and have sound???? I don't think it works like that though. I think the HDaudio connector on the mobo looks for a chip on the special front panel connector pcb, and without it, you can't use HDaudio.

Regards,

Art

---

### Post by opensshd on 2012-09-04
Good question.

And thank you, I'm catching you a bit better now :)

Hmmm... I would definitely hook up those case wires to my board and see if hdaudio works. Would I tell you to do that, probably not :)

I'm pretty reckless with hardware and don't mind a little 'guess and test' with 'different wires n stuff', and am very lucky I have never bricked a board really...

So, if you have a working implementation of this configuration at your nephews, then it's gotta be possible...

It's odd that it would just 'stop working' with no apparent cause... that concerns me a bit...

---

### Post by goodbye-windows(tm) on 2012-09-04
When it stopped working was during the period of time when I was configuring the system to my liking. It's allot of work to get al the aps and to configure the system in a way that makes the op comfortable. So, when it stopped working, it wasn't noticed right away because i was flat out working on other issues. 

The addition of my user to the admin group was the last major issue. By the time I looked at the audio problem, I had most of the system configured and expected the audio problem to be a quick fix. I was so WRONG!!!!!

I will pull the wires off the mobo audio connector and set the bios for HDaudio and try to make some audio appear.  I don't need fancy audio, but something that can make a simple beep is necessary. 

HDaudio is a mess, there are major differences between the various types of it and it's more than I really want to get into. However, I'll poke around with the front panel leads and and see if I can get some output.

If I can't get output, do you know how to completely remove the soundcard software and all its configuration files so that I can reinstall it from scratch?

I was wondering if this was the way to remove the sound card support:

```

sudo apt-get purge pulseaudio 

then

sudo apt-get install pulseaudio


```

Regards,

Art

---

### Post by opensshd on 2012-09-04
Art,

Curious, when you installed the operating system initially, did it detect the sound card by itself and just work out of the box, or did you need to configure anything?

If it worked out of the box, then I would imagine it should also work using a default liveOS, but that was not the case, correct?

Did you try both BIOS audio settings with the liveCD? Did you test both conditions with front and back connectors?

I would take these steps to diagnose the problem further.

Also, alsa is also installed by default in 12.04 which is another sound system, but keep in mind, these are applications that (how to say) add a unified interface for other applications to access the audio card? These are not the interfaces by which you would manipulate device drivers or kernel modules that give core functionality to your sound card.

Again, just speaking from the couple of CST courses I took and a bit of experience, I could be wrong on any number of technicalities but I sometimes sound convincing (even to myself which is kinda scary), so I feel the need to warn you! Hehehe

---

### Post by goodbye-windows(tm) on 2012-09-05
> Curious, when you installed the operating system initially, did it detect the sound card by itself and just work out of the box, or did you need to configure anything?

It worked right out of the box-hoever it should be noted that 'worked' is based on my observation that it played the ubuntu sound-African Drums. 

I had new hardware and a completely new install of Xubuntu to deal with and I simply DID NOT (totally) test the audio for functionality at that time.

> If it worked out of the box, then I would imagine it should also work using a default liveOS, but that was not the case, correct?

OK, initially I heard the African Drums. But, much later (2 days ago) I tried to listen to the sound from the live cd-it didn't work. But, many new pieces of hardware and many changes to the software and configuration were done by then.

> Did you try both BIOS audio settings with the liveCD? Did you test both conditions with front and back connectors?


Yes, I did test both conditions with the live cd. However, I did not test the back connectors at all as they are just to inconvenient to be useful to me. I rely on the front panel audio connectors almost exclusively so didn't test the output from the rear connectors until today.

> Also, alsa is also installed by default in 12.04 which is another sound system, but keep in mind, these are applications that (how to say) add a unified interface for other applications to access the audio card? These are not the interfaces by which you would manipulate device drivers or kernel modules that give core functionality to your sound card.


Interesting........I just checked the software center, and it shows that alsa is not installed. I'm not exactly sure which alsa application you're referring to, but I assume it's 'ALSA sound mixer for GNOME', also referred to as "GNOME ALSA Mixer'. If this is the alsa you're referring to, I do not think it was installed by default. It is NOT currently installed on my system.

Yes, I do understand that the sound system needs to be evaluated without distractions such as help apps, etc.

Is it possible that alsa is not installed by default in Xubuntu?????

> so I feel the need to warn you! Hehehe

OK, I'm warned........

Here's an update.........

Last evening (very late), I set the bios back to default and DID NOT adjust anything in the bios-purely defaults were used. I checked and the bios was set for HDaudio. I was concerned that the front panel wires to the mobo might cause problems if the machine operates in HDaudio mode with ac97 connections used on the mobo.

So, I removed all the front panel wires from the mobo connector before resetting the bios to default.

When I rebooted, I heard audio from my speakers (the rear panel speakers were connected to the lime green audio connector on the back of the punchbox). The audio is clean and sounds great.

But, the mic input (pink jack) does nothing when my mic is plugged into it.

It was late, I stopped testing at that point and went to bed.

So, I do have some audio now, but something isn't quite right.

More info later.

Art

---

### Post by opensshd on 2012-09-05
Sounds like progress =]

Yah, I run gnome-shell window manager so perhaps the packages installed will be different, re: Alsa.

Seems you now have hardware support, perhaps the mic is just a matter of settings... perhaps muted? If you check your sound mixer properties/settings you may find it's a simple setting.

Glad you are making some headway!

Dale

---

