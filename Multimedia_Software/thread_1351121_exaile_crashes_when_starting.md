---
title: "exaile crashes when starting"
date: 2009-12-10
forum: Multimedia Software
---

### Post by analogian on 2009-12-10
Hi, bit of a newbie but can't find solution anywhere... updated exaile after older version was crashing a lot. New version worked after installation but won't start today. Exaile crashes when I try to run.
tried aptitude purge and reinstall

please move if in wrong place

running jaunty

many thanks

Loading Exaile 0.3.0.2...
INFO : Loading settings...
INFO : Setting up deferred idle manager function...
INFO : Loading plugins...
INFO : Loading collection...
INFO : Loading devices...
INFO : HAL Providers: [<cd.CDHandler object at 0xa8ffeac>]
Traceback (most recent call last):
  File "/usr/lib/exaile/exaile.py", line 56, in <module>
    main()
  File "/usr/lib/exaile/exaile.py", line 53, in main
    exaile = main.Exaile()
  File "/usr/lib/exaile/xl/main.py", line 90, in __init__
    self.__init()
  File "/usr/lib/exaile/xl/main.py", line 194, in __init
    self.stations = playlist.PlaylistManager('radio_stations')
  File "/usr/lib/exaile/xl/playlist.py", line 1141, in __init__
    self.load_names()
  File "/usr/lib/exaile/xl/playlist.py", line 1200, in load_names
    pl.load_from_location(os.path.join(self.playlist_dir, f))
  File "/usr/lib/exaile/xl/playlist.py", line 848, in load_from_location
    (loc, meta) = loc.split('\t')
ValueError: too many values to unpack
cornelius@dinner:~$

---

