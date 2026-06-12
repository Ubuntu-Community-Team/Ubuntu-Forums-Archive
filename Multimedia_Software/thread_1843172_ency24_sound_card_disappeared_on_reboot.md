---
title: "ency24 sound card disappeared on reboot?"
date: 2011-09-13
forum: Multimedia Software
---

### Post by DatBugler on 2011-09-13
I just discovered upon rebooting my computer that my envy24 sound card no longer shows up to ALSA. lsmod shows that the appropriate module is loaded, but ALSA doesn't notice it for some reason. What can I do?

```
~$ lspci | grep 1712
04:05.0 Multimedia audio controller: VIA Technologies Inc. ICE1712 [Envy24] PCI Multi-Channel I/O Controller (rev 02)

~$ lsmod | grep 1712
snd_ice1712            66696  0 
snd_ice17xx_ak4xxx      3115  1 snd_ice1712
snd_ak4xxx_adda         9318  2 snd_ice1712,snd_ice17xx_ak4xxx
snd_cs8427              7938  1 snd_ice1712
snd_ac97_codec        125227  1 snd_ice1712
snd_i2c                 5574  2 snd_ice1712,snd_cs8427
snd_mpu401_uart         6849  1 snd_ice1712
snd_pcm                89104  6 snd_usb_usx2y,snd_usb_audio,snd_ice1712,snd_ac97_codec,snd_hda_intel,snd_hda_codec
snd                    64277  20 snd_usb_usx2y,snd_usb_audio,snd_usbmidi_lib,snd_ice1712,snd_ak4xxx_adda,snd_cs8427,snd_ac97_codec,snd_i2c,snd_mpu401_uart,snd_hda_codec_via,snd_hda_intel,snd_hda_codec,snd_rawmidi,snd_hwdep,snd_pcm,snd_seq,snd_timer,snd_seq_device

~$ cat /proc/asound/cards
 0 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xfbff4000 irq 16
 1 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xfe97c000 irq 19
 2 [PCR            ]: USB-Audio - PCR
                      EDIROL PCR at usb-0000:00:12.1-2, full speed
 3 [USX2Y          ]: USB US-X2Y - TASCAM US-X2Y
                      TASCAM US-X2Y (1604:8007 if 0 at 004/007)

~$ cat /proc/asound/modules
 0 snd_hda_intel
 1 snd_hda_intel
 2 snd_usb_audio
 3 snd_usb_usx2y
```

---

### Post by DatBugler on 2011-09-13
Possible solution?

I have a copy of my old /proc/asound/cards. Would it work if I just pasted the old section for the missing card into /proc/asound/cards and then used alsa-utils to restart the card? I'm hesitant to try this without some input, for fear of borking things even worse.

---

