---
title: "Rhythmbox Freezing when attempting to play .wma"
date: 2009-10-29
forum: Multimedia Software
---

### Post by BrynC on 2009-10-29
As the title suggests, my rhythmbox freezes whenever I attempt to play .wma files. Problem first cropped up a few days ago, hadn't had any issues before. Normally, it seems to function fine, it just won't play back, until I attempt to change the song, at which point it freezes entirely. 

In simple terms, I'm a bit stumped. Running Jaunty on an Acer Aspire 5535, (250GB HDD, 4GB memory, 2GHz AMD Turion X2 processor).

---

### Post by BrynC on 2009-10-29
Debug gives me the following, fyi:
$ rhythmbox --debug
(17:50:53) [0x8815408] [rb_debug_init_match] rb-debug.c:215: Debugging enabled
(17:50:53) [0x8815408] [main] main.c:187: initializing Rhythmbox 0.12.0
(17:50:53) [0x8815408] [rb_threads_init] rb-util.c:388: GMutex isn't recursive
(17:50:53) [0x8815408] [main] main.c:195: going to create DBus object
(17:50:53) [0x8815408] [main] main.c:353: THE END

Could be a code error?

---

### Post by BrynC on 2009-11-01
Just bumping to see if anyone can fling some advice my way.

---

