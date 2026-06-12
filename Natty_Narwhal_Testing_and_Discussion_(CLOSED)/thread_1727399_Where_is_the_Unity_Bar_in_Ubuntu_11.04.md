---
title: "Where is the Unity Bar in Ubuntu 11.04"
date: 2011-04-12
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by jacatone on 2011-04-12
Been playing around with the new Ubuntu 11.04 beta and was wondering where this Unity Bar is located. Anyone know?

So far, it looks like Macbuntu without the greyness. Thanks.

---

### Post by TeoBigusGeekus on 2011-04-12
You need to install 3d drivers for your graphics card (restricted drivers I guess) and then you will be able to choose the unity desktop when you log in.

---

### Post by uRock on 2011-04-12
Moved to Natty Narwhal Testing & Discussion.

---

### Post by jacatone on 2011-04-12
And how do I install these 3D drivers?

---

### Post by Joe of loath on 2011-04-12
system > administration > additional drivers ;)

---

### Post by jacatone on 2011-04-12
Just say's "No proprietary drivers are in use on this system". What now?

---

### Post by marin123 on 2011-04-12
```
sudo apt-get install fglrx
```

at least that works for me, i have ati radeon hd 5xxx card..

---

### Post by TeoBigusGeekus on 2011-04-12
What's your graphics card?
```
lshw -C display
```

---

### Post by Joe of loath on 2011-04-12
> **marin123 said:**
> ```
sudo apt-get install fglrx
```

at least that works for me, i have ati radeon hd 5xxx card..

Only works if you have a newer ATI card.

---

### Post by grahammechanical on 2011-04-13
It may have said

>  "No proprietary drivers are in use on this system".

because that statement is true but did get get an option to activate a driver? If you did, then make sure you have an internet connection and click activate and the drivers will be installed.

Regards.

---

