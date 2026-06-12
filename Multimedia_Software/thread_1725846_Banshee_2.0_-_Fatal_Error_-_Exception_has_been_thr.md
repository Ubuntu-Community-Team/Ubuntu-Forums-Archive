---
title: "Banshee 2.0 - Fatal Error - Exception has been thrown by the target of an invocation"
date: 2011-04-10
forum: Multimedia Software
---

### Post by jay_outside on 2011-04-10
Banshee is crashing at launch.  I haven't made any major changes, other than to download some files trying to get a game to run.  I've recently downloaded pyLoTRO, some python files, and some qt4 files, but have since removed the pyLoTRo.  It worked fine until these downloads, and removing the pyLoTRo didn't change the error.  I'm running 10.10 Meerkat, and I'm brand new to ubuntu :/   I get the following error:  

Encountered a Fatal Error
Exception has been thrown by the target of an invocation
Error details:
An unhandled exception was thrown: Could not read add-in description

  at Mono.Addins.Addin.get_Description () [0x00000] in <filename unknown>:0 
  at Mono.Addins.TreeNode.ResetCachedData () [0x00000] in <filename unknown>:0 
  at Mono.Addins.TreeNode.ResetCachedData () [0x00000] in <filename unknown>:0 
  at Mono.Addins.TreeNode.ResetCachedData () [0x00000] in <filename unknown>:0 
  at Mono.Addins.TreeNode.ResetCachedData () [0x00000] in <filename unknown>:0 
  at Mono.Addins.ExtensionContext.ResetCachedData () [0x00000] in <filename unknown>:0 
  at Mono.Addins.AddinSessionService.ResetCachedData () [0x00000] in <filename unknown>:0 
  at Mono.Addins.Database.AddinDatabase.ResetCachedData () [0x00000] in <filename unknown>:0 
  at Mono.Addins.Database.AddinDatabase.Update (IProgressStatus monitor, System.String domain) [0x00000] in <filename unknown>:0 
  at Mono.Addins.Database.AddinDatabase.Repair (IProgressStatus monitor, System.String domain) [0x00000] in <filename unknown>:0 
  at Mono.Addins.AddinRegistry.Rebuild (IProgressStatus monitor) [0x00000] in <filename unknown>:0 
  at Banshee.ServiceStack.ServiceManager.InitializeAddins () [0x00075] in /build/buildd/banshee-2.0.0/src/Core/Banshee.Services/Banshee.ServiceStack/ServiceManager.cs:86 
  at Banshee.ServiceStack.ServiceManager.DefaultInitialize () [0x00005] in /build/buildd/banshee-2.0.0/src/Core/Banshee.Services/Banshee.ServiceStack/ServiceManager.cs:119 
  at Banshee.ServiceStack.Application.Initialize () [0x00000] in /build/buildd/banshee-2.0.0/src/Core/Banshee.Services/Banshee.ServiceStack/Application.cs:80 
  at Banshee.Gui.GtkBaseClient.Initialize (Boolean registerCommonServices) [0x00010] in /build/buildd/banshee-2.0.0/src/Core/Banshee.ThickClient/Banshee.Gui/GtkBaseClient.cs:143 
  at Banshee.Gui.GtkBaseClient..ctor (Boolean initializeDefault, System.String defaultIconName) [0x00013] in /build/buildd/banshee-2.0.0/src/Core/Banshee.ThickClient/Banshee.Gui/GtkBaseClient.cs:95 
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
  at Banshee.Gui.GtkBaseClient.Startup () [0x00000] in /build/buildd/banshee-2.0.0/src/Core/Banshee.ThickClient/Banshee.Gui/GtkBaseClient.cs:82 
  at Hyena.Gui.CleanRoomStartup.Startup (Hyena.Gui.StartupInvocationHandler startup) [0x00044] in /build/buildd/banshee-2.0.0/src/Hyena/Hyena.Gui/Hyena.Gui/CleanRoomStartup.cs:54 

.NET Version: 2.0.50727.1433
OS Version: Unix 2.6.35.28

Assembly Version Information:

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

Platform Information: Linux 2.6.35-28-generic i686 unknown GNU/Linux

Disribution Information:

[/etc/lsb-release]
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.10
DISTRIB_CODENAME=maverick
DISTRIB_DESCRIPTION="Ubuntu 10.10"

[/etc/debian_version]
squeeze/sid


This is the debug:

