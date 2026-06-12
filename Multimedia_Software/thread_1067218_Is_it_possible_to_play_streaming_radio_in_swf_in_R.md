---
title: "Is it possible to play streaming radio in swf in Rhythmbox?"
date: 2009-02-11
forum: Multimedia Software
---

### Post by chene on 2009-02-11
Greetings,

one of my favour online radio is classical FM 96.3, which broadcast in SWF format.  Currently, I use firefox/flash to play it, but I'm looking for a more light-weight solution.

Is it possible to play SWF streaming radio in Rhythmbox?  I tried to add the URL for the SWF file into rhythmbox, but it complains about no suitable codec was found.

any help is very much appreciated,

---

### Post by neu2buntu on 2009-02-11
yeah i have just mastered how to do this for any stream i have tried yet.... for a start the url header ie the page itself is no use . simply do

[1] open rhymbox and your browser 
[2] in rhythmbox open the radio
[3] now in browser put your mouse arrow over where you would download the stream eg 128k 64k
[4] RIGHT click over the required quality ,choose >properties and copy the link properties url
[5] now back to rhythmbox, now look near top and select NEW and paste in value to this window
[6] it will copy the address as the title too but can be easily changed
[?]  in some radio pages right clicking the actual play button will give you an address that will play the stream in rhythmbox as in steps above

---

### Post by neu2buntu on 2009-02-12
UPDATE :  seems i cant get "swf" to play without the need for "licensed software" , i checked your classic fm page sources and all the embedded players are html and swf.  tried this ```
http://player.streamtheworld.com/_players/classical/classical963.swf?stamp=1231521809
``` as a new station but it searches for the codecs then the only choice seems to purchase them (and we dont want that)

i will work at this to see if there is a way around it!!!!

---

### Post by neu2buntu on 2009-02-13
i have pretty much worked at this .swf issue for the past 2 days and still no joy. i have installed every lib and dev file that seems relevant.... 
   when i run rhythmbox from terminal and try to play .swf radio i get

