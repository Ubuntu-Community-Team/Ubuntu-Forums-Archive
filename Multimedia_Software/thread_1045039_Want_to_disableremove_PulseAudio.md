---
title: "Want to disable/remove PulseAudio"
date: 2009-01-20
forum: Multimedia Software
---

### Post by Macintosh SE on 2009-01-20
I was using Ubuntu 7.04, but was basically forced to upgrade to 8.04 when the 7.04 repositories were taken offline. Everything is working now, except I don't like PulseAudio (sounds actually sound slightly different). I want to revert back to ALSA but retain the benefits of playing multiple sounds at once (esound?). When I go to install esound, the package manager wants me to remove ubuntu-desktop. This seems like a very bad idea to me. Is there any way around this, or am I stuck with PulseAudio?

---

### Post by wolfen69 on 2009-01-20
i did it and my sound works great now. don't worry about removing ubuntu-desktop, it won't remove it. that is just the meta package for ubuntu desktop. go for it.

---

### Post by stderr on 2009-01-20
Ubuntu-desktop is what they call a metapackage. 

As I understand it, it contains nothing really itself, but when installed will install a collection of other packages that are deemed part of the ubuntu desktop experience. When removed, all it means is that should those at Ubuntu decide to add extra/different applications into the ubuntu desktop environment in the future, they won't be installed automatically.

I believe it's meant to be the case that if the user wants to customise their experience by removing GNOME apps from their desktop, then they probably don't want other stuff being installed without their asking for them. Therefore, ubuntu-desktop *depends* on loads of GNOME applications. Should one of them be removed, the dependencies are no longer satisfied for ubuntu-desktop, and it's removed too. 

Hope that's right...

---

