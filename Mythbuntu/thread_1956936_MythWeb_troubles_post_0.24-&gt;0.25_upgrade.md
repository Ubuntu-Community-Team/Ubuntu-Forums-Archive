---
title: "MythWeb troubles post 0.24-&gt;0.25 upgrade"
date: 2012-04-11
forum: Mythbuntu
---

### Post by lionsnob on 2012-04-11
Hi all -

The upgrade went well except for MythWeb.  It's really slow for upcoming recordings and recorded programs.  The browser will act like it's loading the page for about 20 minutes before it finally appears.  For recorded programs, anything recorded after the upgrade has a "broken image" thumbnail.  When I click on status, after about an hour I get:

```
Warning at /usr/share/mythtv/mythweb/modules/status/handler.php, line 32:
!!NoTrans: file_get_contents(http://192.168.0.179:6544/Status/GetStatusHTML): failed to open stream: HTTP request failed! !!
```

My setup is a master backend with one HD-PVR and two HDHomeRuns,  I also have a secondary backend with an HD-PVR.  The entire setup is working fine except for MythWeb (which I really like to use).  My version of MythWeb is 2:0.25.0+fixes.20120410.1f5962a from the daily builds.

Contents of tail -n 100 /var/log/mythtv/mythbackend.log from the master backend are:

