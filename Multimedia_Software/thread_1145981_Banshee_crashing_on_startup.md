---
title: "Banshee crashing on startup?"
date: 2009-05-02
forum: Multimedia Software
---

### Post by Quift on 2009-05-02
Hi, I cannot seem to get banshee to work at all. Starting it from the terminal i get this:

pierre-emil@pierre-emil-laptop:~/Skrivbord/testmapp$ banshee
[Info  11:48:55.639] Running Banshee 1.4.3: [Ubuntu jaunty (development branch) (linux-gnu, x86_64) @ 2009-03-22 17:00:13 UTC]
[Warn  11:48:57.707] Service `Banshee.Database.BansheeDbConnection' not started: SQL logic error or missing database
[Warn  11:48:57.728] Caught an exception - SQL logic error or missing database (in `Mono.Data.SqliteClient')
  at Mono.Data.SqliteClient.SqliteCommand.ExecuteStatement (IntPtr pStmt, System.Int32& cols, System.IntPtr& pazValue, System.IntPtr& pazColName) [0x00000] 
  at (wrapper remoting-invoke-with-check) Mono.Data.SqliteClient.SqliteCommand:ExecuteStatement (intptr,int&,intptr&,intptr&)
  at Mono.Data.SqliteClient.SqliteDataReader.ReadpVm (IntPtr pVm, Int32 version, Mono.Data.SqliteClient.SqliteCommand cmd) [0x00000] 
  at Mono.Data.SqliteClient.SqliteDataReader..ctor (Mono.Data.SqliteClient.SqliteCommand cmd, IntPtr pVm, Int32 version) [0x00000] 
  at (wrapper remoting-invoke-with-check) Mono.Data.SqliteClient.SqliteDataReader:.ctor (Mono.Data.SqliteClient.SqliteCommand,intptr,int)
  at Mono.Data.SqliteClient.SqliteCommand.ExecuteReader (CommandBehavior behavior, Boolean want_results, System.Int32& rows_affected) [0x00000] 
  at Mono.Data.SqliteClient.SqliteCommand.ExecuteReader (CommandBehavior behavior) [0x00000] 
  at Mono.Data.SqliteClient.SqliteCommand.ExecuteReader () [0x00000] 
  at Mono.Data.SqliteClient.SqliteCommand.ExecuteScalar () [0x00000] 
  at Hyena.Data.Sqlite.HyenaSqliteCommand.Execute (Hyena.Data.Sqlite.HyenaSqliteConnection hconnection, Mono.Data.SqliteClient.SqliteConnection connection) [0x00000] 
