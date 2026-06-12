---
title: "Black video playback - live tv and recorded"
date: 2013-11-27
forum: Mythbuntu
---

### Post by David_Stoll on 2013-11-27
I have a fresh install of 13.04 32bit on a nettop with an Nvidia ION video card.  This is a frontend only.  The recorded videos and also live tv playback as black video.  The display shows the channel info and show info.  I normally use VDPAU slim or VDPAU normal.  However, even if I change to a non-VDPAU playback profile, it doesn't help.  I am using the proprietary Nvidia driver from "additional drivers" tab of the software updates window.  I've tried a couple different driver versions including 304 and 310.

---

### Post by itlarson2 on 2013-11-30
Do the recordings play with VLC, Either directly from the back-end storage directories, or if you copy them to another computer?  If not your tuner is either bad or not set up properly, or the antenna connection is bad.   I have some notes I took on how to check that a tuner is working:

scan /usr/share/dvb/atsc/us-ATSC-center-frequencies-8VSB > channels.conf
open channels.conf in vlc to watch tv
("scan" is in package dvb-apps or dvb-utils)

I'll  leave it to you to figure out how to adapt this to your situation. 

If the recordings are good, try playing them in a different mythtv front-end, if you have one. If the problem effects all front-ends, it's probably on the back-end.  Possible non tuner back-end issues are file permissions or settings for the storage directory location.  The network and  database connections between the front-ends  and the back-end can be ruled out since recording information is showing up in the front-end.

Next check video setup on the front-end.  Double check the Nvidia driver setup by running nvidia-settings.  It will tell you immediately if the proprietary driver isn't active.  VDPAU requires Nvidia's driver to work.  Copy a recording to a flash drive, and play it on the front-end in VLC.  If that works, but Mythtv still doesn't, check that VDPAU is working outside Mythtv.  To do this install smplayer and set it to use VDPAU under options-> preferences-> output driver.  

If VDPAU isn't working run nvidia-settings as root, and let it generate an xorg.conf file for you.  reboot and try again.  There are  also several xorg tweaks for vdpau.  Add the following as a new section:
 
Section "Extensions"
       Option "Composite" "Disabled"
EndSection

Add the following to the "device" section:

Option    "TripleBuffer"     "True"

This will also require a reboot.  If you can get vdpau working in smplayer, then it comes down to fiddling with mythtv settings.  Remember to check the logs.

---

### Post by David_Stoll on 2013-12-02
The tuners are ok because the backend machine plays them just fine.  XBMC on the problem frontend seems to play the videos just fine also.  But, yes VLC plays the videos on the backend/frontend just fine.  I can even play the recorded mpg files from my tablet...although the HD recordings don't play all that well over wireless, but that's no surprise.

I did run nvidia-settings and let it create a new xorg.conf, rebooted, but no luck there.

I'll try the settings you mentioned below for the conf file.

What should the permissions be for the recording files and folder on the backend?

Thanks


> **itlarson2 said:**
> Do the recordings play with VLC, Either directly from the back-end storage directories, or if you copy them to another computer?  If not your tuner is either bad or not set up properly, or the antenna connection is bad.   I have some notes I took on how to check that a tuner is working:

scan /usr/share/dvb/atsc/us-ATSC-center-frequencies-8VSB > channels.conf
open channels.conf in vlc to watch tv
("scan" is in package dvb-apps or dvb-utils)

I'll  leave it to you to figure out how to adapt this to your situation. 

If the recordings are good, try playing them in a different mythtv front-end, if you have one. If the problem effects all front-ends, it's probably on the back-end.  Possible non tuner back-end issues are file permissions or settings for the storage directory location.  The network and  database connections between the front-ends  and the back-end can be ruled out since recording information is showing up in the front-end.

Next check video setup on the front-end.  Double check the Nvidia driver setup by running nvidia-settings.  It will tell you immediately if the proprietary driver isn't active.  VDPAU requires Nvidia's driver to work.  Copy a recording to a flash drive, and play it on the front-end in VLC.  If that works, but Mythtv still doesn't, check that VDPAU is working outside Mythtv.  To do this install smplayer and set it to use VDPAU under options-> preferences-> output driver.  

If VDPAU isn't working run nvidia-settings as root, and let it generate an xorg.conf file for you.  reboot and try again.  There are  also several xorg tweaks for vdpau.  Add the following as a new section:
 
