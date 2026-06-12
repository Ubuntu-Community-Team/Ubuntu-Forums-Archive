---
title: "[timidity] no sound if started at boot"
date: 2009-07-05
forum: Multimedia Software
---

### Post by allaf on 2009-07-05
Hi,

I have a weird situation here.

Timidity is started at boot from init.d but tuxguitar can't use it.
But if I kill it and start it again **as a regular user** then it works fine.
It's really lame to have to start it manually evreytime.
Any idea?

---

### Post by ajgreeny on 2009-07-05
Just add it as a startup program instead of in init.d.  It will then start as user, not root.

---

