---
title: "Can not rip audio cds to mp3 using k3b"
date: 2008-11-15
forum: Multimedia Software
---

### Post by vytalelementz on 2008-11-15
I am having trouble ripping audio cds to mp3 format using k3b. I get an error message stating the lame command has failed. I installed lame and the libraries required so I'm not sure why it keeps failing. Any help is appreciated.

---

### Post by benerivo on 2008-11-15
What is the exact error message? I think you have to specify some lame 'arguments' when encoding, and these can cause an error. In k3b there is an option somewhere to edit the lame encoding. What do you use? I would use something like```
lame --preset standard -h --tt %t --ta %a --tl %m --ty %y --tg %g --tn %n --tc %c - %f
```

---

### Post by vytalelementz on 2008-11-15
I have just tried the same command you have posted and still nothing.

---

