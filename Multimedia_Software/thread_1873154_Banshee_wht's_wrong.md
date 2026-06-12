---
title: "Banshee wht's wrong?"
date: 2011-10-31
forum: Multimedia Software
---

### Post by saltcushy on 2011-10-31
```
banshee --debug 
** Running Mono with --debug   ** 
[1 Info  20:21:01.217] Running Banshee 2.2.0: [Ubuntu oneiric (development branch) (linux-gnu, i686) @ 2011-09-23 04:51:00 UTC] 
[1 Debug 20:21:01.236] Initializing GTK 
[1 Debug 20:21:02.115] Post-Initializing GTK 
[1 Debug 20:21:02.124] Configuration client extension loaded (Banshee.GnomeBackend.GConfConfigurationClient) 
[1 Debug 20:21:02.130] Using default gconf-base-key 
[1 Debug 20:21:02.173] Bus.Session.RequestName ('org.bansheeproject.Banshee') replied with PrimaryOwner 
[1 Debug 20:21:02.232] Core service started (DBusServiceManager, 0,001249) 
[1 Debug 20:21:02.234] Registering remote object /org/bansheeproject/Banshee/DBusCommandService (Banshee.ServiceStack.DBusCommandService) on org.bansheeproject.Banshee 
[1 Debug 20:21:02.241] Core service started (DBusCommandService, 0,00823) 
[1 Debug 20:21:02.274] Opened SQLite (version 3.7.7) connection to /home/lbu/.config/banshee-1/banshee.db 
[1 Debug 20:21:02.275] Core service started (DbConnection, 0,034212) 
[1 Debug 20:21:02.280] Database version 44 is up to date 
[1 Debug 20:21:02.314] Core service started (PreferenceService, 0,012489) 
[1 Debug 20:21:02.330] Core service started (Network, 0,015553) 
[1 Debug 20:21:02.330] Registering remote object /org/bansheeproject/Banshee/SourceManager (Banshee.Sources.SourceManager) on org.bansheeproject.Banshee 
[1 Debug 20:21:02.330] Core service started (SourceManager, 0,000704) 
[1 Debug 20:21:02.335] Core service started (MediaProfileManager, 0,000233) 
[1 Debug 20:21:02.340] Registering remote object /org/bansheeproject/Banshee/PlayerEngine (Banshee.MediaEngine.PlayerEngineService) on org.bansheeproject.Banshee 
[1 Debug 20:21:02.342] Core service started (PlayerEngine, 0,006053) 
[1 Debug 20:21:02.365] Registering remote object /org/bansheeproject/Banshee/PlaybackController (Banshee.PlaybackController.PlaybackControllerService) on org.bansheeproject.Banshee 
[1 Debug 20:21:02.367] Core service started (PlaybackController, 0,003322) 
[1 Debug 20:21:02.372] Starting - Startup Job 
[1 Debug 20:21:02.372] Core service started (JobScheduler, 0,00514) 
[1 Debug 20:21:02.390] IO provider extension loaded (Banshee.IO.Gio.Provider) 
[1 Debug 20:21:02.433] Loaded HardwareManager backend: Banshee.Hardware.Gio 
[1 Debug 20:21:02.435] Core service started (HardwareManager, 0,0623) 
[1 Debug 20:21:02.437] Bus.Session.RequestName ('org.bansheeproject.CollectionIndexer') replied with PrimaryOwner 
[1 Debug 20:21:02.438] Registering remote object /org/bansheeproject/Banshee/CollectionIndexerService (Banshee.Collection.Indexer.CollectionIndexerService) on org.bansheeproject.CollectionIndexer 
[1 Debug 20:21:02.440] Core service started (CollectionIndexerService, 0,004633) 
[1 Debug 20:21:02.441] Core service started (SaveTrackMetadataService, 0,00124) 
[1 Debug 20:21:02.457] Adding icon theme search path: /usr/share/banshee/icons 
[1 Debug 20:21:02.458] Core service started (GtkElementsService, 0,017045) 
[1 Debug 20:21:02.459] Core service started (InterfaceActionService, 0,001175) 
[1 Debug 20:21:02.554] Extension actions loaded: MetadataFixActions 
[1 Debug 20:21:02.555] Registering remote object /org/bansheeproject/Banshee/GlobalUIActions (Banshee.Gui.GlobalActions) on org.bansheeproject.Banshee 
[1 Debug 20:21:02.556] Album artwork path set to /home/lbu/.cache/media-art 
[1 Debug 20:21:02.579] Core service started (ArtworkManager, 0,024145) 
[1 Debug 20:21:02.579] Core service started (BookmarksService, 0,000128) 
[1 Debug 20:21:02.801] Adding context page lastfm-recommendations 
[1 Debug 20:21:02.824] Adding context page wikipedia 
[1 Debug 20:21:03.019] Constructed Nereid interface: 0,399045 
[1 Debug 20:21:03.103] Creating new surface cache for 90px images, capped at 0,93 MiB (30 items) 
[1 Debug 20:21:03.152] Registering remote object /org/bansheeproject/Banshee/ClientWindow (Nereid.PlayerInterface) on org.bansheeproject.Banshee 
[1 Debug 20:21:03.153] Core service started (NereidPlayerInterface, 0,555663) 
[1 Debug 20:21:03.169] Audioscrobbler state: disconnected 
[1 Debug 20:21:03.183] Extension service started (AudioscrobblerService, 0,028863) 
[1 Debug 20:21:03.184] Extension service started (DapService, 0,00088) 
[1 Debug 20:21:03.187] Extension service started (AmazonMp3DownloaderService, 0,002009) 
[1 Debug 20:21:03.241] Extension service started (AudioCdService, 0,050439) 
[1 Debug 20:21:03.246] Extension service started (DaapService, 0,000911) 
[1 Debug 20:21:03.287] Extension service started (GStreamerCoreService, 0,039025) 
[1 Debug 20:21:03.295] Extension service started (MprisService, 0,007826) 
[1 Debug 20:21:03.302] Extension service started (SoundMenuService, 0,007126) 
[1 Debug 20:21:03.332] Extension service started (EmusicService, 0,029692) 
[1 Info  20:21:03.336] Updating web proxy from GConf 
[1 Debug 20:21:03.350] Direct connection, no proxy in use 
[1 Debug 20:21:03.363] Extension service started (GnomeService, 0,031026) 
[1 Debug 20:21:03.373] Extension service started (BpmService, 0,01025) 
[1 Warn  20:21:03.385] Caught an exception - System.ApplicationException: No support GNOME Settings Daemon could be reached. (in `Banshee.MultimediaKeys') 
  at Banshee.MultimediaKeys.MultimediaKeysService.Banshee.ServiceStack.IExtensionService.Initialize () [0x00000] in <filename unknown>:0 
  at Banshee.ServiceStack.ServiceManager.StartExtension (Mono.Addins.TypeExtensionNode node) [0x00000] in <filename unknown>:0 
