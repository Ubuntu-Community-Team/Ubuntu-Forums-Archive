---
title: "banshee crashing, audioscrobbler plugin?"
date: 2006-11-14
forum: Multimedia &amp; Video
---

### Post by Uolirod on 2006-11-14
I am running edgy amd64 and banshee 0.11.1.  Banshee seems to run fine if I disable the audioscrobbler plugin but if I enable it banshee will crash the first time it attempts to report to last.fm.  It states that banshee has encountered a fatal error: could not find a part of the path "/home/~/.gnome2/banshee/plugins".  There is no plugins folder in the banshee directory.  Still trying to blindly stumble through this so any help is greatly appreciated.

Details-

```
An unhandled exception was thrown: Could not find a part of the path "/home/~/.gnome2/banshee/plugins".

at System.IO.FileStream..ctor (string,System.IO.FileMode,System.IO.FileAccess,System.IO.FileShare,int,bool,System.IO.FileOptions) <0x002d1>
at System.IO.FileStream..ctor (string,System.IO.FileMode,System.IO.FileAccess,System.IO.FileShare) <0x00046>
at (wrapper remoting-invoke-with-check) System.IO.FileStream..ctor (string,System.IO.FileMode,System.IO.FileAccess,System.IO.FileShare) <0x0006d>
at System.Xml.XmlTextWriter..ctor (string,System.Text.Encoding) <0x00048>
at Banshee.Plugins.Audioscrobbler.Queue.Save () <0x00069>
at Banshee.Plugins.Audioscrobbler.Engine.TransmitQueue () <0x00037>
at Banshee.Plugins.Audioscrobbler.Engine.StateTransitionHandler () <0x00199>
at (wrapper delegate-invoke) System.MulticastDelegate.invoke_bool () <0x0004c>
at TimeoutProxy.Handler () <0x00045>
at (wrapper native-to-managed) TimeoutProxy.Handler () <0x0005a>
in (unmanaged) 0x2b765ad8118a
at (wrapper managed-to-native) Gtk.Application.gtk_main () <0x0000b>
at Gtk.Application.Run () <0x00008>
at Banshee.BansheeEntry.Startup (string[]) <0x00823>
at (wrapper delegate-invoke) System.MulticastDelegate.invoke_void_string[] (string[]) <0x00060>
at Banshee.Gui.CleanRoomStartup.Startup (Banshee.Gui.CleanRoomStartup/StartupInvocationHandler,string[]) <0x000eb>

.NET Version: 2.0.50727.42

Assembly Version Information:

System.Web (2.0.0.0)
System.Configuration (2.0.0.0)
Mono.Security (2.0.0.0)
Recommendation (0.11.1.0)
Podcast (0.11.1.0)
NotificationAreaIcon (0.11.1.41354)
MiniMode (0.11.1.0)
MusicBrainz (0.11.1.41345)
MetadataSearch (0.11.1.41353)
MMKeys (0.11.1.41353)
avahi-sharp (1.0.0.0)
Daap (0.11.1.41235)
Banshee.Plugins.Audioscrobbler (0.11.1.41351)
ipod-sharp-ui (0.0.1.0)
njb-sharp (0.3.0.42394)
Banshee.Dap.Njb (0.11.1.41351)
gnome-vfs-sharp (2.16.0.0)
Banshee.Dap.MassStorage (0.11.1.41350)
ipod-sharp (0.0.1.0)
Banshee.Dap.Ipod (0.11.1.41350)
GStreamerPlayerEngine (0.11.1.41350)
System.Xml (2.0.0.0)
System.Data (2.0.0.0)
Mono.Data.SqliteClient (2.0.0.0)
pango-sharp (2.10.0.0)
Mono.Cairo (2.0.0.0)
Hal (0.0.0.0)
Last.FM (0.0.0.0)
NDesk.DBus (0.0.0.0)
Mono.Posix (2.0.0.0)
Banshee.Widgets (0.11.1.41347)
glade-sharp (2.10.0.0)
gnome-sharp (2.16.0.0)
gconf-sharp (2.16.0.0)
NDesk.DBus.GLib (0.0.0.0)
gdk-sharp (2.10.0.0)
System (2.0.0.0)
atk-sharp (2.10.0.0)
glib-sharp (2.10.0.0)
gtk-sharp (2.10.0.0)
Banshee.Base (0.11.1.41349)
banshee (0.11.1.41355)
mscorlib (2.0.0.0)

Platform Information: Linux 2.6.17-10-generic x86_64 unknown GNU/Linux

Disribution Information:

[/etc/debian_version]
testing/unstable

[/etc/lsb-release]
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=6.10
DISTRIB_CODENAME=edgy
DISTRIB_DESCRIPTION="Ubuntu 6.10"
```

---

### Post by ciscosurfer on 2006-11-14
If what you are looking for is a great Last.fm player, you can use **last-exit**, **lastfm** (both in the repos), or (I prefer) **Amarok**.  You can also download and install the Last.fm beta off the Last.fm site and use that.  I've had the best results with last-exit and Amarok, althought the beta is very nice as well, but you may have some trouble setting it up.  Your mileage may vary.

---

### Post by Uolirod on 2006-11-14
Well, actually I already have Last-Exit installed and though it doesn't work for saving streams it works well enough.  I was just trying to get Banshee to work for reporting my songs played with Banshee.  I like Banshee's layout and the fact that I can rip with it but I have no clue how to stop audioscrobbler from crashing it, other than turning it off.  Thanks though.

---

