---
title: "Problems with sound in Fiesty"
date: 2007-05-21
forum: Multimedia &amp; Video
---

### Post by vmden on 2007-05-21
I have an Acer Aspire 5571 laptop and recently installed ubuntu Fiesty on it. This is the first time I am using ubuntu. The installation was real smooth. The inbuilt soundcards were properly detected. Everything went on fine for a week. Then without notice , I cant hear any sound out of the laptop. I cant pinpoint the source of the problem. However a quick search for a solution led me to do the below:

Opened **gnome-volume-control** , everything is properly checked including laptop speakers.
Also “Edit” -> “Preference”, “Headphone Jack ” and “Line Jack " are checked.

Further research led me to the below post:

 [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

I tried step 1 and it was successful and as directed opened "alsamixer" and everything was in order.
Finally a " ps -eaf "  showed the gnome-volume-manager also running.

Could anyone let me know what the problem could be? Would appreciate any inputs in this respect :)

---

