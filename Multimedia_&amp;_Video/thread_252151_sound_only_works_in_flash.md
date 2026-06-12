---
title: "sound only works in flash"
date: 2006-09-06
forum: Multimedia &amp; Video
---

### Post by nebiru on 2006-09-06
So, I had sound working perfectly, it was a beautiful thing...until I rebooted.  Now I only get sound with flash, nothing else will even play a note.  I've searched to forums but can't find anything that helps.

$ lspci -v | grep audio
0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
0000:01:04.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)

---

### Post by CyberCod on 2007-03-22
Look under switches for something like
IEC958 in Monitor
and make sure it is on

---

