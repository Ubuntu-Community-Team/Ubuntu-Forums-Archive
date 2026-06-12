---
title: "audacious2 seg faults in Karmic"
date: 2009-11-20
forum: Multimedia Software
---

### Post by mocha on 2009-11-20
I just upgraded a 32 bit box from Jaunty to Karmic.  Audacious got updated to "audacious2" and now all it does is seg fault and I get messages like this in /var/log/messages:

```
audacious2[32132]: segfault at 0 ip 00e5791a sp bff0f870 error 4 in libglib-2.0.so.0.2200.2[e37000+b4000]
```

Is anyone else having this problem?  I even tried installing a version from source and still have the same problem.  I guess a bug in libglib??

---

### Post by a7j_72 on 2009-11-21
Not sure if this will help...
but you could try to look up libglib under Synaptics package manager... and re-installing all currently installed packages.

Maybe easier, just delete and reinstall Audacious2.

hopefully it helps.

"Segmentation fault usually means that the program
is trying to access memory which doesn't belong to
it, and the kernel smacks it over the head." - Tinkster

---

### Post by Melcar on 2009-11-21
Do you by any chance have the sampling rate converter enabled?  Audacious2 doesn't seem to work if you have that one (for me at least).

---

### Post by a7j_72 on 2009-11-21
> **Melcar said:**
> Do you by any chance have the sampling rate converter enabled?  Audacious2 doesn't seem to work if you have that one (for me at least).

I think it has to do with which output plugin you have selected... The plugin might not support this.

---

### Post by Melcar on 2009-11-21
Tried it with both PA (GNOME) and without (KDE).  Same result.  Worked fine in before.

---

### Post by mocha on 2009-11-22
I renamed the config directory and it just keeps seg faulting the same way.  I don't think it has anything to do with the configuration.

---

### Post by mocha on 2009-11-22
Okay I think I figured it out.  Haven't done extensive testing yet but this appears to work.  There is a problem with the timidity.so input library.  Rename the file "/usr/lib/audacious/Input/timidity.so" to something like timidity.so.old and then audacious2 should be able to run.  It won't play MIDI's anymore, but totem still plays them fine anyway, and I'm probably one of the few people around that still screws around with MIDI's anyway...

---

### Post by mc4man on 2009-11-22
redundant - solved

---

