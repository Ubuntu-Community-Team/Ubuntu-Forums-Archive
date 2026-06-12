---
title: "Run MediaTomb as service"
date: 2007-08-06
forum: Multimedia &amp; Video
---

### Post by kaffelars on 2007-08-06
I use MediaTomb to show pictures and play music on my PS3, and it works great.
However, I can't figure out how to run it as a service (i run Feisty), so I have to log in to get it running.

Has anyone set it up as a service and would like to share how?:)

---

### Post by broth420 on 2007-08-08
sudo nano /etc/default/mediatomb
change the NO_START option from "yes" to ""

I posted this and then tried it.  In my situation, it didn't work, but these are the instructions from the website.  thus the edit

---

### Post by kaffelars on 2007-08-09
It doesn't seem to start, although running [Bsudo /etc/init.d/mediatomb start][/B] does not give any error messages :(
I'll poke around with it when I get home from work to try to get it working.. :)

---

### Post by insertnewsn on 2007-12-30
Any news? Did you manage to get it working?

---

