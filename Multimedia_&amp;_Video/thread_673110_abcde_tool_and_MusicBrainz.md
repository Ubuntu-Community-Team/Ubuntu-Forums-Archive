---
title: "abcde tool and MusicBrainz"
date: 2008-01-20
forum: Multimedia &amp; Video
---

### Post by PaulVDV on 2008-01-20
Hi,

abcde is configured to use freedb by default.

Does anyone know how to modify the abcde configuration file to connect to MusicBrainz instead ?

Thanks.

---

### Post by nick_h on 2008-01-20
According to the manual page you need to set:
```
CDDBMETHOD=musicbrainz
```
Then track details are retrieved using a script called *musicbrainz-get-tracks* which depends on python.

I haven't tried it myself.

---

### Post by yabbadabbadont on 2008-01-20
Musicbrainz support is not fully functional yet.  (according to the changelog)

---

