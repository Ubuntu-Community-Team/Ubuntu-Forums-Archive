---
title: "Network management disabled, mysteriously"
date: 2010-08-03
forum: Networking &amp; Wireless
---

### Post by Anjetto on 2010-08-03
Hello, I installed Kubuntu recently and everything worked well. I went on holiday for two weeks, left my laptop at home and off the entire time. When I came back he laptop won't connect, it says that 'Network management has been disabled' and, try as I might I'm unable to reactivate it.

I've tried everything that I know so any help would be appreciated. Thanks

---

### Post by dineshs on 2010-08-03
I dont know kubuntu.Maybe this will work```
gksudo gedit /etc/NetworkManager/nm-system-settings.conf 
``` 
and set```
managed=true
```

---

