---
title: "how to fix FF sound bug in 8.04"
date: 2008-10-13
forum: Multimedia Software
---

### Post by c/Kr3t on 2008-10-13
this worked for me

```
sudo ln -s /usr/lib/libesd.so.0 /usr/lib/libesd.so.1
sudo mkdir -p /tmp/.esd/
sudo touch /tmp/.esd/socket
sudo apt-get install libflashsupport
```

edit: also, i had flash 9 installed

---

