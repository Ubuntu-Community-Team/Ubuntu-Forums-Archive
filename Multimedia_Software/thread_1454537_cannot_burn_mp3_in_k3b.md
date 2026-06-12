---
title: "cannot burn mp3 in k3b"
date: 2010-04-14
forum: Multimedia Software
---

### Post by slashwannabe94 on 2010-04-14
hello everyone, im having major issues. i would like to burn some mp3s to a disc using k3b. yet when i try it gives an error message "sorry, unsupported format". 

how do i fix this? 

i must burn them as an mp3 for my mom. simple problem i know but anyone out there who can help.... please :)

---

### Post by slashwannabe94 on 2010-04-14
p:s im using ubuntu 9.10

---

### Post by ron999 on 2010-04-14
Hi
In k3b look in:-
Settings > Configure k3b > Plugins

Look to see if there's a plugin named 'K3b MAD decoder'. If it's there make sure it's ticked.

---

### Post by slashwannabe94 on 2010-04-14
i have no such decoder installed, where do i get this "MAD DECODER" ron???

---

### Post by ron999 on 2010-04-14
Hi
In Synaptic I think it is the package **libk3b6-extracodecs**.

---

### Post by slashwannabe94 on 2010-04-14
thanks mate. that worked :D

---

### Post by smoka on 2010-11-14
Cheers ron999,

**libk3b6-extracodecs** enabled burning mp3 for me as well (ubuntu 10.04)

---

### Post by aussielinuxguy on 2011-03-13
Thanks ron999, it worked for me as well. good stuff.

---

### Post by shakma on 2011-05-03
Super awesome!  Thanks so much for this simple solution.  Why the @!*# isn't this just one of the dependencies?!  MP3 inc. really needs to just give in and go open source...

Peace.

---