jay_hubert@DeepThought:~$ sudo killall banshee
[sudo] password for jay_hubert: 
banshee: no process found
jay_hubert@DeepThought:~$ banshee --debug
** Running Mono with --debug   **
[1 Info  08:57:17.811] Running Banshee 2.0.0: [Ubuntu 10.10 (linux-gnu, i686) @ 2011-04-08 22:47:09 UTC]
[1 Debug 08:57:17.896] Initializing GTK
Exception has been thrown by the target of an invocation.
System.Reflection.TargetInvocationException: Exception has been thrown by the target of an invocation. ---> System.InvalidOperationException: Could not read add-in description
  at Mono.Addins.Addin.get_Description () [0x00000] in <filename unknown>:0 
  at Mono.Addins.TreeNode.ResetCachedData () [0x00000] in <filename unknown>:0 
  at Mono.Addins.TreeNode.ResetCachedData () [0x00000] in <filename unknown>:0 
  at Mono.Addins.TreeNode.ResetCachedData () [0x00000] in <filename unknown>:0 
  at Mono.Addins.TreeNode.ResetCachedData () [0x00000] in <filename unknown>:0 
  at Mono.Addins.ExtensionContext.ResetCachedData () [0x00000] in <filename unknown>:0 
  at Mono.Addins.AddinSessionService.ResetCachedData () [0x00000] in <filename unknown>:0 
  at Mono.Addins.Database.AddinDatabase.ResetCachedData () [0x00000] in <filename unknown>:0 
  at Mono.Addins.Database.AddinDatabase.Update (IProgressStatus monitor, System.String domain) [0x00000] in <filename unknown>:0 
  at Mono.Addins.Database.AddinDatabase.Repair (IProgressStatus monitor, System.String domain) [0x00000] in <filename unknown>:0 
  at Mono.Addins.AddinRegistry.Rebuild (IProgressStatus monitor) [0x00000] in <filename unknown>:0 
  at Banshee.ServiceStack.ServiceManager.InitializeAddins () [0x00075] in /build/buildd/banshee-2.0.0/src/Core/Banshee.Services/Banshee.ServiceStack/ServiceManager.cs:86 
  at Banshee.ServiceStack.ServiceManager.DefaultInitialize () [0x00005] in /build/buildd/banshee-2.0.0/src/Core/Banshee.Services/Banshee.ServiceStack/ServiceManager.cs:119 
  at Banshee.ServiceStack.Application.Initialize () [0x00000] in /build/buildd/banshee-2.0.0/src/Core/Banshee.Services/Banshee.ServiceStack/Application.cs:80 
  at Banshee.Gui.GtkBaseClient.Initialize (Boolean registerCommonServices) [0x00010] in /build/buildd/banshee-2.0.0/src/Core/Banshee.ThickClient/Banshee.Gui/GtkBaseClient.cs:143 
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

At this point, it threw the same error that I get on launch.  Thanks for any and all help.

---

