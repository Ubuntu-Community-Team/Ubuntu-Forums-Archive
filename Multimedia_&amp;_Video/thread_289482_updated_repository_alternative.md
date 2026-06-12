---
title: "updated repository? alternative?"
date: 2006-10-31
forum: Multimedia &amp; Video
---

### Post by namgman on 2006-10-31
Hi

I've noticed that the dapper repository still contains Ardour .99.2.  I believe that version is fairly out of date.  Is this an indication of how current the repository is in general?

If so, is there a recommended repository where the latest stable (or not so stable, Ardour 2 beta for example) packages reside?

Thanks.

---

### Post by KoRnholio on 2006-10-31
Yes, Edgy's repositories.

Dapper is a LTS release, so it only gets security fixes and other updates considered critical.

---

### Post by dolson on 2006-10-31
The version of ardour that I see in Edgy is 0.99.2-2build1. 0.99.3 is the most recent stable build.

However, Ubuntu Studio does not maintain repositories for software. We are working with Ubuntu's repositories only - most of which are pulled directly out of Debian to begin with. If you want newer software, package it and submit it to Ubuntu's REVU system, or better - to Debian.

Alternately, you can compile from source, or use updated deb packages from Debian (I recommend rebuilding them yourself anyhow, since it's not hard and will almost certainly work).

---

