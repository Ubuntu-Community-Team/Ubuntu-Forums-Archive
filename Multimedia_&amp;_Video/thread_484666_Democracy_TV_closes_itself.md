---
title: "Democracy TV closes itself"
date: 2007-06-26
forum: Multimedia &amp; Video
---

### Post by Taleman on 2007-06-26
I installed Democracy TV on Feisty and i,m not having anyproblems except that after i stop playing a media file Democracy TV automatically closes itself.


Here a copy of the terminal output if it helps:

antonio@antonio-laptop:~$ democracyplayer %F
/usr/bin/democracyplayer.real:81: DeprecationWarning: The dbus_bindings module is deprecated and will go away soon.

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
INFO     Starting up Democracy Player
INFO     Version:  0.9.6
INFO     Revision: unknown
INFO     Loading preferences...
INFO     Starting event loop thread
INFO     Restoring database...
INFO     Connecting to /home/antonio/.democracy/sqlitedb
TIMING   Database load slow: 1.102
INFO     Recomputing filters...
INFO     Spawning auto downloader...
INFO     Displaying main frame...
WARNING  Menu item action "CheckVersion" not implemented
WARNING  Menu item action "FastForward" not implemented
WARNING  Menu item action "Rewind" not implemented
WARNING  Menu item action "UpVolume" not implemented
WARNING  Menu item action "DownVolume" not implemented
WARNING  Volume changed before videoDisplay created
WARNING  Display updated before video display was created
INFO     *** Launching Downloader Daemon ****
INFO     Creating video display...
alsa
oss
pulseaudio
none
file
INFO     loaded renderer 'xinerenderer'
TIMING   gtkAsyncMethod: <function initRenderers at 0x89712cc> took too long: 1.289
INFO     Setting VolumeLevel to 1.0
TIMING   Icon clear: 0.013
INFO     Finished startup sequence
TIMING   idle (Finishing startup) too slow (4.047 secs)
INFO     *** Daemon ready ***
INFO     got file:///tmp/tmpJ9iLBS.html
INFO     got file:///tmp/tmpTrH43V.html
INFO     got [https://channelguide.participatoryculture.org/](https://channelguide.participatoryculture.org/)
INFO     got [https://channelguide.participatoryculture.org/front](https://channelguide.participatoryculture.org/front)
LoadPlugin: failed to initialize shared library /usr/lib/jvm/java-6-sun-1.6.0.00/jre/plugin/i386/ns7/libjavaplugin_oji.so [/usr/lib/jvm/java-6-sun-1.6.0.00/jre/plugin/i386/ns7/libjavaplugin_oji.so: undefined symbol: _ZTVN10__cxxabiv121__vmi_class_type_infoE]
TIMING   feed update for: [http://www.youtube.com/rss/tag/Shevchenko.rss](http://www.youtube.com/rss/tag/Shevchenko.rss) too slow (0.316 secs)
TIMING   feed update for: [http://www.tvo.org/TVOspecial3/WebObjects/TVOMedia.woa?AgendaVideoFeed](http://www.tvo.org/TVOspecial3/WebObjects/TVOMedia.woa?AgendaVideoFeed) too slow (0.159 secs)
TIMING   feed update for: [http://jetset.blip.tv/?skin=rss](http://jetset.blip.tv/?skin=rss) too slow (0.104 secs)
TIMING   timeout (Save database) too slow (0.622 secs)
TIMING   feed update for: [http://geekbrief.podshow.com/feed.xml](http://geekbrief.podshow.com/feed.xml) too slow (0.360 secs)
TIMING   feed update for: [http://revision3.com/diggnation/feed/quicktime-large](http://revision3.com/diggnation/feed/quicktime-large) too slow (0.326 secs)
TIMING   feed update for: [http://feeds.feedburner.com/Terravideos](http://feeds.feedburner.com/Terravideos) too slow (0.708 secs)
TIMING   idle (Thread Pool Callback (Feedparser callback - [http://feeds.feedburner.com/Terravideos](http://feeds.feedburner.com/Terravideos))) too slow (0.708 secs)
TIMING   feed update for: [http://revision3.com/pixelperfect/feed/quicktime-high-definition](http://revision3.com/pixelperfect/feed/quicktime-high-definition) too slow (0.155 secs)
TIMING   feed update for: [http://www.smallcarrot.com/podcast.php](http://www.smallcarrot.com/podcast.php) too slow (0.186 secs)
INFO     got action:handleSelect?area=tablist&viewName=staticTabs&id=809&shiftDown=0&ctrlDown=0
INFO     got file:///tmp/tmpKbeta2.html
INFO     got action:playViewNamed?viewName=matchingItems&firstItemId=758
INFO     Playing item with renderer: <frontend_implementation.xinerenderer.Renderer instance at 0x98c840c>
INFO     got file:///tmp/tmpewkt2F.html
/var/lib/python-support/python2.5/democracy/frontend_implementation/Application.py:28: Warning: invalid cast from `GtkMozEmbed' to `GtkWindow'
  gtk.main()
/var/lib/python-support/python2.5/democracy/frontend_implementation/Application.py:28: GtkWarning: gtk_window_set_transient_for: assertion `parent == NULL || GTK_IS_WINDOW (parent)' failed
  gtk.main()
TIMING   timeout (Save database) too slow (0.823 secs)
INFO     Playing item with renderer: <frontend_implementation.xinerenderer.Renderer instance at 0x98c840c>
INFO     got file:///tmp/tmp02hdTg.html
DTV: Warning: Can't process cookie expiration: Sun, 17-Jan-2038 19:14:07 GMT
DTV: Warning: Can't process cookie expiration: Sun, 17-Jan-2038 19:14:07 GMT
DTV: Warning: Can't process cookie expiration: Sun, 17-Jan-2038 19:14:07 GMT
DTV: Warning: Can't process cookie expiration: Sun, 17-Jan-2038 19:14:07 GMT
DTV: Warning: Can't process cookie expiration: Sun, 17-Jan-2038 19:14:07 GMT
DTV: Warning: Can't process cookie expiration: Sun, 17-Jan-2038 19:14:07 GMT
DTV: Warning: Can't process cookie expiration: Sun, 17-Jan-2038 19:14:07 GMT
DTV: Warning: Can't process cookie expiration: Sun, 17-Jan-2038 19:14:07 GMT
DTV: Warning: Can't process cookie expiration: Sun, 17-Jan-2038 19:14:07 GMT
DTV: Warning: Can't process cookie expiration: Sun, 17-Jan-2038 19:14:07 GMT
DTV: Warning: Can't process cookie expiration: Sun, 17-Jan-2038 19:14:07 GMT
DTV: Warning: Can't process cookie expiration: Sun, 17-Jan-2038 19:14:07 GMT
DTV: Warning: Can't process cookie expiration: Sun, 17-Jan-2038 19:14:07 GMT
DTV: Warning: Can't process cookie expiration: Sun, 17-Jan-2038 19:14:07 GMT
DTV: Warning: Can't process cookie expiration: Sun, 17-Jan-2038 19:14:07 GMT
DTV: Warning: Can't process cookie expiration: Sun, 17-Jan-2038 19:14:07 GMT
DTV: Warning: Can't process cookie expiration: Sun, 17-Jan-2038 19:14:07 GMT
DTV: Warning: Can't process cookie expiration: Sun, 17-Jan-2038 19:14:07 GMT
DTV: Warning: Can't process cookie expiration: Sun, 17-Jan-2038 19:14:07 GMT
DTV: Warning: Can't process cookie expiration: Sun, 17-Jan-2038 19:14:07 GMT
DTV: Warning: Can't process cookie expiration: Sun, 17-Jan-2038 19:14:07 GMT
DTV: Warning: Can't process cookie expiration: Sun, 17-Jan-2038 19:14:07 GMT
DTV: Warning: Can't process cookie expiration: Sun, 17-Jan-2038 19:14:07 GMT
DTV: Warning: Can't process cookie expiration: Sun, 17-Jan-2038 19:14:07 GMT
DTV: Warning: Can't process cookie expiration: Sun, 17-Jan-2038 19:14:07 GMT
INFO     Playing item with renderer: <frontend_implementation.xinerenderer.Renderer instance at 0x98c840c>
INFO     got file:///tmp/tmpBt9xb8.html
INFO     got action:handleSelect?area=tablist&viewName=staticTabs&id=809&shiftDown=0&ctrlDown=0
The program 'Gecko' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 10574 error_code 8 request_code 141 minor_code 13)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
WARNING  downloader: connection closed -- quitting
INFO     Shutting down downloaders...
antonio@antonio-laptop:~$

---

### Post by jenhsun on 2007-07-01
1. remove ubuntu-restricted-extra which contains Java6-Sun-bin, jre and plugin
2. sudo gedit /usr/share/python-support/democracyplayer/democracy/frontend_implementation/VideoDisplay.py

Find the line that says:

# self.add_renderer("gstrenderer")

And remove the # at the beginning of it, so it should look like:

self.add_renderer("gstrenderer")

The comment out the line that says

self.add_renderer("xinerenderer")

So that is looks like this:

#  self.add_renderer("xinerenderer")

Save the file, Done

---

### Post by quicksilver1024 on 2007-07-08
EDIT: I take what i said back...it works beautifully :)
Thanks

---

