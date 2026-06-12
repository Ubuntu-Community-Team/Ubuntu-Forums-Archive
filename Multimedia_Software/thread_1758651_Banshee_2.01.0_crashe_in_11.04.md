---
title: "Banshee 2.0/1.0 crashe in 11.04"
date: 2011-05-14
forum: Multimedia Software
---

### Post by insanekat on 2011-05-14
Every time I open Banshee on Ubuntu 11.04, I get a Fatal Error. It just happened all of a sudden on both 2.0.0 and 2.1.0. 
Here's the error message:

Fatal Error
Exception has been thrown by the target of an invocation.
```
An unhandled exception was thrown: Sqlite error 266: disk I/O error (SQL: SELECT COUNT(*), SUM(CoreTracks.FileSize), SUM(CoreTracks.Duration) FROM CoreTracks CROSS JOIN CoreArtists,CoreAlbums WHERE CoreArtists.ArtistID = CoreTracks.ArtistID AND CoreAlbums.AlbumID = CoreTracks.AlbumID  AND CoreTracks.PrimarySourceID = 1 )

  at Hyena.Data.Sqlite.Connection.CheckError (Int32 errorCode, System.String sql) [0x00000] in <filename unknown>:0 
  at Hyena.Data.Sqlite.Statement.CheckError (Int32 code) [0x00000] in <filename unknown>:0 
  at Hyena.Data.Sqlite.QueryReader.Read () [0x00000] in <filename unknown>:0 
  at Hyena.Data.Sqlite.ArrayDataReader..ctor (IDataReader reader, System.String sql) [0x00000] in <filename unknown>:0 
  at Hyena.Data.Sqlite.HyenaSqliteCommand.Execute (Hyena.Data.Sqlite.HyenaSqliteConnection hconnection, Hyena.Data.Sqlite.Connection connection) [0x00000] in <filename unknown>:0 
Exception has been thrown by the target of an invocation.

  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] in <filename unknown>:0 
  at System.Reflection.MonoCMethod.Invoke (BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] in <filename unknown>:0 
  at System.Reflection.ConstructorInfo.Invoke (System.Object[] parameters) [0x00000] in <filename unknown>:0 
  at System.Activator.CreateInstance (System.Type type, Boolean nonPublic) [0x00000] in <filename unknown>:0 
  at System.Activator.CreateInstance (System.Type type) [0x00000] in <filename unknown>:0 
  at Banshee.Gui.GtkBaseClient.Startup () [0x00000] in <filename unknown>:0 
  at Hyena.Gui.CleanRoomStartup.Startup (Hyena.Gui.StartupInvocationHandler startup) [0x00000] in <filename unknown>:0 

.NET Version: 2.0.50727.1433
OS Version: Unix 2.6.38.8

Assembly Version Information:

gkeyfile-sharp (1.0.0.0)
Banshee.AudioCd (2.1.0.0)
Banshee.CoverArt (2.1.0.0)
notify-sharp (0.4.0.0)
Banshee.NotificationArea (2.1.0.0)
Migo (2.1.0.0)
Banshee.Emusic (2.1.0.0)
Banshee.Mpris (2.1.0.0)
Banshee.LastfmStreaming (2.1.0.0)
Lastfm (2.1.0.0)
Banshee.Daap (2.1.0.0)
Banshee.Dap (2.1.0.0)
Banshee.MultimediaKeys (2.1.0.0)
Banshee.Bpm (2.1.0.0)
Banshee.Lastfm (2.1.0.0)
Banshee.WebBrowser (2.1.0.0)
Banshee.Wikipedia (2.1.0.0)
pango-sharp (2.12.0.0)
Banshee.Fixup (2.1.0.0)
Banshee.Widgets (2.1.0.0)
gio-sharp (2.14.0.0)
gudev-sharp (1.0.0.0)
Banshee.Gio (2.1.0.0)
Banshee.GStreamer (2.1.0.0)
System.Configuration (2.0.0.0)
dbus-sharp-glib (1.0.0.0)
gconf-sharp (2.24.0.0)
Banshee.Gnome (2.1.0.0)
Banshee.NowPlaying (2.1.0.0)
Mono.Cairo (2.0.0.0)
System.Xml (2.0.0.0)
Banshee.Core (2.1.0.0)
Hyena.Data.Sqlite (2.1.0.0)
gdk-sharp (2.12.0.0)
Mono.Addins (0.4.0.0)
atk-sharp (2.12.0.0)
Hyena.Gui (2.1.0.0)
Mono.Posix (2.0.0.0)
gtk-sharp (2.12.0.0)
Banshee.ThickClient (2.1.0.0)
Nereid (2.1.0.0)
DBus.Proxies (0.0.0.0)
System.Core (3.5.0.0)
Hyena (2.1.0.0)
dbus-sharp (1.0.0.0)
glib-sharp (2.12.0.0)
System (2.0.0.0)
Banshee.Services (2.1.0.0)
Banshee (2.1.0.0)
mscorlib (2.0.0.0)

Platform Information: Linux 2.6.38-8-generic i686 i386 GNU/Linux

Disribution Information:

[/etc/lsb-release]
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.04
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu 11.04"

[/etc/debian_version]
squeeze/sid


```

---

### Post by directhex on 2011-05-15
IO error implies a broken DB. Try: [http://kenno.wordpress.com/2010/09/28/banshee-crashes-the-database-disk-image-is-malformed/](http://kenno.wordpress.com/2010/09/28/banshee-crashes-the-database-disk-image-is-malformed/)

---

### Post by insanekat on 2011-05-15
Thank you! I'll remember that for future.

---

