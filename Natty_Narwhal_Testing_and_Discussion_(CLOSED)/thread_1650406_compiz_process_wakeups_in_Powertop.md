---
title: "compiz process wakeups in Powertop"
date: 2010-12-21
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by hugmenot on 2010-12-21
Since Compiz 0.9.2 I’m seeing 60-70 wakeups a second from the compiz process. Does everybody get that?

Compiz used to wake up only with about 5Hz.

[IMG]http://i.imgur.com/XR5vU.png[/IMG]

---

### Post by cariboo on 2010-12-21
I get pretty similar results, but I seem to be getting longer battery life, than I did with Maverick, I can now use my netbook for 3 hours, before having to plug it in, whereas with maverick it was only lasting for 2.5 hours

---

### Post by MacUntu on 2010-12-21
Same here. If you feel this is a regression, why not open a bug report? I'd confirm it and add a +1 to "affects me". :)

---

### Post by hugmenot on 2010-12-21
> **MacUntu said:**
> Same here. If you feel this is a regression, why not open a bug report? I'd confirm it and add a +1 to "affects me". :)

[Yes, please do]("http://pad.lv/681696")

---

### Post by hugmenot on 2010-12-26
I’ve disable all of compiz’ plugins one-by-one, but those wakeups seem to arise from compiz core. i.e., not from mouse polling, etc.

---

### Post by Amaranth on 2010-12-26
This is caused by using glib timers in core instead of our own custom made timers. 0.8 and the main 0.9 upstream code do not have this issue, only the glib branch does (which ubuntu uses). We're going to write our own timer system again but this time hooking in to the glib mainloop to solve this problem.

---

### Post by MacUntu on 2010-12-26
Thanks for the clarification!

---

### Post by hugmenot on 2010-12-26
> **Amaranth said:**
> This is caused by using glib timers in core instead of our own custom made timers. 0.8 and the main 0.9 upstream code do not have this issue, only the glib branch does (which ubuntu uses). We're going to write our own timer system again but this time hooking in to the glib mainloop to solve this problem.


Cool thanks. The 60Hz now eat battery.

---

### Post by hugmenot on 2011-01-14
Fixed as of today:

[IMG]http://i.imgur.com/GXVyX.png[/IMG]

---

