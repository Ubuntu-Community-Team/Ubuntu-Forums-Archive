---
title: "Dell inspiron mini 1018 no wireless -  says hardware switch disabled"
date: 2012-08-30
forum: Networking &amp; Wireless
---

### Post by blazing64 on 2012-08-30
Hello, I have a Dell Inspiron mini, and as the description says, wireless is not working... I am currently hard-wired for internet... please, if someone is willing to walk me through, that would be great...

---

### Post by Squirty on 2012-09-17
Hello,
After having benefited a long time from the tons of documentation that is available through this forum, this is my first attempt to help to solve a thread, so if anything is not clear or simply incorrect, don't hesitate to let me know.
I had the same problem with a Dell Vostro and managed to fix it, will just list the steps I took below:


[LIST]
[*]Check in BIOS if wireless is ENABLED (if not: enable)
[*]Reset BIOS defaults
[*]Open a terminal window, type in following command:  **sudo rmmod -f dell-laptop**
rmmod  will unload a module; option  -f means "force" (&#8771;  "/force" in  windows); this will allow the module to be unloaded even while in use.
[*]Previous command made certain that wireless worked, but after the next boot wireless was disabled again.
To  solve this, I edited blacklist.conf (read-only, so open it using  terminal window and type something like sudo gedit  /etc/modprobe.d/blacklist.conf).
type **blacklist dell-laptop** in a new line in the document and save.
[/LIST]
After this, problem was solved.
Wireless is available after booting.

---

