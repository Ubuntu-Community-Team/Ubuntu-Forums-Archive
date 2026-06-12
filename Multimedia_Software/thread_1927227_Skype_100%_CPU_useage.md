---
title: "Skype 100% CPU useage"
date: 2012-02-17
forum: Multimedia Software
---

### Post by 65 mustang on 2012-02-17
In the last week or so i have had problems with Skype stuck at 100% CPU useage.  I have to do a 'pkill -9 skype' to get it to stop.

The only change i have made lately is to add the "proposed" repo.  That may have broke it.  Running Ubuntu 11.10 x64.

---

### Post by winh8r on 2012-02-17
I remember reading somewhere that Skype sometimes has problems if it cannot find logfiles to write to.

try this in the teminal:


```
mkdir ~/.Skype/Logs
```


If it works, good, if it doesn't then we will look elsewhere!!!

---

