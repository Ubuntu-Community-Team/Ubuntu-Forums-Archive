---
title: "Banshee crashes on startup"
date: 2011-04-14
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by lanetherif on 2011-04-14
Hi,

though at first it worked fine, after a few updates, Banshee started to crash when run.

I am not sure what the problem is or whether it is a bug or not. Here is the error message when I run it:

```
An unhandled exception was thrown: Object reference not set to an instance of an object

  at Hyena.Data.Sqlite.SqliteModelCache`1[Banshee.Collection.Database.DatabaseArtistInfo].CheckCacheTable () [0x00000] in <filename unknown>:0 
  at Hyena.Data.Sqlite.SqliteModelCache`1[Banshee.Collection.Database.DatabaseArtistInfo]..ctor (Hyena.Data.Sqlite.HyenaSqliteConnection connection, System.String uuid, ICacheableDatabaseModel model, Hyena.Data.Sqlite.SqliteModelProvider`1 provider) [0x00000] in <filename unknown>:0 
  at Banshee.Database.BansheeModelCache`1[Banshee.Collection.Database.DatabaseArtistInfo]..ctor (Hyena.Data.Sqlite.HyenaSqliteConnection connection, System.String uuid, ICacheableDatabaseModel model, Hyena.Data.Sqlite.SqliteModelProvider`1 provider) [0x00000] in <filename unknown>:0 
  at Banshee.Collection.Database.DatabaseFilterListModel`2[T,U]..ctor (System.String name, System.String label, Banshee.Sources.DatabaseSource source, Banshee.Collection.Database.DatabaseTrackListModel trackModel, Hyena.Data.Sqlite.HyenaSqliteConnection connection, Hyena.Data.Sqlite.SqliteModelProvider`1 provider, .U selectAllItem, System.String uuid) [0x00000] in <filename unknown>:0 
  at Banshee.Collection.Database.DatabaseArtistListModel..ctor (Banshee.Sources.DatabaseSource source, Banshee.Collection.Database.DatabaseTrackListModel trackModel, Banshee.Database.BansheeDbConnection connection, System.String uuid) [0x00000] in <filename unknown>:0 
  at Banshee.Sources.DatabaseSource+<CreateFiltersFor>c__IteratorB.MoveNext () [0x00000] in <filename unknown>:0 
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
OS Version: Unix 2.6.38.8
```

```
Assembly Version Information:

gkeyfile-sharp (1.0.0.0)
Banshee.AudioCd (2.0.0.0)
Banshee.CoverArt (2.0.0.0)
Banshee.Bpm (2.0.0.0)
Banshee.Daap (2.0.0.0)
notify-sharp (0.4.0.0)
Banshee.SoundMenu (2.0.0.0)
Banshee.Mpris (2.0.0.0)
Banshee.Dap (2.0.0.0)
Migo (2.0.0.0)
Banshee.Podcasting (2.0.0.0)
Banshee.LibraryWatcher (2.0.0.0)
Banshee.MultimediaKeys (2.0.0.0)
Banshee.YouTube (2.0.0.0)
Banshee.WebBrowser (2.0.0.0)
Banshee.Wikipedia (2.0.0.0)
pango-sharp (2.12.0.0)
Banshee.Fixup (2.0.0.0)
Banshee.Widgets (2.0.0.0)
gio-sharp (2.14.0.0)
gudev-sharp (1.0.0.0)
Banshee.Gio (2.0.0.0)
Banshee.GStreamer (2.0.0.0)
System.Configuration (2.0.0.0)
NDesk.DBus.GLib (1.0.0.0)
gconf-sharp (2.24.0.0)
Banshee.Gnome (2.0.0.0)
Banshee.NowPlaying (2.0.0.0)
Mono.Cairo (2.0.0.0)
System.Xml (2.0.0.0)
Banshee.Core (2.0.0.0)
Hyena.Data.Sqlite (2.0.0.0)
System.Core (3.5.0.0)
gdk-sharp (2.12.0.0)
Mono.Addins (0.4.0.0)
atk-sharp (2.12.0.0)
Hyena.Gui (2.0.0.0)
gtk-sharp (2.12.0.0)
Banshee.ThickClient (2.0.0.0)
Nereid (2.0.0.0)
NDesk.DBus.Proxies (0.0.0.0)
Mono.Posix (2.0.0.0)
Hyena (2.0.0.0)
NDesk.DBus (1.0.0.0)
glib-sharp (2.12.0.0)
System (2.0.0.0)
Banshee.Services (2.0.0.0)
Banshee (2.0.0.0)
mscorlib (2.0.0.0)

