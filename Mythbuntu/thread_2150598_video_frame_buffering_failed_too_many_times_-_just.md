---
title: "video frame buffering failed too many times - just one channel?"
date: 2013-06-01
forum: Mythbuntu
---

### Post by jimp180 on 2013-06-01
Ok, the title say's it all, well except that the channel is SYFY so I might as well sit my TV and all out on the curb for the trash people to pick up!!! I recently dropped mythbuntu after using mythtv for at least 10 years and mythbuntu since 2007 and loaded windows media center because of all of the blank (0byte) recordings I was having, but the wife insisted we go back to "the old tv program" (I was sick of having to reactivate windows every morning to watch the news also) so I did a fresh install of mythbuntu 12.04 -2 and am running .26.0 + fixes. I have 2 HDHR Primes and one pchdtv 5500 card none of which will show SYFY, when I first tune to the channel it shows video for a few seconds, the video and audio both seem fine with smooth playback then the screen just frezzes and after a few more seconds I get the failed too many times message. any help would be appreciated

---

### Post by BicyclerBoy on 2013-06-02
Do you have a 100MB sample available ?

You can cut a sample of the file to size with "dd" but very very careful using this program..
It is important to retain the beginning of the sample.

---

### Post by jimp180 on 2013-06-02
> **BicyclerBoy said:**
> Do you have a 100MB sample available ?

You can cut a sample of the file to size with "dd" but very very careful using this program..
It is important to retain the beginning of the sample.

