---
title: "little help with banshee after transfer"
date: 2010-02-22
forum: Multimedia Software
---

### Post by efranor on 2010-02-22
Hi, well in short I transferred from Gnome to KDE and after installing all applications I ran into a few problems. My VLC didn't play any sound even thou the video was streaming so I set the PCM and now it works, still my Banshee doesn't. When i try to play something I get a red x by the title and it doesn't play any sound. I installed oss and alsa but still no result.

---

### Post by boombox1387 on 2010-02-22
If you run Banshee from terminal with the --debug option, it might give you useful output.  I'd be happy to do what I can to help if post that output here.  The command is either 
```
banshee --debug
```
or
```
banshee-1 --debug
```

depending on where you got Banshee from.  If it's from the ubuntu repositories, I think it's the first one; if you got it from a PPA or built from source, it should be the second one.

---

### Post by efranor on 2010-02-22
** Running Mono with --debug   **                                               
[Info  19:12:20.638] Running Banshee 1.5.1: [Ubuntu karmic (development branch) (linux-gnu, i486) @ 2009-10-19 14:46:07 UTC]                                    

(/usr/lib/banshee-1/Banshee.exe:2086): GLib-WARNING **: g_set_prgname() called multiple times                                                                   
[Debug 19:12:22.183] Bus.Session.RequestName ('org.bansheeproject.Banshee') replied with PrimaryOwner                                                           
[Debug 19:12:22.197] Core service started (DBusServiceManager, 0.002015s)       
[Debug 19:12:22.201] Registering remote object /org/bansheeproject/Banshee/DBusCommandService (Banshee.ServiceStack.DBusCommandService) on org.bansheeproject.Banshee                                                                           
[Debug 19:12:22.220] Core service started (DBusCommandService, 0.022287s)       
[Debug 19:12:22.377] Opened SQLite connection to /home/efranor/.config/banshee-1/banshee.db                                                                     
[Debug 19:12:22.378] Core service started (DbConnection, 0.157447s)             
[Debug 19:12:22.408] Database version 35 is up to date                          
[Debug 19:12:22.663] Core service started (PreferenceService, 0.014243s)        
[Debug 19:12:22.664] Registering remote object /org/bansheeproject/Banshee/SourceManager (Banshee.Sources.SourceManager) on org.bansheeproject.Banshee          
[Debug 19:12:22.665] Core service started (SourceManager, 0.001272s)            
[Debug 19:12:22.665] Core service started (MediaProfileManager, 0.000254s)      
[Debug 19:12:22.666] Registering remote object /org/bansheeproject/Banshee/PlayerEngine (Banshee.MediaEngine.PlayerEngineService) on org.bansheeproject.Banshee 
[Debug 19:12:22.668] Core service started (PlayerEngine, 0.002692s)             
[Debug 19:12:22.674] Configuration client extension loaded (Banshee.GnomeBackend.GConfConfigurationClient)                                                      
[Debug 19:12:22.686] Using default gconf-base-key                               
[Debug 19:12:22.770] IO provider extension loaded (Banshee.IO.Unix.Provider)    
[Debug 19:12:22.783] Core service started (TranscoderService, 0.016618s)        
[Debug 19:12:22.785] Registering remote object /org/bansheeproject/Banshee/PlaybackController (Banshee.PlaybackController.PlaybackControllerService) on org.bansheeproject.Banshee                                                              
[Debug 19:12:22.786] Core service started (PlaybackController, 0.003077s)       
[Debug 19:12:22.786] Core service started (ImportSourceManager, 0.000603s)      
[Debug 19:12:22.795] Core service started (LibraryImportManager, 0.00856s)      
[Debug 19:12:22.796] Core service started (JobScheduler, 0.001073s)             
[Debug 19:12:22.827] Core service started (HardwareManager, 0.030997s)          
[Debug 19:12:22.833] Bus.Session.RequestName ('org.bansheeproject.CollectionIndexer') replied with PrimaryOwner                                                 
[Debug 19:12:22.834] Registering remote object /org/bansheeproject/Banshee/CollectionIndexerService (Banshee.Collection.Indexer.CollectionIndexerService) on org.bansheeproject.CollectionIndexer                                               
[Debug 19:12:22.835] Core service started (CollectionIndexerService, 0.00758s)  
[Debug 19:12:22.837] Core service started (SaveMetadataService, 0.00188s)       
[Debug 19:12:22.961] Adding icon theme search path: /usr/share/banshee-1/icons  
[Debug 19:12:22.962] Core service started (GtkElementsService, 0.125095s)       
[Debug 19:12:22.965] Core service started (InterfaceActionService, 0.002525s)   
[Debug 19:12:23.066] Album artwork path set to /home/efranor/.cache/album-art   
[Debug 19:12:23.066] Core service started (ArtworkManager, 0.003161s)           
[Debug 19:12:23.433] Adding context page lastfm-recommendations                 

