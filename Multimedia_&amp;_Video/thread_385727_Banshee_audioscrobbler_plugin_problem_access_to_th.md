---
title: "Banshee audioscrobbler plugin problem: access to the path is denied"
date: 2007-03-16
forum: Multimedia &amp; Video
---

### Post by denilson3 on 2007-03-16
I'm having problems getting the audioscobbler plugin to work.

At first I encountered this error 

Could not find a part of the path "/home/~/.gnome2/banshee/plugins".

so i did

sudo mkdir /home/jay/.gnome2/banshee/plugins/

Now I am getting this error:

```
An unhandled exception was thrown: Access to the path "/home/jay/.gnome2/banshee/plugins/AudioscrobblerQueue.xml" is denied.

at System.IO.FileStream..ctor (string,System.IO.FileMode,System.IO.FileAccess,System.IO.FileShare,int,bool,System.IO.FileOptions) <0x0036a>
at System.IO.FileStream..ctor (string,System.IO.FileMode,System.IO.FileAccess,System.IO.FileShare) <0x0001f>
at (wrapper remoting-invoke-with-check) System.IO.FileStream..ctor (string,System.IO.FileMode,System.IO.FileAccess,System.IO.FileShare) <0x0004b>
at System.Xml.XmlTextWriter..ctor (string,System.Text.Encoding) <0x0002a>
at Banshee.Plugins.Audioscrobbler.Queue.Save () <0x00061>
at Banshee.Plugins.Audioscrobbler.Engine.TransmitQueue () <0x00029>
at Banshee.Plugins.Audioscrobbler.Engine.StateTransitionHandler () <0x00175>
at (wrapper delegate-invoke) System.MulticastDelegate.invoke_bool () <0x00037>
at TimeoutProxy.Handler () <0x0002a>
at (wrapper native-to-managed) TimeoutProxy.Handler () <0x00036>
in (unmanaged) 0xb7f41dd5
at (wrapper managed-to-native) Gtk.Application.gtk_main () <0x00004>
at Gtk.Application.Run () <0x00007>
at Banshee.BansheeEntry.Startup (string[]) <0x00657>
at (wrapper delegate-invoke) System.MulticastDelegate.invoke_void_string[] (string[]) <0x00048>
at Banshee.Gui.CleanRoomStartup.Startup (Banshee.Gui.CleanRoomStartup/StartupInvocationHandler,string[]) <0x000ae>

.NET Version: 2.0.50727.42

Assembly Version Information:

System.Web (2.0.0.0)
System.Configuration (2.0.0.0)
Mono.Security (2.0.0.0)
NotificationAreaIcon (0.11.1.41236)
MusicBrainz (0.11.1.41226)
MetadataSearch (0.11.1.41235)
MMKeys (0.11.1.41236)
Banshee.Plugins.Audioscrobbler (0.11.1.41234)
ipod-sharp-ui (0.0.1.0)
njb-sharp (0.3.0.27013)
Banshee.Dap.Njb (0.11.1.41233)
gnome-vfs-sharp (2.16.0.0)
Banshee.Dap.MassStorage (0.11.1.41233)
ipod-sharp (0.0.1.0)
Banshee.Dap.Ipod (0.11.1.41232)
GStreamerPlayerEngine (0.11.1.41231)
System.Xml (2.0.0.0)
System.Data (2.0.0.0)
Mono.Data.SqliteClient (2.0.0.0)
pango-sharp (2.10.0.0)
Mono.Cairo (2.0.0.0)
Hal (0.0.0.0)
Last.FM (0.0.0.0)
NDesk.DBus (0.0.0.0)
Mono.Posix (2.0.0.0)
Banshee.Widgets (0.11.1.41228)
glade-sharp (2.10.0.0)
gnome-sharp (2.16.0.0)
gconf-sharp (2.16.0.0)
NDesk.DBus.GLib (0.0.0.0)
gdk-sharp (2.10.0.0)
System (2.0.0.0)
atk-sharp (2.10.0.0)
glib-sharp (2.10.0.0)
gtk-sharp (2.10.0.0)
Banshee.Base (0.11.1.41231)
banshee (0.11.1.41238)
mscorlib (2.0.0.0)

Platform Information: Linux 2.6.17-11-generic i686 unknown GNU/Linux

Disribution Information:

[/etc/debian_version]
testing/unstable

[/etc/lsb-release]
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=6.10
DISTRIB_CODENAME=edgy
DISTRIB_DESCRIPTION="Ubuntu 6.10"
```

Very new to this, any help would be appreciated.

---

### Post by jeeves on 2007-03-24
What if it's a permission problem that "plugins" directory you created?

I had the same problem, but was able to fix it simply by creating a "plugins" directory using the Thunar file manage. That directory is owned by the current user and  writeable without having to use sudo.  This worked for me, and I simply installed "banshee" & "banshee-official-plugins" using the snaptic package manager. I'm running Xubuntu 6.10 edgy.

Sounds like you already read the thread below, but here is a link just in case:
[http://ubuntuforums.org/showthread.php?p=170](http://ubuntuforums.org/showthread.php?p=170)

---

### Post by phr0z3n on 2007-03-25
Hmm..... I had the same error as well with the plugins directory. I did mkdir "/home/~/.gnome2/banshee/plugins and then I found commands where you had to set up the username and password via the command line, I can find them if you like, I was getting the error even after I made the directory.

---

