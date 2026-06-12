---
title: "nVidia CK804 AC'97 Audio Controller - Scratchy and fading sound"
date: 2011-07-13
forum: Multimedia Software
---

### Post by feyeer on 2011-07-13
Hi,

To make a long story short:
I've got a vanilla ubuntu 11.04 installed, everything seemes to be working perfectly, sound incl. However after a certain amount of time (15min) the sound card misteriously starts to make scratchy noise (like an old turntable player) and  soon after it stops playing back. Sometimes a reboot helps but not always.

Anybody know how to fix this? Thanks in advance.

The PC has an integrated sound card
```

00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
	Subsystem: ASUSTeK Computer Inc. K8N4-E or A8N-E Mainboard
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
	I/O ports at dc00 [size=256]
	I/O ports at e000 [size=256]
	Memory at db103000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: Intel ICH
	Kernel modules: snd-intel8x0

```

Modules used:

```

snd_wavefront          34696  0 
snd_usb_audio          91410  1 
snd_cs4236             29291  0 
snd_intel8x0           33213  1 
snd_wss_lib            30006  2 snd_wavefront,snd_cs4236
snd_ac97_codec        105614  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_opl3_lib           18760  2 snd_wavefront,snd_cs4236
snd_pcm                80244  6 snd_cs4236,snd_usb_audio,snd_intel8x0,snd_ac97_codec,snd_wss_lib,saa7134_alsa
snd_hwdep              13274  3 snd_wavefront,snd_usb_audio,snd_opl3_lib
snd_usbmidi_lib        24388  1 snd_usb_audio
snd_mpu401             13800  0 
snd_mpu401_uart        13865  3 snd_wavefront,snd_cs4236,snd_mpu401
snd_seq_midi           13132  0 
snd_rawmidi            25269  4 snd_wavefront,snd_usbmidi_lib,snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28659  4 snd_wss_lib,snd_opl3_lib,snd_pcm,snd_seq
snd_seq_device         14110  4 snd_opl3_lib,snd_seq_midi,snd_rawmidi,snd_seq
snd                    55295  23 snd_wavefront,snd_usb_audio,snd_cs4236,snd_intel8x0,snd_ac97_codec,snd_wss_lib,snd_opl3_lib,saa7134_alsa,snd_pcm,snd_hwdep,snd_usbmidi_lib,snd_mpu401,snd_mpu401_uart,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
snd_page_alloc         14073  3 snd_intel8x0,snd_wss_lib,snd_pcm
soundcore              12600  1 snd

```

---

### Post by lidex on 2011-07-14
Try resetting your pulse configuration.
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
sudo rm /etc/asound.conf
```
**Reboot**
* Ignore any 'No such file or directory' errors*

---

