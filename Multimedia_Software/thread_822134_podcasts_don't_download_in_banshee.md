---
title: "podcasts don't download in banshee"
date: 2008-06-07
forum: Multimedia Software
---

### Post by phoenix23 on 2008-06-07
Using banshee 1.0, every (tested/working elsewhere) podcast will download for exactly 60 seconds, then stop.

debug:

```
bstephen@stephen-desktop:~$ banshee-1 --debug
[Debug 22:18:12.841] NDesk.DBus.Bus.Session.RequestName ('org.bansheeproject.Banshee') => PrimaryOwner
[Info  22:18:12.864] Running Banshee 1.0.0
[Debug 22:18:14.714] Core service started (DBusServiceManager, 0.003115s)
[Debug 22:18:14.746] Core service started (DBusCommandService, 0.027367s)
[Debug 22:18:14.848] Opened SQLite connection to /home/stephen/.config/banshee-1/banshee.db
[Debug 22:18:14.849] Core service started (DbConnection, 0.10253s)
[Debug 22:18:14.915] Database version 11 is up to date
[Debug 22:18:14.954] Core service started (PreferenceService, 0.035707s)
[Debug 22:18:14.958] Core service started (SourceManager, 0.003745s)
[Debug 22:18:15.372] Core service started (MediaProfileManager, 0.41386s)
[Debug 22:18:15.380] Core service started (PlayerEngine, 0.00667s)
[Debug 22:18:15.392] Configuration client extension loaded (Banshee.GnomeBackend.GConfConfigurationClient)
[Debug 22:18:15.527] IO provider extension loaded (Banshee.IO.Unix.Provider)
[Debug 22:18:15.546] Core service started (TranscoderService, 0.025309s)
[Debug 22:18:15.552] Core service started (PlaybackController, 0.005131s)
[Debug 22:18:15.559] Core service started (ImportSourceManager, 0.000995s)
[Debug 22:18:15.569] Core service started (LibraryImportManager, 0.010106s)
[Debug 22:18:15.571] Core service started (UserJobManager, 0.001365s)
[Debug 22:18:15.613] Core service started (HardwareManager, 0.041053s)
[Debug 22:18:15.667] Adding icon theme search path: /usr/share/banshee-1/icons
[Debug 22:18:15.670] Core service started (GtkElementsService, 0.056458s)
[Debug 22:18:15.863] Core service started (InterfaceActionService, 0.192997s)
[Debug 22:18:15.865] Album artwork path set to /home/stephen/.cache/album-art
[Debug 22:18:15.866] Core service started (ArtworkManager, 0.002032s)
[Debug 22:18:16.997] Core service started (NereidPlayerInterface, 1.130848s)
[Debug 22:18:17.002] Extension service started (DapService, 0.002876s)
[Debug 22:18:17.089] Extension service started (BookmarksService, 0.08137s)
[Debug 22:18:17.379] Extension service started (NotificationAreaService, 0.288995s)
[Debug 22:18:17.594] Extension service started (AudioCdService, 0.213218s)
[Debug 22:18:17.692] Audioscrobbler state: connected
[Debug 22:18:17.707] Extension service started (AudioscrobblerService, 0.111614s)
[Debug 22:18:17.715] Extension service started (GnomeService, 0.008581s)
[Debug 22:18:18.466] Extension service started (PodcastService, 0.750321s)
[Debug 22:18:18.473] Using GNOME 2.22 API for Multimedia Keys
[Debug 22:18:18.474] Extension service started (MultimediaKeysService, 0.007163s)
[Debug 22:18:18.830] GStreamer pipeline does not run: audioconvert ! xingenc bitrate=128 ! id3v2mux
[Debug 22:18:19.014] GStreamer pipeline does not run: audioconvert ! fluwmaenc bitrate=64000 vbr=false ! fluasfmux
[Debug 22:18:19.016] Extension service started (GStreamerCoreService, 0.541718s)
[Debug 22:18:19.087] Player state change: NotReady -> Ready
[Debug 22:18:19.126] Player state change: Ready -> Idle
[Debug 22:18:19.155] Extension service started (CoverArtService, 0.005177s)
[Info  22:18:19.159] All services are started 4.455789s
[Info  22:18:21.475] nereid Client Started
[Debug 22:18:21.580] Dap support extension loaded: Banshee.Dap.Mtp
[Warn  22:18:22.014] Caught an exception - org.freedesktop.Hal.NoSuchProperty: No property volume.is_mounted on device with id /org/freedesktop/Hal/devices/platform_floppy_0_storage_platform_floppy (in `NDesk.DBus.Proxies')
  at IDeviceProxy.GetPropertyBoolean (System.String ) [0x00000] 
  at Hal.Device.GetPropertyBoolean (System.String key) [0x00000] in /build/buildd/banshee-1-1.0.0/src/Backends/Banshee.Hal/Hal/Device.cs:227 
  at Banshee.HalBackend.Volume.get_IsMounted () [0x00000] in /build/buildd/banshee-1-1.0.0/src/Backends/Banshee.Hal/Banshee.HalBackend/Volume.cs:102 
  at Banshee.HalBackend.Volume.CheckVolumeMounted (Banshee.HalBackend.Volume volume) [0x0006c] in /build/buildd/banshee-1-1.0.0/src/Backends/Banshee.Hal/Banshee.HalBackend/Volume.cs:185 
  at Banshee.HalBackend.Volume.Resolve (Banshee.HalBackend.BlockDevice parent, Hal.Manager manager, Hal.Device device) [0x00044] in /build/buildd/banshee-1-1.0.0/src/Backends/Banshee.Hal/Banshee.HalBackend/Volume.cs:56 
