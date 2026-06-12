---
title: "[SOLVED] Listen Music Player won't start"
date: 2007-09-15
forum: Multimedia &amp; Video
---

### Post by mndzmyst on 2007-09-15
Sure do hope this is the right place to post this. I installed Listen Music Player from synaptic. I see the splash come up when started, but that is all. When I run it from the terminal, this is what I get.

No Hal support
No musicbrainz support (musicbrainz2 missing)
No Audio cd support (musicbrainz2 missing)
Traceback (most recent call last):
  File "/usr/lib/listen/listen.py", line 219, in <module>
    ListenApp()
  File "/usr/lib/listen/listen.py", line 146, in __init__
    self.listen_instance = Listen()
  File "/usr/lib/listen/widget/listen.py", line 88, in __init__
    self.player_ui = PlayerUI(player)
  File "/usr/lib/listen/widget/player_ui.py", line 98, in __init__
    self.playlist.load()
  File "/usr/lib/listen/widget/player_playlist.py", line 164, in load
    songs = utils.load_db("playlist_cur.db")
  File "/usr/lib/listen/utils.py", line 414, in load_db
    objs = cPickle.load(f)
  File "/usr/lib/listen/song.py", line 423, in __setitem__
    dict.__setitem__(self,"~~"+key,utils.xmlescape(str_value))
  File "/usr/lib/listen/utils.py", line 256, in xmlescape
    return str.replace("&", "&amp;").replace("<", "&lt;").replace(">", "&gt;")
AttributeError: 'long' object has no attribute 'replace'

=======end of output=====

Any help :confused:

---

### Post by Gremlinzzz on 2007-09-15
Did you add repositories if not do so and reinstall player.

[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

---

### Post by mndzmyst on 2007-09-15
All the extra repositories are enabled from what I can tell. It used to work month ago when I first tried Listen, don't know what could have happened since then.

---

### Post by mndzmyst on 2007-10-14
Forget it, will just wait for gutsy next week and see if that help any.

---

