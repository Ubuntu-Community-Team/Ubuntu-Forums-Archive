---
title: "Banshee keeps crashing every time after trying to play something"
date: 2013-02-11
forum: Multimedia Software
---

### Post by Habermas on 2013-02-11
Hey guys, tried searching for similar problems and solutions but without much luck. Suddenly Banshee media player stopped working properly, every time I try to play something from my library it plays it for a few secs and then crashes. The problem seems to be with something called gstreamer. 

Here is the debug info from the console. 

```
master@Master:/$ banshee --debug
** Running Mono with --debug   **
[1 Debug 00:01:49.033] Bus.Session.RequestName ('org.bansheeproject.Banshee') replied with PrimaryOwner
[1 Info  00:01:49.103] Running Banshee 2.6.0: [Ubuntu 12.10 (linux-gnu, i686) @ 2012-12-12 06:19:16 UTC]
[1 Debug 00:01:49.130] Initializing GTK
[1 Debug 00:01:52.055] Post-Initializing GTK
[1 Debug 00:01:52.094] Configuration client extension loaded (Banshee.GnomeBackend.GConfConfigurationClient)
[1 Debug 00:01:52.102] Using default gconf-base-key
[1 Debug 00:01:52.352] Core service started (DBusServiceManager, 0.004694)
[1 Debug 00:01:52.360] Registering remote object /org/bansheeproject/Banshee/DBusCommandService (Banshee.ServiceStack.DBusCommandService) on org.bansheeproject.Banshee
[1 Debug 00:01:52.384] Core service started (DBusCommandService, 0.030592)
[1 Debug 00:01:52.483] Opened SQLite (version 3.7.13) connection to /home/master/.config/banshee-1/banshee.db
[1 Debug 00:01:52.485] Core service started (DbConnection, 0.10072)
[1 Debug 00:01:52.507] Database version 45 is up to date
[1 Debug 00:01:52.598] Core service started (PreferenceService, 0.033049)
[1 Debug 00:01:52.626] Core service started (Network, 0.0273)
[1 Debug 00:01:52.629] Registering remote object /org/bansheeproject/Banshee/SourceManager (Banshee.Sources.SourceManager) on org.bansheeproject.Banshee
[1 Debug 00:01:52.629] Core service started (SourceManager, 0.002663)
[1 Debug 00:01:52.646] Core service started (MediaProfileManager, 0.000884)
[1 Debug 00:01:52.654] Registering remote object /org/bansheeproject/Banshee/PlayerEngine (Banshee.MediaEngine.PlayerEngineService) on org.bansheeproject.Banshee
[1 Debug 00:01:52.662] Core service started (PlayerEngine, 0.016047)
[1 Debug 00:01:52.710] Registering remote object /org/bansheeproject/Banshee/PlaybackController (Banshee.PlaybackController.PlaybackControllerService) on org.bansheeproject.Banshee
[1 Debug 00:01:52.713] Core service started (PlaybackController, 0.008802)
[1 Debug 00:01:52.733] Starting - Startup Job
[1 Debug 00:01:52.736] Core service started (JobScheduler, 0.022525)
[1 Debug 00:01:52.770] IO provider extension loaded (Banshee.IO.Gio.Provider)
[1 Debug 00:01:52.920] Loaded HardwareManager backend: Banshee.Hardware.Gio
[1 Debug 00:01:52.925] Core service started (HardwareManager, 0.188931)
[1 Debug 00:01:52.930] Bus.Session.RequestName ('org.bansheeproject.CollectionIndexer') replied with PrimaryOwner
[1 Debug 00:01:52.934] Registering remote object /org/bansheeproject/Banshee/CollectionIndexerService (Banshee.Collection.Indexer.CollectionIndexerService) on org.bansheeproject.CollectionIndexer
[1 Debug 00:01:52.939] Core service started (CollectionIndexerService, 0.013013)
[1 Debug 00:01:52.943] Core service started (SaveTrackMetadataService, 0.004786)
[1 Debug 00:01:53.012] Adding icon theme search path: /usr/share/banshee/icons
[1 Debug 00:01:53.015] Core service started (GtkElementsService, 0.071267)
[1 Debug 00:01:53.020] Core service started (InterfaceActionService, 0.004409)
[1 Debug 00:01:53.279] Registering remote object /org/bansheeproject/Banshee/GlobalUIActions (Banshee.Gui.GlobalActions) on org.bansheeproject.Banshee
[1 Debug 00:01:53.284] Album artwork path set to /home/master/.cache/media-art
[1 Debug 00:01:53.345] Core service started (ArtworkManager, 0.06565)
[1 Debug 00:01:53.346] Core service started (BookmarksService, 0.000551)
[1 Debug 00:01:54.598] Constructed Nereid interface: 1.049223
[1 Debug 00:01:54.899] Registering remote object /org/bansheeproject/Banshee/ClientWindow (Nereid.PlayerInterface) on org.bansheeproject.Banshee
[1 Debug 00:01:54.899] Core service started (NereidPlayerInterface, 1.421532)
[1 Info  00:01:54.917] Updating web proxy from GConf
[1 Debug 00:01:54.943] Direct connection, no proxy in use
[1 Debug 00:01:55.011] Extension service started (GnomeService, 0.108481)
[1 Debug 00:01:55.024] Extension service started (PodcastService, 0.011676)
BansheeRemoteListener: Preferences installed
BansheRemoteListener will listen on port 7469
[1 Debug 00:01:55.110] Extension service started (RemoteServer, 0.085985)
[1 Debug 00:01:55.214] Extension service started (GStreamerCoreService, 0.103326)
[1 Debug 00:01:55.217] Extension service started (DapService, 0.002596)
[1 Info  00:01:55.220] All services are started 3.034764
[1 Debug 00:01:57.807] Extension source loaded: Now Playing
[1 Debug 00:01:57.822] Starting GTK main loop
[1 Debug 00:01:58.139] Creating Pango.Layout, configuring Cairo.Context

** (Banshee:4876): WARNING **: Invalid borders specified for theme pixmap:
        /usr/share/themes/Lubuntu-default/gtk-2.0/images/null.png,
borders don't fit within the image

** (Banshee:4876): WARNING **: Invalid borders specified for theme pixmap:
        /usr/share/themes/Lubuntu-default/gtk-2.0/images/scrollbar_vertical.png,
borders don't fit within the image
[1 Info  00:01:58.518] nereid Client Started
[1 Debug 00:01:58.527] Delayed Initializating Banshee.MediaEngine.PlayerEngineService
[1 Debug 00:01:58.588] (libbanshee:player) Audiosink has volume: YES
[1 Debug 00:01:58.639] (libbanshee:player) Using system (gst-plugins-good) equalizer element
[1 Debug 00:01:58.825] Player state change: NotReady -> Ready
[1 Debug 00:01:58.839] Loaded equalizer presets: 0.000915
[1 Debug 00:01:58.856] Selected equalizer: Rock
[1 Debug 00:01:58.870] Player state change: Ready -> Idle
[1 Debug 00:01:58.881] (libbanshee:player) Enabled ReplayGain
[1 Debug 00:01:58.929] (libbanshee:player) scaled volume: 1.00 (ReplayGain) * 1.00 (User) = 1.00
[1 Info  00:01:58.934] GStreamer version 0.10.36.0, gapless: True, replaygain: True
[1 Debug 00:01:58.946] (libbanshee:player) scaled volume: 1.00 (ReplayGain) * 1.00 (User) = 1.00
[1 Debug 00:01:58.950] Delayed Initializating Banshee.Podcasting.PodcastService
[1 Debug 00:01:59.136] Delayed Initializating Banshee.Dap.DapService
[1 Debug 00:01:59.161] Dap support extension loaded: Banshee.Dap.MassStorage
[9 Debug 00:01:59.191] Refreshing any podcasts that haven't been updated in over an hour
[1 Debug 00:02:00.196] Finished - Startup Job
[1 Debug 00:02:02.976] Starting - Saving Metadata to File
[13 Debug 00:02:03.029] Finished - Saving Metadata to File
[1 Debug 00:02:24.197] Player state change: Idle -> Loading
[1 Debug 00:02:24.683] Player state change: Loading -> Loaded
[1 Debug 00:02:24.755] (libbanshee:player) [gapless] Triggering track-change signal

(Banshee:4876): GStreamer-CRITICAL **: gst_element_query: assertion `GST_IS_ELEMENT (element)' failed
[1 Debug 00:02:24.860] Player state change: Loaded -> Playing
[1 Debug 00:02:24.954] Creating Pango.Layout, configuring Cairo.Context
[1 Debug 00:02:24.955] Creating Pango.Layout, configuring Cairo.Context
[1 Debug 00:02:25.866] TrackInfoDisplay RenderAnimation: 23.00 FPS
(!) [ 4899:    0.000] --> Caught signal 24 (unknown origin) <--
Stacktrace:

