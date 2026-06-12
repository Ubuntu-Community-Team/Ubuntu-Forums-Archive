---
title: "Banshee  error message &quot;Banshee encountered a fatal error...&quot;"
date: 2009-07-09
forum: Multimedia Software
---

### Post by KFwLsKvVAs on 2009-07-09
For some reason, Bashee will not work anymore.  It froze up while I was adding some tracks to a playlist, and when I opened it again it gave this error message and closed.  

I tried restarting and opening it again, it threw the same error.  

Not really sure what caused this, could it be that my music library is too large (15,896 items)?


Banshee encountered a fatal error

Exception has been thrown by the target of an invocation

Error Details
An unhandled exception was thrown: The database is locked.

  at Mono.Data.SqliteClient.SqliteCommand.ExecuteStatement (IntPtr pStmt, System.Int32& cols, System.IntPtr& pazValue, System.IntPtr& pazColName) [0x00000] 
  at Mono.Data.SqliteClient.SqliteCommand.ExecuteStatement (IntPtr pStmt) [0x00000] 
  at Mono.Data.SqliteClient.SqliteCommand.ExecuteReader (CommandBehavior behavior, Boolean want_results, System.Int32& rows_affected) [0x00000] 
  at Mono.Data.SqliteClient.SqliteCommand.ExecuteNonQuery () [0x00000] 
  at Hyena.Data.Sqlite.HyenaSqliteCommand.Execute (Hyena.Data.Sqlite.HyenaSqliteConnection hconnection, Mono.Data.SqliteClient.SqliteConnection connection) [0x00000] 
