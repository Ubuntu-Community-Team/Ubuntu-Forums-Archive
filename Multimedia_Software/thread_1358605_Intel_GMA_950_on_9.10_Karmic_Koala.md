---
title: "Intel GMA 950 on 9.10 Karmic Koala"
date: 2009-12-18
forum: Multimedia Software
---

### Post by Braveheart1980 on 2009-12-18
I just installed 9.10 on an intel mobo ( D945GCLF2D ) that has the Intel GMA 950 on board graphic card

I need to get higher resolution than the default 800x600 , and I think that what I have to do is to install the intel drivers since in glxinfo I see that I am using the mesa ones

I also found out that there is no persistent xorg.conf anymore to edit

So how can I enable the intel GMA 950 drivers???

---

### Post by Braveheart1980 on 2009-12-19
Anyone?

---

### Post by cigtoxdoc on 2009-12-19
I had similar problem earlier this week when i changed graphics card.  Go to System/ Hardware drivers and Ubuntu should start looking for new drivers.  I had to log on as ROOT in order to get permissions to activate new drivers.

John

---

### Post by Braveheart1980 on 2009-12-20
> **cigtoxdoc said:**
> I had similar problem earlier this week when i changed graphics card.  Go to System/ Hardware drivers and Ubuntu should start looking for new drivers.  I had to log on as ROOT in order to get permissions to activate new drivers.

John


Just did that (went to System --> Administration --> Hardware drivers) , but it said that no proprietary drivers found

Any more ideas?

---

### Post by sandy8925 on 2009-12-20
It should be working automatically since Intel drivers are open source. It always works out of the box for my g.card which is an Intel 910/915 GML or something like that.

---