(!) [ 4886:    0.000] --> Caught signal 24 (unknown origin) <--
Aborted (core dumped)
master@Master:/$ 

```

P.S. I only have basic computer skills so please guys keep it simple :) Thanks in advance!

---

### Post by unheeding on 2013-02-12
This might be a problem with gstreamer, I found an instance of an Arch Linux user who had to recompile gstreamer to fix it.


First off, try this in a terminal:

```
sudo apt-get install gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly
```

---

### Post by Habermas on 2013-02-12
Already tried that, it tells me that I already have the latest versions of all those plugins.

```
gstreamer0.10-plugins-good is already the newest version.
gstreamer0.10-plugins-ugly is already the newest version.
gstreamer0.10-plugins-bad is already the newest version.
The following packages were automatically installed and are no longer required:
  icoutils kde-runtime-data libakonadi-kabc4 libakonadi-kcal4
  libakonadi-kmime4 libart-2.0-2 libbonoboui2-0 libbonoboui2-common libdmtx0a
  libfltk1.1 libgnomecanvas2-0 libgnomecanvas2-common libgnomeui-0
  libgnomeui-common libjpeg-progs libjpeg-turbo-progs libkabc4 libkcal4
  libkdecorations4abi1 libkdesu5 libkmediaplayer4 libknotifyconfig4
  libkolabxml0 libkresources4 libkwineffects1abi4 libkwinglutils1abi1
  libkwinnvidiahack4 libkworkspace4abi2 libmailtransport4 libmicroblog4
  libntrack-qt4-1 libntrack0 libprison0 libqapt-runtime libqapt1 libqjson0
  libqrencode3 libqt4-help libqt4-scripttools libqt4-test
  libqtassistantclient4 libxerces-c3.1 ntrack-module-libnl-0 oxygen-icon-theme
  plasma-scriptengine-javascript python-qt4 python-sip
  shared-desktop-ontologies thunderbird-locale-en thunderbird-locale-en-gb
  thunderbird-locale-en-us thunderbird-locale-zh-cn thunderbird-locale-zh-hans
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 65 not upgraded.

