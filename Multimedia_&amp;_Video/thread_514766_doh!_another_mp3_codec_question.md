---
title: "doh! another mp3 codec question"
date: 2007-08-01
forum: Multimedia &amp; Video
---

### Post by blingboi on 2007-08-01
ill make this short, i just want to install whatever codec to play mp3s with amarok
im a minimalist, but a newbie at ubuntu, please point me in the right direction

ive tried to search, but could not come up with a definite answer, thanks

---

### Post by redhat24 on 2007-08-01
Check aptitude (the gui-version), there is a package for it (search: "mp3")

---

### Post by Steve1961 on 2007-08-01
> **blingboi said:**
> ill make this short, i just want to install whatever codec to play mp3s with amarok
im a minimalist, but a newbie at ubuntu, please point me in the right direction

ive tried to search, but could not come up with a definite answer, thanks

Make sure you add the medibuntu repo to your apt sources list and ensure amarok is using the xine engine.  Then install the package w32codecs.

---

### Post by blingboi on 2007-08-01
so, w32 is what i want?

---

### Post by Steve1961 on 2007-08-01
yes, you need the w32codecs

---

### Post by blingboi on 2007-08-01
> **Steve1961 said:**
> yes, you need the w32codecs

one last question if you may... whats so special about medibuntu repo?

---

### Post by Steve1961 on 2007-08-01
It contains non-free packages that Ubuntu doesn't include in its standard repos

---

### Post by Arthur Archnix on 2007-08-08
Check out the [Ubuntu Feisty Guide]("http://ubuntuguide.org/wiki/Ubuntu:Feisty").

Search for mediabuntu, w32codecs, and codecs.

I see your a minimalist. Ubuntu is a difficult distro to achieve that. You might start by removing the ubuntu-desktop, fonts for languages you don't use, and other programs you don't want through synaptic. Just don't remove ubuntu-standard, or core, or anything that says it will take out either of those two things. Otherwise, get the hammer out and start breaking things!

---

