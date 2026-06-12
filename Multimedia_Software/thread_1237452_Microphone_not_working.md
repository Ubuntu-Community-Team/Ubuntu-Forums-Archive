---
title: "Microphone not working"
date: 2009-08-11
forum: Multimedia Software
---

### Post by whisp71 on 2009-08-11
Hello. Can't record/talk in Audacity/Mumble
Motherboard Asus P5Q-E, integrated audio (snd-hda-intel). Headset w/ mic (was tested in WinXP). 

In KMixer Mic is unmuted, Mic boost is on 1st level (tried other values). Same in alsamixer. In "System Settings -> Multimedia" HDA Intel is set default for Audio capture (tried setting it default for everything, no result). (additional PCI soundcard installed).
Headphones are working fine.

Note: In VLC i can choose between ALSA outputs on-fly (between soundcards). After opening and closing "System Settings -> Multimedia", VLC settings are being ignored and sound goes only through PCI soundcard. This gives me a strong suspicion that this configuration utility screwing things up. Is there any way to disable it?

```
username@compname:~/Desktop$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Juli [ESI Juli@], device 0: ICE1724 [ICE1724]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Juli [ESI Juli@], device 1: IEC1724 IEC958 [IEC1724 IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```Any suggestions? Thanks in advance.

[SOLVED] by installing ubuntu and configuring pulseaudio and alsamixer.

---

### Post by whisp71 on 2009-08-12
-[solved]

---

