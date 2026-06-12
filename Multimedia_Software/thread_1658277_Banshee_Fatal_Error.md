---
title: "Banshee Fatal Error"
date: 2011-01-02
forum: Multimedia Software
---

### Post by gregorydillon on 2011-01-02
This is what it tells me.,  Anyone know what to do?  Thanks.


An unhandled exception was thrown: Object reference not set to an instance of an object

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
OS Version: Unix 2.6.35.24

---

### Post by gregorydillon on 2011-01-04
I think I will reinstall the who OS.

---

