---
title: "Simultaneous Audio on 8.04 (Hardy)"
date: 2008-04-26
forum: Multimedia Software
---

### Post by Sirron on 2008-04-26
I can't seem to use some applications that make a noise simultaneously, without one crashing (namely BMPx) or being muted.

If I open Totem, and play a file in it, or just play a file then pause it, then open BMPx and try to play a file, BMPx closes.

If I open Totem, and do not open any file in it, then open BMPx and try to play a file, I get an error report, then BMPx closes.

[IMG]http://img391.imageshack.us/img391/6724/screenshotplaybackerrorjx0.png[/IMG]

Oddly, VLC and Totem can make noises at the same time.

This is really annoying, any ideas?

---

### Post by Sirron on 2008-04-26
Nevermind! I've sorted it, I needed to install the package [_libflashsupport_]("apt:libflashsupport") and set BMPx to "GNOME Configured Audio Output".

---

### Post by the12plus on 2008-05-09
I still do have kind of the same problem. I cannot have sound from zynaddsubfx and any of my players simultaneously. If zynaddsubfx is started first, no player will play (time will be stuck to 0:00) while a player started first will mute zynaddsubfx. Can anyone think of a workaround please? Thanks a lot in advance :)

---

