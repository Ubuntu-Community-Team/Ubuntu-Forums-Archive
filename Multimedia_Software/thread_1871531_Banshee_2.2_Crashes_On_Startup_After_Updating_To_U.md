---
title: "Banshee 2.2 Crashes On Startup After Updating To Ubuntu 11.10"
date: 2011-10-29
forum: Multimedia Software
---

### Post by Precipitous on 2011-10-29
Banshee crashes on startup after updating to Ubuntu 11.10. The terminal output from running banshee --debug is:

```
** Running Mono with --debug   **
[1 Info  00:06:07.801] Running Banshee 2.2.0: [Ubuntu oneiric (development branch) (linux-gnu, i686) @ 2011-09-23 04:51:00 UTC]
[1 Debug 00:06:07.947] Initializing GTK
[1 Debug 00:06:09.797] Post-Initializing GTK
[1 Debug 00:06:09.859] Configuration client extension loaded (Banshee.GnomeBackend.GConfConfigurationClient)
[1 Debug 00:06:09.862] Using default gconf-base-key
[1 Debug 00:06:10.039] Bus.Session.RequestName ('org.bansheeproject.Banshee') replied with PrimaryOwner
[1 Debug 00:06:10.158] Core service started (DBusServiceManager, 0.001776)
[1 Debug 00:06:10.161] Registering remote object /org/bansheeproject/Banshee/DBusCommandService (Banshee.ServiceStack.DBusCommandService) on org.bansheeproject.Banshee
[1 Debug 00:06:10.171] Core service started (DBusCommandService, 0.012034)
[1 Debug 00:06:10.505] Opened SQLite (version 3.7.7) connection to /home/gslater/.config/banshee-1/banshee.db
[1 Debug 00:06:10.505] Core service started (DbConnection, 0.33466)
[1 Debug 00:06:10.513] Database version 44 is up to date
[1 Debug 00:06:10.626] Core service started (PreferenceService, 0.032093)
[1 Debug 00:06:10.639] Core service started (Network, 0.012799)
[1 Debug 00:06:10.640] Registering remote object /org/bansheeproject/Banshee/SourceManager (Banshee.Sources.SourceManager) on org.bansheeproject.Banshee
[1 Debug 00:06:10.640] Core service started (SourceManager, 0.001048)
[1 Debug 00:06:10.646] Core service started (MediaProfileManager, 0.000305)
[1 Debug 00:06:10.662] Registering remote object /org/bansheeproject/Banshee/PlayerEngine (Banshee.MediaEngine.PlayerEngineService) on org.bansheeproject.Banshee
[1 Debug 00:06:10.664] Core service started (PlayerEngine, 0.017719)
[1 Debug 00:06:10.737] Registering remote object /org/bansheeproject/Banshee/PlaybackController (Banshee.PlaybackController.PlaybackControllerService) on org.bansheeproject.Banshee
[1 Debug 00:06:10.739] Core service started (PlaybackController, 0.00362)
[1 Debug 00:06:10.745] Starting - Startup Job
[1 Debug 00:06:10.746] Core service started (JobScheduler, 0.00763)
[1 Debug 00:06:10.762] IO provider extension loaded (Banshee.IO.Gio.Provider)
[1 Debug 00:06:10.857] Loaded HardwareManager backend: Banshee.Hardware.Gio
[1 Debug 00:06:10.859] Core service started (HardwareManager, 0.113015)
[1 Debug 00:06:10.866] Bus.Session.RequestName ('org.bansheeproject.CollectionIndexer') replied with PrimaryOwner
[1 Debug 00:06:10.867] Registering remote object /org/bansheeproject/Banshee/CollectionIndexerService (Banshee.Collection.Indexer.CollectionIndexerService) on org.bansheeproject.CollectionIndexer
[1 Debug 00:06:10.869] Core service started (CollectionIndexerService, 0.009472)
[1 Debug 00:06:10.871] Core service started (SaveTrackMetadataService, 0.001929)
[1 Debug 00:06:10.890] Adding icon theme search path: /usr/share/banshee/icons
[1 Debug 00:06:10.891] Core service started (GtkElementsService, 0.0199)
[1 Debug 00:06:10.893] Core service started (InterfaceActionService, 0.001855)
[1 Debug 00:06:11.074] Loaded new mode into  shuffler: mirage_similar
[1 Debug 00:06:11.078] Loaded new mode into  shuffler: lastfm_shuffle_similar_artists
[1 Debug 00:06:11.079] RandomByLastfmUserTopArtists: Initialising List
[1 Debug 00:06:11.079] Loaded new mode into  shuffler: lastfm_shuffle_topartists
[1 Debug 00:06:11.180] Extension actions loaded: MetadataFixActions
[1 Debug 00:06:11.183] Registering remote object /org/bansheeproject/Banshee/GlobalUIActions (Banshee.Gui.GlobalActions) on org.bansheeproject.Banshee
[1 Debug 00:06:11.208] Album artwork path set to /home/gslater/.cache/media-art
[1 Debug 00:06:11.256] Core service started (ArtworkManager, 0.073084)
[1 Debug 00:06:11.257] Core service started (BookmarksService, 0.000293)
[1 Debug 00:06:11.936] Adding context page wikipedia
[1 Debug 00:06:11.996] Adding context page lastfm-recommendations
[1 Debug 00:06:12.150] Adding context page lyrics
[1 Debug 00:06:12.182] Adding context page YouTube
[1 Debug 00:06:12.189] Adding context page karaoke
[1 Debug 00:06:12.685] Constructed Nereid interface: 1.359404
[1 Debug 00:06:12.830] Creating new surface cache for 90px images, capped at 0.74 MiB (24 items)
[1 Debug 00:06:12.907] Registering remote object /org/bansheeproject/Banshee/ClientWindow (Nereid.PlayerInterface) on org.bansheeproject.Banshee
[1 Debug 00:06:12.907] Core service started (NereidPlayerInterface, 1.616062)
[1 Debug 00:06:12.943] Extension service started (BpmService, 0.034162)
[1 Debug 00:06:13.019] Extension service started (AudioCdService, 0.076434)
[1 Debug 00:06:13.033] Extension service started (DapService, 0.013251)
[1 Debug 00:06:13.085] Zeitgeist client created
[1 Debug 00:06:13.145] Extension service started (ZeitgeistService, 0.111762)
[1 Debug 00:06:13.229] Extension service started (EmusicService, 0.08418)
[1 Debug 00:06:13.249] Extension service started (MprisService, 0.018948)
[1 Debug 00:06:13.256] Extension service started (AmazonMp3DownloaderService, 0.005815)
[1 Debug 00:06:13.262] Extension service started (PodcastService, 0.005963)
[1 Debug 00:06:13.279] Extension service started (LastfmFingerprintService, 0.016884)
[1 Debug 00:06:13.339] Extension service started (SoundMenuService, 0.059867)
[1 Debug 00:06:13.362] Using GNOME 2.22 API for Multimedia Keys
[1 Debug 00:06:13.362] Extension service started (MultimediaKeysService, 0.02247)
[1 Debug 00:06:14.100] Extension service started (ClutterFlowService, 0.738348)
[1 Debug 00:06:14.193] [RadioStationFetcherService] <RadioStationFetcherService> Constructor START
[1 Debug 00:06:14.193] [RadioStationFetcherService] <RadioStationFetcherService> Constructor END
[1 Debug 00:06:14.194] [RadioStationFetcherService] <Initialize> START
[1 Debug 00:06:14.195] [RadioStationFetcherService] <Initialize> END
[1 Debug 00:06:14.195] Extension service started (RadioStationFetcherService, 0.094649)
[1 Debug 00:06:14.202] Extension service started (MiniModeService, 0.006664)
[1 Debug 00:06:14.282] Audioscrobbler state: connected
[1 Debug 00:06:14.285] Extension service started (AudioscrobblerService, 0.082946)
[1 Debug 00:06:14.290] Extension service started (LastfmStreamingService, 0.004378)
[1 Debug 00:06:14.290] Extension service started (MirageService, 0.000417)
[1 Debug 00:06:14.292] BansheeAwn. Starting nereid
[1 Warn  00:06:14.312] BansheeAwn - Failed loading Awn Extension.  - System.Exception: org.freedesktop.DBus.Error.ServiceUnknown: The name com.google.code.Awn was not provided by any .service files (in `DBus.Proxies')
  at Banshee.Awn.IAvantWindowNavigatorProxy.UnsetTaskIconByName (System.String TaskName) [0x00000] in <filename unknown>:0 
  at Banshee.Awn.AwnService.Banshee.ServiceStack.IExtensionService.Initialize () [0x00000] in <filename unknown>:0 
