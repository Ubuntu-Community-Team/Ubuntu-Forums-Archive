---
title: "Hauppauge HVR-2250 S-Video Input on Mythbuntu 16.04"
date: 2018-01-28
forum: Multimedia Software
---

### Post by iry100fan on 2018-01-28
[SIZE=2]Hi everyone,

[FONT=arial]I am trying to setup a Mythbuntu 16.04 back-end using a couple of Hauppauge HVR-2250 cards.  I have the ATSC component working perfectly but I am having trouble getting the S-Video analog inputs working.  I am running Mytbuntu 16.04 with kernel "4.13.0-32-generic".  I have installed "NXP7164-2010-03-10.1.fw", "v4l-saa7164-1.0.2-3.fw", "22xxdrv_27086.zip" and "HVR-12x0-14x0-17x0_1_25_25271_WHQL.zip" into the /lib/firmware directory.  I setup a capture card as "V4L2 Encoder" on /dev/video0 and the input connection set to "s-video".[/FONT][/SIZE] When I tell it to record from that device, I get a file of 0B.

What am I doing wrong?

Thanks for the help.
-Brian

---

### Post by iry100fan on 2018-02-07
Update:
I have found that VLC works fine with the s-video input.  So the problem only exists with MythTV, so it's probably not a hardware/driver problem.  I'm guessing I'm configuring MythTV incorrectly.  More testing...

---

### Post by iry100fan on 2018-02-07
A little more info...

Here is part of the backend log pertaining to recording from the analog input.

[INDENT]TVRecEvent tv_rec.cpp:1088 (HandleStateChange) TVRec[13]: Changing from None to RecordingOnly
TVRecEvent tv_rec.cpp:3580 (TuningCheckForHWChange) TVRec[13]: HW Tuner: 13->13
TVRecEvent tv_rec.cpp:3704 (TuningFrequency) TVRec[13]: TuningFrequency
TVRecEvent recorders/v4lchannel.cpp:368 (GetCurrentChannelNum) V4LChannel[13](/dev/video2): GetCurrentChannelNum(0): Failed to find Channel
TVRecEvent recorders/v4lchannel.cpp:385 (Tune) Channel(/dev/video2)::Tune(0): Error, failed to find channel.
TVRecEvent tv_rec.cpp:2011 (SetupDTVSignalMonitor) TVRec[13]: No valid DTV info, ATSC maj(0) min(0), MPEG pn(-1)
TVRecEvent tv_rec.cpp:2065 (SetupSignalMonitor) TVRec[13]: Failed to setup digital signal monitoring
TVRecEvent tv_rec.cpp:3836 (TuningFrequency) TVRec[13]: Failed to setup signal monitor
[/INDENT]

If looks like MythTV is trying to "tune" the video in to a channel that doesn't exist.  I did setup a channel called "VCR" to channel 0 in order to eliminate error messages when exiting backend setup.  I wonder if I did that wrong.

---

