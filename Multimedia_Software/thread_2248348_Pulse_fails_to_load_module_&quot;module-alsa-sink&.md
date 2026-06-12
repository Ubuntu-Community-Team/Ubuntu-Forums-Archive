---
title: "Pulse fails to load module &quot;module-alsa-sink&quot;"
date: 2014-10-14
forum: Multimedia Software
---

### Post by thekiwi5000 on 2014-10-14
Hello,

I'm trying to set up my pulseaudio to work.

```
kiwi@kiwi-gigabyte:~$ pulseaudio
E: [pulseaudio] module.c: Failed to load module "module-alsa-sink" (argument: "device=hw:0,0"): initialization failed.
E: [pulseaudio] main.c: Module load failed.
```

That's the failing line:

```
load-module module-alsa-sink device=hw:0,0
```

and that's the aplay -l output

```
**** Lista PLAYBACK urz&#261;dze&#324; ****
card 0: SB [HDA ATI SB], device 0: ALC889 Analog [ALC889 Analog]
  subdevices: 1/1
  subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC889 Digital [ALC889 Digital]
  Urz&#261;dzenia podrz&#281;dne: 1/1
  subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  subdevices: 1/1
  subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: HDMI 0 [HDMI 0]
  subdevices: 1/1
  subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: HDMI 0 [HDMI 0]
  subdevices: 1/1
  subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: HDMI 0 [HDMI 0]
  subdevices: 1/1
  subdevice #0: subdevice #0
```

also, is there any way to disable command outputs translations? (i had to translate aplay output )

---

