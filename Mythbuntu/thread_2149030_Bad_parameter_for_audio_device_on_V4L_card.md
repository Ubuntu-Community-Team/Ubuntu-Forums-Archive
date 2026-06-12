---
title: "Bad parameter for audio device on V4L card"
date: 2013-05-27
forum: Mythbuntu
---

### Post by Taylorcraft078 on 2013-05-27
I am running MythTV on Ubuntu instead of Mythbuntu but the was the closest forum I could find.  The machine had a failed upgrade to 12.04 from 11.something.  A fresh install of 12.04 was done to a new drive and the database and recording directories brought over from the old drive.  OTA recoding works fine.  I also use a V4L analog input for a feed out of my satellite receiver.  I get video recorded but not audio.  Troubleshooting I find this in the mythtvbackend logs.

May 27 10:31:42 htpc mythbackend[3160]: I TVRecEvent tv_rec.cpp:3989 (TuningNewRecorder) TVRec(1): rec->GetPathname(): '/var/lib/mythtv/recordings/1110_20130527103200.nuv'
May 27 10:31:44 htpc mythbackend[3160]: E TVRecEvent audioinputalsa.cpp:336 (AlsaBad) **AudioInALSA(default:CARD=CA0106): pcm open failed:** Invalid argument
 May 27 10:31:44 htpc mythbackend[3160]: E TVRecEvent NuppelVideoRecorder.cpp:772 (AudioInit) NVR(/dev/video0): Failed to open audio device ALSA:default:CARD=CA0106
May 27 10:31:44 htpc mythbackend[3160]: E TVRecEvent NuppelVideoRecorder.cpp:700 (Initialize) NVR(/dev/video0): Failed to init audio input device
 May 27 10:31:44 htpc mythbackend[3160]: N Scheduler autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
May 27 10:31:44 htpc mythbackend[3160]: I Scheduler scheduler.cpp:2033 (HandleReschedule) Reschedule requested for id 0.
 May 27 10:31:44 htpc mythbackend[3160]: E NVRAudio audioinputalsa.cpp:336 (AlsaBad) AudioInALSA(default:CARD=CA0106): pcm open failed: Invalid argument
May 27 10:31:44 htpc mythbackend[3160]: E NVRAudio NuppelVideoRecorder.cpp:2380 (doAudioThread) NVR(/dev/video0): Failed to open audio device ALSA:default:CARD=CA0106
 May 27 10:31:44 htpc mythbackend[3160]: I Scheduler scheduler.cpp:2093 (HandleReschedule) Scheduled 2 items in 0.2 = 0.00 match + 0.21 place

This is the parameter that was in place for years on the old installation.  What has changed in 12.04 and how should I adjust the parameter so Mythtv gets the right sound input device?

Dave

---

