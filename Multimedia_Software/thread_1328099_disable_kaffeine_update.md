---
title: "disable kaffeine update?"
date: 2009-11-16
forum: Multimedia Software
---

### Post by proevofanatik on 2009-11-16
i upgraded from kubuntu 9.04 to 9.10. i had the older kaffeine installed and it auto updated to the new one. i didnt like it so i uninstalled the new kaffeine and installed the old one again. but everytime i boot up it says ive got 1 update for kaffeine. how do i disable this?

the reason i dont like the new kaffeine is there isnt any soft cams available.

thanks

---

### Post by hal10000 on 2009-11-16
run synaptic, choose the kaffeine package, then go to "Package"--->"lock version"

---

### Post by proevofanatik on 2009-11-16
how do i run synaptic in kubuntu 9.10?

---

### Post by realzippy on 2009-11-16
There is no synaptic in Kubuntu.You can install it with adept packet manager.Or in terminal:
**sudo apt-get install synaptic**

---

### Post by proevofanatik on 2009-11-16
i locked the version but the update still appears. its just anoying that it pops up everytime i boot up

---

### Post by proevofanatik on 2009-11-19
anyone know how to get rid of this?

---

### Post by SuperSonic4 on 2009-11-19
```
sudo aptitude hold kaffeine
```

---

### Post by proevofanatik on 2009-11-19
> **SuperSonic4 said:**
> ```
sudo aptitude hold kaffeine
```


update still comming up m8. this is driving me bonkers.

---

### Post by proevofanatik on 2009-11-20
does anyone know how to disable this update?

---

### Post by tim71 on 2009-11-21
```
sudo apt-get install wajig

sudo wajig hold kaffeine
```

issuing a "Lock version" in synaptic may also be needed in addition.

---

