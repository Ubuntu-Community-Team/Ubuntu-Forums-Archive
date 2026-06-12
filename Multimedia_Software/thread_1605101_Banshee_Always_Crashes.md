---
title: "Banshee Always Crashes"
date: 2010-10-24
forum: Multimedia Software
---

### Post by rfdeshon on 2010-10-24
Just upgraded to 10.10 NBR. Every time I launch banshee it crashes within seconds of opening. I tried nuking ~/.config/banshee-1 and the problem persists.

Output from banshee --debug:
```
rdeshone@molly:~$ banshee --debug
** Running Mono with --debug   **
[1 Info  21:32:36.653] Running Banshee 1.7.6: [Ubuntu maverick (development branch) (linux-gnu, i686) @ 2010-09-18 20:47:48 UTC]
[1 Debug 21:32:36.770] Initializing GTK
[1 Debug 21:32:51.046] Post-Initializing GTK
[1 Debug 21:32:51.192] Configuration client extension loaded (Banshee.GnomeBackend.GConfConfigurationClient)
[1 Debug 21:32:51.279] Using default gconf-base-key
[1 Debug 21:32:51.539] Bus.Session.RequestName ('org.bansheeproject.Banshee') replied with PrimaryOwner
[1 Debug 21:32:51.994] Core service started (DBusServiceManager, 0.007675)
[1 Debug 21:32:52.010] Registering remote object /org/bansheeproject/Banshee/DBusCommandService (Banshee.ServiceStack.DBusCommandService) on org.bansheeproject.Banshee
[1 Debug 21:32:52.113] Core service started (DBusCommandService, 0.116652)
[1 Debug 21:32:52.527] Opened SQLite (version 3.7.2) connection to /home/rdeshone/.config/banshee-1/banshee.db
[1 Debug 21:32:52.531] Core service started (DbConnection, 0.416917)
[1 Debug 21:32:52.553] Migrating from database version 0 to 43
[1 Debug 21:32:52.658] Running ANALYZE against database to improve performance
[1 Debug 21:32:52.668] Updating collation keys for locale en-US (was )
[1 Info  21:32:52.683] Starting collection of anonymous usage data
[1 Debug 21:32:52.962] Core service started (PreferenceService, 0.099947)
[1 Debug 21:32:52.964] Registering remote object /org/bansheeproject/Banshee/SourceManager (Banshee.Sources.SourceManager) on org.bansheeproject.Banshee
[1 Debug 21:32:52.965] Core service started (SourceManager, 0.002832)
[1 Debug 21:32:53.013] Core service started (MediaProfileManager, 0.000981)
[1 Debug 21:32:53.028] Registering remote object /org/bansheeproject/Banshee/PlayerEngine (Banshee.MediaEngine.PlayerEngineService) on org.bansheeproject.Banshee
[1 Debug 21:32:53.045] Core service started (PlayerEngine, 0.031757)
[1 Debug 21:32:53.133] Registering remote object /org/bansheeproject/Banshee/PlaybackController (Banshee.PlaybackController.PlaybackControllerService) on org.bansheeproject.Banshee
[1 Debug 21:32:53.137] Core service started (PlaybackController, 0.019585)
[1 Debug 21:32:53.179] Starting - Startup Job
[1 Debug 21:32:53.182] Core service started (JobScheduler, 0.044616)
[1 Debug 21:32:53.270] IO provider extension loaded (Banshee.IO.Gio.Provider)
[1 Debug 21:32:53.459] Loaded HardwareManager backend: Banshee.Hardware.Gio
[1 Debug 21:32:53.468] Core service started (HardwareManager, 0.286392)
[1 Debug 21:32:53.488] Bus.Session.RequestName ('org.bansheeproject.CollectionIndexer') replied with PrimaryOwner
[1 Debug 21:32:53.494] Registering remote object /org/bansheeproject/Banshee/CollectionIndexerService (Banshee.Collection.Indexer.CollectionIndexerService) on org.bansheeproject.CollectionIndexer
[1 Debug 21:32:53.502] Core service started (CollectionIndexerService, 0.033875)
[1 Debug 21:32:53.511] Core service started (SaveTrackMetadataService, 0.009057)
[1 Debug 21:32:53.553] Adding icon theme search path: /usr/share/banshee-1/icons
[1 Debug 21:32:53.559] Core service started (GtkElementsService, 0.04739)
[1 Debug 21:32:53.566] Core service started (InterfaceActionService, 0.00636)
[1 Debug 21:32:54.168] Extension actions loaded: MetadataFixActions
[1 Debug 21:32:54.170] Registering remote object /org/bansheeproject/Banshee/GlobalUIActions (Banshee.Gui.GlobalActions) on org.bansheeproject.Banshee
[1 Debug 21:32:54.177] Album artwork path set to /home/rdeshone/.cache/media-art
[1 Debug 21:32:54.286] Core service started (ArtworkManager, 0.115604)
[1 Debug 21:32:54.290] Core service started (BookmarksService, 0.003237)
[1 Debug 21:32:55.336] Adding context page wikipedia
[1 Debug 21:32:55.697] Adding context page lastfm-recommendations
[1 Debug 21:32:56.853] Constructed Nereid interface: 2.433494
[1 Debug 21:32:57.321] Creating new surface cache for 90px images, capped at 0.56 MiB (18 items)
[1 Debug 21:32:57.612] Registering remote object /org/bansheeproject/Banshee/ClientWindow (Nereid.PlayerInterface) on org.bansheeproject.Banshee
[1 Debug 21:32:57.613] Core service started (NereidPlayerInterface, 3.323013)
[1 Debug 21:32:57.758] Extension service started (GStreamerCoreService, 0.141028)
[1 Debug 21:32:57.786] Extension service started (BpmService, 0.027745)
[1 Debug 21:32:57.809] Using GNOME 2.22 API for Multimedia Keys
[1 Debug 21:32:57.810] Extension service started (MultimediaKeysService, 0.024161)
[1 Debug 21:32:57.817] Extension service started (LibraryWatcherService, 0.00699)
[1 Debug 21:32:57.824] Extension service started (DapService, 0.00646)
[1 Debug 21:32:57.837] Extension service started (PodcastService, 0.012817)
[1 Debug 21:32:57.841] Extension service started (DaapService, 0.003712)
[1 Info  21:32:57.856] Updating web proxy from GConf
[1 Debug 21:32:57.876] Direct connection, no proxy in use
[1 Debug 21:32:57.951] Extension service started (GnomeService, 0.109659)
[1 Debug 21:32:58.296] Core service started (Network, 0.020214)
[1 Debug 21:32:58.298] Audioscrobbler state: connected
[1 Debug 21:32:58.305] Extension service started (AudioscrobblerService, 0.353916)
[1 Debug 21:32:58.321] Extension service started (LastfmStreamingService, 0.015909)
[1 Debug 21:32:58.720] Extension service started (AmazonMp3DownloaderService, 0.398831)
[1 Debug 21:32:58.832] Extension service started (NotificationAreaService, 0.111593)
[1 Debug 21:32:58.845] Extension service started (CoverArtService, 0.013135)
[1 Debug 21:32:58.912] Extension service started (AudioCdService, 0.066942)
[1 Info  21:32:58.915] All services are started 7.370705
[1 Debug 21:33:00.466] Registering remote object /org/bansheeproject/Banshee/SourceManager/PlayQueue (Banshee.PlayQueue.PlayQueueSource) on org.bansheeproject.Banshee
[1 Debug 21:33:00.468] Extension source loaded: Play Queue
[1 Debug 21:33:00.495] Extension source loaded: Now Playing
[1 Debug 21:33:00.639] Extension source loaded: Last.fm
[1 Warn  21:33:00.698] Migrating Internet Radio Stations - System.IO.DirectoryNotFoundException: Directory '/home/rdeshone/.config/banshee-1/plugins/stations/user' not found. (in `mscorlib')
  at System.IO.Directory.GetFileSystemEntries (System.String path, System.String searchPattern, FileAttributes mask, FileAttributes attrs) [0x00000] in <filename unknown>:0 
  at System.IO.Directory.GetFiles (System.String path, System.String searchPattern) [0x00000] in <filename unknown>:0 
  at Banshee.InternetRadio.XspfMigrator.Migrate () [0x00000] in <filename unknown>:0 
