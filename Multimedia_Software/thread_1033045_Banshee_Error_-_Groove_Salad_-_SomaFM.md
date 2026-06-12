---
title: "Banshee Error - Groove Salad - SomaFM"
date: 2009-01-06
forum: Multimedia Software
---

### Post by Peder_Erickson on 2009-01-06
I found that Banshee doesn't have SomaFM anymore, so I got the needed address for streaming, and set up a radio station, Groove Salad, my favourite station

Whenever I start the station, it plays, but it also displays a error dialog box

```
Dialog Title: Bansee Encountered a Fatal Error

An unhandled exception was thrown: Cannot send null variant

at NDesk.DBus.MessageWriter.Write (object) <0x00059>
at NDesk.DBus.MessageWriter.Write (System.Type,object) <0x000c9>
at NDesk.DBus.MessageWriter.WriteFromDict (System.Type,System.Type,System.Collections.IDictionary) <0x00115>
at NDesk.DBus.MessageWriter.Write (System.Type,object) <0x001f3>
at NDesk.DBus.MessageHelper.ConstructDynamicReply (NDesk.DBus.MethodCall,System.Reflection.MethodInfo,object,object[]) <0x000f9>
at NDesk.DBus.ExportObject.HandleMethodCall (NDesk.DBus.MethodCall) <0x0035c>
at NDesk.DBus.Connection.HandleMethodCall (NDesk.DBus.MethodCall) <0x00372>
at NDesk.DBus.Connection.HandleMessage (NDesk.DBus.Message) <0x00123>
at NDesk.DBus.Connection.Iterate () <0x00023>
at <>c__CompilerGenerated0.<>c__AnonymousMethod1 (intptr,NDesk.GLib.IOCondition,intptr) <0x00027>
at (wrapper native-to-managed) <>c__CompilerGenerated0.<>c__AnonymousMethod1 (intptr,NDesk.GLib.IOCondition,intptr) <0x0004b>
at (wrapper managed-to-native) Gtk.Application.gtk_main () <0x00004>
at Gtk.Application.Run () <0x00007>
at Banshee.Gui.GtkBaseClient.Run () <0x00052>
at Banshee.Gui.GtkBaseClient.Startup () <0x00034>
at Hyena.Gui.CleanRoomStartup.Startup (Hyena.Gui.CleanRoomStartup/StartupInvocationHandler) <0x000a2>


.NET Version: 2.0.50727.42
OS Version: Unix 2.6.27.9

Assembly Version Information:

System.Web (2.0.0.0)
System.Configuration (2.0.0.0)
ipod-sharp (0.0.1.0)
Mtp (1.2.1.19132)
avahi-sharp (1.0.0.0)
Mono.Zeroconf.Providers.Avahi (2.0.0.76)
Mono.Zeroconf (2.0.0.76)
Banshee.Dap.Mtp (1.2.1.19141)
Banshee.Dap.MassStorage (1.2.1.19141)
taglib-sharp (2.0.3.0)
Mono.Media (1.2.1.19131)
Banshee.InternetRadio (1.2.1.19145)
Banshee.PlayQueue (1.2.1.19149)
Banshee.FileSystemQueue (1.2.1.19145)
notify-sharp (0.4.0.0)
Banshee.NotificationArea (1.2.1.19147)
Lastfm (1.2.1.19133)
Banshee.Lastfm (1.2.1.19146)
Banshee.CoverArt (1.2.1.19143)
Banshee.Bookmarks (1.2.1.19142)
Migo (1.2.1.19131)
Banshee.Podcasting (1.2.1.19149)
Banshee.MultimediaKeys (1.2.1.19147)
Banshee.Daap (1.2.1.19144)
Banshee.AudioCd (1.2.1.19142)
pango-sharp (2.12.0.0)
Mono.Cairo (2.0.0.0)
Banshee.Widgets (1.2.1.19136)
Banshee.Dap.Ipod (1.2.1.19140)
Banshee.Dap (1.2.1.19140)
Banshee.Hal (1.2.1.19150)
Banshee.Unix (1.2.1.19151)
Banshee.GStreamer (1.2.1.19151)
gconf-sharp (2.20.0.0)
Banshee.Gnome (1.2.1.19150)
Banshee.NowPlaying (1.2.1.19148)
System.Transactions (2.0.0.0)
System.Xml (2.0.0.0)
System.Data (2.0.0.0)
Mono.Data.SqliteClient (2.0.0.0)
Mono.Addins (0.3.0.0)
atk-sharp (2.12.0.0)
Hyena.Gui (1.2.1.19130)
NDesk.DBus.Proxies (0.0.0.0)
Mono.Posix (2.0.0.0)
NDesk.DBus.GLib (1.0.0.0)
NDesk.DBus (1.0.0.0)
gtk-sharp (2.12.0.0)
Hyena (1.2.1.19129)
System (2.0.0.0)
glib-sharp (2.12.0.0)
gdk-sharp (2.12.0.0)
Banshee.Core (1.2.1.19134)
Banshee.Services (1.2.1.19135)
Banshee.ThickClient (1.2.1.19138)
Nereid (1.2.1.19139)
mscorlib (2.0.0.0)

Platform Information: Linux 2.6.27-9-generic i686 unknown GNU/Linux

Disribution Information:

[/etc/lsb-release]
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.10
DISTRIB_CODENAME=intrepid
DISTRIB_DESCRIPTION="Ubuntu 8.10"

[/etc/debian_version]
lenny/sid

```

