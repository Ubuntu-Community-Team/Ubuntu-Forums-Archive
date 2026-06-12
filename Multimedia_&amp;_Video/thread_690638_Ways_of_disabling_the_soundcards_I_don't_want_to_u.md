---
title: "Ways of disabling the soundcards I don't want to use"
date: 2008-02-07
forum: Multimedia &amp; Video
---

### Post by Mr.Johnny on 2008-02-07
Hi!

I have 3 soundcards detected in Ubuntu, but I just want one to bee seen. 

Of what ways can I disable the other two?

(note: I don't think modprobe -r is an option, because there are too many dependencies)

---

### Post by Mr.Johnny on 2008-02-10
bump

---

### Post by Dave Otter on 2008-02-10
Applications-Accessories-Terminal

           Type- asoundconf set-- default-cardCARD

           replacing Card with card you wish to use

---

### Post by Mr.Johnny on 2008-02-11
I'll try it, thanks ;)

---

