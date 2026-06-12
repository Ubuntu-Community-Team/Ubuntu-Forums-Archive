---
title: "pacmd issues."
date: 2015-04-24
forum: Multimedia Software
---

### Post by pingaan on 2015-04-24
Hi,

I'm trying to use pacmd to chose default sound output but the device I want to use is not listed when typing;
```
pacmd list-sinks | grep name:
```

Some additional info I can provide is that it is a coaxial s/pdif port which is integrated on the motherboard.
I'm able to choose it from the gui sound devices.

Regards.

---

### Post by dino99 on 2015-04-24
when i need to tweak sound, i'm using pavucontrol, which let you set the 'config' & 'Output Devices' tabs
try to find the good working choices from these tabs: 'config' first, then 'output devices'

---

### Post by pingaan on 2015-04-24
I want the computer to boot up with the s/pdif as default output, no matter which is default when I shut down.
Is that possible using puvacontrol?

---

### Post by pingaan on 2015-04-24
Cheers, sorted it out with pavucontrol! :)

---

