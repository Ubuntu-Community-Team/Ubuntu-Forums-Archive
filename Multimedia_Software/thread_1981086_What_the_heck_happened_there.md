---
title: "What the heck happened there ?"
date: 2012-05-16
forum: Multimedia Software
---

### Post by Swagman on 2012-05-16
I just used the search box and clicked on a sound file to play .. Ironically it was Shampoo's "Trouble"

Not that I'm bothered and I haven't tried to launch again, *yet*. I just thought I'd better copy & paste that error message first.


> 

An unhandled exception was thrown: Sqlite error 5: database is locked (SQL: 
                INSERT INTO CoreSmartPlaylists
                    (Name, Condition, OrderBy, LimitNumber, LimitCriterion, PrimarySourceID, IsTemporary, IsHiddenWhenEmpty)
                    VALUES ('Favourites', '<request><query banshee-version="1"><greaterThanEquals><field name="rating" /><int>4</int></greaterThanEquals></query></request>', NULL, NULL, NULL, 1, 0, 1))

  at Hyena.Data.Sqlite.Connection.CheckError (Int32 errorCode, System.String sql) [0x00000] in <filename unknown>:0 
  at Hyena.Data.Sqlite.Connection.Execute (System.String sql) [0x00000] in <filename unknown>:0 
  at Hyena.Data.Sqlite.HyenaSqliteCommand.Execute (Hyena.Data.Sqlite.HyenaSqliteConnection hconnection, Hyena.Data.Sqlite.Connection connection) [0x00000] in <filename unknown>:0 
Exception has been thrown by the target of an invocation.

  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] in <filename unknown>:0 
  at System.Reflection.MonoCMethod.Invoke (BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] in <filename unknown>:0 
  at System.Reflection.ConstructorInfo.Invoke (System.Object[] parameters) [0x00000] in <filename unknown>:0 
  at System.Activator.CreateInstance (System.Type type, Boolean nonPublic) [0x00000] in <filename unknown>:0 
  at System.Activator.CreateInstance (System.Type type) [0x00000] in <filename unknown>:0 
  at Banshee.Gui.GtkBaseClient.Startup () [0x00000] in <filename unknown>:0 
  at Hyena.Gui.CleanRoomStartup.Startup (Hyena.Gui.StartupInvocationHandler startup) [0x00000] in <filename unknown>:0 

.NET Version: 4.0.30319.1
OS Version: Unix 3.0.0.20

Assembly Version Information:

notify-sharp (0.4.0.0)
Banshee.SoundMenu (2.2.0.0)
Banshee.Podcasting (2.2.0.0)
Banshee.MultimediaKeys (2.2.0.0)
Banshee.Mpris (2.2.0.0)
Lastfm (2.2.0.0)
Migo (2.2.0.0)
Banshee.Emusic (2.2.0.0)
Banshee.Dap (2.2.0.0)
Banshee.Daap (2.2.0.0)
Banshee.CoverArt (2.2.0.0)
Banshee.Bpm (2.2.0.0)
gkeyfile-sharp (1.0.0.0)
Banshee.AudioCd (2.2.0.0)
Banshee.AmazonMp3 (2.2.0.0)
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

Platform Information: Linux 3.0.0-20-generic-pae i686 i386 GNU/Linux

Disribution Information:

[/etc/lsb-release]
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"

[/etc/debian_version]
wheezy/sid



Quote tags used so you don't have to scroll

---

### Post by Swagman on 2012-05-16
Huh.. Working ok now..

Weird is weird !!

---

### Post by mörgæs on 2012-05-16
In that case, please mark the thread 'solved'.

---

