---
title: "mp3fs very slow"
date: 2012-02-05
forum: Multimedia Software
---

### Post by brent on 2012-02-05
I have a collection of music in Flac and Mp3, and every month or so I reconvert my 3-or-higher rated music on my computer to Mp3 for use on my Android. Since this is fairly time-consuming and 99% redundant. Most songs will not have changed rating, but manually tracking those which did is even more work, so that why I just select all songs and convert to Mp3 at once.

Yesterday I thought I might solve this problem a bit more elegantly with mp3fs. I could rsync this to my phone every now and then, and rsync will propagate all updates, be it removed, added or updated music. Alas, mp3fs appears extremely slow. Transfer speeds are between 50 and 150 kbyte/s, which is clearly too slow to be of any use (speed is the same if I use rsync or just copy a folder in Nautilus). Manually converting the music gives me multiple Mbytes/s. I use mp3fs 0.30 on 10.04. Do any of you have a similar experience or perhaps a remedy?

---

### Post by brent on 2012-02-06
I just tried it on another system, which displays the same issue: very slow speeds. This system has Ubuntu 11.10, and mp3fs .30.

---

