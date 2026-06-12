---
title: "Fresh 12.04.  Normal Audio on Desktop, Static with internal player"
date: 2012-09-21
forum: Mythbuntu
---

### Post by TheMiz on 2012-09-21
I have a fresh installation of Mythbuntu with the 12.04 LTR.  I have been unable to get audio working inside of Mythtv (Internal Player).

Desktop audio works fine.  speaker-test from the command line works fine.  All of my videos will play through VLC fine.  My recorded TV shows will play fine with normal outside of the internal player (I upnp them to my PlayStation).

I have gone through every available option in the Audio configuration screen in the Mythtv Frontend, with no luck. 

When I try to play something through the internal player I get only static .  I can't mute this static, or change its volume from within Mythtv.  Audio is going out through the HDMI cable (which works fine from the desktop).

I also have a remote FE which is connected to its TV with a VGA cable and a mini-stereo plug.  It is having the same problem.

I'm sure it is a setting that I haven't set correctly from within Mythtv, but I can't figure out what that setting is.  I have tried every conceivable combination of the advanced audio options from within Mythtv's frontend.

Can someone point me in the right direction?

Thanks.

---

### Post by nickrout on 2012-09-21
> **TheMiz said:**
> I have a fresh installation of Mythbuntu with the 12.04 LTR.  I have been unable to get audio working inside of Mythtv (Internal Player).

Desktop audio works fine.  speaker-test from the command line works fine.  All of my videos will play through VLC fine.  My recorded TV shows will play fine with normal outside of the internal player (I upnp them to my PlayStation).

I have gone through every available option in the Audio configuration screen in the Mythtv Frontend, with no luck. 

When I try to play something through the internal player I get only static .  I can't mute this static, or change its volume from within Mythtv.  Audio is going out through the HDMI cable (which works fine from the desktop).

I also have a remote FE which is connected to its TV with a VGA cable and a mini-stereo plug.  It is having the same problem.

I'm sure it is a setting that I haven't set correctly from within Mythtv, but I can't figure out what that setting is.  I have tried every conceivable combination of the advanced audio options from within Mythtv's frontend.

Can someone point me in the right direction?

Thanks.Did you scan for audio devices in mythfrontend's audio setup screen? If you use the Setup Wizard it will scan for you. The test audio is pink/white noise, but once you have one that tests right it should work. Unless you have some other setting wrong. A frontend log would help once you have gone through the scan and audio test options would help.

---

### Post by TheMiz on 2012-09-21
Yes, I did scan for audio.
 
I am getting white/pink noise from the audio test from the Audio setup screen within Mythtv - although that sounds similar to what I am getting while trying to watch a video, so I didn't know that was how it was *supposed* to sound. 
 
From a terminal, I can do ```
speaker-test -twav -c2
``` and get the voice.
 
However, when I try to play a recording, watch tv, or watch a video with Mythtv's internal player, the audio continues to come out as pure static - there is not even any identifiable garble to it. All of these videos play perfectly on an external player (vlc) on my mythbox or on my PlayStation using UPnP.
 
I'll get a frontend log this evening and post that as well.
 
Thanks!

---