Section "Extensions"
       Option "Composite" "Disabled"
EndSection

Add the following to the "device" section:

Option    "TripleBuffer"     "True"

This will also require a reboot.  If you can get vdpau working in smplayer, then it comes down to fiddling with mythtv settings.  Remember to check the logs.

---

### Post by David_Stoll on 2013-12-02
I tried the edits/adds mentioned for the xorg.conf, but it didn't seem to help.  I initiated playback of a recorded file and here is the log from that event from mythfrontend.log:

```
Dec  2 21:43:05 R3610 mythlogserver: mythfrontend[1630]: I CoreContext tv_play.cpp:1017 (TV) TV: Creating TV objectDec  2 21:43:06 R3610 mythlogserver: mythfrontend[1630]: N CoreContext mythmainwindow.cpp:2606 (PauseIdleTimer) Resuming idle timer
Dec  2 21:43:06 R3610 mythlogserver: mythfrontend[1630]: N CoreContext mythmainwindow.cpp:2601 (PauseIdleTimer) Suspending idle timer
Dec  2 21:43:06 R3610 mythlogserver: mythfrontend[1630]: I CoreContext tv_play.cpp:1232 (Init) TV: Created TvPlayWindow.
Dec  2 21:43:06 R3610 mythlogserver: mythfrontend[1630]: I CoreContext tv_play.cpp:2155 (HandleStateChange) TV: Attempting to change from None to WatchingPreRecorded
Dec  2 21:43:06 R3610 mythlogserver: mythfrontend[1630]: I CoreContext mythcorecontext.cpp:1191 (CheckProtoVersion) Using protocol version 75
Dec  2 21:43:06 R3610 mythlogserver: mythfrontend[1630]: I CoreContext mythcorecontext.cpp:1191 (CheckProtoVersion) Using protocol version 75
Dec  2 21:43:07 R3610 mythlogserver: mythfrontend[1630]: I CoreContext audio/audiopulsehandler.cpp:322 (SuspendInternal) Pulse: PulseAudio suspend OK
Dec  2 21:43:07 R3610 mythlogserver: mythfrontend[1630]: N CoreContext audioplayer.cpp:167 (ReinitAudio) AudioPlayer: Enabling Audio
Dec  2 21:43:08 R3610 mythlogserver: mythfrontend[1630]: I CoreContext avformatdecoder.cpp:2172 (ScanStreams) AFD: Opened codec 0x9f17400, id(MPEG2VIDEO) type(Video)
Dec  2 21:43:08 R3610 mythlogserver: mythfrontend[1630]: I CoreContext avformatdecoder.cpp:2021 (ScanStreams) AFD: codec MP2 has 2 channels
Dec  2 21:43:08 R3610 mythlogserver: mythfrontend[1630]: I CoreContext avformatdecoder.cpp:2172 (ScanStreams) AFD: Opened codec 0x9f33520, id(MP2) type(Audio)
Dec  2 21:43:08 R3610 mythlogserver: mythfrontend[1630]: I CoreContext audio/audiooutputbase.cpp:791 (Reconfigure) AO: Opening audio device 'dmix:CARD=NVidia,DEV=3' ch 2(2) sr 48000 sf signed 32 bit reenc 0
Dec  2 21:43:08 R3610 mythlogserver: mythfrontend[1630]: E CoreContext audio/audiooutputalsa.cpp:783 (SetParameters) ALSA: Requested 500000us got 170666 buffer time
Dec  2 21:43:08 R3610 mythlogserver: mythfrontend[1630]: E CoreContext audio/audiooutputalsa.cpp:242 (IncPreallocBufferSize) ALSA: Try to manually increase audio buffer with: echo 192 | sudo tee /proc/asound/card0/pcm3p/sub0/prealloc
Dec  2 21:43:08 R3610 mythlogserver: mythfrontend[1630]: E CoreContext audio/audiooutputalsa.cpp:961 (OpenMixer) ALSA: no playback control PCM found on mixer device default
Dec  2 21:43:08 R3610 mythlogserver: mythfrontend[1630]: E CoreContext audio/audiooutputalsa.cpp:497 (OpenDevice) ALSA: Unable to open audio mixer. Volume control disabled
Dec  2 21:43:09 R3610 mythlogserver: mythfrontend[1630]: E CoreContext mythrender_vdpau.cpp:1546 (CreateDevice) VDPAU: Error at mythrender_vdpau.cpp:1546 (#1, Unknown)
Dec  2 21:43:09 R3610 mythlogserver: mythfrontend[1630]: E CoreContext mythrender_vdpau.cpp:1550 (CreateDevice) VDPAU: Failed to create VDPAU device.
Dec  2 21:43:10 R3610 mythlogserver: mythfrontend[1630]: E CoreContext mythrender_vdpau.cpp:390 (Create) VDPAU: No VDPAU device
Dec  2 21:43:10 R3610 mythlogserver: mythfrontend[1630]: E CoreContext mythrender_vdpau.cpp:406 (Create) VDPAU: Failed to create VDPAU render device.
Dec  2 21:43:10 R3610 mythlogserver: mythfrontend[1630]: E CoreContext videoout_vdpau.cpp:147 (InitRender) VidOutVDPAU: Failed to initialise VDPAU
Dec  2 21:43:10 R3610 mythlogserver: mythfrontend[1630]: E CoreContext videooutbase.cpp:305 (Create) VideoOutput: Not compiled with any useable video output method.
Dec  2 21:43:10 R3610 mythlogserver: mythfrontend[1630]: E CoreContext mythplayer.cpp:492 (InitVideo) Player(0): Couldn't create VideoOutput instance. Exiting..
Dec  2 21:43:10 R3610 mythlogserver: mythfrontend[1630]: E CoreContext mythplayer.cpp:2700 (StartPlaying) Player(0): Unable to initialize video.
Dec  2 21:43:10 R3610 mythlogserver: mythfrontend[1630]: I CoreContext audio/audiopulsehandler.cpp:322 (SuspendInternal) Pulse: PulseAudio resume OK
Dec  2 21:43:30 R3610 mythlogserver: mythfrontend[1630]: E CoreContext playercontext.cpp:472 (StartPlaying) playCtx: StartPlaying() Failed to start player
Dec  2 21:43:30 R3610 mythlogserver: mythfrontend[1630]: I CoreContext tv_play.cpp:2485 (HandleStateChange) TV: Main UI disabled.
Dec  2 21:43:30 R3610 mythlogserver: mythfrontend[1630]: I CoreContext tv_play.cpp:403 (StartTV) TV: Entering main playback loop.
Dec  2 21:43:30 R3610 mythlogserver: mythfrontend[1630]: I CoreContext tv_play.cpp:405 (StartTV) TV: Exiting main playback loop.
Dec  2 21:43:30 R3610 mythlogserver: mythfrontend[1630]: N CoreContext mythmainwindow.cpp:2606 (PauseIdleTimer) Resuming idle timer
```

