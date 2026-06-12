---
title: "Get IDJC working with a usb headset"
date: 2009-08-01
forum: Multimedia Software
---

### Post by Eviltechie on 2009-08-01
Ok here's what I want to do. I want to get IDJC working with my logitech G35 headset. Does anyone know how to do this? I know that I need to get jack working and I'll probably need pulseaudio too. Anyone know how to do this?

---

### Post by StephenF on 2009-08-04
> **Eviltechie said:**
> Ok here's what I want to do. I want to get IDJC working with my logitech G35 headset. Does anyone know how to do this? I know that I need to get jack working and I'll probably need pulseaudio too. Anyone know how to do this?
This is more a question of getting jack-audio-connection-kit working with your headset.

---

### Post by bobince on 2009-08-05
Yeah, you should load qjackctl and hit ‘Setup’, then pick out your headset for both ‘Input Device’ and ‘Output device’. When you start it up, JACK applications including idjc should use your headset's audio device for everything, ignoring the usual default sound card.

---

