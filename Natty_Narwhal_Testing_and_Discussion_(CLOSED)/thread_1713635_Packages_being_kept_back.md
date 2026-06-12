---
title: "Packages being kept back?"
date: 2011-03-24
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by hotshot247 on 2011-03-24
i upgraded from ubuntu 10.10 to 11.04 and i updated the system but why is their a bunch of stuff that is being kept back? it won't even let me submit a problem report for a program that crashes because it says that i need to upgrade those packages. does anybody know what i can do about that? thanks

---

### Post by fabricator4 on 2011-03-24
> **hotshot247 said:**
> i upgraded from ubuntu 10.10 to 11.04 and i updated the system but why is their a bunch of stuff that is being kept back? it won't even let me submit a problem report for a program that crashes because it says that i need to upgrade those packages. does anybody know what i can do about that? thanks

Umm, 11.04 is currently a development release, an "alpha" release.  It's not even due for beta release until the end of the month.  

What you did wasn't so much an upgrade, as a sidestep off the path into the dark forest where PCs have been known to disappear with no trace.  An alpha release can get broken at any time and it's not meant to be used in a production environment - at best you should make a separate boot partition for it if you want to try it out for the purpose of testing and to submit bug reports.

You picked maybe the worst possible moment to "upgrade" to 11.04.  It seems that the .7 kernel has problems and has either been withdrawn, or there is a problem which has suddenly made it impossible to update the kernel past the older .5 release.  I have a .7 release that is working fine, but a newer install will not update past .5 except for an offered "partial" update.  The partial update is a bad idea, as I found it seriously breaks the system requiring a re-install from scratch.

The reason some bits are held back is simple - no one has written them yet, or at least no one has managed to fix whatever was broken well enough to make it available for testing by those brave enough.

You really need to re-format your partition and re-install 10.10 Maverick if that was working OK for you.  Leave 11.04 until the proper release comes out, which will probably be at the end of April if it's ready by then.  Even then, you might want to leave it a month or two before replacing your operating system, as there's usually still a lot work that gets done immediately after the official release.

Unless you really want to get involved in testing the alpha and beta releases, stick to the releases that are available from the [official download page]("http://www.ubuntu.com/desktop/get-ubuntu/download").

Chris

---

### Post by howefield on 2011-03-24
Thread moved to "*Natty Narwhal Testing and Discussion*"

---

### Post by dino99 on 2011-03-24
> **hotshot247 said:**
> i upgraded from ubuntu 10.10 to 11.04 and i updated the system but why is their a bunch of stuff that is being kept back? it won't even let me submit a problem report for a program that crashes because it says that i need to upgrade those packages. does anybody know what i can do about that? thanks

look closely at your sources.list: uncheck everything but genuine natty repo. Then clean the sources:

sudo rm /var/cache/apt/archives/*

then update, upgrade

natty have the latest available packages

---

