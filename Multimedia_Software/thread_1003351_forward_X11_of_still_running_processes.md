---
title: "forward X11 of still running processes"
date: 2008-12-06
forum: Multimedia Software
---

### Post by skylerweaver on 2008-12-06
Hey guys,

I searched online and I can't seem to figure this out:

When you restart X (ctrl+alt+bksp) the processes you had running are still there. Is there any way to bring the X windows back?

Furthermore, if I ssh with xterm into a remote linux box can I forward the currently running processes' X to my local machine?

Skyler

---

### Post by cdtech on 2008-12-06
> **skylerweaver said:**
> if I ssh with xterm into a remote linux box can I forward the currently running processes' X to my local machine?
Skyler
To forward a program using the client X session:
```
ssh -Y user@server "program"
```

---

### Post by skylerweaver on 2008-12-06
Thanks for the quick reply!

I don't think that is exactly what I want...

```
ssh -Y user@server "program"
```

will connect to 'server' as 'user' and launch 'program' forwarding X11 to me.

But I started a program on the remote box already. Now I don't want to go over to the other machine to check its progress. (I know it is finished from 'top -u') Can I forward its *already* launched X to my remote machine? Even just to view?

---

### Post by cdtech on 2008-12-06
This can be achieved using the X window system. You can read about it here:
[http://www.faqs.org/docs/Linux-mini/Remote-X-Apps.html](http://www.faqs.org/docs/Linux-mini/Remote-X-Apps.html)

---

