---
title: "Banshee Fatal Error At Start"
date: 2010-01-28
forum: Multimedia Software
---

### Post by Naro on 2010-01-28
I did a quick search and only found [this](http://ubuntuforums.org/showthread.php?t=1314826&highlight=ubuntu+disk+malformed) thread, which didn't really help me.

Basically, when I try to open Banshee I get an error message telling me that the disk is malformed and then Banshee closes itself (faster than I can copy and paste the exact error).  I did some searching and apparently it's caused by the configuration file, but I did a complete removal of Banshee from the package manager, restarted the computer, and re-installed Banshee, but it's still giving me the error.  Any idea on how to fix this?

---

### Post by Naro on 2010-01-28
Update:

I just downloaded an update, and the error I'm not getting is this:

> An unhandled exception was thrown: Sqlite error

cannot start a transaction within a transaction

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
OS Version: Unix 2.6.31.17

Assembly Version Information:

System.Configuration (2.0.0.0)
Banshee.AudioCd (1.5.0.0)
Banshee.CoverArt (1.5.0.0)
Banshee.Bookmarks (1.5.0.0)
notify-sharp (0.4.0.0)
Banshee.NotificationArea (1.5.0.0)
Lastfm (1.5.0.0)
Banshee.Daap (1.5.0.0)
NDesk.DBus.Proxies (0.0.0.0)
Mono.Zeroconf.Providers.AvahiDBus (4.0.0.90)
Mono.Zeroconf (4.0.0.90)
Banshee.RemoteAudio (1.5.0.0)
taglib-sharp (2.0.3.2)
Migo (1.5.0.0)
Banshee.Podcasting (1.5.0.0)
Banshee.MultimediaKeys (1.5.0.0)
Banshee.Bpm (1.5.0.0)
Banshee.Lastfm (1.5.0.0)
pango-sharp (2.12.0.0)
Banshee.Widgets (1.5.0.0)
Banshee.Dap.Ipod (1.5.0.0)
Banshee.Dap (1.5.0.0)
Banshee.Hal (1.5.0.0)
Banshee.Unix (1.5.0.0)
Banshee.GStreamer (1.5.0.0)
gconf-sharp (2.24.0.0)
Banshee.Gnome (1.5.0.0)
Banshee.NowPlaying (1.5.0.0)
Mono.Media (1.5.0.0)
System.Transactions (2.0.0.0)
NDesk.DBus.GLib (1.0.0.0)
Mono.Cairo (2.0.0.0)
System.Data (2.0.0.0)
Mono.Data.Sqlite (1.5.0.0)
gdk-sharp (2.12.0.0)
Mono.Addins (0.4.0.0)
atk-sharp (2.12.0.0)
Hyena.Gui (1.5.0.0)
Mono.Posix (2.0.0.0)
gtk-sharp (2.12.0.0)
Banshee.Core (1.5.0.0)
Banshee.ThickClient (1.5.0.0)
Nereid (1.5.0.0)
System.Xml (2.0.0.0)
NDesk.DBus.Proxies (0.0.0.0)
System.Core (3.5.0.0)
System (2.0.0.0)
Hyena (1.5.0.0)
NDesk.DBus (1.0.0.0)
glib-sharp (2.12.0.0)
Banshee.Services (1.5.0.0)
Banshee (1.5.0.0)
mscorlib (2.0.0.0)

Platform Information: Linux 2.6.31-17-generic i686 unknown GNU/Linux

Disribution Information:

[/etc/lsb-release]
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.10
DISTRIB_CODENAME=karmic
DISTRIB_DESCRIPTION="Ubuntu 9.10"

[/etc/debian_version]
squeeze/sid

---

