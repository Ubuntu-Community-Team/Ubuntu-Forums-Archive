---
title: "Sound stops in Jaunty"
date: 2009-06-13
forum: Multimedia Software
---

### Post by dundee5 on 2009-06-13
Hi,
if I'm playing Mafia (wine), the sound stops after while (few seconds to few minutes). This didn't happen before (in 8.10).

Probably pulseaudio is using too much processor and stops itself.

I tried some hacks in /etc/pulse/daemon.conf:
high-priority = yes
nice-level = 3
no-cpu-limit = yes

But nothing helps.

Any solution?

---

### Post by dundee5 on 2009-06-14
It could be Wine problem as well. This message appears many times:

fixme:d3d:state_zenable W buffer is not well handled

---

### Post by duanerobertson on 2009-06-14
After I installed 9.04, World of Warcraft gave me a lot of sound-related errors. I ended up removing pulseaudio altogether and going back to alsa. To be honest, it wasn't worth the time to troubleshoot for me.

---

### Post by dundee5 on 2009-06-15
> **duanerobertson said:**
> After I installed 9.04, World of Warcraft gave me a lot of sound-related errors. I ended up removing pulseaudio altogether and going back to alsa. To be honest, it wasn't worth the time to troubleshoot for me.

It works, thank you!

Guide how to replace pulseaudio with alsa:
[http://ubuntuforums.org/showthread.php?t=1149634]("http://ubuntuforums.org/showthread.php?t=1149634")

Or simply:
```
sudo apt-get remove gstreamer0.10-pulseaudio libpulse-browse0 libpulsecore9 pulseaudio-module-gconf pulseaudio-module-hal pulseaudio-module-x11 pulseaudio-utils
```

---

