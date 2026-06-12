---
title: "ices2 won't start in ALSA-mode (Lucid)"
date: 2010-04-29
forum: Multimedia Software
---

### Post by produnis on 2010-04-29
Hi folks,  I did a fresh install of Lucid today.  While under Jaunty and Karmic, I run ices2 in alsa-mode using this xml:

---

### Post by produnis on 2010-04-29
(dont know whats going on here, so here is my post)

Now, running a fresh install of Lucid, ices2 crashes. The Log-File shows:

[2010-04-29  20:26:31] INFO ices-core/main IceS 2.0.1 started...
[2010-04-29  20:26:31] EROR input-alsa/alsa_open_module Error setting 2 periods: Invalid argument
[2010-04-29  20:26:31] EROR input/input_loop Couldn't initialise input module "alsa"
[2010-04-29  20:26:31] INFO ices-core/main Shutdown complete

Does anyone know how to fix that?

---

### Post by produnis on 2010-04-30
Got it.

In the ices2.xml-File, I removed this entry:
[PHP]param name="periods">2</param[/PHP]

This entry created the "interrupts". I don't really know what it was for,
and it worked with jaunty and karmic,
but in lucid I needed to remove it...

Now it works

---

