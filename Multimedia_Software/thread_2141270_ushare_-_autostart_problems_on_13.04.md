---
title: "ushare - autostart problems on 13.04"
date: 2013-05-02
forum: Multimedia Software
---

### Post by e-Tiggy on 2013-05-02
**UPDATE: sorry, does not stick, see first reply.**

Hi,

I had a problem with ushare not autostarting ever since I updated to raring, finally found the sollution to fix the rc.d scripts thanks to KodeShark and I thought I share it with you guys in case somebody else needs it.
Type these two commands in the terminal:
```
sudo update-rc.d -f ushare remove
sudo update-rc.d ushare start 90 2 3 4 5 . stop 10 0 1 6 .
```

[Original article]("http://kodeshark.com/tutorials/ubuntu/install-ushare")

---

### Post by e-Tiggy on 2013-05-02
All right, so it worked for one restart, I repeat, ONE restart. It's getting on my nerves, anybody knows a sollution for this?
Of course, there is always a way for adding a simple 'ushare' command to the "startup applications" dialog but I consider this a workaround, not an actual fix since this way the process cannot be stopped by '/etc/init.d/ushare stop' or 'service ushare stop'.

---

