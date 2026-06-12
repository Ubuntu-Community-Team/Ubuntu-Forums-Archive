---
title: "Exaile! Problems with import cd &amp; rescan collection"
date: 2008-01-10
forum: Multimedia &amp; Video
---

### Post by orawax on 2008-01-10
I'm using Exaile in xubuntu gutsy

The Sound Juicer plugin works well, but Import CD or Import Selected Track -options in the context menu don't. Here's the error message:

Exception in thread Thread-9:
Traceback (most recent call last):
  File "threading.py", line 460, in __bootstrap
    self.run()
  File "threading.py", line 440, in run
    self.__target(*self.__args, **self.__kwargs)
  File "/usr/share/exaile/xl/cd_import.py", line 177, in do_import
    'total': len(songs)
KeyError: 'current'

Another problem is that as I try to rescan the collection (Tools > Rescan Collection), nothing happens. There's no clue on this in the command line, it just states 'Library rescan called'. As soon as I have opened and closed the Edit > Preferences dialogue, though, the new tracks are added to the collection.

---

