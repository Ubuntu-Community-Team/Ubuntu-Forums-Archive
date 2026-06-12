---
title: "How to PREVENT ATI FGLRX package update"
date: 2006-06-16
forum: Multimedia &amp; Video
---

### Post by flapane on 2006-06-16
hi
I installed succesfully 8.25.18 on amd64 and compiled fglrx module, too, on my custom kernel.
So I'd prevent to update ati packages when doing apt-get upgrade, to avoid issues with 3d.
So how to mark a package as UNUPDATABLE ?

---

### Post by olsonar on 2006-06-16
open synaptic, select the package and choose package -> lock version.

---

### Post by Galban on 2006-06-16
Thanks olsonar, I didn't know that you can do that within Synaptic.

---

### Post by flapane on 2006-06-16
i use adept and I can't find it:(

---

### Post by olsonar on 2006-06-16
k, try this
```
sudo aptitude <packagename>=
```

---

