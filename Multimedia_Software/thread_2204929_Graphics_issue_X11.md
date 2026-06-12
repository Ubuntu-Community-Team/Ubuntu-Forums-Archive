---
title: "Graphics issue X11"
date: 2014-02-11
forum: Multimedia Software
---

### Post by jesualdo2 on 2014-02-11
Dear all.

We are facing a strange situation we are not been able to fix. We are running Force Field Explorer using X11 forwarding and we get different results from different operating systems, and we do not really understand why. The connections are to the same server (Ubuntu 12.04) and with the same user.

From Max OS, using ssh -X, it works fine.
From Windows using Putty+Xming, it works fine. Comment: Xming-mesa not basic Xming. With MobaxTerm the rendering of graphics is not correct.
From Ubuntu 12.04 , with ssh -X it does not work fine. The rendering of the graphics have problems, it displays something like interferences (see file attached).

Thanks for any help or hint.

---

### Post by jesualdo2 on 2014-02-18
We have "solved" this problem by upgrading to Ubuntu 13.10, we were not able to find any solution for 12.04.

---

