---
title: "Problem with Exaile and --get-artist"
date: 2009-10-14
forum: Multimedia Software
---

### Post by DarkSideoftheMoon on 2009-10-14
I'm running Exaile 0.2.14 on Jaunty (well, technically it's the basic Eeebuntu 3.0 install, which as far as I know is just Jaunty with some extra EeePC bits).  I'm trying to get my current song displayed in my MSN personal message, which in theory I should be able to do using "exaile --get-artist" and "exaile --get-title".  The output I get in the terminal, though, is:

```
me@mycomputer:~$ exaile --get-artist
Disturbed
/usr/share/exaile/xl/library.py:17: DeprecationWarning: the md5 module is deprecated; use hashlib instead
  import md5, os, random, re, threading, time, traceback, gc, sys
location: /usr/lib/xulrunner-1.9.1.3/libxpcom.so 
before 3
```

I can see it's telling me *something* is wrong, but I haven't a clue how to go about working out what the problem is or how to fix it.  I've tried reinstalling Exaile, which doesn't help.  Can anyone tell me what it means/how to fix it?

---

