---
title: "HDPVR 1212/Directv: Unable to start live tv - Failed to find Channel"
date: 2014-02-26
forum: Mythbuntu
---

### Post by jogeedaklown on 2014-02-26
Hello Everyone,
I am pulling my hair trying to get my MythTV 0.27 setup to watch Live TV.  When I try to watch Live TV my screen flicker and will return to the frontend.   I looked at the mythbackup logs I have these error messages.

Feb 26 10:23:45 jogeemyth mythbackend: mythbackend[4552]: I ProcessRequest mainserver.cpp:1420 (HandleAnnounce) MainServer::ANN PlaybackFeb 26 10:23:45 jogeemyth mythbackend: mythbackend[4552]: I ProcessRequest mainserver.cpp:1422 (HandleAnnounce) adding: jogeemyth as a client (events: 0)
Feb 26 10:23:45 jogeemyth mythbackend: mythbackend[4552]: I TVRecEvent tv_rec.cpp:1050 (HandleStateChange) TVRec[2]: Changing from None to WatchingLiveTV
Feb 26 10:23:45 jogeemyth mythbackend: mythbackend[4552]: I TVRecEvent tv_rec.cpp:3602 (TuningCheckForHWChange) TVRec[2]: HW Tuner: 2->2
Feb 26 10:23:45 jogeemyth mythbackend: mythbackend[4552]: I TVRecEvent recorders/v4lchannel.cpp:558 (SetInputAndFormat) V4LChannel[2](/dev/video1): SetInputAndFormat(1, NTSC) (v4l v2) input_switch: 0 mode_switch: 0
Feb 26 10:23:45 jogeemyth mythbackend: mythbackend[4552]: E TVRecEvent recorders/v4lchannel.cpp:375 (GetCurrentChannelNum) V4LChannel[2](/dev/video1): GetCurrentChannelNum(206): Failed to find Channel
Feb 26 10:23:45 jogeemyth mythbackend: mythbackend[4552]: E TVRecEvent recorders/v4lchannel.cpp:392 (Tune) Channel(/dev/video1)::Tune(206): Error, failed to find channel.
Feb 26 10:23:45 jogeemyth mythbackend: mythbackend[4552]: E TVRecEvent tv_rec.cpp:3792 (TuningFrequency) TVRec[2]: Failed to set channel to 3. Reverting to kState_None
Feb 26 10:23:45 jogeemyth mythbackend: mythbackend[4552]: I TVRecEvent tv_rec.cpp:1050 (HandleStateChange) TVRec[2]: Changing from WatchingLiveTV to None

I have set up the change channel script to point to /usr/local/bin/channel-script.sh which calls a perl script that will change the channel on my directv box through IP.  I have set the permissions to 755 for both script so it should be executable to the mythtv user. The script does work via command-line so I am not sure when I keep receiving these error messages.  I attached the scripts to this post.  Am I missing something?

Thanks!
Jose

---

### Post by aelfric55 on 2014-02-28
Just a shot here. By "the script does work via command line" I assume you're referring to the perl script. And though you didn't mention it specifically, I assume that if you haven't got live-TV working, you can't (or haven't tried) a timed recording of a particular channel in mythtv (where mythtv would be changing the channel on its own without user involvement).

A "failed to find channel" error from the backend when invoking a channel in live tv would seem to imply that there's been no channel database entry set up  in the channel editor for the particular channel number you're trying to change to.

---

