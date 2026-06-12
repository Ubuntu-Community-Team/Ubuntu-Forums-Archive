---
title: "Creox and Jack"
date: 2009-04-24
forum: Multimedia Software
---

### Post by neanderslob on 2009-04-24
Howdy,

I've been searching the internet trying to find ANY coherent directions on how to configure Jack to work with Creox.  I've gotten bits and pieces but am still largely in the dark.  I know Jack has configuration documentation, however it's very open ended given the individual application. I'd appreciate it if someone could point me in the right direction. 

 :guitar:  

Many thanks.

---

### Post by everthonvaladao on 2009-08-06
you need to run jackd before creox, so this command will do the job:

```
(xterm -e "jackd -d alsa" &) && creox
```

:)

---

