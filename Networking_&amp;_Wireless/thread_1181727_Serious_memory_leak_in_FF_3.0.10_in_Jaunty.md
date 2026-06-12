---
title: "Serious memory leak in FF 3.0.10 in Jaunty"
date: 2009-06-08
forum: Networking &amp; Wireless
---

### Post by Cubytus on 2009-06-08
Hi to all, 

on a P4 1,6GHz/512MB RAM/525MB swap, Firefox, open on the Yahoo Mail page, takes very little time to fill in the available memory, **including swap**; htop reports that, on the aproximate 1GB virtual memory available, FF takes 800MB, just to keep Yahoo Mail open. In fact, it doesn't seem linked to Yahoo itself, since having FF opened on the default start page (Custom Ubuntu/G**gle page) still sows the default.


As a consequence, it is to demanding on the hard drive that its activity light doesn't blink, but remains solid, and the computer is slowed to the point it appears essentially frozen. I don't have another machine on hand to compare, but I remember using FF 3 on Interpid Ibex and keeping it open for days with about 20 tabs that FF was heavy on memory, as it has always been, but still usable. 

This Firefox here has only 3 extensions; the one from Canonical, Adblock Plus and Flashblock.

Is there a solution to this bad behaviour?

---

### Post by whoop on 2009-06-08
I haven't got yahoo mail so I can't check... I think the way to go is to get someone else to confirm this. If the person can confirm it a bugreport should be posted. If it can't be confirmed you need to test it further, to see where it differs from working installs...

---

### Post by superprash2003 on 2009-06-08
i face similar problems..

---

### Post by Cubytus on 2009-06-09
Yu don't have Yahoo Mail, or you'Re experiencing similar problems when FF 3.0.10 is idle on Jaunty?

---

### Post by superprash2003 on 2009-06-09
memory leak when accessing a lot of webpages..

---

### Post by Cubytus on 2009-06-09
So it's not the same problem as I have. I do have memory leak after only light browsing, then long idle.

---