Platform Information: Linux 2.6.38-8-generic x86_64 x86_64 GNU/Linux

Disribution Information:

[/etc/lsb-release]
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.04
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu Natty (development branch)"

[/etc/debian_version]
squeeze/sid
```

And this is what I get, when it is run through terminal:

```
[Info  21:23:29.340] Running Banshee 2.0.0: [Ubuntu Natty (development branch) (linux-gnu, x86_64) @ 2011-04-09 07:44:31 UTC]
[Warn  21:23:29.615] Caught an exception - Hyena.Data.Sqlite.SqliteException: Sqlite error 11: database disk image is malformed (SQL: SELECT COUNT(*) FROM sqlite_master WHERE Type='table' AND Name='CoreTracks') (in `Hyena.Data.Sqlite')
  at Hyena.Data.Sqlite.Connection.CheckError (Int32 errorCode, System.String sql) [0x00000] in <filename unknown>:0 
  at Hyena.Data.Sqlite.Statement.CheckError (Int32 code) [0x00000] in <filename unknown>:0 
  at Hyena.Data.Sqlite.Statement..ctor (Hyena.Data.Sqlite.Connection connection, System.String sql) [0x00000] in <filename unknown>:0 
  at Hyena.Data.Sqlite.Connection.Query[Object] (System.String sql) [0x00000] in <filename unknown>:0 
  at Hyena.Data.Sqlite.HyenaSqliteCommand.Execute (Hyena.Data.Sqlite.HyenaSqliteConnection hconnection, Hyena.Data.Sqlite.Connection connection) [0x00000] in <filename unknown>:0 
[Warn  21:23:29.615] Service `Banshee.Database.BansheeDbConnection' not started: Sqlite error 11: database disk image is malformed (SQL: SELECT COUNT(*) FROM sqlite_master WHERE Type='table' AND Name='CoreTracks')
[Warn  21:23:29.615] Caught an exception - Hyena.Data.Sqlite.SqliteException: Sqlite error 11: database disk image is malformed (SQL: SELECT COUNT(*) FROM sqlite_master WHERE Type='table' AND Name='CoreTracks') (in `Hyena.Data.Sqlite')
  at Hyena.Data.Sqlite.Connection.CheckError (Int32 errorCode, System.String sql) [0x00000] in <filename unknown>:0 
  at Hyena.Data.Sqlite.Statement.CheckError (Int32 code) [0x00000] in <filename unknown>:0 
  at Hyena.Data.Sqlite.Statement..ctor (Hyena.Data.Sqlite.Connection connection, System.String sql) [0x00000] in <filename unknown>:0 
  at Hyena.Data.Sqlite.Connection.Query[Object] (System.String sql) [0x00000] in <filename unknown>:0 
  at Hyena.Data.Sqlite.HyenaSqliteCommand.Execute (Hyena.Data.Sqlite.HyenaSqliteConnection hconnection, Hyena.Data.Sqlite.Connection connection) [0x00000] in <filename unknown>:0 
[Info  21:23:30.559] Updating web proxy from GConf
[Warn  21:23:30.591] Caught an exception - System.NullReferenceException: Object reference not set to an instance of an object (in `Banshee.CoverArt')
  at Banshee.CoverArt.CoverArtService.Banshee.ServiceStack.IExtensionService.Initialize () [0x00000] in <filename unknown>:0 
  at Banshee.ServiceStack.ServiceManager.StartExtension (Mono.Addins.TypeExtensionNode node) [0x00000] in <filename unknown>:0 
[Warn  21:23:30.591] Extension `Banshee.CoverArt.CoverArtService' not started: Object reference not set to an instance of an object
[Warn  21:23:30.617] Caught an exception - System.NullReferenceException: Object reference not set to an instance of an object (in `Banshee.CoverArt')
  at Banshee.CoverArt.CoverArtService.Banshee.ServiceStack.IExtensionService.Initialize () [0x00000] in <filename unknown>:0 
  at Banshee.ServiceStack.ServiceManager.StartExtension (Mono.Addins.TypeExtensionNode node) [0x00000] in <filename unknown>:0 
[Warn  21:23:30.617] Extension `Banshee.CoverArt.CoverArtService' not started: Object reference not set to an instance of an object
[Info  21:23:30.618] All services are started 1.064019
Exception has been thrown by the target of an invocation.
System.Reflection.TargetInvocationException: Exception has been thrown by the target of an invocation. ---> System.NullReferenceException: Object reference not set to an instance of an object
  at Hyena.Data.Sqlite.SqliteModelCache`1[Banshee.Collection.Database.DatabaseArtistInfo].CheckCacheTable () [0x00000] in <filename unknown>:0 
  at Hyena.Data.Sqlite.SqliteModelCache`1[Banshee.Collection.Database.DatabaseArtistInfo]..ctor (Hyena.Data.Sqlite.HyenaSqliteConnection connection, System.String uuid, ICacheableDatabaseModel model, Hyena.Data.Sqlite.SqliteModelProvider`1 provider) [0x00000] in <filename unknown>:0 
  at Banshee.Database.BansheeModelCache`1[Banshee.Collection.Database.DatabaseArtistInfo]..ctor (Hyena.Data.Sqlite.HyenaSqliteConnection connection, System.String uuid, ICacheableDatabaseModel model, Hyena.Data.Sqlite.SqliteModelProvider`1 provider) [0x00000] in <filename unknown>:0 
  at Banshee.Collection.Database.DatabaseFilterListModel`2[T,U]..ctor (System.String name, System.String label, Banshee.Sources.DatabaseSource source, Banshee.Collection.Database.DatabaseTrackListModel trackModel, Hyena.Data.Sqlite.HyenaSqliteConnection connection, Hyena.Data.Sqlite.SqliteModelProvider`1 provider, .U selectAllItem, System.String uuid) [0x00000] in <filename unknown>:0 
  at Banshee.Collection.Database.DatabaseArtistListModel..ctor (Banshee.Sources.DatabaseSource source, Banshee.Collection.Database.DatabaseTrackListModel trackModel, Banshee.Database.BansheeDbConnection connection, System.String uuid) [0x00000] in <filename unknown>:0 
  at Banshee.Sources.DatabaseSource+<CreateFiltersFor>c__IteratorB.MoveNext () [0x00000] in <filename unknown>:0 
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
  --- End of inner exception stack trace ---
  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] in <filename unknown>:0 
  at System.Reflection.MonoCMethod.Invoke (BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] in <filename unknown>:0 
  at System.Reflection.ConstructorInfo.Invoke (System.Object[] parameters) [0x00000] in <filename unknown>:0 
  at System.Activator.CreateInstance (System.Type type, Boolean nonPublic) [0x00000] in <filename unknown>:0 
  at System.Activator.CreateInstance (System.Type type) [0x00000] in <filename unknown>:0 
  at Banshee.Gui.GtkBaseClient.Startup () [0x00000] in <filename unknown>:0 
  at Hyena.Gui.CleanRoomStartup.Startup (Hyena.Gui.StartupInvocationHandler startup) [0x00000] in <filename unknown>:0 

