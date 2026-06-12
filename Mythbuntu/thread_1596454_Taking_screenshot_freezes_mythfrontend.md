---
title: "Taking screenshot freezes mythfrontend"
date: 2010-10-14
forum: Mythbuntu
---

### Post by bcg30506 on 2010-10-14
When I do a screenshot using mythfrontend while watching an HD show recorded with an HDHomeRun, the frontend app locks and won't accept any more input.  I have to force kill it.  It does take the snapshot of the frame successfully, but then appears to wait forever for a thread.  I've mapped the Ctrl+R key to this function.  When I do it for SD programs from the PVR-150, it does not lock up.  Here is the frontend log with -v playback passed on the command line.

```
2010-10-14 07:57:23.371 mythbackend version: branches/release-0-23-fixes [26732] www.mythtv.org
2010-10-14 07:57:23.372 Using runtime prefix = /usr
2010-10-14 07:57:23.372 Using configuration directory = /home/me/.mythtv
2010-10-14 07:57:23.372 Using localhost value of mythbox
2010-10-14 07:57:23.372 Testing network connectivity to '192.168.7.210'
2010-10-14 07:57:23.381 New DB connection, total: 1
2010-10-14 07:57:23.383 Connected to database 'mythconverg' at host: 192.168.7.210
2010-10-14 07:57:23.383 Closing DB connection named 'DBManager0'
2010-10-14 07:57:23.384 Connected to database 'mythconverg' at host: 192.168.7.210
2010-10-14 07:57:23.387 Current MythTV Schema Version (DBSchemaVer): 1254
2010-10-14 07:57:23.388 ProgramInfo(): Updated pathname '':'' -> '5193_20101013195900.mpg'
2010-10-14 07:57:23.431 AFD: Opened codec 0x9a91c70, id(MPEG2VIDEO) type(Video)
2010-10-14 07:57:23.431 AFD: codec AC3 has 6 channels
2010-10-14 07:57:23.431 AFD: Opened codec 0x9aa4990, id(AC3) type(Audio)
2010-10-14 07:57:23.600 Preview: Grabbed preview '/var/lib/mythtv/recordings/5193_20101013195900.mpg' 1920x1088@18911f
2010-10-14 07:57:24.280 ~MythContext waiting for threads to exit.

```

---

### Post by bcg30506 on 2010-10-14
I did a screen cap from the SD PVR-150 source while running with the -v playback flag for comparison.  It keeps working after grabbing the image and interestingly, here is the one and only line logged when doing it:

```
2010-10-14 08:41:32.127 Saved: '/home/me/.mythtv/1046_20101014084114_168.png'

```

---

