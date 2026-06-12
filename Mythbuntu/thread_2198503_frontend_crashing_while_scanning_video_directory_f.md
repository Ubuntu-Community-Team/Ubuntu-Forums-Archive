---
title: "frontend crashing while scanning video directory for changes"
date: 2014-01-09
forum: Mythbuntu
---

### Post by Lido on 2014-01-09
I'm running Ubuntu 12.04 LTS with MythTV fixes/0.25 (v0.25.2-15-g46cab93). I copied a video into my videos directory today, but when I went to watch it, it didn't appear in the frontend media library under videos. I hit "M" to scan for changes and the progress bar jumps to about halfway, then freezes, then it crashed the frontend. I tried it several times and rebooted the machine and the same thing keeps happening and the database is never updated as far as I can tell. Here's a few lines from the log:

```

```tail mythfrontend.log
Jan  8 13:55:13 Mythbuntu mythfrontend[3138]: I VideoScanner videoscan.cpp:280 (verifyFiles) Removing file SG(Mythbuntu) :VTS_01_0.VOB:
Jan  8 13:55:13 Mythbuntu mythfrontend[3138]: I VideoScanner videoscan.cpp:280 (verifyFiles) Removing file SG(Mythbuntu) :VTS_01_1.VOB:
Jan  8 13:55:13 Mythbuntu mythfrontend[3138]: I VideoScanner videoscan.cpp:280 (verifyFiles) Removing file SG(Mythbuntu) :VTS_01_2.VOB:
Jan  8 13:55:13 Mythbuntu mythfrontend[3138]: I VideoScanner videoscan.cpp:280 (verifyFiles) Removing file SG(Mythbuntu) :VTS_01_3.VOB:
Jan  8 13:55:13 Mythbuntu mythfrontend[3138]: I VideoScanner videoscan.cpp:280 (verifyFiles) Removing file SG(Mythbuntu) :VTS_01_4.VOB:
Jan  8 13:55:13 Mythbuntu mythfrontend[3138]: I VideoScanner videoscan.cpp:280 (verifyFiles) Removing file SG(Mythbuntu) :VTS_01_5.VOB:
Jan  8 13:55:43 Mythbuntu mythfrontend[3138]: E VideoScanner mythsocket.cpp:534 (readStringList) MythSocket(18978a0:52): readStringList: Error, timed out after 30000 ms.
Jan  8 13:55:43 Mythbuntu mythfrontend[3138]: N VideoScanner mythcorecontext.cpp:960 (SendReceiveStringList) Connection to backend server lost
Jan  8 13:55:43 Mythbuntu mythfrontend[3138]: I VideoScanner mythcorecontext.cpp:371 (ConnectCommandSocket) MythCoreContext: Connecting to backend server: localhost:6585 (try 1 of 1)
Jan  8 13:55:43 Mythbuntu mythfrontend[3138]: E VideoScanner mythcorecontext.cpp:892 (GetBackendServerIP) No address defined for host: localhost

---

### Post by tuat2 on 2014-01-11
That looks like the backend crashes (the frontend loses connection) and maybe restarts. Did you check mythbackend.log, too?

---

### Post by Lido on 2014-02-11
I'm getting a lot of repeating errors in the backend log, but I don't see why it's crashing the scan for changes command when I'm viewing the videos listing under Media Library. Here are the lines from the frontend log:
```
Feb 10 22:50:33 Mythbuntu mythfrontend[2617]: I VideoScanner videoscan.cpp:280 (verifyFiles) Removing file SG(Mythbuntu) :MST3K/MST3K Shorts/VIDEO_TS/VTS_01_5.VOB:
Feb 10 22:50:56 Mythbuntu mythfrontend[2617]: N PreviewGenerator previewgenerator.cpp:388 (RemotePreviewRun) Preview: RemotePreviewRun() -- no reply..
Feb 10 22:51:03 Mythbuntu mythfrontend[2617]: E VideoScanner mythsocket.cpp:534 (readStringList) MythSocket(3700850:49): readStringList: Error, timed out after 30000 ms.
Feb 10 22:51:03 Mythbuntu mythfrontend[2617]: N VideoScanner mythcorecontext.cpp:960 (SendReceiveStringList) Connection to backend server lost
```

