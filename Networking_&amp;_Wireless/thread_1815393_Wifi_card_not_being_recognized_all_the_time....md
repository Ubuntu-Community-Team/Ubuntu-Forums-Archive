---
title: "Wifi card not being recognized all the time..."
date: 2011-07-31
forum: Networking &amp; Wireless
---

### Post by jfulcher on 2011-07-31
Not sure if I am posting in the right area... I am a noob to this site. But I have a sony vaio vng-n220e and my wifi card doesn't always work with ubuntu, forcing me (ugh) to revert back to windows... I would really like to resolve this issue if anyone can help.

---

### Post by chili555 on 2011-07-31
If it is sometimes recognized and sometimes not, it is likely that the driver doesn't always see the wireless card and load automatically. Let's see what card you have and tell the system to load the driver automatically. Please open a terminal and run and post:```
lspci -nn | grep 0280
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

