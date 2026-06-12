---
title: "[howto] fix login after installing farsight dependices"
date: 2009-08-22
forum: Networking &amp; Wireless
---

### Post by jarrah-95 on 2009-08-22
after installing glib while trying to install farsight the login screen might not load propely 
instead of a login screen you get the loading cursor and a black background 
to fix this press ctrl alt f1 and login then type 
```

sudo apt-get purge glib

```
then the lodin screen ready should sound 
press ctrl alt f7 and login normaly 
if you dont reinstall glib after this then it should not happen again

---

