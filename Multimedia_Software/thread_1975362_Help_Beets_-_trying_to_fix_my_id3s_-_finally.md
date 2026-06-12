---
title: "Help Beets - trying to fix my id3s - finally"
date: 2012-05-07
forum: Multimedia Software
---

### Post by geekyhawkes on 2012-05-07
hey;

so im trying to get ontop of my horrible ID3 tags and beets seems to be the weapon of choice for linux.

Im running 12.04 xubuntu and ran sudo apt-get install beets.  All went well, i have a beets config file (albeit pretty slim as it only has chroma and the directories in it).  When i try to run a beet import /media/nas/New/ i get this error

> ** error loading plugin chroma
Traceback (most recent call last):
  File "/usr/share/beets/beets/plugins.py", line 148, in load_plugins
    __import__(modname, None, None)
  File "/usr/share/beets/beetsplug/chroma.py", line 21, in <module>
    import acoustid
ImportError: No module named acoustid

Traceback (most recent call last):
  File "/usr/bin/beet", line 9, in <module>
    load_entry_point('beets==1.0b12', 'console_scripts', 'beet')()
  File "/usr/share/beets/beets/ui/__init__.py", line 697, in main
    raise UserError("database file %s could not be opened" % db_path)
beets.ui.UserError: database file /home/geeky/music/musiclibrary.blb could not be opened


Can someone help me please?  

Thanks

---

### Post by geekyhawkes on 2012-05-17
Can anyone help me with this please? I cant get to the bottom of what the error means let alone where to start fixing it!

---

### Post by enigma32 on 2012-05-17
I'm no expert, but I'll take a stab at it while I'm waiting for my thread to be answered :-)

I believe this is the key:
```
File "/usr/share/beets/beetsplug/chroma.py", line 21, in <module>
import acoustid
ImportError: No module named acoustid
```

Looks like you're missing a python module.
I would guess it is this one: [http://packages.ubuntu.com/precise/python-acoustid](http://packages.ubuntu.com/precise/python-acoustid)

I don't see that package in 10.04/Lucid, but perhaps you'll find it if you search for it in Synaptic in your release version?

---

### Post by geekyhawkes on 2012-05-21
Thanks, getting closer i think.  The error now reads:

> Traceback (most recent call last):
  File "/usr/bin/beet", line 9, in <module>
    load_entry_point('beets==1.0b12', 'console_scripts', 'beet')()
  File "/usr/share/beets/beets/ui/__init__.py", line 697, in main
    raise UserError("database file %s could not be opened" % db_path)
beets.ui.UserError: database file /home/geeky/music/musiclibrary.blb could not be opened


After i installed the missing py module you mentioned.

---

### Post by geekyhawkes on 2012-05-23
Anyone?

---

### Post by geekyhawkes on 2012-05-24
EDIT: Fixed im an idiot and the directory i was pointing beets to in the config file didnt exist (i had music not Music!)

---

