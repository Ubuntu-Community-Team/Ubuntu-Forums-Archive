---
title: "ath9k install, top level directory"
date: 2010-05-21
forum: Networking &amp; Wireless
---

### Post by davavanstone on 2010-05-21
Hi im trying to install the latest ath9k driver and i get this error...

./scripts/driver-select ath9k
Must run ./scripts/driver-select from the compat-wireless top level directory

What does this mean, what am i doing wrong?

---

### Post by HansCombee on 2010-05-21
Same problem here, I had no problem installing this before. Now also getting this error with a virgin install of my netbook.

Hans.:guitar:

---

### Post by pytheas22 on 2010-05-21
Try doing just:
```

scripts/driver-select ath9k
```

That works for me using the snapshot of the code released today.

---

### Post by HansCombee on 2010-05-21
Weird... this doesn't do the job for me. I retrieved a version of last week which gave me no problem...

:confused:

---

### Post by pytheas22 on 2010-05-21
What is the output of the command:
```

pwd
```

in the same shell from which you're trying to run the script?

---

### Post by davavanstone on 2010-05-22
Giving up!!
Ive been reading some more about my card and it doesnt look like n speeds are gonna be happening for a while, unless someone here has sorted it before? What cards work out of the box for 9.10 and 10.04?

---

### Post by pytheas22 on 2010-05-22
> Giving up!!
Ive been reading some more about my card and it doesnt look like n speeds are gonna be happening for a while, unless someone here has sorted it before? What cards work out of the box for 9.10 and 10.04? 

I'm pretty sure ath9k has supported 11n mode since 2008.  What exactly is not working for you?  Is the wireless card not detected at all, or is it just not performing as well as you'd like?

---

### Post by HansCombee on 2010-05-26
Hi guys!

I solved the issue by downloading an April version of the wireless drivers, they install fine. Beware that after a kernel upgrade you will have to do the trick again. :)

Hans.

---

