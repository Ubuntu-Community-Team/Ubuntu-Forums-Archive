---
title: "Mounting network drive without username or pwd"
date: 2009-09-18
forum: Networking &amp; Wireless
---

### Post by tushar_t on 2009-09-18
I want to mount a network drive using this command:

```
sudo mount -t cifs -o username=user,password=pwd //server//folder /home/Desktop
```But suppose there is no username or password for this server, how do I modify the command? I'm guessing there is an escape character that allows me to do that, because simply leaving blanks gives me a "Permission denied" error.

---

### Post by tushar_t on 2009-09-18
bump :)

---

