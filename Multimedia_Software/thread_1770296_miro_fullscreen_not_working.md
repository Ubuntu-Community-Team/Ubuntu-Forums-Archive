---
title: "miro fullscreen not working"
date: 2011-05-29
forum: Multimedia Software
---

### Post by higashi on 2011-05-29
When trying to make a video fullscreen in miro, i get this crash report:

```
{{{
App:        Miro
Publisher:  Participatory Culture Foundation
Platform:   linux
Python:     2.7.1+ (r271:86832, Apr 11 2011, 18:13:53)  [GCC 4.5.2]
Py Path:    ['/usr/bin', '/usr/lib/python2.7/dist-packages/gst-0.10', '/usr/share/miro/resources/extensions', '/usr/bin', '/usr/lib/python2.7', '/usr/lib/python2.7/plat-linux2', '/usr/lib/python2.7/lib-tk', '/usr/lib/python2.7/lib-old', '/usr/lib/python2.7/lib-dynload', '/usr/local/lib/python2.7/dist-packages', '/usr/lib/python2.7/dist-packages', '/usr/lib/python2.7/dist-packages/PIL', '/usr/lib/pymodules/python2.7/gtk-2.0', '/usr/lib/python2.7/dist-packages/gtk-2.0', '/usr/lib/pymodules/python2.7', '/usr/lib/pymodules/python2.7/ubuntuone-control-panel', '/usr/lib/pymodules/python2.7/ubuntuone-client', '/usr/lib/pymodules/python2.7/ubuntuone-storage-protocol']
Version:    4.0.1
Serial:     20110524000
Revision:   ssh://wguaraldi@git.participatoryculture.org:2191/var/git/miro - 90022384
Builder:    buildd@dubnium
Build Time: 1306423201.62
Time:       Sun May 29 02:37:39 2011
When:       in frontend thread

Exception
---------
Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.7/miro/frontends/widgets/gtk/weakconnect.py", line 50, in handle_callback
    return real_method(obj, *(args + self.user_args))
  File "/usr/lib/pymodules/python2.7/miro/frontends/widgets/gtk/video.py", line 637, in on_button_press
    app.playback_manager.toggle_fullscreen()
  File "/usr/lib/pymodules/python2.7/miro/frontends/widgets/playback.py", line 628, in toggle_fullscreen
    self.enter_fullscreen()
  File "/usr/lib/pymodules/python2.7/miro/frontends/widgets/playback.py", line 633, in enter_fullscreen
    self.video_display.enter_fullscreen()
  File "/usr/lib/pymodules/python2.7/miro/frontends/widgets/displays.py", line 630, in enter_fullscreen
    self.renderer.enter_fullscreen()
  File "/usr/lib/pymodules/python2.7/miro/frontends/widgets/gtk/video.py", line 589, in enter_fullscreen
    self.screensaver_manager.disable()
  File "/usr/lib/pymodules/python2.7/miro/plat/screensaver.py", line 53, in disable
    self.cookie = obj.Inhibit(prog, reason)
  File "/usr/lib/pymodules/python2.7/dbus/proxies.py", line 68, in __call__
    return self._proxy_method(*args, **keywords)
  File "/usr/lib/pymodules/python2.7/dbus/proxies.py", line 140, in __call__
    **keywords)
  File "/usr/lib/pymodules/python2.7/dbus/connection.py", line 630, in call_blocking
    message, timeout)
DBusException: org.freedesktop.DBus.Error.UnknownMethod: Method "Inhibit" with signature "ss" on interface "(null)" doesn't exist


Call Stack
---------
  File "/usr/bin/miro.real", line 312, in <module>
    startapp()
  File "/usr/bin/miro.real", line 265, in startapp
    parsed_options.theme)
  File "/usr/lib/pymodules/python2.7/miro/startfrontend.py", line 87, in run_application
    application.run_application()
  File "/usr/lib/pymodules/python2.7/miro/plat/frontends/widgets/application.py", line 137, in run_application
    LinuxApplication().run()
  File "/usr/lib/pymodules/python2.7/miro/plat/frontends/widgets/application.py", line 176, in run
    gtk.main()
  File "/usr/lib/pymodules/python2.7/miro/frontends/widgets/application.py", line 121, in exception_handler
    exc_info=(typ, value, traceback), details=None)
  File "/usr/lib/pymodules/python2.7/miro/crashreport.py", line 70, in format_crash_report
    stack = util.get_nice_stack()
  File "/usr/lib/pymodules/python2.7/miro/util.py", line 74, in get_nice_stack
    stack = traceback.extract_stack()

Threads
-------
Current: MainThread
Active:
 - MainThread
 - LibCURL Event Loop
 - mDNS Browser Thread
 - ThreadPool - 1 [Daemon]
 - ThreadPool - 0 [Daemon]
 - Movie Data Thread [Daemon]
 - Event Loop
 - ThreadPool - 2 [Daemon]
ENDHEADERS
}}}
{{{
Log
---
2011-05-29 02:37:22,146 INFO     root: Starting up Miro
2011-05-29 02:37:22,147 INFO     root: Version:    4.0.1
2011-05-29 02:37:22,147 INFO     root: Revision:   ssh://wguaraldi@git.participatoryculture.org:2191/var/git/miro - 90022384
2011-05-29 02:37:22,147 INFO     root: Builder:    buildd@dubnium
2011-05-29 02:37:22,148 INFO     root: Build Time: 1306423201.62
2011-05-29 02:37:22,148 INFO     root: Debugmode:  False
2011-05-29 02:37:22,148 INFO     root: Reading HTTP Password list
2011-05-29 02:37:22,148 INFO     root: Starting libCURL thread
2011-05-29 02:37:22,151 INFO     root: Starting event loop thread
2011-05-29 02:37:22,152 INFO     root: Restoring database...
2011-05-29 02:37:22,152 INFO     root: Loading core extensions in /usr/share/miro/resources/extensions
2011-05-29 02:37:22,153 INFO     root: Sqlite3 version:   3.7.4
2011-05-29 02:37:22,153 INFO     root: Pysqlite version:  2.6.0
2011-05-29 02:37:22,155 INFO     root: opening database /home/george/.miro/sqlitedb
2011-05-29 02:37:22,156 INFO     root: Loading user extensions in /home/george/.miro/extensions
2011-05-29 02:37:22,163 INFO     root: Linux version:     Linux 2.6.38-9-generic x86_64
2011-05-29 02:37:22,164 INFO     root: Python version:    2.7.1+ (r271:86832, Apr 11 2011, 18:13:53) 
[GCC 4.5.2]
2011-05-29 02:37:22,164 INFO     root: Gtk+ version:      (2, 24, 4)
2011-05-29 02:37:22,165 INFO     root: PyGObject version: (2, 28, 3)
2011-05-29 02:37:22,165 INFO     root: PyGtk version:     (2, 22, 0)
2011-05-29 02:37:22,166 TIMING   root: Database upgrade time: 0.013
2011-05-29 02:37:22,166 INFO     root: Language:          [('LANGUAGE', 'en_CA:en')]
2011-05-29 02:37:22,187 INFO     root: libtorrent:        0.15.5.0
2011-05-29 02:37:22,188 INFO     root: pycurl:            libcurl/7.21.3 GnuTLS/2.8.6 zlib/1.2.3.4 libidn/1.18
2011-05-29 02:37:22,221 INFO     root: GStreamer version: GStreamer 0.10.32
2011-05-29 02:37:22,222 DBLOG    root: start database log entries
2011-05-29 02:37:22,223 DBLOG    root: * Sat May 28 21:36:55 2011: Upgraded database from version 119 to 159
2011-05-29 02:37:22,223 DBLOG    root: * Sat May 28 21:38:30 2011: Removed IconCache objects without an associated db object: None
2011-05-29 02:37:22,224 DBLOG    root: end database log entries
2011-05-29 02:37:22,227 INFO     root: GStreamer audiosink: gconfaudiosink
2011-05-29 02:37:22,237 INFO     root: GStreamer videosink: gconfvideosink
2011-05-29 02:37:22,239 INFO     root: GStreamer version: GStreamer 0.10.32
2011-05-29 02:37:22,241 INFO     root: GStreamer audiosink: gconfaudiosink
2011-05-29 02:37:22,243 INFO     root: set_renderer: successfully loaded gstreamerrenderer
2011-05-29 02:37:22,772 INFO     root: Loading video converters...
2011-05-29 02:37:22,803 INFO     root: setup tabs...
2011-05-29 02:37:22,808 INFO     root: setup theme...
2011-05-29 02:37:22,849 INFO     root: Checking movies directory '/home/george/Videos/Miro/'...
2011-05-29 02:37:25,806 INFO     root: Starting auto downloader...
2011-05-29 02:37:25,837 INFO     root: this platform has autoupdate disabled.  skipping.
2011-05-29 02:37:34,921 WARNING  root: not reselecting
2011-05-29 02:37:35,482 WARNING  root: not reselecting

Downloader Log
---
2011-05-29 02:37:30,963 INFO     root: Launching Downloader Daemon
2011-05-29 02:37:30,987 INFO     root: libtorrent: 0.15.5.0
2011-05-29 02:37:30,991 INFO     root: pycurl:     libcurl/7.21.3 GnuTLS/2.8.6 zlib/1.2.3.4 libidn/1.18
2011-05-29 02:37:31,031 INFO     root: Starting downloaders
2011-05-29 02:37:31,035 INFO     root: Daemon ready
}}}

```

