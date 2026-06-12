---
title: "Rhythmbox local cover search not working"
date: 2009-01-18
forum: Multimedia Software
---

### Post by RobertK81 on 2009-01-18
Hi,

I just added a few albums to rhythmbox which can't be found on Amazon, so I tried to find a way it can recognize locally stored artwork.

In the folder for the artdisplay plugin, there is a file called LocalCoverArtSearch.py, which contains the line
IMAGE_NAMES = ["cover", "album", "albumart", ".folder", "folder"]

Also, I saw some comments on the net saying that files like "cover.jpg" in the same folder as the album would be recognized.

I have a cover jpg file in that album folder, tried to rename it to every variant from that .py file, RB still doesn't recognize any of it.

Using RB 0.11.5 with ubuntu 8.04.1

Regards,

Robert

---

