---
title: "Banshee  &quot;given key&quot; problem"
date: 2008-02-02
forum: Multimedia &amp; Video
---

### Post by alastairthegreat on 2008-02-02
HI there,
I've been running 7.10 for some months now and I'm loving it, its awesome, ive had a few issues but a quick search has usually turned up a very simple fix, however this time i cant find one so ive decided to post in the place where most of the simple fixes seem to come from.

the problem is to do with banshee music player0 (i have tried others but i really like the look and feel of it + its got all my podcasts and ratings etc) when i try to start it it shows the splash screen and then gives an error message saying:


> Banshee encountered a fatal error

the given key was not present in the dictionary

here's the "error details" if that helps

> An unhandled exception was thrown: The given key was not present in the dictionary.

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
Banshee.Plugins.Recommendation (0.13.1.19715)
Banshee.Plugins.Radio (0.13.1.19715)
Banshee.Plugins.Podcast (0.13.1.19713)
Banshee.Plugins.NotificationAreaIcon (0.13.1.19712)
Banshee.Plugins.MiniMode (0.13.1.19711)
Banshee.Plugins.MetadataSearch (0.13.1.19710)
Banshee.Plugins.Bookmarks (0.13.1.19708)
Banshee.Plugins.Awn (0.0.0.0)
Banshee.Plugins.Audioscrobbler (0.13.1.19707)
njb-sharp (0.3.0.27013)
Banshee.Dap.Njb (0.13.1.19706)
gnome-vfs-sharp (2.16.0.0)
Banshee.Dap.MassStorage (0.13.1.19706)
ipod-sharp (0.0.1.0)
Banshee.Dap.Ipod (0.13.1.19705)
Banshee.MediaEngine.GStreamer (0.13.1.19704)
System.Xml (2.0.0.0)
System.Transactions (2.0.0.0)
gconf-sharp (2.16.0.0)
System.Data (2.0.0.0)
Mono.Data.SqliteClient (2.0.0.0)
pango-sharp (2.10.0.0)
Mono.Cairo (2.0.0.0)
Hal (0.0.0.0)
Banshee.Widgets (0.13.1.19699)
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
Banshee.Base (0.13.1.19702)
banshee (0.13.1.19704)
mscorlib (2.0.0.0)

Platform Information: Linux 2.6.22-14-generic i686 unknown GNU/Linux

Disribution Information:

[/etc/debian_version]
lenny/sid

[/etc/lsb-release]
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=7.10
DISTRIB_CODENAME=gutsy
DISTRIB_DESCRIPTION="Ubuntu 7.10"



any ideas on how to fix this?

thanks

ali

---

### Post by alastairthegreat on 2008-02-03
is this the right sub-forum for this sort of question?

ali

---

### Post by SomeGuyDude on 2008-02-04
This literally just started happening to me as well.

---

### Post by alastairthegreat on 2008-02-04
> **SomeGuyDude said:**
> This literally just started happening to me as well.
i tried re-installing but that didnt work for me, have you tried anything else?

---

### Post by tgalati4 on 2008-02-04
banshee --debug

Try posting stuff just before the crash.  

My banshee works (0.13.1) on Linux Mint 4 XFCE (based on Gutsy).  I haven't applied all the latest updates, so perhaps it's an update problem.  My updater is showing audacity and libpulse0 have patches.  Also, Mint doesn't update xorg or the kernel by default, so it could be an xorg/kernel issue if you recently applied those patches.

---

