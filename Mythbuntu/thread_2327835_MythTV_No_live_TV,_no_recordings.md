---
title: "MythTV No live TV, no recordings"
date: 2016-06-14
forum: Mythbuntu
---

### Post by cjgump720 on 2016-06-14
I have a combined frontend/backend HTPC running Ubuntu with MythTV that has been running great for a while now even though I am still very new to Linux/Ubuntu/MythTV.  Last Saturday I rebooted to finish installing some updates, and now MythTV won't show live TV, and all my scheduled recordings are failing.  I checked the HDHomerun tuner with the SiliconDust setup GUI, and it is clearly sending the TV signal to the computer.

Searching the forums suggested that the problem could be the directory permissions.  I'm not sure that an update could have messed with them, but I took a look.  The MythTV directory was owned by root and in the root group.  The LiveTV directory did not have a owner listed, but is in the MythTV group. In a last ditch effort, I changed the read and write permissions: 

```
drwxrwsrwx  2 mythtv mythtv 12288 Jun 14 20:28 banners
drwxrwsrwx  2 mythtv mythtv 12288 Jun 14 20:28 coverart
drwxrwsrwx  2 mythtv mythtv  4096 Jun 14 20:28 db_backups
drwxrwsrwx  2 mythtv mythtv 12288 Jun 14 20:28 fanart
drwxrwsrwx  2 mythtv mythtv  4096 Jun 14 20:28 livetv
drwxrwsrwx  2 mythtv mythtv 20480 Jun 14 20:28 recordings
drwxrwsrwx  2 mythtv mythtv 36864 Jun 14 20:28 screenshots
drwxrwsrwx  2 mythtv mythtv  4096 Jun 14 20:28 streaming
drwxrwsrwx  2 mythtv mythtv  4096 Jun 14 20:28 trailers
drwxrwsrwx 23 mythtv mythtv  4096 Jun 14 20:28 videos
```

Still no luck.  I tried wading through the frontend and backend logs, but I don't really know what to look for in them.  The section that jumped out at me as being different in the backend log was this:

