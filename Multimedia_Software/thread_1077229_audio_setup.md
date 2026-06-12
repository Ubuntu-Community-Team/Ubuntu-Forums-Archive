---
title: "audio setup?"
date: 2009-02-22
forum: Multimedia Software
---

### Post by maddave2008 on 2009-02-22
can someone tell me if there is a simple way of playing electric guitar with kubuntu?i have jack?whatever that is,no instructions on how to setup or what the hell its for, and also installed creox which just says error when started,will i have to sit here and punch in code for a day,cos if so ill go back to MS,as its all plug an play,,and thats all i want to do,,play my guitar,i belive that more users will adopt linux when it is easy to use,

---

### Post by everthonvaladao on 2009-08-06
you need to run jackd before creox, so this command will do the job:

```
(xterm -e "jackd -d alsa" &) && creox
```

:)

---

