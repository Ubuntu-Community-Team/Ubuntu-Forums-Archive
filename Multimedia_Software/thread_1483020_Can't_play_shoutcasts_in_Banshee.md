---
title: "Can't play shoutcasts in Banshee"
date: 2010-05-14
forum: Multimedia Software
---

### Post by amksep on 2010-05-14
I just added the liveradio extension to banshee which contains both magnatune and shoutcast support.

Magnatune works perfect..but for shoutcasts i can see all stations lists and load them ..but when i click play it stucks in contacting status .. it suddenly worked only one time and then it does not work. Any help?

---

### Post by boombox1387 on 2010-05-26
I might not be of much help since I'm not using that extension, but in general you might get useful information by running Banshee from a terminal with the 'debug' option:

```
banshee --debug
```

Be sure to watch the console for any useful warnings or errors when you try to play shoutcast stations.  If you post the output here, I'll take a look at it and see if anything jumps out at me.  You might also have more luck asking about this on [the Banshee mailing list]("http://mail.gnome.org/mailman/listinfo/banshee-list") or by [filing a bug]("http://banshee-project.org/contribute/file-bugs/") in Banshee's bug tracker.

---

### Post by amksep on 2010-05-26
Thank you for the reply.
Here is the output of running banshee --debug


** Running Mono with --debug   **
[1 Info  06:34:08.590] Running Banshee 1.6.0: [Ubuntu lucid (development branch) (linux-gnu, i486) @ 2010-04-04 14:18:33 UTC]
[1 Debug 06:34:10.321] Initializing GTK
[1 Debug 06:34:10.386] Configuration client extension loaded (Banshee.GnomeBackend.GConfConfigurationClient)
[1 Debug 06:34:10.398] Using default gconf-base-key
[1 Debug 06:34:10.501] Bus.Session.RequestName ('org.bansheeproject.Banshee') replied with PrimaryOwner
[1 Debug 06:34:10.514] Core service started (DBusServiceManager, 0.001859s)
[1 Debug 06:34:10.518] Registering remote object /org/bansheeproject/Banshee/DBusCommandService (Banshee.ServiceStack.DBusCommandService) on org.bansheeproject.Banshee
[1 Debug 06:34:10.537] Core service started (DBusCommandService, 0.022045s)
[1 Debug 06:34:10.677] Opened SQLite connection to /home/amk/.config/banshee-1/banshee.db
[1 Debug 06:34:10.678] Core service started (DbConnection, 0.140742s)
[1 Debug 06:34:10.684] Database version 41 is up to date
[1 Debug 06:34:10.732] Core service started (PreferenceService, 0.019749s)
[1 Debug 06:34:10.733] Registering remote object /org/bansheeproject/Banshee/SourceManager (Banshee.Sources.SourceManager) on org.bansheeproject.Banshee
[1 Debug 06:34:10.734] Core service started (SourceManager, 0.001203s)
[1 Debug 06:34:10.734] Core service started (MediaProfileManager, 0.000333s)
[1 Debug 06:34:10.739] Registering remote object /org/bansheeproject/Banshee/PlayerEngine (Banshee.MediaEngine.PlayerEngineService) on org.bansheeproject.Banshee
[1 Debug 06:34:10.741] Core service started (PlayerEngine, 0.006574s)
[1 Debug 06:34:10.771] IO provider extension loaded (Banshee.IO.Unix.Provider)
[1 Debug 06:34:10.792] Core service started (TranscoderService, 0.027286s)
[1 Debug 06:34:10.795] Registering remote object /org/bansheeproject/Banshee/PlaybackController (Banshee.PlaybackController.PlaybackControllerService) on org.bansheeproject.Banshee
[1 Debug 06:34:10.796] Core service started (PlaybackController, 0.004177s)
[1 Debug 06:34:10.797] Core service started (ImportSourceManager, 0.000864s)
[1 Debug 06:34:10.806] Core service started (LibraryImportManager, 0.009225s)
[1 Debug 06:34:10.808] Core service started (JobScheduler, 0.001488s)
[1 Debug 06:34:10.826] Core service started (HardwareManager, 0.018048s)
[1 Debug 06:34:10.831] Bus.Session.RequestName ('org.bansheeproject.CollectionIndexer') replied with PrimaryOwner
[1 Debug 06:34:10.833] Registering remote object /org/bansheeproject/Banshee/CollectionIndexerService (Banshee.Collection.Indexer.CollectionIndexerService) on org.bansheeproject.CollectionIndexer
[1 Debug 06:34:10.834] Core service started (CollectionIndexerService, 0.007848s)
[1 Debug 06:34:10.837] Core service started (SaveMetadataService, 0.002342s)
[1 Debug 06:34:10.869] Adding icon theme search path: /usr/share/banshee-1/icons
[1 Debug 06:34:10.870] Core service started (GtkElementsService, 0.033423s)
[1 Debug 06:34:10.873] Core service started (InterfaceActionService, 0.002293s)
[1 Debug 06:34:11.002] Album artwork path set to /home/amk/.cache/media-art
[1 Debug 06:34:11.020] Core service started (ArtworkManager, 0.018997s)
[1 Debug 06:34:11.431] Adding context page lastfm-recommendations
[1 Debug 06:34:11.462] Adding context page wikipedia
[1 Debug 06:34:11.862] Constructed Nereid interface: 0.797425s
[1 Debug 06:34:11.968] Creating new surface cache for 90px images, capped at 1.24 MiB (40 items)
[1 Debug 06:34:12.129] Registering remote object /org/bansheeproject/Banshee/ClientWindow (Nereid.PlayerInterface) on org.bansheeproject.Banshee
[1 Debug 06:34:12.129] Core service started (NereidPlayerInterface, 1.109316s)
[1 Debug 06:34:12.156] Extension service started (GStreamerCoreService, 0.025767s)
[1 Debug 06:34:12.164] Extension service started (BpmService, 0.007586s)
[1 Debug 06:34:12.168] Using GNOME 2.22 API for Multimedia Keys
[1 Debug 06:34:12.168] Extension service started (MultimediaKeysService, 0.004087s)
[1 Debug 06:34:12.171] Extension service started (PodcastService, 0.003189s)
[1 Debug 06:34:12.172] Extension service started (DapService, 0.001099s)
[1 Debug 06:34:12.173] Extension service started (DaapService, 0.000964s)
[1 Debug 06:34:12.183] Extension service started (GnomeService, 0.005953s)
[1 Debug 06:34:12.208] Core service started (Network, 0.007839s)
[1 Debug 06:34:12.209] Audioscrobbler state: connected
[1 Debug 06:34:12.211] Extension service started (AudioscrobblerService, 0.028271s)
[1 Debug 06:34:12.231] Extension service started (NotificationAreaService, 0.01979s)
[1 Debug 06:34:12.253] Extension service started (BookmarksService, 0.021415s)
[1 Debug 06:34:12.256] Extension service started (CoverArtService, 0.002991s)
[1 Debug 06:34:12.259] Extension service started (MiniModeService, 0.003598s)
[1 Debug 06:34:12.329] Extension service started (AudioCdService, 0.070018s)
[1 Info  06:34:12.335] All services are started 1.833375s
[1 Debug 06:34:13.714] Registering remote object /org/bansheeproject/Banshee/SourceManager/PlayQueue (Banshee.PlayQueue.PlayQueueSource) on org.bansheeproject.Banshee
[1 Debug 06:34:13.832] [LiveRadioSource]<Constructor> START
[1 Debug 06:34:13.856] [LiveRadioSource]<Constructor> found plugin: live365.com, enabled: False
[1 Debug 06:34:13.856] [LiveRadioSource]<Constructor> found plugin: magnatune.com, enabled: True
[1 Debug 06:34:13.856] [LiveRadioSource]<Constructor> found plugin: SHOUTcast.com, enabled: True
[1 Debug 06:34:13.856] [LiveRadioSource]<Constructor> found plugin: xiph.org, enabled: False
[1 Debug 06:34:14.238] [LiveRadioSource]<Constructor> END
[1 Debug 06:34:14.267] Starting GTK main loop
[1 Debug 06:34:14.628] Creating Pango.Layout, configuring Cairo.Context
[1 Debug 06:34:14.670] Creating Pango.Layout, configuring Cairo.Context
[1 Debug 06:34:14.761] Creating Pango.Layout, configuring Cairo.Context
[1 Info  06:34:15.005] nereid Client Started
[1 Debug 06:34:15.007] Delayed Initializating Banshee.MediaEngine.PlayerEngineService
[1 Debug 06:34:15.025] (libbanshee:player) Using system (gst-plugins-good) equalizer element
[1 Debug 06:34:15.165] Player state change: NotReady -> Ready
[1 Debug 06:34:15.173] Loaded equalizer presets: 0.000102s
[1 Debug 06:34:15.179] Selected equalizer: Rock
[1 Debug 06:34:15.194] Player state change: Ready -> Idle
[1 Debug 06:34:15.205] (libbanshee:player) Disabled ReplayGain
[1 Debug 06:34:15.207] Delayed Initializating Banshee.Podcasting.PodcastService
[1 Debug 06:34:15.329] Delayed Initializating Banshee.Dap.DapService
[2 Debug 06:34:15.339] Refreshing any podcasts that haven't been updated in over an hour
[1 Debug 06:34:15.342] Dap support extension loaded: Banshee.Dap.MassStorage
[1 Debug 06:34:15.344] Dap support extension loaded: Banshee.Dap.Mtp
[1 Debug 06:34:15.645] Delayed Initializating Banshee.Daap.DaapService
[3 Debug 06:34:15.827] DAAP Proxy listening for connections on port 8089
[4 Debug 06:34:15.934] [MagnatunePlugin] <ParseGenres> 78 genres found
[1 Debug 06:34:17.002] Creating Pango.Layout, configuring Cairo.Context
[1 Debug 06:34:17.010] Creating Pango.Layout, configuring Cairo.Context
[5 Debug 06:34:18.362] [ShoutCastPlugin] <ParseGenres> 458 genres found
[1 Debug 06:34:20.121] Starting
[1 Debug 06:34:20.160] Finished - Adding 1 of 1 to SHOUTcast.com
[1 Debug 06:34:20.168] Finished - Adding 1 of 1 to SHOUTcast.com
[6 Warn  06:34:20.428] Caught an exception - System.Xml.XmlException: 'li' is expected  Line 1001, position 124. (in `System.Xml')
  at Mono.Xml2.XmlTextReader.Expect (System.String expected) [0x00000] 
  at Mono.Xml2.XmlTextReader.ReadEndTag () [0x00000] 
  at Mono.Xml2.XmlTextReader.ReadContent () [0x00000] 
  at Mono.Xml2.XmlTextReader.Read () [0x00000] 
  at System.Xml.XmlTextReader.Read () [0x00000] 
  at System.Xml.XmlDocument.ReadNodeCore (System.Xml.XmlReader reader) [0x00000] 
  at System.Xml.XmlDocument.ReadNodeCore (System.Xml.XmlReader reader) [0x00000] 
  at System.Xml.XmlDocument.ReadNodeCore (System.Xml.XmlReader reader) [0x00000] 
  at System.Xml.XmlDocument.ReadNodeCore (System.Xml.XmlReader reader) [0x00000] 
  at System.Xml.XmlDocument.ReadNodeCore (System.Xml.XmlReader reader) [0x00000] 
  at System.Xml.XmlDocument.ReadNodeCore (System.Xml.XmlReader reader) [0x00000] 
  at System.Xml.XmlDocument.ReadNodeCore (System.Xml.XmlReader reader) [0x00000] 
  at System.Xml.XmlDocument.ReadNode (System.Xml.XmlReader reader) [0x00000] 
  at System.Xml.XmlDocument.Load (System.Xml.XmlReader xmlReader) [0x00000] 
  at System.Xml.XmlDocument.LoadXml (System.String xml) [0x00000] 
  at Migo.Syndication.RssParser..ctor (System.String url, System.String xml) [0x00026] in /build/buildd/banshee-1.6.0/src/Libraries/Migo/Migo.Syndication/RssParser.cs:52 
[6 Warn  06:34:20.428] Caught an exception - System.FormatException: Invalid XML document. (in `Migo')
  at Migo.Syndication.RssParser..ctor (System.String url, System.String xml) [0x000c0] in /build/buildd/banshee-1.6.0/src/Libraries/Migo/Migo.Syndication/RssParser.cs:76 
  at Migo.Syndication.FeedUpdateTask.OnDownloadDataReceived (System.Object sender, Migo.Net.DownloadStringCompletedEventArgs args) [0x00055] in /build/buildd/banshee-1.6.0/src/Libraries/Migo/Migo.Syndication/FeedUpdateTask.cs:157 
[7 Warn  06:34:20.919] Caught an exception - System.Xml.XmlException: 'li' is expected  Line 861, position 124. (in `System.Xml')
  at Mono.Xml2.XmlTextReader.Expect (System.String expected) [0x00000] 
  at Mono.Xml2.XmlTextReader.ReadEndTag () [0x00000] 
  at Mono.Xml2.XmlTextReader.ReadContent () [0x00000] 
  at Mono.Xml2.XmlTextReader.Read () [0x00000] 
  at System.Xml.XmlTextReader.Read () [0x00000] 
  at System.Xml.XmlDocument.ReadNodeCore (System.Xml.XmlReader reader) [0x00000] 
  at System.Xml.XmlDocument.ReadNodeCore (System.Xml.XmlReader reader) [0x00000] 
  at System.Xml.XmlDocument.ReadNodeCore (System.Xml.XmlReader reader) [0x00000] 
  at System.Xml.XmlDocument.ReadNodeCore (System.Xml.XmlReader reader) [0x00000] 
  at System.Xml.XmlDocument.ReadNodeCore (System.Xml.XmlReader reader) [0x00000] 
  at System.Xml.XmlDocument.ReadNodeCore (System.Xml.XmlReader reader) [0x00000] 
  at System.Xml.XmlDocument.ReadNodeCore (System.Xml.XmlReader reader) [0x00000] 
  at System.Xml.XmlDocument.ReadNode (System.Xml.XmlReader reader) [0x00000] 
  at System.Xml.XmlDocument.Load (System.Xml.XmlReader xmlReader) [0x00000] 
  at System.Xml.XmlDocument.LoadXml (System.String xml) [0x00000] 
  at Migo.Syndication.RssParser..ctor (System.String url, System.String xml) [0x00026] in /build/buildd/banshee-1.6.0/src/Libraries/Migo/Migo.Syndication/RssParser.cs:52 
[7 Warn  06:34:20.920] Caught an exception - System.FormatException: Invalid XML document. (in `Migo')
  at Migo.Syndication.RssParser..ctor (System.String url, System.String xml) [0x000c0] in /build/buildd/banshee-1.6.0/src/Libraries/Migo/Migo.Syndication/RssParser.cs:76 
  at Migo.Syndication.FeedUpdateTask.OnDownloadDataReceived (System.Object sender, Migo.Net.DownloadStringCompletedEventArgs args) [0x00055] in /build/buildd/banshee-1.6.0/src/Libraries/Migo/Migo.Syndication/FeedUpdateTask.cs:157 
[4 Debug 06:34:21.311] [LiveRadioBasePlugin"SHOUTcast.com"]<RaiseRequestResultRetrieved> result contains 36 entries for query African
[4 Debug 06:34:21.314] Starting
[4 Debug 06:34:22.039] Finished - Adding 36 of 36 to SHOUTcast.com
[4 Debug 06:34:22.056] Finished - Adding 36 of 36 to SHOUTcast.com
[8 Warn  06:34:25.614] Caught an exception - System.Xml.XmlException: 'li' is expected  Line 790, position 124. (in `System.Xml')
  at Mono.Xml2.XmlTextReader.Expect (System.String expected) [0x00000] 
  at Mono.Xml2.XmlTextReader.ReadEndTag () [0x00000] 
  at Mono.Xml2.XmlTextReader.ReadContent () [0x00000] 
  at Mono.Xml2.XmlTextReader.Read () [0x00000] 
  at System.Xml.XmlTextReader.Read () [0x00000] 
  at System.Xml.XmlDocument.ReadNodeCore (System.Xml.XmlReader reader) [0x00000] 
  at System.Xml.XmlDocument.ReadNodeCore (System.Xml.XmlReader reader) [0x00000] 
  at System.Xml.XmlDocument.ReadNodeCore (System.Xml.XmlReader reader) [0x00000] 
  at System.Xml.XmlDocument.ReadNodeCore (System.Xml.XmlReader reader) [0x00000] 
  at System.Xml.XmlDocument.ReadNodeCore (System.Xml.XmlReader reader) [0x00000] 
  at System.Xml.XmlDocument.ReadNodeCore (System.Xml.XmlReader reader) [0x00000] 
  at System.Xml.XmlDocument.ReadNodeCore (System.Xml.XmlReader reader) [0x00000] 
  at System.Xml.XmlDocument.ReadNode (System.Xml.XmlReader reader) [0x00000] 
  at System.Xml.XmlDocument.Load (System.Xml.XmlReader xmlReader) [0x00000] 
  at System.Xml.XmlDocument.LoadXml (System.String xml) [0x00000] 
  at Migo.Syndication.RssParser..ctor (System.String url, System.String xml) [0x00026] in /build/buildd/banshee-1.6.0/src/Libraries/Migo/Migo.Syndication/RssParser.cs:52 
[8 Warn  06:34:25.614] Caught an exception - System.FormatException: Invalid XML document. (in `Migo')
  at Migo.Syndication.RssParser..ctor (System.String url, System.String xml) [0x000c0] in /build/buildd/banshee-1.6.0/src/Libraries/Migo/Migo.Syndication/RssParser.cs:76 
  at Migo.Syndication.FeedUpdateTask.OnDownloadDataReceived (System.Object sender, Migo.Net.DownloadStringCompletedEventArgs args) [0x00055] in /build/buildd/banshee-1.6.0/src/Libraries/Migo/Migo.Syndication/FeedUpdateTask.cs:157 
[1 Debug 06:34:27.736] (libbanshee:player) bp_stop: setting state to GST_STATE_NULL
[9 Debug 06:34:28.374] Parsed 0 URIs out of [www.shoutcast.com](www.shoutcast.com) - African Online Radio - [SHOUTcast.com] (on Pablo Lubadika - Tolingana) <00:00:00> [<unknown>]
[1 Debug 06:34:37.802] Service disposed (AudioCdService)
[1 Debug 06:34:37.802] Service disposed (MiniModeService)
[1 Debug 06:34:37.804] Service disposed (CoverArtService)
[1 Debug 06:34:37.805] Service disposed (BookmarksService)
[1 Debug 06:34:37.813] Service disposed (NotificationAreaService)
[1 Debug 06:34:37.817] Service disposed (AudioscrobblerService)
[1 Debug 06:34:37.818] Service disposed (Network)
[1 Debug 06:34:37.818] Service disposed (GnomeService)
[1 Debug 06:34:37.828] Service disposed (DaapService)
[1 Debug 06:34:37.832] Service disposed (DapService)
[1 Debug 06:34:37.860] Service disposed (PodcastService)
[1 Debug 06:34:37.863] Service disposed (MultimediaKeysService)
[1 Debug 06:34:37.864] Service disposed (BpmService)
[1 Debug 06:34:37.864] Service disposed (GStreamerCoreService)
[1 Debug 06:34:37.867] Service disposed (NereidPlayerInterface)
[1 Debug 06:34:37.867] Service disposed (CollectionIndexerService)
[1 Debug 06:34:37.869] Service disposed (HardwareManager)
[1 Debug 06:34:37.871] (libbanshee:player) bp_stop: setting state to GST_STATE_NULL
[1 Debug 06:34:37.872] (libbanshee:player) bp_destroy: disposed player
[1 Debug 06:34:37.872] Service disposed (PlayerEngine)
[1 Debug 06:34:37.903] Service disposed (SourceManager)
[1 Debug 06:34:37.907] Service disposed (DbConnection)

---

### Post by colin-m on 2010-05-29
This problem has already been reported ( [https://bugs.launchpad.net/ubuntu/+source/banshee-community-extensions/+bug/572819](https://bugs.launchpad.net/ubuntu/+source/banshee-community-extensions/+bug/572819) ). It looks as if a fix should be included soon.

---