[1 Debug 00:06:14.313] Extension service started (Avant Window Navigator, 0.022437)
[1 Debug 00:06:14.315] Extension service started (DaapService, 0.001865)
[1 Info  00:06:14.321] Updating web proxy from GConf
[1 Debug 00:06:14.330] Direct connection, no proxy in use
[1 Debug 00:06:14.348] Extension service started (GnomeService, 0.032935)
[1 Debug 00:06:14.351] Extension service started (CoverArtService, 0.003741)
[1 Debug 00:06:14.410] Extension service started (OpenVPService, 0.058552)
[1 Debug 00:06:14.910] Extension service started (LyricsService, 0.499257)
[1 Debug 00:06:15.627] Extension service started (GStreamerCoreService, 0.717713)
[1 Debug 00:06:15.630] Initializing Alarm Plugin
[8 Debug 00:06:15.631] Alarm thread started
[1 Debug 00:06:15.633] Extension service started (AlarmClockService, 0.004818)
[1 Debug 00:06:15.668] Extension service started (StreamrecorderService, 0.035218)
[8 Debug 00:06:15.678] Time until alarm is 04:38:44.3675930
[1 Debug 00:06:15.679] Extension service started (LibraryWatcherService, 0.009836)
[1 Debug 00:06:15.682] Extension service started (AlbumArtWriterService, 0.003117)
[1 Debug 00:06:15.689] [Karaoke] GstPlugin audiokaraoke found
[1 Debug 00:06:15.692] Extension service started (KaraokeService, 0.010356)
[1 Debug 00:06:15.706] Extension service started (TelepathyService, 0.012975)
[1 Info  00:06:15.707] All services are started 5.666476
[1 Debug 00:06:17.537] Creating Pango.Layout, configuring Cairo.Context
[1 Debug 00:06:18.995] Loaded IScreensaverManager: Banshee.GnomeBackend.GnomeScreensaverManager
[1 Debug 00:06:20.342] Extension source loaded: File System Queue
[1 Debug 00:06:20.348] Extension source loaded: Miro Guide
** (Banshee:4211): DEBUG: Syncdaemon not running, waiting for it to start in NameOwnerChanged