Hello, thanks for the reply,
not quite sure what you are asking for, a sample of video? 
here is what the front end log says
```
Jun  1 16:16:19 Zotac mythlogserver: mythfrontend[1363]: I CoreContext tv_play.cpp:2394 (HandleStateChange) TV: Changing from None to WatchingLiveTV
Jun  1 16:16:19 Zotac mythlogserver: mythfrontend[1363]: I CoreContext tv_play.cpp:2406 (HandleStateChange) TV: State is LiveTV & mctx == ctx
Jun  1 16:16:19 Zotac mythlogserver: mythfrontend[1363]: I CoreContext tv_play.cpp:2408 (HandleStateChange) TV: UpdateOSDInput done
Jun  1 16:16:19 Zotac mythlogserver: mythfrontend[1363]: I CoreContext tv_play.cpp:2410 (HandleStateChange) TV: UpdateLCD done
Jun  1 16:16:19 Zotac mythlogserver: mythfrontend[1363]: I CoreContext tv_play.cpp:2412 (HandleStateChange) TV: ITVRestart done
Jun  1 16:16:19 Zotac mythlogserver: mythfrontend[1363]: I CoreContext tv_play.cpp:2485 (HandleStateChange) TV: Main UI disabled.
Jun  1 16:16:19 Zotac mythlogserver: mythfrontend[1363]: I CoreContext tv_play.cpp:403 (StartTV) TV: Entering main playback loop.
Jun  1 16:16:19 Zotac mythlogserver: mythfrontend[1363]: I CoreContext mythcorecontext.cpp:1191 (CheckProtoVersion) Using protocol version 75
Jun  1 16:16:19 Zotac mythlogserver: mythfrontend[1363]: I CoreContext mythcorecontext.cpp:1191 (CheckProtoVersion) Using protocol version 75
Jun  1 16:16:21 Zotac mythlogserver: mythfrontend[1363]: W CoreContext ringbuffer.cpp:1035 (WaitForReadsAllowed) RingBuf(myth://192.168.0.35:6543/2045_20130601211618.mpg): Taking too long to be allowed to read..
Jun  1 16:16:36  mythlogserver: last message repeated 302 times
Jun  1 16:16:36 Zotac mythlogserver: mythfrontend[1363]: I CoreContext tv_play.cpp:1017 (TV) TV: Creating TV object
Jun  1 16:16:36 Zotac mythlogserver: mythfrontend[1363]: N CoreContext mythmainwindow.cpp:2606 (PauseIdleTimer) Resuming idle timer
Jun  1 16:16:36 Zotac mythlogserver: mythfrontend[1363]: N CoreContext mythmainwindow.cpp:2601 (PauseIdleTimer) Suspending idle timer
Jun  1 16:16:36 Zotac mythlogserver: mythfrontend[1363]: I CoreContext tv_play.cpp:1232 (Init) TV: Created TvPlayWindow.
Jun  1 16:16:36 Zotac mythlogserver: mythfrontend[1363]: I CoreContext tv_play.cpp:2155 (HandleStateChange) TV: Attempting to change from None to WatchingLiveTV
Jun  1 16:16:36 Zotac mythlogserver: mythfrontend[1363]: I CoreContext mythcorecontext.cpp:375 (ConnectCommandSocket) MythCoreContext: Connecting to backend server: 192.168.0.35:6543 (try 1 of 1)
Jun  1 16:16:36 Zotac mythlogserver: mythfrontend[1363]: I CoreContext mythcorecontext.cpp:1191 (CheckProtoVersion) Using protocol version 75
Jun  1 16:16:36 Zotac mythlogserver: mythfrontend[1363]: N CoreContext tv_play.cpp:2222 (HandleStateChange) TV: Spawning LiveTV Recorder -- begin
Jun  1 16:16:36 Zotac mythlogserver: mythfrontend[1363]: N CoreContext tv_play.cpp:2229 (HandleStateChange) TV: Spawning LiveTV Recorder -- end
Jun  1 16:16:36 Zotac mythlogserver: mythfrontend[1363]: I CoreContext tv_play.cpp:2250 (HandleStateChange) TV: playbackURL(myth://192.168.0.35:6543/2045_20130601211635.mpg) cardtype(DUMMY)
Jun  1 16:16:36 Zotac mythlogserver: mythfrontend[1363]: I CoreContext audio/audiopulsehandler.cpp:322 (SuspendInternal) Pulse: PulseAudio suspend OK
Jun  1 16:16:36 Zotac mythlogserver: mythfrontend[1363]: N CoreContext audioplayer.cpp:167 (ReinitAudio) AudioPlayer: Enabling Audio
Jun  1 16:16:36 Zotac mythlogserver: mythfrontend[1363]: I CoreContext signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Jun  1 16:16:36 Zotac mythlogserver: mythfrontend[1363]: I CoreContext signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Jun  1 16:16:36 Zotac mythlogserver: mythfrontend[1363]: I CoreContext videoout_xv.cpp:611 (InitXVideo) VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
Jun  1 16:16:36 Zotac mythlogserver: mythfrontend[1363]: I CoreContext osd.cpp:228 (OverrideUIScale) OSD: Base theme size: 1280x720
Jun  1 16:16:36 Zotac mythlogserver: mythfrontend[1363]: I CoreContext osd.cpp:233 (OverrideUIScale) OSD: Scaling factors: 0.5625x0.8
Jun  1 16:16:36 Zotac mythlogserver: mythfrontend[1363]: I CoreContext osd.cpp:228 (OverrideUIScale) OSD: Base theme size: 1280x720
Jun  1 16:16:36 Zotac mythlogserver: mythfrontend[1363]: I CoreContext osd.cpp:233 (OverrideUIScale) OSD: Scaling factors: 0.5625x0.8
Jun  1 16:16:36 Zotac mythlogserver: mythfrontend[1363]: I CoreContext mythplayer.cpp:1752 (InitAVSync) Player(1): Video timing method: USleep with busy wait
Jun  1 16:16:36 Zotac mythlogserver: mythfrontend[1363]: I CoreContext tv_play.cpp:5240 (StartPlayer) TV: Created player.
Jun  1 16:16:36 Zotac mythlogserver: mythfrontend[1363]: I CoreContext tv_play.cpp:2394 (HandleStateChange) TV: Changing from None to WatchingLiveTV
Jun  1 16:16:36 Zotac mythlogserver: mythfrontend[1363]: I CoreContext tv_play.cpp:2406 (HandleStateChange) TV: State is LiveTV & mctx == ctx
Jun  1 16:16:36 Zotac mythlogserver: mythfrontend[1363]: I CoreContext tv_play.cpp:2408 (HandleStateChange) TV: UpdateOSDInput done
Jun  1 16:16:36 Zotac mythlogserver: mythfrontend[1363]: I CoreContext tv_play.cpp:2410 (HandleStateChange) TV: UpdateLCD done
Jun  1 16:16:36 Zotac mythlogserver: mythfrontend[1363]: I CoreContext tv_play.cpp:2412 (HandleStateChange) TV: ITVRestart done
Jun  1 16:16:36 Zotac mythlogserver: mythfrontend[1363]: I CoreContext tv_play.cpp:2485 (HandleStateChange) TV: Main UI disabled.
Jun  1 16:16:36 Zotac mythlogserver: mythfrontend[1363]: I CoreContext tv_play.cpp:403 (StartTV) TV: Entering main playback loop.
Jun  1 16:16:37 Zotac mythlogserver: mythfrontend[1363]: I CoreContext mythcorecontext.cpp:1191 (CheckProtoVersion) Using protocol version 75
Jun  1 16:16:37 Zotac mythlogserver: mythfrontend[1363]: I CoreContext mythcorecontext.cpp:1191 (CheckProtoVersion) Using protocol version 75
Jun  1 16:16:40 Zotac mythlogserver: mythfrontend[1363]: W CoreContext ringbuffer.cpp:1035 (WaitForReadsAllowed) RingBuf(myth://192.168.0.35:6543/2045_20130601211636.mpg): Taking too long to be allowed to read..

```

