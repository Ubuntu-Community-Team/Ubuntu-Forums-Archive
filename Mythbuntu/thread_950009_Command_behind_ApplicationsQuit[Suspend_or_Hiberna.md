---
title: "Command behind Applications/Quit/[Suspend or Hibernate]?"
date: 2008-10-16
forum: Mythbuntu
---

### Post by jboehm on 2008-10-16
Hi,

I'm wondering what the actual commands behind the menu items Applications/Quit/ Suspend or Hibernate are?  I plan on setting up auto power down and auto power up.  I know at the core they they do an s2disk but there are a lot of helper scripting around that command that makes other processes happy and correctly survive a power down / power up cycle.

Thanks,
Jon

---

### Post by laga on 2008-10-17
I *think* that's done using HAL. Look at /usr/share/mythtv/myth-hibernate.sh for an example.

---

### Post by jboehm on 2008-10-17
Thanks for the myth-hibernate.sh suggestion.  Using that as an example I created myth-suspend.sh.  See attached.  So far it works great.

Thanks,
Jon

---