### Post by SomeGuyDude on 2008-02-04
```
Debug: [2/4/2008 1:56:04 PM] (Audioscrobbler starting protocol engine) - 
/home/crew/.config/banshee/plugins/lyrics/
Creating new Pane
Performing compatibility update on playlist 'Guitar Hero 3'
The given key was not present in the dictionary.
System.Collections.Generic.KeyNotFoundException: The given key was not present in the dictionary.
  at System.Collections.Generic.Dictionary`2[System.Int32,Banshee.Base.TrackInfo].get_Item (Int32 ) [0x00000] 
  at Banshee.Sources.PlaylistSource.LoadFromDatabase () [0x000da] in /build/buildd/banshee-0.13.1+dfsg/src/Core/Banshee.Base/Sources/PlaylistSource.cs:143 
  at Banshee.Sources.PlaylistSource..ctor (Int32 id) [0x00000] 
  at Banshee.Sources.PlaylistUtil.LoadSources () [0x00020] in /build/buildd/banshee-0.13.1+dfsg/src/Core/Banshee.Base/Sources/PlaylistSource.cs:432 
  at Banshee.Sources.LibrarySource.LoadPlaylists () [0x00000] in /build/buildd/banshee-0.13.1+dfsg/src/Core/Banshee.Base/Sources/LibrarySource.cs:80 
  at Banshee.Sources.LibrarySource..ctor () [0x00000] 
  at Banshee.Sources.LibrarySource.get_Instance () [0x0000b] in /build/buildd/banshee-0.13.1+dfsg/src/Core/Banshee.Base/Sources/LibrarySource.cs:45 
  at Banshee.PlayerUI.OnStartupRunFinished (System.Object o, System.EventArgs args) [0x00092] in /build/buildd/banshee-0.13.1+dfsg/src/Core/Banshee/PlayerInterface.cs:578 
  at (wrapper delegate-invoke) System.MulticastDelegate:invoke_void_object_EventArgs (object,System.EventArgs)
  at Banshee.Base.ComponentInitializer.OnRunFinished () [0x0000d] in /build/buildd/banshee-0.13.1+dfsg/src/Core/Banshee.Base/ComponentInitializer.cs:148 
  at Banshee.Base.ComponentInitializer.Run () [0x00081] in /build/buildd/banshee-0.13.1+dfsg/src/Core/Banshee.Base/ComponentInitializer.cs:133 
  at Banshee.Base.Globals.Initialize (Banshee.Base.ComponentInitializerHandler interfaceStartupHandler) [0x00343] in /build/buildd/banshee-0.13.1+dfsg/src/Core/Banshee.Base/Globals.cs:198 
  at Banshee.BansheeEntry.Startup (System.String[] args) [0x0029c] in /build/buildd/banshee-0.13.1+dfsg/src/Core/Banshee/Main.cs:113 
  at (wrapper delegate-invoke) System.MulticastDelegate:invoke_void_string[] (string[])
  at Banshee.Gui.CleanRoomStartup.Startup (Banshee.Gui.StartupInvocationHandler startup, System.String[] args) [0x00045] in /build/buildd/banshee-0.13.1+dfsg/src/Core/Banshee.Base/Gui/CleanRoomStartup.cs:54 

** (banshee:13243): WARNING **: Invalid borders specified for theme pixmap:
        /home/crew/.themes/Neutronium DeepBlack/gtk-2.0/Range/null.png,
borders don't fit within the image

** (banshee:13243): WARNING **: invalid source position for bilinear gradient


** (banshee:13243): WARNING **: invalid source position for vertical gradient


** (banshee:13243): WARNING **: invalid source position for horizontal gradient

```

---

### Post by alastairthegreat on 2008-02-05
heres what i got:




alastair@alastair-desktop:~$ banshee --debug
** Running Banshee in Debug Mode **
** Running Mono with --debug   **

(Banshee:13600): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",
Debug: [05/02/2008 15:38:52] (Loading audio profiles) - /usr/share/banshee/audio-profiles

Unhandled Exception: System.Collections.Generic.KeyNotFoundException: The given key was not present in the dictionary.
  at System.Collections.Generic.Dictionary`2[System.Int32,Banshee.Base.TrackInfo].get_Item (Int32 ) [0x00000] 
  at Banshee.Sources.PlaylistSource.LoadFromDatabase () [0x000da] in /build/buildd/banshee-0.13.1+dfsg/src/Core/Banshee.Base/Sources/PlaylistSource.cs:143 
  at Banshee.Sources.PlaylistSource..ctor (Int32 id) [0x00000] 
  at Banshee.Sources.PlaylistUtil.LoadSources () [0x00020] in /build/buildd/banshee-0.13.1+dfsg/src/Core/Banshee.Base/Sources/PlaylistSource.cs:432 
  at Banshee.Sources.LibrarySource.LoadPlaylists () [0x00000] in /build/buildd/banshee-0.13.1+dfsg/src/Core/Banshee.Base/Sources/LibrarySource.cs:80 
  at Banshee.Sources.LibrarySource..ctor () [0x00000] 
  at Banshee.Sources.LibrarySource.get_Instance () [0x0000b] in /build/buildd/banshee-0.13.1+dfsg/src/Core/Banshee.Base/Sources/LibrarySource.cs:45 
  at Banshee.Base.Library.ReloadLibraryThread () [0x0009f] in /build/buildd/banshee-0.13.1+dfsg/src/Core/Banshee.Base/Library.cs:131 
  at (wrapper delegate-invoke) System.MulticastDelegate:invoke_void ()
