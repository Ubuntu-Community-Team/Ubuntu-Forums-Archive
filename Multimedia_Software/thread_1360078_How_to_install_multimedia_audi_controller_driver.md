---
title: "How to install multimedia audi controller driver"
date: 2009-12-20
forum: Multimedia Software
---

### Post by marcher22 on 2009-12-20
Hey I have Ubuntu 9.10 running (Karmic Koala) . I have trouble of getting the sound card to work, or even be detected for that matter. While running Windows XP for some reason sound card was not working but I think all it needed was a multie media audio controller driver. ( i had that problem with another PC before). 
 
How could I go about downloading one on ubuntu. In fact Im not sure about installing anything on Ubuntu because I remember looking for a tutorial on downloading Flash and I was kind of disapointed how i had to type things In a command line to get flash. Maybe there was another way but Im used to just downloading smething and then running the installating.
 
thanks

---

### Post by Yellow Pasque on 2009-12-20
So... what sound device do you have?
```
lspci
aplay -l
lshw -C mulitmedia
```

---

