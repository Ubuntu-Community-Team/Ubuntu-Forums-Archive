---
title: "/dev/dsp can't be mapped.."
date: 2008-03-12
forum: Multimedia &amp; Video
---

### Post by Nevermore on 2008-03-12
Hi everyone
until yesterday i was happily playing enemy territory with sound too..
then it suddenly disappeared!
/dev/dsp is there but can't be mapped
the modules are loaded
alsa works..
i dunno what else to do..

update:
problem solved
cdemu daemon was locking the /dev/snd and /dev/dsp
keep cdemu daemon not running and everything works

---

