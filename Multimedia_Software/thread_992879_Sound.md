---
title: "Sound"
date: 2008-11-25
forum: Multimedia Software
---

### Post by McJagger on 2008-11-25
Hi.

I can't get sound to work with Ubuntu 8.10 using a Gigabyte GA-MA78GM-S2H with HDMI and S/PDIF, AMD 780G Chipset.

I have tried ALSA and PulseAudio, but no luck...



```

ante@filer:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC885 Analog [ALC885 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC885 Digital [ALC885 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0




lspci -v

01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller
        Subsystem: ATI Technologies Inc RS780 Azalia controller
        Flags: bus master, fast devsel, latency 0, IRQ 19
        Memory at fdffc000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel

```


All volumes i the mixers are at maximum.

Analogue works fine, but no HDMI or S/PDIF output.

Any ideas?

---

### Post by EMCBSB on 2009-05-01
Hi!
Do you solve this problem?
I have the same.
Edson
edson@edson-pc:~$ aplay -l
**** Lista de Dispositivos PLAYBACK Hardware ****
placa 0: SB [HDA ATI SB], dispositivo 0: ALC883 Analog [ALC883 Analog]
  Dispositivo secundário: 0/1
  Dispositivo secundário #0: subdevice #0
placa 0: SB [HDA ATI SB], dispositivo 1: ALC883 Digital [ALC883 Digital]
  Dispositivo secundário: 1/1
  Dispositivo secundário #0: subdevice #0
placa 1: HDMI [HDA ATI HDMI], dispositivo 3: ATI HDMI [ATI HDMI]
  Dispositivo secundário: 1/1
  Dispositivo secundário #0: subdevice #0

---

