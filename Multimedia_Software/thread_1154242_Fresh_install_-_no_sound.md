---
title: "Fresh install - no sound"
date: 2009-05-09
forum: Multimedia Software
---

### Post by Red_Beret on 2009-05-09
Hey,

I just install Jaunty on my desktop, but i have no sound :(

The sound card is an Realtek ALC880.

The system is connected to an amplifier, using Coaxial S/PDIF

When i execute 

```
aplay -l
```

i got

```
**** Lista de Dispositivos de Hardware PLAYBACK ****
placa 0: Intel [HDA Intel], dispositivo 0: ALC880 Analog [ALC880 Analog]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0

```

Can anyone help me. I'm totally noob on Linux..

---

### Post by The Mad Mule on 2009-05-09
Have you looked at all the other "no sound" threads? There are a couple of mega ones.

---

### Post by apparle on 2009-05-09
I didn't get ALSA to work for me so I just installed OSS sound drivers.
Try to get ALSA working, if it doesn't work then install OSS drivers
[http://www.opensound.com](http://www.opensound.com)

---

### Post by Red_Beret on 2009-05-09
> **The Mad Mule said:**
> Have you looked at all the other "no sound" threads? There are a couple of mega ones.

yes, some of them, but some of the solutions are too complex, and others don't even apply (edit files that don't exist on my system...)

:(

---

