---
title: "Why are so many 'extra packages' coming through?"
date: 2010-07-21
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Slug71 on 2010-07-21
Geez, almost every time i've installed packages that have been held back its dragged in new dependencies. Why is this? If they weren't required before then why is it necessary now? Space is always a concern on the CD but then new dependencies are always added!?

---

### Post by 23meg on 2010-07-21
It's hard to tell why unless you cite specific examples. It could be packaging changes (splits, deprecations etc.) that deprecate some packages and bring in new ones with different names, or it could be genuinely new libraries that are required for new features that land, and it could be both.

You can usually tell what's going on yourself by looking at the changelogs.

---

### Post by Slug71 on 2010-07-21
Most recent example: 

> The following extra packages will be installed:
  gnome-settings-daemon libgnomekbd-common libgnomekbd4 ubuntuone-client
  ubuntuone-client-gnome
Suggested packages:
  gnome-screensaver
[B]The following NEW packages will be installed:
  gnome-settings-daemon libgnomekbd-common libgnomekbd4[/B]
The following packages will be upgraded:
  python-ubuntuone-client ubuntuone-client ubuntuone-client-gnome
3 upgraded, 3 newly installed, 0 to remove and 4 not upgraded.
Need to get 598kB of archives.
After this operation, 5,292kB of additional disk space will be used.
Do you want to continue [Y/n]? 


Theres been so many over the past few weeks though.

I can understand if a new dependency is better/adds new features etc, but then it should replace or remove the weaker package.

---

### Post by 23meg on 2010-07-21
gnome-settings-daemon, libgnomekbd-common and libgnomekbd4 are all packages that are supposed to be installed by default; they aren't new dependencies. You may have removed them unintentionally before, possibly through a partial upgrade.

---

### Post by Slug71 on 2010-07-21
> **23meg said:**
> gnome-settings-daemon, libgnomekbd-common and libgnomekbd4 are all packages that are supposed to be installed by default; they aren't new dependencies. You may have removed them unintentionally before, possibly through a partial upgrade.

Thanks 23meg, thats probably what i did too.

---

