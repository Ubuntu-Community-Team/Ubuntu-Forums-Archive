---
title: "VirtualBox and Guest Additions"
date: 2010-09-01
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Peter09 on 2010-09-01
Don't know what it is but for the life of me I cannot get Maverick to move from 800x600 in VirtualBox. Anyone seen a resolution to this anywhere?

---

### Post by jfernyhough on 2010-09-01
[http://ubuntuforums.org/showthread.php?t=1564881](http://ubuntuforums.org/showthread.php?t=1564881)

> This is down to the current guest addition not supporting xorg-server 1.9.

Error message from my Maverick-on-Maverick VM:

```
Warning: unsupported pre-release version of X.Org Server installed.  Not installing the X.Org drivers.
```

Along with a lot of other things we have to wait until other companies update to support Xorg 7.6 (and server 1.9).

---

### Post by Peter09 on 2010-09-01
thanks for the answer

---

### Post by loboris on 2010-09-01
Uninstall VirtualBox guest additions and instal guest additions from Maverick repo. Everything works.

---

### Post by Peter09 on 2010-09-01
Well I thought I'd done that, certainly reinstalled guest additions - so would have thought that would have been picked up  from the Maverick repositories.

---

### Post by jfernyhough on 2010-09-01
> **loboris said:**
> Uninstall VirtualBox guest additions and instal guest additions from Maverick repo. Everything works.That's crafty, and excellent!

Not sure I like how it wants to install VirtualBox within the running VM, though.

---

### Post by KdotJ on 2010-09-01
Which do I need to install from the repo? The Addons or the ISO image? I installed the addons (There was 3 of them) and I still couldn't change the resolution...

---

