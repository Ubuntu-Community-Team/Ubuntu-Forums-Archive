---
title: "Broken Sound When Using Festival"
date: 2010-08-03
forum: Multimedia Software
---

### Post by Cerin on 2010-08-03
I'm running Ubuntu 10.04 on a Macbook Pro 5.5. I'm trying to use Festival, and while the install seemed to proceed without error, I'm getting inconsistent sound generation.

When I ran this the first time, I had perfect speech generation:
```
echo '(SayText "hello world")' | esddsp festival --pipe
```

However, when I ran it a second time, the sound was all garbled and broken. If I open up the Sound Preferences dialog and switch the profile back and forth from "Analog Surround 4.0 Output", playback will work again...until I close the Sound Preferences dialog. Then it's broken again.

When I run that command, I'm also getting the warning/error message:

```
ERROR: ld.so: object '/usr/lib/esound/libesddsp.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libesd.so.0' from LD_PRELOAD cannot be preloaded: ignored.
```

This seems to be a [reported bug]("https://bugs.launchpad.net/ubuntu/+source/esound/+bug/214465"), which was allegedly resolved long ago...

What could be causing this unreliable playback?

---