### Post by TheMiz on 2012-09-23
My Log initially showed: 
> 2012-09-22 22:24:23.240193 I  TV: Created TvPlayWindow.
2012-09-22 22:24:23.277759 I  TV: Attempting to change from None to WatchingLive
TV
2012-09-22 22:24:23.277849 I  MythCoreContext: Connecting to backend server: 192.168.1.xxx:6543 (try 1 of 1)
2012-09-22 22:24:23.279423 I  Using protocol version 72
2012-09-22 22:24:23.301115 N  TV: Spawning LiveTV Recorder -- begin
2012-09-22 22:24:23.535508 N  TV: Spawning LiveTV Recorder -- end
2012-09-22 22:24:23.553354 I  TV: playbackURL(/var/lib/mythtv/livetv/1111_20120922222423.mpg) cardtype(DUMMY)
2012-09-22 22:24:23.888223 N  AudioPlayer: Enabling Audio
2012-09-22 22:24:23.974880 I  VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2012-09-22 22:24:24.045409 I  OSD: Base theme size: 1280x720
2012-09-22 22:24:24.045592 I  OSD: Scaling factors: 0.5625x0.8
greedyhdeint: size changed from 0 x 0 -> 720 x 576
2012-09-22 22:24:24.216310 I  OSD: Base theme size: 1280x720
2012-09-22 22:24:24.216415 I  OSD: Scaling factors: 0.5625x0.8
2012-09-22 22:24:24.247257 I  Player(0): Video timing method: USleep with busy wait
2012-09-22 22:24:24.248804 I  TV: Created player.
2012-09-22 22:24:24.249014 I  TV: Changing from None to WatchingLiveTV
2012-09-22 22:24:24.249064 I  TV: State is LiveTV & mctx == ctx
2012-09-22 22:24:24.257919 I  TV: UpdateOSDInput done
2012-09-22 22:24:24.258007 I  TV: UpdateLCD done
2012-09-22 22:24:24.260042 I  TV: ITVRestart done
2012-09-22 22:24:24.283321 I  TV: Main UI disabled.
2012-09-22 22:24:24.284799 I  TV: Entering main playback loop.
2012-09-22 22:24:28.472668 I  VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2012-09-22 22:24:28.705291 I  OSD: Base theme size: 1280x720
2012-09-22 22:24:28.705355 I  OSD: Scaling factors: 1.5x1.5
2012-09-22 22:24:28.857061 I  AFD: Opened codec 0x29adc40, id(MPEG2VIDEO) type(Video)
2012-09-22 22:24:28.857104 I  AFD: codec AC3 has 6 channels
2012-09-22 22:24:28.858274 I  AFD: Opened codec 0x29b2870, id(AC3) type(Audio)
2012-09-22 22:24:28.858363 I  AFD: codec AC3 has 1 channels
2012-09-22 22:24:28.859471 I  AFD: Opened codec 0x46d8cc0, id(AC3) type(Audio)
2012-09-22 22:24:28.882476 I  AO: Opening audio device 'hdmi:CARD=NVidia,DEV=0' ch 2(6) sr 48000 sf signed 16 bit reenc 0
2012-09-22 22:24:28.888320 E  ALSA: Setting hardware audio buffer size to 128
2012-09-22 22:24:28.888729 E  ALSA: Error opening /proc/asound/card0/pcm3p/sub0/prealloc: Permission denied. 
2012-09-22 22:24:28.888769 E  ALSA: Try to manually increase audio buffer with: 
echo 128 | sudo tee /proc/asound/card0/pcm3p/sub0/prealloc
2012-09-22 22:24:28.888821 E  ALSA: Unable to sufficiently increase ALSA hardware buffer size - underruns are likely
2012-09-22 22:24:28.924609 N  AFD: Resetting byte context eof (livetv 1 was eof 0)
2012-09-22 22:24:29.290810 N  Player(0): Waited 103ms for video buffers AAAAAAAAAAAAAAAAAAAAAAAAAAAuULLPSo I ran:
```
echo 128 | sudo tee /proc/asound/card0/pcm3p/sub0/prealloc
```and crossed my fingers, but I still had the same audio problem on the next attempt which showed:

