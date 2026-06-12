---
title: "UnShare Folder in Command Line"
date: 2009-07-16
forum: Networking &amp; Wireless
---

### Post by Anxious Nut on 2009-07-16
I was messing around when I Shared my home folder, I then installed some programs so i rebooted my pc. The login screen showed up, but after entering my user name and password I got this error that says The home folder must not be accessed by multiple users (shared) and it mentioned something about having  permission 644. 

All I can use right now is the Alt+F1 (shell thingie "CLI") so I really need to know how to Un-Share a Folder using the Command line. So Heeeeeeeelp

Thanx in advance

---

### Post by nixscripter on 2009-07-29
Try changing the permissions:

```
sudo chmod 644 /home/**youruser**
```

---

