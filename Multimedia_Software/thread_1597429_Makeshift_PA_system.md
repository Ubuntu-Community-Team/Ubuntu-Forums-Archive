---
title: "Makeshift PA system"
date: 2010-10-15
forum: Multimedia Software
---

### Post by travisl_10 on 2010-10-15
Hi, I'm trying to re-route the mic-in to line-out on the computer, and use it as a sort of makeshift loudspeaker. 

I've tried using pacat to make a loop between the two devices like this:
```
pacat -r -d [source] | pacat -p -d [sink]
```

Unfortunately, the latency is horrible (around 2s delay). Does anyone know a better method? Any help would be appreciated :)

---

