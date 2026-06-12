---
title: "Koala broke my flash?"
date: 2009-11-22
forum: Multimedia Software
---

### Post by josephellengar on 2009-11-22
Is anybody else having this problem?  Flash won't load at all.  I'm on a 64 bit system and have tried everything that I could possibly think of to fix it.  I've reinstalled flash like 8 times.  I've downloaded every version from the adobe website, I've used scripts I found around online, it's just not working.  Any suggestions?   It's really annoying.  Gnome.

---

### Post by josephellengar on 2009-11-22
bump.  I know this is fast, but I'm kind of desperate to get this working (have some homework to do)

---

### Post by Mr Nemo on 2009-11-22
[http://labs.adobe.com/technologies/flashplayer10/64bit.html](http://labs.adobe.com/technologies/flashplayer10/64bit.html)

That should be the latest flash file from adobe. I've had all of these problems too. I fixed it by moving the file to /use/lib64/mozilla/plugins. If that doesnt work make sure the flash file is in the other lib/mozilla folders too.

---

### Post by josephellengar on 2009-11-22
> **Mr Nemo said:**
> [http://labs.adobe.com/technologies/flashplayer10/64bit.html](http://labs.adobe.com/technologies/flashplayer10/64bit.html)

That should be the latest flash file from adobe. I've had all of these problems too. I fixed it by moving the file to /use/lib64/mozilla/plugins. If that doesnt work make sure the flash file is in the other lib/mozilla folders too.

I finally figured it out.  I had already tried that, but I had to do a --force-architecture with the i386 version.

---