[1 Warn  20:21:03.385] Extension `Banshee.MultimediaKeys.MultimediaKeysService' not started: No support GNOME Settings Daemon could be reached. 
[1 Debug 20:21:03.388] Extension service started (CoverArtService, 0,002195) 
[1 Debug 20:21:03.389] Extension service started (PodcastService, 0,001534) 
[1 Warn  20:21:03.392] Caught an exception - System.ApplicationException: No support GNOME Settings Daemon could be reached. (in `Banshee.MultimediaKeys') 
  at Banshee.MultimediaKeys.MultimediaKeysService.Banshee.ServiceStack.IExtensionService.Initialize () [0x00000] in <filename unknown>:0 
  at Banshee.ServiceStack.ServiceManager.StartExtension (Mono.Addins.TypeExtensionNode node) [0x00000] in <filename unknown>:0 
[1 Warn  20:21:03.392] Extension `Banshee.MultimediaKeys.MultimediaKeysService' not started: No support GNOME Settings Daemon could be reached. 
[1 Info  20:21:03.392] All services are started 1,218407 
[1 Debug 20:21:03.679] Creating Pango.Layout, configuring Cairo.Context 
[1 Debug 20:21:03.784] Extension source loaded: Last.fm 
[1 Debug 20:21:03.873] Registering remote object /org/bansheeproject/Banshee/SourceManager/PlayQueue (Banshee.PlayQueue.PlayQueueSource) on org.bansheeproject.Banshee 
[1 Debug 20:21:03.874] Extension source loaded: Kolejka odtwarzania 
[1 Debug 20:21:03.880] Extension source loaded: Teraz odtwarzany 
[1 Debug 20:21:03.915] Extension source loaded: Audiobooki 
[1 Debug 20:21:03.936] Extension source loaded: Radio 
[1 Debug 20:21:03.951] Extension source loaded: Internet Archive 
[1 Debug 20:21:03.975] Extension source loaded: Kolejka systemu plików 
[1 Info  20:21:03.981] AmazonMP3 store redirect URL: https://one.ubuntu.com/music/store/amz/
[1 Debug 20:21:03.984] Extension source loaded: Sklep Amazon MP3 
[1 Debug 20:21:03.990] Extension source loaded: Przewodnik Miro 
[1 Debug 20:21:04.005] Starting GTK main loop 
[1 Debug 20:21:04.205] Creating Pango.Layout, configuring Cairo.Context 
[1 Debug 20:21:04.242] Creating Pango.Layout, configuring Cairo.Context 
[1 Info  20:21:04.339] nereid Client Started 
[1 Debug 20:21:04.341] Delayed Initializating Banshee.MediaEngine.PlayerEngineService 
Cannot connect to server socket err = Nie ma takiego pliku ani katalogu 
Cannot connect to server socket 
jack server is not running or cannot be started 
[1 Debug 20:21:04.358] (libbanshee:player) Audiosink has volume: NO 
[1 Debug 20:21:04.372] (libbanshee:player) Using system (gst-plugins-good) equalizer element 
[1 Debug 20:21:04.427] Player state change: NotReady -> Ready 
[1 Debug 20:21:04.431] Loaded equalizer presets: 0,000181 
[1 Debug 20:21:04.445] Selected equalizer: Rock 
[1 Debug 20:21:04.450] Player state change: Ready -> Idle 
[1 Debug 20:21:04.454] (libbanshee:player) Disabled ReplayGain 
[1 Info  20:21:04.456] GStreamer version 0.10.35.0, gapless: True, replaygain: False 
[1 Debug 20:21:04.461] Delayed Initializating Banshee.Dap.DapService 
[1 Debug 20:21:04.475] Dap support extension loaded: Banshee.Dap.Mtp 
[1 Debug 20:21:04.477] Dap support extension loaded: Banshee.Dap.MassStorage 
[1 Debug 20:21:04.478] Dap support extension loaded: Banshee.Dap.AppleDevice 
[1 Debug 20:21:04.482] Delayed Initializating Banshee.Daap.DaapService 
[1 Debug 20:21:04.489] Delayed Initializating Banshee.Podcasting.PodcastService 
[1 Debug 20:21:05.572] Finished - Startup Job 
[13 Debug 20:21:05.998] DAAP Proxy listening for connections on port 808
```
If clik under "play" then  nothing happens, lack audio
I NEED THIS PLAYER because him can save it(link) in metadata
Maybe exist other  the audio player  with same a function?

---