```

---

### Post by tgalati4 on 2013-02-12
I've never seen signal 24 before.  According to the interwebz:

SIGXCPU	24	CPU limit exceeded (4.2 BSD)

Another source:

SIGXCPU	24,24,30	Core	CPU time limit exceeded (4.2 BSD)

That doesn't help, nor the fact that the debug gives:  Caught signal 24 (unknown origin)--so we really don't know what sent the signal in the first place.

Some setting has determined that Banshee (or a subprocess) is taking too much CPU time and forces Banshee to quit with a core dump--the expected behavior for Signal 24 which is trapped by the process and then handled by the kernel.

Is it possible that your Banshee database got corrupted and it's taking too much time to load?  How many tracks do you have in Banshee?

Do other music players work?

In a terminal:

```
aplay -l
aplay musicfile.mp3
```

---

### Post by Habermas on 2013-02-13
Thank you for your response! According to Banshee I have 6396 songs in my library. Tried the "aplay" command and it made my speakers do some weird snake-like noises :P Here is what the console gave me when I tried playing mp3 file with that command:

```
master@Master:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC272X Analog [ALC272X Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
master@Master:~$ aplay /home/master/Music/"Rick James - Mary Jane.mp3"
Playing raw data '/home/master/Music/Rick James - Mary Jane.mp3' : Unsigned 8 bit, Rate 8000 Hz, Mono

```

Later on I'll try installing a different media player to see if the problem is more widespread or just limited to Banshee but I would really like to get Banshee working cause I really like it :)

---

### Post by tgalati4 on 2013-02-13
My fault, *aplay* handles WAV and other formats, but not mp3 natively.  You need to use mplayer or some other player.

6400 tracks is not a huge number.  When you get over 10K tracks, things can get slow and strange--depending on hardware.

Try rhythmbox and import a few of  your tracks.  I really think it might be a Banshee database corruption.  That means, deleting your library (NOT your music tracks) and re-importing the tracks into a new library.  You might want to search for a documented procedure to wipe the database in Banshee.  Check for mangled music-track filenames, that can sometimes trip up the database.

---

