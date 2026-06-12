---
title: "video formats"
date: 2010-03-04
forum: Multimedia Software
---

### Post by dbowlin17 on 2010-03-04
I tried to use PiTiVi and make a .mpg file. When I play it on linux it works. when i go to windows computers it varies by each machine. is there any special thing that is known to be required for such files to play correctly? the attached image shows the issue I am experiencing with certain XP machines and vista machines trying to play this file...

---

### Post by Jose Catre-Vandis on 2010-03-04
When in linux run :
```
ffmpeg -i video.mpg
``` and post back output. You should get lots of useful info about the file you have created. (You'll need ffmpeg installed for this to work :))

---

### Post by dbowlin17 on 2010-03-04
hey, thanks for the quick response. i decided to try changing the way i encoded it, for about the 6th time, BUT this time it work!!! thanks for everything, this is for you but also the entire community who has always been able to help under any circumstance.

---

### Post by Jose Catre-Vandis on 2010-03-05
Well I didn't want to say "why the heck are you encoding to mpg?" because I am sure you have your reasons, and each to his own. :)

Glad you got it sorted.

---

