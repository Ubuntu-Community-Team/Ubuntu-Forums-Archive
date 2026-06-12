---
title: "Rhythm box only starting with --no-registration"
date: 2008-07-14
forum: Multimedia Software
---

### Post by moon300 on 2008-07-14
Hi all, I have the following problem:
Rhythmbox does not start. When I start it with 'rhythmbox -d' it produces the following output:

[0x80fb408] [rb_debug_init_match] rb-debug.c:153: Debugging enabled
[0x80fb408] [main] main.c:171: initializing Rhythmbox 0.11.2
[0x80fb408] [rb_threads_init] rb-util.c:460: GMutex isn't recursive
[0x80fb408] [main] main.c:179: going to create DBus object
[0x80fb408] [main] main.c:322: THE END

(the version might be 0.11.5/6, well at least the last version you get from apt-get update, apt-get upgrade).
Rhythmbox does start with: 'rhythmbox --no-registration', but then complains about plugins failing to load and other things. I'm not sure what the --no-registration option does. Can anybody explain? Is there a way I can start rhythmbox normally again?

Solutions tried:
- apt-get install --reinstall rhythmbox  : doesn't solve it
- Searched the internet for users with similar problems, no solutions found

OS is Ubuntu Hardy 8.04

Greetings,
          moon300

---

