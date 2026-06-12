---
title: "Mediatomb not Indexing id3 of mp3's"
date: 2008-04-12
forum: Multimedia &amp; Video
---

### Post by StevenHarper on 2008-04-12
I have 2 Hardy installs, one on my laptop on on my desktop:

there both 32bit versions.

On my laptop the mp3's I add to mediatomb index perfectly (id3)

On my desktop everything gets indexed as unknown.

I have read lots of stuff, but my laptop is almost a vanilla Hardy install, I have tried installing all sorts of id3 library's on my desktop, but I didnt have to do anything on the laptop.

Any Ideas?

Steve

---

### Post by StevenHarper on 2008-04-12
With help from the guys who develop mediatomb on sourceforge I have discovered why My files could be found my mediatomb but not indexed - they all showed up as UNKNOWN

The problem was that all my files had Group read rights but NOT the ALL read rights.

Mediatomb could see the files, but the ID3 tagger didnt have group read rights

it was a simple fix of a recursive chmod to the files

```
cd /mybigstashofmp3s/
chmod -R a+r *
```

thats it!

Steve

---

