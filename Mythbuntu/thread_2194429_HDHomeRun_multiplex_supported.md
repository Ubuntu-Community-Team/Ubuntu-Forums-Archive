---
title: "HDHomeRun multiplex supported?"
date: 2013-12-18
forum: Mythbuntu
---

### Post by arobinson on 2013-12-18
I have an older HDHR (HWModel HDHR-US, Model hdhomerun_atsc) and I thought that it supported tuner multiplexing but it does not seem to be working. In the mythtv-setup, I have two tuners added (0 and 1). At first I set their "Max Recordings" to 2 on each.

I noticed that some of my recordings were failing. On the mythfrontend, if I tried some of the 4 encoders, the frontend would got to a black screen and hang.

Here is a sample log when it fails:
```
Dec 15 08:00:00 mythtv mythlogserver: mythbackend[2293]: I TVRecEvent tv_rec.cpp:1043 (HandleStateChange) TVRec(1): Changing from None to RecordingOnly
Dec 15 08:00:00 mythtv mythlogserver: mythbackend[2293]: I TVRecEvent mythdbcon.cpp:409 (PurgeIdleConnections) New DB connection, total: 10
Dec 15 08:00:00 mythtv mythlogserver: mythbackend[2293]: I TVRecEvent tv_rec.cpp:3562 (TuningCheckForHWChange) TVRec(1): HW Tuner: 1->1
Dec 15 08:00:00 mythtv mythlogserver: mythbackend[2293]: E TVRecEvent dtvmultiplex.cpp:327 (ParseTuningParams) DTVMux: ParseTuningParams -- Unknown tuner type = 0xffffffff80000000
Dec 15 08:00:00 mythtv mythlogserver: mythbackend[2293]: E TVRecEvent dtvchannel.cpp:308 (SetChannelByString) DTVChan(10173A3D-0): SetChannelByString(61): Failed to initialize multiplex options
Dec 15 08:00:00 mythtv mythlogserver: mythbackend[2293]: E TVRecEvent tv_rec.cpp:3748 (TuningFrequency) TVRec(1): Failed to set channel to 61. Reverting to kState_None
Dec 15 08:00:00 mythtv mythlogserver: mythbackend[2293]: I TVRecEvent tv_rec.cpp:1043 (HandleStateChange) TVRec(1): Changing from RecordingOnly to None
```

Setting the "Max Recordings" back to one prevents the issue. Was I wrong in that the HDHR-US supports multiplexing or did I just not configure something correctly?

MythTV Version: 2:0.26.1+fixes.20131113.3beccab-0ubuntu0mythbuntu1
HDHomeRun firmware version 20130328

---

### Post by tgm4883 on 2013-12-18
> **arobinson said:**
> I have an older HDHR (HWModel HDHR-US, Model hdhomerun_atsc) and I thought that it supported tuner multiplexing but it does not seem to be working. In the mythtv-setup, I have two tuners added (0 and 1). At first I set their "Max Recordings" to 2 on each.

I noticed that some of my recordings were failing. On the mythfrontend, if I tried some of the 4 encoders, the frontend would got to a black screen and hang.

Here is a sample log when it fails:
```
Dec 15 08:00:00 mythtv mythlogserver: mythbackend[2293]: I TVRecEvent tv_rec.cpp:1043 (HandleStateChange) TVRec(1): Changing from None to RecordingOnly
Dec 15 08:00:00 mythtv mythlogserver: mythbackend[2293]: I TVRecEvent mythdbcon.cpp:409 (PurgeIdleConnections) New DB connection, total: 10
Dec 15 08:00:00 mythtv mythlogserver: mythbackend[2293]: I TVRecEvent tv_rec.cpp:3562 (TuningCheckForHWChange) TVRec(1): HW Tuner: 1->1
Dec 15 08:00:00 mythtv mythlogserver: mythbackend[2293]: E TVRecEvent dtvmultiplex.cpp:327 (ParseTuningParams) DTVMux: ParseTuningParams -- Unknown tuner type = 0xffffffff80000000
Dec 15 08:00:00 mythtv mythlogserver: mythbackend[2293]: E TVRecEvent dtvchannel.cpp:308 (SetChannelByString) DTVChan(10173A3D-0): SetChannelByString(61): Failed to initialize multiplex options
Dec 15 08:00:00 mythtv mythlogserver: mythbackend[2293]: E TVRecEvent tv_rec.cpp:3748 (TuningFrequency) TVRec(1): Failed to set channel to 61. Reverting to kState_None
Dec 15 08:00:00 mythtv mythlogserver: mythbackend[2293]: I TVRecEvent tv_rec.cpp:1043 (HandleStateChange) TVRec(1): Changing from RecordingOnly to None
```

Setting the "Max Recordings" back to one prevents the issue. Was I wrong in that the HDHR-US supports multiplexing or did I just not configure something correctly?

MythTV Version: 2:0.26.1+fixes.20131113.3beccab-0ubuntu0mythbuntu1
HDHomeRun firmware version 20130328

MythTV does not support multiplexing on the HDHR3-CC, or the HDHR3-CC doesn't support multiplexing. Either way, it's not going to work.

:EDITED because only the HDHR3-CC doesn't support multirec, not the regular HDHR's

---

### Post by cosmotherobot on 2014-01-02
I have a newer HDHomerun - HDHR3-US  & multiplexing works just fine.  I'm on Mythtv .27 if that matters.     Bother tuners have Max Recorders set at 2.

---

### Post by tgm4883 on 2014-01-03
> **cosmotherobot said:**
> I have a newer HDHomerun - HDHR3-US  & multiplexing works just fine.  I'm on Mythtv .27 if that matters.     Bother tuners have Max Recorders set at 2.

You're right, only the HDHR3-CC doesn't support multirec. I've edited my post.

---

