---
title: "Restart X in 10.10 Maverick Beta"
date: 2010-09-16
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by axonxorz on 2010-09-16
Hey,

I was wondering how to restart an X session in Ubuntu 10.10. Normally I would CTRL+ALT+Fn to a VT, and restart the GDM service, but now when GDM comes back up, it says 'User x, already logged in' and logging in seems to return to the session in progress (a crashed white screen)

How do I fully end a desktop session without rebooting?

---

### Post by zika on 2010-09-16
> **axonxorz said:**
> Hey,

I was wondering how to restart an X session in Ubuntu 10.10. Normally I would CTRL+ALT+Fn to a VT, and restart the GDM service, but now when GDM comes back up, it says 'User x, already logged in' and logging in seems to return to the session in progress (a crashed white screen)

How do I fully end a desktop session without rebooting?Go to tty1 (Ctrl-Alt-F1) and try **sudo service gdm restart**...

---

### Post by dannyboy79 on 2010-09-16
im assuming he already tried that since his comments clearly were written that he "restarted gdm". 

I would try this, once in the VT, as you call it, (im assuming you're talking about tty1 or the likes, instead of restarting gdm, STOP it. commands would be
```
sudo service gdm stop
```
```
startx
```

see what happens. good luck

---

### Post by xebian on 2010-09-16
> **axonxorz said:**
> Hey,

I was wondering how to restart an X session in Ubuntu 10.10. Normally I would CTRL+ALT+Fn to a VT, and restart the GDM service, but now when GDM comes back up, it says 'User x, already logged in' and logging in seems to return to the session in progress (a crashed white screen)

How do I fully end a desktop session without rebooting?

When at the tty

sudo stop gdm
sudo gdm

If you still have problems after stopping gdm, sudo killall gdm usually helps for me.

---

