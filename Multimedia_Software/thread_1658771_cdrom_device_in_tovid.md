---
title: "cdrom device in tovid ?"
date: 2011-01-03
forum: Multimedia Software
---

### Post by rvchari on 2011-01-03
hi guys,
i came across tovid and have installed it. i have some video clips that i transfered from my handycam to my comp using kino. i also converted the raw dv files to avi using the same software kino.

now i wish to give menu titles and burn on a cd so it can be played as a normal vcd. i m trying to use tovid and the device says default /dev/dvdrw. how do i know whats mine ? any particular terminal command i issue so i know that ?

i am totally new to multimedia in ubuntu and i wish to create good vcds...

---

### Post by grepster on 2011-01-11
You should have a symlink in /dev called "cdrw" or "cdrom".
```
ls -l /dev/cd*
```
from a terminal should show it to you.

grepster

---