[Debug 22:18:22.492] Dap support extension loaded: Banshee.Dap.MassStorage
[Warn  22:18:22.724] Caught an exception - org.freedesktop.Hal.NoSuchProperty: No property volume.is_mounted on device with id /org/freedesktop/Hal/devices/platform_floppy_0_storage_platform_floppy (in `NDesk.DBus.Proxies')
  at IDeviceProxy.GetPropertyBoolean (System.String ) [0x00000] 
  at Hal.Device.GetPropertyBoolean (System.String key) [0x00000] in /build/buildd/banshee-1-1.0.0/src/Backends/Banshee.Hal/Hal/Device.cs:227 
  at Banshee.HalBackend.Volume.get_IsMounted () [0x00000] in /build/buildd/banshee-1-1.0.0/src/Backends/Banshee.Hal/Banshee.HalBackend/Volume.cs:102 
  at Banshee.HalBackend.Volume.CheckVolumeMounted (Banshee.HalBackend.Volume volume) [0x0006c] in /build/buildd/banshee-1-1.0.0/src/Backends/Banshee.Hal/Banshee.HalBackend/Volume.cs:185 
  at Banshee.HalBackend.Volume.Resolve (Banshee.HalBackend.BlockDevice parent, Hal.Manager manager, Hal.Device device) [0x00044] in /build/buildd/banshee-1-1.0.0/src/Backends/Banshee.Hal/Banshee.HalBackend/Volume.cs:56 
[Debug 22:18:23.075] Dap support extension loaded: Banshee.Dap.Ipod
[Warn  22:18:23.285] Caught an exception - org.freedesktop.Hal.NoSuchProperty: No property volume.is_mounted on device with id /org/freedesktop/Hal/devices/platform_floppy_0_storage_platform_floppy (in `NDesk.DBus.Proxies')
  at IDeviceProxy.GetPropertyBoolean (System.String ) [0x00000] 
  at Hal.Device.GetPropertyBoolean (System.String key) [0x00000] in /build/buildd/banshee-1-1.0.0/src/Backends/Banshee.Hal/Hal/Device.cs:227 
  at Banshee.HalBackend.Volume.get_IsMounted () [0x00000] in /build/buildd/banshee-1-1.0.0/src/Backends/Banshee.Hal/Banshee.HalBackend/Volume.cs:102 
  at Banshee.HalBackend.Volume.CheckVolumeMounted (Banshee.HalBackend.Volume volume) [0x0006c] in /build/buildd/banshee-1-1.0.0/src/Backends/Banshee.Hal/Banshee.HalBackend/Volume.cs:185 
  at Banshee.HalBackend.Volume.Resolve (Banshee.HalBackend.BlockDevice parent, Hal.Manager manager, Hal.Device device) [0x00044] in /build/buildd/banshee-1-1.0.0/src/Backends/Banshee.Hal/Banshee.HalBackend/Volume.cs:56 

(Nereid:5973): Gdk-WARNING **: GdkWindow 0x3000205 unexpectedly destroyed

(Nereid:5973): Gdk-WARNING **: GdkWindow 0x3000204 unexpectedly destroyed


```

any help?

---

### Post by prol on 2008-06-25
Podcasting for me worked when I had just installed ubuntu but after some updates i have this same problem

---

### Post by k3lt01 on 2008-07-22
It is listed as a bug on Banshee, I just asked on my own bug report if anything has been worked out yet.

I prefer Banshee to the other music/podcast players and now it has video capability it should be so much better but this failure to successfully download podcasts bug is something that is keeping me from using it.

---

