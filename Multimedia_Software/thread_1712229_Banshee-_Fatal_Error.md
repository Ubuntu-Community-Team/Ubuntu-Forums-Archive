---
title: "Banshee- Fatal Error"
date: 2011-03-22
forum: Multimedia Software
---

### Post by heddleston on 2011-03-22
hey guys, i was able to install Banshee and it worked the first few times i ran it, but now i get a fatal error.

> An unhandled exception was thrown: Object reference not set to an instance of an object

  at Hyena.Data.Sqlite.SqliteModelCache`1[Banshee.Collection.Database.DatabaseArtistInfo].CheckCacheTable () [0x00000] in <filename unknown>:0 
  at Hyena.Data.Sqlite.SqliteModelCache`1[Banshee.Collection.Database.DatabaseArtistInfo]..ctor (Hyena.Data.Sqlite.HyenaSqliteConnection connection, System.String uuid, ICacheableDatabaseModel model, Hyena.Data.Sqlite.SqliteModelProvider`1 provider) [0x00000] in <filename unknown>:0 
  at Banshee.Database.BansheeModelCache`1[Banshee.Collection.Database.DatabaseArtistInfo]..ctor (Hyena.Data.Sqlite.HyenaSqliteConnection connection, System.String uuid, ICacheableDatabaseModel model, Hyena.Data.Sqlite.SqliteModelProvider`1 provider) [0x00000] in <filename unknown>:0 
  at Banshee.Collection.Database.DatabaseFilterListModel`2[T,U]..ctor (System.String name, System.String label, Banshee.Sources.DatabaseSource source, Banshee.Collection.Database.DatabaseTrackListModel trackModel, Hyena.Data.Sqlite.HyenaSqliteConnection connection, Hyena.Data.Sqlite.SqliteModelProvider`1 provider, .U selectAllItem, System.String uuid) [0x00000] in <filename unknown>:0 
  at Banshee.Collection.Database.DatabaseArtistListModel..ctor (Banshee.Sources.DatabaseSource source, Banshee.Collection.Database.DatabaseTrackListModel trackModel, Banshee.Database.BansheeDbConnection connection, System.String uuid) [0x00000] in <filename unknown>:0 
  at Banshee.Sources.DatabaseSource+<CreateFiltersFor>c__Iterator6.MoveNext () [0x00000] in <filename unknown>:0 
  at Banshee.Sources.DatabaseSource.DatabaseSourceInitialize () [0x00000] in <filename unknown>:0 
  at Banshee.Sources.DatabaseSource..ctor (System.String generic_name, System.String name, System.String id, Int32 order, Banshee.Sources.Source parent) [0x00000] in <filename unknown>:0 
  at Banshee.Sources.DatabaseSource..ctor (System.String generic_name, System.String name, System.String id, Int32 order) [0x00000] in <filename unknown>:0 
  at Banshee.Sources.PrimarySource..ctor (System.String generic_name, System.String name, System.String id, Int32 order) [0x00000] in <filename unknown>:0 
  at Banshee.Library.LibrarySource..ctor (System.String label, System.String name, Int32 order) [0x00000] in <filename unknown>:0 
  at Banshee.Library.MusicLibrarySource..ctor () [0x00000] in <filename unknown>:0 
  at Banshee.ServiceStack.Application.Run () [0x00000] in <filename unknown>:0 
  at Banshee.Gui.GtkBaseClient.Initialize (Boolean registerCommonServices) [0x00000] in <filename unknown>:0 
  at Banshee.Gui.GtkBaseClient..ctor (Boolean initializeDefault, System.String defaultIconName) [0x00000] in <filename unknown>:0 
  at Banshee.Gui.GtkBaseClient..ctor () [0x00000] in <filename unknown>:0 
  at Nereid.Client..ctor () [0x00000] in <filename unknown>:0 
  at (wrapper managed-to-native) System.Reflection.MonoCMethod:InternalInvoke (object,object[],System.Exception&)
  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] in <filename unknown>:0 
Exception has been thrown by the target of an invocation.

  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] in <filename unknown>:0 
  at System.Reflection.MonoCMethod.Invoke (BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] in <filename unknown>:0 
  at System.Reflection.ConstructorInfo.Invoke (System.Object[] parameters) [0x00000] in <filename unknown>:0 
  at System.Activator.CreateInstance (System.Type type, Boolean nonPublic) [0x00000] in <filename unknown>:0 
  at System.Activator.CreateInstance (System.Type type) [0x00000] in <filename unknown>:0 
  at Banshee.Gui.GtkBaseClient.Startup () [0x00000] in <filename unknown>:0 
  at Hyena.Gui.CleanRoomStartup.Startup (Hyena.Gui.StartupInvocationHandler startup) [0x00000] in <filename unknown>:0 

.NET Version: 2.0.50727.1433
OS Version: Unix 2.6.35.22

Assembly Version Information:

gkeyfile-sharp (1.0.0.0)
Banshee.AudioCd (1.8.0.0)
Banshee.CoverArt (1.8.0.0)
notify-sharp (0.4.0.0)
Banshee.NotificationArea (1.8.0.0)
Banshee.AmazonMp3 (1.8.0.0)
Banshee.Bpm (1.8.0.0)
Banshee.Daap (1.8.0.0)
Lastfm (1.8.0.0)
Banshee.Dap (1.8.0.0)
Migo (1.8.0.0)
Banshee.Podcasting (1.8.0.0)
Banshee.LibraryWatcher (1.8.0.0)
Banshee.MultimediaKeys (1.8.0.0)
Banshee.Lastfm (1.8.0.0)
Banshee.WebBrowser (1.8.0.0)
Banshee.Wikipedia (1.8.0.0)
pango-sharp (2.12.0.0)
Banshee.Fixup (1.8.0.0)
Banshee.Widgets (1.8.0.0)
gio-sharp (2.14.0.0)
gudev-sharp (1.0.0.0)
Banshee.Gio (1.8.0.0)
Banshee.GStreamer (1.8.0.0)
Mono.Media (1.8.0.0)
System.Transactions (2.0.0.0)
System.Configuration (2.0.0.0)
NDesk.DBus.GLib (1.0.0.0)
gconf-sharp (2.24.0.0)
Banshee.Gnome (1.8.0.0)
Banshee.NowPlaying (1.8.0.0)
Mono.Cairo (2.0.0.0)
System.Data (2.0.0.0)
Mono.Data.Sqlite (1.8.0.0)
System.Xml (2.0.0.0)
Banshee.Core (1.8.0.0)
Hyena.Data.Sqlite (1.8.0.0)
System.Core (3.5.0.0)
gdk-sharp (2.12.0.0)
Mono.Addins (0.4.0.0)
atk-sharp (2.12.0.0)
Hyena.Gui (1.8.0.0)
gtk-sharp (2.12.0.0)
Banshee.ThickClient (1.8.0.0)
Nereid (1.8.0.0)
NDesk.DBus.Proxies (0.0.0.0)
Mono.Posix (2.0.0.0)
NDesk.DBus (1.0.0.0)
glib-sharp (2.12.0.0)
Hyena (1.8.0.0)
System (2.0.0.0)
Banshee.Services (1.8.0.0)
Banshee (1.8.0.0)
mscorlib (2.0.0.0)

Platform Information: Linux 2.6.35-22-generic x86_64 unknown GNU/Linux




any ideas?

---

### Post by directhex on 2011-03-22
Looks like your banshee.db got corrupted. Run "mv ~/.config/banshee-1/banshee.db ~/Desktop", and attach the file on your desktop to [https://bugzilla.gnome.org/show_bug.cgi?id=621057](https://bugzilla.gnome.org/show_bug.cgi?id=621057)

---

### Post by heddleston on 2011-03-22
tried to, but even after compressing the file it was too big to attach. where can i host it and then link to it?

---

