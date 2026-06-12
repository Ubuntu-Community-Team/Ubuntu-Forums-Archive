---
title: "View video information"
date: 2008-10-12
forum: Multimedia Software
---

### Post by frit on 2008-10-12
Hello all, I want to know if there is a way to view my video card information in ubuntu. I've just switched from windows and I remember it having some kind of 'display settings' where I could view information like manufacturer, model, etc.
Thanks in advance.

---

### Post by cariboo on 2008-10-13
IF you have a Nvidia graphics cardh you can check System-->Administration-->Nvidia X Server Settings. Another way is in a Applications-->Accessories--Terminal type:

```
sudo lshw -C video
```

Jim

---

### Post by frit on 2008-10-13
Thank you very much ;)

---

