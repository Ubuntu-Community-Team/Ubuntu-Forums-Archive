---
title: "Trying to use S-video with HVR-1600"
date: 2010-10-17
forum: Multimedia Software
---

### Post by Tronman on 2010-10-17
Hello there!

I've been trying to set up my HVR-1600 card with MythTV but have run into a road block. As far as I can tell, the card is setup and the drivers are working properly ( cx18 ). The output of lspci shows:

02:06.0 Multimedia video controller: Conexant Systems, Inc. CX23418 Single-Chip MPEG-2 Encoder with Integrated Analog Video/Broadcast Audio Decoder

Unfortunately, I don't seem to be able to change channels when my cable is connected using ivtv-tune no matter what channel or frequency table I try (I live in Canada), though the S-video and audio input seem to work fine (but not through MythTV, see below).

Likewise, when I tried to scan for channels in MythTV, nothing is found, though the same cable plugged into a TV gives just regular cable as it should.

I'm not too worried about the tuners (although if you have any suggestions why it can't tune channels, let me know), since I have digital cable and would like to use the S-video anyway (and the IR blaster when I get that far). But I can't seem to get MythTV to recongize the S-video input. These are my backend settings:

Capture Card Setup:
Card type: IVTV MPEG-2 encoder card
Video device: /dev/video0
Probed Info (Hauppauge HVR-1600 [cx18]
Default Input: S-Video 1

Video sources: Configured not to use a grabber (for now)

Input connector:

Capture devide: /dev/video0
Input S-Video 1

My starting channel is not set (I suppose I would want to be S-video?) which may be a problem, as everytime I close Myth Backend Setup, I get a warning me that starting channel is not set (but I don't know how to set it to S-video). When I try to "WatchTV" but from the Front End, all I get is a "Please Wait" and then a few seconds later I return to the main menu. These are the last few logs from the front end and back end:

Back end:

2010-10-17 18:22:39.873 TVRec(1): Changing from None to WatchingLiveTV
2010-10-17 18:22:39.883 GetChannelData() failed because it could not
find channel number 'Please add' in DB for source '1'.
2010-10-17 18:22:39.887 ChannelBase(1): IsTunable(S-Video 1,Please add) Failed to find channel in DB on input '2'
2010-10-17 18:22:39.907 ChannelBase(1) Error: Setting start channel 'Please add' failed,
and we failed to find any suitible channels on any input.
2010-10-17 18:22:39.915 TVRec(1): HW Tuner: 1->1
2010-10-17 18:22:39.933 GetChannelData() failed because it could not
find channel number 'Please add' in DB for source '1'.
2010-10-17 18:22:39.948 TVRec(1) Error: Failed to set channel to Please add. Reverting to kState_None
2010-10-17 18:22:39.957 TVRec(1): Changing from WatchingLiveTV to None
2010-10-17 18:23:37.201 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min

Front end:

2010-10-17 18:22:39.850 TV: Attempting to change from None to WatchingLiveTV
2010-10-17 18:22:39.850 MythContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2010-10-17 18:22:39.850 Using protocol version 56
2010-10-17 18:22:39.871 Spawning LiveTV Recorder -- begin
2010-10-17 18:22:39.965 Spawning LiveTV Recorder -- end
2010-10-17 18:22:39.966 GetEntryAt(-1) failed.
2010-10-17 18:22:39.980 EntryToProgram(0@Wed Dec 31 20:00:00 1969) failed to get pginfo
2010-10-17 18:22:39.980 TV Error: HandleStateChange(): LiveTV not successfully started
2010-10-17 18:22:39.983 We have a RingBuffer
2010-10-17 18:22:40.043 TV Error: LiveTV not successfully started
2010-10-17 18:22:40.067 ScreenSaverX11Private: DPMS Deactivated 1
2010-10-17 18:22:40.068 ScreenSaverX11Private: DPMS Reactivated 1
2010-10-17 18:22:46.809 AudioPulseUtil: Resume Success
2010-10-17 18:22:46.810 Deleting UPnP client...

The backend logs seem to indicate that it doesn't like not having a channel to go to, though I want it to go to S-video.

In addition, I can see the tuner's output by using:

mplayer /dev/video0

I can also switch inputs using

v4l2-ctl -d /dev/video0 -i 1 (or 0 for the tuner).

I can also cat the video to a file and that works fine.

However, this *does not* work when I log in as the MythTV user. Cat to a file works fine, but trying to run it from mplayer gives me quite a few errors:

No protocol specified
XOpenDisplay() failed
Home directory /home/jason not ours.
W: core-util.c: Failed to open configuration file '/home/jason/.pulse//daemon.conf': Permission denied
W: daemon-conf.c: Failed to open configuration file: Permission denied
waitpid(): No child processes
AO: [pulse] Init failed: Internal error
Failed to initialize audio driver 'pulse'
No protocol specified
XOpenDisplay() failed
Home directory /home/jason not ours.
W: core-util.c: Failed to open configuration file '/home/jason/.pulse//daemon.conf': Permission denied
W: daemon-conf.c: Failed to open configuration file: Permission denied
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
[swscaler @ 0x7f4c7bc0e620]No accelerated colorspace conversion found from yuv420p to rgb4.
[swscaler @ 0x7f4c7bc0e620]using unscaled yuv420p -> rgb4 special converter
VO: [fbdev] 720x480 => 720x540 BGR 4-bit
FATAL: Cannot initialize video driver.
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
[swscaler @ 0x7f4c7bc0e620]No accelerated colorspace conversion found from yuv420p to rgb4.
VO: [fbdev] 720x480 => 720x540 BGR 4-bit
FATAL: Cannot initialize video driver.
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
[swscaler @ 0x7f4c7bc0e620]No accelerated colorspace conversion found from yuv420p to rgb4.
VO: [fbdev] 720x480 => 720x540 BGR 4-bit
FATAL: Cannot initialize video driver.
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
[swscaler @ 0x7f4c7bc0e620]No accelerated colorspace conversion found from yuv420p to rgb4.
VO: [fbdev] 720x480 => 720x540 BGR 4-bit
FATAL: Cannot initialize video driver.
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
[swscaler @ 0x7f4c7bc0e620]No accelerated colorspace conversion found from yuv420p to rgb4.
VO: [fbdev] 720x480 => 720x540 BGR 4-bit
FATAL: Cannot initialize video driver.
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
[swscaler @ 0x7f4c7bc0e620]No accelerated colorspace conversion found from yuv420p to rgb4.
VO: [fbdev] 720x480 => 720x540 BGR 4-bit
FATAL: Cannot initialize video driver.
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
[swscaler @ 0x7f4c7bc0e620]No accelerated colorspace conversion found from yuv420p to rgb4.
VO: [fbdev] 720x480 => 720x540 BGR 4-bit
FATAL: Cannot initialize video driver.

FATAL: Could not initialize video filters (-vf) or video output (-vo).


Exiting... (End of file)

I'm not sure if perhaps it's a permission error someone since it works as my own user? It seems very strange. So ultimately it seems I have two main issues:

1. Why can't I configure MythTV to use the S-video input?
2. Why does the MythTV user get errors when trying to use the /dev/video0 device with mplayer? (Remember, cat /dev/video0 > recording.mpg works fine as both MythTV user and my user account)

A few other details:

Ubuntu version: 10.04 64-bit
MythTV version: 0.23.0+fixes24158-0ubuntu2 (from the Ubuntu repository)
Nvidia 9400gt video card (with latest nvidia drivers, 195 I believe)

Thanks for any advice you may have!

---