Debug: [05/02/2008 15:38:53] (GStreamer pipeline does not run) - audioconvert ! xingenc bitrate=128 ! id3v2mux
Debug: [05/02/2008 15:38:53] (GStreamer pipeline does not run) - audioconvert ! fluwmaenc bitrate=64000 vbr=false ! fluasfmux
Debug: [05/02/2008 15:38:53] (Default player engine) - GStreamer 0.10
Debug: [05/02/2008 15:38:53] (Audio CD Core Initialised) - 
Debug: [05/02/2008 15:38:53] (Testing device for DAP support) - /org/freedesktop/Hal/devices/volume_uuid_7C28E51C28E4D664
Debug: [05/02/2008 15:38:54] (Waiting for possible DAP to mount) - /org/freedesktop/Hal/devices/volume_uuid_7C28E51C28E4D664
Debug: [05/02/2008 15:38:54] (DAP has not been added) - /org/freedesktop/Hal/devices/volume_uuid_7C28E51C28E4D664
Warning: [05/02/2008 15:38:54] (Power Management Call Failed) - Cannot find GNOME Power Manager: Name org.gnome.PowerManager has no owner
Debug: [05/02/2008 15:38:54] (Enabled multimedia keys support) - Using org.gnome.SettingsDaemon
The given key was not present in the dictionary.
System.Collections.Generic.KeyNotFoundException: The given key was not present in the dictionary.
  at System.Collections.Generic.Dictionary`2[System.Int32,Banshee.Base.TrackInfo].get_Item (Int32 ) [0x00000] 
  at Banshee.Sources.PlaylistSource.LoadFromDatabase () [0x000da] in /build/buildd/banshee-0.13.1+dfsg/src/Core/Banshee.Base/Sources/PlaylistSource.cs:143 
  at Banshee.Sources.PlaylistSource..ctor (Int32 id) [0x00000] 
  at Banshee.Sources.PlaylistUtil.LoadSources () [0x00020] in /build/buildd/banshee-0.13.1+dfsg/src/Core/Banshee.Base/Sources/PlaylistSource.cs:432 
  at Banshee.Sources.LibrarySource.LoadPlaylists () [0x00000] in /build/buildd/banshee-0.13.1+dfsg/src/Core/Banshee.Base/Sources/LibrarySource.cs:80 
  at Banshee.Sources.LibrarySource..ctor () [0x00000] 
  at Banshee.Sources.LibrarySource.get_Instance () [0x0000b] in /build/buildd/banshee-0.13.1+dfsg/src/Core/Banshee.Base/Sources/LibrarySource.cs:45 
  at Banshee.PlayerUI.OnStartupRunFinished (System.Object o, System.EventArgs args) [0x00092] in /build/buildd/banshee-0.13.1+dfsg/src/Core/Banshee/PlayerInterface.cs:578 
  at (wrapper delegate-invoke) System.MulticastDelegate:invoke_void_object_EventArgs (object,System.EventArgs)
  at Banshee.Base.ComponentInitializer.OnRunFinished () [0x0000d] in /build/buildd/banshee-0.13.1+dfsg/src/Core/Banshee.Base/ComponentInitializer.cs:148 
  at Banshee.Base.ComponentInitializer.Run () [0x00081] in /build/buildd/banshee-0.13.1+dfsg/src/Core/Banshee.Base/ComponentInitializer.cs:133 
  at Banshee.Base.Globals.Initialize (Banshee.Base.ComponentInitializerHandler interfaceStartupHandler) [0x00343] in /build/buildd/banshee-0.13.1+dfsg/src/Core/Banshee.Base/Globals.cs:198 
  at Banshee.BansheeEntry.Startup (System.String[] args) [0x0029c] in /build/buildd/banshee-0.13.1+dfsg/src/Core/Banshee/Main.cs:113 
  at (wrapper delegate-invoke) System.MulticastDelegate:invoke_void_string[] (string[])
  at Banshee.Gui.CleanRoomStartup.Startup (Banshee.Gui.StartupInvocationHandler startup, System.String[] args) [0x00045] in /build/buildd/banshee-0.13.1+dfsg/src/Core/Banshee.Base/Gui/CleanRoomStartup.cs:54 
Segmentation fault (core dumped)

---

### Post by tgalati4 on 2008-02-05
I'm not at my machine at the moment, but sometimes the database gets messed up.  The program is working OK but there is a malformed structure in the database that trips it up.  Try deleting the music database and bring up banshee fresh.  I'm not sure where the database is located, you will have to look for it.

In synaptic you can use *remove completely* to purge user files associated with Banshee.  Then reinstall and see if it comes up with an empty database.  If so, you can reimport your music and you should be good to go.

---

