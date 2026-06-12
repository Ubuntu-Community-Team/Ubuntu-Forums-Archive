---
title: "Rhythmbox cannot load Jamendo catalogue"
date: 2007-12-13
forum: Multimedia &amp; Video
---

### Post by atomkarinca on 2007-12-13
It was working after [this]("https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/158941") workaround but now when i want to browse Jamendo it gives me this:

```
Traceback (most recent call last):
  File "/usr/lib/rhythmbox/plugins/jamendo/JamendoSource.py", line 183, in __load_catalogue_read_cb
    parser.close()
  File "/usr/lib/python2.5/site-packages/_xmlplus/sax/expatreader.py", line 226, in close
    self.feed("", isFinal = 1)
  File "/usr/lib/python2.5/site-packages/_xmlplus/sax/expatreader.py", line 220, in feed
    self._err_handler.fatalError(exc)
  File "/usr/lib/python2.5/site-packages/_xmlplus/sax/handler.py", line 38, in fatalError
    raise exception
xml.sax._exceptions.SAXParseException: <unknown>:1:0: no element found
Traceback (most recent call last):
  File "/usr/lib/rhythmbox/plugins/jamendo/JamendoSource.py", line 161, in finish_loadscreen
    self.__load_db ()
  File "/usr/lib/rhythmbox/plugins/jamendo/JamendoSource.py", line 294, in __load_db
    tracks = self.__saxHandler.tracks
AttributeError: JamendoSaxHandler instance has no attribute 'tracks'
```



Is there a workaround for this? I also filed a [bug report.]("https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/176194")

---

### Post by atomkarinca on 2007-12-14
I've managed to solve this problem. If you're experiencing problems browsing Jamendo with Rhythmbox, here's what you can do:

1- Type in terminal:

```
gksudo gedit /usr/lib/rhythmbox/plugins/jamendo/JamendoSource.py
```line 332 is like this:

```
self.__db.set(entry, rhythmdb.PROP_TRACK_NUMBER, int(track['trackno']))
```

change it with:

```
trackno = int(track['trackno'])
if trackno >= 0:
 self.__db.set(entry, rhythmdb.PROP_TRACK_NUMBER, trackno)
```

2- Open nautilus with root privilages, hit alt+f2 and type:

```
gksudo nautilus
```browse to /usr/lib/rhythmbox/plugins/jamendo and delete JamendoSource.pyc

3- Open Rhythmbox with root privilages, hit alt+f2 and type:

```
gksudo rhythmbox
```Now it should create the file JamendoSource.pyc. You can now open your Rhythmbox the usual way. Have fun.

---

### Post by graingert on 2008-01-13
I have done that and it worked for a while.

But suddenly it failed with this error:

```
  File "/usr/lib/rhythmbox/plugins/jamendo/JamendoSource.py", line 183, in __load_catalogue_read_cb
    parser.close()
  File "/usr/lib/python2.5/site-packages/_xmlplus/sax/expatreader.py", line 226, in close
    self.feed("", isFinal = 1)
  File "/usr/lib/python2.5/site-packages/_xmlplus/sax/expatreader.py", line 220, in feed
    self._err_handler.fatalError(exc)
  File "/usr/lib/python2.5/site-packages/_xmlplus/sax/handler.py", line 38, in fatalError
    raise exception
xml.sax._exceptions.SAXParseException: <unknown>:1:0: no element found
Traceback (most recent call last):
  File "/usr/lib/rhythmbox/plugins/jamendo/JamendoSource.py", line 161, in finish_loadscreen
    self.__load_db ()
  File "/usr/lib/rhythmbox/plugins/jamendo/JamendoSource.py", line 294, in __load_db
    tracks = self.__saxHandler.tracks
AttributeError: JamendoSaxHandler instance has no attribute 'tracks'
```

---

### Post by atomkarinca on 2008-01-13
I've noticed that, too. When the problem occurs again, just repeat steps 2 and 3. It should be OK for a while.

---

### Post by graingert on 2008-01-14
ok it's working.... sitll outputs:

```
Traceback (most recent call last):
  File "/usr/lib/rhythmbox/plugins/jamendo/JamendoSource.py", line 183, in __load_catalogue_read_cb
    parser.close()
  File "/usr/lib/python2.5/site-packages/_xmlplus/sax/expatreader.py", line 226, in close
    self.feed("", isFinal = 1)
  File "/usr/lib/python2.5/site-packages/_xmlplus/sax/expatreader.py", line 220, in feed
    self._err_handler.fatalError(exc)
  File "/usr/lib/python2.5/site-packages/_xmlplus/sax/handler.py", line 38, in fatalError
    raise exception
xml.sax._exceptions.SAXParseException: <unknown>:1:0: no element found
Traceback (most recent call last):
  File "/usr/lib/rhythmbox/plugins/jamendo/JamendoSource.py", line 161, in finish_loadscreen
    self.__load_db ()
  File "/usr/lib/rhythmbox/plugins/jamendo/JamendoSource.py", line 294, in __load_db
    tracks = self.__saxHandler.tracks
AttributeError: JamendoSaxHandler instance has no attribute 'tracks'

```

grrr.... why is this so flaky?

Also do you know how I can set up the plugin to use deluge for downloading albums rather than firefox? or better use  xdg-open

---

### Post by atomkarinca on 2008-01-15
You can change your default browser. System > Preferences > Preferred Applications > Internet. It's flaky alright but definitely more stable than BMPx.

---

### Post by graingert on 2008-01-15
I have found the code relating to it,
```
def __download_p2plink (self, link):
		gnomevfs.url_show(link)
```
I think a wget into temp then a xdg-open on that file perhaps?

---