[1 Debug 21:33:00.719] Extension source loaded: Radio
[1 Debug 21:33:00.788] Extension source loaded: File System Queue
[1 Debug 21:33:00.813] Extension source loaded: Amazon MP3 Store
[1 Debug 21:33:00.856] Extension source loaded: Internet Archive
[1 Debug 21:33:00.891] Extension source loaded: Miro Guide
[1 Debug 21:33:00.979] Extension source loaded: Audiobooks, etc
[1 Debug 21:33:01.014] Starting GTK main loop
[1 Debug 21:33:01.790] Creating Pango.Layout, configuring Cairo.Context
[1 Debug 21:33:02.063] Creating Pango.Layout, configuring Cairo.Context
[1 Debug 21:33:02.125] Creating Pango.Layout, configuring Cairo.Context
[1 Info  21:33:02.351] nereid Client Started
[1 Debug 21:33:02.364] Delayed Initializating Banshee.MediaEngine.PlayerEngineService
[1 Debug 21:33:02.386] (libbanshee:player) Stream volume supported: YES
[1 Debug 21:33:02.395] (libbanshee:player) Audiosink has volume: NO
[1 Debug 21:33:02.405] (libbanshee:player) Using system (gst-plugins-good) equalizer element
[1 Debug 21:33:02.593] Player state change: NotReady -> Ready
[1 Debug 21:33:02.610] Loaded equalizer presets: 0.000615
[1 Debug 21:33:02.626] Selected equalizer: Rock
[1 Debug 21:33:02.643] Player state change: Ready -> Idle
[1 Debug 21:33:02.662] (libbanshee:player) Enabled ReplayGain
[1 Debug 21:33:02.719] (libbanshee:player) scaled volume: 1.00 (ReplayGain) * 0.00 (User) = 0.00
[1 Debug 21:33:02.726] (libbanshee:player) scaled volume: 1.00 (ReplayGain) * 0.80 (User) = 0.80
[1 Debug 21:33:02.743] Delayed Initializating Banshee.LibraryWatcher.LibraryWatcherService
[1 Debug 21:33:02.782] Core service started (LibraryImportManager, 0.023926)
[1 Debug 21:33:02.828] Started LibraryWatcher for Music (/home/rdeshone/Music/)
[1 Debug 21:33:02.869] Starting
[1 Debug 21:33:03.005] Starting
[1 Debug 21:33:03.127] Delayed Initializating Banshee.Dap.DapService
[1 Debug 21:33:03.218] Dap support extension loaded: Banshee.Dap.MassStorage
[1 Debug 21:33:03.227] Dap support extension loaded: Banshee.Dap.AppleDevice
[1 Debug 21:33:03.233] Dap support extension loaded: Banshee.Dap.Mtp
[1 Debug 21:33:03.257] Dap support extension loaded: Banshee.Dap.Karma
[1 Debug 21:33:03.267] Delayed Initializating Banshee.Podcasting.PodcastService
[1 Debug 21:33:03.805] Delayed Initializating Banshee.Daap.DaapService
[2 Debug 21:33:03.887] Refreshing any podcasts that haven't been updated in over an hour
[4 Debug 21:33:04.931] Found DAAP share Jessica Keck&#8217;s Library, trying to resolve...
[3 Debug 21:33:04.934] Finished - Rescanning 1 of 1
[1 Debug 21:33:05.030] Finished - Startup Job
[4 Debug 21:33:05.307] Managed to resolve DAAP share Jessica Keck&#8217;s Library.
[4 Debug 21:33:05.363] OnServiceResolved provided 192.168.0.14
[4 Debug 21:33:05.364] Using address 192.168.0.14
[5 Debug 21:33:05.439] DAAP Proxy listening for connections on port 8089
Exception in Gtk# callback delegate
  Note: Applications can use GLib.ExceptionManager.UnhandledException to handle the exception.