I'm running Miro 4.0.1 on ubuntu 11.10 and Gnome 3.0.2

---

### Post by higashi on 2011-05-30
bump

---

### Post by higashi on 2011-06-01
buuuuump

---

### Post by higashi on 2011-06-04
bumpbumpbumpbump

---

### Post by higashi on 2011-06-13
bump

---

### Post by ill2029 on 2011-09-29
I got exact same problem. Did you have any luck with finding a solution?

Cheers.):P

This is my report:
```

{{{
App:        Miro
Publisher:  Participatory Culture Foundation
Platform:   linux
Python:     2.7.1+ (r271:86832, Apr 11 2011, 18:05:24)  [GCC 4.5.2]
Py Path:    ['/usr/bin', '/usr/lib/python2.7/dist-packages/gst-0.10', '/usr/share/miro/resources/extensions', '/usr/bin', '/usr/lib/python2.7', '/usr/lib/python2.7/plat-linux2', '/usr/lib/python2.7/lib-tk', '/usr/lib/python2.7/lib-old', '/usr/lib/python2.7/lib-dynload', '/usr/local/lib/python2.7/dist-packages', '/usr/lib/python2.7/dist-packages', '/usr/lib/python2.7/dist-packages/PIL', '/usr/lib/pymodules/python2.7/gtk-2.0', '/usr/lib/python2.7/dist-packages/gtk-2.0', '/usr/lib/pymodules/python2.7', '/usr/lib/pymodules/python2.7/ubuntuone-client', '/usr/lib/pymodules/python2.7/ubuntuone-control-panel', '/usr/lib/pymodules/python2.7/ubuntuone-storage-protocol', '/usr/lib/python2.7/dist-packages/ubuntu-sso-client', '/usr/lib/python2.7/dist-packages/wx-2.8-gtk2-unicode']
Version:    4.0.3
Serial:     20110810000
Revision:   ssh://wguaraldi@git.participatoryculture.org:2191/var/git/miro - 82931155
Builder:    buildd@samarium
Build Time: 1313156433.71
Time:       Thu Sep 29 20:17:52 2011
When:       in frontend thread

Exception
---------
Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.7/miro/frontends/widgets/gtk/weakconnect.py", line 50, in handle_callback
    return real_method(obj, *(args + self.user_args))
  File "/usr/lib/pymodules/python2.7/miro/frontends/widgets/gtk/video.py", line 83, in on_click
    self.emit('clicked')
  File "/usr/lib/pymodules/python2.7/miro/signals.py", line 183, in emit
    callback_returned_true = self._run_signal(name, args)
  File "/usr/lib/pymodules/python2.7/miro/signals.py", line 200, in _run_signal
    if callback.invoke(self, args):
  File "/usr/lib/pymodules/python2.7/miro/signals.py", line 75, in invoke
    return self.func(obj, *(args + self.extra_args))
  File "/usr/lib/pymodules/python2.7/miro/frontends/widgets/gtk/video.py", line 365, in handle_fullscreen
    app.playback_manager.toggle_fullscreen()
  File "/usr/lib/pymodules/python2.7/miro/frontends/widgets/playback.py", line 632, in toggle_fullscreen
    self.enter_fullscreen()
  File "/usr/lib/pymodules/python2.7/miro/frontends/widgets/playback.py", line 637, in enter_fullscreen
    self.video_display.enter_fullscreen()
  File "/usr/lib/pymodules/python2.7/miro/frontends/widgets/displays.py", line 630, in enter_fullscreen
    self.renderer.enter_fullscreen()
  File "/usr/lib/pymodules/python2.7/miro/frontends/widgets/gtk/video.py", line 589, in enter_fullscreen
    self.screensaver_manager.disable()
  File "/usr/lib/pymodules/python2.7/miro/plat/screensaver.py", line 53, in disable
    self.cookie = obj.Inhibit(prog, reason)
  File "/usr/lib/pymodules/python2.7/dbus/proxies.py", line 68, in __call__
    return self._proxy_method(*args, **keywords)
  File "/usr/lib/pymodules/python2.7/dbus/proxies.py", line 140, in __call__
    **keywords)
  File "/usr/lib/pymodules/python2.7/dbus/connection.py", line 630, in call_blocking
    message, timeout)
DBusException: org.freedesktop.DBus.Error.UnknownMethod: Method "Inhibit" with signature "ss" on interface "(null)" doesn't exist


Call Stack
---------
  File "/usr/bin/miro.real", line 312, in <module>
    startapp()
  File "/usr/bin/miro.real", line 265, in startapp
    parsed_options.theme)
  File "/usr/lib/pymodules/python2.7/miro/startfrontend.py", line 87, in run_application
    application.run_application()
  File "/usr/lib/pymodules/python2.7/miro/plat/frontends/widgets/application.py", line 137, in run_application
    LinuxApplication().run()
  File "/usr/lib/pymodules/python2.7/miro/plat/frontends/widgets/application.py", line 176, in run
    gtk.main()
  File "/usr/lib/pymodules/python2.7/miro/frontends/widgets/application.py", line 121, in exception_handler
    exc_info=(typ, value, traceback), details=None)
  File "/usr/lib/pymodules/python2.7/miro/crashreport.py", line 63, in format_crash_report
    header += format_stack_report(details, exc_info)
  File "/usr/lib/pymodules/python2.7/miro/crashreport.py", line 128, in format_stack_report
    stack = util.get_nice_stack()
  File "/usr/lib/pymodules/python2.7/miro/util.py", line 74, in get_nice_stack
    stack = traceback.extract_stack()

Threads
-------
Current: MainThread
Active:
 - MainThread
 - Event Loop
 - mDNS Browser Thread
 - Thread-1 [Daemon]
 - ThreadPool - 0 [Daemon]
 - Movie Data Thread [Daemon]
 - LibCURL Event Loop
 - ThreadPool - 2 [Daemon]
 - ThreadPool - 1 [Daemon]
ENDHEADERS
}}}
{{{
Log

```

---

### Post by 4zdenek on 2011-10-14
I've upgraded to 11.10 just now and have the same problem.

---

### Post by Karolis on 2011-10-14
I have the same issue, though just confirming that won't help anyone :)

Please go and click "It affects me too" on the bug report [https://bugs.launchpad.net/ubuntu/+source/miro/+bug/871123](https://bugs.launchpad.net/ubuntu/+source/miro/+bug/871123)

---