```
 rhythmbox

(rhythmbox:11394): Rhythmbox-WARNING **: Could not open device /dev/radio0
Rhythmbox: could not connect to socket
Rhythmbox: No such file or directory
WARN  coherence                   Feb 14 03:41:42  Coherence UPnP framework version 0.5.6 starting... (coherence/base.py:237)
WARN  webserver                   Feb 14 03:41:42  WebServer on port 42289 ready (coherence/base.py:106)
WARN  rb_media_renderer           Feb 14 03:41:43  __init__ RhythmboxPlayer {'shell': <rb.Shell object at 0xb4ff1e14 (RBShell at 0x9ffa048)>, 'no_thread_needed': True} (coherence/MediaPlayer.py:33)
WARN  rb_media_renderer           Feb 14 03:41:43  get_volume 1.0 (coherence/MediaPlayer.py:357)
Unhandled error in Deferred:
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/twisted/internet/gtk2reactor.py", line 226, in simulate
    self.runUntilCurrent()
  File "/usr/lib/python2.5/site-packages/twisted/internet/base.py", line 705, in runUntilCurrent
    call.func(*call.args, **call.kw)
  File "/usr/lib/python2.5/site-packages/twisted/internet/defer.py", line 243, in callback
    self._startRunCallbacks(result)
  File "/usr/lib/python2.5/site-packages/twisted/internet/defer.py", line 312, in _startRunCallbacks
    self._runCallbacks()
--- <exception caught here> ---
  File "/usr/lib/python2.5/site-packages/twisted/internet/defer.py", line 328, in _runCallbacks
    self.result = callback(self.result, *args, **kw)
  File "/usr/lib/python2.5/site-packages/louie/plugin.py", line 103, in called
    return receiver(*args, **kw)
exceptions.TypeError: detected_media_server() takes exactly 3 non-keyword arguments (2 given)
WARN  rb_media_renderer           Feb 14 03:41:49  elapsed_changed <rb.ShellPlayer object at 0xac553c4 (RBShellPlayer at 0xa17a058)> 0L (coherence/MediaPlayer.py:155)
WARN  rb_media_renderer           Feb 14 03:41:49  update_position 0L -1 (coherence/MediaPlayer.py:183)
WARN  rb_media_renderer           Feb 14 03:42:01  elapsed_changed <rb.ShellPlayer object at 0xac553c4 (RBShellPlayer at 0xa17a058)> 0L (coherence/MediaPlayer.py:155)
WARN  rb_media_renderer           Feb 14 03:42:01  update_position 0L -1 (coherence/MediaPlayer.py:183)
WARN  rb_media_renderer           Feb 14 03:42:01  elapsed_changed <rb.ShellPlayer object at 0xac553c4 (RBShellPlayer at 0xa17a058)> 0L (coherence/MediaPlayer.py:155)
WARN  rb_media_renderer           Feb 14 03:42:01  update_position 0L 0 (coherence/MediaPlayer.py:183)
WARN  rb_media_renderer           Feb 14 03:42:02  playing_song_changed <RhythmDBEntry at 0xb51026c0> (coherence/MediaPlayer.py:71)
WARN  rb_media_renderer           Feb 14 03:42:02  playing_song_changed '<DIDL-Lite xmlns="urn:schemas-upnp-org:metadata-1-0/DIDL-Lite/" xmlns:dc="http://purl.org/dc/elements/1.1/" xmlns:dlna="urn:schemas-dlna-org:metadata-1-0" xmlns:pv="http://www.pv.com/pvns/" xmlns:upnp="urn:schemas-upnp-org:metadata-1-0/upnp/"><item id="1000023" parentID="None" restricted="0"><dc:title>http://player.streamtheworld.com/_players/classical/classical963.swf?stamp=1231521809</dc:title><upnp:class>object.item.audioItem.musicTrack</upnp:class><dc:date>1997-02-28T17:20:00+01:00</dc:date><upnp:artist /><upnp:originalTrackNumber>0</upnp:originalTrackNumber><upnp:genre>Unknown</upnp:genre><upnp:album /><upnp:originalTrackNumber>0</upnp:originalTrackNumber></item></DIDL-Lite>' (coherence/MediaPlayer.py:128)
WARN  rb_media_renderer           Feb 14 03:42:02  elapsed_changed <rb.ShellPlayer object at 0xac553c4 (RBShellPlayer at 0xa17a058)> 0L (coherence/MediaPlayer.py:155)
WARN  rb_media_renderer           Feb 14 03:42:02  update_position 0L 0 (coherence/MediaPlayer.py:183)
WARN  rb_media_renderer           Feb 14 03:42:02  playing_changedTrue (coherence/MediaPlayer.py:134)
WARN  rb_media_renderer           Feb 14 03:42:02  update 'PLAYING' (coherence/MediaPlayer.py:164)
WARN  rb_media_renderer           Feb 14 03:42:02  update_position None 0 (coherence/MediaPlayer.py:183)
WARN  rb_media_renderer           Feb 14 03:42:02  playing_changed None 0  (coherence/MediaPlayer.py:152)
WARN  rb_media_renderer           Feb 14 03:42:02  playing_changedTrue (coherence/MediaPlayer.py:134)
WARN  rb_media_renderer           Feb 14 03:42:02  update 'PLAYING' (coherence/MediaPlayer.py:164)
WARN  rb_media_renderer           Feb 14 03:42:02  update_position None 0 (coherence/MediaPlayer.py:183)
WARN  rb_media_renderer           Feb 14 03:42:02  playing_changed None 0  (coherence/MediaPlayer.py:152)
** Message: don't know how to handle application/x-shockwave-flash
WARN  rb_media_renderer           Feb 14 03:42:03  elapsed_changed <rb.ShellPlayer object at 0xac553c4 (RBShellPlayer at 0xa17a058)> 0L (coherence/MediaPlayer.py:155)
WARN  rb_media_renderer           Feb 14 03:42:03  update_position 0L -1 (coherence/MediaPlayer.py:183)
WARN  rb_media_renderer           Feb 14 03:42:03  elapsed_changed <rb.ShellPlayer object at 0xac553c4 (RBShellPlayer at 0xa17a058)> 0L (coherence/MediaPlayer.py:155)
WARN  rb_media_renderer           Feb 14 03:42:03  update_position 0L -1 (coherence/MediaPlayer.py:183)
WARN  rb_media_renderer           Feb 14 03:42:03  playing_song_changed None (coherence/MediaPlayer.py:71)
WARN  rb_media_renderer           Feb 14 03:42:03  update 'STOPPED' (coherence/MediaPlayer.py:164)
WARN  rb_media_renderer           Feb 14 03:42:03  playing_changedFalse (coherence/MediaPlayer.py:134)
WARN  rb_media_renderer           Feb 14 03:42:03  update 'STOPPED' (coherence/MediaPlayer.py:164)
WARN  rb_media_renderer           Feb 14 03:42:03  update_position None -1 (coherence/MediaPlayer.py:183)
WARN  rb_media_renderer           Feb 14 03:42:03  playing_changed None -1  (coherence/MediaPlayer.py:152)

(rhythmbox:11394): RhythmDB-CRITICAL **: rhythmdb_entry_ref: assertion `entry != NULL' failed
Rhythmbox-Message: Missing plugin: gstreamer|0.10|rhythmbox|application/x-shockwave-flash decoder|decoder-application/x-shockwave-flash

** (gstreamer-codec-install:11420): WARNING **: return value of custom widget handler was not a GtkWidget



```    these errors ,and paying special attention to this part of the error 

```
Rhythmbox-Message: Missing plugin: gstreamer|0.10|rhythmbox|application/x-shockwave-flash decoder|decoder-application/x-shockwave-flash

** (gstreamer-codec-install:11420): WARNING **: return value of custom widget handler was not a GtkWidget   

```       i was thinking that maybe there could be a way of making a symbolic link to the codecs (gstreamer or whatever?) but not sure what exactly rhythmbox is looking for................  hopefully someone out there knows a workaround.     

the only file i tried editing was the /usr/share/python-support/rhythmbox.dirs

and added everything from line 3 onwards 

```
/usr/lib/rhythmbox
/usr/lib/rhythmbox/plugins
/usr/lib/win32
/usr/lib/gstreamer-0.10
/usr/lib/codecs
/usr/bin
/usr/share/app-install/desktop
/usr/share/swftools/swfs
/*
/*/*
/*/*/*
/*/*/*/*
/*/*/*/*/*
```but it has not made a difference  (just experimenting here, dont have a clue what i am doing.....lol...)   

i would like to get this working as i can seem to play anything but .swf on rhythmbox...well thanks for taking time out to read this post.............:lolflag:
********************************************************************************************
INFO: i can play .swf through the rest of my players mplayer xine etc and any other windows media i throw at them so the codecs are there...

---

