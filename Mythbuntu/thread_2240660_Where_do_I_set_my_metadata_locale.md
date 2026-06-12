---
title: "Where do I set my metadata locale?"
date: 2014-08-21
forum: Mythbuntu
---

### Post by JamesNorris on 2014-08-21
About a fortnight ago, my Myth box died. The PSU fan stopped and there seems to have been a spike of some sort that fried a HDD. 

My videos are on another drive, so at least I don't have to spend week ripping all of my DVDs again, but I do seem to be facing the prospect of manually setting the metadata for my videos as it did take the mythtv database with it. 

I know that the update to 0.27 came with an updated tmdb script (or something like this) and this allows me to fetch results in en_gb, rather than American, so I can get all of my certificates in my regional format... I just can't find for the life of me where I set MythTV to do this!!

All help appreciated.

---

### Post by JamesNorris on 2014-08-21
Solved...

Seems that the metadata scripts are passed the internal mythtv locale, which despite my setting everything to british, was listed in Mythweb as US. Logging in to Mythweb and changing the current host's "country" setting to "GB" seems to have sorted it.

---

