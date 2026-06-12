---
title: "Alsamixer will not start"
date: 2010-01-27
forum: Multimedia Software
---

### Post by tylersontag on 2010-01-27
Hey all,

I just got a new nvidia video card and i'm trying to get sound to carry over the HDMI out.   I'd read the normal process is to open up alsa mixer and simply unmute HDMI out, which is muted by default.

However, I'm trying to run alsamixer and i get this error

```
alsamixer: function snd_mixer_load failed:  Invalid argument
```

Also... interestingly enough aplay -l doesn't list my HDMI OUT... thought lspci -v lists this for it

```
01:00.1 Audio device: nVidia Corporation Device 0be3 (rev a1)
	Subsystem: Giga-byte Technology Device 34d5
	Flags: bus master, fast devsel, latency 0, IRQ 10
	Memory at f9e7c000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
```


Any suggestions?

---

### Post by tylersontag on 2010-01-28
any advice?  I'm currently using alsa (as opposed to OSS) so im thinking this has to be a largly superficial error...

---

