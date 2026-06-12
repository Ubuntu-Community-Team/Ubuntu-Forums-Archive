---
title: "Error trying to read Maverick Launchpad PPA"
date: 2010-09-26
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Peter7K on 2010-09-26
```
Could not open file /var/lib/apt/lists/ppa.launchpad.net__ppa_ubuntu_dists_maverick_main_source_Sources - open (2: No such file or directory)
```

Is there a fix for this?  Maybe I was muddling around and messed something up..  Thanks.

---

### Post by cariboo on 2010-09-26
Try changing the version to Lucid, many ppa's don't have a Maverick version yet.

---

### Post by Peter7K on 2010-09-26
I actually got this error when I sudo apt-get build-dep wine.  Is there a way to do lucid build-deps from this command?  Thanks.

---

### Post by cariboo on 2010-09-26
Where are the depends supposed to come from? The ppa or the regular repositories.

---

### Post by Peter7K on 2010-09-26
I'm using wine-1.3.3... I guess I should get the ppa and use that.. doh!

---

### Post by Peter7K on 2010-09-26
Well even after adding the ppa it gives the same error.  I basically just need the dependencies for wine-1.3.3 so I can compile it on Maverick.  Thanks.

---

### Post by mc4man on 2010-09-26
Why don't you open up software sources and under the Ubuntu Software tab make sure the Source code box is colored in.
If it was then unmark it, click close and reload.
Then open software sources again, enable the Sources box, close and reload

---

### Post by Peter7K on 2010-09-26
That still didn't seem to work.. but I fixed it by adding the ppa and manually installing wine1.3-dev in addition to a few other dev packages (while compiling it would give an error stating "you probably want this package.. otherwise you won't see any fonts lawl")

---

