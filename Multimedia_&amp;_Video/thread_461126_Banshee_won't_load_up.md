---
title: "Banshee won't load up"
date: 2007-06-01
forum: Multimedia &amp; Video
---

### Post by macabro22 on 2007-06-01
Fellow Ubuntuers,

I get a fatal error when I try to run Banshee:

```
An unhandled exception was thrown: The classes in the module cannot be loaded.

  at <0x00000> <unknown method>
  at (wrapper managed-to-native) System.Reflection.Assembly:GetTypes (bool)
  at System.Reflection.Assembly.GetTypes () [0x00000] 
  at Banshee.Plugins.PluginFactory`1[Banshee.Plugins.Plugin].LoadPluginsFromAssembly (System.Reflection.Assembly ) [0x00000] 
  at Banshee.Plugins.PluginFactory`1[Banshee.Plugins.Plugin].LoadPluginsFromFile (System.IO.FileInfo ) [0x00000] 
  at Banshee.Plugins.PluginFactory`1[Banshee.Plugins.Plugin].LoadPluginsFromDirectory (System.IO.DirectoryInfo ) [0x00000] 
  at Banshee.Plugins.PluginFactory`1[Banshee.Plugins.Plugin].LoadPlugins () [0x00000] 
  at Banshee.Plugins.PluginCore.Initialize () [0x00000] 
  at (wrapper delegate-invoke) System.MulticastDelegate:invoke_void ()
  at Banshee.Base.ComponentInitializer.Run () [0x00000] 
  at Banshee.Base.Globals.Initialize (Banshee.Base.ComponentInitializerHandler interfaceStartupHandler) [0x00000] 
  at Banshee.BansheeEntry.Startup (System.String[] args) [0x00000] 
  at (wrapper delegate-invoke) System.MulticastDelegate:invoke_void_string[] (string[])
  at Banshee.Gui.CleanRoomStartup.Startup (Banshee.Gui.StartupInvocationHandler startup, System.String[] args) [0x00000] 
.NET Version: 2.0.50727.42

Assembly Version Information:

MiniMode (0.11.1.0)
Banshee.Plugins.Recommendation (0.12.1.12341)
Banshee.Plugins.Radio (0.12.1.12340)
Banshee.Plugins.Podcast (0.12.1.12339)
Banshee.Plugins.NotificationAreaIcon (0.12.1.12337)
Banshee.Plugins.MiniMode (0.12.1.12336)
Banshee.Plugins.MetadataSearch (0.12.1.12335)
Banshee.Plugins.MMKeys (0.12.1.12336)
Banshee.Plugins.Daap (0.12.1.12334)
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

```

May someone assist me?

---

### Post by Virtual DarKness on 2007-06-04
Hi,
I had the same problem and solved it removing the banshee-official-plugins (or something like that) package.

bye,
Giovanni.

---

### Post by macabro22 on 2007-06-04
Thanx! That did it.

---

