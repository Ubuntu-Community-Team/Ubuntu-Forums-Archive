---
title: "Banshee crash on open"
date: 2012-02-09
forum: Multimedia Software
---

### Post by patman0623 on 2012-02-09
Every time I open Banshee, it crashes with the following message: 
> [Info  15:45:44.640] Running Banshee 2.2.1: [Ubuntu 11.10 (linux-gnu, x86_64) @ 2011-12-19 14:58:04 UTC]

(Banshee:4062): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(Banshee:4062): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(Banshee:4062): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(Banshee:4062): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
[Info  15:45:47.888] Updating web proxy from GConf
[Info  15:45:48.309] All services are started 2.875607
[Warn  15:45:49.150] Caught an exception - Hyena.Data.Sqlite.SqliteException: Sqlite error 14: unable to open database file (SQL: UPDATE CorePrimarySources SET CachedCount = 1291 WHERE PrimarySourceID = 1) (in `Hyena.Data.Sqlite')
  at Hyena.Data.Sqlite.Connection.CheckError (Int32 errorCode, System.String sql) [0x00000] in <filename unknown>:0 
  at Hyena.Data.Sqlite.Connection.Execute (System.String sql) [0x00000] in <filename unknown>:0 
  at Hyena.Data.Sqlite.HyenaSqliteCommand.Execute (Hyena.Data.Sqlite.HyenaSqliteConnection hconnection, Hyena.Data.Sqlite.Connection connection) [0x00000] in <filename unknown>:0 
Exception has been thrown by the target of an invocation.
System.Reflection.TargetInvocationException: Exception has been thrown by the target of an invocation. ---> Hyena.Data.Sqlite.SqliteException: Sqlite error 14: unable to open database file (SQL: UPDATE CorePrimarySources SET CachedCount = 1291 WHERE PrimarySourceID = 1)
  at Hyena.Data.Sqlite.Connection.CheckError (Int32 errorCode, System.String sql) [0x00000] in <filename unknown>:0 
  at Hyena.Data.Sqlite.Connection.Execute (System.String sql) [0x00000] in <filename unknown>:0 
  at Hyena.Data.Sqlite.HyenaSqliteCommand.Execute (Hyena.Data.Sqlite.HyenaSqliteConnection hconnection, Hyena.Data.Sqlite.Connection connection) [0x00000] in <filename unknown>:0 
  --- End of inner exception stack trace ---
  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] in <filename unknown>:0 
  at System.Reflection.MonoCMethod.Invoke (BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] in <filename unknown>:0 
  at System.Reflection.ConstructorInfo.Invoke (System.Object[] parameters) [0x00000] in <filename unknown>:0 
  at System.Activator.CreateInstance (System.Type type, Boolean nonPublic) [0x00000] in <filename unknown>:0 
  at System.Activator.CreateInstance (System.Type type) [0x00000] in <filename unknown>:0 
  at Banshee.Gui.GtkBaseClient.Startup () [0x00000] in <filename unknown>:0 
  at Hyena.Gui.CleanRoomStartup.Startup (Hyena.Gui.StartupInvocationHandler startup) [0x00000] in <filename unknown>:0 

I don't think it's worth filing a bug report, as it seems I can probably just delete an existing file somewhere (the database?). How can I fix this?

---

