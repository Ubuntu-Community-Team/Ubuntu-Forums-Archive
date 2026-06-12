---
title: "mkv with sm player"
date: 2012-02-22
forum: Multimedia Software
---

### Post by bbb13 on 2012-02-22
Im running xubuntu 11.10 in my old machine (ASUS P4VM800,Pentium 4 3.0GHZ, 2GB DDR,ATI Radeon X1950 Pro).i'm using the open source drivers for my ATI that came with xubuntu, since catalyst cannot be installed in my system cause it doesnt suppor the newest X.Org. With XV video output in sm player i can watch .avi's but when i try an .mkv file (not HD) it stutters like crazy. any ideas??

---

### Post by SeijiSensei on 2012-02-22
I'd guess that the Matroska containers have video encoded in H.264, while the AVIs have XviD or DivX video.  Decoding H.264 material is very processor intensive and can often overpower older machines.  Having an ATI card is another limitation since there's no method for offloading the H.264 decoding task to the graphics hardware like you can with recent NVIDIA cards.

I don't think there is any simple solution for you.  One option is to try replacing mplayer with mplayer2 by adding a PPA repository as outlined [here]("http://www.ubuntugeek.com/install-mplayer2-on-ubuntu-using-ppa.html").  Another is to use mencoder to convert the H.264 files into XviD encodes.  Documentation for that available [here]("http://131.246.123.5/DOCS/HTML/en/encoding-guide.html") and [here]("http://en.gentoo-wiki.com/wiki/Mencoder").

---

### Post by bbb13 on 2012-02-23
thnx a lot, i'll try that

---

