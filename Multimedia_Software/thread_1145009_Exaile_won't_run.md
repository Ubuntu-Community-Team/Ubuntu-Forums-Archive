---
title: "Exaile won't run"
date: 2009-05-01
forum: Multimedia Software
---

### Post by blakkandekka on 2009-05-01
Just upgraded to Jaunty and thought I'd give Exaile a try.  Installed from the repositories but it won't run from the menu.  Running exaile %f from the terminal gives the following:

```
/usr/share/exaile/xl/library.py:17: DeprecationWarning: the md5 module is deprecated; use hashlib instead
  import md5, os, random, re, threading, time, traceback, gc, sys
location: /usr/lib/xulrunner-1.9.0.10/libxpcom.so 
before 3
Exaile 0.2.14
-----------------------
 <module> ( /usr/lib/exaile/exaile.py @ 18):
-----------------------
Traceback (most recent call last):
  File "/usr/lib/exaile/exaile.py", line 135, in <module>
    init()
  File "/usr/lib/exaile/exaile.py", line 131, in init
    exaile = exailemain.ExaileWindow(options, xl.path.firstrun)
  File "/usr/share/exaile/xl/gui/main.py", line 139, in __init__
    self.settings = config.Config(xl.path.get_config('settings.ini'))
  File "/usr/share/exaile/xl/config.py", line 260, in __init__
    self.config = XlConfigParser(loc)
  File "/usr/share/exaile/xl/config.py", line 54, in __init__
    converter = ConvertIniToConf(self, self.loc)
  File "/usr/share/exaile/xl/config_convert.py", line 98, in __init__
    v[1](setting, v[0])
  File "/usr/share/exaile/xl/config_convert.py", line 130, in add_rem_list
    if col_name in values:
TypeError: argument of type 'NoneType' is not iterable
```

Should I start with the depreciation warning at the top or the typerror at the bottom?

Any help greatly appreciated.

---

### Post by veloce on 2009-05-07
You could try the development releases from [www.exaile.org's](www.exaile.org's) own repositories.  Full instructions are on their site.

---

### Post by colau on 2009-05-07
You can use audacious
[html]
aptitude install audacious.
[/html]

---

### Post by colau on 2009-05-07
You can use audacious
[html]
aptitude install audacious.
[/html]

---

