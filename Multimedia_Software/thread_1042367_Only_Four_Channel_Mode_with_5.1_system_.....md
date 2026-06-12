---
title: "Only Four Channel Mode with 5.1 system ...."
date: 2009-01-17
forum: Multimedia Software
---

### Post by TwiStEr55 on 2009-01-17
Hey guys,

I have a Terratec Aureon 7.1 with a 5.1 system connected. 

My problem is, that I have sound out of the 2 front and 2 back speakers, but not the center.

In Volume Controle the Device is named: C-Media CMI8768

When I activate all controls in the Volume Control I only have one option for sourround which is: Four Channel Mode, which activates the 2 speakers behind me.

No matter what I change in the settings there, my center speaker stays quiet.

Does anybody of you have an idea how to fix this?

---

### Post by Gorstak on 2009-01-23
Try to change 
```
default-sample-channels = 6
```
in ```
/etc/pulse/daemon.conf
```

---

