---
title: "no sound in ubuntu"
date: 2008-09-27
forum: Multimedia Software
---

### Post by vandreaddita on 2008-09-27
i had my pc on when i went to work, when i came back i had no sound.

im using standard plug and play speaker, which i have tested using other devices, so i know that there working.


8.04, what could be cauing this problem

---

### Post by stands2reason on 2008-09-28
> **vandreaddita said:**
> 
8.04, what could be cauing this problem

A hanged or zombie process. My favorite soluion:

```


killall -9 -1


```

This will kill all processes that you have authority to kill (make sure to save all work, etc. before trying this). This should fix the problem.

---