---

### Post by itlarson2 on 2013-12-02
Since the files play fine everywhere else, the recordings and their permissions aren't the problem.  The back-end just needs to read and write them is all.  Come to think of it you would probably get a "file not available" dialog if that was the issue.  It pretty much seems like this is a configuration issue with mythtfrontend.  Maybe look at the settings in the front-end on your back-end machine, and try applying those to the other one?   Does XBMC use VDPAU?  If so it's deffinitly a mythtv issue, not Nvidia or xorg.

---

### Post by David_Stoll on 2013-12-03
To be honest, I'm not sure about VDPAU and xbmc.  Settings look pretty identical to me...but different hardware...so...?

> **itlarson2 said:**
> Since the files play fine everywhere else, the recordings and their permissions aren't the problem.  The back-end just needs to read and write them is all.  Come to think of it you would probably get a "file not available" dialog if that was the issue.  It pretty much seems like this is a configuration issue with mythtfrontend.  Maybe look at the settings in the front-end on your back-end machine, and try applying those to the other one?   Does XBMC use VDPAU?  If so it's deffinitly a mythtv issue, not Nvidia or xorg.

---

### Post by David_Stoll on 2014-01-12
To fix the issue do the following:
[COLOR=#000000]
- Go to Settings|General Settings|Page two.[/COLOR]

[COLOR=#000000]- Choose (tick) Use custom identifier for frontend preferences and give it a unique name. It should then start with a fresh and uncorrupted set of preferences. (once mythfrontend is restarted).  You'll have to change your theme and maybe your audio settings, but it will now work with vdpau.

[/COLOR]

---