(/usr/lib/banshee-1/Banshee.exe:2086): GVFS-RemoteVolumeMonitor-WARNING **: cannot open directory /usr/share/gvfs/remote-volume-monitors: Error opening directory '/usr/share/gvfs/remote-volume-monitors': No such file or directory           
[Debug 19:12:23.860] Registering remote object /org/bansheeproject/Banshee/ClientWindow (Nereid.PlayerInterface) on org.bansheeproject.Banshee                  
[Debug 19:12:23.860] Core service started (NereidPlayerInterface, 0.794008s)    
[Debug 19:12:23.911] Extension service started (GStreamerCoreService, 0.049132s)
[Debug 19:12:23.918] Extension service started (BpmService, 0.006839s)          
[Warn  19:12:23.943] Caught an exception - No support GNOME Settings Daemon could be reached. (in `Banshee.MultimediaKeys')                                     
  at Banshee.MultimediaKeys.MultimediaKeysService.Banshee.ServiceStack.IExtensionService.Initialize () [0x00000]                                                
  at Banshee.ServiceStack.ServiceManager.StartExtension (Mono.Addins.TypeExtensionNode node) [0x00000]                                                          
[Warn  19:12:23.951] Extension `Banshee.MultimediaKeys.MultimediaKeysService' not started: No support GNOME Settings Daemon could be reached.                   
[Debug 19:12:23.954] Extension service started (PodcastService, 0.003056s)      
[Debug 19:12:23.954] Extension service started (DapService, 0.000333s)          
[Debug 19:12:23.978] Extension service started (DaapService, 0.023503s)         
[Debug 19:12:23.981] Extension service started (GnomeService, 0.00247s)         
[Debug 19:12:24.042] Core service started (Network, 0.023933s)                  
[Debug 19:12:24.043] Audioscrobbler state: connected                            
[Debug 19:12:24.046] Extension service started (AudioscrobblerService, 0.064881s)                                                                               
[Debug 19:12:24.074] Extension service started (NotificationAreaService, 0.028096s)                                                                             
[Debug 19:12:24.117] Extension service started (BookmarksService, 0.04303s)     
[Debug 19:12:24.120] Extension service started (CoverArtService, 0.003599s)     
[Debug 19:12:24.190] Extension service started (AudioCdService, 0.069944s)      
[Warn  19:12:24.193] Caught an exception - No support GNOME Settings Daemon could be reached. (in `Banshee.MultimediaKeys')                                     
  at Banshee.MultimediaKeys.MultimediaKeysService.Banshee.ServiceStack.IExtensionService.Initialize () [0x00000]                                                
  at Banshee.ServiceStack.ServiceManager.StartExtension (Mono.Addins.TypeExtensionNode node) [0x00000]                                                          
[Warn  19:12:24.193] Extension `Banshee.MultimediaKeys.MultimediaKeysService' not started: No support GNOME Settings Daemon could be reached.                   
[Info  19:12:24.193] All services are started 2.008965s                         
[Debug 19:12:25.578] Registering remote object /org/bansheeproject/Banshee/SourceManager/PlayQueue (Banshee.PlayQueue.PlayQueueSource) on org.bansheeproject.Banshee                                                                            
[Info  19:12:25.967] GNOME screensaver service not found                        
[Debug 19:12:25.967] Loaded IScreensaverManager: Banshee.GnomeBackend.GnomeScreensaverManager                                                                   
[Debug 19:12:26.682] Creating Pango.Layout, configuring Cairo.Context           
[Debug 19:12:26.731] Creating Pango.Layout, configuring Cairo.Context           
[Debug 19:12:26.766] Creating new surface cache for 9216 KB (max) images, capped at 1 MB (113 items)                                                            
[Debug 19:12:26.807] Creating Pango.Layout, configuring Cairo.Context           
[Info  19:12:27.126] nereid Client Started                                      
[Debug 19:12:27.128] Delayed Initializating Banshee.MediaEngine.PlayerEngineService                                                                             
[Debug 19:12:27.151] (libbanshee:player) Using system (gst-plugins-good) equalizer element                                                                      
[Debug 19:12:27.280] Player state change: NotReady -> Ready                     
[Debug 19:12:27.288] Player state change: Ready -> Idle                         
[Debug 19:12:27.293] (libbanshee:player) Disabled ReplayGain                    
[Debug 19:12:27.293] Delayed Initializating Banshee.Podcasting.PodcastService   
[Debug 19:12:27.717] Refreshing any podcasts that haven't been updated in over an hour                                                                          
[Debug 19:12:27.720] Delayed Initializating Banshee.Dap.DapService              
[Debug 19:12:27.729] Dap support extension loaded: Banshee.Dap.MassStorage      
[Debug 19:12:28.113] Dap support extension loaded: Banshee.Dap.Ipod             
[Debug 19:12:28.390] Dap support extension loaded: Banshee.Dap.Mtp              
[Debug 19:12:28.676] Dap support extension loaded: Banshee.Dap.Karma            
[Debug 19:12:28.958] Delayed Initializating Banshee.Daap.DaapService            
[Debug 19:12:38.438] Player state change: Idle -> Loading                       
** Message: don't know how to handle audio/mpeg, mpegversion=(int)1, layer=(int)3                                                                               
[Debug 19:12:38.462] (libbanshee:player) Saving missing element details ('gstreamer|0.10|/usr/lib/banshee-1/Banshee.exe|MPEG-1 Layer 3 (MP3) decoder|decoder-audio/mpeg, mpegversion=(int)1, layer=(int)3')                                     
[Debug 19:12:38.465] (libbanshee:player) bp_stop: setting state to GST_STATE_NULL                                                                               
[Debug 19:12:38.465] Player state change: Loading -> Idle                       
[Error 19:12:38.467] GStreamer stream error: CodecNotFound                      
[Debug 19:12:38.720] Querying model for track to play in Linear:Next mode       
[Debug 19:12:38.735] Player state change: Idle -> Loading                       
** Message: don't know how to handle audio/mpeg, mpegversion=(int)1, layer=(int)3                                                                               
[Debug 19:12:38.781] (libbanshee:player) Saving missing element details ('gstreamer|0.10|/usr/lib/banshee-1/Banshee.exe|MPEG-1 Layer 3 (MP3) decoder|decoder-audio/mpeg, mpegversion=(int)1, layer=(int)3')                                     
[Debug 19:12:38.782] (libbanshee:player) bp_stop: setting state to GST_STATE_NULL
[Debug 19:12:38.782] Player state change: Loading -> Idle
[Error 19:12:38.783] GStreamer stream error: CodecNotFound
[Debug 19:12:39.034] Querying model for track to play in Linear:Next mode
[Debug 19:12:39.041] Player state change: Idle -> Loading
** Message: don't know how to handle audio/mpeg, mpegversion=(int)1, layer=(int)3
[Debug 19:12:39.094] (libbanshee:player) Saving missing element details ('gstreamer|0.10|/usr/lib/banshee-1/Banshee.exe|MPEG-1 Layer 3 (MP3) decoder|decoder-audio/mpeg, mpegversion=(int)1, layer=(int)3')

Well i installed gstreamer and nada

---

### Post by boombox1387 on 2010-02-22
There are some fairly important gstreamer plugins as well; do you also have:

gstreamer0.10-plugins-base
gstreamer0.10-plugins-good
gstreamer0.10-plugins-bad
gstreamer0.10-plugins-ugly

The names might differ slightly, but you'll need the -ugly plugin for mp3 playback.  (There are some alternatives like -fluendo-mp3 and -ffmpeg, but I don't know much about those, and there are some known issues with --ffmpeg).

From the look of things, the MultimediaKeys extension is also running into problems on KDE, so you might want to disable that (in Edit > Preferences > Extensions), though I highly doubt that will affect playback.  Unfortunately, none of the main Banshee developers regularly use KDE, so if you have all the required gstreamer plugins and you still can't play back music, your best bet may be to report a bug (or find a KDE user who got it to work -- I've been meaning to test Banshee on KDE, but so far I haven't).

---

### Post by efranor on 2010-02-22
hah seems I forgot that those gstreamer parts aren't a package, well for your information now you have a KDE user who's Banshee works, thx ppl

---

### Post by boombox1387 on 2010-02-22
> **efranor said:**
> hah seems I forgot that those gstreamer parts aren't a package, well for your information now you have a KDE user who's Banshee works, thx ppl

Woohoo! Glad to hear it.  Since Banshee is less-thoroughly tested on KDE, be sure to report any bugs you run into.

---

### Post by wagoner on 2010-03-28
I have banshee working on KDE, however, it won't playback if I start firefox first.  I work around this by closing firefox and then starting banshee.  Otherwise banshee just puts a red 'x' next to the track.

---

### Post by boombox1387 on 2010-03-29
> **wagoner said:**
> I have banshee working on KDE, however, it won't playback if I start firefox first.  I work around this by closing firefox and then starting banshee.  Otherwise banshee just puts a red 'x' next to the track.

You're not alone; see this thread: [http://ubuntuforums.org/showthread.php?p=9035089](http://ubuntuforums.org/showthread.php?p=9035089)

I'm not really sure what the deal is, but someone experiencing the issue should probably report it to Launchpad.  People there will help figure out which project is to blame, which would be the first step toward getting it fixed.

---

