---
title: "MythTV parental rating in DB schema"
date: 2009-11-08
forum: Mythbuntu
---

### Post by menny on 2009-11-08
Hi,
I'm trying to understand the parental level use in MythTV so my metadata script ([http://code.google.com/p/fill-mythvideo-metadata/](http://code.google.com/p/fill-mythvideo-metadata/)) will also add the required meta data for this too.

Does anyone know how MythTV stores this information?
In the 'videometadata' table there are three columns:
showlevel (int)
rating (string)
childid (int)

My guess is that showlevel is mapped to the rating:
1 == G
2 == PG
3 == R
4 == NR

If so, why do I need the "rating" column? and what is "childid"?

Thanks.

---

