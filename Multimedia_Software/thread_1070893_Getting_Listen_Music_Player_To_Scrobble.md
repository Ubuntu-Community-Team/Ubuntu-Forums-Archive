---
title: "Getting Listen Music Player To Scrobble"
date: 2009-02-15
forum: Multimedia Software
---

### Post by joey-elijah on 2009-02-15
hey y'all, Listen 0.5 will not scrobble to last fm. 

I followed the "fix" on the trac ticket which gave a new version of 'audio_scrobbler.py' however when i replace the old one with the new listen refuses to start. Running in terminal it gives me this: -

```
location: /usr/lib/xulrunner-1.9.0.6/libxpcom.so 
before 3
Traceback (most recent call last):
  File "/usr/lib/listen/listen.py", line 218, in <module>
    ListenApp()
  File "/usr/lib/listen/listen.py", line 144, in __init__
    from widget.listen import Listen
  File "/usr/lib/listen/widget/listen.py", line 41, in <module>
    from audioscrobbler_manager import AudioScrobblerManager
  File "/usr/lib/listen/audioscrobbler_manager.py", line 1
    <!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
    ^
SyntaxError: invalid syntax

```

The actual listen sites isn't very helpful on this. any takers?

---

