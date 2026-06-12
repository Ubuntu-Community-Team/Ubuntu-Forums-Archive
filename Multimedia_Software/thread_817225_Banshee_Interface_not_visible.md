---
title: "Banshee Interface not visible"
date: 2008-06-03
forum: Multimedia Software
---

### Post by darkside299 on 2008-06-03
I am using Ubuntu Hardy Heron and is up to date. When I start banshee-1, it simply isnt showing any buttons, icons or panes. There is the window frame with nothing inside the frame. When I try to start it from terminal with debug option, i get the following output:

[Info  22:11:30.237] Running Banshee 0.99.2
[Debug 22:11:32.673] NDesk.DBus.Bus.Session.RequestName ('org.bansheeproject.Banshee') => PrimaryOwner
[Debug 22:11:32.681] Core service started (DBusServiceManager, 0.204047s)
[Debug 22:11:32.919] Opened SQLite connection to /home/siddhesh/.config/banshee-1/banshee.db
[Debug 22:11:32.919] Core service started (DbConnection, 0.237591s)
[Debug 22:11:32.982] Database version 11 is up to date
[Debug 22:11:33.003] Core service started (PreferenceService, 0.019369s)
[Debug 22:11:33.027] Core service started (SourceManager, 0.022637s)
[Debug 22:11:33.362] Core service started (MediaProfileManager, 0.334127s)
[Debug 22:11:33.384] Core service started (PlayerEngine, 0.022164s)
[Debug 22:11:33.394] Configuration client extension loaded (Banshee.GnomeBackend.GConfConfigurationClient)
[Debug 22:11:33.544] IO provider extension loaded (Banshee.IO.Unix.Provider)
[Debug 22:11:33.598] Core service started (TranscoderService, 0.065938s)
[Debug 22:11:33.602] Core service started (PlaybackController, 0.002809s)
[Debug 22:11:33.602] Core service started (ImportSourceManager, 0.000147s)
[Debug 22:11:33.609] Core service started (LibraryImportManager, 0.006824s)
[Debug 22:11:33.614] Core service started (UserJobManager, 0.004814s)
[Debug 22:11:33.666] Core service started (HardwareManager, 0.050227s)
[Debug 22:11:33.863] Adding icon theme search path: /usr/share/banshee-1/icons
[Debug 22:11:33.864] Core service started (GtkElementsService, 0.197852s)
[Debug 22:11:34.020] Core service started (InterfaceActionService, 0.15577s)
[Debug 22:11:34.022] Album artwork path set to /home/siddhesh/.cache/album-art
[Debug 22:11:34.022] Core service started (ArtworkManager, 0.001452s)
[Debug 22:11:35.244] Core service started (NereidPlayerInterface, 1.221448s)
[Debug 22:11:35.437] Extension service started (AudioCdService, 0.19203s)
[Debug 22:11:35.440] Extension service started (DapService, 0.001623s)
[Debug 22:11:35.454] Using GNOME 2.22 API for Multimedia Keys
[Debug 22:11:35.454] Extension service started (MultimediaKeysService, 0.013986s)
[Debug 22:11:35.495] Extension service started (BookmarksService, 0.040389s)
[Debug 22:11:35.969] GStreamer pipeline does not run: audioconvert ! lame mode=4 bitrate=128 ! id3v2mux
[Debug 22:11:35.971] GStreamer pipeline does not run: audioconvert ! xingenc bitrate=128 ! id3v2mux
[Debug 22:11:36.301] GStreamer pipeline does not run: audioconvert ! fluwmaenc bitrate=64000 vbr=false ! fluasfmux
[Debug 22:11:36.301] Extension service started (GStreamerCoreService, 0.806103s)
[Debug 22:11:36.369] Player state change: NotReady -> Ready
[Debug 22:11:36.400] Player state change: Ready -> Idle
[Debug 22:11:36.622] Extension service started (NotificationAreaService, 0.197377s)
[Debug 22:11:36.634] Extension service started (GnomeService, 0.011406s)
[Debug 22:11:37.324] Extension service started (PodcastService, 0.689174s)

Here is the screenshot of the window: 
[http://www.flickr.com/photos/sidh299/2533611463/](http://www.flickr.com/photos/sidh299/2533611463/)

---

### Post by kakyoism on 2008-07-04
I got the same problem today...
probably after the gstream upgrade, i'm not sure

---

