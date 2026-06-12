---
title: "[SOLVED] Myth 0.21 kills mythvideo"
date: 2008-03-19
forum: Mythbuntu
---

### Post by batman01 on 2008-03-19
Just done a clean install of mythbuntu 7.10. cos I had a problem where the upgrade to Myth 0.21 killed Mythvideo. WhenI went to update manager mythvideo was listed but I couldn't select it.

So as mentioned I did a clean install, I've run the update manager and sure enough myth video is present but not selectable, so I guess its gonna break again.

Anyone else had this problem? Is it a cock up by someone looking ater the update system?

Cheers

Pete

---

### Post by larsolav on 2008-03-19
To fix the mythvideo problem:

```
sudo aptitude remove mythdvd

sudo aptitude install mythvideo
```

Several threads on this topic on this forum, see for example:
[http://ubuntuforums.org/showthread.php?t=722960](http://ubuntuforums.org/showthread.php?t=722960)
[http://ubuntuforums.org/showthread.php?t=727063](http://ubuntuforums.org/showthread.php?t=727063)
[http://ubuntuforums.org/showthread.php?t=722756](http://ubuntuforums.org/showthread.php?t=722756)

---

### Post by batman01 on 2008-03-22
Thanks, you're the man! I'll use the search button next time....

---

### Post by batman01 on 2008-04-04
OK I upgraded it again, went to follow your advice, except its Music Controls and Gallery that are dead this time, Videos work OK.

This is pissing me off now, the update process to Mythbuntu appears to be exceedingly sloppy.

Can anyone give me an idea where how to proceed?

CHeers

Pete

---