I made it look as much as the actuail dialog as possible, here's the terminal output
```
$ banshee-1
[Info  22:28:47.625] Running Banshee 1.2.1
[Info  22:28:50.471] All services are started 2.376189s
[Info  22:28:51.765] nereid Client Started
Cannot send null variant
System.NotSupportedException: Cannot send null variant
at NDesk.DBus.MessageWriter.Write (object) <0x00059>
at NDesk.DBus.MessageWriter.Write (System.Type,object) <0x000c9>
at NDesk.DBus.MessageWriter.WriteFromDict (System.Type,System.Type,System.Collections.IDictionary) <0x00115>
at NDesk.DBus.MessageWriter.Write (System.Type,object) <0x001f3>
at NDesk.DBus.MessageHelper.ConstructDynamicReply (NDesk.DBus.MethodCall,System.Reflection.MethodInfo,object,object[]) <0x000f9>
at NDesk.DBus.ExportObject.HandleMethodCall (NDesk.DBus.MethodCall) <0x0035c>
at NDesk.DBus.Connection.HandleMethodCall (NDesk.DBus.MethodCall) <0x00372>
at NDesk.DBus.Connection.HandleMessage (NDesk.DBus.Message) <0x00123>
at NDesk.DBus.Connection.Iterate () <0x00023>
at <>c__CompilerGenerated0.<>c__AnonymousMethod1 (intptr,NDesk.GLib.IOCondition,intptr) <0x00027>
at (wrapper native-to-managed) <>c__CompilerGenerated0.<>c__AnonymousMethod1 (intptr,NDesk.GLib.IOCondition,intptr) <0x0004b>
at (wrapper managed-to-native) Gtk.Application.gtk_main () <0x00004>
at Gtk.Application.Run () <0x00007>
at Banshee.Gui.GtkBaseClient.Run () <0x00052>
at Banshee.Gui.GtkBaseClient.Startup () <0x00034>
at Hyena.Gui.CleanRoomStartup.Startup (Hyena.Gui.CleanRoomStartup/StartupInvocationHandler) <0x000a2>

```

The music keeps on playing until I hit the close button on the dialog box, then banshee closes

Can anyone help?  This is very annoying to have happen, even though it still runs, I cannot hide the window, and it has that error message, which I may close by accident, causing me to have to re-load Banshee, and re-open Groove Salad, sticking that message to my desktop

Thanks in advance

---

### Post by tgalati4 on 2009-01-07
Try running in debug mode then post the output of:

>banshee-1 --debug

---

### Post by Peder_Erickson on 2009-01-09
It took me a little bit longer to get back to you than I wanted, but here's what happens

