---
title: "Quod Libet not starting."
date: 2009-01-24
forum: Multimedia Software
---

### Post by RubenK on 2009-01-24
Problem is simple. Here's what I do:
> ruben@ruben-desktop:~$ quodlibet
Quod Libet is already running.
ruben@ruben-desktop:~$ ps aux | grep quod
ruben     7196  0.0  0.0   1844   488 ?        S    13:48   0:00 /bin/sh -c quodlibet --status
ruben     7197  0.0  0.1   5268  3692 ?        S    13:48   0:00 /usr/bin/python /usr/bin/quodlibet --status
ruben     8493  0.0  0.0   2016   564 pts/0    R+   14:32   0:00 grep quod
ruben@ruben-desktop:~$ kill -9 7196 7197
ruben@ruben-desktop:~$ quodlibet
Quod Libet is already running.
ruben@ruben-desktop:~$ 
I've reinstalled Quod Libet (sudo apt-get purge quodlibet > reboot > sudo apt-get install quodlibet). Result? See the above... :(

Who can help me?

---

### Post by Stochastic on 2009-01-24
Moved to Multimedia & Video

---

### Post by RubenK on 2009-01-24
I posted it in Multimedia & Video... Anyhow, any has the solution?

---

### Post by RubenK on 2009-01-24
Reinstalling didn't work so I tried to locate all the files containing quodlibet, mutagen en exfalso: sudo find / -iname '*quodlibet*' -exec rm {} \;

Replacing quodlibet with mutagen en exfalso when needed. After this installing exfalso and quodlibet with synaptic worked fine and everything works again.

---

