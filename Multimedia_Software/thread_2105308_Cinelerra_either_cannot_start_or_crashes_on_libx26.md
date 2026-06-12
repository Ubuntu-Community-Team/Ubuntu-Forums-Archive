---
title: "Cinelerra either cannot start or crashes on libx264.so.98"
date: 2013-01-15
forum: Multimedia Software
---

### Post by 1script on 2013-01-15
Hi all, love(d) Cinelerra while on 10.10, now upgraded to 12.04 and can no longer start it. Re-installed Cinelerra several times already through both the repository and apt-get as well as compiled from Git source - still no go.

Here is the error:
```

cinelerra: error while loading shared libraries: libx264.so.98: cannot open shared object file: No such file or directory 
```

Well, OK, understandable - libx264 is on version 120 already. So, I link libx264.so.98 to libx264.so.120 - now Cinelerra starts but crushes every time you load a video file (of any kind).

Does anyone know how to get past this? In my hours of research online I saw a mention of a patch that exists but cannot figure out where do people get it - is there a repository for Cinlerra patches? cinelerrra.org is devoid of patches except for just one for some plugin. 

Help!

---