Unhandled Exception: Mono.Unix.UnixIOException: Broken pipe [EPIPE].
at Mono.Unix.UnixMarshal.ThrowExceptionForLastError () <0x00013>
at Mono.Unix.UnixStream.Write (byte[],int,int) <0x000b3>
at NDesk.DBus.Connection.WriteMessage (NDesk.DBus.Message) <0x0009c>
at NDesk.DBus.Connection.Send (NDesk.DBus.Message) <0x0003b>
at NDesk.DBus.ExportObject.HandleMethodCall (NDesk.DBus.MethodCall) <0x0045b>
at NDesk.DBus.Connection.HandleMethodCall (NDesk.DBus.MethodCall) <0x00487>
at NDesk.DBus.Connection.HandleMessage (NDesk.DBus.Message) <0x0016f>
at NDesk.DBus.Connection.Iterate () <0x0002b>
at NDesk.DBus.BusG/<Init>c__AnonStorey0.<>m__0 (intptr,NDesk.GLib.IOCondition,intptr) <0x0003b>
at (wrapper native-to-managed) NDesk.DBus.BusG/<Init>c__AnonStorey0.<>m__0 (intptr,NDesk.GLib.IOCondition,intptr) <0x00086>
at (wrapper managed-to-native) Gtk.Dialog.gtk_dialog_run (intptr) <0x0005b>
at Gtk.Dialog.Run () <0x00017>
at Hyena.Gui.CleanRoomStartup.Startup (Hyena.Gui.CleanRoomStartup/StartupInvocationHandler) <0x0010f>
at Banshee.Gui.GtkBaseClient.Startup<Nereid.Client> () <0x00073>
at Banshee.Gui.GtkBaseClient.Startup<Nereid.Client> (string[]) <0x000f3>
at Nereid.Client.Main (string[]) <0x0001b>
at (wrapper managed-to-native) System.AppDomain.ExecuteAssembly (System.Reflection.Assembly,string[]) <0x00062>
at System.AppDomain.ExecuteAssemblyInternal (System.Reflection.Assembly,string[]) <0x0003f>
at System.AppDomain.ExecuteAssembly (string,System.Security.Policy.Evidence,string[]) <0x00037>
at (wrapper remoting-invoke-with-check) System.AppDomain.ExecuteAssembly (string,System.Security.Policy.Evidence,string[]) <0x00087>
at System.AppDomain.ExecuteAssembly (string) <0x0001f>
at (wrapper remoting-invoke-with-check) System.AppDomain.ExecuteAssembly (string) <0x00067>
at Booter.Booter.BootClient (string) <0x0006f>
at Booter.Booter.Main () <0x001eb>

