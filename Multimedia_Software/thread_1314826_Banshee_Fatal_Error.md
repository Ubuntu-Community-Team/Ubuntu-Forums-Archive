---
title: "Banshee Fatal Error"
date: 2009-11-04
forum: Multimedia Software
---

### Post by DylanRush on 2009-11-04
Yeah, banshee just doesnt want to work anymore dont really know why, it happened out of no where.  i get:

```
An unhandled exception was thrown: The database disk image is malformed 
database disk image is malformed

  at Mono.Data.Sqlite.Sqlite3.Reset (Mono.Data.Sqlite.SqliteStatement stmt) [0x00000] 
  at Mono.Data.Sqlite.Sqlite3.Step (Mono.Data.Sqlite.SqliteStatement stmt) [0x00000] 
  at Mono.Data.Sqlite.SqliteCommand.ExecuteNonQuery () [0x00000] 
  at (wrapper remoting-invoke-with-check) Mono.Data.Sqlite.SqliteCommand:ExecuteNonQuery ()
  at Hyena.Data.Sqlite.HyenaSqliteCommand.Execute (Hyena.Data.Sqlite.HyenaSqliteConnection hconnection, Mono.Data.Sqlite.SqliteConnection connection) [0x00000] 
Exception has been thrown by the target of an invocation.

  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  at System.Reflection.MonoCMethod.Invoke (BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  at System.Reflection.ConstructorInfo.Invoke (System.Object[] parameters) [0x00000] 
  at System.Activator.CreateInstance (System.Type type, Boolean nonPublic) [0x00000] 
  at System.Activator.CreateInstance (System.Type type) [0x00000] 
  at Banshee.Gui.GtkBaseClient.Startup () [0x00000] 
  at Hyena.Gui.CleanRoomStartup.Startup (Hyena.Gui.StartupInvocationHandler startup) [0x00000] 

.NET Version: 2.0.50727.1433
OS Version: Unix 2.6.31.14

Assembly Version Information:

Mono.Media (1.5.0.0)
System.Core (3.5.0.0)
System.Transactions (2.0.0.0)
NDesk.DBus.GLib (1.0.0.0)
Mono.Cairo (2.0.0.0)
System.Data (2.0.0.0)
Mono.Data.Sqlite (1.5.0.0)
gdk-sharp (2.12.0.0)
Mono.Addins (0.4.0.0)
atk-sharp (2.12.0.0)
Hyena.Gui (1.5.0.0)
gtk-sharp (2.12.0.0)
Banshee.ThickClient (1.5.0.0)
Nereid (1.5.0.0)
System.Xml (2.0.0.0)
NDesk.DBus.Proxies (0.0.0.0)
Mono.Posix (2.0.0.0)
Banshee.Core (1.5.0.0)
System (2.0.0.0)
Hyena (1.5.0.0)
NDesk.DBus (1.0.0.0)
glib-sharp (2.12.0.0)
Banshee.Services (1.5.0.0)
Banshee (1.5.0.0)
mscorlib (2.0.0.0)

Platform Information: Linux 2.6.31-14-generic x86_64 unknown GNU/Linux

Disribution Information:

[/etc/lsb-release]
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.10
DISTRIB_CODENAME=karmic
DISTRIB_DESCRIPTION="Ubuntu 9.10"

[/etc/debian_version]
squeeze/sid


```

any help?

---

### Post by axeligl on 2009-12-04
Same problem here. Any solution?

---

### Post by robstel on 2009-12-10
just found this at [http://forums.xkcd.com/viewtopic.php?f=20&t=47863:](http://forums.xkcd.com/viewtopic.php?f=20&t=47863:)

to delete your banshee settings:
[FONT="Courier New"]> mv ~/.config/banshee-1 ~/.config/banshee-1.bak
> rm -rf ~/.cache/.banshee-1
[/FONT]

this gets Banshee working again, but loses all your playlists and ratings :(

---

### Post by axeligl on 2009-12-13
Yeah, I know that. That's how I'm using banshee now but I wonder if there is any way I can rescue all my ratings.
Thanks!

---

