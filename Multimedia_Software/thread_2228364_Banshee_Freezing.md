---
title: "Banshee Freezing"
date: 2014-06-07
forum: Multimedia Software
---

### Post by Jonny87 on 2014-06-07
I have a problem with banshee freezing all the time. I have even tried to upgrade banshee to the lates vesion from its ppa. I've also tried disabling all the plugins thatI don't need. 

Here is the terminal output from running it in the terminal;
```
jonny@jonny-desktop:~$ banshee
[Info  14:30:02.343] Running Banshee 2.6.1: [Ubuntu 12.04.2 LTS (linux-gnu, x86_64) @ 2013-06-14 20:46:57 UTC]
[Warn  14:30:03.452] Caught an exception - System.ApplicationException: No support GNOME Settings Daemon could be reached. (in `Banshee.MultimediaKeys')
  at Banshee.MultimediaKeys.MultimediaKeysService.Banshee.ServiceStack.IExtensionService.Initialize () [0x00000] in <filename unknown>:0 
  at Banshee.ServiceStack.ServiceManager.StartExtension (Mono.Addins.TypeExtensionNode node) [0x00000] in <filename unknown>:0 
[Warn  14:30:03.452] Extension `Banshee.MultimediaKeys.MultimediaKeysService' not started: No support GNOME Settings Daemon could be reached.
[Info  14:30:03.474] Updating web proxy from GConf
[Warn  14:30:04.019] Caught an exception - System.ApplicationException: No support GNOME Settings Daemon could be reached. (in `Banshee.MultimediaKeys')
  at Banshee.MultimediaKeys.MultimediaKeysService.Banshee.ServiceStack.IExtensionService.Initialize () [0x00000] in <filename unknown>:0 
  at Banshee.ServiceStack.ServiceManager.StartExtension (Mono.Addins.TypeExtensionNode node) [0x00000] in <filename unknown>:0 
[Warn  14:30:04.020] Extension `Banshee.MultimediaKeys.MultimediaKeysService' not started: No support GNOME Settings Daemon could be reached.
[Info  14:30:04.022] All services are started 1.441986
[Info  14:30:04.643] nereid Client Started
[Info  14:30:04.745] GStreamer version 0.10.36.0, gapless: True, replaygain: False
[Info  14:30:04.788] AppleDeviceSource is ignoring unmounted volume 44 GB Filesystem
[Info  14:30:04.816] AppleDeviceSource is ignoring unmounted volume System Reserved

(Banshee:4258): Gtk-CRITICAL **: IA__gtk_style_detach: assertion `style->attach_count > 0' failed
[Info  14:30:32.463] GNOME screensaver service not found
jonny@jonny-desktop:~$ 

