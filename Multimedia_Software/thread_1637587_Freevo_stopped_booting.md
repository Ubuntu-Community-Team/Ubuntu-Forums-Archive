---
title: "Freevo stopped booting"
date: 2010-12-04
forum: Multimedia Software
---

### Post by pgcudahy on 2010-12-04
I got freevo up and working pretty smoothly with my pvr-350 tv-out card. When I turned on my computer it would come up automatically. Now it has suddenly stopped loading on boot. When I try and load it from the command line I get
```
It is advisable not to start freevo as root, due to security concerns.
Please use the 'freevo' user to start freevo.
/usr/lib/python2.6/dist-packages/kaa/metadata/disc/cdrom.py:37: DeprecationWarning: the md5 module is deprecated; use hashlib instead
  import md5

Warning: display is set to x11, but the environment has no DISPLAY set. Setting display to fbdev.

Traceback (most recent call last):
  File "/usr/share/pyshared/freevo/config.py", line 658, in <module>
    execfile(overridefile, globals(), our_locals)
  File "/etc/freevo/local_conf.py", line 1834
     
    ^
 SyntaxError: invalid syntax
```

Any ideas on how I can start tracking down what's going on?

---

