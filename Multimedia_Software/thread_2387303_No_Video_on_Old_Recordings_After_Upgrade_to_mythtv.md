---
title: "No Video on Old Recordings After Upgrade to mythtv .28"
date: 2018-03-17
forum: Multimedia Software
---

### Post by bilkay on 2018-03-17
Ubuntu 16.04
 mythtv .28

In a fresh install of ubuntu 16.04 and mythtv .28, the frontend works  well with new recordings, BUT after migrating database with old  recording data from mythtv .27's schema, the old recordings (.mpg) only  play audio and cause the frontend window to disappear. I got the same  result doing an upgrade from 14.04.

---

### Post by bilkay on 2018-03-18
The problem seems to stem from a disparity between the Current Video Playback Profile and the Paint Engine in the frontend Setup.

---

