---
title: "rvmb to avi"
date: 2008-02-17
forum: Multimedia Production
---

### Post by afeasfaerw23231233 on 2008-02-17
which software can be used to convert rmvb/rm/mp4/mpg to mp4/avi?

---

### Post by afeasfaerw23231233 on 2008-02-18
buMp

---

### Post by Creative2 on 2008-02-18
fuoco  converter should be work 
before install it try this :

```
mencoder INPUT -ofps 25 -oac mp3lame -lameopts preset=64 -ovc xvid -xvidencopts bitrate=600  -vf scale -zoom -xy 640  -o OUTPUT 
```

---

