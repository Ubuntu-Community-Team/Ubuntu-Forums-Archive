---
title: "Where are Miro's feeds stored?"
date: 2007-09-23
forum: Multimedia &amp; Video
---

### Post by sleepyenglish on 2007-09-23
I'm having problems with miro where by it freezes while loading the default feeds at start up and consequently ends up freezing. I thought i would find the file which lists the default list of feeds, i cant however find the file in question. I thought it wound be in /home/user/.miro but when i delete this folder the app still freezes while loading the feeds, ive reinstalled the app as well but still no luck.

Thanks

---

### Post by scrooge_74 on 2007-09-23
the feeds Miro download i find them in /home/user/.miro/another_directory

It also freezes or crashes from time to time, it got a little better on the last update

---

### Post by aidanr on 2007-09-23
I think miro stores the feeds in it's database so it's not as easy as just opening a config file and copying them out, the latest realease 0.9.9 adds importing and exporting to opml, so if you haven't already update to 0.9.9 and use the export option.

---

### Post by sleepyenglish on 2007-09-23
Unfortunately i cant export them because the app freezs at start up, and exporting them would only copy them to a .opml would it not?

---

### Post by aidanr on 2007-09-23
of course #-o

Well these are the default feeds:
```

[http://jetset.blip.tv/?skin=rss](http://jetset.blip.tv/?skin=rss)
[http://revision3.com/diggnation/feed/quicktime-large](http://revision3.com/diggnation/feed/quicktime-large)
[http://www.democracynow.org/podcast-video.xml](http://www.democracynow.org/podcast-video.xml)
[http://podcast.msnbc.com/audio/podcast/MSNBC-NN-NETCAST-M4V.xml](http://podcast.msnbc.com/audio/podcast/MSNBC-NN-NETCAST-M4V.xml)
[http://feeds.feedburner.com/TEDTalks_video](http://feeds.feedburner.com/TEDTalks_video)
[http://feeds.feedburner.com/Terravideos](http://feeds.feedburner.com/Terravideos)
[http://feeds.feedburner.com/AskANinja](http://feeds.feedburner.com/AskANinja)
[http://feeds.feedburner.com/Theburg/](http://feeds.feedburner.com/Theburg/)
[http://feeds.theonion.com/OnionNewsNetwork](http://feeds.theonion.com/OnionNewsNetwork)
[http://www.washingtonpost.com/wp-srv/mmedia/hd_podcast.xml](http://www.washingtonpost.com/wp-srv/mmedia/hd_podcast.xml)
[http://www.telemusicvision.com/videos/rss.php](http://www.telemusicvision.com/videos/rss.php)
[http://www.spacetelescope.org/rss/vodcast.xml](http://www.spacetelescope.org/rss/vodcast.xml)

```

does it give any error when running it in the terminal?

---

### Post by sleepyenglish on 2007-09-23
> /usr/bin/miro.real:84: DeprecationWarning: The dbus_bindings module is deprecated and will go away soon.

dbus-python 0.80 provides only a partial emulation of the old
dbus_bindings, which was never meant to be public API.

Most uses of dbus_bindings are applications catching the exception
dbus.dbus_bindings.DBusException. You should use dbus.DBusException
instead (this is compatible with all dbus-python versions since 0.40.2).

If you need additional public API, please contact the maintainers via
<dbus@lists.freedesktop.org>.

  import dbus_bindings
/var/lib/python-support/python2.5/dbus_bindings.py:5: DeprecationWarning: The dbus_bindings module is deprecated and will go away soon.

dbus-python 0.80 provides only a partial emulation of the old
dbus_bindings, which was never meant to be public API.

Most uses of dbus_bindings are applications catching the exception
dbus.dbus_bindings.DBusException. You should use dbus.DBusException
instead (this is compatible with all dbus-python versions since 0.40.2).

If you need additional public API, please contact the maintainers via
<dbus@lists.freedesktop.org>.

  from dbus.dbus_bindings import *
GTK Accessibility Module initialized
INFO     Starting up Miro
INFO     Version:    0.9.9.1
INFO     Revision:   unknown
INFO     Builder:    ben@pitpat
INFO     Build Time: 1189015412.11
INFO     Loading preferences...
INFO     Starting event loop thread
INFO     Restoring database...
INFO     Connecting to /home/mark/.miro/sqlitedb
INFO     Spawning global feed dtv:manualFeed
INFO     Spawning global feed dtv:singleFeed
INFO     Spawning global feed dtv:search
INFO     Spawning global feed dtv:searchDownloads
INFO     Creating channel tab order
INFO     Creating playlist tab order
INFO     Spawning Miro Guide...
(u'News and Tech', [u'http://jetset.blip.tv/?skin=rss', u'http://revision3.com/diggnation/feed/quicktime-large', u'http://www.democracynow.org/podcast-video.xml', u'http://podcast.msnbc.com/audio/podcast/MSNBC-NN-NETCAST-M4V.xml', u'http://feeds.feedburner.com/TEDTalks_video'])
(u'Entertainment', [u'http://feeds.feedburner.com/Terravideos', u'http://feeds.feedburner.com/AskANinja', u'http://feeds.feedburner.com/Theburg/', u'http://feeds.theonion.com/OnionNewsNetwork'])
(u'High-Def', [u'http://www.washingtonpost.com/wp-srv/mmedia/hd_podcast.xml', u'http://www.telemusicvision.com/videos/rss.php', u'http://www.spacetelescope.org/rss/vodcast.xml'])
INFO     Spawning global feed dtv:directoryfeed
INFO     Spawning auto downloader...
INFO     Displaying main frame...
INFO     *** Launching Downloader Daemon ****
WARNING  Menu item action "RenameVideo" not implemented
WARNING  Menu item action "FastForward" not implemented
WARNING  Menu item action "Rewind" not implemented
WARNING  Menu item action "UpVolume" not implemented
WARNING  Menu item action "DownVolume" not implemented
WARNING  Volume changed before videoDisplay created
WARNING  Display updated before video display was created
INFO     Creating video display...
alsa
oss
pulseaudio
arts
esd
none
file
INFO     loaded renderer 'xinerenderer'
TIMING   gtkAsyncMethod: <function initRenderers at 0x89f2ca4> took too long: 1.102
TIMING   gtkSyncMethod: <function getDisplay at 0x8aa4f44> took too long: 1.157
TIMING   Icon clear: 0.196
INFO     Finished startup sequence
TIMING   idle (finalizing startup) too slow (1.911 secs)
INFO     got file:///tmp/tmpeNMS42.html
INFO     got file:///tmp/tmpC15Hai.html


I'm not sure what a error might look like(unless of course it would say error?) so above is the terminal output.

---

### Post by aidanr on 2007-09-23
Yeah I don't see anything obvious there, the only real difference between yours and mine is it says:
INFO ***Daemon Ready***
after
TIMING idle (finalizing startup) too slow (1.911 secs)

You could try building from [source]("https://develop.participatoryculture.org/trac/democracy/wiki/GTKX11BuildDocs"), see if that makes a difference, other than that I haven't a clue.

---

### Post by sleepyenglish on 2007-09-23
Ok thanks for attempting to help thought i appreciate it.

---

### Post by sleepyenglish on 2007-09-23
I have since removed Miro and reverted to Democracy player from the repo and it work for a few minutes but again it freezes, i guess my laptop doesn't like either.

---

