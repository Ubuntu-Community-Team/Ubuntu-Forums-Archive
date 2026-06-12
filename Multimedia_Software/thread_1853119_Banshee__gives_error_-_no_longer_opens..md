---
title: "Banshee  gives error - no longer opens."
date: 2011-10-01
forum: Multimedia Software
---

### Post by Stray Wolf on 2011-10-01
On a fresh install of 11.04 Banshee opened long enough import my music and get my audio working. It may have opened 4 or 5 times then this:
```
[Info  14:57:40.989] Running Banshee 2.0.0: [Ubuntu 11.04 (linux-gnu, x86_64) @ 2011-06-28 05:39:10 UTC]

(Banshee:2440): Gtk-WARNING **: Theme directory scalable/status/32 of theme Buttonized has no size field

[Info  14:57:46.766] Updating web proxy from GConf
[Info  14:57:46.985] All services are started 5.052326
[Warn  14:57:47.111] Caught an exception - Hyena.Data.Sqlite.SqliteException: Sqlite error 11: database disk image is malformed (SQL: 
                BEGIN TRANSACTION;
                    DELETE FROM CoreSmartPlaylistEntries WHERE SmartPlaylistID IN (SELECT SmartPlaylistID FROM CoreSmartPlaylists WHERE IsTemporary = 1);
                    DELETE FROM CoreSmartPlaylists WHERE IsTemporary = 1;
                COMMIT TRANSACTION) (in `Hyena.Data.Sqlite')
  at Hyena.Data.Sqlite.Connection.CheckError (Int32 errorCode, System.String sql) [0x00000] in <filename unknown>:0 
  at Hyena.Data.Sqlite.Connection.Execute (System.String sql) [0x00000] in <filename unknown>:0 
  at Hyena.Data.Sqlite.HyenaSqliteCommand.Execute (Hyena.Data.Sqlite.HyenaSqliteConnection hconnection, Hyena.Data.Sqlite.Connection connection) [0x00000] in <filename unknown>:0 
Exception has been thrown by the target of an invocation.
System.Reflection.TargetInvocationException: Exception has been thrown by the target of an invocation. ---> Hyena.Data.Sqlite.SqliteException: Sqlite error 11: database disk image is malformed (SQL: 
                BEGIN TRANSACTION;
                    DELETE FROM CoreSmartPlaylistEntries WHERE SmartPlaylistID IN (SELECT SmartPlaylistID FROM CoreSmartPlaylists WHERE IsTemporary = 1);
                    DELETE FROM CoreSmartPlaylists WHERE IsTemporary = 1;
                COMMIT TRANSACTION)
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

```I reinstalled Banshee but that did nothing.  Anyone?

---

### Post by Stray Wolf on 2011-10-03
No one helped.  That's okay.  This place is full of busy people and no one's obligated.  Solved by re-installing 11.04 - not choosing additional options during install (software updates and third-party) - allowing driver's to install after first  boot - restarting- allowing software updates to install - restarting - making sure correct audio output is set in sound preferences - then running Banshee.

---

