---
title: "Can't type using Java"
date: 2008-12-13
forum: Multimedia Software
---

### Post by KujiUn on 2008-12-13
When I play Java games on the Internet, sometimes I can't use the keyboard. This can get really annoying, especially when the games require me to log on. I'm using Ubuntu Intepid and Sun Java v.1.6.0.10.

EDIT: I figured out that the input cuts off when I change tabs or programs. Any way to remedy this?

---

### Post by jamesstansell on 2008-12-14
> **KujiUn said:**
> When I play Java games on the Internet, sometimes I can't use the keyboard. This can get really annoying, especially when the games require me to log on. I'm using Ubuntu Intepid and Sun Java v.1.6.0.10.

EDIT: I figured out that the input cuts off when I change tabs or programs. Any way to remedy this?

It sounds like the applet doesn't have keyboard focus anymore.  In other words, your focus may be in a browser window but not in the applet section of the window.  In that case the applet won't be able to read your keystrokes.

---

### Post by KujiUn on 2008-12-15
No, that isn't the problem, because I keep clicking on the applet window, and it even works, but the keyboard is the problem. The mouse works fine.

---