```
$ banshee-1 --debug
** Running Mono with --debug   **
[Debug 11:33:21.700] NDesk.DBus.Bus.Session.RequestName ('org.bansheeproject.Banshee') => PrimaryOwner
[Info  11:33:21.729] Running Banshee 1.2.1
[Debug 11:33:24.526] Core service started (DBusServiceManager, 0.003125s)
[Debug 11:33:24.562] Core service started (DBusCommandService, 0.030739s)
[Debug 11:33:24.791] Opened SQLite connection to /home/peder/.config/banshee-1/banshee.db
[Debug 11:33:24.791] Core service started (DbConnection, 0.228633s)
[Debug 11:33:24.814] Database version 17 is up to date
[Debug 11:33:24.879] Core service started (PreferenceService, 0.054662s)
[Debug 11:33:24.883] Core service started (SourceManager, 0.003655s)
[Debug 11:33:25.354] Core service started (MediaProfileManager, 0.469941s)
[Debug 11:33:25.362] Core service started (PlayerEngine, 0.00712s)
[Debug 11:33:25.376] Configuration client extension loaded (Banshee.GnomeBackend.GConfConfigurationClient)
[Debug 11:33:25.500] IO provider extension loaded (Banshee.IO.Unix.Provider)
[Debug 11:33:25.550] Core service started (TranscoderService, 0.055367s)
[Debug 11:33:25.554] Core service started (PlaybackController, 0.002952s)
[Debug 11:33:25.555] Core service started (ImportSourceManager, 0.000478s)
[Debug 11:33:25.561] Core service started (LibraryImportManager, 0.006312s)
[Debug 11:33:25.562] Core service started (UserJobManager, 0.000728s)
[Debug 11:33:25.587] Core service started (HardwareManager, 0.024967s)
[Debug 11:33:25.677] Adding icon theme search path: /usr/share/banshee-1/icons
[Debug 11:33:25.679] Core service started (GtkElementsService, 0.090883s)
[Debug 11:33:25.778] Core service started (InterfaceActionService, 0.098327s)
[Debug 11:33:25.783] Album artwork path set to /home/peder/.cache/album-art
[Debug 11:33:25.783] Core service started (ArtworkManager, 0.00535s)
[Debug 11:33:26.578] Core service started (NereidPlayerInterface, 0.794347s)
[Debug 11:33:26.705] Extension service started (AudioCdService, 0.125936s)
[Debug 11:33:26.707] Extension service started (DaapService, 0.001319s)
[Debug 11:33:26.708] Extension service started (DapService, 0.001317s)
[Debug 11:33:26.776] Using GNOME 2.22 API for Multimedia Keys
[Debug 11:33:26.776] Extension service started (MultimediaKeysService, 0.067619s)
[Debug 11:33:27.193] Extension service started (PodcastService, 0.416757s)
[Debug 11:33:27.240] Extension service started (BookmarksService, 0.045713s)
[Debug 11:33:27.247] Extension service started (CoverArtService, 0.006872s)
[Debug 11:33:27.273] Extension service started (LastfmRecommendationService, 0.026506s)
[Debug 11:33:27.309] Audioscrobbler state: connected
[Debug 11:33:27.313] Extension service started (AudioscrobblerService, 0.038991s)
[Debug 11:33:27.362] Extension service started (GnomeService, 0.048982s)
[Debug 11:33:27.429] Extension service started (NotificationAreaService, 0.066932s)
[Debug 11:33:27.671] GStreamer pipeline does not run: audioconvert ! xingenc bitrate=128 ! id3v2mux
[Debug 11:33:27.868] GStreamer pipeline does not run: audioconvert ! fluwmaenc bitrate=64000 vbr=false ! fluasfmux
[Debug 11:33:27.868] Extension service started (GStreamerCoreService, 0.438521s)
[Debug 11:33:27.916] Player state change: NotReady -> Ready
[Debug 11:33:27.929] Player state change: Ready -> Idle
[Info  11:33:27.937] All services are started 3.421115s
[Debug 11:33:28.543] Loaded IScreensaverManager: Banshee.GnomeBackend.GnomeScreensaverManager
[Info  11:33:29.212] nereid Client Started
[Debug 11:33:29.242] Dap support extension loaded: Banshee.Dap.MassStorage
[Debug 11:33:29.622] Dap support extension loaded: Banshee.Dap.Mtp
[Debug 11:33:29.919] Dap support extension loaded: Banshee.Dap.Ipod
[Debug 11:33:33.073] Attempting to parse radio playlist - http://steady.somafm.com:9002
[Debug 11:33:33.697] Playing Radio Stream - http://steady.somafm.com:9002
[Debug 11:33:33.701] Player state change: Idle -> Loading
[Debug 11:33:35.313] TrackInfoDisplay RenderAnimation: 26.00 FPS
[Debug 11:33:35.579] Player state change: Loading -> Loaded
[Debug 11:33:35.691] Player state change: Loaded -> Playing
Cannot send null variant
System.NotSupportedException: Cannot send null variant
at NDesk.DBus.MessageWriter.Write (object) [0x00020] in /build/buildd/ndesk-dbus-0.6.0/src/MessageWriter.cs:336
at NDesk.DBus.MessageWriter.Write (System.Type,object) [0x00085] in /build/buildd/ndesk-dbus-0.6.0/src/MessageWriter.cs:209
at NDesk.DBus.MessageWriter.WriteFromDict (System.Type,System.Type,System.Collections.IDictionary) [0x00058] in /build/buildd/ndesk-dbus-0.6.0/src/MessageWriter.cs:399
at NDesk.DBus.MessageWriter.Write (System.Type,object) [0x000f5] in /build/buildd/ndesk-dbus-0.6.0/src/MessageWriter.cs:215
at NDesk.DBus.MessageHelper.ConstructDynamicReply (NDesk.DBus.MethodCall,System.Reflection.MethodInfo,object,object[]) [0x00076] in /build/buildd/ndesk-dbus-0.6.0/src/Mapper.cs:337
at NDesk.DBus.ExportObject.HandleMethodCall (NDesk.DBus.MethodCall) [0x00138] in /build/buildd/ndesk-dbus-0.6.0/src/ExportObject.cs:88
at NDesk.DBus.Connection.HandleMethodCall (NDesk.DBus.MethodCall) [0x001bc] in /build/buildd/ndesk-dbus-0.6.0/src/Connection.cs:455
at NDesk.DBus.Connection.HandleMessage (NDesk.DBus.Message) [0x000e3] in /build/buildd/ndesk-dbus-0.6.0/src/Connection.cs:343
at NDesk.DBus.Connection.Iterate () [0x00012] in /build/buildd/ndesk-dbus-0.6.0/src/Connection.cs:309
at <>c__CompilerGenerated0.<>c__AnonymousMethod1 (intptr,NDesk.GLib.IOCondition,intptr) [0x00036] in /build/buildd/ndesk-dbus-glib-0.4.1/src/GLib.cs:40
at (wrapper native-to-managed) <>c__CompilerGenerated0.<>c__AnonymousMethod1 (intptr,NDesk.GLib.IOCondition,intptr) <0x0004b>
at (wrapper managed-to-native) Gtk.Application.gtk_main () <0x00004>
at Gtk.Application.Run () <0x00007>
at Banshee.Gui.GtkBaseClient.Run () [0x00027] in /build/buildd/banshee-1.2.1/src/Core/Banshee.ThickClient/Banshee.Gui/GtkBaseClient.cs:114
at Banshee.Gui.GtkBaseClient.Startup () [0x00000] in /build/buildd/banshee-1.2.1/src/Core/Banshee.ThickClient/Banshee.Gui/GtkBaseClient.cs:55
at Hyena.Gui.CleanRoomStartup.Startup (Hyena.Gui.CleanRoomStartup/StartupInvocationHandler) [0x00048] in /build/buildd/banshee-1.2.1/src/Libraries/Hyena.Gui/Hyena.Gui/CleanRoomStartup.cs:54

[Debug 11:33:36.776] TrackInfoDisplay RenderAnimation: 28.00 FPS
Real-time signal 1

```

---

### Post by Peder_Erickson on 2009-01-11
Can't anyone help?

---

### Post by Peder_Erickson on 2009-01-13
erm... I would like to be able to use Radio stations in Banshee... aside from the one that comes pre-installed

---

### Post by markbuntu on 2009-01-14
I use Amarok to listen to groove salad. The aacPlus stream does not play however the others do. I think there is no codec for that yet.

---

### Post by tgalati4 on 2009-03-03
Both links:

[http://somafm.com/groovesalad.pls](http://somafm.com/groovesalad.pls)

and

[http://steady.somafm.com:9002](http://steady.somafm.com:9002)

work for me using Banshee 1.4.2.  I just right-clicked on "Radio"-->"Add Station" then hit play.

---

