---
title: "Listen"
date: 2009-12-11
forum: Multimedia Software
---

### Post by matty-guy on 2009-12-11
I've been trying to get Listen to work for a while now, and even after upgrading my system it still seems to have trouble. I'm pretty determined to get this program to work, and help would be appreciated. Its in the menu, but when i click on it, nothing happens. I then went to the terminal and typed Listen and got this error:

> listen
/usr/lib/pymodules/python2.6/musicbrainz2/model.py:21: DeprecationWarning: the sets module is deprecated
  from sets import Set
Traceback (most recent call last):
  File "listen", line 210, in <module>
    Updater()
  File "/usr/lib/listen/updater/__init__.py", line 34, in __init__
    self.update()
  File "/usr/lib/listen/updater/__init__.py", line 38, in update
    version = self.get_config_version()
  File "/usr/lib/listen/updater/__init__.py", line 284, in get_config_version
    objs = unpk.load()
  File "/usr/lib/python2.6/pickle.py", line 858, in load
    dispatch[key](self)
  File "/usr/lib/python2.6/pickle.py", line 880, in load_eof
    raise EOFError
EOFError

I don't know if anyones ever experienced this, and through google i can only find people who have had errors with "pickle.py" and the same line error as me, but in other programs. Through reading other peoples solutions, there seems to be an unclosed open_file something or other, but with my minimal programming experience i couldn't find anything in seemingly the file that everything is loaded from. Any help would be appreciated. If you need me to post up the main listen file then just say, and i will post it.

Thanks

---

### Post by matty-guy on 2009-12-12
No one?

---

### Post by commodore256 on 2009-12-12
Never do an OS upgrade, Always backup and then reformat and then re-install all of your apps.

---

### Post by matty-guy on 2009-12-12
Thanks, I've already backed up so I'll fresh install because i have other stuff that seems stuck half way between the old and new versions.

---

