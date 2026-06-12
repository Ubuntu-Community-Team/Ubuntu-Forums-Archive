---
title: "Random Compiz Crash"
date: 2010-02-08
forum: Multimedia Software
---

### Post by Hawk__0 on 2010-02-08
I am using TwinView with an nvidia GeForce 8400GS and I randomly get compiz crashes.  It's not often, but enough to be annoying (since all my windows are jammed onto the default 2 screens...).  This is the error I found in dmesg:

```
[97021.847506] compiz.real[2412]: segfault at 8 ip 0181f2c5 sp bfa27d94 error 4 in libGLcore.so.185.18.36[dd4000+d6f000]
```

I'm not positive this is the error, since I don't exactly know what dmesg does.  I just ran dmesg | grep compiz when I got in this morning and found that compiz died.

---

### Post by plut0 on 2010-02-09
I've been having the same problem with compiz for years.  I'm getting real sick of it.

```
[266335.113090] compiz.real[2473]: segfault at 8 ip 00007fc4df2fc583 sp 00007fffe65953e0 error 4 in libGLcore.so.185.18.36[7fc4de80a000+dda000]
[271536.464872] compiz.real[693]: segfault at 8 ip 00007fbd1c6ff583 sp 00007fff8d5144b0 error 4 in libGLcore.so.185.18.36[7fbd1bc0d000+dda000]
```

---

### Post by Hawk__0 on 2010-02-09
You've had this problem on several versions of ubuntu or just one?  I never had this problem till this release on this computer...

---

### Post by plut0 on 2010-02-09
I had compiz crashes on 9.04 and still do on 9.10.

---

