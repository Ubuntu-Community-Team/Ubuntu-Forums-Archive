---
title: "Kdenlive crashed!"
date: 2009-03-27
forum: Multimedia Software
---

### Post by B4RR13N705 on 2009-03-27
Hi, i was using kdenlive normally then, one time i tried to execute it and this happened:
```

kdenlive: WARNING: //////  RENDER, SET SCENE LIST
KCrash: Application 'kdenlive' crashing...
Unable to start Dr. Konqi

```
And it closes.
I also tried
```
strace kdenlive
```
And i can find this line at the end:
```

write(2, "Unable to start Dr. Konqi\n", 26Unable to start Dr. Konqi

```
What happened?

---

