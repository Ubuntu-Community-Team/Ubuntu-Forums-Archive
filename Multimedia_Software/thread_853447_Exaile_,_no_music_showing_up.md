---
title: "Exaile , no music showing up"
date: 2008-07-08
forum: Multimedia Software
---

### Post by BBin on 2008-07-08
Exaile scans my collection directory, but no music is showing up in the list (Rhythmbox works fine on the same dir.). What could be the problem?

Using gutsy and exaile from apt.

---

### Post by pofigster on 2008-07-08
Do you have the mp3 codecs installed?

---

### Post by BBin on 2008-07-08
I don't know. Rhythmbox, totem, vlc works with mp3, but maybe all those are xine?
Edit: I installed gstreamer0.10-fluendo-mp3... No change.
Edit #2: Removed totem-xine and installed totem-gstreamer. Mp3 is working in totem, so it's not the codecs.

---

### Post by BBin on 2008-07-09
Gotta bump! This is really important :confused:

---

### Post by BBin on 2008-07-09
EDIT: I have narrowed the problem down to artists/songs with ÅÄÖ (and probably other non-american letters) in their ID3-Tags/Filename/Filepath (not sure witch one of those)



After removing the ~/.exaile directory and reinstalling exaile.
Starting up program and adding two directories with stndard-character (no ÅÄÖ) artists/songs, Terminal output:
```

Importing sql changes file changes0001.sql
Importing sql changes file changes0002.sql
Created db for thread Thread-1
{'Thread-1': <sqlite3.Connection object at 0x8a1a728>}
Closed db for thread Thread-1
Using multimedia keys from: gnome
loading tracks...
done loading tracks...
loading songs
Clearing tracks cache
Last playlist loaded
Starting scan timer at 25
Running is False
File count: 12
Created db for thread Thread-6
{'Thread-6': <sqlite3.Connection object at 0x8a1a728>}
Count is now: 12
Closed db for thread Thread-6
loading tracks...
done loading tracks...
loading songs
Clearing tracks cache
Running is False
File count: 145
Count is now: 145
Created db for thread Thread-9
{'Thread-9': <sqlite3.Connection object at 0x8a1a728>}
loading tracks...
Closed db for thread Thread-9
done loading tracks...
loading songs
Clearing tracks cache

```


When I add a directory with songs with non-english characters:
```

Running is False
File count: 124
/usr/share/exaile/xl/xlmisc.py:703: GtkWarning: gtk_text_buffer_emit_insert: assertion `g_utf8_validate (text, len, NULL)' failed
  self.buf.insert(iter, text)
Couldn't read tags from file: /media/Zero/music/Winnerbäck/2007 - Daugava/09-Vad &#65533;r Det Som Bekymrar Sara Wehn.mp3
-----------------------
 run ( /usr/share/exaile/xl/library.py @ 616):
-----------------------
Traceback (most recent call last):
  File "/usr/share/exaile/xl/library.py", line 654, in run
    self.do_function(loc)
  File "/usr/share/exaile/xl/library.py", line 804, in do_function
    path_id = get_column_id(db, 'paths', 'name', unicode(loc, xlmisc.get_default_encoding()))
UnicodeDecodeError: 'utf8' codec can't decode byte 0x9f in position 52: unexpected code byte

Count is now: 124
Created db for thread Thread-12
{'Thread-12': <sqlite3.Connection object at 0x8a1a9f8>}
Exception in thread Thread-12:
Traceback (most recent call last):
  File "/usr/lib/python2.5/threading.py", line 486, in __bootstrap_inner
    self.run()
  File "/usr/lib/python2.5/threading.py", line 446, in run
    self.__target(*self.__args, **self.__kwargs)
  File "/usr/share/exaile/xl/library.py", line 900, in load_songs
    self.exaile.all_songs)
  File "/usr/share/exaile/xl/library.py", line 306, in load_tracks
    """):
  File "/usr/share/exaile/xl/db.py", line 186, in select
    cur.execute(query, args)
OperationalError: Could not decode to UTF-8 column 'name' with text '/media/Zero/music/Winnerbäck/2007 - Daugava/09-Vad &#65533;r Det Som Bekymrar Sara Wehn.mp3'

```

---

### Post by rbolio on 2008-09-09
could it have something to do with your library being in folders?... i mean my collection only detects 9 songs >.<

---

