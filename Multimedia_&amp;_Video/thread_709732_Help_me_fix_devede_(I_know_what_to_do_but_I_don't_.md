---
title: "Help me fix devede (I know what to do but I don't know how to do it!)"
date: 2008-02-27
forum: Multimedia &amp; Video
---

### Post by s3a on 2008-02-27
Go to: "http://www.rastersoft.com/programas/devede.html"

"Note for Ubuntu Gutsy users: by default (as November 21, 2007) Gutsy comes with Mplayer/Mencoder buggy version 1.0RC1 (like Feisty); but fortunately there's the version 1.0rc2 avaiblable in the backports repository, which fixes the sound bug. To install it, just go to System->Admin->Software repositories and activate the Backports source."

I use Ubuntu 7.10 32 bits and simply want to have a version of devede (and supposedly mencoder/mplayer) that works without sound problems (=no sound whatsoever) on the final burnt disc!!!

---

### Post by CarpKing on 2008-02-27
Go to System -> Administration -> Software Sources.  Then go to the "Updates" tab and check "Unsupported updates (gutsy-backports)."  Next go open a terminal and type "sudo apt-get update" and "sudo apt-get upgrade" (you could probably also just open Update Manager).

---

### Post by uberlube on 2008-02-27
google devede patch and install its quick and simple.

---

