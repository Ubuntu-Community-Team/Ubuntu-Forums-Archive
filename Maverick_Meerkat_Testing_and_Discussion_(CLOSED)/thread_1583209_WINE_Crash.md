---
title: "WINE Crash"
date: 2010-09-27
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by themattbeballin on 2010-09-27
I tried Googling this issue, got directed to the forums, but the post was gone... so I had no help with this...

If you all an point me into a right direction, that's be nice..

I tried opening World of Warcraft, and get to logging in... and it pops up a window that says "Wine program crash"

then "Internal errors - invalid parameters received" 

i'm posting this in the Maverick testing thread, because it didn't do it in Lucid, and I'm running the latest of the Maverick testing.. if this deserves to go to the wine forum, please move it.

Anyway, please try and  point me into the right direction.

---

### Post by GeoPirate on 2010-09-27
the kernel used in maverick is 2.6.35.3 wich is a little older than the current stable, there's a kernel issue that affects wine when you try to run WoW or SC2.  Upgrading to a newer kernel should resolve the problem for you.

---

### Post by cariboo on 2010-09-27
The current kernel is:

> Linux alexis-maverick 2.6.35-22-generic #33-Ubuntu SMP Sun Sep 19 20:32:27 UTC 2010 x86_64 GNU/Linux

If you're using 2.6.35.3 you need to update.

---

### Post by dino99 on 2010-09-28
> **themattbeballin said:**
> I tried Googling this issue, got directed to the forums, but the post was gone... so I had no help with this...

If you all an point me into a right direction, that's be nice..

I tried opening World of Warcraft, and get to logging in... and it pops up a window that says "Wine program crash"

then "Internal errors - invalid parameters received" 

i'm posting this in the Maverick testing thread, because it didn't do it in Lucid, and I'm running the latest of the Maverick testing.. if this deserves to go to the wine forum, please move it.

Anyway, please try and  point me into the right direction.

[COLOR="Blue"]you should post into wine subforum for all related wine issues

[http://appdb.winehq.org/appview.php?iAppId=1922](http://appdb.winehq.org/appview.php?iAppId=1922)[/COLOR]

---

### Post by themattbeballin on 2010-09-28
> **dino99 said:**
> [COLOR=Blue]you should post into wine subforum for all related wine issues

[http://appdb.winehq.org/appview.php?iAppId=1922](http://appdb.winehq.org/appview.php?iAppId=1922)[/COLOR]

I don't see a reason why I should, now that I think about it... because  it's a issue with Maverick Meerkat's kernel and not Lucid, Karmic, or  any other version of Ubuntu.

> **cariboo907 said:**
> The current kernel is:



If you're using 2.6.35.3 you need to update.

I tried running WoW off of both kernels, and it didn't make a difference. Still gave me the same error.

---

### Post by GeoPirate on 2010-09-29
both what kernels exactly? I went to 2.6.36 to resolve this issue on my system.

---

### Post by themattbeballin on 2010-09-29
> **geopirate said:**
> both what kernels exactly? I went to 2.6.36 to resolve this issue on my system.



2.6.35
2.6.36

---