```
Apr 11 20:29:59 mythdish mythbackend[2486]: I Scheduler scheduler.cpp:2459 (HandleRecordingStatusChange) Tuning recording: Suburgatory:"Down Time": channel 1071 on cardid 10, sourceid 1
Apr 11 20:30:00 mythdish mythbackend[2486]: I CoreContext scheduler.cpp:634 (UpdateRecStatus) Updating status for "Betty White's Off Their Rockers" on cardid 10 (Recording => Recorded)
Apr 11 20:30:00 mythdish mythbackend[2486]: E CoreContext mainserver.cpp:871 (customEvent) MainServer: PREVIEW_SUCCESS but no receivers.
Apr 11 20:30:00 mythdish mythbackend[2486]: I CoreContext scheduler.cpp:634 (UpdateRecStatus) Updating status for "Best Friends Forever":"The Butt Dial" on cardid 12 (Tuning => Recording)
Apr 11 20:30:00 mythdish mythbackend[2486]: I TVRecEvent tv_rec.cpp:1014 (HandleStateChange) TVRec(9): Changing from RecordingOnly to None
Apr 11 20:30:00 mythdish mythbackend[2486]: I CoreContext scheduler.cpp:634 (UpdateRecStatus) Updating status for Suburgatory:"Down Time" on cardid 10 (Tuning => Recording)
Apr 11 20:30:01 mythdish mythbackend[2486]: I TVRecEvent tv_rec.cpp:3950 (TuningNewRecorder) TVRec(12): rec->GetPathname(): '/recordings1/1041_20120411203000.mpg'
Apr 11 20:30:01 mythdish mythbackend[2486]: I TVRecEvent tv_rec.cpp:3950 (TuningNewRecorder) TVRec(10): rec->GetPathname(): '/recordings2/1071_20120411203000.mpg'
Apr 11 20:30:01 mythdish mythbackend[2486]: E TVRecEvent recorderbase.cpp:164 (SetStrOption) RecBase(12:10324852-1): SetStrOption(...recordingtype): Option not in profile.
Apr 11 20:30:01 mythdish mythbackend[2486]: E TVRecEvent recorderbase.cpp:164 (SetStrOption) RecBase(10:10324852-0): SetStrOption(...recordingtype): Option not in profile.
Apr 11 20:30:01 mythdish mythbackend[2486]: I Scheduler scheduler.cpp:2010 (HandleReschedule) Reschedule requested for id 0.
Apr 11 20:30:01 mythdish mythbackend[2486]: E RecThread mpegrecorder.cpp:1017 (run) MPEGRec(/dev/video0): Device EOF detected
Apr 11 20:30:04 mythdish mythbackend[2486]: I CoreContext scheduler.cpp:634 (UpdateRecStatus) Updating status for "SpongeBob SquarePants":Squiditis on cardid 9 (Recording => Recorded)
Apr 11 20:30:04 mythdish mythbackend[2486]: I TVRecEvent recordinginfo.cpp:1113 (FinishedRecording) Finished recording SpongeBob SquarePants "Squiditis": channel 3300
Apr 11 20:30:09 mythdish mythbackend[2486]: E CoreContext mainserver.cpp:871 (customEvent) MainServer: PREVIEW_SUCCESS but no receivers.
Apr 11 20:30:09 mythdish mythbackend[2486]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
Apr 11 20:30:09 mythdish mythbackend[2486]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: mythdish as a client (events: 0)
Apr 11 20:30:09 mythdish mythbackend[2486]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
Apr 11 20:30:09 mythdish mythbackend[2486]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: mythdish as a client (events: 1)
Apr 11 20:30:09 mythdish mythbackend[2486]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
Apr 11 20:30:09 mythdish mythbackend[2486]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: mythdish as a client (events: 0)
Apr 11 20:30:09 mythdish mythbackend[2486]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
Apr 11 20:30:09 mythdish mythbackend[2486]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: mythdish as a client (events: 1)
Apr 11 20:30:10 mythdish mythbackend[2486]: I Scheduler scheduler.cpp:2057 (HandleReschedule) Reschedule interrupted, will retry
Apr 11 20:30:10 mythdish mythbackend[2486]: I Scheduler scheduler.cpp:2010 (HandleReschedule) Reschedule requested for id 0.
Apr 11 20:30:10 mythdish mythbackend[2486]: I Scheduler scheduler.cpp:2010 (HandleReschedule) Reschedule requested for id 0.
Apr 11 20:30:17 mythdish mythbackend[2486]: I Scheduler scheduler.cpp:2068 (HandleReschedule) Scheduled 1184 items in 6.0 = 0.00 match + 6.04 place
Apr 11 20:32:12 mythdish mythbackend[2486]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
Apr 11 20:32:50 mythdish mythbackend[2486]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 7 min
Apr 11 20:34:51 mythdish mythbackend[2300]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
Apr 11 20:37:16 mythdish mythbackend[2486]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
Apr 11 20:39:26 mythdish mythbackend[2486]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
Apr 11 20:39:26 mythdish mythbackend[2486]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: mythdish as a client (events: 0)
Apr 11 20:39:26 mythdish mythbackend[2486]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
Apr 11 20:39:26 mythdish mythbackend[2486]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: mythdish as a client (events: 1)
Apr 11 20:39:36 mythdish mythbackend[2486]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
Apr 11 20:39:36 mythdish mythbackend[2486]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: mythdish as a client (events: 0)
Apr 11 20:39:36 mythdish mythbackend[2486]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
Apr 11 20:39:36 mythdish mythbackend[2486]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: mythdish as a client (events: 1)
Apr 11 20:39:58 mythdish mythbackend[2300]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
Apr 11 20:40:50 mythdish mythbackend[2486]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 7 min
Apr 11 20:42:16 mythdish mythbackend[2486]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
Apr 11 20:43:29 mythdish mythbackend[2300]: E Expire autoexpire.cpp:161 (CalcParams) AutoExpire: Filesystem Info cache is empty, unable to calculate necessary parameters.
Apr 11 20:43:29 mythdish mythbackend[2300]: E Expire autoexpire.cpp:421 (ExpireRecordings) AutoExpire: Filesystem Info cache is empty, unable to determine what Recordings to expire
Apr 11 20:43:50 mythdish mythbackend[2486]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Playback
Apr 11 20:43:50 mythdish mythbackend[2486]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: bedroom1110 as a client (events: 0)
Apr 11 20:43:50 mythdish mythbackend[2486]: I ProcessRequest mainserver.cpp:1475 (HandleAnnounce) MainServer::HandleAnnounce FileTransfer
Apr 11 20:43:50 mythdish mythbackend[2486]: I ProcessRequest mainserver.cpp:1477 (HandleAnnounce) adding: bedroom1110 as a remote file transfer
Apr 11 20:43:54 mythdish mythbackend[2486]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
Apr 11 20:43:54 mythdish mythbackend[2486]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: mythdish as a client (events: 0)
Apr 11 20:43:54 mythdish mythbackend[2486]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
Apr 11 20:43:54 mythdish mythbackend[2486]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: mythdish as a client (events: 1)
Apr 11 20:45:05 mythdish mythbackend[2300]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
Apr 11 20:47:19 mythdish mythbackend[2486]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
Apr 11 20:47:50 mythdish mythbackend[2486]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 7 min
Apr 11 20:50:05 mythdish mythbackend[2300]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
Apr 11 20:52:25 mythdish mythbackend[2486]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
Apr 11 20:54:50 mythdish mythbackend[2486]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 7 min
Apr 11 20:55:09 mythdish mythbackend[2300]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
Apr 11 20:57:30 mythdish mythbackend[2486]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
Apr 11 20:58:29 mythdish mythbackend[2300]: E Expire autoexpire.cpp:161 (CalcParams) AutoExpire: Filesystem Info cache is empty, unable to calculate necessary parameters.
Apr 11 20:58:29 mythdish mythbackend[2300]: E Expire autoexpire.cpp:421 (ExpireRecordings) AutoExpire: Filesystem Info cache is empty, unable to determine what Recordings to expire
Apr 11 20:59:33 mythdish mythbackend[2486]: I TVRecEvent tv_rec.cpp:1518 (HandlePendingRecordings) TVRec(12): ASK_RECORDING 12 26 0 0
Apr 11 20:59:33 mythdish mythbackend[2486]: I TVRecEvent tv_rec.cpp:1518 (HandlePendingRecordings) TVRec(10): ASK_RECORDING 10 27 0 0
Apr 11 20:59:59 mythdish mythbackend[2486]: E CoreContext mainserver.cpp:871 (customEvent) MainServer: PREVIEW_SUCCESS but no receivers.
Apr 11 21:00:01 mythdish mythbackend[2486]: W Scheduler ThreadedFileWriter.cpp:301 (Flush) TFW(/recordings2/1071_20120411203000.mpg:56): Taking a long time to flush.. buffer size 115056
Apr 11 21:00:03 mythdish mythbackend[2486]: W Scheduler ThreadedFileWriter.cpp:301 (Flush) TFW(/recordings2/1071_20120411203000.mpg:56): Taking a long time to flush.. buffer size 0
Apr 11 21:00:03 mythdish mythbackend[2486]: N Scheduler autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 7 min
Apr 11 21:00:03 mythdish mythbackend[2486]: I Scheduler scheduler.cpp:2459 (HandleRecordingStatusChange) Started recording: "Modern Family":"Election Day": channel 1071 on cardid 10, sourceid 1
Apr 11 21:00:03 mythdish mythbackend[2486]: I TVRecEvent tv_rec.cpp:1014 (HandleStateChange) TVRec(12): Changing from RecordingOnly to None
Apr 11 21:00:03 mythdish mythbackend[2486]: I HDHRStreamHandler tv_rec.cpp:3253 (RingBufferChanged) TVRec(10): RingBufferChanged()
Apr 11 21:00:03 mythdish mythbackend[2486]: I TVRecEvent recordinginfo.cpp:1113 (FinishedRecording) Finished recording Best Friends Forever "The Butt Dial": channel 1041
Apr 11 21:00:03 mythdish mythbackend[2486]: I HDHRStreamHandler recordinginfo.cpp:1113 (FinishedRecording) Finished recording Suburgatory "Down Time": channel 1071
Apr 11 21:00:03 mythdish mythbackend[2486]: I TVRecEvent tv_rec.cpp:1014 (HandleStateChange) TVRec(12): Changing from None to RecordingOnly
Apr 11 21:00:03 mythdish mythbackend[2486]: I TVRecEvent tv_rec.cpp:3456 (TuningCheckForHWChange) TVRec(12): HW Tuner: 12->12
Apr 11 21:00:04 mythdish mythbackend[2486]: N Scheduler autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 7 min
Apr 11 21:00:04 mythdish mythbackend[2486]: I Scheduler scheduler.cpp:2459 (HandleRecordingStatusChange) Tuning recording: NOVA:"Deadliest Tornadoes": channel 1561 on cardid 12, sourceid 1
Apr 11 21:00:04 mythdish mythbackend[2486]: I CoreContext scheduler.cpp:634 (UpdateRecStatus) Updating status for "Best Friends Forever":"The Butt Dial" on cardid 12 (Recording => Recorded)
Apr 11 21:00:04 mythdish mythbackend[2486]: I CoreContext scheduler.cpp:634 (UpdateRecStatus) Updating status for Suburgatory:"Down Time" on cardid 10 (Recording => Recorded)
Apr 11 21:00:04 mythdish mythbackend[2486]: E CoreContext mainserver.cpp:871 (customEvent) MainServer: PREVIEW_SUCCESS but no receivers.
Apr 11 21:00:04 mythdish mythbackend[2486]: E CoreContext mainserver.cpp:871 (customEvent) MainServer: PREVIEW_SUCCESS but no receivers.
Apr 11 21:00:04 mythdish mythbackend[2486]: I CoreContext scheduler.cpp:634 (UpdateRecStatus) Updating status for NOVA:"Deadliest Tornadoes" on cardid 12 (Tuning => Recording)
Apr 11 21:00:04 mythdish mythbackend[2486]: I TVRecEvent tv_rec.cpp:3950 (TuningNewRecorder) TVRec(12): rec->GetPathname(): '/recordings2/1561_20120411210000.mpg'
Apr 11 21:00:04 mythdish mythbackend[2486]: E TVRecEvent recorderbase.cpp:164 (SetStrOption) RecBase(12:10324852-1): SetStrOption(...recordingtype): Option not in profile.
Apr 11 21:00:05 mythdish mythbackend[2486]: I Scheduler scheduler.cpp:2010 (HandleReschedule) Reschedule requested for id 0.
Apr 11 21:00:05 mythdish mythbackend[2486]: I Scheduler scheduler.cpp:2010 (HandleReschedule) Reschedule requested for id 0.
Apr 11 21:00:13 mythdish mythbackend[2486]: I Scheduler scheduler.cpp:2068 (HandleReschedule) Scheduled 1180 items in 8.1 = 0.00 match + 8.08 place
Apr 11 21:00:16 mythdish mythbackend[2300]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
Apr 11 21:02:35 mythdish mythbackend[2486]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
Apr 11 21:02:50 mythdish mythbackend[2486]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 7 min
Apr 11 21:05:17 mythdish mythbackend[2300]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
Apr 11 21:07:39 mythdish mythbackend[2486]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
Apr 11 21:09:50 mythdish mythbackend[2486]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 7 min
Apr 11 21:10:24 mythdish mythbackend[2300]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
Apr 11 21:12:46 mythdish mythbackend[2486]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
Apr 11 21:13:29 mythdish mythbackend[2300]: E Expire autoexpire.cpp:161 (CalcParams) AutoExpire: Filesystem Info cache is empty, unable to calculate necessary parameters.
Apr 11 21:13:29 mythdish mythbackend[2300]: E Expire autoexpire.cpp:421 (ExpireRecordings) AutoExpire: Filesystem Info cache is empty, unable to determine what Recordings to expire
Apr 11 21:15:27 mythdish mythbackend[2300]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
Apr 11 21:16:50 mythdish mythbackend[2486]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 7 min
Apr 11 21:17:53 mythdish mythbackend[2486]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
```

