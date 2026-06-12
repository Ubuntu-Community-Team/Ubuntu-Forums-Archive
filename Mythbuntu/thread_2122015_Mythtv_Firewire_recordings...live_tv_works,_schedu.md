---
title: "Mythtv Firewire recordings...live tv works, scheduled recordings fail"
date: 2013-03-03
forum: Mythbuntu
---

### Post by Culito on 2013-03-03
I recently upgraded to digital tv and I'm trying to get my firewire to work.  I had no problems with a tuner.


I am using a STB with P2P firewire, and mythtv recognizes the box no problem.
Basically, as the title suggests, I can watch live TV just fine.  Mythtv creates a file in the live tv folder.  However, if I schedule recordings, They come up as empty files.  I've been though all the settings that I can think of, and even tried using the Live TV profile for scheduled recordings with no luck.

I think I have a snippet of the backend log which shows a 5-minute test recording I scheduled:

```
Mar  3 18:59:32 HTPC mythbackend[6839]: I TVRecEvent tv_rec.cpp:1544 (HandlePendingRecordings) TVRec(6): ASK_RECORDING 6 21 0 0
Mar  3 18:59:57 HTPC mythbackend[6839]: I TVRecEvent tv_rec.cpp:1030 (HandleStateChange) TVRec(6): Changing from None to RecordingOnly
Mar  3 18:59:57 HTPC mythbackend[6839]: I TVRecEvent tv_rec.cpp:3503 (TuningCheckForHWChange) TVRec(6): HW Tuner: 6->6
Mar  3 18:59:58 HTPC mythbackend[6839]: I TVRecEvent firewiredevice.cpp:331 (SetLastChannel) SetLastChannel(3): cleared: yes
Mar  3 19:00:00 HTPC mythbackend[6839]: I TVRecEvent firewiredevice.cpp:331 (SetLastChannel) SetLastChannel(3): cleared: yes
Mar  3 19:00:00 HTPC mythbackend[6839]: E TVRecEvent tv_rec.cpp:1933 (SetupDTVSignalMonitor) TVRec(6): No valid DTV info, ATSC maj(0) min(0), MPEG pn(-1)
Mar  3 19:00:00 HTPC mythbackend[6839]: E TVRecEvent tv_rec.cpp:1987 (SetupSignalMonitor) TVRec(6): Failed to setup digital signal monitoring
Mar  3 19:00:00 HTPC mythbackend[6839]: E TVRecEvent tv_rec.cpp:3743 (TuningFrequency) TVRec(6): Failed to setup signal monitor
Mar  3 19:00:00 HTPC mythbackend[6839]: N Scheduler autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min
Mar  3 19:00:00 HTPC mythbackend[6839]: I Scheduler scheduler.cpp:2514 (HandleRecordingStatusChange) Tuning recording: "3 1000 - 7:00 PM (Manual Record)":"Sun Mar 3 19:00:00 2013": channel 1000 on cardid 6, sourceid 1
Mar  3 19:03:20 HTPC mythbackend[6839]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
Mar  3 19:03:20 HTPC mythbackend[6839]: I HouseKeeping housekeeper.cpp:299 (RunHouseKeeping) Running mythfilldatabase
Mar  3 19:03:20 HTPC mythbackend[6839]: I SystemManager system-unix.cpp:263 (run) Starting process manager
Mar  3 19:03:20 HTPC mythbackend[6839]: I SystemSignalManager system-unix.cpp:485 (run) Starting process signal handler
Mar  3 19:03:20 HTPC mythbackend[6839]: I SystemIOHandlerR system-unix.cpp:90 (run) Starting IO manager (read)
Mar  3 19:03:20 HTPC mythbackend[6839]: I SystemIOHandlerW system-unix.cpp:90 (run) Starting IO manager (write)
Mar  3 19:05:00 HTPC mythbackend[6839]: I TVRecEvent tv_rec.cpp:1030 (HandleStateChange) TVRec(6): Changing from RecordingOnly to None
Mar  3 19:05:59 HTPC mythbackend[6839]: E ProcessRequest programinfo.cpp:2278 (GetPlaybackURL) ProgramInfo(1000_20130303190000.mpg): GetPlaybackURL: '1000_20130303190000.mpg' should be local, but it can not be found.
Mar  3 19:06:20  mythbackend[6839]: last message repeated 5 times
```

Any suggestions?  I'm stumped.

---

### Post by newlinux on 2013-03-04
It's been years since I used firewire, but I can try to help. Do you empty files or do you not get the file at all for recordings? Have you made sure your recording storage groups are setup correctly and the directories have the right permissions? How are you storage groups setup? What happens when you record a show you started watching as liveTV (after the recording ends). Does the channel on the set top box successfully change even though the recording fails?

---

### Post by Culito on 2013-03-10
Hey, thanks for the reply.

I get no files at all in the "recordings" directory, where the scheduled recordings are supposed to go.
I think I have the recording profiles set up correctly, but not sure.  Mythtv seems to set up that stuff automatically in the "default" group.
The "recordings" directory has the appropriate permissions (same as the "livetv" folder).

Live TV creates a .mpg file in the "livetv" folder, no problem.  I can watch it with VLC.

The channel successfully changes on the set top box, but a file is never created...

For now, I think I'll just switch back to my old PVR tuner card.  I just wanted to upgrade the recording quality, but the wife is already pissed about missing shows!

---

### Post by one30nav on 2013-03-10
Firewire setups are usually via broadcast and not P2P. There's a bunch of help in the wikis and archived here. What STB are you using and what is your service provider? Need, essentially, more detail of your hardware and software setup to help.

---

