---
title: "Exaile crashing"
date: 2009-08-04
forum: Multimedia Software
---

### Post by Dinchamion on 2009-08-04
Hi all,

I'm using Jaunty, and after a fresh install today I can't use Exaile. I start it up, it starts to scan my collection, then it crashes. Here is the console output:

```
dinchamion@daedalus:~$ exaile
/usr/share/exaile/xl/library.py:17: DeprecationWarning: the md5 module is deprecated; use hashlib instead
  import md5, os, random, re, threading, time, traceback, gc, sys
location: /usr/lib/xulrunner-1.9.0.12/libxpcom.so 
before 3
Exaile 0.2.14
Plugins 'Desktop Cover' version '0.3.3' loaded successfully
Activated gnome mmkeys for gnome 2.22.x
Using multimedia keys from: gnome
[Last.FM]: Logged in successfully
Plugins 'Shoutcast Radio' version '0.4.8' loaded successfully
Plugins 'Resume Playback' version '0.2.3' loaded successfully
Plugins 'Tray Buttons' version '0.7.3' loaded successfully
Created db for thread Thread-2
{'Thread-2': <sqlite3.Connection object at 0x1a79d50>}
Closed db for thread Thread-2
Starting scan timer at 25.0
loading tracks...
done loading tracks...
loading songs
Clearing tracks cache
Last playlist loaded
Library rescan called
Running is False
Created db for thread Thread-7
{'Thread-7': <sqlite3.Connection object at 0x2175e30>}
File count: 2336
/usr/share/exaile/xl/media/__init__.py:61: DeprecationWarning: object.__init__() takes no parameters
  long.__init__(self, num)
Segmentation fault
```

Any suggestions?

Thanks in advance!

---