Any ideas?
Thanks!
Steve

---

### Post by lionsnob on 2012-04-12
Some more info:
I can connect to the secondary backend's status page, in my case [http://192.168.0.143:6544/](http://192.168.0.143:6544/), but still not the master backend's status page ([http://192.168.0.179:6544/](http://192.168.0.179:6544/)).  I suspect if I can get this to work then the other MythWeb issues will clear up.

---

### Post by tgm4883 on 2012-04-12
Check /etc/apache2/sites-enabled/mythweb.conf and verify that the mysql info is correct (see below) 


```
            setenv db_server        "REDACTED"
            setenv db_name          "mythconverg"
            setenv db_login         "mythtv"
            setenv db_password      "REDACTED"
```

---

### Post by lionsnob on 2012-04-12
Thanks tgm4883,

The pertinent part of the file looks like:

```
            setenv db_server        "localhost"
            setenv db_name          "mythconverg"
            setenv db_login         "mythtv"
            setenv db_password      "redacted"
```

should it not be localhost and instead be the actual IP of the server?

---

### Post by tgm4883 on 2012-04-13
> **lionsnob said:**
> Thanks tgm4883,

The pertinent part of the file looks like:

```
            setenv db_server        "localhost"
            setenv db_name          "mythconverg"
            setenv db_login         "mythtv"
            setenv db_password      "redacted"
```

should it not be localhost and instead be the actual IP of the server?

localhost should be fine as long as the mysql server is on the same box (which you would have had to manually do some changes to move it elsewhere).

Is there anything in the apache error log?

---

### Post by lionsnob on 2012-04-13
There's one line, but I've been attempting to access the status page more than just once and certainly since Wednesday:

```
[Wed Apr 11 13:05:12 2012] [notice] Graceful restart requested, doing restart
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Wed Apr 11 13:05:12 2012] [notice] Digest: generating secret for digest authentication ...
[Wed Apr 11 13:05:12 2012] [notice] Digest: done
[Wed Apr 11 13:05:13 2012] [notice] Apache/2.2.20 (Ubuntu) PHP/5.3.6-13ubuntu3.6 with Suhosin-Patch configured -- resuming normal operations
[Wed Apr 11 13:08:40 2012] [notice] caught SIGTERM, shutting down
[Wed Apr 11 13:11:18 2012] [notice] Digest: generating secret for digest authentication ...
[Wed Apr 11 13:11:18 2012] [notice] Digest: done
[Wed Apr 11 13:11:20 2012] [notice] Apache/2.2.20 (Ubuntu) PHP/5.3.6-13ubuntu3.6 with Suhosin-Patch configured -- resuming normal operations
[Wed Apr 11 17:52:21 2012] [notice] Graceful restart requested, doing restart
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Wed Apr 11 17:52:21 2012] [notice] Digest: generating secret for digest authentication ...
[Wed Apr 11 17:52:21 2012] [notice] Digest: done
[Wed Apr 11 17:52:22 2012] [notice] Apache/2.2.20 (Ubuntu) PHP/5.3.6-13ubuntu3.6 with Suhosin-Patch configured -- resuming normal operations
[Wed Apr 11 17:52:58 2012] [notice] Graceful restart requested, doing restart
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Wed Apr 11 17:52:58 2012] [notice] Digest: generating secret for digest authentication ...
[Wed Apr 11 17:52:58 2012] [notice] Digest: done
[Wed Apr 11 17:52:58 2012] [notice] Apache/2.2.20 (Ubuntu) PHP/5.3.6-13ubuntu3.6 with Suhosin-Patch configured -- resuming normal operations
[Wed Apr 11 17:59:59 2012] [error] [client 24.192.12.160] PHP Fatal error:  require(): Failed opening required 'modules/tv/tmpl/default/upcoming.php' (include_path='/usr/local/share/mythtv/bindings/php/:/usr/share/mythtv/bindings/php/:.:/usr/share/php:/usr/share/pear:/usr/share/mythtv/mythweb/modules/tv') in /usr/share/mythtv/mythweb/modules/tv/upcoming.php on line 149, referer: http://the-harringtons.org:808/mythweb/status
[Wed Apr 11 20:09:18 2012] [notice] Graceful restart requested, doing restart
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Wed Apr 11 20:09:18 2012] [notice] Digest: generating secret for digest authentication ...
[Wed Apr 11 20:09:18 2012] [notice] Digest: done
[Wed Apr 11 20:09:18 2012] [notice] Apache/2.2.20 (Ubuntu) PHP/5.3.6-13ubuntu3.6 with Suhosin-Patch configured -- resuming normal operations
[Thu Apr 12 16:34:16 2012] [notice] Graceful restart requested, doing restart
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Thu Apr 12 16:34:16 2012] [notice] Digest: generating secret for digest authentication ...
[Thu Apr 12 16:34:16 2012] [notice] Digest: done
[Thu Apr 12 16:34:17 2012] [notice] Apache/2.2.20 (Ubuntu) PHP/5.3.6-13ubuntu3.6 with Suhosin-Patch configured -- resuming normal operations

```

---

### Post by tgm4883 on 2012-04-13
> **lionsnob said:**
> There's one line, but I've been attempting to access the status page more than just once and certainly since Wednesday:

```
[Wed Apr 11 13:05:12 2012] [notice] Graceful restart requested, doing restart
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Wed Apr 11 13:05:12 2012] [notice] Digest: generating secret for digest authentication ...
[Wed Apr 11 13:05:12 2012] [notice] Digest: done
[Wed Apr 11 13:05:13 2012] [notice] Apache/2.2.20 (Ubuntu) PHP/5.3.6-13ubuntu3.6 with Suhosin-Patch configured -- resuming normal operations
[Wed Apr 11 13:08:40 2012] [notice] caught SIGTERM, shutting down
[Wed Apr 11 13:11:18 2012] [notice] Digest: generating secret for digest authentication ...
[Wed Apr 11 13:11:18 2012] [notice] Digest: done
[Wed Apr 11 13:11:20 2012] [notice] Apache/2.2.20 (Ubuntu) PHP/5.3.6-13ubuntu3.6 with Suhosin-Patch configured -- resuming normal operations
[Wed Apr 11 17:52:21 2012] [notice] Graceful restart requested, doing restart
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Wed Apr 11 17:52:21 2012] [notice] Digest: generating secret for digest authentication ...
[Wed Apr 11 17:52:21 2012] [notice] Digest: done
[Wed Apr 11 17:52:22 2012] [notice] Apache/2.2.20 (Ubuntu) PHP/5.3.6-13ubuntu3.6 with Suhosin-Patch configured -- resuming normal operations
[Wed Apr 11 17:52:58 2012] [notice] Graceful restart requested, doing restart
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Wed Apr 11 17:52:58 2012] [notice] Digest: generating secret for digest authentication ...
[Wed Apr 11 17:52:58 2012] [notice] Digest: done
[Wed Apr 11 17:52:58 2012] [notice] Apache/2.2.20 (Ubuntu) PHP/5.3.6-13ubuntu3.6 with Suhosin-Patch configured -- resuming normal operations
[Wed Apr 11 17:59:59 2012] [error] [client 24.192.12.160] PHP Fatal error:  require(): Failed opening required 'modules/tv/tmpl/default/upcoming.php' (include_path='/usr/local/share/mythtv/bindings/php/:/usr/share/mythtv/bindings/php/:.:/usr/share/php:/usr/share/pear:/usr/share/mythtv/mythweb/modules/tv') in /usr/share/mythtv/mythweb/modules/tv/upcoming.php on line 149, referer: http://the-harringtons.org:808/mythweb/status
[Wed Apr 11 20:09:18 2012] [notice] Graceful restart requested, doing restart
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Wed Apr 11 20:09:18 2012] [notice] Digest: generating secret for digest authentication ...
[Wed Apr 11 20:09:18 2012] [notice] Digest: done
[Wed Apr 11 20:09:18 2012] [notice] Apache/2.2.20 (Ubuntu) PHP/5.3.6-13ubuntu3.6 with Suhosin-Patch configured -- resuming normal operations
[Thu Apr 12 16:34:16 2012] [notice] Graceful restart requested, doing restart
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Thu Apr 12 16:34:16 2012] [notice] Digest: generating secret for digest authentication ...
[Thu Apr 12 16:34:16 2012] [notice] Digest: done
[Thu Apr 12 16:34:17 2012] [notice] Apache/2.2.20 (Ubuntu) PHP/5.3.6-13ubuntu3.6 with Suhosin-Patch configured -- resuming normal operations

```

It looks like you may have tried to compile MythTV by hand previously and that it may be conflicting with the upgrade. Looking at the following code snippet you posted

```
[Wed Apr 11 17:59:59 2012] [error] [client 24.192.12.160] PHP Fatal error:  require(): Failed opening required 'modules/tv/tmpl/default/upcoming.php' (include_path='/usr/local/share/mythtv/bindings/php/:/usr/share/mythtv/bindings/php/:.:/usr/share/php:/usr/share/pear:/usr/share/mythtv/mythweb/modules/tv') in /usr/share/mythtv/mythweb/modules/tv/upcoming.php on line 149, referer: http://the-harringtons.org:808/mythweb/status

```

We don't install to /usr/local/share/mythtv.

---

### Post by lionsnob on 2012-04-13
Interesting.  I've only ever installed by packages.  Before I upgraded to 0.25 I used the Avenard packages.  I'll try a purge of mythtv-backend and see if that helps.  Total stabs in the dark at this point :)

---

### Post by lionsnob on 2012-04-13
The purge and reinstall did not work.

Also, does the MythTV status page even use Apache?  I thought one connected directly to the backend when using port 6544?  If that's the case, then the Apache logs should not matter.

---

### Post by scatat on 2012-04-15
Hi - I had a similar problem and realised that Mythbackend was in fact in a state - lots of open connections to port 6544 and restarting mythbackend didn't work - ie there was a total lock-up. 

I had to "pkill -9 mythbackend" in order to kill mythbackend. Once this was done and mythbackend restarted, mythweb worked fine. Hope this helps.

---

### Post by lionsnob on 2012-04-15
> **scatat said:**
> Hi - I had a similar problem and realised that Mythbackend was in fact in a state - lots of open connections to port 6544 and restarting mythbackend didn't work - ie there was a total lock-up. 

I had to "pkill -9 mythbackend" in order to kill mythbackend. Once this was done and mythbackend restarted, mythweb worked fine. Hope this helps.

Thanks!  That seems to have worked.  What was trying to connect to 6544 so much in your case?

Assuming it still works tomorrow I'll marked this as solved then.

---

### Post by billstei on 2012-06-08
I had a complete computer lock-up around the time a scheduled recording was supposed to start, and after wrestling with mythweb and getting very slow responses, I did a "sudo pkill -9 mythbackend" and now mythweb is back to normal and scheduled recordings are working.  I am not sure if the original lockup is the same problem or a different one.  Am running mythtv 0.25.0+fixes on Ubuntu 12.04 Precise.

---

### Post by l3ill on 2012-06-09
Same issue with my Mythweb - recently upgraded to 12.04 (64bit) - (Orig [mythbuntu] install was Maverick some years ago) - and I believe that gives MythTv .25.

All seems fine with mythtv - however, mythweb is misbehaving in a similar manner to previous descriptions. 

I can access most parts of mythweb - but the main things I do: check "Upcoming recordings" and "Backend Status" - without these, I'm kinda blind to current and soon-to-be-current activity - immediately after a reboot - and for several hours these functions seem to work properly - then for some reason (?) they stop working - only headers displayed and no results/info - and they return the same kind of PHP error messages described in previous posts.

I tried the "sudo pkill -9 mythbackend" and that seems to have "worked" - ie. I can now use the Upcoming recordings and Backedn STatus functions normally.

Thank you for the info on how to rectify the issue - VERY useful - however, I'm left wondering what causes it in the first place??? Is there anything I can do or provide to assist in diagnosis of a root cause here?

Cheers ... Bill

---

### Post by billstei on 2012-06-09
I checked the mythbackend log file (here: /var/log/mythtv/mythbackend.log) and my initial failed recording was due to a Permission denied (13) error when trying to save the file to a folder that did not have the correct permissions.  The question is (perhaps) whether the trouble that the mythbackend was having caused mythweb to hang waiting for it to respond, or was mythweb also having trouble generating thumbnail snapshots of that recording in that same folder (is there a way to stop mythweb from generating them in that location?), either because of the same permission problem, or because the recording file itself was not actually there?  Whatever the cause, multiple mythbackend processes were present as per "ps ax | grep mythbackend", and hence the "fix" of killing all of them.

---

### Post by dannyboy79 on 2013-04-17
> **tgm4883 said:**
> It looks like you may have tried to compile MythTV by hand previously and that it may be conflicting with the upgrade. Looking at the following code snippet you posted

```
[Wed Apr 11 17:59:59 2012] [error] [client 24.192.12.160] PHP Fatal error:  require(): Failed opening required 'modules/tv/tmpl/default/upcoming.php' (include_path='/usr/local/share/mythtv/bindings/php/:/usr/share/mythtv/bindings/php/:.:/usr/share/php:/usr/share/pear:/usr/share/mythtv/mythweb/modules/tv') in /usr/share/mythtv/mythweb/modules/tv/upcoming.php on line 149, referer: http://the-harringtons.org:808/mythweb/status

```

We don't install to /usr/local/share/mythtv.i am having this same issue and I never tried to compile mythtv at all, i am using mythbuntu 0.26+fixes. Can you please help?

---

### Post by tgm4883 on 2013-04-18
Please open a new thread if the thread you want to post to is over 6 months old (from the last post)

---

