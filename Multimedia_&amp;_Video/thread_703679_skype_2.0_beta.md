---
title: "skype 2.0 beta"
date: 2008-02-21
forum: Multimedia &amp; Video
---

### Post by root_at_home on 2008-02-21
Hi there

I installed Skype 2.0 beta but when I start it I get the following error..

skype: Symbol `_ZTI7QWidget' has different size in shared object, consider re-linking
Fatal: Cannot mix incompatible Qt libraries
Aborted (core dumped)


Plese can someone assist me?

Thanks

Root_at_home

---

### Post by willfleury on 2008-03-31
Hi, i had the same problem,
if you type 
ldd /usr/bin/skype

if you see the qt libraries in an inappropriate place (other than /usr/lib/...) then thats the problem.
I had nessus installed int /opt/nessus and the qt libraries were pointing to ql libs installed under that
directory. I had to remove nessus to fix the problem

---

### Post by root_at_home on 2008-04-03
Hi there

thanks for the reply, I also removed nessus and that solved the issue, 

Many thanks

Root_at _home

---

### Post by wieman01 on 2008-04-03
By the way, the final version of Skype is out. I guess you have noticed.

---