(Banshee:4211): libsoup-WARNING **: No feature manager for feature of type 'U1RequestChrome'
Domain: 'Gtk' Level: Critical
Message: IA__gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed
Trace follows:
   at GLib.Log.PrintTraceLogFunction(System.String domain, LogLevelFlags level, System.String message)
   at GLib.Object.gtksharp_object_newv(IntPtr , Int32 , System.IntPtr[] , GLib.Value[] )
   at GLib.Object.CreateNativeObject(System.String[] names, GLib.Value[] vals)
   at Gtk.Object.CreateNativeObject(System.String[] names, GLib.Value[] vals)
   at Gtk.Widget.CreateNativeObject(System.String[] names, GLib.Value[] vals)
   at UbuntuOne.U1MusicStore..ctor()
   at Banshee.UbuntuOneMusicStore.UbuntuOneMusicStoreSource+StoreWrapper..ctor()
   at Banshee.UbuntuOneMusicStore.UbuntuOneMusicStoreSource+CustomView..ctor()
   at Banshee.UbuntuOneMusicStore.UbuntuOneMusicStoreSource..ctor()
   at System.Reflection.MonoCMethod.InternalInvoke(System.Reflection.MonoCMethod , System.Object , System.Object[] , System.Exception ByRef )
   at System.Reflection.MonoCMethod.Invoke(System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture)
   at System.Reflection.MonoCMethod.Invoke(BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture)
   at System.Reflection.ConstructorInfo.Invoke(System.Object[] parameters)
   at System.Activator.CreateInstance(System.Type type, Boolean nonPublic)
   at System.Activator.CreateInstance(System.Type type)
   at Mono.Addins.TypeExtensionNode.CreateInstance()
   at Banshee.Sources.SourceManager.OnExtensionChanged(System.Object o, Mono.Addins.ExtensionNodeEventArgs args)
   at Mono.Addins.ExtensionNode.add_ExtensionNodeChanged(Mono.Addins.ExtensionNodeEventHandler value)
   at Mono.Addins.ExtensionContext.AddExtensionNodeHandler(System.String path, Mono.Addins.ExtensionNodeEventHandler handler)
   at Mono.Addins.AddinManager.AddExtensionNodeHandler(System.String path, Mono.Addins.ExtensionNodeEventHandler handler)
   at Banshee.Sources.SourceManager.LoadExtensionSources()
   at Banshee.ServiceStack.Application.Run()
   at Banshee.Gui.GtkBaseClient.Initialize(Boolean registerCommonServices)
   at Banshee.Gui.GtkBaseClient..ctor(Boolean initializeDefault, System.String defaultIconName)
   at Banshee.Gui.GtkBaseClient..ctor()
   at Nereid.Client..ctor()
   at System.Reflection.MonoCMethod.InternalInvoke(System.Reflection.MonoCMethod , System.Object , System.Object[] , System.Exception ByRef )
   at System.Reflection.MonoCMethod.Invoke(System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture)
   at System.Reflection.MonoCMethod.Invoke(BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture)
   at System.Reflection.ConstructorInfo.Invoke(System.Object[] parameters)
   at System.Activator.CreateInstance(System.Type type, Boolean nonPublic)
   at System.Activator.CreateInstance(System.Type type)
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
[1 Debug 00:06:20.788] Extension source loaded: Ubuntu One Music Store
[1 Debug 00:06:20.843] Extension source loaded: Now Playing
[1 Debug 00:06:20.892] Extension source loaded: Radio
[1 Debug 00:06:21.097] Extension source loaded: Last.fm
[1 Debug 00:06:21.100] Extension source loaded: Jamendo
[1 Debug 00:06:21.264] [LiveRadioSource]<Constructor> found plugin: live365.com, enabled: True
[1 Debug 00:06:21.264] [LiveRadioSource]<Constructor> found plugin: magnatune.com, enabled: False
[1 Debug 00:06:21.268] [LiveRadioSource]<Constructor> found plugin: RealRadios.com, enabled: True
[1 Debug 00:06:21.268] [LiveRadioSource]<Constructor> found plugin: SHOUTcast.com, enabled: True
[1 Debug 00:06:21.268] [LiveRadioSource]<Constructor> found plugin: xiph.org, enabled: False
[1 Debug 00:06:21.990] Extension source loaded: LiveRadio
[1 Debug 00:06:22.030] Loaded new mode into  shuffler: mirage_similar
[1 Debug 00:06:22.032] Loaded new mode into  shuffler: lastfm_shuffle_similar_artists
[1 Debug 00:06:22.032] Loaded new mode into  shuffler: lastfm_shuffle_topartists
[1 Debug 00:06:23.624] Registering remote object /org/bansheeproject/Banshee/SourceManager/PlayQueue (Banshee.PlayQueue.PlayQueueSource) on org.bansheeproject.Banshee
[1 Debug 00:06:23.624] Extension source loaded: Play Queue
[1 Debug 00:06:23.684] Extension source loaded: Internet Archive
[1 Info  00:06:23.700] AmazonMP3 store redirect URL: https://one.ubuntu.com/music/store/amz/
[1 Debug 00:06:23.714] Extension source loaded: Amazon MP3 Store
[1 Debug 00:06:23.729] Starting GTK main loop
ClutterFlow - Loading Covers
[15 Debug 00:06:24.064] ArtworkLookup Run ()
The program 'Banshee' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadRequest (invalid request code or no such operation)'.
  (Details: serial 672 error_code 1 request_code 128 minor_code 187)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
