---
title: "Microsoft lifecam VX-1000 on Linux"
date: 2009-09-26
forum: Multimedia Software
---

### Post by avi93 on 2009-09-26
hey,
i spent over a month trying to play my camera (Microsoft lifecam VX-1000) on Ubuntu but with no success.
i looked for solutions but no one seems to be works for me.
    
i'd love to know if anyone has solved this before

Thanks!

---

### Post by stanca on 2009-10-07
Works in 9.04 with cheese:
```
sudo apt-get install subversion build-essential linux-headers-$(uname -r) && wget http://linuxtv.org/hg/~jfrancois/gspca/archive/tip.tar.bz2 && tar xf tip.tar.bz2 && cd gspca-* && make && sudo make install && sudo depmod -ae $(uname -r)
```

---

### Post by boobaloo on 2009-10-18
stanca, thx a lot! it is works. The only thing - in Skype mic now not works. In past video not worked, but mic works fine. now all is head over heels :)
microsoft...

---

### Post by p41r0 on 2009-10-31
> **stanca said:**
> Works in 9.04 with cheese:
```
sudo apt-get install subversion build-essential linux-headers-$(uname -r) && wget http://linuxtv.org/hg/~jfrancois/gspca/archive/tip.tar.bz2 && tar xf tip.tar.bz2 && cd gspca-* && make && sudo make install && sudo depmod -ae $(uname -r)
```


that code does'nt work for me, when it's about to finish, it asks me for the Karmoc Koala Live CD, whitch I dont have, since I upgraded from 9.04...what should I do??

---

