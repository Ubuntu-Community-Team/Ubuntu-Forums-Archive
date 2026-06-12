---
title: "alsa + jack input levels"
date: 2008-10-20
forum: Multimedia Software
---

### Post by hellfeuer on 2008-10-20
I have jack setup to use alsa. The problem is that the input levels on my hardware input are too high. Changing this in alsamixer does not help. I also tried killing pulseaudio, moving /etc/asound.conf and then using alsamixer. Still nothing. This problem does not arise when I don't use jack.

Any ideas? For now I have got things to work by:
input -> jackEQ -> output
So I can control gain in jackEQ, but shouldn't the alsamixer settings work? This solution is a hack since if I understand correctly this isn't "really" changing the input level so distortion at the input is still possible.

---

### Post by markbuntu on 2008-10-20
Do you have jack setup to use hardware inputs or "default"?
What application are you trying to use to record with and what is your hardware setup?

---

### Post by hellfeuer on 2009-01-17
I've tried using default and selecting my card (Intel) it doesn't work either way.

Also the application doesn't seem to matter. I can hear a hiss even if I directly connect input to output in jack

---

