---
title: "Listen music player, stopped working."
date: 2008-01-01
forum: Multimedia &amp; Video
---

### Post by vpvega on 2008-01-01
So the Listen player was working just fine. I believe I installed the python package along with it. I also installed some other package to get ipod support which caused the player to stopped functioning. I don't remember the name of this package, but I want to uninstall it. 
Now Listen does not go past the "Starting Listen Music..." phase. Launching the program through the Terminal gives me:

apple@apple-desktopU:~$ listen
No musicbrainz support (musicbrainz2 missing)
No Audio cd support (musicbrainz2 missing)
Traceback (most recent call last):
  File "/usr/lib/listen/listen.py", line 218, in <module>
    ListenApp()
  File "/usr/lib/listen/listen.py", line 145, in __init__
    self.listen_instance = Listen()
  File "/usr/lib/listen/widget/listen.py", line 89, in __init__
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
Segmentation fault (core dumped)

Would anyone know how to solve this? Or know the name of the 2nd package that I installed. Thanks in advance for any help.

---

### Post by jordilin on 2008-01-01
I just tried to install Listen through synaptic and it goes with python-pymad dependency. Hope that helps.

---

### Post by vpvega on 2008-01-02
I tried....and it is still not working :(

---

