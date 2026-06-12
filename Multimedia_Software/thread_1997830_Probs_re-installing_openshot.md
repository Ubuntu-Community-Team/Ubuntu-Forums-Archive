---
title: "Probs re-installing openshot"
date: 2012-06-05
forum: Multimedia Software
---

### Post by Baldrick_NZ on 2012-06-05
Hi all,

Last night I installed the upgraded to the newest version of Kdenlive, but in doing so, it seems to have removed Openshot, which is my prefered video editor.

I have since removed Kdenlive and tried to reinstall Openshot using terminal, and I get this
```
The following packages have unmet dependencies.
 openshot : Depends: python-mlt3 but it is not going to be installed or
                     python-mlt2 but it is not installable or
                     python-mlt but it is not installable
E: Unable to correct problems, you have held broken packages.

```

So, in Synaptic, I try to resolve the packages one-by-one, and it would seem I can have some working but not all at the same time.

I then do```
sudo apt-get purge libmlt-data libmlt3 libmlt4 melt python-mlt3 python-mlt4 kdenlive kdenlive-data

```in order to start afresh, but I get the same message regarding unmet dependencies.

Any help to get Openshot re-installed would be very much appreciated!

---

### Post by Baldrick_NZ on 2012-06-05
Solved. Answer found here [http://www.debianuserforums.org/viewtopic.php?f=55&t=1036](http://www.debianuserforums.org/viewtopic.php?f=55&t=1036)

Happy me...

---