> 2012-09-22 22:31:53.039589 I  TV: Attempting to change from None to WatchingLiveTV
2012-09-22 22:31:53.039679 I  MythCoreContext: Connecting to backend server: 192.168.1.111:6543 (try 1 of 1)
2012-09-22 22:31:53.041129 I  Using protocol version 72
2012-09-22 22:31:53.066712 N  TV: Spawning LiveTV Recorder -- begin
2012-09-22 22:31:53.219172 N  TV: Spawning LiveTV Recorder -- end
2012-09-22 22:31:53.239326 I  TV: playbackURL(/var/lib/mythtv/livetv/1173_20120922223153.mpg) cardtype(DUMMY)
2012-09-22 22:31:53.508153 N  AudioPlayer: Enabling Audio
2012-09-22 22:31:53.581932 I  VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2012-09-22 22:31:53.656065 I  OSD: Base theme size: 1280x720
2012-09-22 22:31:53.656127 I  OSD: Scaling factors: 0.5625x0.8
2012-09-22 22:31:53.805185 I  OSD: Base theme size: 1280x720
2012-09-22 22:31:53.805261 I  OSD: Scaling factors: 0.5625x0.8
greedyhdeint: size changed from 0 x 0 -> 720 x 576
2012-09-22 22:31:53.823585 I  Player(0): Video timing method: USleep with busy wait
2012-09-22 22:31:53.824942 I  TV: Created player.
2012-09-22 22:31:53.825071 I  TV: Changing from None to WatchingLiveTV
2012-09-22 22:31:53.825095 I  TV: State is LiveTV & mctx == ctx
2012-09-22 22:31:53.831027 I  TV: UpdateOSDInput done
2012-09-22 22:31:53.831101 I  TV: UpdateLCD done
2012-09-22 22:31:53.832422 I  TV: ITVRestart done
2012-09-22 22:31:53.975043 I  TV: Main UI disabled.
2012-09-22 22:31:53.976654 I  TV: Entering main playback loop.
greedyhdeint: size changed from 0 x 0 -> 704 x 480
2012-09-22 22:31:54.901555 I  VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2012-09-22 22:31:54.962781 I  OSD: Base theme size: 1280x720
2012-09-22 22:31:54.962847 I  OSD: Scaling factors: 0.55x0.666667
2012-09-22 22:31:55.118649 I  AFD: Opened codec 0x40bef60, id(MPEG2VIDEO) type(Video)
2012-09-22 22:31:55.118688 I  AFD: codec AC3 has 2 channels
2012-09-22 22:31:55.119790 I  AFD: Opened codec 0x40f14e0, id(AC3) type(Audio)
2012-09-22 22:31:55.184736 I  AO: Opening audio device 'hdmi:CARD=NVidia,DEV=0' ch 2(2) sr 48000 sf signed 16 bit reen 0
2012-09-22 22:31:55.222712 N  AFD: Resetting byte context eof (livetv 1 was eof 0)
2012-09-22 22:31:55.472702 N  Player(0): Waited 103ms for video buffers AAAAAAAAAAAAAAAAAAAAAAAAAAAAAuLP
2012-09-22 22:31:55.574549 N  Player(0): Waited 205ms for video buffers UULUULAAAAAAAAAAAAAAAAAAAAAAAUUP
2012-09-22 22:31:55.626901 I  VideoOutput: Created YV12 OSD.
2012-09-22 22:32:09.286662 I  Using protocol version 72
2012-09-22 22:32:09.289386 I  Using protocol version 72
2012-09-22 22:32:09.469588 I  Using protocol version 72
2012-09-22 22:32:09.474968 I  Using protocol version 72
2012-09-22 22:32:19.292153 I  RingBuf(/var/lib/mythtv/livetv/1173_20120922223154.mpg): Waited 0.2 seconds for data to become available... 25168 < 32768
2012-09-22 22:32:20.219010 I  Using protocol version 72
2012-09-22 22:32:20.222892 I  Using protocol version 72
2012-09-22 22:32:28.045674 E  decoding error
            eno: Input/output error (5)
2012-09-22 22:32:28.050181 E  decoding error
            eno: Input/output error (5)
2012-09-22 22:32:28.055504 E  decoding error
            eno: Input/output error (5)
2012-09-22 22:32:28.061944 E  decoding error
            eno: Input/output error (5)I'm not sure what those decoding errors mean, since I didn't see that at first, and the audio didn't work either time.  Sorry for the info dump, but I would appreciate any clues as to why the internal player is not properly playing sound from any source.

---

### Post by nickrout on 2012-09-23
Sounds like you are sending audio at the wrong rate, eg 44.1kHz (cd audio rate) rather than 48kHz (typical ac3 bitrate).

What EXACTLY are all your settings in audio setup, and what capabilities does your audio scan tell you the receiver/tv actually has.

---

### Post by TheMiz on 2012-09-23
So apparently I was not as careful about adjusting ALL of the settings before posting.  Once I checked "Force audio device output to 48kHz", without changing anything else, it worked fine.

Thanks nick, glad it was an easy fix.  Marking my problem as "solved"

---

### Post by nickrout on 2012-09-23
> **TheMiz said:**
> So apparently I was not as careful about adjusting ALL of the settings before posting.  Once I checked "Force audio device output to 48kHz", without changing anything else, it worked fine.

Thanks nick, glad it was an easy fix.  Marking my problem as "solved"

I seem to be following this conversation both here and the mailing list LOL. Glad it fixed it.

---

