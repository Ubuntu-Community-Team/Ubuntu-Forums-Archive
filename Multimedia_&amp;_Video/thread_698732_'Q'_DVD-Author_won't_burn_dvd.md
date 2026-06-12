---
title: "'Q' DVD-Author won't burn dvd"
date: 2008-02-16
forum: Multimedia &amp; Video
---

### Post by albertoguevara on 2008-02-16
Hey guys i'm using 'q' dvd-author to make a DVD Project, i have everything ready and when i click on 'Create DVD' i get this: ```
STAT: fixed 2 VOBUS                         
FATAL: /dev/dvd already carries isofs!
* BD/DVDÂ±RW/-RAM format utility by <appro@fy.chalmers.se>, version 7.0.
:-( unable to open("/dev/srcd0"): No such file or directory
/tmp/execute.sh: line 3: mkisofs: command not found
/tmp/execute.sh: line 3: dvdrecord: command not found
```

And nothing else happens then... anyone know what could be wrong?... thanks.

---

### Post by bliffle on 2008-02-19
I haven't tried qdvdauthor, yet, but it looks to me like the diagnostics say:

1-your target DVD disk already has the file structure on it from an "ISO", so it can't burn the new ISO. Possibly, a previous attempt to burn the DVD got partly done. Lookat the DVD with nautilus (or something like it) to see if it already has a file system.

2-two programs (mkisofs, dvdrecord) are not where qdvdauthor expects them to be. Perhaps an install went awry.

I'm just guessing.

---

