---
title: "Big problems with wifi"
date: 2010-11-15
forum: Networking &amp; Wireless
---

### Post by I love this on 2010-11-15
hey guys i was messing around with ndiswrapper and i installed a driver for my wifi cause i was only getting 1mb with the linux drivers my card was already working i was just trying out the ndiswrapper and now i have no drivers is there any way i can turn the linux drivers back on?

---

### Post by TBABill on 2010-11-15
First need to find out which card you are working with before knowing which driver needs to be working, which driver you tried to use, etc. Please post the output of the following in a terminal:
```
sudo [COLOR=black]lshw -c network[/COLOR]
``` and ```
lspci
``` and ```
iwconfig
``` and ```
sudo rfkill list
```

---

