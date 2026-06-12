---
title: "Sound probs with cmedia 8738 - has selective playing"
date: 2008-10-09
forum: Multimedia Software
---

### Post by kDDs on 2008-10-09
My cmedia 8738 worked kinda out of the box. Rythmbox player works, as does the start up sound, but, for some reason, flash has absolutely no sound.... Any suggestions as to why? :(

I also noticed it doesn't work in blob wars, which was one of the main reasons why I installed ubuntu...

---

### Post by wolfen69 on 2008-10-09
you may want to try ```
sudo apt-get install libflashsupport
``` if that doesn't work, you could try [removing pulseaudio]("http://www.ubuntugeek.com/fix-for-all-pulseaudio-related-issues.html").

---

### Post by kDDs on 2008-10-09
Thanks, for the help, but it seems to have fixed itself :S I think it's cause I still had the intel HD audio on in BIOS, turned it off, and flash and blob wars work fine!

---

