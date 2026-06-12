---
title: "Banshee Error"
date: 2010-03-06
forum: Multimedia Software
---

### Post by ljrmorgan on 2010-03-06
I've been using the PPA version of banshee, and I got this error - just wondering if anyone else has it too! I'm able to play a song, but when the song finishes and the next one starts I get this error:

Banshee Encountered a Fatal Error

Object reference not sent to an instance of an object

Error details:
```

An unhandled exception was thrown: Object reference not set to an instance of an object

at Hyena.Gui.Theming.GtkTheme.GetCairoTextMidColor (Gtk.Widget) <0x00017>
at Banshee.NotificationArea.NotificationAreaService.get_TextLightColor () <0x0002f>
at Banshee.NotificationArea.NotificationAreaService.MarkupFormat (string,string[]) <0x00043>
at Banshee.NotificationArea.NotificationAreaService.GetByFrom (string,string,string,string) <0x000d7>
at Banshee.NotificationArea.NotificationAreaService.ShowTrackNotification () <0x0043b>
at Banshee.NotificationArea.NotificationAreaService.OnPlayerEvent (Banshee.MediaEngine.PlayerEventArgs) <0x00063>
at Banshee.MediaEngine.PlayerEngineService.RaiseEvent (Banshee.MediaEngine.PlayerEventArgs) <0x0012a>
at Banshee.MediaEngine.PlayerEngineService.OnEngineEventChanged (Banshee.MediaEngine.PlayerEventArgs) <0x000cb>
at Banshee.MediaEngine.PlayerEngine.RaiseEventChanged (Banshee.MediaEngine.PlayerEventArgs) <0x00027>
at Banshee.MediaEngine.PlayerEngine.OnEventChanged (Banshee.MediaEngine.PlayerEventArgs) <0x00047>
at Banshee.MediaEngine.PlayerEngine.OnEventChanged (Banshee.MediaEngine.PlayerEvent) <0x00032>
at Banshee.GStreamer.PlayerEngine.OnStateChange (intptr,Banshee.GStreamer.GstState,Banshee.GStreamer.GstState,Banshee.GStreamer.GstState) <0x0007f>
at (wrapper native-to-managed) Banshee.GStreamer.PlayerEngine.OnStateChange (intptr,Banshee.GStreamer.GstState,Banshee.GStreamer.GstState,Banshee.GStreamer.GstState) <0x0007e>
at (wrapper managed-to-native) Gtk.Application.gtk_main () <0x00052>
at Gtk.Application.Run () <0x0000b>
at Banshee.Gui.GtkBaseClient.Run () <0x00047>
at Banshee.Gui.GtkBaseClient.Startup () <0x00046>
at Hyena.Gui.CleanRoomStartup.Startup (Hyena.Gui.CleanRoomStartup/StartupInvocationHandler) <0x0008e>


.NET Version: 2.0.50727.1433
OS Version: Unix 2.6.31.20

Assembly Version Information:

System.Configuration (2.0.0.0)
taglib-sharp (2.0.3.6)
Banshee.PlayQueue (1.5.0.0)
Banshee.AudioCd (1.5.0.0)
Banshee.CoverArt (1.5.0.0)
notify-sharp (0.4.0.0)
Banshee.NotificationArea (1.5.0.0)
Lastfm (1.5.0.0)
Banshee.MultimediaKeys (1.5.0.0)
webkit-sharp (1.0.0.0)
Banshee.Wikipedia (1.5.0.0)
Banshee.Lastfm (1.5.0.0)
pango-sharp (2.12.0.0)
Banshee.Widgets (1.5.0.0)
Banshee.Hal (1.5.0.0)
Banshee.Unix (1.5.0.0)
Banshee.GStreamer (1.5.0.0)
Mono.Media (1.5.0.0)
System.Transactions (2.0.0.0)
NDesk.DBus.GLib (1.0.0.0)
gconf-sharp (2.24.0.0)
Banshee.Gnome (1.5.0.0)
Banshee.NowPlaying (1.5.0.0)
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

Platform Information: Linux 2.6.31-20-generic x86_64 unknown GNU/Linux

Disribution Information:

[/etc/lsb-release]
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.10
DISTRIB_CODENAME=karmic
DISTRIB_DESCRIPTION="Ubuntu 9.10"

[/etc/debian_version]
squeeze/sid

```

---

### Post by BinaryMn on 2010-03-07
I've been using the PPA version also. I discovered that the SQLite3 database became corrupted overnight, so I renamed the corrupted database so I can go back and pull playlists and whatnot from it later.

As soon as I started over with a new database, I've been getting this same error. I'm going to file a bug [s]against the current version in the PPA[/s] upstream because the PPA is just compiling from git.

---

### Post by BinaryMn on 2010-03-07
FWIW, whihile my original database is corrupted (looks like the Mirage Playlist Generator extension broke it), it takes care of the crashing when switching to new songs.

I dropped down to 1.5.4, FYI.

---

### Post by ljrmorgan on 2010-03-07
The latest build from the daily PPA (came out just under an hour ago) doesn't seem to have this problem, or at least I haven't come across it yet. My library doesn't seem to have been affected.

---

### Post by BinaryMn on 2010-03-07
Bug is filed.

[https://bugzilla.gnome.org/show_bug.cgi?id=612138](https://bugzilla.gnome.org/show_bug.cgi?id=612138)

---