System.NullReferenceException: Object reference not set to an instance of an object
  at Hyena.Widgets.RoundedFrame.DrawFrame (Cairo.Context cr, Rectangle clip) [0x00000] in <filename unknown>:0 
  at Hyena.Widgets.RoundedFrame.OnExposeEvent (Gdk.EventExpose evnt) [0x00000] in <filename unknown>:0 
  at Gtk.Widget.exposeevent_cb (IntPtr widget, IntPtr evnt) [0x00000] in <filename unknown>:0 
   at GLib.ExceptionManager.RaiseUnhandledException(System.Exception e, Boolean is_terminal)
   at Gtk.Widget.exposeevent_cb(IntPtr widget, IntPtr evnt)
   at Gtk.Application.gtk_main()
   at Gtk.Application.Run()
   at Banshee.Gui.GtkBaseClient.Run()
   at Banshee.Gui.GtkBaseClient.Startup()
   at Hyena.Gui.CleanRoomStartup.Startup(Hyena.Gui.StartupInvocationHandler startup)
   at Banshee.Gui.GtkBaseClient.Startup()
   at Banshee.Gui.GtkBaseClient.Startup(System.String[] args)
   at Nereid.Client.Main(System.String[] args)
   at System.AppDomain.ExecuteAssembly(System.Reflection.Assembly , System.String[] )
   at System.AppDomain.ExecuteAssemblyInternal(System.Reflection.Assembly a, System.String[] args)
   at System.AppDomain.ExecuteAssembly(System.String assemblyFile, System.Security.Policy.Evidence assemblySecurity, System.String[] args)
   at System.AppDomain.ExecuteAssembly(System.String assemblyFile)
   at Booter.Booter.BootClient(System.String clientName)
   at Booter.Booter.Main()

```

Halp?

---

### Post by rfdeshon on 2010-10-24
Hrmm... disregard this. I finally re-read the output and realized the DAAP plugin was causing the crash. Disabling it has (so far) resulted in banshee continuing to run. I need to drink more coffee before I start breaking things clearly.

---

