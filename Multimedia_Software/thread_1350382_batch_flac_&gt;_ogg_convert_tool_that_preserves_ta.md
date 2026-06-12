---
title: "batch flac &gt; ogg convert tool that preserves tags?"
date: 2009-12-09
forum: Multimedia Software
---

### Post by size_XXM on 2009-12-09
Hi. I'm looking for a flac equivalent of [mp32ogg](http://packages.ubuntu.com/karmic/mp32ogg).
A flac2ogg script [apparently exists](http://members.fortunecity.com/stateq/flac2ogg.html), but
[list][*]it's not in the repo
[*]it does a two-step, file-based conversion (flac>wav>vorbis) instead of using pipes, gobbling up disk space for large tracks
[*]the TODO indicates it's unfinished - it doesn't put the resulting file in the same directory as the original one, somewhat failing the whole point of **batch** conversion
[*]it appears unmaintained, making the above point unlikely to go away[/list]

Are there any other tools?

---

### Post by David Gerard on 2010-02-18
> **size_XXM said:**
> Hi. I'm looking for a flac equivalent of [mp32ogg](http://packages.ubuntu.com/karmic/mp32ogg).
A flac2ogg script [apparently exists](http://members.fortunecity.com/stateq/flac2ogg.html), but
[list][*]it's not in the repo
[*]it does a two-step, file-based conversion (flac>wav>vorbis) instead of using pipes, gobbling up disk space for large tracks
[*]the TODO indicates it's unfinished - it doesn't put the resulting file in the same directory as the original one, somewhat failing the whole point of **batch** conversion
[*]it appears unmaintained, making the above point unlikely to go away[/list]

Are there any other tools?

acxi was just released:

[http://techpatterns.com/forums/about1491.html]("http://techpatterns.com/forums/about1491.html")

It's an updated version of flac2ogg.pl .

It appears to preserve tags too, in a quick test I did just now. If not, it should be easy enough to add tag preservation and submit a patch back!

I haven't tried writing oggs to the directory the flacs are in - my use is taking CDs I've bought and ripped to flac (for storage) and ripping them to ogg (for my music player, a cheap Chinese S1-based thing that plays Oggs even though it's not mentioned anywhere). Try it and see ;-)

---

