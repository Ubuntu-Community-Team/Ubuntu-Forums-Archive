---
title: "No Sound on certain apps - but sound at the system level works"
date: 2008-06-21
forum: Multimedia Software
---

### Post by boyd98 on 2008-06-21
Flash - no sound

DVD player through mplayer - no sound

MythTv, no sound


but at the system level, when i test sound i have it???

because all three apps have multiple threads on no sound, im not sure where to start...seems like it may not be app specific but some underlying issue?


Any thoughts on where i should start - really appreciate it

---

### Post by l33th4x0r on 2008-06-21
I had a similar problem with my sound. I was able to play sound in my media player but not in flash. 
Try enabling libflashsupport
'sudo apt-get install libflashsupport'
This is what fixed my problem. Hopefully that helps

---

