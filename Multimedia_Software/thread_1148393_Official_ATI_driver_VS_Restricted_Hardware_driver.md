---
title: "Official ATI driver VS Restricted Hardware driver?"
date: 2009-05-04
forum: Multimedia Software
---

### Post by HavocXphere on 2009-05-04
The Restricted Driver window is crashing in various creative ways, so I'm thinking of downloading the driver straight off the ATI site:
[LIST=1]
[*]What is the difference between the two [Driver from ATI site VS ATI from Restricted driver page]
[*]The driver won't auto-update if I install it manually - right?
[*]How would I remove the driver from the ATI site again if I want to upgrade?
[/LIST]

Jaunty x64
Radeon 3850 [RV670PRO]

---

### Post by khmr33 on 2009-05-04
I know for sure the driver on the ATi website is more up to date.
(8.002 vs 8.000) I'm pretty sure the driver in the repository is from the beta and hasn't been replaced yet, why I don't know.

The biggest difference I've found so far is major updates to Catalyst Control Center. If you're connected to an HDTV and you get the underscan problem you'll want to go with a manual install. The updated CCC adds the slider control from the Windows CCC that controls the underscan without crashing X.

I suppose once you install manually, you'll have to maintain manually. If it works though, why wouldn't you?

I think the install instructions on [cchtml]("http://wiki.cchtml.com/index.php/Main_Page") show how to completely remove previous drivers before installing new ones.

---

### Post by HavocXphere on 2009-05-04
> **khmr33 said:**
> I know for sure the driver on the ATi website is more up to date.
(8.002 vs 8.000) I'm pretty sure the driver in the repository is from the beta and hasn't been replaced yet, why I don't know.

The biggest difference I've found so far is major updates to Catalyst Control Center. If you're connected to an HDTV and you get the underscan problem you'll want to go with a manual install. The updated CCC adds the slider control from the Windows CCC that controls the underscan without crashing X.

I suppose once you install manually, you'll have to maintain manually. If it works though, why wouldn't you?

I think the install instructions on [cchtml]("http://wiki.cchtml.com/index.php/Main_Page") show how to completely remove previous drivers before installing new ones.
Thanks. I'll follow the instructions on that site. If the one in the repos is still beta then I'm definitely going the manual route.

---

### Post by HavocXphere on 2009-05-04
Sweet...appears to be working.

Glxgears on:

Opensource drivers = 400fps
fglrx without Desktop effects = 7000 fps
fglrx with Desktop effects = 1500fps

I'm a bit surprised that I lost 5500fps by just enabling desktop effects, but its working so who cares.

And yes, I know...glxgears is not a valid benchmark etc.

Edit: Maximize & minimize is slow...but I saw a thread about that somewhere.

---

