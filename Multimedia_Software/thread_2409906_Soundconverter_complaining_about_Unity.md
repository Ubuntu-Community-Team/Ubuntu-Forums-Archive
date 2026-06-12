---
title: "Soundconverter complaining about Unity"
date: 2019-01-08
forum: Multimedia Software
---

### Post by Langstracht on 2019-01-08
I recently (belatedly) installed ubuntu 18.04.  In so doing I somehow lost the Soundconverter installation - which had been working flawlessly.

So I (re)installed it but using it returns an "error" message as follows:

>   "faac" gstreamer element not found, disabling AAC output.
/usr/share/soundconverter/python/soundconverter/ui.py:1406: Warning: g_value_type_transformable: assertion 'G_TYPE_IS_VALUE (src_type)' failed
  builder.add_from_file(gladefile)

(python3:7773): Gtk-WARNING **: 05:52:44.398: ../../../../gtk/gtkliststore.c:836: Unable to convert from (null) to gchararray
Cannot find audio profile "GStreamer profile", resetting to default output.
adding: 0 files
adding: 1 files
Queue start: 1 tasks, 1 thread(s).
Queue done in 103.709s (1 tasks)
/usr/share/soundconverter/python/soundconverter/ui.py:1323: PyGIWarning: Unity was imported without specifying a version first. Use gi.require_version('Unity', '7.0') before import to ensure that the right version gets loaded.
  from gi.repository import Unity 

Supposedly it created a file (in perhaps a quarter of the time I would have expected!)... but I can't locate it.

Muchly appreciate it if someone can tell me how to specify and import (and I guess install) the required Unity version.

TIA

Allan

---

### Post by again? on 2019-01-08
This is in Xubuntu 18.04
Start with the debug option where it will show the ouput location.
I see errors but it still appears to convert into the same directory as the original file.(check soundconverter preferences)
Try with the debug option ...
```
soundconverter --debug
```
```
**[COLOR="#006400"]glen@Bionic:~$[/COLOR] soundconverter --debug**
SoundConverter 3.0.0
  using GTK version: 3.0
  using Gstreamer version: 1.14.1.0
/usr/share/soundconverter/python/soundconverter/gstreamer.py:70: PyGIWarning: GConf was imported without specifying a version first. Use gi.require_version('GConf', '2.0') before import to ensure that the right version gets loaded.
  from gi.repository import GConf
  using gio
  "faac" gstreamer element not found, disabling AAC output.
/usr/share/soundconverter/python/soundconverter/ui.py:1406: Warning: g_value_type_transformable: assertion 'G_TYPE_IS_VALUE (src_type)' failed
  builder.add_from_file(gladefile)

(python3:28296): Gtk-WARNING **: 22:35:05.343: ../../../../gtk/gtkliststore.c:836: Unable to convert from (null) to gchararray
adding: 0 files
Added 0 files in 0.00s (scan 0.00s, add 0.00s)
adding: 1 files
Added 1 files in 0.00s (scan 0.00s, add 0.00s)
Queue start: 1 tasks, 4 thread(s).
launching: 'giosrc location="file:///home/glen/Desktop/bell.mp3" name=src ! decodebin name=decoder ! audiorate ! audioconvert ! audioresample ! vorbisenc quality=0.6 ! oggmux  ! giosink location="file:///home/glen/Desktop/bell.mp3~524385~SC~"'
found_tags: bell.mp3
found_tags: bell.mp3
found_tags: bell.mp3
[COLOR="#FF0000"]/home/glen/Desktop/bell.mp3~524385~SC~ -> /home/glen/Desktop/bell.ogg[/COLOR]
Creating folder 'file:///home/glen/Desktop'?
Queue done in 0.407s (1 tasks)
closing...
```


or try without the graphical interface...
```
soundconverter --debug --batch [COLOR="#696969"]/path/to/file/to/convert[/COLOR]
```
```
**[COLOR="#006400"]glen@Bionic:~$[/COLOR] soundconverter --debug --batch /home/glen/Desktop/bell.mp3**
SoundConverter 3.0.0
  using GTK version: 3.0
  using Gstreamer version: 1.14.1.0
/usr/share/soundconverter/python/soundconverter/gstreamer.py:70: PyGIWarning: GConf was imported without specifying a version first. Use gi.require_version('GConf', '2.0') before import to ensure that the right version gets loaded.
  from gi.repository import GConf
  using gio
  "faac" gstreamer element not found, disabling AAC output.
bell.mp3: \launching: 'giosrc location="file:///home/glen/Desktop/bell.mp3" name=src ! decodebin name=decoder ! audiorate ! audioconvert ! audioresample ! vorbisenc quality=0.6 ! oggmux  ! giosink [COLOR="#FF0000"]location="file:///home/glen/Desktop/bell.ogg"[/COLOR]'
bell.mp3: |found_tags: bell.mp3
found_tags: bell.mp3
found_tags: bell.mp3
```

---

### Post by Yellow Pasque on 2019-01-10
Thread is marked Solved, but no solution is given.
Anyway, if you're trying to make AAC/M4A files in SoudConverter, you need to jump through a few hoops first: [https://ubuntuforums.org/showthread.php?t=2404956&p=13813511#post13813511](https://ubuntuforums.org/showthread.php?t=2404956&p=13813511#post13813511)

---

