---
title: "Backup DVD collection to iso"
date: 2008-09-05
forum: Multimedia Software
---

### Post by ubernoob on 2008-09-05
Hi! 


I have several hundred DVD movies that i own, which i want to backup. Converting them to another format would take too much time, so i would like to back it all up to iso files. (This is legal in my country)

I'm thinking of buying 3 DVD-players to speed up the whole process. What is the easiest way to do the backup?

Does dvdrip support ripping from several dvd players at the same time?

Is is possible to automate it through a script? Can i extract dvd-title in some way to automatically name the iso-files?


Best regards

ubernoob

---

### Post by mc4man on 2008-09-05
taking structure protected titles out of the equation you could use vobcopy to rip to a folder based on volume name with a VIDEO_TS inside.( usually title name

By setting vobcopy as the default (autorun) choice for dvd movie player and using a script as the launch command you can automatically rip multiple titles from multiple drives at the same time.
If your interested let me know and I'll post complete instr. (gotta go to work

Here's the script (only works with multiple drives when run from an autorun launcher
Tested with 2 titles and 2 drives simultaneously  - no problems, only **minor** decrease in rip speed (maybe a min. or so

```
#!/bin/bash
gnome-terminal -e "vobcopy -v -m -F 16" /media/*

```

---

