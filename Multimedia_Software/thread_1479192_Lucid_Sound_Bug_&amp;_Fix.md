---
title: "Lucid Sound Bug &amp; Fix"
date: 2010-05-10
forum: Multimedia Software
---

### Post by Bobhuber on 2010-05-10
This was the original post .....

While trying to play an embedded MP3 sound file in Firefox the volume is  automatically decreased.This happens when the page loads or is  refreshed. I can open the system sound preferences, go to applications  and slide the volume control up while the sound is playing and its fine.

A known bug has been posted with this workaround.From a terminal type the following (Do not use SUDO or GKSUDO to open the terminal).

gconftool --type int --set /apps/totem/volume 100

---

