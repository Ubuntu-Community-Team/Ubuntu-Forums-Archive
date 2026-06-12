---
title: "Need Flash, not gnash"
date: 2009-04-08
forum: Multimedia Software
---

### Post by Bradry on 2009-04-08
On a fresh install of 8.10 I used the Add/Remove Applications to
install gnash.  It does nothing but display a gigantic "play" button
over all Flash apps in Firefox.  I believe I must remove gnash before
I can try installing Flash, however, both Add/Remove and the Synaptic
Package Manager show gnash as *not* being installed.  SPM shows no
broken packages.

Using the Synaptic PM I reinstalled gnash, determined it did nothing,
then uninstalled it.  Firefox still shows the huge "play" button that
when clicked leaves a blank space.

What can I do?

Thanks for your attention.

---

### Post by pafufta503 on 2009-04-08
the huge play button might be the Firefox plugin FlashBlock.  if you have that, try disabling it if it annoys you.

i tried all the flash plugin alternatives, and alot of them worked decently except on a handful of video streaming sites.  the non-free flash plugin is the only one i've found that works, but it cannot run at the same time as Jack server, which makes means i have to change sound device settings constantly depending on what i want to do.

---

### Post by gandaran on 2009-04-08
the huge play button is swfdec flash, remove it and gnash completely and install only the flashplugin-nonfree (adobe flash)

---

### Post by Bradry on 2009-04-08
> **gandaran said:**
> the huge play button is swfdec flash, remove it and gnash completely and install only the flashplugin-nonfree (adobe flash)

That was it!  All is well.  Now, it's off to find those Flash cookies and kill 'em.

Thanks.

Brad

---

