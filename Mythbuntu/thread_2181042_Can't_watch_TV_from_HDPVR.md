---
title: "Can't watch TV from HDPVR"
date: 2013-10-15
forum: Mythbuntu
---

### Post by haneo on 2013-10-15
Hi,

I have setup a new pc with mythubuntu + mythtv 0.27 connected to [COLOR=#333333][FONT=Verdana]Hauppauge 1212 [/FONT][/COLOR][FONT=Verdana]HD[/FONT][COLOR=#333333][FONT=Verdana]-[/FONT][/COLOR][FONT=Verdana]PVR.
I can see the video from the PVR using the command :
$mplayer /dev/video0

But When trying to Watch TV with the Frontend (on the server) I get a black screen for 2 seconds and back to the Frontend's menu

I get this errors in the Mythbackend logs:


[/FONT]Oct 15 23:18:20 mythtv mythbackend: mythbackend[13112]: I ProcessRequest mainserver.cpp:1420 (HandleAnnounce) MainServer::ANN Playback
Oct 15 23:18:20 mythtv mythbackend: mythbackend[13112]: I ProcessRequest mainserver.cpp:1422 (HandleAnnounce) adding: mythtv as a client (events: 0)
Oct 15 23:18:20 mythtv mythbackend: mythbackend[13112]: I TVRecEvent tv_rec.cpp:1048 (HandleStateChange) TVRec[2]: Changing from None to WatchingLiveTV
Oct 15 23:18:20 mythtv mythbackend: mythbackend[13112]: I TVRecEvent tv_rec.cpp:3597 (TuningCheckForHWChange) TVRec[2]: HW Tuner: 2->2
Oct 15 23:18:20 mythtv mythbackend: mythbackend[13112]: I TVRecEvent recorders/v4lchannel.cpp:558 (SetInputAndFormat) V4LChannel[2](/dev/video0): SetInputAndFormat(3, NTSC) (v4l v2) input_switch: 0 mode_switch: 0
**Oct 15 23:18:20 mythtv mythbackend: mythbackend[13112]: E TVRecEvent recorders/v4lchannel.cpp:465 (Tune) Channel(/dev/video0)::Tune(): Error -1 while setting frequency (v2): Inappropriate ioctl for device**
**Oct 15 23:18:20 mythtv mythbackend: mythbackend[13112]: E TVRecEvent tv_rec.cpp:3783 (TuningFrequency) TVRec[2]: Failed to set channel to 2. Reverting to kState_None**
Oct 15 23:18:20 mythtv mythbackend: mythbackend[13112]: I TVRecEvent tv_rec.cpp:1048 (HandleStateChange) TVRec[2]: Changing from WatchingLiveTV to None



I have no idea what that means !

Rem: In myth-setup -> input connections, when I click "Fetch channels from listings source" I get all the channels from "ScheduleDirect.org", but the field "Starting channel" get automatically the value 2. I don't know if it is related with my errors

Any help is welcome :- )

Thank you

---

### Post by tgm4883 on 2013-10-16
> **haneo said:**
> Hi,

I have setup a new pc with mythubuntu + mythtv 0.27 connected to [COLOR=#333333][FONT=Verdana]Hauppauge 1212 [/FONT][/COLOR][FONT=Verdana]HD[/FONT][COLOR=#333333][FONT=Verdana]-[/FONT][/COLOR][FONT=Verdana]PVR.
I can see the video from the PVR using the command :
$mplayer /dev/video0

But When trying to Watch TV with the Frontend (on the server) I get a black screen for 2 seconds and back to the Frontend's menu

I get this errors in the Mythbackend logs:


[/FONT]Oct 15 23:18:20 mythtv mythbackend: mythbackend[13112]: I ProcessRequest mainserver.cpp:1420 (HandleAnnounce) MainServer::ANN Playback
Oct 15 23:18:20 mythtv mythbackend: mythbackend[13112]: I ProcessRequest mainserver.cpp:1422 (HandleAnnounce) adding: mythtv as a client (events: 0)
Oct 15 23:18:20 mythtv mythbackend: mythbackend[13112]: I TVRecEvent tv_rec.cpp:1048 (HandleStateChange) TVRec[2]: Changing from None to WatchingLiveTV
Oct 15 23:18:20 mythtv mythbackend: mythbackend[13112]: I TVRecEvent tv_rec.cpp:3597 (TuningCheckForHWChange) TVRec[2]: HW Tuner: 2->2
Oct 15 23:18:20 mythtv mythbackend: mythbackend[13112]: I TVRecEvent recorders/v4lchannel.cpp:558 (SetInputAndFormat) V4LChannel[2](/dev/video0): SetInputAndFormat(3, NTSC) (v4l v2) input_switch: 0 mode_switch: 0
**Oct 15 23:18:20 mythtv mythbackend: mythbackend[13112]: E TVRecEvent recorders/v4lchannel.cpp:465 (Tune) Channel(/dev/video0)::Tune(): Error -1 while setting frequency (v2): Inappropriate ioctl for device**
**Oct 15 23:18:20 mythtv mythbackend: mythbackend[13112]: E TVRecEvent tv_rec.cpp:3783 (TuningFrequency) TVRec[2]: Failed to set channel to 2. Reverting to kState_None**
Oct 15 23:18:20 mythtv mythbackend: mythbackend[13112]: I TVRecEvent tv_rec.cpp:1048 (HandleStateChange) TVRec[2]: Changing from WatchingLiveTV to None



I have no idea what that means !

Rem: In myth-setup -> input connections, when I click "Fetch channels from listings source" I get all the channels from "ScheduleDirect.org", but the field "Starting channel" get automatically the value 2. I don't know if it is related with my errors

Any help is welcome :- )

Thank you

What type of card did you set the HDPVR up as in MythTV?

---

### Post by haneo on 2013-10-17
Hi,

I found the problem !

In case some one will get the same error: The script for channel change must have a value (I put /bin/true)

---

