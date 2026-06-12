---
title: "How to play matroska file on gutsy?"
date: 2008-02-03
forum: Multimedia &amp; Video
---

### Post by kinngg on 2008-02-03
I have problems playing .mkv files, i dont seem to have the appropriate codecs, help please

---

### Post by RomeReactor on 2008-02-03
Hi. I think you need the w32codecs; to get them, look [here]("http://ubuntuforums.org/showpost.php?p=4254739&postcount=20"). In case you're running Gutsy 64-bit, you need the **w64codecs** package; search for it if you decide to add the Medibuntu repository, or get it [here]("http://packages.medibuntu.org/pool/non-free/w/w64codecs/w64codecs_20061203-0medibuntu2_amd64.deb").

It's better to play Matroska videos that come encoded in h264 in Mplayer than in Totem.

---

### Post by Regenpak on 2008-02-04
Mplayer should play it *out of the box*, if not it will complain about codecs and offer to download restricted/proprietary codecs. Also note that you need a fast CPU to play these files. I used a P4/2.8 GHz which was sometimes unable to decode 720p. Now I have an AMD X2 5000+ and that plays a 1080p file with up to 38% CPU load.

---