```
Jun 14 17:58:01 chris-TA75M mythfrontend.real: mythfrontend[3868]: I CoreContext mythdbcon.cpp:409 (PurgeIdleConnections) New DB connection, total: 4
Jun 14 17:58:01 chris-TA75M mythfrontend.real: mythfrontend[3868]: I PlaybackBoxHelper mythdbcon.cpp:409 (PurgeIdleConnections) New DB connection, total: 4
Jun 14 17:58:02 chris-TA75M mythfrontend.real: mythfrontend[3868]: E PlaybackBoxHelper programinfo.cpp:2358 (GetPlaybackURL) ProgramInfo(1311_20160614235800.mpg): GetPlaybackURL: '1311_20160614235800.mpg' should be local, but it can not be found.
Jun 14 17:58:02 chris-TA75M mythfrontend.real: mythfrontend[3868]: E PlaybackBoxHelper playbackboxhelper.cpp:88 (CheckAvailability) PlaybackBoxHelper: CHECK_AVAILABILITY 'GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/chris-TA75M/1311_20160614235800.mpg' file not found
Jun 14 17:58:02 chris-TA75M mythfrontend.real: mythfrontend[3868]: E PlaybackBoxHelper programinfo.cpp:2358 (GetPlaybackURL) ProgramInfo(1311_20160614235800.mpg): GetPlaybackURL: '1311_20160614235800.mpg' should be local, but it can not be found.
Jun 14 17:58:02 chris-TA75M mythfrontend.real: mythfrontend[3868]: E PlaybackBoxHelper playbackboxhelper.cpp:88 (CheckAvailability) PlaybackBoxHelper: CHECK_AVAILABILITY 'GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/chris-TA75M/1311_20160614235800.mpg' file not found
Jun 14 17:58:02 chris-TA75M mythfrontend.real: mythfrontend[3868]: I PreviewGeneratorQueue mythdbcon.cpp:409 (PurgeIdleConnections) New DB connection, total: 4
Jun 14 17:58:02 chris-TA75M mythfrontend.real: mythfrontend[3868]: E PlaybackBoxHelper programinfo.cpp:2358 (GetPlaybackURL) ProgramInfo(1311_20160614235800.mpg): GetPlaybackURL: '1311_20160614235800.mpg' should be local, but it can not be found.
Jun 14 17:58:02 chris-TA75M mythfrontend.real: mythfrontend[3868]: E PlaybackBoxHelper playbackboxhelper.cpp:88 (CheckAvailability) PlaybackBoxHelper: CHECK_AVAILABILITY 'GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/chris-TA75M/1311_20160614235800.mpg' file not found
Jun 14 17:58:02 chris-TA75M mythfrontend.real: mythfrontend[3868]: E PlaybackBoxHelper programinfo.cpp:2358 (GetPlaybackURL) ProgramInfo(1311_20160614235800.mpg): GetPlaybackURL: '1311_20160614235800.mpg' should be local, but it can not be found.
Jun 14 17:58:02 chris-TA75M mythfrontend.real: mythfrontend[3868]: E PlaybackBoxHelper playbackboxhelper.cpp:88 (CheckAvailability) PlaybackBoxHelper: CHECK_AVAILABILITY 'GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/chris-TA75M/1311_20160614235800.mpg' file not found
Jun 14 17:58:02 chris-TA75M mythfrontend.real: mythfrontend[3868]: E PlaybackBoxHelper programinfo.cpp:2358 (GetPlaybackURL) ProgramInfo(1311_20160614235800.mpg): GetPlaybackURL: '1311_20160614235800.mpg' should be local, but it can not be found.
Jun 14 17:58:02 chris-TA75M mythfrontend.real: mythfrontend[3868]: E PlaybackBoxHelper playbackboxhelper.cpp:88 (CheckAvailability) PlaybackBoxHelper: CHECK_AVAILABILITY 'GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/chris-TA75M/1311_20160614235800.mpg' file not found
Jun 14 17:58:02 chris-TA75M mythfrontend.real: mythfrontend[3868]: E PlaybackBoxHelper programinfo.cpp:2358 (GetPlaybackURL) ProgramInfo(1311_20160614235801.mpg): GetPlaybackURL: '1311_20160614235801.mpg' should be local, but it can not be found.
Jun 14 17:58:02 chris-TA75M mythfrontend.real: mythfrontend[3868]: E PlaybackBoxHelper playbackboxhelper.cpp:88 (CheckAvailability) PlaybackBoxHelper: CHECK_AVAILABILITY 'GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/chris-TA75M/1311_20160614235801.mpg' file not found
Jun 14 17:58:02 chris-TA75M mythfrontend.real: mythfrontend[3868]: E PlaybackBoxHelper programinfo.cpp:2358 (GetPlaybackURL) ProgramInfo(1311_20160614235801.mpg): GetPlaybackURL: '1311_20160614235801.mpg' should be local, but it can not be found.
Jun 14 17:58:02 chris-TA75M mythfrontend.real: mythfrontend[3868]: E PlaybackBoxHelper playbackboxhelper.cpp:88 (CheckAvailability) PlaybackBoxHelper: CHECK_AVAILABILITY 'GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/chris-TA75M/1311_20160614235801.mpg' file not found
Jun 14 17:58:02 chris-TA75M mythfrontend.real: mythfrontend[3868]: E PlaybackBoxHelper programinfo.cpp:2358 (GetPlaybackURL) ProgramInfo(1311_20160614235801.mpg): GetPlaybackURL: '1311_20160614235801.mpg' should be local, but it can not be found.
Jun 14 17:58:02 chris-TA75M mythfrontend.real: mythfrontend[3868]: E PlaybackBoxHelper playbackboxhelper.cpp:88 (CheckAvailability) PlaybackBoxHelper: CHECK_AVAILABILITY 'GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/chris-TA75M/1311_20160614235801.mpg' file not found
Jun 14 18:02:41 chris-TA75M mythfrontend.real: mythfrontend[3868]: I CoreContext tv_play.cpp:1058 (TV) TV: Creating TV object
Jun 14 18:02:41 chris-TA75M mythfrontend.real: mythfrontend[3868]: N CoreContext mythmainwindow.cpp:2638 (PauseIdleTimer) Suspending idle timer
Jun 14 18:02:41 chris-TA75M mythfrontend.real: mythfrontend[3868]: I CoreContext tv_play.cpp:1275 (Init) TV: Created TvPlayWindow.
Jun 14 18:02:41 chris-TA75M mythfrontend.real: mythfrontend[3868]: I CoreContext tv_play.cpp:2201 (HandleStateChange) TV: Attempting to change from None to WatchingPreRecorded
Jun 14 18:02:44 chris-TA75M mythfrontend.real: mythfrontend[3868]: E CoreContext audio/audiooutputalsa.cpp:172 (GetPCMInfo) ALSA: snd_pcm_info_get_card: Operation not permitted
Jun 14 18:02:44 chris-TA75M mythfrontend.real: mythfrontend[3868]: N CoreContext audioplayer.cpp:164 (ReinitAudio) AudioPlayer: Enabling Audio
```

Based on the time stamp, it's from the failed attempt to record Jeopardy today :).

I'm not sure what, if any, of this info is useful or relevant.  I'm hoping that it'll make more sense to someone else.

Thanks,

Chris

---

### Post by khPWXxF on 2016-06-15
If you schedule a recording, what do you see in the backend log?
Look at the time when it starts, and also at the time it is scheduled to finish.
Phil

---

### Post by cjgump720 on 2016-06-15
And now its working again.  I deleted and re-added my tuners and sources.  But that just made the Live TV give me the "All tuners are currently busy" error.  I rebooted once or twice and gave up for the day.  So I have no idea what finally fixed it.  I'm sorry that I'm not able to supply an answer for anyone else who might end up with similar symptoms, other than just wait a few days and see if it starts working again.

chris

---