---

### Post by BicyclerBoy on 2013-06-02
Are you sure that problem channel is "copy freely".
Only MWC can record non-"copy freely"..

Yes a 100MB sample of video uploaded to some public location or private FTP server..
I have a small international collection of H264 clips to allow mythtv code testing..

What sort of zotac box ?
ION2 or some intel chipset graphics?

If you have a low power CPU then you could require GPU h/w decode thru' VAAPI or VDPAU (to play that problem channel)

Can you try to run from terminal:
mediainfo <problem-recording-file>

You could try capture logging from backend while trying to play LiveTV:
(assuming you are using upstart).
sudo service mythtv-backend stop
mythbackend -v playback --loglevel debug > mbe.log
- run frontend & use liveTV..
mythfrontend -v playback --loglevel debug > mfe.log

Use <ctrl>+<c> to stop backend & then return to normal:
sudo service mythtv-backend start

---

### Post by jimp180 on 2013-06-03
> **BicyclerBoy said:**
> Are you sure that problem channel is "copy freely".
Only MWC can record non-"copy freely"..

funny you mention that, it is copy freely or at least it has always been, the SYFY HD channel isn't , all the other HD channels that my provider has are copy freely except SYFY, so I have to settle for the SD version. I could get either with WMC, but when my activation was screwed-up and the copy once channels wouldn't work on WMC, I still could tune in the SD one.

> **BicyclerBoy said:**
> Yes a 100MB sample of video uploaded to some public location or private FTP server..
I have a small international collection of H264 clips to allow mythtv code testing..

I will try when I get back home next week. I am not sure Mythtv actually records anything, I think when I looked on mythweb before I left the house friday it showed the recordings of the attempts to watch SYFY live tv as 0 byte recordings. When ever I tune a channel the stream plays for a few seconds and then stutters (quits) for just a second, I think it might be where the overlay goes away, and then continues to play fine after that. It seems like it is at this point when SYFY stops but it doesnt ever start back, and then it falls back to the menu and I get the buffering error.

> **BicyclerBoy said:**
> What sort of zotac box ?
ION2 or some intel chipset graphics?

It is an ION2, well I say that but I am guessing since I am out of town right now, but it does have Nvidia "new generation" graphics

> **BicyclerBoy said:**
> If you have a low power CPU then you could require GPU h/w decode thru' VAAPI or VDPAU (to play that problem channel)

I actualy set it to use VDPAU after my last post and it made no difference.

> **BicyclerBoy said:**
> Can you try to run from terminal:
mediainfo <problem-recording-file>

