---
title: "Sound dies in Kubuntu 10.10 after a few minutes of usage"
date: 2010-10-27
forum: Multimedia Software
---

### Post by UrbenLegend on 2010-10-27
I installed Kubuntu 10.10 and realized that the sound would suddenly stop working after a few hours. This occurs randomly and doing a sudo alsa force-reload and then a sudo killall pulseaudio does not restore sound. This is really frustrating since I've experienced this bug before in Kubuntu 9 and they fixed it, but now the problem is back.

Does anyone know what's going on?

---

### Post by gwillhardt on 2010-10-27
I have the same problem with Ubuntu 10.04 LTS. Anyone know how to fix it in this edition.

---

### Post by UrbenLegend on 2010-11-02
Are you using pulseaudio?

---

### Post by UrbenLegend on 2010-11-03
There was an ALSA update today. Hopefully that fixes it.

---

### Post by UrbenLegend on 2010-11-03
Nvm that update did nothing.

---

### Post by UrbenLegend on 2010-12-25
Currently I am working around this by disabling pulseaudio from starting up on boot up. You can do this by executing the command:
```
echo autospawn = no >> ~/.pulse/client.conf
```
This will force everything to use ALSA which works perfectly.

---

