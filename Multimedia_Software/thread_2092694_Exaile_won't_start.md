---
title: "Exaile won't start"
date: 2012-12-08
forum: Multimedia Software
---

### Post by Dubanubiel on 2012-12-08
Exaile was happily running up until a couple of weeks ago when it just decided to not open up any more. Tried running it through terminal and got the following:

INFO    : Loading Exaile 0.3.2.2...
INFO    : Loading settings...
WARNING : Failed to import gtk.glade, interface will not be fully translated.
INFO    : Loading plugins...
INFO    : Loading collection...
INFO    : Loading devices...
INFO    : Loading interface...
WARNING : Failed to connect to HAL, autodetection of devices will be disabled.
INFO    : Loading main window...
INFO    : Connecting main window events...
Traceback (most recent call last):
  File "/usr/lib/exaile/exaile.py", line 62, in <module>
    main()
  File "/usr/lib/exaile/exaile.py", line 59, in main
    exaile = main.Exaile()
  File "/usr/lib/exaile/xl/main.py", line 102, in __init__
    self.__init()
  File "/usr/lib/exaile/xl/main.py", line 226, in __init
    self.gui = xlgui.Main(self)
  File "/usr/lib/exaile/xlgui/__init__.py", line 102, in __init__
    exaile.collection, exaile.player, exaile.queue, covers.MANAGER)
  File "/usr/lib/exaile/xlgui/main.py", line 406, in __init__
    self.load_saved_tabs()
  File "/usr/lib/exaile/xlgui/main.py", line 444, in load_saved_tabs
    pl = self.add_playlist(pl, erase_empty=False)
  File "/usr/lib/exaile/xlgui/main.py", line 523, in add_playlist
    while (name % i) in names:
ValueError: unsupported format character 'R' (0x52) at index 5

---