[Warn  11:49:00.326] Caught an exception - Object reference not set to an instance of an object (in `Banshee.Bookmarks')
  at Banshee.Bookmarks.Bookmark.Initialize () [0x00000] 
  at Banshee.Bookmarks.BookmarksService.Banshee.ServiceStack.IExtensionService.Initialize () [0x00000] 
  at Banshee.ServiceStack.ServiceManager.StartExtension (Mono.Addins.TypeExtensionNode node) [0x00000] 
[Warn  11:49:00.326] Extension `Banshee.Bookmarks.BookmarksService' not started: Object reference not set to an instance of an object
[Warn  11:49:00.328] Caught an exception - Object reference not set to an instance of an object (in `Banshee.CoverArt')
  at Banshee.CoverArt.CoverArtService.Banshee.ServiceStack.IExtensionService.Initialize () [0x00000] 
  at Banshee.ServiceStack.ServiceManager.StartExtension (Mono.Addins.TypeExtensionNode node) [0x00000] 
[Warn  11:49:00.328] Extension `Banshee.CoverArt.CoverArtService' not started: Object reference not set to an instance of an object
[Warn  11:49:01.432] Caught an exception - Object reference not set to an instance of an object (in `Hyena')
  at Hyena.Data.Sqlite.SqliteModelProvider`1[Migo.Syndication.Feed].CheckVersion () [0x00000] 
  at Hyena.Data.Sqlite.SqliteModelProvider`1[Migo.Syndication.Feed].Init () [0x00000] 
  at Hyena.Data.Sqlite.SqliteModelProvider`1[Migo.Syndication.Feed]..ctor (Hyena.Data.Sqlite.HyenaSqliteConnection connection, System.String table_name) [0x00000] 
  at Migo.Syndication.MigoModelProvider`1[Migo.Syndication.Feed]..ctor (Hyena.Data.Sqlite.HyenaSqliteConnection connection, System.String table_name) [0x00000] 
  at Migo.Syndication.FeedProvider..ctor (Hyena.Data.Sqlite.HyenaSqliteConnection connection) [0x00000] 
  at Migo.Syndication.Feed.Init () [0x00000] 
  at Migo.Syndication.FeedsManager..ctor (Hyena.Data.Sqlite.HyenaSqliteConnection connection, Migo.DownloadCore.DownloadManager downloadManager, System.String podcast_base_dir) [0x00000] 
  at Banshee.Podcasting.PodcastService..ctor () [0x00000] 
  at (wrapper managed-to-native) System.Reflection.MonoCMethod:InternalInvoke (object,object[],System.Exception&)
  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
[Warn  11:49:01.432] Extension `/Banshee/ServiceManager/Service/__nid_10' not started: Exception has been thrown by the target of an invocation.
[Warn  11:49:01.621] Caught an exception - Object reference not set to an instance of an object (in `Banshee.Bookmarks')
  at Banshee.Bookmarks.Bookmark.Initialize () [0x00000] 
  at Banshee.Bookmarks.BookmarksService.Banshee.ServiceStack.IExtensionService.Initialize () [0x00000] 
  at Banshee.ServiceStack.ServiceManager.StartExtension (Mono.Addins.TypeExtensionNode node) [0x00000] 
[Warn  11:49:01.621] Extension `Banshee.Bookmarks.BookmarksService' not started: Object reference not set to an instance of an object
[Warn  11:49:01.621] Caught an exception - Object reference not set to an instance of an object (in `Banshee.CoverArt')
  at Banshee.CoverArt.CoverArtService.Banshee.ServiceStack.IExtensionService.Initialize () [0x00000] 
  at Banshee.ServiceStack.ServiceManager.StartExtension (Mono.Addins.TypeExtensionNode node) [0x00000] 
[Warn  11:49:01.622] Extension `Banshee.CoverArt.CoverArtService' not started: Object reference not set to an instance of an object
[Warn  11:49:01.625] Caught an exception - Object reference not set to an instance of an object (in `Hyena')
  at Hyena.Data.Sqlite.SqliteModelProvider`1[Migo.Syndication.Feed].CheckVersion () [0x00000] 
  at Hyena.Data.Sqlite.SqliteModelProvider`1[Migo.Syndication.Feed].Init () [0x00000] 
  at Hyena.Data.Sqlite.SqliteModelProvider`1[Migo.Syndication.Feed]..ctor (Hyena.Data.Sqlite.HyenaSqliteConnection connection, System.String table_name) [0x00000] 
  at Migo.Syndication.MigoModelProvider`1[Migo.Syndication.Feed]..ctor (Hyena.Data.Sqlite.HyenaSqliteConnection connection, System.String table_name) [0x00000] 
  at Migo.Syndication.FeedProvider..ctor (Hyena.Data.Sqlite.HyenaSqliteConnection connection) [0x00000] 
  at Migo.Syndication.Feed.Init () [0x00000] 
  at Migo.Syndication.FeedsManager..ctor (Hyena.Data.Sqlite.HyenaSqliteConnection connection, Migo.DownloadCore.DownloadManager downloadManager, System.String podcast_base_dir) [0x00000] 
  at Banshee.Podcasting.PodcastService..ctor () [0x00000] 
  at (wrapper managed-to-native) System.Reflection.MonoCMethod:InternalInvoke (object,object[],System.Exception&)
  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
[Warn  11:49:01.625] Extension `/Banshee/ServiceManager/Service/__nid_10' not started: Exception has been thrown by the target of an invocation.
[Info  11:49:01.627] All services are started 4,886322s
Exception has been thrown by the target of an invocation.
System.Reflection.TargetInvocationException: Exception has been thrown by the target of an invocation. ---> System.NullReferenceException: Object reference not set to an instance of an object
  at Banshee.Configuration.DatabaseConfigurationClient.Get (System.String namespce, System.String key) [0x00000] 
  at Banshee.Configuration.DatabaseConfigurationClient.Get[Int32] (System.String namespce, System.String key, Int32 fallback) [0x00000] 
  at Banshee.Database.BansheeModelProvider`1[Banshee.Collection.Database.DatabaseTrackInfo].CheckVersion (System.String namespce, System.String key, Int32 new_version, Banshee.Database.MigrateDel func) [0x00000] 
  at Banshee.Database.BansheeModelProvider`1[Banshee.Collection.Database.DatabaseTrackInfo].CheckVersion () [0x00000] 
  at Hyena.Data.Sqlite.SqliteModelProvider`1[Banshee.Collection.Database.DatabaseTrackInfo].Init () [0x00000] 
  at Hyena.Data.Sqlite.SqliteModelProvider`1[Banshee.Collection.Database.DatabaseTrackInfo]..ctor (Hyena.Data.Sqlite.HyenaSqliteConnection connection, System.String table_name) [0x00000] 
  at Banshee.Database.BansheeModelProvider`1[Banshee.Collection.Database.DatabaseTrackInfo]..ctor (Banshee.Database.BansheeDbConnection connection, System.String table_name) [0x00000] 
  at Banshee.Collection.Database.DatabaseTrackModelProvider`1[Banshee.Collection.Database.DatabaseTrackInfo]..ctor (Banshee.Database.BansheeDbConnection connection) [0x00000] 
  at Banshee.Collection.Database.DatabaseTrackInfo.get_Provider () [0x00000] 
  at Banshee.Sources.DatabaseSource.get_TrackProvider () [0x00000] 
  at Banshee.Sources.DatabaseSource.CreateTrackModelFor (Banshee.Sources.DatabaseSource src) [0x00000] 
  at Banshee.Sources.DatabaseSource.get_DatabaseTrackModel () [0x00000] 
  at Banshee.Sources.DatabaseSource+<CreateFiltersFor>c__Iterator5.MoveNext () [0x00000] 
  at Banshee.Sources.DatabaseSource.DatabaseSourceInitialize () [0x00000] 
  at Banshee.Sources.DatabaseSource..ctor (System.String generic_name, System.String name, System.String id, Int32 order, Banshee.Sources.Source parent) [0x00000] 
  at Banshee.Sources.DatabaseSource..ctor (System.String generic_name, System.String name, System.String id, Int32 order) [0x00000] 
  at Banshee.Sources.PrimarySource..ctor (System.String generic_name, System.String name, System.String id, Int32 order) [0x00000] 
  at Banshee.Library.LibrarySource..ctor (System.String label, System.String name, Int32 order) [0x00000] 
  at Banshee.Library.MusicLibrarySource..ctor () [0x00000] 
  at Banshee.ServiceStack.Application.Run () [0x00000] 
  at Banshee.Gui.GtkBaseClient.Initialize (Boolean registerCommonServices) [0x00000] 
  at Banshee.Gui.GtkBaseClient..ctor (Boolean initializeDefault, System.String defaultIconName) [0x00000] 
  at Banshee.Gui.GtkBaseClient..ctor () [0x00000] 
  at Nereid.Client..ctor () [0x00000] 
  at (wrapper managed-to-native) System.Reflection.MonoCMethod:InternalInvoke (object,object[],System.Exception&)
  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  --- End of inner exception stack trace ---
  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  at System.Reflection.MonoCMethod.Invoke (BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  at System.Reflection.ConstructorInfo.Invoke (System.Object[] parameters) [0x00000] 
  at System.Activator.CreateInstance (System.Type type, Boolean nonPublic) [0x00000] 
  at System.Activator.CreateInstance (System.Type type) [0x00000] 
  at Banshee.Gui.GtkBaseClient.Startup () [0x00000] 
  at Hyena.Gui.CleanRoomStartup.Startup (Hyena.Gui.StartupInvocationHandler startup) [0x00000] 

and the error from the program itself:

Ett ohanterat undantag kastades: Object reference not set to an instance of an object

  at Banshee.Configuration.DatabaseConfigurationClient.Get (System.String namespce, System.String key) [0x00000] 
  at Banshee.Configuration.DatabaseConfigurationClient.Get[Int32] (System.String namespce, System.String key, Int32 fallback) [0x00000] 
  at Banshee.Database.BansheeModelProvider`1[Banshee.Collection.Database.DatabaseTrackInfo].CheckVersion (System.String namespce, System.String key, Int32 new_version, Banshee.Database.MigrateDel func) [0x00000] 
  at Banshee.Database.BansheeModelProvider`1[Banshee.Collection.Database.DatabaseTrackInfo].CheckVersion () [0x00000] 
  at Hyena.Data.Sqlite.SqliteModelProvider`1[Banshee.Collection.Database.DatabaseTrackInfo].Init () [0x00000] 
  at Hyena.Data.Sqlite.SqliteModelProvider`1[Banshee.Collection.Database.DatabaseTrackInfo]..ctor (Hyena.Data.Sqlite.HyenaSqliteConnection connection, System.String table_name) [0x00000] 
  at Banshee.Database.BansheeModelProvider`1[Banshee.Collection.Database.DatabaseTrackInfo]..ctor (Banshee.Database.BansheeDbConnection connection, System.String table_name) [0x00000] 
  at Banshee.Collection.Database.DatabaseTrackModelProvider`1[Banshee.Collection.Database.DatabaseTrackInfo]..ctor (Banshee.Database.BansheeDbConnection connection) [0x00000] 
  at Banshee.Collection.Database.DatabaseTrackInfo.get_Provider () [0x00000] 
  at Banshee.Sources.DatabaseSource.get_TrackProvider () [0x00000] 
  at Banshee.Sources.DatabaseSource.CreateTrackModelFor (Banshee.Sources.DatabaseSource src) [0x00000] 
  at Banshee.Sources.DatabaseSource.get_DatabaseTrackModel () [0x00000] 
  at Banshee.Sources.DatabaseSource+<CreateFiltersFor>c__Iterator5.MoveNext () [0x00000] 
  at Banshee.Sources.DatabaseSource.DatabaseSourceInitialize () [0x00000] 
  at Banshee.Sources.DatabaseSource..ctor (System.String generic_name, System.String name, System.String id, Int32 order, Banshee.Sources.Source parent) [0x00000] 
  at Banshee.Sources.DatabaseSource..ctor (System.String generic_name, System.String name, System.String id, Int32 order) [0x00000] 
  at Banshee.Sources.PrimarySource..ctor (System.String generic_name, System.String name, System.String id, Int32 order) [0x00000] 
  at Banshee.Library.LibrarySource..ctor (System.String label, System.String name, Int32 order) [0x00000] 
  at Banshee.Library.MusicLibrarySource..ctor () [0x00000] 
  at Banshee.ServiceStack.Application.Run () [0x00000] 
  at Banshee.Gui.GtkBaseClient.Initialize (Boolean registerCommonServices) [0x00000] 
  at Banshee.Gui.GtkBaseClient..ctor (Boolean initializeDefault, System.String defaultIconName) [0x00000] 
  at Banshee.Gui.GtkBaseClient..ctor () [0x00000] 
  at Nereid.Client..ctor () [0x00000] 
  at (wrapper managed-to-native) System.Reflection.MonoCMethod:InternalInvoke (object,object[],System.Exception&)
  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
Exception has been thrown by the target of an invocation.

  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  at System.Reflection.MonoCMethod.Invoke (BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  at System.Reflection.ConstructorInfo.Invoke (System.Object[] parameters) [0x00000] 
  at System.Activator.CreateInstance (System.Type type, Boolean nonPublic) [0x00000] 
  at System.Activator.CreateInstance (System.Type type) [0x00000] 
  at Banshee.Gui.GtkBaseClient.Startup () [0x00000] 
  at Hyena.Gui.CleanRoomStartup.Startup (Hyena.Gui.StartupInvocationHandler startup) [0x00000] 

.NET Version: 2.0.50727.42
OS Version: Unix 2.6.28.11

Assembly Version Information:

Lastfm (1.4.0.0)
Banshee.Lastfm (1.4.0.0)
Migo (1.4.0.0)
Banshee.Podcasting (1.4.0.0)
notify-sharp (0.4.0.0)
Banshee.NotificationArea (1.4.0.0)
Banshee.AudioCd (1.4.0.0)
Banshee.CoverArt (1.4.0.0)
Banshee.Bookmarks (1.4.0.0)
Banshee.MultimediaKeys (1.4.0.0)
Banshee.Daap (1.4.0.0)
pango-sharp (2.12.0.0)
Banshee.Widgets (1.4.0.0)
Banshee.Dap.Ipod (1.4.0.0)
Banshee.Dap (1.4.0.0)
Banshee.Hal (1.4.0.0)
Banshee.Unix (1.4.0.0)
Banshee.GStreamer (1.4.0.0)
gconf-sharp (2.24.0.0)
Banshee.Gnome (1.4.0.0)
Banshee.NowPlaying (1.4.0.0)
System.Transactions (2.0.0.0)
NDesk.DBus.GLib (1.0.0.0)
Mono.Cairo (2.0.0.0)
System.Data (2.0.0.0)
Mono.Data.SqliteClient (2.0.0.0)
gdk-sharp (2.12.0.0)
Mono.Addins (0.4.0.0)
atk-sharp (2.12.0.0)
Hyena.Gui (1.4.0.0)
gtk-sharp (2.12.0.0)
Banshee.ThickClient (1.4.0.0)
Nereid (1.4.0.0)
System.Xml (2.0.0.0)
NDesk.DBus.Proxies (0.0.0.0)
Mono.Posix (2.0.0.0)
Banshee.Core (1.4.0.0)
System (2.0.0.0)
Hyena (1.4.0.0)
NDesk.DBus (1.0.0.0)
glib-sharp (2.12.0.0)
Banshee.Services (1.4.0.0)
Banshee (1.4.0.0)
mscorlib (2.0.0.0)

Platform Information: Linux 2.6.28-11-generic x86_64 unknown GNU/Linux

Disribution Information:

[/etc/lsb-release]
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.04
DISTRIB_CODENAME=jaunty
DISTRIB_DESCRIPTION="Ubuntu 9.04"

[/etc/debian_version]
5.0

Any help appreciated. Thanks everyone

---

