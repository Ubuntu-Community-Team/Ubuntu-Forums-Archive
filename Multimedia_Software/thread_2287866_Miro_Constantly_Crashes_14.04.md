---
title: "Miro Constantly Crashes 14.04"
date: 2015-07-22
forum: Multimedia Software
---

### Post by coljohnhannibalsmith on 2015-07-22
Hello,

Miro constantly crashes in 14.04.  Miro uses VLC as its Video Engine.  I had a similar problem with an earlier version of Miro and was able to resolve it by installing a VLC video server from Synaptic Package Manager.  Synaptic no longer has this item in the repository.  Perhaps this feature has been incorporated into VLC, so that it is no longer necessary to add it separately.

Here's the terminal output:

```
sophie@sophie-Inspiron-1545:~$ miro
using /usr/bin/miro.real
2015-07-22 18:27:26,404 INFO     root: Starting up Miro
2015-07-22 18:27:26,405 INFO     root: Version:    4.0.4
2015-07-22 18:27:26,406 INFO     root: Revision:   git@github.com:pculture/miro.git - 284c92ad
2015-07-22 18:27:26,406 INFO     root: Builder:    buildd@akateko
2015-07-22 18:27:26,407 INFO     root: Build Time: 1385083413.99
2015-07-22 18:27:26,408 INFO     root: Debugmode:  False
2015-07-22 18:27:26,408 INFO     root: Reading HTTP Password list
2015-07-22 18:27:26,436 INFO     root: Starting libCURL thread
2015-07-22 18:27:26,440 INFO     root: Starting event loop thread
2015-07-22 18:27:26,441 INFO     root: Installing deleted file checker...
2015-07-22 18:27:26,443 INFO     root: Loading core extensions in /usr/share/miro/resources/extensions
2015-07-22 18:27:26,443 INFO     root: Restoring database...
2015-07-22 18:27:26,444 INFO     root: Sqlite3 version:   3.8.2
2015-07-22 18:27:26,444 INFO     root: Pysqlite version:  2.6.0
2015-07-22 18:27:26,446 INFO     root: opening database /home/sophie/.miro/sqlitedb
2015-07-22 18:27:26,509 INFO     root: Loading user extensions in /home/sophie/.miro/extensions
2015-07-22 18:27:26,516 INFO     root: Linux version:     Linux 3.16.0-44-generic x86_64
2015-07-22 18:27:26,516 INFO     root: Python version:    2.7.6 (default, Jun 22 2015, 17:58:13) 
[GCC 4.8.2]
2015-07-22 18:27:26,517 INFO     root: Gtk+ version:      (2, 24, 23)
2015-07-22 18:27:26,517 INFO     root: PyGObject version: (2, 28, 6)
2015-07-22 18:27:26,517 INFO     root: PyGtk version:     (2, 24, 0)
2015-07-22 18:27:26,518 INFO     root: Language:          [('LANGUAGE', 'en_US'), ('LANG', 'en_US.UTF-8')]
2015-07-22 18:27:26,725 INFO     root: libtorrent:        0.16.13.0
2015-07-22 18:27:26,725 INFO     root: pycurl:            PycURL/7.19.3 libcurl/7.35.0 GnuTLS/2.12.23 zlib/1.2.8 libidn/1.28 librtmp/2.3
2015-07-22 18:27:27,122 INFO     root: GStreamer version: GStreamer 0.10.36
2015-07-22 18:27:27,175 INFO     root: GStreamer audiosink: gconfaudiosink
2015-07-22 18:27:27,177 INFO     root: GStreamer videosink: gconfvideosink
2015-07-22 18:27:27,178 INFO     root: GStreamer version: GStreamer 0.10.36
2015-07-22 18:27:27,179 INFO     root: GStreamer audiosink: gconfaudiosink
2015-07-22 18:27:27,179 INFO     root: set_renderer: successfully loaded gstreamerrenderer
2015-07-22 18:27:27,188 TIMING   root: Database upgrade time: 0.744
2015-07-22 18:27:27,620 INFO     root: Loading video converters...
2015-07-22 18:27:27,735 INFO     root: setup tabs...
2015-07-22 18:27:27,741 INFO     root: setup theme...
2015-07-22 18:27:27,883 INFO     root: Checking movies directory '/home/sophie/.miro/Movies/'...
java version "1.7.0_79"
OpenJDK Runtime Environment (IcedTea 2.5.5) (7u79-2.5.5-0ubuntu0.14.04.2)
OpenJDK 64-Bit Server VM (build 24.79-b02, mixed mode)
2015-07-22 18:27:34,828 INFO     root: Starting auto downloader...
2015-07-22 18:27:34,847 INFO     root: this platform has the built-in autoupdate parser disabled.  Skipping.
2015-07-22 18:27:40,067 INFO     root: Launching Downloader Daemon
2015-07-22 18:27:40,082 INFO     root: libtorrent: 0.16.13.0
2015-07-22 18:27:40,089 INFO     root: pycurl:     PycURL/7.19.3 libcurl/7.35.0 GnuTLS/2.12.23 zlib/1.2.8 libidn/1.28 librtmp/2.3
2015-07-22 18:27:40,131 INFO     root: Starting downloaders
2015-07-22 18:27:40,240 INFO     root: Daemon ready
2015-07-22 18:27:53,038 WARNING  root: Error downloading guide: <class 'miro.net.ConnectionTimeout'>: Error: Timeout -- Connection to www.clearbits.net timed out
/usr/lib/pymodules/python2.7/miro/plat/frontends/widgets/application.py:176: Warning: cannot register existing type 'GstObject'
  gtk.main()
/usr/lib/pymodules/python2.7/miro/plat/frontends/widgets/application.py:176: Warning: g_once_init_leave: assertion 'result != 0' failed
  gtk.main()
/usr/lib/pymodules/python2.7/miro/plat/frontends/widgets/application.py:176: Warning: g_type_register_static: assertion 'parent_type > 0' failed
  gtk.main()
/usr/lib/pymodules/python2.7/miro/plat/frontends/widgets/application.py:176: Warning: g_object_new: assertion 'G_TYPE_IS_OBJECT (object_type)' failed
  gtk.main()

(miro.real:2704): GStreamer-CRITICAL **: gst_object_ref: assertion 'object != NULL' failed

(miro.real:2704): GStreamer-CRITICAL **: gst_allocator_register: assertion 'allocator != NULL' failed

(miro.real:2704): GStreamer-CRITICAL **: gst_object_ref: assertion 'object != NULL' failed
/usr/lib/pymodules/python2.7/miro/plat/frontends/widgets/application.py:176: Warning: cannot register existing type 'GstFormat'
  gtk.main()
/usr/lib/pymodules/python2.7/miro/plat/frontends/widgets/application.py:176: Warning: cannot retrieve class for invalid (unclassed) type '<invalid>'
  gtk.main()
/usr/lib/pymodules/python2.7/miro/plat/frontends/widgets/application.py:176: Warning: g_boxed_type_register_static: assertion 'g_type_from_name (name) == 0' failed
  gtk.main()
2015-07-22 18:28:04,858 INFO     root: Watching directory /home/sophie/.miro/Movies with class <class 'miro.frontends.widgets.gtk.gtkdirectorywatch.GTKDirectoryWatcher'>

```

Thanks, Hannibal

---

### Post by mc4man on 2015-07-23
miro works here in 14.04 to the extent a project that hasn't updated in 2+ yrs. can work (most of it's listed Sources are broken...
Maybe delete ~/.miro & start over

---

### Post by coljohnhannibalsmith on 2015-07-23
Is there another Internet TV app that you would recommend, perhaps one better than Miro?  I'm willing to pay a fair price for a decent app, if necessary.

Thanks, Hannibal

---

### Post by mc4man on 2015-07-24
If you mean tv in the traditional sense there is netflix, amazon, hulu. You pay them, they provide protected content is some fashion..

---

### Post by coljohnhannibalsmith on 2015-07-24
Web or Live TV for free, streamed over the web.

Thanks, Hannibal

---

