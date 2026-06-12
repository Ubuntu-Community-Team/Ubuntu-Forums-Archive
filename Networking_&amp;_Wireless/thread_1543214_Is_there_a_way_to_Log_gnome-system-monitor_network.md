---
title: "Is there a way to Log gnome-system-monitor network history"
date: 2010-07-31
forum: Networking &amp; Wireless
---

### Post by the_scientist on 2010-07-31
I was wondering if there was a way to save the gnome-system-monitor network history  to a file so that I can monitor my monthly bandwidth usage ..... ?

Any suggestions would be helpful


solution * now using [I]vnStat , It meets my requirements *
[/I]

---

### Post by samthethe on 2012-05-19
ifstat all the way. It does EXACTLY what you want with GREAT EASE.

Took me three hours to find it (think I installed about 100 packages).

ifstat -t >/path/to/log

Does EXACTLY what any normal person would want.

Use wget with limit flag in a loop to use, say 20KB, then TADA you have a long term connection monitor in about 10 line bash script. I download from a work server, but it's easy to find any old site. You can then diagnose dodgy internet EASY PEASY, unlike the billion other rubbish tools out there that require you to be sysadm of massive company with 10 years experience using the dam tool.

---

