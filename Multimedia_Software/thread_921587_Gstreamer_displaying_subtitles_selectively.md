---
title: "Gstreamer displaying subtitles selectively"
date: 2008-09-16
forum: Multimedia Software
---

### Post by master.swarky on 2008-09-16
Hello,

I've encountered a problem: every video application that uses gstreamer as an engine displays the subtitles just selectively, while the mplayer shows 100% of them.

I've heard this is a matter of encodings. Well, my system locale is en_GB.UTF-8 and I watch films with subtitles encoded in UTF-8, CP1250 and ISO-8859-1.

Any ideas?

---

### Post by lovinglinux on 2008-09-16
You have to setup the encoding in the player settings. I would recommend smplayer (it is in the repos). It allow you to use SSA/*** library for subtitle rendering, which gives a very nice result and it's easy to configure the text color, border, font size and encoding.

---

