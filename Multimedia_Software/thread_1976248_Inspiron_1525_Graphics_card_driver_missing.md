---
title: "Inspiron 1525 Graphics card driver missing???"
date: 2012-05-08
forum: Multimedia Software
---

### Post by iMurshaq on 2012-05-08
Hey all!!!

I run Ubuntu 10.04 Lucid on my Inspiron 1525 and I have an issue with the graphics card drivers. If I check the system drivers, it says that there is no driver for the Intel HD graphics card but it works like there is a driver installed. This may not be an actual problem but I believe that since it may not have the correct driver installed, it may be slowing my graphics down a bit.

Any help would be appreciated!!!

(P.S. I am in class right now and therefore don't have access to my Ubuntu machine, so any answers that require console output, I will try when I get back to my dorm)

---

### Post by kc1di on 2012-05-08
> **iMurshaq said:**
> Hey all!!!

I run Ubuntu 10.04 Lucid on my Inspiron 1525 and I have an issue with the graphics card drivers. If I check the system drivers, it says that there is no driver for the Intel HD graphics card but it works like there is a driver installed. This may not be an actual problem but I believe that since it may not have the correct driver installed, it may be slowing my graphics down a bit.

Any help would be appreciated!!!

(P.S. I am in class right now and therefore don't have access to my Ubuntu machine, so any answers that require console output, I will try when I get back to my dorm)
It means that the opensource driver was most likely used. 
If there is a propritory driver it should be offered under system setting > additional drivers. 
you can find the driver currently being used by typing in a terminal the following:
```
lspci | grep VGA
```

---

### Post by iMurshaq on 2012-05-08
I know for a fact that when I go to Additional Drivers, there are no more drivers offered.

---

### Post by Yellow Pasque on 2012-05-08
> **iMurshaq said:**
> I know for a fact that when I go to Additional Drivers, there are no more drivers offered.
That is expected for Intel GPU's, which do not have additional/proprietary drivers. You do not have a problem/issue with the driver.

---

### Post by iMurshaq on 2012-05-08
Ok, thanks!

---

