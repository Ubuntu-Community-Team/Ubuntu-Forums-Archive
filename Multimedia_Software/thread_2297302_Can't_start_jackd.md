---
title: "Can't start jackd"
date: 2015-10-02
forum: Multimedia Software
---

### Post by jose_giraldo on 2015-10-02
I'm unable to start jack.

JACK server starting in realtime mode with priority 10
audio_reservation_init
Acquire audio card Audio0
creating alsa driver ... hw:0|hw:0|1024|2|48000|0|0|nomon|swmeter|-|32bit
ALSA: Cannot open PCM device alsa_pcm for playback. Falling back to capture-only mode
Cannot initialize driver
JackServer::Open failed with -1
Failed to open server


from aplay -l got this

**** Lista de PLAYBACK dispositivos hardware ****
tarjeta 0: HDMI [HDA Intel HDMI], dispositivo 3: HDMI 0 [HDMI 0]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
tarjeta 0: HDMI [HDA Intel HDMI], dispositivo 7: HDMI 1 [HDMI 1]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
tarjeta 0: HDMI [HDA Intel HDMI], dispositivo 8: HDMI 2 [HDMI 2]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
tarjeta 1: PCH [HDA Intel PCH], dispositivo 0: CX20751/2 Analog [CX20751/2 Analog]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0

---

### Post by TokyoGhost on 2015-10-02
Have you seen this thread? [http://ubuntuforums.org/showthread.php?t=1975572](http://ubuntuforums.org/showthread.php?t=1975572)

---

### Post by jose_giraldo on 2015-10-03
I just saw it but I can't find the .jackrc file, it runs when I change the controls in qjackctl but from the terminal keeps showing the error.

---

### Post by jose_giraldo on 2015-10-03
I can run jack from terminal typing:

jackd -d alsa -d  hw:PCH

I'm wonder if there is a way to configure jack to get hw:PCH as default, qjackctl simply did not save the changes

---

