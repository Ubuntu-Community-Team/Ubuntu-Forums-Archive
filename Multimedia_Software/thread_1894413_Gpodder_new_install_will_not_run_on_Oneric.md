---
title: "Gpodder new install will not run on Oneric"
date: 2011-12-12
forum: Multimedia Software
---

### Post by intruderukr on 2011-12-12
I just installed gpodder on my inspiron e1405 running Oneric.  Gpodder does not run, when I tried to run from the terminal I get this message:
[HTML](process:2731): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.
Traceback (most recent call last):
  File "/usr/bin/gpodder", line 201, in <module>
    from gpodder import gui
  File "/usr/lib/pymodules/python2.7/gpodder/gui.py", line 71, in <module>
    from gpodder import util
  File "/usr/lib/pymodules/python2.7/gpodder/util.py", line 69, in <module>
    locale.setlocale(locale.LC_ALL, '')
  File "/usr/lib/python2.7/locale.py", line 540, in setlocale
    return _setlocale(category, locale)
locale.Error: unsupported locale setting[/HTML]
do I have to change my locale?  Strange, because gpodder works on my dell mini...
please help!

---

