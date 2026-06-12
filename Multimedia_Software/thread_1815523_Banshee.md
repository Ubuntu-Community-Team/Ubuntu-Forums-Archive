---
title: "Banshee"
date: 2011-07-31
forum: Multimedia Software
---

### Post by Ederico on 2011-07-31
Hello all,

I'm experiencing a problem running Banshee 2.0 on my Ubuntu 11.04 system. Basically, I'm getting the following fatal error, the code of which is quoted hereunder. Of note is that uninstalling and reinstalling Banshee (through Ubuntu Software Centre) doesn't fix this problem. 

Incidentally or not, I also seem to have a problem with my other (and preferred) media player, Amarok. I created a thread on this problem [HERE]("http://ubuntuforums.org/showthread.php?p=11104999#post11104999").

This is the error code:

```
Si è verificata un eccezione non gestita: Sqlite error 14: unable to open database file (SQL: UPDATE CorePrimarySources SET CachedCount = 1568 WHERE PrimarySourceID = 1)

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

.NET Version: 2.0.50727.1433
OS Version: Unix 2.6.38.10

Assembly Version Information:

gkeyfile-sharp (1.0.0.0)
Banshee.AudioCd (2.0.0.0)
Banshee.MiniMode (2.0.0.0)
Banshee.CoverArt (2.0.0.0)
Banshee.AmazonMp3 (2.0.0.0)
Banshee.Daap (2.0.0.0)
Banshee.Mpris (2.0.0.0)
Lastfm (2.0.0.0)
Migo (2.0.0.0)
Banshee.Podcasting (2.0.0.0)
Banshee.Dap (2.0.0.0)
notify-sharp (0.4.0.0)
Banshee.NotificationArea (2.0.0.0)
Banshee.LibraryWatcher (2.0.0.0)
Banshee.MultimediaKeys (2.0.0.0)
Banshee.Bpm (2.0.0.0)
Banshee.YouTube (2.0.0.0)
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

Platform Information: Linux 2.6.38-10-generic i686 i386 GNU/Linux

Disribution Information:

[/etc/lsb-release]
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.04
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu 11.04"

[/etc/debian_version]
squeeze/sid


```

I hope someone can help. Thanks beforehand.

Best Regards,
Ederico.

---

### Post by directhex on 2011-07-31
Try this guide: [http://thelinuxexperiment.com/guinea-pigs/jon-f/recovering-a-corrupted-banshee-database/](http://thelinuxexperiment.com/guinea-pigs/jon-f/recovering-a-corrupted-banshee-database/)

Looks like your banshee.db is hosed.

---

### Post by Ederico on 2011-08-01
Thanks for the tip, I didn't really manage using it. However, thanks to it I found another way round. I just deleted the banshee-1 folder in .config and am recreating the database from scratch. That should fix my problem. Thanks!

---

