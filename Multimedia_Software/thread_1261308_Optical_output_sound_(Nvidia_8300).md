---
title: "Optical output sound (Nvidia 8300)"
date: 2009-09-08
forum: Multimedia Software
---

### Post by ezacon on 2009-09-08
I have an HTPC based on ASUS M3N78-EM (nvidia 8300) with Windows 7 64 and Ubuntu 9.04 64.
In windows 7, i now have sound in optical output but hdmi sound does not work.
In linux, i have sound in HDMI, but optical output is not working.

In linux, i want to use hdmi sound to play movies with VLC (it is now working) and optical output to play music with MPD in the 5.1 amp (not working).

aplay -l show 1 interface and 3 ports
**** Lista de PLAYBACK Dispositivos Hardware ****
tarjeta 0: NVidia [HDA NVidia], dispositivo 0: ALC1200 Analog [ALC1200 Analog]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
tarjeta 0: NVidia [HDA NVidia], dispositivo 1: ALC1200 Digital [ALC1200 Digital]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
tarjeta 0: NVidia [HDA NVidia], dispositivo 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0

Port 3 is HDMI and  1 is optical output.

In have added this to /etc/mpd.conf

audio_output {
        type                    "alsa"
        name                    "5.1 Fibra"
        device                  "hw:0,1"     # optional
#       format                  "44100:16:2" # optional
}

If i use hw:0,3 the sound is played in HDMI but if i use hw:0,1, no sound in HDMI or optical.

In sound config application, if i select HDMI an test, i can heard the "beep" test but when i chose optical and test, no sound.

Anybody has optical output working in linux with this chipset?

---

