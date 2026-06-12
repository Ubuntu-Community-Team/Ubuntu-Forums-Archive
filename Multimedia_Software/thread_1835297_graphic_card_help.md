---
title: "graphic card help?"
date: 2011-08-29
forum: Multimedia Software
---

### Post by Utsukushii Tsubasa on 2011-08-29
alright, so, i had an e-machine that i loaded ubuntu into, and i knew what it had in it. however, that ones put away, and i ended up getting another. seeing how i enjoy using ubuntu so much, i swapped operating systems again. but theres been some work done to it, and i dont know how to see what graphics card i have. i can pretty much navigate myself around, and figure everything out that i need to, but on the things i dont, i come to you guys (and gals). what do i need to run in terminal to find my graphics card? and if you want to go the extra mile, where can i go to learn more about ubuntu, and commands? thanks in advance.
os, ubuntu 11.04

---

### Post by realzippy on 2011-08-29
```
lspci |grep VGA
```

```
lshw -c video
```

---

