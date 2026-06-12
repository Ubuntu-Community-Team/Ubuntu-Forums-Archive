---
title: "pssh not working"
date: 2011-04-03
forum: Networking &amp; Wireless
---

### Post by marsty5 on 2011-04-03
Hi!

I use ubuntu 10.04 and here's the problem. I've installed pssh, but when I type pssh i got this message 
```
# pssh
Traceback (most recent call last):
  File "/usr/bin/pssh", line 29, in <module>
    from psshlib.basethread import BaseThread
ImportError: No module named basethread

```Also, if I type man pssh I got this message: 
See 'man 7 undocumented' for help when manual pages are not available.

I've reinstalled it, but nothing changed. 
I've found that basethread is located here:
/usr/lib/python2.5/site-packages/psshlib/basethread.py
/usr/lib/python2.5/site-packages/psshlib/basethread.pyc

I think the problem has to do with the location of the file, but i'm not sure since I'm quite new to this! I would appreciate if someone could help me!
Thanks! :)
Maria

---

### Post by marsty5 on 2011-04-04
Please is there anyone who could help me?? Any idea would be appreciated!!

---