```

Should I report it? If I should, to where? 

Thanks...

---

### Post by directhex on 2011-04-15
Looks like your database is corrupt. 'rm ~/.config/banshee*/banshee.db' will delete it, so you can recreate it - you'll need to reimport etc your music though

---

### Post by lanetherif on 2011-04-15
> **directhex said:**
> Looks like your database is corrupt. 'rm ~/.config/banshee*/banshee.db' will delete it, so you can recreate it - you'll need to reimport etc your music though


I did it as you said. Now, it starts normally, yet it shuts itself down as soon as it starts rescanning music library; a situation which I am familiar from 10.10 and which I didn't mind. :) Thanks for answer.

---

### Post by jonbwilson on 2011-04-20
> **directhex said:**
> Looks like your database is corrupt. 'rm ~/.config/banshee*/banshee.db' will delete it, so you can recreate it - you'll need to reimport etc your music though

Thanks for this.  I scoured the internet for a half hour trying to find a fix for this and this was the only pertinent answer I found.  Ubuntu Forums FTW.

---

### Post by gnomeuser on 2011-04-21
> **jonbwilson said:**
> Thanks for this.  I scoured the internet for a half hour trying to find a fix for this and this was the only pertinent answer I found.  Ubuntu Forums FTW.

Deleting the whole thing is a bit drastic as a first step, the Banshee FAQ contains a means of rebuilding the db in case corruption.

[http://banshee.fm/support/faq/](http://banshee.fm/support/faq/)

As for the crashing on scanning, ensure that you are using gio-sharp 0.3 and if that is the case. Please read:

[http://www.omgubuntu.co.uk/2011/04/banshee-suckth-the-big-one-or-how-to-correctly-file-a-bug-and-stop-worrying/](http://www.omgubuntu.co.uk/2011/04/banshee-suckth-the-big-one-or-how-to-correctly-file-a-bug-and-stop-worrying/)

and tell us, Bugzilla works very well for, politely, complaining when Banshee sucks.

---

### Post by lanetherif on 2011-04-21
> **gnomeuser said:**
> Deleting the whole thing is a bit drastic as a first step, the Banshee FAQ contains a means of rebuilding the db in case corruption.

[http://banshee.fm/support/faq/](http://banshee.fm/support/faq/)

As for the crashing on scanning, ensure that you are using gio-sharp 0.3 and if that is the case. Please read:

[http://www.omgubuntu.co.uk/2011/04/banshee-suckth-the-big-one-or-how-to-correctly-file-a-bug-and-stop-worrying/](http://www.omgubuntu.co.uk/2011/04/banshee-suckth-the-big-one-or-how-to-correctly-file-a-bug-and-stop-worrying/)

and tell us, Bugzilla works very well for, politely, complaining when Banshee sucks.

Actually, I figured out why it crashes while scanning library. It happens if I try to update library while Banshee tries to detect bpm for tracks. It is I guess a bug...

---

