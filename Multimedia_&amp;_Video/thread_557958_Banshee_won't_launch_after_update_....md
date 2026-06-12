---
title: "Banshee won't launch after update ..."
date: 2007-09-23
forum: Multimedia &amp; Video
---

### Post by nirv117 on 2007-09-23
After applying an update to Ubuntu (7.04) about 3 days ago banshee fails to start.

I can't remember which update it was.  It was one that the update manager asked to install.  Is there a history saved of those anywhere?

When I try to run banshee I get the following error:

banshee Encountered a Fatal Error
An unhandled exception was thrown: The given key was not present in the dictionary.

  at System.Collections.Generic.Dictionary`2[System.Int32,Banshee.Base.TrackInfo].get_Item (Int32 ) [0x00000] 
  at Banshee.Sources.PlaylistSource.LoadFromDatabase () [0x00000] 
  at Banshee.Sources.PlaylistSource..ctor (Int32 id) [0x00000] 
  at Banshee.Sources.PlaylistUtil.LoadSources () [0x00000] 
  at Banshee.Sources.LibrarySource.LoadPlaylists () [0x00000] 
  at Banshee.Sources.LibrarySource..ctor () [0x00000] 
  at Banshee.Sources.LibrarySource.get_Instance () [0x00000] 
  at Banshee.PlayerUI.OnStartupRunFinished (System.Object o, System.EventArgs args) [0x00000] 
  at (wrapper delegate-invoke) System.MulticastDelegate:invoke_void_object_EventArgs (object,System.EventArgs)
  at Banshee.Base.ComponentInitializer.OnRunFinished () [0x00000] 
  at Banshee.Base.ComponentInitializer.Run () [0x00000] 
  at Banshee.Base.Globals.Initialize (Banshee.Base.ComponentInitializerHandler interfaceStartupHandler) [0x00000] 
  at Banshee.BansheeEntry.Startup (System.String[] args) [0x00000] 
  at (wrapper delegate-invoke) System.MulticastDelegate:invoke_void_string[] (string[])
  at Banshee.Gui.CleanRoomStartup.Startup (Banshee.Gui.StartupInvocationHandler startup, System.String[] args) [0x00000] 
.NET Version: 2.0.50727.42

Assembly Version Information:

System.Configuration (2.0.0.0)
glade-sharp (2.10.0.0)
Boo.Lang.Compiler (1.0.0.0)
iTunesImporter (1.0.2549.7219)
Banshee.Plugins.Recommendation (0.12.1.12341)
Banshee.Plugins.Radio (0.12.1.12340)
Banshee.Plugins.Podcast (0.12.1.12339)
Banshee.Plugins.NotificationAreaIcon (0.12.1.12337)
Banshee.Plugins.MiniMode (0.12.1.12336)
Banshee.Plugins.MetadataSearch (0.12.1.12335)
Banshee.Plugins.MMKeys (0.12.1.12336)
Banshee.Plugins.Audioscrobbler (0.12.1.12332)
njb-sharp (0.3.0.27013)
Banshee.Dap.Njb (0.12.1.12331)
gnome-vfs-sharp (2.16.0.0)
Banshee.Dap.MassStorage (0.12.1.12331)
ipod-sharp (0.0.1.0)
Banshee.Dap.Ipod (0.12.1.12330)
Banshee.MediaEngine.GStreamer (0.12.1.12329)
System.Xml (2.0.0.0)
System.Transactions (2.0.0.0)
gconf-sharp (2.16.0.0)
System.Data (2.0.0.0)
Mono.Data.SqliteClient (2.0.0.0)
pango-sharp (2.10.0.0)
Mono.Cairo (2.0.0.0)
Hal (0.0.0.0)
Banshee.Widgets (0.12.1.12322)
Last.FM (0.0.0.0)
NDesk.DBus (1.0.0.0)
Mono.Posix (2.0.0.0)
NDesk.DBus.GLib (1.0.0.0)
gnome-sharp (2.16.0.0)
gdk-sharp (2.10.0.0)
System (2.0.0.0)
atk-sharp (2.10.0.0)
glib-sharp (2.10.0.0)
gtk-sharp (2.10.0.0)
Banshee.Base (0.12.1.12326)
banshee (0.12.1.12328)
mscorlib (2.0.0.0)

Platform Information: Linux 2.6.20-16-generic i686 unknown GNU/Linux

Disribution Information:

[/etc/debian_version]
4.0

[/etc/lsb-release]
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=7.04
DISTRIB_CODENAME=feisty
DISTRIB_DESCRIPTION="Ubuntu 7.04"

---

### Post by IceReaver75 on 2007-10-05
After an update today the same thing is happening here but alittle different message.  It was working yesterday and now its not but im pretty sure the only updates I had today were for open office though:  Anyways this is what I get:

An unhandled exception was thrown: Unable to open the session message bus.

  at NDesk.DBus.Bus.get_Session () [0x00000] 
  at NDesk.DBus.BusG.Init () [0x00000] 
  at Banshee.ServiceStack.DBusServiceManager..ctor () [0x00000] 
  at Banshee.ServiceStack.ServiceManager.Run () [0x00000] 
  at Banshee.ServiceStack.Application.Run () [0x00000] 
  at (wrapper delegate-invoke) System.MulticastDelegate:invoke_void ()
  at Banshee.Base.ComponentInitializer.Run () [0x00000] 
  at Banshee.Base.Globals.Initialize (Banshee.Base.ComponentInitializerHandler interfaceStartupHandler) [0x00000] 
  at Banshee.BansheeEntry.Startup (System.String[] args) [0x00000] 
  at (wrapper delegate-invoke) System.MulticastDelegate:invoke_void_string[] (string[])
  at Banshee.Gui.CleanRoomStartup.Startup (Banshee.Gui.StartupInvocationHandler startup, System.String[] args) [0x00000] 
.NET Version: 2.0.50727.42

Assembly Version Information:

System.Data (2.0.0.0)
pango-sharp (2.10.0.0)
Mono.Cairo (2.0.0.0)
Hal (0.0.0.0)
Banshee.Services (0.0.0.0)
Banshee.Widgets (0.13.1.42088)
Last.FM (0.0.0.0)
NDesk.DBus (1.0.0.0)
Mono.Posix (2.0.0.0)
NDesk.DBus.GLib (1.0.0.0)
gnome-sharp (2.16.0.0)
gdk-sharp (2.10.0.0)
System (2.0.0.0)
atk-sharp (2.10.0.0)
glib-sharp (2.10.0.0)
gtk-sharp (2.10.0.0)
Banshee.Base (0.13.1.42093)
banshee (0.13.1.42097)
mscorlib (2.0.0.0)

Platform Information: Linux 2.6.20-16-generic i686 unknown GNU/Linux

Disribution Information:

[/etc/debian_version]
4.0

[/etc/lsb-release]
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=7.04
DISTRIB_CODENAME=feisty
DISTRIB_DESCRIPTION="Ubuntu 7.04"

---

### Post by misfitpierce on 2007-10-05
Mine still works fine... Where did you get package? I got from getdeb and it works fine with new updates.

---

### Post by IceReaver75 on 2007-10-05
I compiled mine from the .tar file on the banshee homepage.

I got mine working.  I went over to the banshee homepage and made sure I had all the dependicies.  I found out I was missing the Gtk-sharp dependicies.  Not really sure why it worked yesterday but still installing those and It ran just fine.

---

