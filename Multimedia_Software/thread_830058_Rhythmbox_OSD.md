---
title: "Rhythmbox OSD"
date: 2008-06-15
forum: Multimedia Software
---

### Post by billybag on 2008-06-15
How exactly do you get OSD to work with Rhythmbox?

I have Gnome OSD installed
i am using Hardy Heron/Linux Mint 5

OK i got it to work. Now how do i configure it? i is really ugly and annoying

---

### Post by barzam on 2008-06-26
Just alt+f2 and enter gnome-osd-properties, that opens the setup program. Good luck!

---

### Post by lunatico on 2008-08-24
I'm trying to get this to work too.
If I do gnome-osd-properties I get:

> ~$ gnome-osd-properties 
Traceback (most recent call last):
  File "/usr/local/bin/gnome-osd-properties", line 4, in <module>
    capplet.main()
  File "/usr/local/lib/python2.5/site-packages/gnomeosd/capplet.py", line 346, in main
    notebook.append_page(general_preferences(), gobject.new(
  File "/usr/local/lib/python2.5/site-packages/gnomeosd/capplet.py", line 198, in general_preferences
    FontSync(font, prefs, 'osd_font')
  File "/usr/local/lib/python2.5/site-packages/gnomeosd/capplet.py", line 104, in __init__
    font.set_font_name(prefs[key])
  File "/usr/local/lib/python2.5/site-packages/gnomeosd/gconfsync.py", line 103, in __getitem__
    return self.__gconf_get(key)
  File "/usr/local/lib/python2.5/site-packages/gnomeosd/gconfsync.py", line 70, in __gconf_get
    val = self.__value_to_python(val)
  File "/usr/local/lib/python2.5/site-packages/gnomeosd/gconfsync.py", line 43, in __value_to_python
    if value.type == gconf.VALUE_BOOL:
AttributeError: 'NoneType' object has no attribute 'type'


Any help is much appreciated!

---

