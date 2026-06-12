---
title: "[BANSHEE 1.8] Duplicate imports"
date: 2010-10-18
forum: Multimedia Software
---

### Post by Cyb3rD0n Architectus on 2010-10-18
Hi,

I have serious trouble with the importing of new tracks in Banshee mediaplayer. I use Banshee since 1.2 and now we're at 1.8 and I still like it. But I've noticed that when importing a folder with mixed new and already imported tracks, Banshee imports duplicates of tracks with comma's "," and "&" in the artist-, track- or albumtitle. At first I couldn't find the culprit, but just now I noticed that every track that has a comma in the title or artist, is imported over and over again. There are tracks in my library with over a dozen duplicates, all tracks with a comma or "&" in them! :-k

Is there something wrong with Banshee with it's handling of titles with comma's, or might there be something wrong with the character encoding used by Banshee's SQLite database? And how can I solve this problem, because I have folders which I fill with new tracks from time to time, like, "Beatport" for all my Beatport downloads. These are huge folders with >1500 tracks each easily. [-o<

I also use Ex Falso for the first tag cleanup actions before I import them into Banshee. Thoughts on that? :?:

Thanks in advance!

---

### Post by NeoZeroG on 2010-12-31
Same problem bud, no solution anybody??? I swear banshee has the worst bugs and they never get fix. Been struggling for as long as I can remember. Guess its time for a change.

---

### Post by Cyb3rD0n Architectus on 2011-01-10
Banshee's website claims to have fixed the duplicates problem in the latest release. It was due to a character encoding problem. So let's wait for a stable release and check it out! :D

---

### Post by 1jackjack on 2011-01-17
I've also had issues with the Import Media tool, up to and including v1.9.1. I have never successfully done one big import of my entire music collection (80GB). When I try and do a big import (e.g. more than 15 albums), I always get missing tracks as well as duplicate files (e.g. Leaf_House.mp3 and Leaf_House(1).mp3) as well as duplicates in my library (2 tracks within Banshee pointing to the same file). My problem is not specific to any particular set of characters etc, as loads of the problematic files are just alphanumeric in filename. ALSO it works fine if I import each album separately.

The solution I have just found is to enable the "Library Watcher" extension, and simply copy your mp3s into your library folder. Seems to be working for large imports.

---

