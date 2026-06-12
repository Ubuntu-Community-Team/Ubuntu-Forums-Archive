---
title: "Banshee Frozen on Startup"
date: 2009-08-02
forum: Multimedia Software
---

### Post by The_Weaver on 2009-08-02
I've been using Banshee 1.4.3 on Mint 6 (Intrepid) for a while without trouble, but today its started to freeze on start-up. I've un-installed and reinstalled without any benefit. Still relatively new to Linux, so not sure where (or if) there are any log files to help diagnosis.

Thanks

---

### Post by The_Weaver on 2009-08-02
Heres the Debug log

[Info  16:34:28.633] Running Banshee 1.4.3: [Ubuntu 8.10 (linux-gnu, i486) @ 2009-04-21 13:16:22 UTC]
[Debug 16:34:30.293] Bus.Session.RequestName ('org.bansheeproject.Banshee') replied with PrimaryOwner
[Debug 16:34:30.304] Core service started (DBusServiceManager, 0.002412s)
[Debug 16:34:30.308] Registering remote object /org/bansheeproject/Banshee/DBusCommandService (Banshee.ServiceStack.DBusCommandService) on org.bansheeproject.Banshee
[Debug 16:34:30.324] Core service started (DBusCommandService, 0.018704s)
[Debug 16:34:30.424] Opened SQLite connection to /home/keith/.config/banshee-1/banshee.db
[Debug 16:34:30.424] Core service started (DbConnection, 0.09985s)
[Debug 16:34:30.443] Database version 22 is up to date
[Debug 16:34:30.489] Core service started (PreferenceService, 0.044283s)
[Debug 16:34:30.491] Registering remote object /org/bansheeproject/Banshee/SourceManager (Banshee.Sources.SourceManager) on org.bansheeproject.Banshee
[Debug 16:34:30.491] Core service started (SourceManager, 0.002019s)
[Debug 16:34:30.735] Core service started (MediaProfileManager, 0.243679s)
[Debug 16:34:30.737] Registering remote object /org/bansheeproject/Banshee/PlayerEngine (Banshee.MediaEngine.PlayerEngineService) on org.bansheeproject.Banshee
[Debug 16:34:30.739] Core service started (PlayerEngine, 0.004273s)
[Debug 16:34:30.747] Configuration client extension loaded (Banshee.GnomeBackend.GConfConfigurationClient)
[Debug 16:34:30.821] IO provider extension loaded (Banshee.IO.Unix.Provider)
[Debug 16:34:30.840] Core service started (TranscoderService, 0.023016s)
[Debug 16:34:30.842] Registering remote object /org/bansheeproject/Banshee/PlaybackController (Banshee.PlaybackController.PlaybackControllerService) on org.bansheeproject.Banshee
[Debug 16:34:30.843] Core service started (PlaybackController, 0.003118s)
[Debug 16:34:30.845] Core service started (ImportSourceManager, 0.002408s)
[Debug 16:34:30.853] Core service started (LibraryImportManager, 0.00753s)
[Debug 16:34:30.854] Core service started (UserJobManager, 0.000873s)
[Debug 16:34:30.877] Core service started (HardwareManager, 0.0234s)
[Debug 16:34:30.881] Bus.Session.RequestName ('org.bansheeproject.CollectionIndexer') replied with PrimaryOwner
[Debug 16:34:30.882] Registering remote object /org/bansheeproject/Banshee/CollectionIndexerService (Banshee.Collection.Indexer.CollectionIndexerService) on org.bansheeproject.CollectionIndexer
[Debug 16:34:30.884] Core service started (CollectionIndexerService, 0.006145s)
[Debug 16:34:30.984] Adding icon theme search path: /usr/share/banshee-1/icons
[Debug 16:34:30.986] Core service started (GtkElementsService, 0.102325s)
[Debug 16:34:31.061] Core service started (InterfaceActionService, 0.074358s)
[Debug 16:34:31.064] Album artwork path set to /home/keith/.cache/album-art
[Debug 16:34:31.064] Core service started (ArtworkManager, 0.002478s)
[Debug 16:34:31.665] Registering remote object /org/bansheeproject/Banshee/ClientWindow (Nereid.PlayerInterface) on org.bansheeproject.Banshee
[Debug 16:34:31.665] Core service started (NereidPlayerInterface, 0.601283s)
[Debug 16:34:31.672] Using GNOME 2.22 API for Multimedia Keys
[Debug 16:34:31.673] Extension service started (MultimediaKeysService, 0.006781s)
[Debug 16:34:31.675] Extension service started (DaapService, 0.001335s)
[Debug 16:34:31.815] GStreamer pipeline does not run: audioconvert ! xingenc bitrate=128 ! id3v2mux
[Debug 16:34:31.914] GStreamer pipeline does not run: audioconvert ! fluwmaenc bitrate=64000 vbr=false ! fluasfmux
[Debug 16:34:31.914] Extension service started (GStreamerCoreService, 0.239739s)
[Debug 16:34:31.942] Player state change: NotReady -> Ready
[Debug 16:34:31.965] Enabling equalizer preset: New Preset
[Debug 16:34:31.979] Player state change: Ready -> Idle
[Debug 16:34:31.988] (libbanshee:player) Enabled ReplayGain
[Debug 16:34:31.988] (libbanshee:player) scaled volume: 1.000000 (ReplayGain) * 0.550000 (User) = 0.550000
[Debug 16:34:31.989] Extension service started (DapService, 0.000748s)
[Debug 16:34:32.239] Extension service started (PodcastService, 0.250344s)
[Debug 16:34:32.259] Extension service started (BookmarksService, 0.019076s)
[Debug 16:34:32.261] Extension service started (CoverArtService, 0.002177s)
[Debug 16:34:32.266] Extension service started (GnomeService, 0.004195s)
[Debug 16:34:32.328] Extension service started (AudioCdService, 0.062036s)
[Debug 16:34:32.512] Extension service started (NotificationAreaService, 0.184141s)
[Debug 16:34:32.548] Extension service started (LastfmRecommendationService, 0.036062s)
[Debug 16:34:32.568] Core service started (Network, 0.004767s)
[Debug 16:34:32.569] Audioscrobbler state: connected
[Debug 16:34:32.571] Extension service started (AudioscrobblerService, 0.022332s)
[Info  16:34:32.572] All services are started 2.277794s

---

### Post by The_Weaver on 2009-08-03
Any suggestions ?

---

### Post by The_Weaver on 2009-08-12
bump

---

