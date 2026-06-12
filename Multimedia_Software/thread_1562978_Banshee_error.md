---
title: "Banshee error"
date: 2010-08-28
forum: Multimedia Software
---

### Post by efranor on 2010-08-28
Ok after I turned on my laptop and logged into my account I started banshee to listen to some music as I play a few games on my console but Banshee just didn't play my mp3s. At first i thought that i forgot to mount my drive but it was mounted so I ran debug and got this:

** Running Mono with --debug   **
[1 Debug 17:41:12.221] Bus.Session.RequestName ('org.bansheeproject.Banshee') replied with InQueue
efranor@efranor-laptop:~$ banshee --debug
** Running Mono with --debug   **
[1 Info  17:41:24.192] Running Banshee 1.6.1: [Ubuntu 10.04 LTS (linux-gnu, i486) @ 2010-06-18 09:51:55 UTC]
[1 Debug 17:41:24.228] Initializing GTK
[1 Debug 17:41:27.321] Post-Initializing GTK
[1 Debug 17:41:27.357] Configuration client extension loaded (Banshee.GnomeBackend.GConfConfigurationClient)
[1 Debug 17:41:27.374] Using default gconf-base-key
[1 Debug 17:41:27.467] Bus.Session.RequestName ('org.bansheeproject.Banshee') replied with PrimaryOwner
[1 Debug 17:41:27.479] Core service started (DBusServiceManager, 0.001488 )
[1 Debug 17:41:27.482] Registering remote object /org/bansheeproject/Banshee/DBusCommandService (Banshee.ServiceStack.DBusCommandService) on org.bansheeproject.Banshee
[1 Debug 17:41:27.504] Core service started (DBusCommandService, 0.024358 )
[1 Debug 17:41:27.653] Opened SQLite connection to /home/efranor/.config/banshee-1/banshee.db
[1 Debug 17:41:27.654] Core service started (DbConnection, 0.149506)
[1 Debug 17:41:27.660] Database version 41 is up to date
[1 Debug 17:41:27.699] Core service started (PreferenceService, 0.015865)
[1 Debug 17:41:27.700] Registering remote object /org/bansheeproject/Banshee/SourceManager (Banshee.Sources.SourceManager) on org.bansheeproject.Banshee
[1 Debug 17:41:27.700] Core service started (SourceManager, 0.000868 )
[1 Debug 17:41:27.701] Core service started (MediaProfileManager, 0.000237)
[1 Debug 17:41:27.704] Registering remote object /org/bansheeproject/Banshee/PlayerEngine (Banshee.MediaEngine.PlayerEngineService) on org.bansheeproject.Banshee
[1 Debug 17:41:27.706] Core service started (PlayerEngine, 0.005183)
[1 Debug 17:41:27.748] IO provider extension loaded (Banshee.IO.Unix.Provider)
[1 Debug 17:41:27.771] Core service started (TranscoderService, 0.035974)
[1 Debug 17:41:27.779] Registering remote object /org/bansheeproject/Banshee/PlaybackController (Banshee.PlaybackController.PlaybackControllerService) on org.bansheeproject.Banshee
[1 Debug 17:41:27.780] Core service started (PlaybackController, 0.008475)
[1 Debug 17:41:27.781] Core service started (ImportSourceManager, 0.000776)  
[1 Debug 17:41:27.791] Core service started (LibraryImportManager, 0.009993) 
[1 Debug 17:41:27.792] Core service started (JobScheduler, 0.001083)         
[1 Debug 17:41:27.820] Core service started (HardwareManager, 0.027745)      
[1 Debug 17:41:27.824] Bus.Session.RequestName ('org.bansheeproject.CollectionIndexer') replied with PrimaryOwner                                         
[1 Debug 17:41:27.826] Registering remote object /org/bansheeproject/Banshee/CollectionIndexerService (Banshee.Collection.Indexer.CollectionIndexerService) on org.bansheeproject.CollectionIndexer                                    
[1 Debug 17:41:27.827] Core service started (CollectionIndexerService, 0.006824)                                                                          
[1 Debug 17:41:27.828] Core service started (SaveMetadataService, 0.001621)
[1 Debug 17:41:27.868] Adding icon theme search path: /usr/share/banshee-1/icons
[1 Debug 17:41:27.869] Core service started (GtkElementsService, 0.040853)
[1 Debug 17:41:27.871] Core service started (InterfaceActionService, 0.001957)
[1 Debug 17:41:27.982] Registering remote object /org/bansheeproject/Banshee/GlobalUIActions (Banshee.Gui.GlobalActions) on org.bansheeproject.Banshee
[1 Debug 17:41:27.983] Album artwork path set to /home/efranor/.cache/media-art
[1 Debug 17:41:28.001] Core service started (ArtworkManager, 0.018653)
[1 Debug 17:41:28.394] Adding context page lastfm-recommendations
[1 Debug 17:41:28.440] Adding context page wikipedia
[1 Warn  17:41:28.829] Caught an exception - GLib.GException: Icon 'process-working' not present in theme (in `gtk-sharp')
  at Gtk.IconTheme.LoadIcon (System.String icon_name, Int32 size, IconLookupFlags flags) [0x00000] 
  at Banshee.Gui.Widgets.TaskStatusIcon..ctor () [0x00000] 
[1 Debug 17:41:28.860] Constructed Nereid interface: 0.803014
[1 Debug 17:41:28.994] Creating new surface cache for 90px images, capped at 0.25 MiB (8 items)
[1 Debug 17:41:29.099] Registering remote object /org/bansheeproject/Banshee/ClientWindow (Nereid.PlayerInterface) on org.bansheeproject.Banshee
[1 Debug 17:41:29.099] Core service started (NereidPlayerInterface, 1.093948 )
[1 Debug 17:41:29.141] Extension service started (GStreamerCoreService, 0.041349)
[1 Debug 17:41:29.156] Extension service started (BpmService, 0.014713)
[1 Debug 17:41:29.168] Extension service started (PodcastService, 0.012345)
[1 Debug 17:41:29.169] Extension service started (DapService, 0.000367)
[1 Debug 17:41:29.170] Extension service started (DaapService, 0.001449)
[1 Debug 17:41:29.175] Extension service started (GnomeService, 0.004051)
[1 Debug 17:41:29.213] Core service started (Network, 0.008906)
[1 Debug 17:41:29.214] Audioscrobbler state: connected
[1 Debug 17:41:29.216] Extension service started (AudioscrobblerService, 0.041859)
[1 Debug 17:41:29.247] Extension service started (NotificationAreaService, 0.030965)
[1 Debug 17:41:29.275] Extension service started (BookmarksService, 0.027314)
[1 Debug 17:41:29.277] Extension service started (CoverArtService, 0.002243)
[1 Debug 17:41:29.342] Extension service started (AudioCdService, 0.065086)
[1 Info  17:41:29.344] All services are started 1.875605
[1 Debug 17:41:30.430] Registering remote object /org/bansheeproject/Banshee/SourceManager/PlayQueue (Banshee.PlayQueue.PlayQueueSource) on org.bansheeproject.Banshee
[1 Debug 17:41:30.535] Starting GTK main loop
[1 Debug 17:41:30.868] Creating Pango.Layout, configuring Cairo.Context
[1 Debug 17:41:30.902] Creating Pango.Layout, configuring Cairo.Context
[1 Debug 17:41:30.931] Creating Pango.Layout, configuring Cairo.Context
[1 Info  17:41:31.069] nereid Client Started
[1 Debug 17:41:31.071] Delayed Initializating Banshee.MediaEngine.PlayerEngineService
[1 Debug 17:41:31.091] (libbanshee: player) Using system (gst-plugins-good) equalizer element
[1 Debug 17:41:31.289] Player state change: NotReady -> Ready
[1 Debug 17:41:31.316] Loaded equalizer presets: 0.021212
[1 Debug 17:41:31.322] Selected equalizer: Power Metal
[1 Debug 17:41:31.326] Syncing equalizer to engine: Power Metal
[1 Debug 17:41:31.332] Player state change: Ready -> Idle
[1 Debug 17:41:31.340] (libbanshee: player) Disabled ReplayGain
[1 Debug 17:41:31.342] Delayed Initializating Banshee.Podcasting.PodcastService
[1 Debug 17:41:31.472] Delayed Initializating Banshee.Dap.DapService
[1 Debug 17:41:31.478] Dap support extension loaded: Banshee.Dap.MassStorage
[1 Debug 17:41:31.478] Dap support extension loaded: Banshee.Dap.Ipod
[1 Debug 17:41:31.481] Dap support extension loaded: Banshee.Dap.Mtp
[1 Debug 17:41:31.482] Dap support extension loaded: Banshee.Dap.Karma
[2 Debug 17:41:31.487] Refreshing any podcasts that haven't been updated in over an hour
[1 Debug 17:41:32.047] Delayed Initializating Banshee.Daap.DaapService
[3 Debug 17:41:32.685] DAAP Proxy listening for connections on port 8089
[1 Debug 17:41:33.820] EqualizerManager - Saved equalizers to disk
[1 Debug 17:41:50.313] Player state change: Idle -> Loading
[1 Debug 17:41:50.340] (libbanshee: player) bp_stop: setting state to GST_STATE_NULL
[1 Debug 17:41:50.342] Player state change: Loading -> Idle
[1 Error 17:41:50.344] GStreamer resource error: OpenRead
[1 Debug 17:41:50.600] Querying model for track to play in off:Next mode
[1 Debug 17:41:50.609] Player state change: Idle -> Loading
[1 Debug 17:41:50.663] (libbanshee: player) bp_stop: setting state to GST_STATE_NULL
[1 Debug 17:41:50.667] Player state change: Loading -> Idle
[1 Error 17:41:50.670] GStreamer resource error: OpenRead
[1 Debug 17:41:50.920] Querying model for track to play in off:Next mode
[1 Debug 17:41:50.921] Player state change: Idle -> Loading
[1 Debug 17:41:50.974] (libbanshee: player) bp_stop: setting state to GST_STATE_NULL
[1 Debug 17:41:50.974] Player state change: Loading -> Idle
[1 Error 17:41:50.976] GStreamer resource error: OpenRead
[1 Debug 17:41:51.226] Querying model for track to play in off:Next mode
[1 Debug 17:41:51.227] Player state change: Idle -> Loading
[1 Debug 17:41:51.283] (libbanshee: player) bp_stop: setting state to GST_STATE_NULL
[1 Debug 17:41:51.283] Player state change: Loading -> Idle
[1 Error 17:41:51.285] GStreamer resource error: OpenRead
[1 Debug 17:41:51.535] Querying model for track to play in off:Next mode
[1 Debug 17:41:51.536] Player state change: Idle -> Loading
[1 Debug 17:41:51.588] (libbanshee: player) bp_stop: setting state to GST_STATE_NULL

---

