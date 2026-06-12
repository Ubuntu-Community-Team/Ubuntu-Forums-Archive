---
title: "mythtv use to convert to divx/xvid/dvd but will not now"
date: 2007-09-23
forum: Multimedia &amp; Video
---

### Post by jba6511 on 2007-09-23
I had mythtv working and autotranscoding (converting) to divx/xvid/etc with the old zap2it account. I recently upgraded to the new mythtv version and have begun to import my own xml listings. Everything works great until I get to the converting of the recordings. This has not changed at all and I do not know why it no longer will convert. Running nuvexport in the terminal works fine and the shows will convert from mpg to divx and then move themselves to the correct directory. I checked the logs and found the following:

[PHP]2007-09-22 14:24:48.681 JobQueue: Started "Convert to DIVX" for "5 HBO (5)" recorded from channel 1050 at Sat Sep 22 14:19:00 2007
2007-09-22 14:24:48.691 jobqueue: Job "Convert to DIVX" Started: Started "Convert to DIVX" for "5 HBO (5)" recorded from channel 1050 at Sat Sep 22 14:19:00 2007
OSPEED was not set, defaulting to 9600 at /usr/local/share/nuvexport/nuv_export/shared_utils.pm line 61
Can't find a valid termcap file at /usr/local/share/nuvexport/nuv_export/shared_utils.pm line 61
Compilation failed in require at /usr/local/bin/nuvexport-divx line 36.
BEGIN failed--compilation aborted at /usr/local/bin/nuvexport-divx line 36.

Cleaning up temp files.
2007-09-22 14:24:48.935 JobQueue: Finished "Convert to DIVX" for "5 HBO (5)" recorded from channel 1050 at Sat Sep 22 14:19:00 2007.
2007-09-22 14:24:48.940 jobqueue: Job "Convert to DIVX" Finished: Finished "Convert to DIVX" for "5 HBO (5)" recorded from channel 1050 at Sat Sep 22 14:19:00 2007.
2007-09-22 14:26:45.866 MainServer::HandleAnnounce Monitor
2007-09-22 14:26:45.869 adding: e6300 as a client (events: 0)
2007-09-22 14:26:49.585 MainServer::HandleAnnounce Monitor
2007-09-22 14:26:49.589 adding: e6300 as a client (events: 0)
2007-09-22 14:26:56.315 MainServer::HandleAnnounce Monitor
2007-09-22 14:26:56.317 adding: e6300 as a client (events: 0)
2007-09-22 14:33:39.491 MainServer::HandleAnnounce Monitor
2007-09-22 14:33:39.504 adding: e6300 as a client (events: 0)
2007-09-22 14:33:45.034 MainServer::HandleAnnounce Monitor
2007-09-22 14:33:45.035 adding: e6300 as a client (events: 0)
2007-09-22 14:33:56.399 MainServer::HandleAnnounce Monitor
2007-09-22 14:33:56.400 adding: e6300 as a client (events: 0)
2007-09-22 14:33:58.611 MainServer::HandleAnnounce Monitor
2007-09-22 14:33:58.614 adding: e6300 as a client (events: 0)
2007-09-22 14:34:00.744 MainServer::HandleAnnounce Monitor
2007-09-22 14:34:00.747 adding: e6300 as a client (events: 0)
2007-09-22 14:34:04.264 MainServer::HandleAnnounce Monitor
2007-09-22 14:34:04.266 adding: e6300 as a client (events: 0)
2007-09-22 14:34:38.227 MainServer::HandleAnnounce Monitor
2007-09-22 14:34:38.228 adding: e6300 as a client (events: 0)
2007-09-22 14:34:41.170 MainServer::HandleAnnounce Monitor
2007-09-22 14:34:41.187 adding: e6300 as a client (events: 0)
2007-09-22 14:34:46.523 MainServer::HandleAnnounce Monitor
2007-09-22 14:34:46.525 adding: e6300 as a client (events: 0)
2007-09-22 14:34:58.917 MainServer::HandleAnnounce Monitor
2007-09-22 14:34:58.918 adding: e6300 as a client (events: 0)
2007-09-22 14:34:58.936 Reschedule requested for id 369.
2007-09-22 14:34:58.994 Scheduled 6 items in 0.1 = 0.05 match + 0.01 place
2007-09-22 14:34:58.997 scheduler: Scheduled items: Scheduled 6 items in 0.1 = 0.05 match + 0.01 place
2007-09-22 14:35:01.675 MainServer::HandleAnnounce Monitor
2007-09-22 14:35:01.682 adding: e6300 as a client [/PHP]

Can someone help me decipher this and fix what looks like to be an error on nuvexport -divx?

---

### Post by jba6511 on 2007-09-23
working on it for awhile and still got nowhere. Anyone???

---

### Post by jba6511 on 2007-09-25
seems I am missing HiRes::Time. Does anyone know how to install this? I tried using cpan but it fails on installation?

---

