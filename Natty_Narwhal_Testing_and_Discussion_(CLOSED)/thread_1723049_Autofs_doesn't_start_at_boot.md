---
title: "Autofs doesn't start at boot"
date: 2011-04-06
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by druhboruch on 2011-04-06
Autofs doesn't start at boot
I has to be started manually.

Could you suggest any way to automate it?

---

### Post by druhboruch on 2011-04-07
The bug was already in:
[https://bugs.launchpad.net/ubuntu/natty/+source/autofs5/+bug/733914](https://bugs.launchpad.net/ubuntu/natty/+source/autofs5/+bug/733914)

What I am looking for is some temporary cludge to start the service after boot process is completed.

Any suggestions?

---

### Post by cariboo on 2011-04-07
What are you using autofs for? Nautilus normally looks after auto mounting drives and devices.

---

### Post by druhboruch on 2011-04-07
I am automounting my nfs shares. 
It is much more convenient than fstab, because I can change mounts without rebooting.

I do hope that the bug will be fixed soon, but in the mean time I would like to run 
```
service autofs start
``` after rebooting.

I was thinking rc.local?

---

### Post by alexmurray on 2011-04-07
Yes - rc.local is probably the best spot for it.

---

### Post by druhboruch on 2011-04-07
The computer in question runs XBMS standalone live.
If I try to start autofs from rc.local then my XBMC doesn't load.

Currently I have to ssh to this box in order to start automounter.
Otherwise it won't find my media...

---

### Post by cariboo on 2011-04-07
Rc.local, or an upstart script:

[http://upstart.ubuntu.com/getting-started.html](http://upstart.ubuntu.com/getting-started.html)

---

### Post by druhboruch on 2011-04-07
Thanks,
Learning how to write upstart scripts sounds like time well wasted.
I will give it a shot.


Edit:  Fix released.

---

