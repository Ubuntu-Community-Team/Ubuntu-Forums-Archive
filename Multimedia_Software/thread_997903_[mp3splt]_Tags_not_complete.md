---
title: "[mp3splt] Tags not complete"
date: 2008-11-30
forum: Multimedia Software
---

### Post by Choxo on 2008-11-30
Hi all,

I'm using mp3splt for splitting ASOT episodes to tracks.
Unfortunately, the tags are not completly written to the file:

I use this command in console:

```

mp3splt -c avbasot380.cue avbasot380.mp3 -o "@n.@p_-_@t"


```

In Exaile, I see for example this:
[img]http://members.lycos.nl/choxo/content/screenie.png[/img]


In nautilus, when I right-click and check the properties, I see the same tags.

I would not rather have to use easytag to re-render the tags.

Is there an option I'm missing? Also, if there 're non standard characters, for example the "ÿ", mp3splt will fail.

---

### Post by Choxo on 2008-12-05
nobody?

---

### Post by PlaneTeeR on 2009-05-10
Hey,

With the newer version of mp3splt you can use the -2 option to use ID3v2 tags. This should do the trick.

---

