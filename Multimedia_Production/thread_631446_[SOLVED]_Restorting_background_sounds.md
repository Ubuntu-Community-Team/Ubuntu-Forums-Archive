---
title: "[SOLVED] Restorting background sounds"
date: 2007-12-04
forum: Multimedia Production
---

### Post by Ebuntor on 2007-12-04
Hi everyone,

I have a recording with a voice and special background sounds. I'd like to filter out the voice and restore the background sounds.
Is there an option to this with Audacity or similar apps?

Thanks in advance.

---

### Post by Stochastic on 2007-12-05
install the ladspa plugins and then use the karaoke plugin (can do this  in any ladspa compatible editor such as audacity, rezound, ardour, jokosher, etc...).

---

### Post by Ebuntor on 2007-12-05
> **Stochastic said:**
> install the ladspa plugins and then use the karaoke plugin (can do this  in any ladspa compatible editor such as audacity, rezound, ardour, jokosher, etc...).


Thank you, I'll try that. :)

---

### Post by Ebuntor on 2007-12-06
In case someone else is looking for the LADSPA plugins you can find them in the swh-plugins package in synaptic.

Or you can just enter this command in the terminal:

```
sudo aptitude install swh-plugins
```Unfortunately the karaoke plugin only really works with stereo tracks where the singer is in the "middle" of both the left and right tracks. What the karaoke plugin does is just invert one of the tracks to filter out the vocal sounds. Therefore the instruments on both the left and right tracks have to be identical.

---

