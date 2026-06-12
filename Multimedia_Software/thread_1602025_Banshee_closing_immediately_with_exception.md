---
title: "Banshee closing immediately with exception"
date: 2010-10-20
forum: Multimedia Software
---

### Post by falcojr on 2010-10-20
When I try to open Banshee, I can see the GUI for about half a second, then it closes with "Unhandled Exception: GLib.GException: Can't recursively copy directory".

I'm running Ubuntu 10.10 amd64, and had an old version of banshee installed from a few releases back (don't remember which).  I deleted the banshee-1 folder in my ~/.config directly, as well as uninstalled and reinstalled with no luck.  Other Mono apps (such as gnome-do) work fine.

Here is the full output of "banshee --debug":

** Running Mono with --debug   **
[1 Info  21:09:19.692] Running Banshee 1.7.6: [Ubuntu maverick (development branch) (linux-gnu, x86_64) @ 2010-09-18 21:00:29 UTC]
[1 Debug 21:09:19.709] Initializing GTK
[1 Debug 21:09:20.702] Post-Initializing GTK
[1 Debug 21:09:20.713] Configuration client extension loaded (Banshee.GnomeBackend.GConfConfigurationClient)
[1 Debug 21:09:20.719] Using default gconf-base-key
[1 Debug 21:09:20.740] Bus.Session.RequestName ('org.bansheeproject.Banshee') replied with PrimaryOwner
[1 Debug 21:09:20.789] Core service started (DBusServiceManager, 0.00078)
[1 Debug 21:09:20.791] Registering remote object /org/bansheeproject/Banshee/DBusCommandService (Banshee.ServiceStack.DBusCommandService) on org.bansheeproject.Banshee
[1 Debug 21:09:20.797] Core service started (DBusCommandService, 0.007548)
[1 Debug 21:09:20.842] Opened SQLite (version 3.7.2) connection to /home/james/.config/banshee-1/banshee.db
[1 Debug 21:09:20.842] Core service started (DbConnection, 0.04516)
[1 Debug 21:09:20.844] Database version 43 is up to date
[1 Debug 21:09:20.858] Core service started (PreferenceService, 0.006401)
[1 Debug 21:09:20.859] Registering remote object /org/bansheeproject/Banshee/SourceManager (Banshee.Sources.SourceManager) on org.bansheeproject.Banshee
[1 Debug 21:09:20.859] Core service started (SourceManager, 0.000398)
[1 Debug 21:09:20.864] Core service started (MediaProfileManager, 0.000126)
[1 Debug 21:09:20.865] Registering remote object /org/bansheeproject/Banshee/PlayerEngine (Banshee.MediaEngine.PlayerEngineService) on org.bansheeproject.Banshee
[1 Debug 21:09:20.867] Core service started (PlayerEngine, 0.002739)
[1 Debug 21:09:20.877] Registering remote object /org/bansheeproject/Banshee/PlaybackController (Banshee.PlaybackController.PlaybackControllerService) on org.bansheeproject.Banshee
[1 Debug 21:09:20.877] Core service started (PlaybackController, 0.001827)
[1 Debug 21:09:20.882] Starting - Startup Job
[1 Debug 21:09:20.883] Core service started (JobScheduler, 0.005413)
[1 Debug 21:09:20.894] IO provider extension loaded (Banshee.IO.Gio.Provider)
[1 Debug 21:09:20.917] Loaded HardwareManager backend: Banshee.Hardware.Gio
[1 Debug 21:09:20.918] Core service started (HardwareManager, 0.035121)
[1 Debug 21:09:20.919] Bus.Session.RequestName ('org.bansheeproject.CollectionIndexer') replied with PrimaryOwner
[1 Debug 21:09:20.920] Registering remote object /org/bansheeproject/Banshee/CollectionIndexerService (Banshee.Collection.Indexer.CollectionIndexerService) on org.bansheeproject.CollectionIndexer
[1 Debug 21:09:20.921] Core service started (CollectionIndexerService, 0.002954)
[1 Debug 21:09:20.922] Core service started (SaveTrackMetadataService, 0.00098)
[1 Debug 21:09:20.928] Adding icon theme search path: /usr/share/banshee-1/icons
[1 Debug 21:09:20.929] Core service started (GtkElementsService, 0.006696)
[1 Debug 21:09:20.930] Core service started (InterfaceActionService, 0.000948)
[1 Debug 21:09:20.999] Extension actions loaded: MetadataFixActions
[1 Debug 21:09:20.999] Registering remote object /org/bansheeproject/Banshee/GlobalUIActions (Banshee.Gui.GlobalActions) on org.bansheeproject.Banshee
[1 Debug 21:09:21.000] Album artwork path set to /home/james/.cache/media-art
[1 Warn  21:09:21.025] Could not migrate album artwork cache directory - System.IO.DirectoryNotFoundException: Directory 'file:/home/james/.cache/album-art/34' not found. (in `mscorlib')
  at System.IO.Directory.GetFileSystemEntries (System.String path, System.String searchPattern, FileAttributes mask, FileAttributes attrs) [0x00000] in <filename unknown>:0 
  at System.IO.Directory.GetDirectories (System.String path, System.String searchPattern) [0x00000] in <filename unknown>:0 
  at System.IO.Directory.GetDirectories (System.String path) [0x00000] in <filename unknown>:0 
  at System.IO.Directory.RecursiveDelete (System.String path) [0x00000] in <filename unknown>:0 
  at System.IO.Directory.Delete (System.String path, Boolean recursive) [0x00000] in <filename unknown>:0 
  at Banshee.IO.Gio.Directory.Delete (System.String directory, File dir, Boolean recursive) [0x00047] in /build/buildd/banshee-1.7.6/src/Backends/Banshee.Gio/Banshee.IO.Gio/Directory.cs:76 
  at Banshee.IO.Gio.Directory.Delete (System.String directory, Boolean recursive) [0x00000] in /build/buildd/banshee-1.7.6/src/Backends/Banshee.Gio/Banshee.IO.Gio/Directory.cs:57 
  at Banshee.IO.Directory.Delete (System.String directory, Boolean recursive) [0x00000] in /build/buildd/banshee-1.7.6/src/Core/Banshee.Core/Banshee.IO/Directory.cs:60 
  at Banshee.Collection.Gui.ArtworkManager.MigrateCacheDir () [0x000cf] in /build/buildd/banshee-1.7.6/src/Core/Banshee.ThickClient/Banshee.Collection.Gui/ArtworkManager.cs:343 
  at Banshee.Collection.Gui.ArtworkManager..ctor () [0x00057] in /build/buildd/banshee-1.7.6/src/Core/Banshee.ThickClient/Banshee.Collection.Gui/ArtworkManager.cs:78 
[1 Debug 21:09:21.025] Core service started (ArtworkManager, 0.025663)
[1 Debug 21:09:21.026] Core service started (BookmarksService, 7.4E-05)
[1 Debug 21:09:21.151] Adding context page lastfm-recommendations
[1 Debug 21:09:21.165] Adding context page wikipedia
[1 Debug 21:09:21.344] Constructed Nereid interface: 0.302013
[1 Debug 21:09:21.389] Creating new surface cache for 90px images, capped at 1.11 MiB (36 items)
[1 Debug 21:09:21.428] Registering remote object /org/bansheeproject/Banshee/ClientWindow (Nereid.PlayerInterface) on org.bansheeproject.Banshee
[1 Debug 21:09:21.428] Core service started (NereidPlayerInterface, 0.402253)
[1 Debug 21:09:21.444] Extension service started (GStreamerCoreService, 0.01545)
[1 Debug 21:09:21.448] Extension service started (BpmService, 0.004616)
[1 Debug 21:09:21.451] Using GNOME 2.22 API for Multimedia Keys
[1 Debug 21:09:21.451] Extension service started (MultimediaKeysService, 0.002697)
[1 Debug 21:09:21.452] Extension service started (LibraryWatcherService, 0.000883)
[1 Debug 21:09:21.525] Extension service started (NotificationAreaService, 0.072546)
[1 Debug 21:09:21.526] Extension service started (PodcastService, 0.00171)
[1 Debug 21:09:21.527] Extension service started (DapService, 0.000653)
[1 Debug 21:09:21.537] Core service started (Network, 0.002952)
[1 Debug 21:09:21.537] Audioscrobbler state: connected
[1 Debug 21:09:21.538] Extension service started (AudioscrobblerService, 0.011258)
[1 Debug 21:09:21.541] Extension service started (LastfmStreamingService, 0.002211)
[1 Debug 21:09:21.541] Extension service started (DaapService, 0.000597)
[1 Info  21:09:21.543] Updating web proxy from GConf
[1 Debug 21:09:21.546] Direct connection, no proxy in use
[1 Debug 21:09:21.558] Extension service started (GnomeService, 0.016383)
[1 Debug 21:09:21.559] Extension service started (AmazonMp3DownloaderService, 0.001337)
[1 Info  21:09:21.560] Netbook extension initialized with hidden panel
[1 Debug 21:09:21.563] Extension service started (MeeGoService, 0.003926)
[1 Debug 21:09:21.564] Extension service started (CoverArtService, 0.001202)
[1 Debug 21:09:21.579] Extension service started (AudioCdService, 0.014334)
[1 Info  21:09:21.579] All services are started 0.838523
[1 Debug 21:09:21.811] Registering remote object /org/bansheeproject/Banshee/SourceManager/PlayQueue (Banshee.PlayQueue.PlayQueueSource) on org.bansheeproject.Banshee
[1 Debug 21:09:21.812] Extension source loaded: Play Queue
[1 Debug 21:09:21.830] Extension source loaded: Last.fm
[1 Debug 21:09:21.834] Extension source loaded: Now Playing
[1 Debug 21:09:21.841] Extension source loaded: Radio
[1 Debug 21:09:21.846] Extension source loaded: Amazon MP3 Store
[1 Debug 21:09:21.854] Extension source loaded: File System Queue
[1 Debug 21:09:21.858] Extension source loaded: Miro Guide
[1 Debug 21:09:21.870] Extension source loaded: Audiobooks, etc
[1 Debug 21:09:21.877] Extension source loaded: Internet Archive
[1 Debug 21:09:21.880] Starting GTK main loop
[1 Debug 21:09:21.921] Growing surface cache for 90px images to 1.61 MiB (52 items)
[1 Debug 21:09:21.963] Creating Pango.Layout, configuring Cairo.Context
[1 Debug 21:09:21.998] Creating Pango.Layout, configuring Cairo.Context
[1 Debug 21:09:22.006] Creating Pango.Layout, configuring Cairo.Context
[1 Info  21:09:22.166] nereid Client Started
[1 Debug 21:09:22.168] Delayed Initializating Banshee.MediaEngine.PlayerEngineService
[1 Debug 21:09:22.172] (libbanshee:player) Stream volume supported: YES
[1 Debug 21:09:22.174] (libbanshee:player) Audiosink has volume: NO
[1 Debug 21:09:22.175] (libbanshee:player) Using system (gst-plugins-good) equalizer element
[1 Debug 21:09:22.205] Player state change: NotReady -> Ready
[1 Debug 21:09:22.208] Loaded equalizer presets: 0.000111
[1 Debug 21:09:22.210] Selected equalizer: Rock
[1 Debug 21:09:22.212] Player state change: Ready -> Idle
[1 Debug 21:09:22.214] (libbanshee:player) Disabled ReplayGain
[1 Debug 21:09:22.218] Delayed Initializating Banshee.LibraryWatcher.LibraryWatcherService
[1 Debug 21:09:22.222] Core service started (LibraryImportManager, 0.002937)
[1 Debug 21:09:22.448] Started LibraryWatcher for Music (/media/SimpleDrive/media/music/)
[1 Debug 21:09:22.448] Will not watch library Videos because its folder doesn't exist: /home/james/Videos/
[1 Debug 21:09:22.451] Starting
[1 Debug 21:09:22.462] Starting
[1 Debug 21:09:22.465] Delayed Initializating Banshee.Podcasting.PodcastService
[2 Debug 21:09:22.471] Finished
[3 Warn  21:09:22.474] Caught an exception - GLib.GException: Too many levels of symbolic links (in `gio-sharp')
  at GLib.FileAdapter.EnumerateChildren (System.String attributes, FileQueryInfoFlags flags, GLib.Cancellable cancellable) [0x00000] in <filename unknown>:0 
  at Banshee.IO.Gio.Directory+<GetFiles>c__Iterator6.MoveNext () [0x00023] in /build/buildd/banshee-1.7.6/src/Backends/Banshee.Gio/Banshee.IO.Gio/Directory.cs:120 
  at Banshee.IO.DirectoryScannerPipelineElement.ScanForFiles (System.String source, Boolean skip_hidden) [0x000c5] in /build/buildd/banshee-1.7.6/src/Core/Banshee.Core/Banshee.IO/DirectoryScannerPipelineElement.cs:88 
[1 Debug 21:09:22.519] Delayed Initializating Banshee.Dap.DapService
[1 Debug 21:09:22.523] Dap support extension loaded: Banshee.Dap.MassStorage
[1 Debug 21:09:22.524] Dap support extension loaded: Banshee.Dap.AppleDevice
[1 Debug 21:09:22.524] Dap support extension loaded: Banshee.Dap.Karma
[1 Debug 21:09:22.525] Dap support extension loaded: Banshee.Dap.Mtp
[1 Debug 21:09:22.528] Delayed Initializating Banshee.Daap.DaapService

Unhandled Exception: GLib.GException: Can't recursively copy directory
  at GLib.FileAdapter.Move (File destination, FileCopyFlags flags, GLib.Cancellable cancellable, GLib.FileProgressCallback progress_callback) [0x00000] in <filename unknown>:0 
  at Banshee.IO.Gio.Directory.Move (Hyena.SafeUri from, Hyena.SafeUri to) [0x0000c] in /build/buildd/banshee-1.7.6/src/Backends/Banshee.Gio/Banshee.IO.Gio/Directory.cs:162 
  at Banshee.IO.Directory.Move (Hyena.SafeUri from, Hyena.SafeUri to) [0x00000] in /build/buildd/banshee-1.7.6/src/Core/Banshee.Core/Banshee.IO/Directory.cs:50 
  at Banshee.Podcasting.PodcastService.<DelayedInitialize>m__9 () [0x0010c] in /build/buildd/banshee-1.7.6/src/Extensions/Banshee.Podcasting/Banshee.Podcasting/PodcastService.cs:257

---

### Post by directhex on 2010-10-21
Looks like it's falling over on an infinite recursive symlink. I'd report a bug about it on the Banshee bugzilla.

---