You could try capture logging from backend while trying to play LiveTV:
(assuming you are using upstart).
sudo service mythtv-backend stop
mythbackend -v playback --loglevel debug > mbe.log
- run frontend & use liveTV..
mythfrontend -v playback --loglevel debug > mfe.log

Use <ctrl>+<c> to stop backend & then return to normal:
sudo service mythtv-backend start

Thanks for the sugesstions, I will try to get you some results as soon as I get back home next weekend.

---

### Post by jimp180 on 2013-06-08
Since I left town Mythtv tried recording 5 times on SYFY channel 45, 3 of them are 0byte recordings, 1 is 1.5 mb and another is 25 mb. would a 25mb file be any good to you?

> **BicyclerBoy said:**
> Can you try to run from terminal:
mediainfo <problem-recording-file>

I loaded media info and ran it on the 25 mb recording and this is the result

```

General

ID                                       : 0 (0x0)

Complete name                            : /var/lib/mythtv/recordings/2045_20130604000000.mpg

Format                                   : MPEG-TS

File size                                : 24.6 MiB

Overall bit rate mode                    : Variable



Video

ID                                       : 3802 (0xEDA)

Menu ID                                  : 1 (0x1)

Format                                   : MPEG Video

Format version                           : Version 2

Format profile                           : Main@Main

Format settings, BVOP                    : Yes

Format settings, Matrix                  : Custom

Codec ID                                 : 2

Bit rate mode                            : Variable

Maximum bit rate                         : 15.0 Mbps

Width                                    : 704 pixels

Height                                   : 480 pixels

Display aspect ratio                     : 4:3

Frame rate                               : 29.970 fps

Standard                                 : NTSC

Color space                              : YUV

Chroma subsampling                       : 4:2:0

Bit depth                                : 8 bits

Compression mode                         : Lossy



Audio #1

ID                                       : 3803 (0xEDB)

Menu ID                                  : 1 (0x1)

Format                                   : AC-3

Format/Info                              : Audio Coding 3

Mode extension                           : CM (complete main)

Codec ID                                 : 129

Bit rate mode                            : Constant

Bit rate                                 : 192 Kbps

Channel(s)                               : 2 channels

Channel positions                        : Front: L R

Sampling rate                            : 48.0 KHz

Bit depth                                : 16 bits

Compression mode                         : Lossy

Delay relative to video                  : -406ms

Language                                 : English



Audio #2

ID                                       : 3804 (0xEDC)

Menu ID                                  : 1 (0x1)

Format                                   : AC-3

Format/Info                              : Audio Coding 3

Mode extension                           : CM (complete main)

Codec ID                                 : 129

Bit rate mode                            : Constant
Bit rate                                 : 192 Kbps

Channel(s)                               : 2 channels

Channel positions                        : Front: L R

Sampling rate                            : 48.0 KHz

Bit depth                                : 16 bits

Compression mode                         : Lossy

Delay relative to video                  : -405ms

Language                                 : Spanish



Menu

ID                                       : 69 (0x45)

Menu ID                                  : 1 (0x1)

List                                     : 3802 (0xEDA) (MPEG Video) / 3803 (0xEDB) (AC-3, English) / 3804 (0xEDC) (AC-3, Spanish)

Language                                 :  / English / Spanish

SCTE35_PID                               : 3805



```
I did double check and the prime's logfile shows this channel as being subscribed and not encrypted at all. also there are 9 other chanels on qam 256-28 and all of them play fine.
I will try the other (logging) stuff as soon as I figure out how to do what your talking about and what the heck upstart is and if im using it!
thanks

---

### Post by BicyclerBoy on 2013-06-08
I think you might need to run backend with full logging options & then schedule recordings on that channel.

sudo service mythtv-backend stop
mythbackend -v all --loglevel debug > mbe.log
(could need to start with --user mythtv & then & only then use sudo) 

The channel could be changing video stream size/resolution/refresh/encoding profile or audio stream ?
The channel does not go off air (stop TXing) during night does it?

When was the last time you deleted "all tuners/capture cards" & re-instated them (mythtv-setup) ?

---

