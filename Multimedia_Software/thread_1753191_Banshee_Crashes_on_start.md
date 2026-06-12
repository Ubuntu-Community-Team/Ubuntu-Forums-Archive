---
title: "Banshee Crashes on start"
date: 2011-05-08
forum: Multimedia Software
---

### Post by ga5im on 2011-05-08
Banshee outputs this error when i start it

An unhandled exception was thrown: Sqlite error 14: unable to open database file (SQL: 
                BEGIN TRANSACTION;
                     DELETE FROM CoreSmartPlaylistEntries WHERE SmartPlaylistID IN (SELECT  SmartPlaylistID FROM CoreSmartPlaylists WHERE IsTemporary = 1);
                    DELETE FROM CoreSmartPlaylists WHERE IsTemporary = 1;
                COMMIT TRANSACTION)

  at Hyena.Data.Sqlite.Connection.CheckError (Int32 errorCode, System.String sql) [0x00000] in <filename unknown>:0 
  at Hyena.Data.Sqlite.Connection.Execute (System.String sql) [0x00000] in <filename unknown>:0 
   at Hyena.Data.Sqlite.HyenaSqliteCommand.Execute  (Hyena.Data.Sqlite.HyenaSqliteConnection hconnection,  Hyena.Data.Sqlite.Connection connection) [0x00000] in <filename  unknown>:0 
Exception has been thrown by the target of an invocation.

   at System.Reflection.MonoCMethod.Invoke (System.Object obj,  BindingFlags invokeAttr, System.Reflection.Binder binder,  System.Object[] parameters, System.Globalization.CultureInfo culture)  [0x00000] in <filename unknown>:0 
  at  System.Reflection.MonoCMethod.Invoke (BindingFlags invokeAttr,  System.Reflection.Binder binder, System.Object[] parameters,  System.Globalization.CultureInfo culture) [0x00000] in <filename  unknown>:0 
  at System.Reflection.ConstructorInfo.Invoke (System.Object[] parameters) [0x00000] in <filename unknown>:0 
  at System.Activator.CreateInstance (System.Type type, Boolean nonPublic) [0x00000] in <filename unknown>:0 
  at System.Activator.CreateInstance (System.Type type) [0x00000] in <filename unknown>:0 
  at Banshee.Gui.GtkBaseClient.Startup () [0x00000] in <filename unknown>:0 
  at Hyena.Gui.CleanRoomStartup.Startup (Hyena.Gui.StartupInvocationHandler startup) [0x00000] in <filename unknown>:0 

.NET Version: 2.0.50727.1433
OS Version: Unix 2.6.38.8

Assembly Version Information:

gkeyfile-sharp (1.0.0.0)
Banshee.AudioCd (2.0.0.0)
Banshee.CoverArt (2.0.0.0)
Banshee.AmazonMp3 (2.0.0.0)
Banshee.Daap (2.0.0.0)
notify-sharp (0.4.0.0)
Banshee.SoundMenu (2.0.0.0)
Banshee.Mpris (2.0.0.0)
Migo (2.0.0.0)
Banshee.Podcasting (2.0.0.0)
Banshee.Dap (2.0.0.0)
Lastfm (2.0.0.0)
Banshee.MultimediaKeys (2.0.0.0)
Banshee.Bpm (2.0.0.0)
Banshee.WebBrowser (2.0.0.0)
Banshee.Wikipedia (2.0.0.0)
Banshee.Lastfm (2.0.0.0)
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

Platform Information: Linux 2.6.38-8-generic i686 i386 GNU/Linux

Disribution Information:

[/etc/lsb-release]
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.04
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu 11.04"

[/etc/debian_version]
squeeze/sid


Running Ubuntu 11.04

---

### Post by ga5im on 2011-05-09
And I have a solution! 
The following commands shld clear your database:

mv ~/.config/banshee-1 ~/.config/banshee-1.bak
rm -rf ~/.cache/.banshee-1

Of course, u will need to reimport artwork etc..

---

### Post by jmikii on 2012-04-07
Thanks ga5i, that worked also for me.

---

