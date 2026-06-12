---
title: "Banshee Crashing After Launch"
date: 2011-04-26
forum: Multimedia Software
---

### Post by treeflappa on 2011-04-26
It was working and works on my gf's login but not mine.

I'm getting the following, can anyone help?

Encountered a Fatal Error.

An unhandled exception was thrown: The database disk image is malformed
database disk image is malformed

  at Mono.Data.Sqlite.Sqlite3.Reset (Mono.Data.Sqlite.SqliteStatement stmt) [0x00000] in <filename unknown>:0 
  at Mono.Data.Sqlite.Sqlite3.Step (Mono.Data.Sqlite.SqliteStatement stmt) [0x00000] in <filename unknown>:0 
  at Mono.Data.Sqlite.SqliteCommand.ExecuteNonQuery () [0x00000] in <filename unknown>:0 
  at (wrapper remoting-invoke-with-check) Mono.Data.Sqlite.SqliteCommand:ExecuteNonQuery ()
  at Hyena.Data.Sqlite.HyenaSqliteCommand.Execute (Hyena.Data.Sqlite.HyenaSqliteConnection hconnection, Mono.Data.Sqlite.SqliteConnection connection) [0x00000] in <filename unknown>:0 
Exception has been thrown by the target of an invocation.

  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] in <filename unknown>:0 
  at System.Reflection.MonoCMethod.Invoke (BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] in <filename unknown>:0 
  at System.Reflection.ConstructorInfo.Invoke (System.Object[] parameters) [0x00000] in <filename unknown>:0 
  at System.Activator.CreateInstance (System.Type type, Boolean nonPublic) [0x00000] in <filename unknown>:0 
  at System.Activator.CreateInstance (System.Type type) [0x00000] in <filename unknown>:0 
  at Banshee.Gui.GtkBaseClient.Startup () [0x00000] in <filename unknown>:0 
  at Hyena.Gui.CleanRoomStartup.Startup (Hyena.Gui.StartupInvocationHandler startup) [0x00000] in <filename unknown>:0 

.NET Version: 2.0.50727.1433
OS Version: Unix 2.6.35.28

Assembly Version Information:

Banshee.AudioCd (1.8.0.0)
Banshee.CoverArt (1.8.0.0)
notify-sharp (0.4.0.0)
Banshee.NotificationArea (1.8.0.0)
Banshee.Daap (1.8.0.0)
Migo (1.8.0.0)
Banshee.Podcasting (1.8.0.0)
Banshee.Dap (1.8.0.0)
Banshee.LibraryWatcher (1.8.0.0)
Lastfm (1.8.0.0)
Banshee.MultimediaKeys (1.8.0.0)
Banshee.Bpm (1.8.0.0)
Banshee.YouTube (1.8.0.0)
Banshee.WebBrowser (1.8.0.0)
Banshee.Wikipedia (1.8.0.0)
Banshee.Lastfm (1.8.0.0)
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

Platform Information: Linux 2.6.35-28-generic i686 unknown GNU/Linux

Disribution Information:

[/etc/lsb-release]
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.10
DISTRIB_CODENAME=maverick
DISTRIB_DESCRIPTION="Ubuntu 10.10"

[/etc/debian_version]
squeeze/sid

---

