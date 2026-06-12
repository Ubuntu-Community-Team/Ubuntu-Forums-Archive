---
title: "Apt dependency problem MythTV + Sound Juicer"
date: 2007-02-06
forum: Multimedia &amp; Video
---

### Post by tiainte on 2007-02-06
Hola,

Problem being that if i try to use mythtv-ripper to rip music, i get sound-juicer to pop-up on top of mythfrontend-window.

I tried to remove and re-configure sound-juicer but i'm stuck with dependency problem to ubuntu-desktop which would force me to remove everything if i try to remove sound-juicer.
Sound-juicer also doesnt seem to support option "dont do anything when cd inserted".

Is there an easy way to go around this dependency (less than hour of work) or is my only choice to re-install half of my system to get rid of one CD-ripper?

---

### Post by koshari on 2007-02-06
removing soundjuicer wont remove everything as you say it would, but it will remove the ubuntu desktop metapackage , this is fine and just says that one of the dependencys for the complete ubuntu desktop install is removed. (as you intend to do).

---

### Post by tiainte on 2007-02-06
Lovely,
it worked as you said.

When i tried to remove sound-juicer from aptitude, it said it will remove everything and i was a bit scared to try that.

running apt-get remove --purge sound-juicer worked just fine.

---

