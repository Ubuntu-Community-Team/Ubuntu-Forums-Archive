---
title: "Scan for changes taking over 24 hours"
date: 2011-03-19
forum: Mythbuntu
---

### Post by enoxx on 2011-03-19
I recently reinstalled myhtbuntu 10.10 but have run into a strange issue. When I try to update the video database with "Scan for Changes" it is taking rather long. I have left it running for 24 hours and so far it is only up to 49%. I never recall it taking this long in my previous installs (I have been running myth for 2 years and never recall it taking longer than an hr for the original instll.) I would say there are about 800 TV episodes and movies.

The backend log looks a bit funny, but I'm not sure if this is normal as I have never checked the log when scanning for new files before:

2011-03-20 10:19:19.810 Hash eb59ed65852da916 already exists in the database, updating record 11078 with new filename Movies/Movies/Movies/Movies/Movies/Movies/Movies/Movies/Movies/Movies/Movies/Movies/Movies/Movies/Movies/Movies/Movies/Movies/Movies/Movies/Movies/Movies/Movies/Movies/Movies/Movies/Movies/Movies/Movies/TV/The Big Bang Theory/The.Big.Bang.Theory.S01.avi

What I find weird is its saying "already exists in the database" when this is the first time I have run a scan so the database should be empty. Also, the filename doesn't look right containing that many /Movies.


I have no idea how to trouble shoot this and would be grateful for any help.

Thanks



EDIT: The load on the CPU is quite high

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 1048 mysql     20   0  250m 7200 1252 S  146  0.4 473:24.17 mysqld
 1812 goosie    20   0  994m 391m 5320 S    5 22.3  41:41.26 mythfrontend.re


 10:25:23 up 23:16,  4 users,  load average: 1.98, 2.10, 2.15

---

### Post by enoxx on 2011-03-19
Just figured it out!

I had a symbolic link inside the Movies folder pointing to the Movies folder and another symbolic link pointing to the TV folder so there was an infinite loop.

I guess that explains the long filename.

I hope this helps someone.

---

