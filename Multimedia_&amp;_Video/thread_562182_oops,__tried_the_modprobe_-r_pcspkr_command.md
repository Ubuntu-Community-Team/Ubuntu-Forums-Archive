---
title: "oops,  tried the modprobe -r pcspkr command"
date: 2007-09-28
forum: Multimedia &amp; Video
---

### Post by Peppyreek on 2007-09-28
I wanted to disable my internal laptop speakers, but, erm, ended up without sound at all. The unforunate event happened when i typed 
**modprobe -r pcspkr**
Can someone come up with a solution to redo my mistake?

Grateful for all help!

PS.
Does anyone know how to permanently disable laptop speakers? tried all the easy solutions in sound preferences. The system don't seem to recognize the difference between internal-speakers and headphones as i get no  difference in sound levels with the front/headphone controller.

---

### Post by overkillm on 2007-09-28
Does the following work?

```
modprobe -a pcspkr
```

If not, does the problem persist after a reboot?

As for permanently disabling laptop speakers... I don't know... someone more knowledgeable than me (not hard to come by) will have to answer that one.

---

### Post by Peppyreek on 2007-09-29
Thanks, worked out fine in the end, 
rebooting can solve many problems:)

---

