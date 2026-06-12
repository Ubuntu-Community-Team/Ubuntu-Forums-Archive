---
title: "xorg editing for i845 inspiron 1100"
date: 2010-06-08
forum: Multimedia Software
---

### Post by at0msk on 2010-06-08
Really? 2008 and no replies? I have just installed 10.04 LTS on my Inspiron 1100 and I really want to get this video driver debacle taken care of! It seems that one cannot simply edit xorg.conf on 10.04 LTS as it's owned by root and I'm not sure how to acquire root access...

Anyway, can we get some aid here?

I've read a couple of threads similar to this one here:
[http://ubuntuforums.org/showthread.php?t=30235&page=2](http://ubuntuforums.org/showthread.php?t=30235&page=2)

Problem is, I can't save changes to the xorg.conf file...

---

### Post by _Mark_ on 2010-06-08
sudo is you're friend

```
sudo gedit /etc/X11/xorg.conf
```

of course make a backup first

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

---

### Post by overdrank on 2010-06-08
I have moved your post to its own thread, no need to bump a 2 year old thread. :)

---