```

The last part is when it froze. I waited a bit then closed it. Are there any experts out there that know why Banshee keeps doing this?

I'm running 12.04 LTS

---

### Post by Yellow Pasque on 2014-06-07
Try running with --debug to get more detail: [https://wiki.ubuntu.com/DebuggingBanshee](https://wiki.ubuntu.com/DebuggingBanshee)

---

### Post by Jonny87 on 2014-06-07
> **Temüjin said:**
> Try running with --debug to get more detail: [https://wiki.ubuntu.com/DebuggingBanshee](https://wiki.ubuntu.com/DebuggingBanshee)

OK heres the debug output

```
jonny@jonny-desktop:~$ banshee --debug
** Running Mono with --debug   **
[1 Debug 22:46:37.935] Bus.Session.RequestName ('org.bansheeproject.Banshee') replied with PrimaryOwner
[1 Info  22:46:37.968] Running Banshee 2.6.1: [Ubuntu 12.04.2 LTS (linux-gnu, x86_64) @ 2013-06-14 20:46:57 UTC]
[1 Debug 22:46:37.987] Initializing GTK
[1 Debug 22:46:39.045] Post-Initializing GTK
[1 Debug 22:46:39.057] Configuration client extension loaded (Banshee.GnomeBackend.GConfConfigurationClient)
[1 Debug 22:46:39.059] Using default gconf-base-key
[1 Debug 22:46:39.138] Core service started (DBusServiceManager, 0.00126)
[1 Debug 22:46:39.140] Registering remote object /org/bansheeproject/Banshee/DBusCommandService (Banshee.ServiceStack.DBusCommandService) on org.bansheeproject.Banshee
[1 Debug 22:46:39.149] Core service started (DBusCommandService, 0.010572)
[1 Debug 22:46:39.339] Opened SQLite (version 3.7.9) connection to /home/jonny/.config/banshee-1/banshee.db
[1 Debug 22:46:39.339] Core service started (DbConnection, 0.190546)
[1 Debug 22:46:39.347] Database version 45 is up to date
[1 Debug 22:46:39.387] Core service started (PreferenceService, 0.018407)
[1 Debug 22:46:39.410] Core service started (Network, 0.022763)
[1 Debug 22:46:39.410] Registering remote object /org/bansheeproject/Banshee/SourceManager (Banshee.Sources.SourceManager) on org.bansheeproject.Banshee
[1 Debug 22:46:39.410] Core service started (SourceManager, 0.000655)
[1 Debug 22:46:39.416] Core service started (MediaProfileManager, 0.000467)
[1 Debug 22:46:39.419] Registering remote object /org/bansheeproject/Banshee/PlayerEngine (Banshee.MediaEngine.PlayerEngineService) on org.bansheeproject.Banshee
[1 Debug 22:46:39.421] Core service started (PlayerEngine, 0.005285)
[1 Debug 22:46:39.437] Registering remote object /org/bansheeproject/Banshee/PlaybackController (Banshee.PlaybackController.PlaybackControllerService) on org.bansheeproject.Banshee
[1 Debug 22:46:39.438] Core service started (PlaybackController, 0.002643)
[1 Debug 22:46:39.444] Starting - Startup Job
[1 Debug 22:46:39.445] Core service started (JobScheduler, 0.006309)
[1 Debug 22:46:39.454] IO provider extension loaded (Banshee.IO.Gio.Provider)
[1 Debug 22:46:39.480] Loaded HardwareManager backend: Banshee.Hardware.Gio
[1 Debug 22:46:39.482] Core service started (HardwareManager, 0.03699)
[1 Debug 22:46:39.483] Bus.Session.RequestName ('org.bansheeproject.CollectionIndexer') replied with PrimaryOwner
[1 Debug 22:46:39.484] Registering remote object /org/bansheeproject/Banshee/CollectionIndexerService (Banshee.Collection.Indexer.CollectionIndexerService) on org.bansheeproject.CollectionIndexer
[1 Debug 22:46:39.485] Core service started (CollectionIndexerService, 0.003288)
[1 Debug 22:46:39.486] Core service started (SaveTrackMetadataService, 0.001127)
[1 Debug 22:46:39.568] Adding icon theme search path: /usr/share/banshee/icons
[1 Debug 22:46:39.569] Core service started (GtkElementsService, 0.082271)
[1 Debug 22:46:39.570] Core service started (InterfaceActionService, 0.001295)
[1 Debug 22:46:39.680] Extension actions loaded: MetadataFixActions
[1 Debug 22:46:39.680] Registering remote object /org/bansheeproject/Banshee/GlobalUIActions (Banshee.Gui.GlobalActions) on org.bansheeproject.Banshee
[1 Debug 22:46:39.685] Album artwork path set to /home/jonny/.cache/media-art
[1 Debug 22:46:39.714] Core service started (ArtworkManager, 0.033404)
[1 Debug 22:46:39.714] Core service started (BookmarksService, 0.000286)
[1 Debug 22:46:40.129] Constructed Nereid interface: 0.369123
[1 Debug 22:46:40.220] Creating new surface cache for 90px images, capped at 0.93 MiB (30 items)
[1 Debug 22:46:40.291] Registering remote object /org/bansheeproject/Banshee/ClientWindow (Nereid.PlayerInterface) on org.bansheeproject.Banshee
[1 Debug 22:46:40.291] Core service started (NereidPlayerInterface, 0.567036)
[1 Debug 22:46:40.293] Extension service started (DapService, 0.001486)
[1 Warn  22:46:40.320] Caught an exception - System.ApplicationException: No support GNOME Settings Daemon could be reached. (in `Banshee.MultimediaKeys')
  at Banshee.MultimediaKeys.MultimediaKeysService.Banshee.ServiceStack.IExtensionService.Initialize () [0x00000] in <filename unknown>:0 
  at Banshee.ServiceStack.ServiceManager.StartExtension (Mono.Addins.TypeExtensionNode node) [0x00000] in <filename unknown>:0 
[1 Warn  22:46:40.320] Extension `Banshee.MultimediaKeys.MultimediaKeysService' not started: No support GNOME Settings Daemon could be reached.
[1 Debug 22:46:40.329] Extension service started (MprisService, 0.008375)
[1 Debug 22:46:40.339] Extension service started (SoundMenuService, 0.010323)
[1 Debug 22:46:40.341] Extension service started (CoverArtService, 0.002255)
[1 Debug 22:46:40.342] Extension service started (DaapService, 0.000743)
[1 Debug 22:46:40.354] Extension service started (BpmService, 0.011168)
[1 Info  22:46:40.359] Updating web proxy from GConf
[1 Debug 22:46:40.366] Direct connection, no proxy in use
[1 Debug 22:46:40.391] Extension service started (GnomeService, 0.037822)
[1 Debug 22:46:40.712] Extension service started (GStreamerCoreService, 0.320453)
[1 Warn  22:46:40.715] Caught an exception - System.ApplicationException: No support GNOME Settings Daemon could be reached. (in `Banshee.MultimediaKeys')
  at Banshee.MultimediaKeys.MultimediaKeysService.Banshee.ServiceStack.IExtensionService.Initialize () [0x00000] in <filename unknown>:0 
  at Banshee.ServiceStack.ServiceManager.StartExtension (Mono.Addins.TypeExtensionNode node) [0x00000] in <filename unknown>:0 
[1 Warn  22:46:40.715] Extension `Banshee.MultimediaKeys.MultimediaKeysService' not started: No support GNOME Settings Daemon could be reached.
[1 Info  22:46:40.716] All services are started 1.631495
[1 Debug 22:46:41.004] Creating Pango.Layout, configuring Cairo.Context
[1 Debug 22:46:41.095] Extension source loaded: Now Playing
[1 Debug 22:46:41.099] Starting GTK main loop
[1 Debug 22:46:41.333] Creating Pango.Layout, configuring Cairo.Context
[1 Debug 22:46:41.356] Creating Pango.Layout, configuring Cairo.Context
[1 Info  22:46:41.434] nereid Client Started
[1 Debug 22:46:41.437] Delayed Initializating Banshee.MediaEngine.PlayerEngineService
[1 Debug 22:46:41.461] (libbanshee:player) Audiosink has volume: YES
[1 Debug 22:46:41.480] (libbanshee:player) Using system (gst-plugins-good) equalizer element
[1 Debug 22:46:41.550] Player state change: NotReady -> Ready
[1 Debug 22:46:41.555] Loaded equalizer presets: 0.00025
[1 Debug 22:46:41.561] Selected equalizer: Rock
[1 Debug 22:46:41.565] Player state change: Ready -> Idle
[1 Debug 22:46:41.568] (libbanshee:player) Disabled ReplayGain
[1 Info  22:46:41.569] GStreamer version 0.10.36.0, gapless: True, replaygain: False
[1 Debug 22:46:41.572] Delayed Initializating Banshee.Dap.DapService
[1 Debug 22:46:41.580] Dap support extension loaded: Banshee.Dap.AppleDevice
[1 Debug 22:46:41.581] Dap support extension loaded: Banshee.Dap.Karma
[1 Debug 22:46:41.604] Delayed Initializating Banshee.Daap.DaapService
[5 Info  22:46:41.634] AppleDeviceSource is ignoring unmounted volume 44 GB Filesystem
[5 Info  22:46:41.653] AppleDeviceSource is ignoring unmounted volume System Reserved
[9 Debug 22:46:41.735] DAAP Proxy listening for connections on port 8089
[1 Debug 22:46:42.622] Finished - Startup Job
[1 Debug 22:46:42.626] Starting - Downloading Cover Art
[10 Debug 22:46:42.628] Finished - Downloading Cover Art
[1 Debug 22:46:51.206] Loaded IScreensaverManager: Banshee.GnomeBackend.GnomeScreensaverManager
Domain: 'Gtk' Level: Critical
Message: IA__gtk_style_detach: assertion `style->attach_count > 0' failed
Trace follows:
   at GLib.Log.PrintTraceLogFunction(System.String domain, LogLevelFlags level, System.String message)
   at Gtk.Widget.gtk_widget_set_style(IntPtr , IntPtr )
   at Gtk.Widget.set_Style(Gtk.Style value)
   at Hyena.Widgets.RatingEntry.OnRealized()
   at Gtk.Widget.realized_cb(IntPtr widget)
   at Gtk.Application.gtk_main()
   at Gtk.Application.Run()
   at Banshee.Gui.GtkBaseClient.Run()
   at Banshee.Gui.GtkBaseClient.Startup()
   at Hyena.Gui.CleanRoomStartup.Startup(Hyena.Gui.StartupInvocationHandler startup)
   at Banshee.Gui.GtkBaseClient.Startup()
   at Banshee.Gui.GtkBaseClient.Startup(System.String[] args)
   at Nereid.Client.Main(System.String[] args)
   at System.AppDomain.ExecuteAssembly(System.AppDomain , System.Reflection.Assembly , System.String[] )
   at System.AppDomain.ExecuteAssemblyInternal(System.Reflection.Assembly a, System.String[] args)
   at System.AppDomain.ExecuteAssembly(System.String assemblyFile, System.Security.Policy.Evidence assemblySecurity, System.String[] args)
   at System.AppDomain.ExecuteAssembly(System.String assemblyFile)
   at Booter.Booter.BootClient(System.String clientName)
   at Booter.Booter.Main()
[1 Debug 22:48:04.998] Querying model for track to play in off:Next mode
[1 Debug 22:48:09.664] Querying model for track to play in off:Next mode
[1 Debug 22:48:22.511] Service disposed (GStreamerCoreService)
[1 Debug 22:48:22.513] Service disposed (GnomeService)
[1 Debug 22:48:22.514] Service disposed (BpmService)
[1 Debug 22:48:22.521] Service disposed (DaapService)
[1 Debug 22:48:22.521] Service disposed (CoverArtService)
[1 Debug 22:48:22.524] Service disposed (SoundMenuService)
[1 Debug 22:48:22.530] Service disposed (MprisService)
[1 Debug 22:48:22.533] Service disposed (DapService)
[1 Debug 22:48:22.538] Service disposed (NereidPlayerInterface)
[1 Debug 22:48:22.539] Service disposed (BookmarksService)
[1 Debug 22:48:22.539] Service disposed (CollectionIndexerService)
[1 Debug 22:48:22.541] Service disposed (HardwareManager)
[1 Debug 22:48:22.542] (libbanshee:player) bp_stop: setting state to GST_STATE_NULL
[1 Debug 22:48:22.544] (libbanshee:player) bp_destroy: disposed player
[1 Debug 22:48:22.544] Service disposed (PlayerEngine)
[1 Debug 22:48:22.549] Service disposed (SourceManager)
[1 Debug 22:48:22.549] Service disposed (Network)
[1 Debug 22:48:22.551] Service disposed (DbConnection)
jonny@jonny-desktop:~$ 


```

I should add that the top menu bar still seems to work but all the main panels are frozen

---

### Post by Yellow Pasque on 2014-06-07
I think it might have something to do with your GTK3 theme (I could be way off though). Do you know what theme you're using for GTK apps?

---

### Post by Jonny87 on 2014-06-07
Thanks mate, seems that you were right, I changed the gtk app theme to radiance instead of oxygen-gtk and now it seem to be working fine. I thought i may have been some thing todo with gtk but wasn't sure what exactly. Now I just need to work out if I can change to a slightly better theme, I'm not a fan of the orange in the Radiance theme, but there's not a lot of options in the drop down box.

I'll keep playing with banshee over the next couple of hours to make sure it has come right completely, and if so I'll mark the thread solved then.

---

