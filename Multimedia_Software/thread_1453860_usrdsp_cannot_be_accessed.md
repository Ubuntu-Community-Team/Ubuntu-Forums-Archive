---
title: "/usr/dsp cannot be accessed"
date: 2010-04-13
forum: Multimedia Software
---

### Post by kooia on 2010-04-13
All my music editing software programs say, "unable to open device /dev/dsp.

Device or resource busy."

How can I fix this?

---

### Post by kooia on 2010-04-16
Yeah, I checked some more programs and they still don't work.

Anyone?  I'm open to any answers.

---

### Post by Yellow Pasque on 2010-04-17
They're trying to use OSS (OpenSound) output. Preferably, you would switch to ALSA or Pulseaudio output. Another possible workaround if you have pulseaudio installed (comes by default with ubuntu), and the pulseaudio-utils package, is to use the padsp utility to route output intended for /dev/dsp into pulseaudio.
```
padsp <programname>
```

If you need more help, please be more specific about which apps are misbehaving and whether you have pulseaudio.

---

### Post by kooia on 2010-04-18
Hi Temujin,

I have pulseaudio installed. (and pulseaudio-utils).  Sweep doesn't work, and I uninstalled some others that didn't work.

Kooia

---

