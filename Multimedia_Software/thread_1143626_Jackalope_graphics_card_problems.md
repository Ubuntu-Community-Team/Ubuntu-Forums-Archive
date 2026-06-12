---
title: "Jackalope graphics card problems"
date: 2009-04-30
forum: Multimedia Software
---

### Post by bravo sierra echo on 2009-04-30
Since upgrading to Xubuntu Jackalope, I'm having some video problems.  I'm starting to wonder if it's not recognising my graphics card properly.

According to lspci I have the following:

00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)

Is there a way I can download drivers for this card?

Many thanks!

---

### Post by VMC on 2009-04-30
> **bravo sierra echo said:**
> Since upgrading to Xubuntu Jackalope, I'm having some video problems.  I'm starting to wonder if it's not recognising my graphics card properly.

According to lspci I have the following:

00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)

Is there a way I can download drivers for this card?

Many thanks!I should start a topic with that card. The ONLY fix that works for that Intel card is the [[COLOR="Red"]**ROLLBACK**[/COLOR]]("https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4") method.

---

### Post by bravo sierra echo on 2009-04-30
Rats :(

Ah well, thanks!  I will do so (or replace the computer, which I've been thinking about doing for a while anyway...)

---

### Post by bravo sierra echo on 2009-05-05
Just for information, that worked perfectly - thanks.  I can now play video, DVDs, and embedded video like YouTube as before (hope this helps anyone searching for that graphics card in the future!)

---

