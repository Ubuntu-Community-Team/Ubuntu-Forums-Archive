---
title: "Sound card not detected"
date: 2007-11-14
forum: Multimedia &amp; Video
---

### Post by qiemem on 2007-11-14
I haven't had any sound issues since about edgy, but today I turned on my laptop (Compaq Presario R3000) and kmix says it can't find any mixer.  Turns out its not being detected.  Here's the relevant info:
```

$ aplay -l
aplay: device_list:204: no soundcards found...

$ lspci -v
...
00:06.0 Multimedia audio controller: nVidia Corporation nForce3 Audio (rev a2)
        Subsystem: Hewlett-Packard Company Unknown device 006d
        Flags: 66MHz, fast devsel, IRQ 19
        I/O ports at 1400 [size=256]
        I/O ports at 1c00 [size=128]
        Memory at e8002000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>
...

$ alsamixer
alsamixer: function snd_ctl_open failed for default: No such device

```

I've tried "sudo modprobe snd-intel8x0" to no avail.  Here's the relevant alsa project page: [http://www.alsa-project.org/main/index.php/Matrix:Vendor-Nvidia](http://www.alsa-project.org/main/index.php/Matrix:Vendor-Nvidia)

Any ideas?

---

### Post by qiemem on 2007-11-14
Well, its working perfectly again.  I didn't anything either... weird. Ah well.

---

