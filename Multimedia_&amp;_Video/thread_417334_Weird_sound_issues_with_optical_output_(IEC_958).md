---
title: "Weird sound issues with optical output (IEC 958)"
date: 2007-04-21
forum: Multimedia &amp; Video
---

### Post by justinlindh on 2007-04-21
If someone can help me with this sound issue, I'll be your best friend.

Basically, my sound comes from an optical audio output (fiber optic) on my motherboard. I've set the "Sound playback" device to NVidia CK8S - IEC958 in "Sound Preferences" to get sound working in some apps. I can get sound from Beep Music Player/Movie Player, but not most others. If I click the "Sounds" tab in "Sound Preferences" and try to play any of the system sounds, I hear nothing. Flash in Firefox plays no sound (which I really need so I can use Rhapsody on Linux). The Test Sound won't play for ALSA/ESD/OSS (only when I specifically pick the CK8S - IEC958), either.

I have a feeling that ALSA just isn't working with the optical port. Here's some command output:

expired@lindros-linux:/etc/modprobe.d$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: CK8S [NVidia CK8S], device 0: Intel ICH [NVidia CK8S]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CK8S [NVidia CK8S], device 2: Intel ICH - IEC958 [NVidia CK8S - IEC958]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

expired@lindros-linux:/etc/modprobe.d$ cat /proc/asound/cards
 0 [CK8S           ]: NFORCE - NVidia CK8S
                      NVidia CK8S with ALC850 at 0xff6fb000, irq 201
 1 [UART           ]: MPU-401 UART - MPU-401 UART
                      MPU-401 UART at 0x300, irq 5

Can anybody help me? I've been fighting this for months.

---

