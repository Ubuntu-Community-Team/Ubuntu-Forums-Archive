---
title: "&quot;ati&quot; driver 3D support with HD2600"
date: 2009-10-31
forum: Multimedia Software
---

### Post by humphreybc on 2009-10-31
Just a quick question, it says [here]("https://help.ubuntu.com/community/RadeonDriver") that cards HD 3xxx and 4xxx have 2D only, and the rest have 3D, but there is no mention of the 2xxx series of cards.

Does the ati/radeon open source driver provide 3D support for an HD2600?

---

### Post by steefjeqv on 2009-10-31
I believe the 2xxx series are also based on R600, just like the 3xxx series. 
This means no 3D I'm afraid.

You can use the xorg on the edge ppa, which will give you 3D for Karmic.
This is experimentall stuff though. It may work, but it can also leave your X broken.

[https://launchpad.net/~xorg-edgers/+archive/ppa]("https://launchpad.net/~xorg-edgers/+archive/ppa")

Luckily, there's a safety net : ppa-purge. This will revert all ppa packages to the standard Ubuntu ones. 

So before applying this ppa, first install ppa-purge. If you get into trouble just do the following :

sudo ppa-purge xorg-edgers

Greetings,
Steven

---

### Post by r2rX on 2009-12-14
I know i'm posting a litle late right now, but don't the official ATi Catalyst's work with the 2xxx series and above, both 2D and 3D?

r2rX  :)

---

### Post by humphreybc on 2009-12-15
> **r2rX said:**
> I know i'm posting a litle late right now, but don't the official ATi Catalyst's work with the 2xxx series and above, both 2D and 3D?

r2rX  :)

Well, it's supposed to...

[https://bugs.launchpad.net/bugs/464525](https://bugs.launchpad.net/bugs/464525)

---