```Does anyone know how to resolve this issue?

---

### Post by ManFromMars on 2011-10-31
Seems a few people have been having Banshee issues in 11.10... I think from reading the bug reports it is still an issue, but can be got around by disabling certain extensions in Edit->Preferences, Extensions tab. I've disabled all extensions requiring internet access as detailed [here]("http://mail.gnome.org/archives/banshee-list/2011-October/msg00113.html"), and that seems to have fixed the problem for now, though if you like those extensions it's a bit inconvenient!

---

### Post by Precipitous on 2011-10-31
> **ManFromMars said:**
> Seems a few people have been having Banshee issues in 11.10... I think from reading the bug reports it is still an issue, but can be got around by disabling certain extensions in Edit->Preferences, Extensions tab. I've disabled all extensions requiring internet access as detailed [here]("http://mail.gnome.org/archives/banshee-list/2011-October/msg00113.html"), and that seems to have fixed the problem for now, though if you like those extensions it's a bit inconvenient!
Thank you for the advice. Although it begs the question, if Banshee crashes on startup, how can one go to Edit > Preferences > Extensions...  Perhaps I will hit Synaptic and try uninstalling said extensions instead. 

I will post the result tonight.

---

### Post by ManFromMars on 2011-11-01
Heh, indeed. My problem/other people's problems that I've seen were that it crashed shortly after startup, so I/they could still go into the preferences menu. Hope you've managed to get it sorted!

---

### Post by Precipitous on 2011-11-01
I tried uninstalling all internet related extensions but it did not have any positive effect...  Still dead in the water. Thank god the newest release of Songbird for Linux runs really well!

---

### Post by liquidmonkey on 2011-11-02
have also had issues when starting banshee from time to time.
it seems rather random than consistent.
sometimes its shutsdown on startup, sometimes waits 10 seconds then crashes or even waits upto 5 minutes for a crash.

then i switched to clementine which is far better BUT that freezes the unity desktop after 30 minutes or so IF YOU TRY TO ACCESS A MENU.

---

### Post by Precipitous on 2011-11-09
I was able to resolve this issue by uninstalling the Clutter Flow extension.

---

