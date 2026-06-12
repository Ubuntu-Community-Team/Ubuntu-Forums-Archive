---
title: "Banshee not starting up in Jaunty, no error."
date: 2009-06-05
forum: Multimedia Software
---

### Post by thetallestpaul on 2009-06-05
Two nights ago, I shutdown my computer and booted it back up the next morning. Now Banshee refuses to start properly and things seem to be running generally quite slowly.

When I start banshee it loads the window itself but fails to load anything inside the window, like my library. It uses 50% of the cpu and just sits there. When I run it in the terminal it displays no error, as if it is just taking a really long time to start up, yet it never finishes. When I try to close it it says Banshee is not responding and allows me to force quit.

I have tried uninstalling, reinstalling, restarting, multiple times in different ways. So far nothing.

I have a 3.0 GHz processor, 1 gig of ram and an nvidia6800go video card

---

### Post by -gr00ve- on 2009-06-09
Hi,

i have the same failure on my machine.
I am using 8.04 LTS with:
deb [http://ppa.launchpad.net/banshee-team/ubuntu](http://ppa.launchpad.net/banshee-team/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/banshee-team/ubuntu](http://ppa.launchpad.net/banshee-team/ubuntu) hardy main

banshee --debug

[Info  11:04:44.262] Running Banshee 1.4.3: [Ubuntu 8.04.2 (linux-gnu, i486) @ 2009-04-21 13:13:59 UTC]
[Debug 11:04:45.590] Bus.Session.RequestName ('org.bansheeproject.Banshee') replied with PrimaryOwner
[Debug 11:04:45.602] Core service started (DBusServiceManager, 0,002969s)
[Debug 11:04:45.609] Registering remote object /org/bansheeproject/Banshee/DBusCommandService (Banshee.ServiceStack.DBusCommandService) on org.bansheeproject.Banshee
[Debug 11:04:45.622] Core service started (DBusCommandService, 0,017948s)
[Debug 11:04:45.777] Opened SQLite connection to /home/groove/.config/banshee-1/banshee.db
[Debug 11:04:45.777] Core service started (DbConnection, 0,155509s)
[Debug 11:04:45.789] Database version 22 is up to date
[Debug 11:04:45.812] Core service started (PreferenceService, 0,021749s)
[Debug 11:04:45.814] Registering remote object /org/bansheeproject/Banshee/SourceManager (Banshee.Sources.SourceManager) on org.bansheeproject.Banshee
[Debug 11:04:45.814] Core service started (SourceManager, 0,001805s)
[Debug 11:04:46.135] Core service started (MediaProfileManager, 0,321102s)
[Debug 11:04:46.137] Registering remote object /org/bansheeproject/Banshee/PlayerEngine (Banshee.MediaEngine.PlayerEngineService) on org.bansheeproject.Banshee
[Debug 11:04:46.139] Core service started (PlayerEngine, 0,003402s)
[Debug 11:04:46.146] Configuration client extension loaded (Banshee.GnomeBackend.GConfConfigurationClient)
[Debug 11:04:46.215] IO provider extension loaded (Banshee.IO.Unix.Provider)
[Debug 11:04:46.224] Core service started (TranscoderService, 0,012763s)
[Debug 11:04:46.227] Registering remote object /org/bansheeproject/Banshee/PlaybackController (Banshee.PlaybackController.PlaybackControllerService) on org.bansheeproject.Banshee
[Debug 11:04:46.228] Core service started (PlaybackController, 0,003765s)
[Debug 11:04:46.229] Core service started (ImportSourceManager, 0,000519s)
[Debug 11:04:46.237] Core service started (LibraryImportManager, 0,007966s)
[Debug 11:04:46.238] Core service started (UserJobManager, 0,000732s)
[Debug 11:04:46.258] Core service started (HardwareManager, 0,01969s)
[Debug 11:04:46.260] Bus.Session.RequestName ('org.bansheeproject.CollectionIndexer') replied with PrimaryOwner
[Debug 11:04:46.262] Registering remote object /org/bansheeproject/Banshee/CollectionIndexerService (Banshee.Collection.Indexer.CollectionIndexerService) on org.bansheeproject.CollectionIndexer
[Debug 11:04:46.263] Core service started (CollectionIndexerService, 0,005584s)
[Debug 11:04:46.309] Adding icon theme search path: /usr/share/banshee-1/icons
[Debug 11:04:46.310] Core service started (GtkElementsService, 0,046605s)
[Debug 11:04:46.380] Core service started (InterfaceActionService, 0,070111s)
[Debug 11:04:46.383] Album artwork path set to /home/groove/.cache/album-art
[Debug 11:04:46.384] Core service started (ArtworkManager, 0,0032s)
[Debug 11:04:47.043] Registering remote object /org/bansheeproject/Banshee/ClientWindow (Nereid.PlayerInterface) on org.bansheeproject.Banshee
[Debug 11:04:47.043] Core service started (NereidPlayerInterface, 0,65922s)
[Debug 11:04:47.103] Extension service started (AudioCdService, 0,059371s)
[Debug 11:04:47.105] Extension service started (DaapService, 0,00125s)
[Debug 11:04:47.106] Extension service started (DapService, 0,000562s)
[Debug 11:04:47.121] Extension service started (BookmarksService, 0,014654s)
[Debug 11:04:47.309] Extension service started (NotificationAreaService, 0,188075s)
[Debug 11:04:47.337] Extension service started (LastfmRecommendationService, 0,027749s)
[Debug 11:04:47.365] Core service started (Network, 0,01353s)
[Debug 11:04:47.365] Audioscrobbler state: connected
[Debug 11:04:47.371] Extension service started (AudioscrobblerService, 0,034101s)
[Debug 11:04:47.375] Extension service started (GnomeService, 0,003912s)
[Debug 11:04:47.620] Extension service started (PodcastService, 0,244526s)
[Debug 11:04:47.623] Using GNOME 2.22 API for Multimedia Keys
[Debug 11:04:47.624] Extension service started (MultimediaKeysService, 0,003287s)
[Debug 11:04:47.792] GStreamer pipeline does not run: audioconvert ! xingenc bitrate=128 ! id3v2mux
[Debug 11:04:47.857] GStreamer pipeline does not run: audioconvert ! fluwmaenc bitrate=64000 vbr=false ! fluasfmux
[Debug 11:04:47.857] Extension service started (GStreamerCoreService, 0,23384s)
[Debug 11:04:47.863] (libbanshee:player) Using built-in equalizer element
[Debug 11:04:47.880] Player state change: NotReady -> Ready
[Debug 11:04:47.901] Enabling equalizer preset: New Preset
[Debug 11:04:47.913] Player state change: Ready -> Idle
[Debug 11:04:47.918] (libbanshee:player) Disabled ReplayGain
[Debug 11:04:47.922] Extension service started (CoverArtService, 0,002744s)
[Info  11:04:47.923] All services are started 2,330379s

So anyone knows whats going on ?

---

### Post by PabloTortilla on 2009-07-22
Bump. I am also getting this error, and it pisses me off. I love banshee, but it just doesn't work. It starts, but all that appears is the window, nothing loads in it. Just a grey box.

---

