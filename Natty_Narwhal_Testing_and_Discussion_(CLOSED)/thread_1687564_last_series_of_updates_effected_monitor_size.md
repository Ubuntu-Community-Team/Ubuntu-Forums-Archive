---
title: "last series of updates effected monitor size"
date: 2011-02-14
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by rburkartjo on 2011-02-14
yea now i cant increase resolution stuck in 800 x 600 use to be able to get my 1300 x 900

---

### Post by tjeremiah on 2011-02-14
do you know what update caused this? If not,did the recent updates fix the problem?

---

### Post by seeker5528 on 2011-02-14
On my system the wallpaper doesn't load either.

At least in my case I'm assuming it was because I am pulling from the gnome3-team PPA and the gnome 3 stuff was updated in the main repositories, so the stuff in the gnome3-team PPA needs to be rebuilt against the newer gnome3 stuff in the official repositories.

If you are not pulling from the gnome3-team PPA, and having this problem, there may be a more general issue with gnome-settings-daemon versus gconf/gsettings.

Typically I would wait a day or two before reporting a bug against this type of thing, unless it is getting late in the development cycle, because it seems likely that it's a case where things need to be updated/recompiled for newer versions of libraries and once that is complete the issue goes away.

Later, Seeker

---

### Post by rburkartjo on 2011-02-14
ya see this happened with alpha1 just going to wait and see if it gets fixed in the next couple of day with updates

---

### Post by Harry33 on 2011-02-14
> **seeker5528 said:**
> On my system the wallpaper doesn't load either.

At least in my case I'm assuming it was because I am pulling from the gnome3-team PPA and the gnome 3 stuff was updated in the main repositories, so the stuff in the gnome3-team PPA needs to be rebuilt against the newer gnome3 stuff in the official repositories.

If you are not pulling from the gnome3-team PPA, and having this problem, there may be a more general issue with gnome-settings-daemon versus gconf/gsettings.

Typically I would wait a day or two before reporting a bug against this type of thing, unless it is getting late in the development cycle, because it seems likely that it's a case where things need to be updated/recompiled for newer versions of libraries and once that is complete the issue goes away.

Later, Seeker

What was recently upgraded in the Natty repos, was GTK+3.0.
It is now the release version.
And it brings about an ABI bump too.

Generally all GTK+3.0 applications ought to be rebuild against it now.
And yes, in the Gnome3 Team PPA the gnome3 development packages do depend on GTk+3.0.

---

