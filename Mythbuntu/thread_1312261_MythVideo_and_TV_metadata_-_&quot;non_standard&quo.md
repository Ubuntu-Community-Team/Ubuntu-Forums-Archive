---
title: "MythVideo and TV metadata - &quot;non standard&quot; filename formats"
date: 2009-11-03
forum: Mythbuntu
---

### Post by stdPikachu on 2009-11-03
Been getting to grips with the new Myth release and mostly hunky dory... but I'm totally lost as to how the new metadata grabber for TV shows is supposed to work.

From reading the mythtv website, I get the impression that the video scanner should have added metadata entries for all my TV shows (all under /storage/tv) based on filename... further reading suggests this is because I'm using a filename format that's not been written into the code; namely:
ShowName 01-01 EpisodeName
ShowName 01 - EpisodeName (for TV shows with no seasons, where the number corresponds to the episode)

I've got over 3000 TV eps in there so adding the metadata manually isn't really an option. I've added a regex to my ttvdb.conf to allow for my 01-01 format (I think):
```
^(.+?)[ \._\-]([0-9]+)-([0-9]+)[^\\/]*$
```
but still can't get the scanner to work... I always get "match not found" even after adding the metadata to the DB manually.

Can anyone offer any pointers?

---