### Post by mc4man on 2011-04-10
You should probably mention how you got banshee 2.0 in maverick
(maverick uses 1.8 and it's banshee-1, banshee is just a link to banshee-1

The error seems similar to what would be seen in an incomplete switchover from banshee-1 to banshee naming

---

### Post by directhex on 2011-04-10
Try blowing away ~/.config/banshee-1/addin-db-001/

---

### Post by jay_outside on 2011-04-10
I can't find the exact site with the instructions I used for banshee 2.0, but this site seems to have similar instructions:

[http://www.jonathanmoeller.com/screed/?p=2793](http://www.jonathanmoeller.com/screed/?p=2793)


I'm not sure what you mean by blowing that command away....again, I'm very new to all of this.

---

### Post by mdhollis on 2011-04-11
I have the same issue.  I just filed a bug about this.  It happens to me in natty and maverick after latest upgrade.

[https://bugzilla.gnome.org/show_bug.cgi?id=647412]("https://bugzilla.gnome.org/show_bug.cgi?id=647412")

---

### Post by mdhollis on 2011-04-11
> You should probably mention how you got banshee 2.0 in maverick
(maverick uses 1.8 and it's banshee-1, banshee is just a link to banshee-1

Thats weird because I upgraded through update manager:confused:

---

### Post by directhex on 2011-04-11
> **jay_outside said:**
> I can't find the exact site with the instructions I used for banshee 2.0, but this site seems to have similar instructions:

[http://www.jonathanmoeller.com/screed/?p=2793](http://www.jonathanmoeller.com/screed/?p=2793)


I'm not sure what you mean by blowing that command away....again, I'm very new to all of this.

rm -r ~/.config/banshee-1/addin-db-001/

---

### Post by jay_outside on 2011-04-11
> **directhex said:**
> rm -r ~/.config/banshee-1/addin-db-001/

thank you but this did not work.  here is the banshee log that seems to contain more information on the error (for those who understand these things):

exec -a banshee mono  /usr/lib/banshee/Banshee.exe    --redirect-log --play-enqueued

[Info  11:50:50.214] Running Banshee 2.0.0: [Ubuntu 10.10 (linux-gnu, i686) @ 2011-04-08 22:47:09 UTC]
[Warn  11:50:51.154] Caught an exception - Hyena.Data.Sqlite.SqliteException: Sqlite error 11: database disk image is malformed (SQL: SELECT COUNT(*) FROM sqlite_master WHERE Type='table' AND Name='CoreTracks') (in `Hyena.Data.Sqlite')
  at Hyena.Data.Sqlite.Connection.CheckError (Int32 errorCode, System.String sql) [0x00000] in <filename unknown>:0 
  at Hyena.Data.Sqlite.Statement.CheckError (Int32 code) [0x00000] in <filename unknown>:0 
  at Hyena.Data.Sqlite.Statement..ctor (Hyena.Data.Sqlite.Connection connection, System.String sql) [0x00000] in <filename unknown>:0 
  at Hyena.Data.Sqlite.Connection.Query[Object] (System.String sql) [0x00000] in <filename unknown>:0 
  at Hyena.Data.Sqlite.HyenaSqliteCommand.Execute (Hyena.Data.Sqlite.HyenaSqliteConnection hconnection, Hyena.Data.Sqlite.Connection connection) [0x00000] in <filename unknown>:0 
[Warn  11:50:51.155] Service `Banshee.Database.BansheeDbConnection' not started: Sqlite error 11: database disk image is malformed (SQL: SELECT COUNT(*) FROM sqlite_master WHERE Type='table' AND Name='CoreTracks')
[Warn  11:50:51.155] Caught an exception - Hyena.Data.Sqlite.SqliteException: Sqlite error 11: database disk image is malformed (SQL: SELECT COUNT(*) FROM sqlite_master WHERE Type='table' AND Name='CoreTracks') (in `Hyena.Data.Sqlite')
  at Hyena.Data.Sqlite.Connection.CheckError (Int32 errorCode, System.String sql) [0x00000] in <filename unknown>:0 
  at Hyena.Data.Sqlite.Statement.CheckError (Int32 code) [0x00000] in <filename unknown>:0 
  at Hyena.Data.Sqlite.Statement..ctor (Hyena.Data.Sqlite.Connection connection, System.String sql) [0x00000] in <filename unknown>:0 
  at Hyena.Data.Sqlite.Connection.Query[Object] (System.String sql) [0x00000] in <filename unknown>:0 
  at Hyena.Data.Sqlite.HyenaSqliteCommand.Execute (Hyena.Data.Sqlite.HyenaSqliteConnection hconnection, Hyena.Data.Sqlite.Connection connection) [0x00000] in <filename unknown>:0 
[Info  11:50:53.733] Updating web proxy from GConf
[Warn  11:50:53.950] Caught an exception - System.NullReferenceException: Object reference not set to an instance of an object (in `Banshee.Lyrics')
  at Banshee.Lyrics.LyricsService.Banshee.ServiceStack.IExtensionService.Initialize () [0x00000] in <filename unknown>:0 
  at Banshee.ServiceStack.ServiceManager.StartExtension (Mono.Addins.TypeExtensionNode node) [0x00000] in <filename unknown>:0 
[Warn  11:50:53.950] Extension `Banshee.Lyrics.LyricsService' not started: Object reference not set to an instance of an object
[Warn  11:50:53.951] Caught an exception - System.NullReferenceException: Object reference not set to an instance of an object (in `Banshee.Services')
  at Banshee.Configuration.DatabaseConfigurationClient.get_Client () [0x00000] in <filename unknown>:0 
  at Banshee.AmazonMp3.AmazonMp3DownloaderService.Initialize () [0x00000] in <filename unknown>:0 
  at Banshee.ServiceStack.ServiceManager.StartExtension (Mono.Addins.TypeExtensionNode node) [0x00000] in <filename unknown>:0 
[Warn  11:50:53.951] Extension `Banshee.AmazonMp3.AmazonMp3DownloaderService' not started: Object reference not set to an instance of an object
[Warn  11:50:53.963] Caught an exception - System.NullReferenceException: Object reference not set to an instance of an object (in `Banshee.CoverArt')
  at Banshee.CoverArt.CoverArtService.Banshee.ServiceStack.IExtensionService.Initialize () [0x00000] in <filename unknown>:0 
  at Banshee.ServiceStack.ServiceManager.StartExtension (Mono.Addins.TypeExtensionNode node) [0x00000] in <filename unknown>:0 
[Warn  11:50:53.963] Extension `Banshee.CoverArt.CoverArtService' not started: Object reference not set to an instance of an object
[Warn  11:50:53.991] Caught an exception - System.NullReferenceException: Object reference not set to an instance of an object (in `Banshee.Lyrics')
  at Banshee.Lyrics.LyricsService.Banshee.ServiceStack.IExtensionService.Initialize () [0x00000] in <filename unknown>:0 
  at Banshee.ServiceStack.ServiceManager.StartExtension (Mono.Addins.TypeExtensionNode node) [0x00000] in <filename unknown>:0 
[Warn  11:50:53.991] Extension `Banshee.Lyrics.LyricsService' not started: Object reference not set to an instance of an object
[Warn  11:50:53.991] Caught an exception - System.NullReferenceException: Object reference not set to an instance of an object (in `Banshee.Services')
  at Banshee.Configuration.DatabaseConfigurationClient.get_Client () [0x00000] in <filename unknown>:0 
  at Banshee.AmazonMp3.AmazonMp3DownloaderService.Initialize () [0x00000] in <filename unknown>:0 
  at Banshee.ServiceStack.ServiceManager.StartExtension (Mono.Addins.TypeExtensionNode node) [0x00000] in <filename unknown>:0 
[Warn  11:50:53.991] Extension `Banshee.AmazonMp3.AmazonMp3DownloaderService' not started: Object reference not set to an instance of an object
[Warn  11:50:53.991] Caught an exception - System.NullReferenceException: Object reference not set to an instance of an object (in `Banshee.CoverArt')
  at Banshee.CoverArt.CoverArtService.Banshee.ServiceStack.IExtensionService.Initialize () [0x00000] in <filename unknown>:0 
  at Banshee.ServiceStack.ServiceManager.StartExtension (Mono.Addins.TypeExtensionNode node) [0x00000] in <filename unknown>:0 
[Warn  11:50:53.991] Extension `Banshee.CoverArt.CoverArtService' not started: Object reference not set to an instance of an object
[Info  11:50:53.992] All services are started 3.004576
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
libmirageaudio: destroy.

---

### Post by mdhollis on 2011-04-11
If you downgrade banshee in the package manager it should work fine, but you should add these logs to the link I posted earlier.

---

### Post by directhex on 2011-04-12
> **jay_outside said:**
> [Warn  11:50:51.154] Caught an exception - Hyena.Data.Sqlite.SqliteException: Sqlite error 11: database disk image is malformed (SQL: SELECT COUNT(*) FROM sqlite_master WHERE Type='table' AND Name='CoreTracks') (in `Hyena.Data.Sqlite')

Looks like your banshee database is corrupt. Remove it with "rm ~/.config/banshee-1/banshee.db" - but you'll need to re-import your tracks

---

### Post by Kinger23 on 2011-04-30
This worked for me

---

### Post by Miller's Garage on 2011-12-07
Hi, sorry to bump up an old - seemingly resolved - thread, but I'm having this problem as well but using the command to delete the database suggested before doesn't seem to be doing the trick for me; the terminal is kicking back "no such file or directory."  The error message I'm getting when I start up Banshee is "Encountered a Fatal Error, exception has been thrown by the target of an invocation," and then this:

An unhandled exception was thrown: Object reference not set to an instance of an object

  at Hyena.Data.Sqlite.SqliteModelCache`1[Banshee.Collection.Database.DatabaseArtistInfo].CheckCacheTable () [0x00000] in <filename unknown>:0 
  at Hyena.Data.Sqlite.SqliteModelCache`1[Banshee.Collection.Database.DatabaseArtistInfo]..ctor (Hyena.Data.Sqlite.HyenaSqliteConnection connection, System.String uuid, ICacheableDatabaseModel model, Hyena.Data.Sqlite.SqliteModelProvider`1 provider) [0x00000] in <filename unknown>:0 
  at Banshee.Database.BansheeModelCache`1[Banshee.Collection.Database.DatabaseArtistInfo]..ctor (Hyena.Data.Sqlite.HyenaSqliteConnection connection, System.String uuid, ICacheableDatabaseModel model, Hyena.Data.Sqlite.SqliteModelProvider`1 provider) [0x00000] in <filename unknown>:0 
  at Banshee.Collection.Database.DatabaseFilterListModel`2[Banshee.Collection.Database.DatabaseArtistInfo,Banshee.Collection.ArtistInfo]..ctor (System.String name, System.String label, Banshee.Sources.DatabaseSource source, Banshee.Collection.Database.DatabaseTrackListModel trackModel, Hyena.Data.Sqlite.HyenaSqliteConnection connection, Hyena.Data.Sqlite.SqliteModelProvider`1 provider, Banshee.Collection.ArtistInfo selectAllItem, System.String uuid) [0x00000] in <filename unknown>:0 
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
  at (wrapper managed-to-native) System.Reflection.MonoCMethod:InternalInvoke (System.Reflection.MonoCMethod,object,object[],System.Exception&)
  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] in <filename unknown>:0 
Exception has been thrown by the target of an invocation.

  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] in <filename unknown>:0 
  at System.Reflection.MonoCMethod.Invoke (BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] in <filename unknown>:0 
  at System.Reflection.ConstructorInfo.Invoke (System.Object[] parameters) [0x00000] in <filename unknown>:0 
  at System.Activator.CreateInstance (System.Type type, Boolean nonPublic) [0x00000] in <filename unknown>:0 
  at System.Activator.CreateInstance (System.Type type) [0x00000] in <filename unknown>:0 
  at Banshee.Gui.GtkBaseClient.Startup () [0x00000] in <filename unknown>:0 
  at Hyena.Gui.CleanRoomStartup.Startup (Hyena.Gui.StartupInvocationHandler startup) [0x00000] in <filename unknown>:0 

.NET Version: 4.0.30319.1
OS Version: Unix 3.0.0.13

Assembly Version Information:

Banshee.CoverArt (2.2.0.0)
Banshee.Emusic (2.2.0.0)
Banshee.Bpm (2.2.0.0)
Banshee.AmazonMp3 (2.2.0.0)
notify-sharp (0.4.0.0)
Banshee.SoundMenu (2.2.0.0)
Banshee.Mpris (2.2.0.0)
Banshee.MultimediaKeys (2.2.0.0)
Banshee.Daap (2.2.0.0)
Migo (2.2.0.0)
Banshee.Podcasting (2.2.0.0)
Banshee.AudioCd (2.2.0.0)
Banshee.Dap (2.2.0.0)
Lastfm (2.2.0.0)
Banshee.YouTube (2.2.0.0)
Banshee.WebBrowser (2.2.0.0)
Banshee.Wikipedia (2.2.0.0)
Banshee.Lastfm (2.2.0.0)
pango-sharp (2.12.0.0)
Mono.Cairo (4.0.0.0)
Banshee.Fixup (2.2.0.0)
Banshee.Widgets (2.2.0.0)
gio-sharp (2.14.0.0)
gudev-sharp (1.0.0.0)
Banshee.Gio (2.2.0.0)
Banshee.GStreamer (2.2.0.0)
System.Configuration (4.0.0.0)
dbus-sharp-glib (1.0.0.0)
gconf-sharp (2.24.0.0)
Banshee.Gnome (2.2.0.0)
Banshee.NowPlaying (2.2.0.0)
System.Xml (4.0.0.0)
Banshee.Core (2.2.0.0)
Hyena.Data.Sqlite (2.2.0.0)
gdk-sharp (2.12.0.0)
Mono.Addins (0.6.0.0)
atk-sharp (2.12.0.0)
Hyena.Gui (2.2.0.0)
Mono.Posix (4.0.0.0)
gtk-sharp (2.12.0.0)
Banshee.ThickClient (2.2.0.0)
Nereid (2.2.0.0)
DBus.Proxies (0.0.0.0)
System.Core (4.0.0.0)
Hyena (2.2.0.0)
dbus-sharp (1.0.0.0)
glib-sharp (2.12.0.0)
System (4.0.0.0)
Banshee.Services (2.2.0.0)
Banshee (2.2.0.0)
mscorlib (4.0.0.0)

Platform Information: Linux 3.0.0-13-generic-pae i686 i386 GNU/Linux

Disribution Information:

[/etc/lsb-release]
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"

[/etc/debian_version]
wheezy/sid

Thanks in advance for any help, I really appreciate it.

---

