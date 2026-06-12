---
title: "Install totem-gstreamer but NOT totem-mozilla"
date: 2008-03-31
forum: Multimedia &amp; Video
---

### Post by sammydee on 2008-03-31
Title says it all really.

I want to replace totem-xine with totem-gstreamer so I can use the libvisual plugins, but apt-get insists on installing totem-mozilla along with it, I do not want totem-mozilla, I much prefer the mplayer firefox plugin.

Any ideas?

Sam

---

### Post by twright on 2008-03-31
let it install totem-mozilla then reinstall the mplayer plugin, it will overwrite totem-mozilla

---

### Post by WearZeeP on 2008-03-31
apt-get remove totem-mozilla?

---

### Post by wolfen69 on 2008-03-31
> **twright said:**
> let it install totem-mozilla then reinstall the mplayer plugin, it will overwrite totem-mozilla

no it wont. totem will conflict with mozilla-mplayer. i get rid of all instances of totem and never have a problem playing anything.

---

### Post by sammydee on 2008-03-31
is there a way of overriding dependencies with apt-get?

sam

---

### Post by wolfen69 on 2008-03-31
they are called dependencies for a reason. it means an app needs certain packages to run correctly. you can get individual packages here. [http://packages.ubuntu.com/](http://packages.ubuntu.com/) good luck.

---

### Post by sammydee on 2008-03-31
Ok, installed totem-gstreamer, then purged totem-mozilla and reinstalled mozilla-mplayer. I think that's fixed it.

Sam

---

### Post by twright on 2008-03-31
if you install on and then the other both will be installed but the one that was installed last will be set as the default in firefox (firefox's plugin framework doesn't always behave the way that apt assumes it does)> **wolfen69 said:**
> no it wont. totem will conflict with mozilla-mplayer. i get rid of all instances of totem and never have a problem playing anything.

---