...and here are the lines from that timeframe from the backend log:
```
Feb 10 22:50:12 Mythbuntu mythbackend[1719]: E CoreContext mythsocket.cpp:534 (readStringList) MythSocket(19ccf40:30): readStringList: Error, timed out after 30000 ms.
Feb 10 22:50:12 Mythbuntu mythbackend[1719]: E CoreContext mainserver.cpp:6146 (reconnectTimeout) MainServer: Failed to open master server socket, timeout
Feb 10 22:50:12 Mythbuntu mythbackend[1719]: I ProcessRequest mainserver.cpp:1410 (HandleAnnounce) adding: Mythbuntu as a slave backend server
Feb 10 22:50:12 Mythbuntu mythbackend[1719]: W ProcessRequest mainserver.cpp:5801 (connectionClosed) MainServer: Unknown socket closing MythSocket(0x19ccf40)
Feb 10 22:50:12 Mythbuntu mythbackend[1719]: E ProcessRequest mythsocket.cpp:358 (writeStringList) MythSocket(19ccf40:-1): writeStringList: Error, socket went unconnected.#012#011#011#011We wrote 0 of 10 bytes with 1 errors#012#011#011#011starts with: 2       OK
Feb 10 22:50:13 Mythbuntu mythbackend[1719]: N CoreContext mainserver.cpp:6090 (reconnectTimeout) Connecting to master server: localhost:6543
Feb 10 22:50:13 Mythbuntu mythbackend[1719]: E CoreContext mythcorecontext.cpp:892 (GetBackendServerIP) No address defined for host: localhost
Feb 10 22:50:13 Mythbuntu mythbackend[1719]: N CoreContext mainserver.cpp:6108 (reconnectTimeout) Connected successfully
Feb 10 22:50:20 Mythbuntu mythbackend[1719]: I PreviewGeneratorQueue mythdbcon.cpp:395 (PurgeIdleConnections) New DB connection, total: 9
Feb 10 22:50:33 Mythbuntu mythbackend[1719]: E ProcessRequest mythsocket.cpp:319 (writeStringList) MythSocket(19d02f0:48): writeStringList: Error, joined null string.
Feb 10 22:50:43 Mythbuntu mythbackend[1719]: E CoreContext mythsocket.cpp:534 (readStringList) MythSocket(19c4010:30): readStringList: Error, timed out after 30000 ms.
Feb 10 22:50:43 Mythbuntu mythbackend[1719]: E CoreContext mainserver.cpp:6146 (reconnectTimeout) MainServer: Failed to open master server socket, timeout
Feb 10 22:50:43 Mythbuntu mythbackend[1719]: I ProcessRequest mainserver.cpp:1410 (HandleAnnounce) adding: Mythbuntu as a slave backend server
Feb 10 22:50:43 Mythbuntu mythbackend[1719]: W ProcessRequest mainserver.cpp:5801 (connectionClosed) MainServer: Unknown socket closing MythSocket(0x19c4010)
Feb 10 22:50:43 Mythbuntu mythbackend[1719]: W ProcessRequest mainserver.cpp:5801 (connectionClosed) MainServer: Unknown socket closing MythSocket(0x1a37650)
Feb 10 22:50:43 Mythbuntu mythbackend[1719]: W ProcessRequest mainserver.cpp:5801 (connectionClosed) MainServer: Unknown socket closing MythSocket(0x1a56540)
Feb 10 22:50:43 Mythbuntu mythbackend[1719]: W ProcessRequest mainserver.cpp:5801 (connectionClosed) MainServer: Unknown socket closing MythSocket(0x1a56540)
Feb 10 22:50:43 Mythbuntu mythbackend[1719]: W ProcessRequest mainserver.cpp:5801 (connectionClosed) MainServer: Unknown socket closing MythSocket(0x1a37650)
Feb 10 22:50:43 Mythbuntu mythbackend[1719]: E ProcessRequest mythsocket.cpp:358 (writeStringList) MythSocket(19c4010:-1): writeStringList: Error, socket went unconnected.#012#011#011#011We wrote 0 of 10 bytes with 1 errors#012#011#011#011starts with: 2       OK
Feb 10 22:50:43 Mythbuntu mythbackend[1719]: E ProcessRequest mythsocket.cpp:358 (writeStringList) MythSocket(1a56540:-1): writeStringList: Error, socket went unconnected.#012#011#011#011We wrote 0 of 21 bytes with 1 errors#012#011#011#011starts with: 13      ACCEPT[]:[]72
Feb 10 22:50:43 Mythbuntu mythbackend[1719]: E ProcessRequest mythsocket.cpp:358 (writeStringList) MythSocket(1a37650:-1): writeStringList: Error, socket went unconnected.#012#011#011#011We wrote 0 of 21 bytes with 1 errors#012#011#011#011starts with: 13      ACCEPT[]:[]72
Feb 10 22:50:43 Mythbuntu mythbackend[1719]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
Feb 10 22:50:43 Mythbuntu mythbackend[1719]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: Mythbuntu as a client (events: 0)
Feb 10 22:50:43 Mythbuntu mythbackend[1719]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
Feb 10 22:50:43 Mythbuntu mythbackend[1719]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: Mythbuntu as a client (events: 1)
Feb 10 22:50:44 Mythbuntu mythbackend[1719]: N CoreContext mainserver.cpp:6090 (reconnectTimeout) Connecting to master server: localhost:6543
Feb 10 22:50:44 Mythbuntu mythbackend[1719]: E CoreContext mythcorecontext.cpp:892 (GetBackendServerIP) No address defined for host: localhost
Feb 10 22:50:44 Mythbuntu mythbackend[1719]: N CoreContext mainserver.cpp:6108 (reconnectTimeout) Connected successfully
```

Because I was having this problem, I deleted the directory MST3K/MST3K Shorts/ entirely (using the OS, not the "D" / delete key in MythTV), but that didn't seem to help. Is there a way to manually go into mysql and delete those videos and see if that fixes the issue or is that not a good idea? Thanks!

---

