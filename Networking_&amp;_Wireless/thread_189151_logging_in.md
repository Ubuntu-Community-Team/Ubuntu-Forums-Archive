---
title: "logging in"
date: 2006-06-04
forum: Networking &amp; Wireless
---

### Post by benner on 2006-06-04
i installed breezy on a dell p3 450.  no prob.  i have an adsl connection through my ethernet card and there appears to be activity.  my provider told me it generates random ip's so i selected DHCP but couldn't figure out where to put in the login/password.  when i called the technicians again, they recommended i switch to windows and couldn't help me with linux.  i wasn't impressed...  i live in china.  not an unusual kind of answer.

-benner

---

### Post by adwait on 2006-06-04
You probably use PPPoE. So try running
```
sudo pppoeconf
```

---