Exception has been thrown by the target of an invocation.

  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  at System.Reflection.MonoCMethod.Invoke (BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  at System.Reflection.ConstructorInfo.Invoke (System.Object[] parameters) [0x00000] 
  at System.Activator.CreateInstance (System.Type type, Boolean nonPublic) [0x00000] 
  at System.Activator.CreateInstance (System.Type type) [0x00000] 
  at Banshee.Gui.GtkBaseClient.Startup () [0x00000] 
  at Hyena.Gui.CleanRoomStartup.Startup (Hyena.Gui.StartupInvocationHandler startup) [0x00000] 

.NET Version: 2.0.50727.42
OS Version: Unix 2.6.27.14

Assembly Version Information:

Banshee.CoverArt (1.2.1.19182)
Migo (1.2.1.19166)
Banshee.Podcasting (1.2.1.19189)
Lastfm (1.2.1.19169)
Banshee.Lastfm (1.2.1.19185)
Banshee.MiniMode (1.2.1.19186)
notify-sharp (0.4.0.0)
Banshee.NotificationArea (1.2.1.19187)
Banshee.Bookmarks (1.2.1.19181)
Banshee.MultimediaKeys (1.2.1.19186)
Banshee.Daap (1.2.1.19183)
Banshee.AudioCd (1.2.1.19180)
pango-sharp (2.12.0.0)
Mono.Cairo (2.0.0.0)
Banshee.Widgets (1.2.1.19173)
Banshee.Dap.Ipod (1.2.1.19178)
Banshee.Dap (1.2.1.19177)
Banshee.Hal (1.2.1.19190)
Banshee.Unix (1.2.1.19192)
Banshee.GStreamer (1.2.1.19191)
gconf-sharp (2.20.0.0)
Banshee.Gnome (1.2.1.19191)
Banshee.NowPlaying (1.2.1.19188)
System.Transactions (2.0.0.0)
System.Xml (2.0.0.0)
System.Data (2.0.0.0)
Mono.Data.SqliteClient (2.0.0.0)
Mono.Addins (0.3.0.0)
atk-sharp (2.12.0.0)
Hyena.Gui (1.2.1.19165)
NDesk.DBus.Proxies (0.0.0.0)
Mono.Posix (2.0.0.0)
NDesk.DBus.GLib (1.0.0.0)
NDesk.DBus (1.0.0.0)
gtk-sharp (2.12.0.0)
Hyena (1.2.1.19164)
System (2.0.0.0)
glib-sharp (2.12.0.0)
gdk-sharp (2.12.0.0)
Banshee.Core (1.2.1.19170)
Banshee.Services (1.2.1.19172)
Banshee.ThickClient (1.2.1.19175)
Nereid (1.2.1.19176)
mscorlib (2.0.0.0)

Platform Information: Linux 2.6.27-14-generic i686 unknown GNU/Linux

Disribution Information:

[/etc/lsb-release]
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.10
DISTRIB_CODENAME=intrepid
DISTRIB_DESCRIPTION="Ubuntu 8.10"

[/etc/debian_version]
lenny/sid


Could really use help getting this working again, I had multiple playlists that took hours upon hours to build, and if I lost it all it would be a real shame.

---

### Post by directhex on 2009-07-09
Do you have write permissions to the ~/.config/banshee-1/banshee.db file?

---

### Post by KFwLsKvVAs on 2009-07-10
Yes, I have read and write permissions.

---

### Post by tgalati4 on 2009-07-10
Do you have 2 instances of banshee running? That might tie up the database.

Try:

```
sudo killall banshee
```

Or, try rebooting.


Then run banshee --debug in a terminal.

Post the errors.

---

### Post by KFwLsKvVAs on 2009-07-17
Eh I tried rebooting, still didn't work, so I went into synaptic, did complete remove, and reinstalled it.  Started it up and it still threw the same error, so I deleted the database file, reimported everything, and it seems to work again.  But I did lose all my playlists and stuff...

---

### Post by directhex on 2009-07-18
If you ever have an issue that requires deleting your database, keep a copy - upstream can't fix bugs unless they can reproduce them, which means they can't fix this bug now because they would have needed a copy of your database

---

### Post by Rafase282 on 2009-10-11
Here is the output of the debug.

rafase282@rafase282-laptop:~$ sudo killall banshee
[sudo] password for rafase282: 
banshee: no process killed
rafase282@rafase282-laptop:~$ banshee --debug
** Running Mono with --debug   **
[Info  12:58:13.356] Running Banshee 1.4.3: [Ubuntu jaunty (development branch) (linux-gnu, x86_64) @ 2009-03-22 17:00:13 UTC]
[Debug 12:58:15.482] Bus.Session.RequestName ('org.bansheeproject.Banshee') replied with PrimaryOwner
[Debug 12:58:15.496] Core service started (DBusServiceManager, 0.002899s)
[Debug 12:58:15.503] Registering remote object /org/bansheeproject/Banshee/DBusCommandService (Banshee.ServiceStack.DBusCommandService) on org.bansheeproject.Banshee
[Debug 12:58:15.525] Core service started (DBusCommandService, 0.028015s)
[Debug 12:58:15.688] Exception executing command: SELECT COUNT(*) FROM CoreTracks
[Warn  12:58:15.789] Service `Banshee.Database.BansheeDbConnection' not started: SQL logic error or missing database
[Warn  12:58:15.802] Caught an exception - SQL logic error or missing database (in `Mono.Data.SqliteClient')
  at Mono.Data.SqliteClient.SqliteCommand.ExecuteStatement (IntPtr pStmt, System.Int32& cols, System.IntPtr& pazValue, System.IntPtr& pazColName) [0x00000] 
  at (wrapper remoting-invoke-with-check) Mono.Data.SqliteClient.SqliteCommand:ExecuteStatement (intptr,int&,intptr&,intptr&)
  at Mono.Data.SqliteClient.SqliteDataReader.ReadpVm (IntPtr pVm, Int32 version, Mono.Data.SqliteClient.SqliteCommand cmd) [0x00000] 
  at Mono.Data.SqliteClient.SqliteDataReader..ctor (Mono.Data.SqliteClient.SqliteCommand cmd, IntPtr pVm, Int32 version) [0x00000] 
  at (wrapper remoting-invoke-with-check) Mono.Data.SqliteClient.SqliteDataReader:.ctor (Mono.Data.SqliteClient.SqliteCommand,intptr,int)
  at Mono.Data.SqliteClient.SqliteCommand.ExecuteReader (CommandBehavior behavior, Boolean want_results, System.Int32& rows_affected) [0x00000] 
  at Mono.Data.SqliteClient.SqliteCommand.ExecuteReader (CommandBehavior behavior) [0x00000] 
  at Mono.Data.SqliteClient.SqliteCommand.ExecuteReader () [0x00000] 
  at Mono.Data.SqliteClient.SqliteCommand.ExecuteScalar () [0x00000] 
  at Hyena.Data.Sqlite.HyenaSqliteCommand.Execute (Hyena.Data.Sqlite.HyenaSqliteConnection hconnection, Mono.Data.SqliteClient.SqliteConnection connection) [0x00082] in /build/buildd/banshee-1.4.3/src/Libraries/Hyena/Hyena.Data.Sqlite/HyenaSqliteCommand.cs:130 
[Debug 12:58:15.875] Core service started (PreferenceService, 0.071636s)
[Debug 12:58:15.878] Registering remote object /org/bansheeproject/Banshee/SourceManager (Banshee.Sources.SourceManager) on org.bansheeproject.Banshee
[Debug 12:58:15.878] Core service started (SourceManager, 0.003502s)
[Debug 12:58:16.231] Core service started (MediaProfileManager, 0.349877s)
[Debug 12:58:16.233] Registering remote object /org/bansheeproject/Banshee/PlayerEngine (Banshee.MediaEngine.PlayerEngineService) on org.bansheeproject.Banshee
[Debug 12:58:16.234] Core service started (PlayerEngine, 0.00317s)
[Debug 12:58:16.245] Configuration client extension loaded (Banshee.GnomeBackend.GConfConfigurationClient)
[Debug 12:58:16.314] IO provider extension loaded (Banshee.IO.Unix.Provider)
[Debug 12:58:16.321] Core service started (TranscoderService, 0.010914s)
[Debug 12:58:16.325] Registering remote object /org/bansheeproject/Banshee/PlaybackController (Banshee.PlaybackController.PlaybackControllerService) on org.bansheeproject.Banshee
[Debug 12:58:16.326] Core service started (PlaybackController, 0.004546s)
[Debug 12:58:16.327] Core service started (ImportSourceManager, 0.000526s)
[Debug 12:58:16.334] Core service started (LibraryImportManager, 0.006531s)
[Debug 12:58:16.334] Core service started (UserJobManager, 0.00054s)
[Debug 12:58:16.352] Core service started (HardwareManager, 0.017694s)
[Debug 12:58:16.356] Bus.Session.RequestName ('org.bansheeproject.CollectionIndexer') replied with PrimaryOwner
[Debug 12:58:16.357] Registering remote object /org/bansheeproject/Banshee/CollectionIndexerService (Banshee.Collection.Indexer.CollectionIndexerService) on org.bansheeproject.CollectionIndexer
[Debug 12:58:16.359] Core service started (CollectionIndexerService, 0.006424s)
[Debug 12:58:16.382] Adding icon theme search path: /usr/share/banshee-1/icons
[Debug 12:58:16.383] Core service started (GtkElementsService, 0.023711s)
[Debug 12:58:16.447] Core service started (InterfaceActionService, 0.063938s)
[Debug 12:58:16.449] Album artwork path set to /home/rafase282/.cache/album-art
[Debug 12:58:16.449] Core service started (ArtworkManager, 0.002167s)
[Debug 12:58:17.171] Registering remote object /org/bansheeproject/Banshee/ClientWindow (Nereid.PlayerInterface) on org.bansheeproject.Banshee
[Debug 12:58:17.171] Core service started (NereidPlayerInterface, 0.721566s)
[Debug 12:58:17.173] Extension service started (DaapService, 0.001562s)
[Debug 12:58:17.174] Extension service started (DapService, 0.000302s)
[Debug 12:58:17.178] Using GNOME 2.22 API for Multimedia Keys
[Debug 12:58:17.179] Extension service started (MultimediaKeysService, 0.004399s)
[Warn  12:58:17.183] Caught an exception - Object reference not set to an instance of an object (in `Banshee.Bookmarks')
  at Banshee.Bookmarks.Bookmark.Initialize () [0x00000] in /build/buildd/banshee-1.4.3/src/Extensions/Banshee.Bookmarks/Banshee.Bookmarks/BookmarksService.cs:336 
  at Banshee.Bookmarks.BookmarksService.Banshee.ServiceStack.IExtensionService.Initialize () [0x00000] in /build/buildd/banshee-1.4.3/src/Extensions/Banshee.Bookmarks/Banshee.Bookmarks/BookmarksService.cs:1 
  at Banshee.ServiceStack.ServiceManager.StartExtension (Mono.Addins.TypeExtensionNode node) [0x00034] in /build/buildd/banshee-1.4.3/src/Core/Banshee.Services/Banshee.ServiceStack/ServiceManager.cs:198 
[Warn  12:58:17.183] Extension `Banshee.Bookmarks.BookmarksService' not started: Object reference not set to an instance of an object
[Warn  12:58:17.185] Caught an exception - Object reference not set to an instance of an object (in `Banshee.CoverArt')
  at Banshee.CoverArt.CoverArtService.Banshee.ServiceStack.IExtensionService.Initialize () [0x00000] in /build/buildd/banshee-1.4.3/src/Extensions/Banshee.CoverArt/Banshee.CoverArt/CoverArtService.cs:65 
  at Banshee.ServiceStack.ServiceManager.StartExtension (Mono.Addins.TypeExtensionNode node) [0x00034] in /build/buildd/banshee-1.4.3/src/Core/Banshee.Services/Banshee.ServiceStack/ServiceManager.cs:198 
[Warn  12:58:17.185] Extension `Banshee.CoverArt.CoverArtService' not started: Object reference not set to an instance of an object
[Debug 12:58:17.332] Extension service started (AudioCdService, 0.146779s)
[Debug 12:58:17.357] Extension service started (LastfmRecommendationService, 0.024562s)
[Debug 12:58:17.376] Core service started (Network, 0.00795s)
[Debug 12:58:17.376] Audioscrobbler state: connected
[Debug 12:58:17.380] Extension service started (AudioscrobblerService, 0.023066s)
[Debug 12:58:17.383] Extension service started (GnomeService, 0.002978s)
[Warn  12:58:17.436] Caught an exception - Object reference not set to an instance of an object (in `Hyena')
  at Hyena.Data.Sqlite.SqliteModelProvider`1[Migo.Syndication.Feed].CheckVersion () [0x00000] in /build/buildd/banshee-1.4.3/src/Libraries/Hyena/Hyena.Data.Sqlite/SqliteModelProvider.cs:135 
  at Hyena.Data.Sqlite.SqliteModelProvider`1[Migo.Syndication.Feed].Init () [0x001fb] in /build/buildd/banshee-1.4.3/src/Libraries/Hyena/Hyena.Data.Sqlite/SqliteModelProvider.cs:129 
  at Hyena.Data.Sqlite.SqliteModelProvider`1[Migo.Syndication.Feed]..ctor (Hyena.Data.Sqlite.HyenaSqliteConnection connection, System.String table_name) [0x0000e] in /build/buildd/banshee-1.4.3/src/Libraries/Hyena/Hyena.Data.Sqlite/SqliteModelProvider.cs:98 
  at Migo.Syndication.MigoModelProvider`1[Migo.Syndication.Feed]..ctor (Hyena.Data.Sqlite.HyenaSqliteConnection connection, System.String table_name) [0x00000] in /build/buildd/banshee-1.4.3/src/Libraries/Migo/Migo.DownloadCore/DownloadGroupStatusChangedEventArgs.cs:1 
  at Migo.Syndication.FeedProvider..ctor (Hyena.Data.Sqlite.HyenaSqliteConnection connection) [0x00000] in /build/buildd/banshee-1.4.3/src/Libraries/Migo/Migo.DownloadCore/DownloadGroupStatusChangedEventArgs.cs:1 
  at Migo.Syndication.Feed.Init () [0x00000] in /build/buildd/banshee-1.4.3/src/Libraries/Migo/Migo.Syndication/Feed.cs:105 
  at Migo.Syndication.FeedsManager..ctor (Hyena.Data.Sqlite.HyenaSqliteConnection connection, Migo.DownloadCore.DownloadManager downloadManager, System.String podcast_base_dir) [0x0003c] in /build/buildd/banshee-1.4.3/src/Libraries/Migo/Migo.Syndication/FeedsManager.cs:137 
  at Banshee.Podcasting.PodcastService..ctor () [0x00073] in /build/buildd/banshee-1.4.3/src/Extensions/Banshee.Podcasting/Banshee.Podcasting/PodcastService.cs:85 
  at (wrapper managed-to-native) System.Reflection.MonoCMethod:InternalInvoke (object,object[],System.Exception&)
  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
[Warn  12:58:17.436] Extension `/Banshee/ServiceManager/Service/__nid_10' not started: Exception has been thrown by the target of an invocation.
[Debug 12:58:17.554] GStreamer pipeline does not run: audioconvert ! xingenc bitrate=128 ! id3v2mux
[Debug 12:58:17.614] GStreamer pipeline does not run: audioconvert ! fluwmaenc bitrate=64000 vbr=false ! fluasfmux
[Debug 12:58:17.614] Extension service started (GStreamerCoreService, 0.177942s)
[Debug 12:58:17.647] Player state change: NotReady -> Ready
[Debug 12:58:17.659] Player state change: Ready -> Idle
[Debug 12:58:17.697] (libbanshee:player) Disabled ReplayGain
[Debug 12:58:17.877] Extension service started (NotificationAreaService, 0.178986s)
[Warn  12:58:17.878] Caught an exception - Object reference not set to an instance of an object (in `Banshee.Bookmarks')
  at Banshee.Bookmarks.Bookmark.Initialize () [0x00000] in /build/buildd/banshee-1.4.3/src/Extensions/Banshee.Bookmarks/Banshee.Bookmarks/BookmarksService.cs:336 
  at Banshee.Bookmarks.BookmarksService.Banshee.ServiceStack.IExtensionService.Initialize () [0x00000] in /build/buildd/banshee-1.4.3/src/Extensions/Banshee.Bookmarks/Banshee.Bookmarks/BookmarksService.cs:1 
  at Banshee.ServiceStack.ServiceManager.StartExtension (Mono.Addins.TypeExtensionNode node) [0x00034] in /build/buildd/banshee-1.4.3/src/Core/Banshee.Services/Banshee.ServiceStack/ServiceManager.cs:198 
[Warn  12:58:17.878] Extension `Banshee.Bookmarks.BookmarksService' not started: Object reference not set to an instance of an object
[Warn  12:58:17.879] Caught an exception - Object reference not set to an instance of an object (in `Banshee.CoverArt')
  at Banshee.CoverArt.CoverArtService.Banshee.ServiceStack.IExtensionService.Initialize () [0x00000] in /build/buildd/banshee-1.4.3/src/Extensions/Banshee.CoverArt/Banshee.CoverArt/CoverArtService.cs:65 
  at Banshee.ServiceStack.ServiceManager.StartExtension (Mono.Addins.TypeExtensionNode node) [0x00034] in /build/buildd/banshee-1.4.3/src/Core/Banshee.Services/Banshee.ServiceStack/ServiceManager.cs:198 
[Warn  12:58:17.879] Extension `Banshee.CoverArt.CoverArtService' not started: Object reference not set to an instance of an object
[Warn  12:58:17.883] Caught an exception - Object reference not set to an instance of an object (in `Hyena')
  at Hyena.Data.Sqlite.SqliteModelProvider`1[Migo.Syndication.Feed].CheckVersion () [0x00000] in /build/buildd/banshee-1.4.3/src/Libraries/Hyena/Hyena.Data.Sqlite/SqliteModelProvider.cs:135 
  at Hyena.Data.Sqlite.SqliteModelProvider`1[Migo.Syndication.Feed].Init () [0x001fb] in /build/buildd/banshee-1.4.3/src/Libraries/Hyena/Hyena.Data.Sqlite/SqliteModelProvider.cs:129 
  at Hyena.Data.Sqlite.SqliteModelProvider`1[Migo.Syndication.Feed]..ctor (Hyena.Data.Sqlite.HyenaSqliteConnection connection, System.String table_name) [0x0000e] in /build/buildd/banshee-1.4.3/src/Libraries/Hyena/Hyena.Data.Sqlite/SqliteModelProvider.cs:98 
  at Migo.Syndication.MigoModelProvider`1[Migo.Syndication.Feed]..ctor (Hyena.Data.Sqlite.HyenaSqliteConnection connection, System.String table_name) [0x00000] in /build/buildd/banshee-1.4.3/src/Libraries/Migo/Migo.DownloadCore/DownloadGroupStatusChangedEventArgs.cs:1 
  at Migo.Syndication.FeedProvider..ctor (Hyena.Data.Sqlite.HyenaSqliteConnection connection) [0x00000] in /build/buildd/banshee-1.4.3/src/Libraries/Migo/Migo.DownloadCore/DownloadGroupStatusChangedEventArgs.cs:1 
  at Migo.Syndication.Feed.Init () [0x00000] in /build/buildd/banshee-1.4.3/src/Libraries/Migo/Migo.Syndication/Feed.cs:105 
  at Migo.Syndication.FeedsManager..ctor (Hyena.Data.Sqlite.HyenaSqliteConnection connection, Migo.DownloadCore.DownloadManager downloadManager, System.String podcast_base_dir) [0x0003c] in /build/buildd/banshee-1.4.3/src/Libraries/Migo/Migo.Syndication/FeedsManager.cs:137 
  at Banshee.Podcasting.PodcastService..ctor () [0x00073] in /build/buildd/banshee-1.4.3/src/Extensions/Banshee.Podcasting/Banshee.Podcasting/PodcastService.cs:85 
  at (wrapper managed-to-native) System.Reflection.MonoCMethod:InternalInvoke (object,object[],System.Exception&)
  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
[Warn  12:58:17.883] Extension `/Banshee/ServiceManager/Service/__nid_10' not started: Exception has been thrown by the target of an invocation.
[Info  12:58:17.883] All services are started 2.400491s
Exception has been thrown by the target of an invocation.
System.Reflection.TargetInvocationException: Exception has been thrown by the target of an invocation. ---> System.NullReferenceException: Object reference not set to an instance of an object
  at Banshee.Configuration.DatabaseConfigurationClient.Get (System.String namespce, System.String key) [0x00000] in /build/buildd/banshee-1.4.3/src/Core/Banshee.Services/Banshee.Configuration/DatabaseConfigurationClient.cs:98 
  at Banshee.Configuration.DatabaseConfigurationClient.Get[Int32] (System.String namespce, System.String key, Int32 fallback) [0x00000] in /build/buildd/banshee-1.4.3/src/Core/Banshee.Services/Banshee.Configuration/DatabaseConfigurationClient.cs:87 
  at Banshee.Database.BansheeModelProvider`1[Banshee.Collection.Database.DatabaseTrackInfo].CheckVersion (System.String namespce, System.String key, Int32 new_version, Banshee.Database.MigrateDel func) [0x00000] in /build/buildd/banshee-1.4.3/src/Core/Banshee.Services/Banshee.Database/BansheeModelProvider.cs:56 
  at Banshee.Database.BansheeModelProvider`1[Banshee.Collection.Database.DatabaseTrackInfo].CheckVersion () [0x00000] in /build/buildd/banshee-1.4.3/src/Core/Banshee.Services/Banshee.Database/BansheeModelProvider.cs:48 
  at Hyena.Data.Sqlite.SqliteModelProvider`1[Banshee.Collection.Database.DatabaseTrackInfo].Init () [0x001fb] in /build/buildd/banshee-1.4.3/src/Libraries/Hyena/Hyena.Data.Sqlite/SqliteModelProvider.cs:129 
  at Hyena.Data.Sqlite.SqliteModelProvider`1[Banshee.Collection.Database.DatabaseTrackInfo]..ctor (Hyena.Data.Sqlite.HyenaSqliteConnection connection, System.String table_name) [0x0000e] in /build/buildd/banshee-1.4.3/src/Libraries/Hyena/Hyena.Data.Sqlite/SqliteModelProvider.cs:98 
  at Banshee.Database.BansheeModelProvider`1[Banshee.Collection.Database.DatabaseTrackInfo]..ctor (Banshee.Database.BansheeDbConnection connection, System.String table_name) [0x00000] in /build/buildd/banshee-1.4.3/src/Core/Banshee.Services/Banshee.Base/RateLimiter.cs:1 
  at Banshee.Collection.Database.DatabaseTrackModelProvider`1[Banshee.Collection.Database.DatabaseTrackInfo]..ctor (Banshee.Database.BansheeDbConnection connection) [0x00000] in /build/buildd/banshee-1.4.3/src/Core/Banshee.Services/Banshee.Base/RateLimiter.cs:1 
  at Banshee.Collection.Database.DatabaseTrackInfo.get_Provider () [0x00000] in /build/buildd/banshee-1.4.3/src/Core/Banshee.Services/Banshee.Collection.Database/DatabaseTrackInfo.cs:66 
  at Banshee.Sources.DatabaseSource.get_TrackProvider () [0x00000] in /build/buildd/banshee-1.4.3/src/Core/Banshee.Services/Banshee.Base/RateLimiter.cs:1 
  at Banshee.Sources.DatabaseSource.CreateTrackModelFor (Banshee.Sources.DatabaseSource src) [0x00000] in /build/buildd/banshee-1.4.3/src/Core/Banshee.Services/Banshee.Sources/DatabaseSource.cs:135 
  at Banshee.Sources.DatabaseSource.get_DatabaseTrackModel () [0x00000] in /build/buildd/banshee-1.4.3/src/Core/Banshee.Services/Banshee.Sources/DatabaseSource.cs:101 
  at Banshee.Sources.DatabaseSource+<CreateFiltersFor>c__Iterator5.MoveNext () [0x0003e] in /build/buildd/banshee-1.4.3/src/Core/Banshee.Services/Banshee.Sources/DatabaseSource.cs:144 
  at Banshee.Sources.DatabaseSource.DatabaseSourceInitialize () [0x0005c] in /build/buildd/banshee-1.4.3/src/Core/Banshee.Services/Banshee.Sources/DatabaseSource.cs:125 
  at Banshee.Sources.DatabaseSource..ctor (System.String generic_name, System.String name, System.String id, Int32 order, Banshee.Sources.Source parent) [0x0001a] in /build/buildd/banshee-1.4.3/src/Core/Banshee.Services/Banshee.Sources/DatabaseSource.cs:74 
  at Banshee.Sources.DatabaseSource..ctor (System.String generic_name, System.String name, System.String id, Int32 order) [0x00000] in /build/buildd/banshee-1.4.3/src/Core/Banshee.Services/Banshee.Base/RateLimiter.cs:1 
  at Banshee.Sources.PrimarySource..ctor (System.String generic_name, System.String name, System.String id, Int32 order) [0x00000] in /build/buildd/banshee-1.4.3/src/Core/Banshee.Services/Banshee.Base/RateLimiter.cs:1 
  at Banshee.Library.LibrarySource..ctor (System.String label, System.String name, Int32 order) [0x00000] in /build/buildd/banshee-1.4.3/src/Core/Banshee.Services/Banshee.Base/RateLimiter.cs:1 
  at Banshee.Library.MusicLibrarySource..ctor () [0x00000] in /build/buildd/banshee-1.4.3/src/Core/Banshee.Services/Banshee.Base/RateLimiter.cs:1 
  at Banshee.ServiceStack.Application.Run () [0x00033] in /build/buildd/banshee-1.4.3/src/Core/Banshee.Services/Banshee.ServiceStack/Application.cs:92 
  at Banshee.Gui.GtkBaseClient.Initialize (Boolean registerCommonServices) [0x000bc] in /build/buildd/banshee-1.4.3/src/Core/Banshee.ThickClient/Banshee.Gui/GtkBaseClient.cs:131 
  at Banshee.Gui.GtkBaseClient..ctor (Boolean initializeDefault, System.String defaultIconName) [0x00013] in /build/buildd/banshee-1.4.3/src/Core/Banshee.ThickClient/Banshee.Gui/GtkBaseClient.cs:91 
  at Banshee.Gui.GtkBaseClient..ctor () [0x00000] in /build/buildd/banshee-1.4.3/src/Core/Banshee.ThickClient/Banshee.Addins.Gui/AddinDetailsDialog.cs:1 
  at Nereid.Client..ctor () [0x00000] in /build/buildd/banshee-1.4.3/src/Clients/Nereid/Nereid/Client.cs:1 
  at (wrapper managed-to-native) System.Reflection.MonoCMethod:InternalInvoke (object,object[],System.Exception&)
  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  --- End of inner exception stack trace ---
  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  at System.Reflection.MonoCMethod.Invoke (BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  at System.Reflection.ConstructorInfo.Invoke (System.Object[] parameters) [0x00000] 
  at System.Activator.CreateInstance (System.Type type, Boolean nonPublic) [0x00000] 
  at System.Activator.CreateInstance (System.Type type) [0x00000] 
  at Banshee.Gui.GtkBaseClient.Startup () [0x00000] in /build/buildd/banshee-1.4.3/src/Core/Banshee.ThickClient/Banshee.Gui/GtkBaseClient.cs:78 
  at Hyena.Gui.CleanRoomStartup.Startup (Hyena.Gui.StartupInvocationHandler startup) [0x00048] in /build/buildd/banshee-1.4.3/src/Libraries/Hyena.Gui/Hyena.Gui/CleanRoomStartup.cs:54 
[Debug 12:58:18.181] Creating Pango.Layout, configuring Cairo.Context
[Debug 12:58:18.183] Creating Pango.Layout, configuring Cairo.Context
[Debug 12:58:18.185] Creating Pango.Layout, configuring Cairo.Context

---

### Post by Funnnny on 2009-10-11
Did you upgrade Banshee from an older version ?
If so, just delete the configuration folder

---

### Post by MossMethod on 2011-07-23
I have the same problem, I ran debug and got this.
> 
$ banshee --debug
** Running Mono with --debug   **
[1 Info  11:10:56.956] Running Banshee 2.0.0: [Ubuntu 11.04 (linux-gnu, i686) @ 2011-06-28 05:46:57 UTC]
[1 Debug 11:10:57.037] Initializing GTK
[1 Debug 11:11:00.358] Post-Initializing GTK
[1 Debug 11:11:00.378] Configuration client extension loaded (Banshee.GnomeBackend.GConfConfigurationClient)
[1 Debug 11:11:00.405] Using default gconf-base-key
[1 Debug 11:11:00.484] Bus.Session.RequestName ('org.bansheeproject.Banshee') replied with PrimaryOwner
[1 Debug 11:11:00.627] Core service started (DBusServiceManager, 0.001553)
[1 Debug 11:11:00.630] Registering remote object /org/bansheeproject/Banshee/DBusCommandService (Banshee.ServiceStack.DBusCommandService) on org.bansheeproject.Banshee
[1 Debug 11:11:00.653] Core service started (DBusCommandService, 0.024916)
[2 Debug 11:11:00.687] Exception executing command: SELECT COUNT(*) FROM sqlite_master WHERE Type='table' AND Name='CoreTracks'
[2 Warn  11:11:00.700] Caught an exception - Hyena.Data.Sqlite.SqliteException: Sqlite error 11: database disk image is malformed (SQL: SELECT COUNT(*) FROM sqlite_master WHERE Type='table' AND Name='CoreTracks') (in `Hyena.Data.Sqlite')
  at Hyena.Data.Sqlite.Connection.CheckError (Int32 errorCode, System.String sql) [0x0003b] in /build/buildd/banshee-2.0.0/src/Hyena/Hyena.Data.Sqlite/Hyena.Data.Sqlite/Sqlite.cs:107 
  at Hyena.Data.Sqlite.Statement.CheckError (Int32 code) [0x00000] in /build/buildd/banshee-2.0.0/src/Hyena/Hyena.Data.Sqlite/Hyena.Data.Sqlite/Sqlite.cs:343 
  at Hyena.Data.Sqlite.Statement..ctor (Hyena.Data.Sqlite.Connection connection, System.String sql) [0x00026] in /build/buildd/banshee-2.0.0/src/Hyena/Hyena.Data.Sqlite/Hyena.Data.Sqlite/Sqlite.cs:236 
  at Hyena.Data.Sqlite.Connection.Query[Object] (System.String sql) [0x00000] in /build/buildd/banshee-2.0.0/src/Hyena/Hyena.Data.Sqlite/Hyena.Data.Sqlite/Sqlite.cs:122 
  at Hyena.Data.Sqlite.HyenaSqliteCommand.Execute (Hyena.Data.Sqlite.HyenaSqliteConnection hconnection, Hyena.Data.Sqlite.Connection connection) [0x00098] in /build/buildd/banshee-2.0.0/src/Hyena/Hyena.Data.Sqlite/Hyena.Data.Sqlite/HyenaSqliteCommand.cs:105 
[1 Warn  11:11:00.708] Service `Banshee.Database.BansheeDbConnection' not started: Sqlite error 11: database disk image is malformed (SQL: SELECT COUNT(*) FROM sqlite_master WHERE Type='table' AND Name='CoreTracks')
[1 Warn  11:11:00.708] Caught an exception - Hyena.Data.Sqlite.SqliteException: Sqlite error 11: database disk image is malformed (SQL: SELECT COUNT(*) FROM sqlite_master WHERE Type='table' AND Name='CoreTracks') (in `Hyena.Data.Sqlite')
  at Hyena.Data.Sqlite.Connection.CheckError (Int32 errorCode, System.String sql) [0x0003b] in /build/buildd/banshee-2.0.0/src/Hyena/Hyena.Data.Sqlite/Hyena.Data.Sqlite/Sqlite.cs:107 
  at Hyena.Data.Sqlite.Statement.CheckError (Int32 code) [0x00000] in /build/buildd/banshee-2.0.0/src/Hyena/Hyena.Data.Sqlite/Hyena.Data.Sqlite/Sqlite.cs:343 
  at Hyena.Data.Sqlite.Statement..ctor (Hyena.Data.Sqlite.Connection connection, System.String sql) [0x00026] in /build/buildd/banshee-2.0.0/src/Hyena/Hyena.Data.Sqlite/Hyena.Data.Sqlite/Sqlite.cs:236 
  at Hyena.Data.Sqlite.Connection.Query[Object] (System.String sql) [0x00000] in /build/buildd/banshee-2.0.0/src/Hyena/Hyena.Data.Sqlite/Hyena.Data.Sqlite/Sqlite.cs:122 
  at Hyena.Data.Sqlite.HyenaSqliteCommand.Execute (Hyena.Data.Sqlite.HyenaSqliteConnection hconnection, Hyena.Data.Sqlite.Connection connection) [0x00098] in /build/buildd/banshee-2.0.0/src/Hyena/Hyena.Data.Sqlite/Hyena.Data.Sqlite/HyenaSqliteCommand.cs:105 
[1 Debug 11:11:00.735] Core service started (PreferenceService, 0.026732)
[1 Debug 11:11:00.752] Core service started (Network, 0.017235)
[1 Debug 11:11:00.753] Registering remote object /org/bansheeproject/Banshee/SourceManager (Banshee.Sources.SourceManager) on org.bansheeproject.Banshee
[1 Debug 11:11:00.753] Core service started (SourceManager, 0.000914)
[1 Debug 11:11:00.772] Core service started (MediaProfileManager, 0.000305)
[1 Debug 11:11:00.776] Registering remote object /org/bansheeproject/Banshee/PlayerEngine (Banshee.MediaEngine.PlayerEngineService) on org.bansheeproject.Banshee
[1 Debug 11:11:00.779] Core service started (PlayerEngine, 0.007061)
[1 Debug 11:11:00.812] Registering remote object /org/bansheeproject/Banshee/PlaybackController (Banshee.PlaybackController.PlaybackControllerService) on org.bansheeproject.Banshee
[1 Debug 11:11:00.814] Core service started (PlaybackController, 0.00674)
[1 Debug 11:11:00.830] Starting - Startup Job
[1 Debug 11:11:00.831] Core service started (JobScheduler, 0.01667)
[1 Debug 11:11:00.872] IO provider extension loaded (Banshee.IO.Gio.Provider)
[1 Debug 11:11:00.935] Loaded HardwareManager backend: Banshee.Hardware.Gio
[1 Debug 11:11:00.940] Core service started (HardwareManager, 0.109162)
[1 Debug 11:11:00.947] Bus.Session.RequestName ('org.bansheeproject.CollectionIndexer') replied with PrimaryOwner
[1 Debug 11:11:00.949] Registering remote object /org/bansheeproject/Banshee/CollectionIndexerService (Banshee.Collection.Indexer.CollectionIndexerService) on org.bansheeproject.CollectionIndexer
[1 Debug 11:11:00.952] Core service started (CollectionIndexerService, 0.011241)
[1 Debug 11:11:00.960] Core service started (SaveTrackMetadataService, 0.008092)
[1 Debug 11:11:00.982] Adding icon theme search path: /usr/share/banshee/icons
[1 Debug 11:11:00.983] Core service started (GtkElementsService, 0.02328)
[1 Debug 11:11:00.986] Core service started (InterfaceActionService, 0.002297)
[1 Debug 11:11:01.070] Loaded new mode into  shuffler: lastfm_shuffle_similar_artists
[1 Debug 11:11:01.072] RandomByLastfmUserTopArtists: Initialising List
[1 Debug 11:11:01.072] Loaded new mode into  shuffler: lastfm_shuffle_topartists
[1 Debug 11:11:01.097] Loaded new mode into  shuffler: mirage_similar
[1 Debug 11:11:01.228] Extension actions loaded: MetadataFixActions
[1 Debug 11:11:01.228] Registering remote object /org/bansheeproject/Banshee/GlobalUIActions (Banshee.Gui.GlobalActions) on org.bansheeproject.Banshee
[1 Debug 11:11:01.230] Album artwork path set to /home/user/.cache/media-art
[1 Debug 11:11:01.292] Core service started (ArtworkManager, 0.063883)
[1 Debug 11:11:01.292] Core service started (BookmarksService, 0.00019)
[1 Debug 11:11:01.661] Adding context page lastfm-recommendations
[1 Debug 11:11:01.709] Adding context page lyrics
[1 Debug 11:11:01.858] Adding context page wikipedia
[1 Debug 11:11:02.232] Constructed Nereid interface: 0.87127
[1 Debug 11:11:02.331] Creating new surface cache for 90px images, capped at 0.28 MiB (9 items)
[1 Debug 11:11:02.448] Registering remote object /org/bansheeproject/Banshee/ClientWindow (Nereid.PlayerInterface) on org.bansheeproject.Banshee
[1 Debug 11:11:02.449] Core service started (NereidPlayerInterface, 1.128288)
[1 Debug 11:11:02.530] Extension service started (GStreamerCoreService, 0.075476)
[1 Debug 11:11:02.548] Extension service started (BpmService, 0.018214)
[1 Debug 11:11:02.559] Using GNOME 2.22 API for Multimedia Keys
[1 Debug 11:11:02.559] Extension service started (MultimediaKeysService, 0.011139)
[1 Debug 11:11:02.770] Audioscrobbler state: disconnected
[1 Debug 11:11:02.773] Extension service started (AudioscrobblerService, 0.213691)
[1 Debug 11:11:02.780] Extension service started (LastfmStreamingService, 0.006766)
[1 Debug 11:11:02.782] Extension service started (DapService, 0.001818)
[1 Debug 11:11:02.787] Extension service started (PodcastService, 0.005517)
[1 Debug 11:11:02.812] Extension service started (MprisService, 0.024354)
[1 Debug 11:11:02.822] Extension service started (SoundMenuService, 0.009604)
[1 Info  11:11:02.827] Updating web proxy from GConf
[1 Debug 11:11:02.833] Direct connection, no proxy in use
[1 Debug 11:11:02.870] Extension service started (GnomeService, 0.048213)
[1 Debug 11:11:02.874] Extension service started (LastfmFingerprintService, 0.004305)
[1 Debug 11:11:02.939] Extension service started (OpenVPService, 0.064416)
[1 Warn  11:11:02.992] Caught an exception - System.NullReferenceException: Object reference not set to an instance of an object (in `Banshee.Lyrics')
  at Banshee.Lyrics.LyricsService.Banshee.ServiceStack.IExtensionService.Initialize () [0x00000] in <filename unknown>:0 
  at Banshee.ServiceStack.ServiceManager.StartExtension (Mono.Addins.TypeExtensionNode node) [0x00034] in /build/buildd/banshee-2.0.0/src/Core/Banshee.Services/Banshee.ServiceStack/ServiceManager.cs:210 
[1 Warn  11:11:02.992] Extension `Banshee.Lyrics.LyricsService' not started: Object reference not set to an instance of an object
[1 Warn  11:11:03.009] Caught an exception - System.NullReferenceException: Object reference not set to an instance of an object (in `Banshee.Services')
  at Banshee.Configuration.DatabaseConfigurationClient.get_Client () [0x00000] in /build/buildd/banshee-2.0.0/src/Core/Banshee.Services/Banshee.Configuration/DatabaseConfigurationClient.cs:40 
  at Banshee.AmazonMp3.AmazonMp3DownloaderService.Initialize () [0x00016] in /build/buildd/banshee-2.0.0/src/Extensions/Banshee.AmazonMp3/Banshee.AmazonMp3/AmazonMp3DownloaderService.cs:44 
  at Banshee.ServiceStack.ServiceManager.StartExtension (Mono.Addins.TypeExtensionNode node) [0x00034] in /build/buildd/banshee-2.0.0/src/Core/Banshee.Services/Banshee.ServiceStack/ServiceManager.cs:210 
[1 Warn  11:11:03.009] Extension `Banshee.AmazonMp3.AmazonMp3DownloaderService' not started: Object reference not set to an instance of an object
[1 Debug 11:11:03.013] Extension service started (DaapService, 0.004083)
[1 Info  11:11:03.014] Netbook extension initialized with hidden panel
[1 Debug 11:11:03.027] Extension service started (MeeGoService, 0.014305)
[1 Debug 11:11:03.031] Initializing Alarm Plugin
[1 Debug 11:11:03.034] Extension service started (AlarmClockService, 0.006257)
[1 Debug 11:11:03.034] Extension service started (MirageService, 0.000313)
[3 Debug 11:11:03.036] Alarm thread started
[1 Warn  11:11:03.038] Caught an exception - System.NullReferenceException: Object reference not set to an instance of an object (in `Banshee.CoverArt')
  at Banshee.CoverArt.CoverArtService.Banshee.ServiceStack.IExtensionService.Initialize () [0x00000] in /build/buildd/banshee-2.0.0/src/Extensions/Banshee.CoverArt/Banshee.CoverArt/CoverArtService.cs:63 
  at Banshee.ServiceStack.ServiceManager.StartExtension (Mono.Addins.TypeExtensionNode node) [0x00034] in /build/buildd/banshee-2.0.0/src/Core/Banshee.Services/Banshee.ServiceStack/ServiceManager.cs:210 
[1 Warn  11:11:03.038] Extension `Banshee.CoverArt.CoverArtService' not started: Object reference not set to an instance of an object
[3 Debug 11:11:03.059] Time until alarm is 22:03:56.9579500
[1 Debug 11:11:03.200] [RadioStationFetcherService] <RadioStationFetcherService> Constructor START
[1 Debug 11:11:03.200] [RadioStationFetcherService] <RadioStationFetcherService> Constructor END
[1 Debug 11:11:03.203] [RadioStationFetcherService] <Initialize> START
[1 Debug 11:11:03.204] [RadioStationFetcherService] <Initialize> END
[1 Debug 11:11:03.204] Extension service started (RadioStationFetcherService, 0.165826)
[1 Debug 11:11:03.288] Extension service started (AudioCdService, 0.083743)
[1 Warn  11:11:03.308] Caught an exception - System.NullReferenceException: Object reference not set to an instance of an object (in `Banshee.Lyrics')
  at Banshee.Lyrics.LyricsService.Banshee.ServiceStack.IExtensionService.Initialize () [0x00000] in <filename unknown>:0 
  at Banshee.ServiceStack.ServiceManager.StartExtension (Mono.Addins.TypeExtensionNode node) [0x00034] in /build/buildd/banshee-2.0.0/src/Core/Banshee.Services/Banshee.ServiceStack/ServiceManager.cs:210 
[1 Warn  11:11:03.308] Extension `Banshee.Lyrics.LyricsService' not started: Object reference not set to an instance of an object
[1 Warn  11:11:03.308] Caught an exception - System.NullReferenceException: Object reference not set to an instance of an object (in `Banshee.Services')
  at Banshee.Configuration.DatabaseConfigurationClient.get_Client () [0x00000] in /build/buildd/banshee-2.0.0/src/Core/Banshee.Services/Banshee.Configuration/DatabaseConfigurationClient.cs:40 
  at Banshee.AmazonMp3.AmazonMp3DownloaderService.Initialize () [0x00016] in /build/buildd/banshee-2.0.0/src/Extensions/Banshee.AmazonMp3/Banshee.AmazonMp3/AmazonMp3DownloaderService.cs:44 
  at Banshee.ServiceStack.ServiceManager.StartExtension (Mono.Addins.TypeExtensionNode node) [0x00034] in /build/buildd/banshee-2.0.0/src/Core/Banshee.Services/Banshee.ServiceStack/ServiceManager.cs:210 
[1 Warn  11:11:03.308] Extension `Banshee.AmazonMp3.AmazonMp3DownloaderService' not started: Object reference not set to an instance of an object
[1 Warn  11:11:03.309] Caught an exception - System.NullReferenceException: Object reference not set to an instance of an object (in `Banshee.CoverArt')
  at Banshee.CoverArt.CoverArtService.Banshee.ServiceStack.IExtensionService.Initialize () [0x00000] in /build/buildd/banshee-2.0.0/src/Extensions/Banshee.CoverArt/Banshee.CoverArt/CoverArtService.cs:63 
  at Banshee.ServiceStack.ServiceManager.StartExtension (Mono.Addins.TypeExtensionNode node) [0x00034] in /build/buildd/banshee-2.0.0/src/Core/Banshee.Services/Banshee.ServiceStack/ServiceManager.cs:210 
[1 Warn  11:11:03.309] Extension `Banshee.CoverArt.CoverArtService' not started: Object reference not set to an instance of an object
[1 Info  11:11:03.309] All services are started 2.823503
Exception has been thrown by the target of an invocation.
System.Reflection.TargetInvocationException: Exception has been thrown by the target of an invocation. ---> System.NullReferenceException: Object reference not set to an instance of an object
  at Hyena.Data.Sqlite.SqliteModelCache`1[Banshee.Collection.Database.DatabaseArtistInfo].CheckCacheTable () [0x00016] in /build/buildd/banshee-2.0.0/src/Hyena/Hyena.Data.Sqlite/Hyena.Data.Sqlite/SqliteModelCache.cs:497 
  at Hyena.Data.Sqlite.SqliteModelCache`1[Banshee.Collection.Database.DatabaseArtistInfo]..ctor (Hyena.Data.Sqlite.HyenaSqliteConnection connection, System.String uuid, ICacheableDatabaseModel model, Hyena.Data.Sqlite.SqliteModelProvider`1 provider) [0x0001d] in /build/buildd/banshee-2.0.0/src/Hyena/Hyena.Data.Sqlite/Hyena.Data.Sqlite/SqliteModelCache.cs:73 
  at Banshee.Database.BansheeModelCache`1[Banshee.Collection.Database.DatabaseArtistInfo]..ctor (Hyena.Data.Sqlite.HyenaSqliteConnection connection, System.String uuid, ICacheableDatabaseModel model, Hyena.Data.Sqlite.SqliteModelProvider`1 provider) [0x00000] in <filename unknown>:0 
  at Banshee.Collection.Database.DatabaseFilterListModel`2[T,U]..ctor (System.String name, System.String label, Banshee.Sources.DatabaseSource source, Banshee.Collection.Database.DatabaseTrackListModel trackModel, Hyena.Data.Sqlite.HyenaSqliteConnection connection, Hyena.Data.Sqlite.SqliteModelProvider`1 provider, .U selectAllItem, System.String uuid) [0x0002d] in /build/buildd/banshee-2.0.0/src/Core/Banshee.Services/Banshee.Collection.Database/DatabaseFilterListModel.cs:72 
  at Banshee.Collection.Database.DatabaseArtistListModel..ctor (Banshee.Sources.DatabaseSource source, Banshee.Collection.Database.DatabaseTrackListModel trackModel, Banshee.Database.BansheeDbConnection connection, System.String uuid) [0x00000] in <filename unknown>:0 
  at Banshee.Sources.DatabaseSource+<CreateFiltersFor>c__IteratorB.MoveNext () [0x0003e] in /build/buildd/banshee-2.0.0/src/Core/Banshee.Services/Banshee.Sources/DatabaseSource.cs:145 
  at Banshee.Sources.DatabaseSource.DatabaseSourceInitialize () [0x0005c] in /build/buildd/banshee-2.0.0/src/Core/Banshee.Services/Banshee.Sources/DatabaseSource.cs:126 
  at Banshee.Sources.DatabaseSource..ctor (System.String generic_name, System.String name, System.String id, Int32 order, Banshee.Sources.Source parent) [0x0001a] in /build/buildd/banshee-2.0.0/src/Core/Banshee.Services/Banshee.Sources/DatabaseSource.cs:75 
  at Banshee.Sources.DatabaseSource..ctor (System.String generic_name, System.String name, System.String id, Int32 order) [0x00000] in <filename unknown>:0 
  at Banshee.Sources.PrimarySource..ctor (System.String generic_name, System.String name, System.String id, Int32 order) [0x00000] in <filename unknown>:0 
  at Banshee.Library.LibrarySource..ctor (System.String label, System.String name, Int32 order) [0x00000] in <filename unknown>:0 
  at Banshee.Library.MusicLibrarySource..ctor () [0x00000] in <filename unknown>:0 
  at Banshee.ServiceStack.Application.Run () [0x00033] in /build/buildd/banshee-2.0.0/src/Core/Banshee.Services/Banshee.ServiceStack/Application.cs:110 
  at Banshee.Gui.GtkBaseClient.Initialize (Boolean registerCommonServices) [0x0010c] in /build/buildd/banshee-2.0.0/src/Core/Banshee.ThickClient/Banshee.Gui/GtkBaseClient.cs:180 
  at Banshee.Gui.GtkBaseClient..ctor (Boolean initializeDefault, System.String defaultIconName) [0x00013] in /build/buildd/banshee-2.0.0/src/Core/Banshee.ThickClient/Banshee.Gui/GtkBaseClient.cs:95 
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
  at Banshee.Gui.GtkBaseClient.Startup () [0x00000] in /build/buildd/banshee-2.0.0/src/Core/Banshee.ThickClient/Banshee.Gui/GtkBaseClient.cs:82 
  at Hyena.Gui.CleanRoomStartup.Startup (Hyena.Gui.StartupInvocationHandler startup) [0x00044] in /build/buildd/banshee-2.0.0/src/Hyena/Hyena.Gui/Hyena.Gui/CleanRoomStartup.cs:54 
[1 Debug 11:11:03.609] Creating Pango.Layout, configuring Cairo.Context
[1 Debug 11:11:03.713] Creating Pango.Layout, configuring Cairo.Context
[1 Debug 11:11:03.719] Creating Pango.Layout, configuring Cairo.Context
libmirageaudio: destroy.

---

### Post by MossMethod on 2011-07-27
> **MossMethod said:**
> I have the same problem, I ran debug and got this.

!!!!!      any 1?

---

### Post by redwheelbarrow on 2011-10-16
Same issue. Happened while rescaning library.

---

### Post by chuckyanutsup on 2011-11-04
I'm a complete n00b, but I was getting the same error and found this helpful. [http://askubuntu.com/questions/30185/banshee-encountered-a-fatal-error-sqlite-error-11-database-disk-image-is-malfo](http://askubuntu.com/questions/30185/banshee-encountered-a-fatal-error-sqlite-error-11-database-disk-image-is-malfo)

I just deleted my banshee.db file and have had to import my media again, but it appears to be working. There are apparently ways of fixing it, but I went for the simplest solution.

Footnote: is it bad etiquette to post links to other forums on here?

---

