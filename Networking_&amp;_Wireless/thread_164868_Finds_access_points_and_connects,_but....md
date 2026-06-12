---
title: "Finds access points and connects, but..."
date: 2006-04-23
forum: Networking &amp; Wireless
---

### Post by UbuntuStudent on 2006-04-23
My PC finds access points and connects. I have entered the encryption key and I would suppose anything was ok, but firefox can't find any pages, can't connect to IM or anything either :( 

Anyone know what the problem is? I suppose it has something to with the configuration since everything else work...

---

### Post by Jason_25 on 2006-04-23
Look at the output of
```

sudo iwconfig

```
Confirm that it matches your key.  If you used the graphical network app it surely set the key wrong.

---

