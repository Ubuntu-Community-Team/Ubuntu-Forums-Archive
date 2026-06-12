---
title: "Speakers not working properly"
date: 2020-05-12
forum: Multimedia Software
---

### Post by hollowsaibot on 2020-05-12
Hi,

I bought a new PC with speakers Mars gaming MS2, wich only sounds from 1 speakers (it is 2.1)
On Ubuntu 18/19 the sound was out from one of them (front-left). Now in 20.04 from the subwoofer. 

I tried a lot of things thinking at the begining that was an Alsa bug or something related to the Realtek drivers.
Now I am checking the usb. I think that this speaker it is not recognized properly even if it sounds, and can't make play the audio well.

*The point with this speaker it is that needs a usb port to supply and a Jack output, and for this reason it can't work well at all neither.
Any help? please! :)

```

carlos@carlos-ubuntu:~$ aplay -l
**** Lista de PLAYBACK dispositivos hardware ****
tarjeta 0: PCH [HDA Intel PCH], dispositivo 0: ALC1220 Analog [ALC1220 Analog]
  Subdispositivos: 0/1
  Subdispositivo #0: subdevice #0
tarjeta 0: PCH [HDA Intel PCH], dispositivo 1: ALC1220 Digital [ALC1220 Digital]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
tarjeta 2: NVidia [HDA NVidia], dispositivo 3: HDMI 0 [HDMI 0]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
tarjeta 2: NVidia [HDA NVidia], dispositivo 7: HDMI 1 [HDMI 1]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
tarjeta 2: NVidia [HDA NVidia], dispositivo 8: HDMI 2 [HDMI 2]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
tarjeta 2: NVidia [HDA NVidia], dispositivo 9: HDMI 3 [HDMI 3]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0

```


My tests are those (with usb speaker and without shows the same
```

carlos@carlos-ubuntu:~$ lsusbBus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 0d8c:0134 C-Media Electronics, Inc. 
Bus 001 Device 002: ID 05e3:0610 Genesys Logic, Inc. 4-port hub
Bus 001 Device 005: ID 046d:c077 Logitech, Inc. M105 Optical Mouse
Bus 001 Device 003: ID 1c4f:0002 SiGma Micro Keyboard TRACER Gamma Ivory
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

---

