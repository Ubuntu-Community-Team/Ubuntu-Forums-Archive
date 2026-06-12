---
title: "Kernel error after installing ndiswrapper"
date: 2010-08-18
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by 98cwitr on 2010-08-18
Installed from software center. Every time it tries to connect to a wireless node I get a crash report (yes, I sent it in). Anyone else having this problem?

---

### Post by cariboo on 2010-08-18
See [this]("http://ubuntuforums.org/showthread.php?t=1546409&highlight=ndiswrapper") thread.

---

### Post by jamaisvu on 2010-08-27
> **cariboo907 said:**
> See [this]("http://ubuntuforums.org/showthread.php?t=1546409&highlight=ndiswrapper") thread.

That thread is just a load of me-toos: there isn't even a workaround posted in it, probably because the only one that works is to pray you've remembered to install usb-modeswitch (why isn't this a default package?) and plug in a dongle. Seeing as Karmic broke b43-fwcutter, the only alternative to ndiswrapper for certain wireless chipsets, and AFAIK it is still broken, Maverick should not ship with a kernel that breaks ndiswrapper as well. The kernel seems to have been getting buggier and buggier when it comes to networking: it hasn't worked as expected since 2.6.29 and there is no sign of anyone either fixing the regressions that have worked their way in since then or explaining what they did to that morass of code so that someone else can have a go at patching it. Are we really going to give LTS to a broken kernel version? It's almost worth piping [this message]("http://lkml.org/lkml/2009/7/28/373") to espeak and turning the volume up to 11...

---

### Post by cariboo on 2010-08-27
If you read the whole thread you would have seen, that we are waiting for an ndiswrapper update from the the author.

---

