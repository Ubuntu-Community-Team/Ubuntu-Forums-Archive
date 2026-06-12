---
title: "Elisa and hebrew subtitles"
date: 2008-12-27
forum: Multimedia Software
---

### Post by Greycloack on 2008-12-27
Hi,

I installed elisa from [http://ppa.launchpad.net/elisa-developers/ubuntu](http://ppa.launchpad.net/elisa-developers/ubuntu)
Everything is running great except the subtitles in the movies.

I have some movies that have hebrew subtitle files. When I play them in Totem, they work great with the subtitles. When I play them in Elisa, the subtitles come out as gibberish.

Does anyone know how to solve this?

Thank you,
Grey

---

### Post by gfnord on 2009-02-04
I don't know about Totem, but as far as I tested Elisa 0.5.x, it seems that it shows non-English characters properly only with subtitles encoded in UTF-8. So try recoding your subtitles in UTF-8. If subtitles in UTF-8 do not work at all, try using UTF-8 without BOM.

---

