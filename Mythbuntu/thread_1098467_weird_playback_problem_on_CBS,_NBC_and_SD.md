---
title: "weird playback problem on CBS, NBC and SD"
date: 2009-03-17
forum: Mythbuntu
---

### Post by rmhurt on 2009-03-17
i thought i'd reached the peak of my frustration a week ago with what turned out to be a simple xorg.conf problem (thanks newlinux!). i've now surpassed that feeling with another playback problem that has me at my wit's end and has my wife questioning my obsession with mythtv. i'm hoping this one is just as easily solved as my last problem but i feel doomed, as doomed as doomed can be.

here's the problem.  on select stations there is lurching which varies in intensity and is most noticeable when the camera is doing a steady pan, but it never effects audio. by lurching i mean that every 2-5 seconds the video goes into slo-mo for around .25 seconds and then resumes.  the audio is just fine while this is happening and remains sync'd, so there must also be some video speed-up somewhere to keep up.  i have seen this behavior on HD CBS, HD NBC and some of the digital StandardDef channels like USA and TNT. on CBS the lurching is subtle and the show is watchable, barely, while on NBC the lurching is more noticeable and not worth the agony. my tv info tells me that CBS & NBC are 1080i while the SD channels are 480i so it seems like there's an interlacing problem.

i wish i could stop there, but it gets more complex (which is why i feel doomed). yesterday i recorded the hockey game on NBC and it played fine (thank God). so do local shows here in Seattle. so does Jay Leno (i just checked). but every single NBC prime time show i've checked since Friday has lurching. oh, and so do some of the commercials being shown during the local NBC shows. that's right. they seem to be the national commercials but i'm not positive. meanwhile, on CBS the 30-minute comedies seem to be fine as does Mentalist, but Ghost Whisperer, NCIS & Numb3rs lurch. yesterday i taped a portion of a USA show which was lurching, and today a sample USA show has no lurching. i'm not making this up.

and finally, i just built my Mythbuntu machine (love Mythbuntu!) and copied across recordings (and db stuff) from a high-maintenance Gentoo mythtv. my old Gentoo NCIS & Numb3rs recordings show the lurching but my old NBC shows (Chuck & Heroes) do not. i think my ears are bleeding...

i'm desperately hoping someone can give me some things to try here that i haven't tried already. my HD recordings will not play if i use the Standard/ffmpeg or libmpeg2 decoder; the cpu max's out and it either plays horribly or not at all. but on the other hand the USA show i recorded still shows the same lurching when played with ffmpeg. i tried to play the HD shows using mplayer and vlc but couldn't get either player to play an HD show. feeling doomed, i tried to downgrade my nvidia driver from 173.14.12 to 100.14.19 because Gentoo was using 100.14.19, but Mythbuntu was unable to compile the 100 driver.  the Gentoo mythtv was also using xvmc-opengl, but Mythbuntu doesn't compile this in automatically and i don't know how to rebuild mythtv manually altho i have a bad feeling i'm going to learn.

here's lots of information.

my hardware is the same as it was for my Gentoo (which played everything back fine), with one exception - the harddrive is a new SATA 1TB Samsung that my old motherboard connects to using an IDE/SATA adapter.
```

motherboard: ECS PT800CE-A socket 478
cpu: Intel(R) Pentium(R) 4 CPU 3.20GHz  (Prescott?)
ram: 1gb
gpu: nVidia GeForce FX 5200
tv cards: 2 pcHDTV HD-3000s
harddrive: SAMSUNG Spinpoint F1 HD103UJ 1TB connected with [URL="http://www.newegg.com/Product/Product.aspx?Item=N82E16812206001"]
this adapter[/URL]

```

my xorg.conf:
```

Section "Module"
    Load           "glx"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    Option         "NoLogo" "1"
    Option         "UseEvents" "1"
    Option         "AddARGBGLXVisuals" "1"
    Option         "RenderAccel" "1"
    Option         "NvAGP" "1"
    Option         "XvMCUsesTextures" "1"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "nvidia-auto-select" "1920x1080" "1280x720" "1024x768" "720x480" "800x600" "640x480"
    EndSubSection
EndSection

```

my nvidia-settings settings:
```

# /home/bob/.nvidia-settings-rc
#
# Configuration file for nvidia-settings - the NVIDIA X Server Settings utility
# Generated on Sun Mar 15 12:02:12 2009
#

# ConfigProperties:

RcFileLocale = C
ToolTips = Yes
DisplayStatusBar = Yes
SliderTextEntries = Yes
IncludeDisplayNameInConfigFile = No
ShowQuitDialog = Yes
Timer = PowerMizer_Monitor_(GPU_0),Yes,1000

# Attributes:

0/DigitalVibrance[DFP-0]=0
0/ImageSharpening[DFP-0]=0
0/SyncToVBlank=1
0/AllowFlipping=1
0/LogAniso=0
0/FSAA=0
0/TextureSharpen=0
0/GammaCorrectedAALines=0
0/CursorShadow=0
0/CursorShadowXOffset=4
0/CursorShadowYOffset=2
0/CursorShadowAlpha=64
0/CursorShadowRed=0
0/CursorShadowGreen=0
0/CursorShadowBlue=0
0/FSAAAppControlled=1
0/LogAnisoAppControlled=1
0/GPUScaling[DFP-0]=65537
0/RedBrightness=0.000000
0/GreenBrightness=0.000000
0/BlueBrightness=0.000000
0/RedContrast=0.000000
0/GreenContrast=0.000000
0/BlueContrast=0.000000
0/RedGamma=1.000000
0/GreenGamma=1.000000
0/BlueGamma=1.000000
0/OpenGLImageSettings=1
0/XVideoTextureSyncToVBlank=1
0/XVideoBlitterSyncToVBlank=1
0/XVideoSyncToDisplay=65536

```

my mythtv > Setup > TV Settings > Playback settings:
```

General Playback (1/9): (settings checked ON are shown)
  Extra audio buffering
  Warn on no audio output
  [COLOR="Red"]**Use video as timebase <---------------------------THIS WAS THE CULPRIT**[/COLOR]
  Enable OpenGL vertical sync for timing
  Clear Saved Position on playback
  Alternate Clear Saved Position
  Jump to Program OSD

General Playback (2/9):
  Vertical scaling: 0
  Horizontal scaling: 0
  Video Aspect Override: Off
  Scan displacement (X): 0
  Scan displacement (Y): 0
  Zoom: Off

General Playback (3/9):
  Current Video Playback Profile: Bob Playback
  if rez >= 0 0 -> XvMC
    properties:
      Decoder: Standard XvMC  Max CPUs: 1  [_]Loopfilter[off]
      Video Renderer: xvmc-blit  OSD Renderer: ia44blend  [_]OSD Fade[off]
      Primary Deinterlacer: Bob (2x)
      Fallback Deinterlacer: One field

```

mythfrontend.log shows nothing at all, at least in normal logging mode. (is there a way to get verbose logging?)  here's everything for 10 seconds of NBC's Kings which has visible lurching:
```

2009-03-16 15:09:39.207 TV: Attempting to change from None to WatchingPreRecorded
2009-03-16 15:09:39.448 AFD: Opened codec 0xb1a4a40, id(MPEG2VIDEO_XVMC) type(Video)
2009-03-16 15:09:39.448 AFD: codec AC3 has 6 channels
2009-03-16 15:09:39.449 AFD: Opened codec 0xb1cc170, id(AC3) type(Audio)
2009-03-16 15:09:39.452 Opening audio device 'default'. ch 2(2) sr 48000
2009-03-16 15:09:39.452 Opening ALSA audio device 'default'.
2009-03-16 15:09:39.492 VideoOutputXv: XvMC Adaptor Name: 'NV17 Video Texture'
2009-03-16 15:09:39.546 OSD Theme Dimensions W: 640 H: 480
2009-03-16 15:09:39.932 TV: Changing from None to WatchingPreRecorded
2009-03-16 15:09:39.937 The realtime priority setting is not enabled.
2009-03-16 15:09:40.038 OpenGLVideoSync()
2009-03-16 15:09:40.072 Video timing method: SGI OpenGL
2009-03-16 15:09:48.992 TV: Attempting to change from WatchingPreRecorded to None
2009-03-16 15:09:49.004 ~OpenGLVideoSync() -- begin
2009-03-16 15:09:49.004 ~OpenGLVideoSync() -- middle
2009-03-16 15:09:49.004 ~OpenGLVideoSync() -- end
2009-03-16 15:09:49.046 TV: Changing from WatchingPreRecorded to None

```

i'm begging for help here!

---

### Post by rmhurt on 2009-03-18
Bueller? Bueller?

turns out there is some slight lurching in CBS' Mentalist, but much less so than in NCIS or Numb3rs.  and there is no lurching in NBC's Tonight Show with Jay Leno, except during the national commercials, whether the commercial is in HD or not.

time to go back to my old dominatrix Gentoo?  wild guesses welcome and appreciated. (about my playback problem, not my dominatrix.)

---

### Post by emillan on 2009-03-18
Check out this thread which might be relevant: [http://ubuntuforums.org/showthread.php?t=918086](http://ubuntuforums.org/showthread.php?t=918086)

Good luck!

---

### Post by newlinux on 2009-03-18
Another mind bender :). No immediate ideas, but you can get more verbose logging with:

```

mythfrontend -v playback

```

That might yield more results.

---

### Post by rmhurt on 2009-03-19
> **newlinux said:**
> Another mind bender :). No immediate ideas, but you can get more verbose logging with:

```

mythfrontend -v playback

```


sheesh, all i had to do was type "mythfrontend --help" and i could have figured that out by myself.  sometimes i amaze myself with what i pursue and what i don't.  thanks again, newlinux.

here is the problem:
```

2009-03-18 22:43:03.339 NVP: Video is 3.00174 frames ahead of audio,
                        doubling video frame interval to slow 
```

this gives me something to Google on, but i've never had an audio problem before and some of the threads on [www.gossamer-threads.com](www.gossamer-threads.com) seem to imply that some people have fixed this problem by setting some audio settings that i already have.  but it's late and i could be mis-reading them.  but also, my audio never misses a beat; the video is able to slow down enough so the audio doesn't have to stop at all.  this seems to be different than what i'm seeing others report.

below is the complete mythfrontend.log with the "-v playback" option for a couple seconds of the USA show which has the lurching; i'm hoping someone will spot something that may help me.  so, any audio experts out there?  should i re-post with a new subject line?

```

2009-03-18 22:43:01.828 TV: Attempting to change from None to WatchingPreRecorded
2009-03-18 22:43:01.830 RingBuf(/var/lib/mythtv/recordings/1928_20090315233200.mpg): OpenFile(/var/lib/mythtv/recordings/1928_20090315233200.mpg, 12)
2009-03-18 22:43:01.847 RingBuf(/var/lib/mythtv/recordings/1928_20090315233200.mpg): CalcReadAheadThresh(152391368 KB)
                         -> threshhold(64 KB) min read(0 KB) blk size(32 KB)
2009-03-18 22:43:01.930 DPMS Deactivated
2009-03-18 22:43:02.060 AFD: Stream #0, has id 0x2432 codec id MPEG2VIDEO, type Video, bitrate 15000000 at 0x0x91bede0
2009-03-18 22:43:02.077 VDP: Accepting: cmp(>= 0 0) dec(xvmc) cpus(1) skiploop(disabled) rend(xvmc-blit) osd(chromakey) osdfade(disabled) deint(bobdeint,onefield) filt()
2009-03-18 22:43:02.081 VDP: LoadBestPreferences(2048x2048, 0)
2009-03-18 22:43:02.081 VDP: LoadBestPreferences(2048x2048, 60)
2009-03-18 22:43:02.081 VDP: LoadBestPreferences(528x480, 60)
2009-03-18 22:43:02.081 Using 1 CPUs for decoding
2009-03-18 22:43:02.083 VDP: Accepting: cmp(>= 0 0) dec(xvmc) cpus(1) skiploop(disabled) rend(xvmc-blit) osd(chromakey) osdfade(disabled) deint(bobdeint,onefield) filt()
2009-03-18 22:43:02.083 VDP: LoadBestPreferences(2048x2048, 0)
2009-03-18 22:43:02.083 VDP: LoadBestPreferences(2048x2048, 60)
2009-03-18 22:43:02.083 VDP: LoadBestPreferences(528x480, 60)
2009-03-18 22:43:02.085 VideoOutputXv: XvMC version: 1.1
2009-03-18 22:43:02.089 XvMCSurfaceTypes::find(w 528, h 480, chroma 1, vld 0, idct 1, mpeg2, sub-width 0, sub-height 0, disp, p<= 356, 3250 <=p, port, surfNum)
2009-03-18 22:43:02.089 Trying XvMC port 325
2009-03-18 22:43:02.112 Found a suitable XvMC surface 0
2009-03-18 22:43:02.114 VDP: Accepting: cmp(>= 0 0) dec(xvmc) cpus(1) skiploop(disabled) rend(xvmc-blit) osd(chromakey) osdfade(disabled) deint(bobdeint,onefield) filt()
2009-03-18 22:43:02.115 VDP: LoadBestPreferences(2048x2048, 0)
2009-03-18 22:43:02.115 VDP: LoadBestPreferences(2048x2048, 60)
2009-03-18 22:43:02.115 VDP: LoadBestPreferences(528x480, 60)
2009-03-18 22:43:02.115 VideoOutputXv: @ j=0 Looking for flag[s]: XvInputMask  1d
2009-03-18 22:43:02.115 VideoOutputXv: Adaptor#0: NV17 Video Texture has flag[s]: XvInputMask XvImageMask
2009-03-18 22:43:02.115 VideoOutputXv: Has XVideo flags...
2009-03-18 22:43:02.116 VideoOutputXv: Missing XV_BRIGHTNESS, rejecting.
2009-03-18 22:43:02.116 VideoOutputXv: Adaptor#1: NV05 Video Blitter has flag[s]: XvInputMask XvImageMask
2009-03-18 22:43:02.116 VideoOutputXv: Has XVideo flags...
2009-03-18 22:43:02.116 VideoOutputXv: Missing XV_BRIGHTNESS, rejecting.
2009-03-18 22:43:02.116 VideoOutputXv: @ j=1 Looking for flag[s]: XvInputMask  d
2009-03-18 22:43:02.116 VideoOutputXv: Adaptor#0: NV17 Video Texture has flag[s]: XvInputMask XvImageMask
2009-03-18 22:43:02.116 VideoOutputXv: Has XVideo flags...
2009-03-18 22:43:02.116 VideoOutputXv: Missing XV_COLORKEY, rejecting.
2009-03-18 22:43:02.116 VideoOutputXv: Adaptor#1: NV05 Video Blitter has flag[s]: XvInputMask XvImageMask
2009-03-18 22:43:02.116 VideoOutputXv: Has XVideo flags...
2009-03-18 22:43:02.116 VideoOutputXv: Missing XV_COLORKEY, rejecting.
2009-03-18 22:43:02.117 VideoOutputXv: @ j=2 Looking for flag[s]: XvInputMask  15
2009-03-18 22:43:02.117 VideoOutputXv: Adaptor#0: NV17 Video Texture has flag[s]: XvInputMask XvImageMask
2009-03-18 22:43:02.117 VideoOutputXv: Has XVideo flags...
2009-03-18 22:43:02.117 VideoOutputXv: Missing XV_BRIGHTNESS, rejecting.
2009-03-18 22:43:02.117 VideoOutputXv: Adaptor#1: NV05 Video Blitter has flag[s]: XvInputMask XvImageMask
2009-03-18 22:43:02.117 VideoOutputXv: Has XVideo flags...
2009-03-18 22:43:02.117 VideoOutputXv: Missing XV_BRIGHTNESS, rejecting.
2009-03-18 22:43:02.117 VideoOutputXv: @ j=3 Looking for flag[s]: XvInputMask  5
2009-03-18 22:43:02.117 VideoOutputXv: Adaptor#0: NV17 Video Texture has flag[s]: XvInputMask XvImageMask
2009-03-18 22:43:02.117 VideoOutputXv: Has XVideo flags...
2009-03-18 22:43:02.117 VideoOutputXv: Here...
2009-03-18 22:43:02.117 XvMCSurfaceTypes::find(w 528, h 480, chroma 1, vld 0, idct 1, mpeg2, sub-width 0, sub-height 0, disp, p<= 356, 3250 <=p, port, surfNum)
2009-03-18 22:43:02.117 Trying XvMC port 325
2009-03-18 22:43:02.118 Found a suitable XvMC surface 0
2009-03-18 22:43:02.118 VideoOutputXv: Grabbed xv port 325
2009-03-18 22:43:02.118 VideoOutputXv: XvMC surface found with IDCT support on port 325
2009-03-18 22:43:02.139 VideoOutputXv: Closing XVideo port 325
2009-03-18 22:43:02.140 AFD: InitVideoCodec() 0x91befe0 id(MPEG2VIDEO_XVMC) type (Video).
2009-03-18 22:43:02.140 detectInterlace(Detect Scan, Interlaced Scan, 29.97, 480) ->Interlaced Scan
2009-03-18 22:43:02.140 AFD: Using xvmc for video decoding
2009-03-18 22:43:02.140 AFD: Looking for decoder for MPEG2VIDEO_XVMC
2009-03-18 22:43:02.140 AFD: Opened codec 0x91befe0, id(MPEG2VIDEO_XVMC) type(Video)
2009-03-18 22:43:02.140 AFD: Stream #1, has id 0x2433 codec id AC3, type Audio, bitrate 192000 at 0x0x91c0590
2009-03-18 22:43:02.140 AFD: codec AC3 has 2 channels
2009-03-18 22:43:02.141 AFD: Looking for decoder for AC3
2009-03-18 22:43:02.141 AFD: Opened codec 0x91c0680, id(AC3) type(Audio)
2009-03-18 22:43:02.143 RingBuf(/var/lib/mythtv/recordings/1928_20090315233200.mpg): CalcReadAheadThresh(153574364 KB)
                         -> threshhold(64 KB) min read(0 KB) blk size(32 KB)
2009-03-18 22:43:02.149 Opening audio device 'default'. ch 2(2) sr 48000
2009-03-18 22:43:02.150 Opening ALSA audio device 'default'.
2009-03-18 22:43:02.257 Dec: Trying to select track (w/lang)
2009-03-18 22:43:02.258 Dec: Selecting first track
2009-03-18 22:43:02.258 Dec: Selected track #1 in the Unknown language(0)
2009-03-18 22:43:02.258 Resyncing position map. posmapStarted = 0 livetv(0) watchingRec(0)
2009-03-18 22:43:02.290 Position map filled from DB to: 1578
2009-03-18 22:43:02.290 SyncPositionMap prerecorded, from DB: 59 entries
2009-03-18 22:43:02.290 SyncPositionMap, new totframes: 1578, new length: 52, posMap size: 59
2009-03-18 22:43:02.290 AFD: Position map found
2009-03-18 22:43:02.290 AFD: Successfully opened decoder for file: "/var/lib/mythtv/recordings/1928_20090315233200.mpg". novideo(0)
2009-03-18 22:43:02.294 VideoOutputXv: XvMC version: 1.1
2009-03-18 22:43:02.294 VideoOutput: Allowed renderers: xvmc-blit
2009-03-18 22:43:02.294 VideoOutput: Allowed renderers (filt: xvmc): xvmc-blit
2009-03-18 22:43:02.295 VideoOutput: Trying video renderer: xvmc-blit
2009-03-18 22:43:02.296 VDP: Accepting: cmp(>= 0 0) dec(xvmc) cpus(1) skiploop(disabled) rend(xvmc-blit) osd(chromakey) osdfade(disabled) deint(bobdeint,onefield) filt()
2009-03-18 22:43:02.296 VDP: LoadBestPreferences(2048x2048, 0)
2009-03-18 22:43:02.296 VDP: LoadBestPreferences(2048x2048, 60)
2009-03-18 22:43:02.310 VideoOutputXv: ctor
2009-03-18 22:43:02.311 XOff: 0, YOff: 0
2009-03-18 22:43:02.311 VDP: LoadBestPreferences(528x480, 60)
2009-03-18 22:43:02.312 Display Rect  left: 0, top: 0, width: 1232, height: 693, aspect: 1.33333
2009-03-18 22:43:02.312 Video Rect    left: 0, top: 0, width: 528, height: 480, aspect: 1.33333
2009-03-18 22:43:02.313 VideoOutputXv: Pixel dimensions: Screen 1280x720, window 1232x693
2009-03-18 22:43:02.314 VideoOutputXv: Estimated display dimensions: 325x182 mm  Aspect: 1.78571
2009-03-18 22:43:02.314 VideoOutputXv: Estimated window dimensions: 312x175 mm  Aspect: 1.78286
2009-03-18 22:43:02.314 VideoOutputXv: XvMC version: 1.1
2009-03-18 22:43:02.315 VideoOutputXv: InitSetupBuffers() render: xvmc-blit, allowed: xvmc-blit
2009-03-18 22:43:02.316 VDP: Accepting: cmp(>= 0 0) dec(xvmc) cpus(1) skiploop(disabled) rend(xvmc-blit) osd(chromakey) osdfade(disabled) deint(bobdeint,onefield) filt()
2009-03-18 22:43:02.316 VDP: LoadBestPreferences(2048x2048, 0)
2009-03-18 22:43:02.316 VDP: LoadBestPreferences(2048x2048, 60)
2009-03-18 22:43:02.316 VDP: LoadBestPreferences(528x480, 60)
2009-03-18 22:43:02.317 VideoOutputXv: @ j=0 Looking for flag[s]: XvInputMask  1d
2009-03-18 22:43:02.317 VideoOutputXv: Adaptor#0: NV17 Video Texture has flag[s]: XvInputMask XvImageMask
2009-03-18 22:43:02.317 VideoOutputXv: Has XVideo flags...
2009-03-18 22:43:02.317 VideoOutputXv: Missing XV_BRIGHTNESS, rejecting.
2009-03-18 22:43:02.317 VideoOutputXv: Adaptor#1: NV05 Video Blitter has flag[s]: XvInputMask XvImageMask
2009-03-18 22:43:02.317 VideoOutputXv: Has XVideo flags...
2009-03-18 22:43:02.317 VideoOutputXv: Missing XV_BRIGHTNESS, rejecting.
2009-03-18 22:43:02.317 VideoOutputXv: @ j=1 Looking for flag[s]: XvInputMask  d
2009-03-18 22:43:02.317 VideoOutputXv: Adaptor#0: NV17 Video Texture has flag[s]: XvInputMask XvImageMask
2009-03-18 22:43:02.317 VideoOutputXv: Has XVideo flags...
2009-03-18 22:43:02.318 VideoOutputXv: Missing XV_COLORKEY, rejecting.
2009-03-18 22:43:02.318 VideoOutputXv: Adaptor#1: NV05 Video Blitter has flag[s]: XvInputMask XvImageMask
2009-03-18 22:43:02.318 VideoOutputXv: Has XVideo flags...
2009-03-18 22:43:02.318 VideoOutputXv: Missing XV_COLORKEY, rejecting.
2009-03-18 22:43:02.318 VideoOutputXv: @ j=2 Looking for flag[s]: XvInputMask  15
2009-03-18 22:43:02.318 VideoOutputXv: Adaptor#0: NV17 Video Texture has flag[s]: XvInputMask XvImageMask
2009-03-18 22:43:02.318 VideoOutputXv: Has XVideo flags...
2009-03-18 22:43:02.318 VideoOutputXv: Missing XV_BRIGHTNESS, rejecting.
2009-03-18 22:43:02.318 VideoOutputXv: Adaptor#1: NV05 Video Blitter has flag[s]: XvInputMask XvImageMask
2009-03-18 22:43:02.318 VideoOutputXv: Has XVideo flags...
2009-03-18 22:43:02.318 VideoOutputXv: Missing XV_BRIGHTNESS, rejecting.
2009-03-18 22:43:02.319 VideoOutputXv: @ j=3 Looking for flag[s]: XvInputMask  5
2009-03-18 22:43:02.319 VideoOutputXv: Adaptor#0: NV17 Video Texture has flag[s]: XvInputMask XvImageMask
2009-03-18 22:43:02.319 VideoOutputXv: Has XVideo flags...
2009-03-18 22:43:02.319 VideoOutputXv: Here...
2009-03-18 22:43:02.319 XvMCSurfaceTypes::find(w 528, h 480, chroma 1, vld 0, idct 1, mpeg2, sub-width 0, sub-height 0, disp, p<= 356, 3250 <=p, port, surfNum)
2009-03-18 22:43:02.319 Trying XvMC port 325
2009-03-18 22:43:02.319 Found a suitable XvMC surface 0
2009-03-18 22:43:02.319 VideoOutputXv: Grabbed xv port 325
2009-03-18 22:43:02.319 VideoOutputXv: XvMC surface found with IDCT support on port 325
2009-03-18 22:43:02.319 VideoOutputXv: XvMC Adaptor Name: 'NV17 Video Texture'
2009-03-18 22:43:02.331 VDP: SetVideoRenderer(xvmc-blit)
2009-03-18 22:43:02.331 VDP: SetVideoRender(xvmc-blit) == GetVideoRenderer()
2009-03-18 22:43:02.332 VideoOutputXv: Chromakeying not possible with this XVideo port.
2009-03-18 22:43:02.332 VideoOutputXv: Ack! Disabling ChromaKey OSD
                        We can't use ChromaKey OSD if chromakeying is not supported!
2009-03-18 22:43:02.332 VideoOutputXv: DiscardFrames(1)
2009-03-18 22:43:02.332 VideoOutputXv: DiscardFrames() 1: AAAAAAAA
2009-03-18 22:43:02.332 VideoOutputXv: DiscardFrames() 2: AAAAAAAA
2009-03-18 22:43:02.332 VideoOutputXv: DiscardFrames() 3: AAAAAAAA -- done()
2009-03-18 22:43:02.333 VideoOutputXv: DiscardFrames(1)
2009-03-18 22:43:02.333 VideoOutputXv: DiscardFrames() 1: AAAAAAAA
2009-03-18 22:43:02.333 VideoOutputXv: DiscardFrames() 2: AAAAAAAA
2009-03-18 22:43:02.333 VideoOutputXv: DiscardFrames() 3: AAAAAAAA -- done()
2009-03-18 22:43:02.335 VideoOutputXv: Closing XVideo port 325
2009-03-18 22:43:02.337 VDP: Accepting: cmp(>= 0 0) dec(xvmc) cpus(1) skiploop(disabled) rend(xvmc-blit) osd(chromakey) osdfade(disabled) deint(bobdeint,onefield) filt()
2009-03-18 22:43:02.337 VDP: LoadBestPreferences(2048x2048, 0)
2009-03-18 22:43:02.337 VDP: LoadBestPreferences(2048x2048, 60)
2009-03-18 22:43:02.337 VDP: LoadBestPreferences(528x480, 60)
2009-03-18 22:43:02.338 VideoOutputXv: @ j=0 Looking for flag[s]: XvInputMask  1d
2009-03-18 22:43:02.338 VideoOutputXv: Adaptor#0: NV17 Video Texture has flag[s]: XvInputMask XvImageMask
2009-03-18 22:43:02.338 VideoOutputXv: Has XVideo flags...
2009-03-18 22:43:02.338 VideoOutputXv: Missing XV_BRIGHTNESS, rejecting.
2009-03-18 22:43:02.338 VideoOutputXv: Adaptor#1: NV05 Video Blitter has flag[s]: XvInputMask XvImageMask
2009-03-18 22:43:02.338 VideoOutputXv: Has XVideo flags...
2009-03-18 22:43:02.338 VideoOutputXv: Missing XV_BRIGHTNESS, rejecting.
2009-03-18 22:43:02.338 VideoOutputXv: @ j=1 Looking for flag[s]: XvInputMask  d
2009-03-18 22:43:02.338 VideoOutputXv: Adaptor#0: NV17 Video Texture has flag[s]: XvInputMask XvImageMask
2009-03-18 22:43:02.339 VideoOutputXv: Has XVideo flags...
2009-03-18 22:43:02.339 VideoOutputXv: Missing XV_COLORKEY, rejecting.
2009-03-18 22:43:02.339 VideoOutputXv: Adaptor#1: NV05 Video Blitter has flag[s]: XvInputMask XvImageMask
2009-03-18 22:43:02.339 VideoOutputXv: Has XVideo flags...
2009-03-18 22:43:02.339 VideoOutputXv: Missing XV_COLORKEY, rejecting.
2009-03-18 22:43:02.339 VideoOutputXv: @ j=2 Looking for flag[s]: XvInputMask  15
2009-03-18 22:43:02.339 VideoOutputXv: Adaptor#0: NV17 Video Texture has flag[s]: XvInputMask XvImageMask
2009-03-18 22:43:02.339 VideoOutputXv: Has XVideo flags...
2009-03-18 22:43:02.339 VideoOutputXv: Missing XV_BRIGHTNESS, rejecting.
2009-03-18 22:43:02.339 VideoOutputXv: Adaptor#1: NV05 Video Blitter has flag[s]: XvInputMask XvImageMask
2009-03-18 22:43:02.339 VideoOutputXv: Has XVideo flags...
2009-03-18 22:43:02.340 VideoOutputXv: Missing XV_BRIGHTNESS, rejecting.
2009-03-18 22:43:02.340 VideoOutputXv: @ j=3 Looking for flag[s]: XvInputMask  5
2009-03-18 22:43:02.340 VideoOutputXv: Adaptor#0: NV17 Video Texture has flag[s]: XvInputMask XvImageMask
2009-03-18 22:43:02.340 VideoOutputXv: Has XVideo flags...
2009-03-18 22:43:02.340 VideoOutputXv: Here...
2009-03-18 22:43:02.340 XvMCSurfaceTypes::find(w 528, h 480, chroma 1, vld 0, idct 1, mpeg2, sub-width 0, sub-height 0, disp, p<= 356, 3250 <=p, port, surfNum)
2009-03-18 22:43:02.340 Trying XvMC port 325
2009-03-18 22:43:02.340 Found a suitable XvMC surface 0
2009-03-18 22:43:02.340 VideoOutputXv: Grabbed xv port 325
2009-03-18 22:43:02.340 VideoOutputXv: XvMC surface found with IDCT support on port 325
2009-03-18 22:43:02.340 VideoOutputXv: XvMC Adaptor Name: 'NV17 Video Texture'
2009-03-18 22:43:02.352 VDP: SetVideoRenderer(xvmc-blit)
2009-03-18 22:43:02.352 VDP: SetVideoRender(xvmc-blit) == GetVideoRenderer()
2009-03-18 22:43:02.352 Display Rect  left: 154, top: 0, width: 924, height: 693, aspect: 1.77778
2009-03-18 22:43:02.352 Video Rect    left: 0, top: 0, width: 528, height: 480, aspect: 1.33333
2009-03-18 22:43:02.354 Over/underscan. V: 0, H: 0
2009-03-18 22:43:02.354 Display Rect  left: 154, top: 0, width: 924, height: 693, aspect: 1.77778
2009-03-18 22:43:02.354 Video Rect    left: 0, top: 0, width: 528, height: 480, aspect: 1.33333
2009-03-18 22:43:02.354 VDP: LoadBestPreferences(528x480, 29.97)
2009-03-18 22:43:02.355 NVP: LoadFilters(''..) -> 0
2009-03-18 22:43:02.357 OSD Theme Dimensions W: 640 H: 480
2009-03-18 22:43:02.829 NVP: ClearAfterSeek(1)
2009-03-18 22:43:02.829 TV: StartPlayer(): took 949 ms to start player.
2009-03-18 22:43:02.829 VideoOutputXv: ClearAfterSeek()
2009-03-18 22:43:02.829 VideoOutputXv: DiscardFrames(0)
2009-03-18 22:43:02.829 VideoOutputXv: DiscardFrames() 1: AAAAAAAA
2009-03-18 22:43:02.829 VideoOutputXv: DiscardFrames() 3: AAAAAAAA -- done()
2009-03-18 22:43:02.830 TV: Changing from None to WatchingPreRecorded
2009-03-18 22:43:02.830 VideoOutputXv: DiscardFrames(1)
2009-03-18 22:43:02.830 VideoOutputXv: DiscardFrames() 1: AAAAAAAA
2009-03-18 22:43:02.831 VideoOutputXv: DiscardFrames() 2: AAAAAAAA
2009-03-18 22:43:02.831 VideoOutputXv: DiscardFrames() 3: AAAAAAAA -- done()
2009-03-18 22:43:02.832 The realtime priority setting is not enabled.
2009-03-18 22:43:02.833 XvMC: picture structure FRAME
2009-03-18 22:43:02.834 VDP: GetFilteredDeint() : xvmc-blit -> 'bobdeint'
2009-03-18 22:43:02.836 Using deinterlace method bobdeint
2009-03-18 22:43:02.844 AFD: DoFastForward(310 (1), do discard frames)
2009-03-18 22:43:02.844 Dec: DoFastForward(310 (1), do discard frames)
2009-03-18 22:43:02.844 AFD: SeekReset(327, 0, do flush, do discard)
2009-03-18 22:43:02.844 AFD: SeekReset() flushing
2009-03-18 22:43:02.844 VideoOutputXv: DiscardFrames(1)
2009-03-18 22:43:02.844 VideoOutputXv: DiscardFrames() 1: UAAAAAAA
2009-03-18 22:43:02.844 VideoOutputXv Error: Child      B       was already marked as available.
2009-03-18 22:43:02.844 VideoOutputXv: DiscardFrames() 2: DAAAAAAA
2009-03-18 22:43:02.844 VideoOutputXv Error: Child      B       was already marked as available.
2009-03-18 22:43:02.844 VideoOutputXv: DiscardFrames() 3: DAAAAAAA -- done()
2009-03-18 22:43:02.844 NVP: ClearAfterSeek(0)
2009-03-18 22:43:02.941 nVidiaVideoSync: VBlank ioctl did not work, unimplemented in this driver?
2009-03-18 22:43:02.941 DRMVideoSync: Could not open device /dev/dri/card0, No such file or directory
2009-03-18 22:43:02.941 OpenGLVideoSync()
2009-03-18 22:43:02.945 OpenGLVideoSync: x,y -> 643, 358
2009-03-18 22:43:02.969 Using OpenGLVideoSync
2009-03-18 22:43:02.969 Set video sync frame interval to 33366
2009-03-18 22:43:02.972 Using video as timebase
2009-03-18 22:43:02.972 Video timing method: SGI OpenGL
2009-03-18 22:43:02.972 Refresh rate: 16666, frame interval: 33366
2009-03-18 22:43:02.987 NVP: progressive frame seen after 2 interlaced  frames
2009-03-18 22:43:03.005 VideoOutputXv Error: Child      B       was already marked as available.
2009-03-18 22:43:03.022 VideoOutputXv Error: Child      B       was already marked as available.
2009-03-18 22:43:03.023 VideoOutputXv Error: Child      B       was already marked as available.
2009-03-18 22:43:03.039 VideoOutputXv Error: Child      B       was already marked as available.
2009-03-18 22:43:03.056 VideoOutputXv Error: Child      B       was already marked as available.
2009-03-18 22:43:03.056 VideoOutputXv Error: Child      B       was already marked as available.
2009-03-18 22:43:03.056 Set video sync frame interval to 33366
2009-03-18 22:43:03.056 Disabled deinterlacing
2009-03-18 22:43:03.072 VideoOutputXv Error: Child      B       was already marked as available.
2009-03-18 22:43:03.073 VideoOutputXv Error: Child      B       was already marked as available.[COLOR="Red"]
2009-03-18 22:43:03.339 NVP: Video is 3.00174 frames ahead of audio,
                        doubling video frame interval to slow down.
2009-03-18 22:43:03.406 NVP: Video is 3.22535 frames ahead of audio,
                        doubling video frame interval to slow down.
2009-03-18 22:43:03.473 NVP: Video is 3.27315 frames ahead of audio,
                        doubling video frame interval to slow down.
2009-03-18 22:43:03.539 NVP: Video is 3.04678 frames ahead of audio,
                        doubling video frame interval to slow down.[/COLOR]
2009-03-18 22:43:03.873 NVP: interlaced frame seen after 23 progressive frames
2009-03-18 22:43:03.873 Set video sync frame interval to 33366
2009-03-18 22:43:03.873 Enabled deinterlacing
2009-03-18 22:43:03.956 NVP: progressive frame seen after 4 interlaced  frames
2009-03-18 22:43:04.023 Set video sync frame interval to 33366
2009-03-18 22:43:04.023 Disabled deinterlacing
2009-03-18 22:43:04.040 NVP: interlaced frame seen after 3 progressive frames
2009-03-18 22:43:04.040 Set video sync frame interval to 33366
2009-03-18 22:43:04.040 Enabled deinterlacing
2009-03-18 22:43:04.123 NVP: progressive frame seen after 4 interlaced  frames
2009-03-18 22:43:04.190 Set video sync frame interval to 33366
2009-03-18 22:43:04.190 Disabled deinterlacing
2009-03-18 22:43:04.206 NVP: interlaced frame seen after 3 progressive frames
2009-03-18 22:43:04.207 Set video sync frame interval to 33366
2009-03-18 22:43:04.207 Enabled deinterlacing
2009-03-18 22:43:04.289 NVP: progressive frame seen after 4 interlaced  frames
2009-03-18 22:43:04.356 Set video sync frame interval to 33366
2009-03-18 22:43:04.356 Disabled deinterlacing
2009-03-18 22:43:04.573 NVP: Video is 3.21567 frames ahead of audio,
                        doubling video frame interval to slow down.
2009-03-18 22:43:04.639 NVP: Video is 3.38578 frames ahead of audio,
                        doubling video frame interval to slow down.
2009-03-18 22:43:04.706 NVP: Video is 3.3785 frames ahead of audio,
                        doubling video frame interval to slow down.
2009-03-18 22:43:04.773 NVP: Video is 3.11829 frames ahead of audio,
                        doubling video frame interval to slow down.
2009-03-18 22:43:05.273 NVP: Video is 3.01876 frames ahead of audio,
                        doubling video frame interval to slow down.
2009-03-18 22:43:05.339 NVP: Video is 3.26059 frames ahead of audio,
                        doubling video frame interval to slow down.
2009-03-18 22:43:05.406 NVP: Video is 3.19469 frames ahead of audio,
                        doubling video frame interval to slow down.
2009-03-18 22:43:05.473 NVP: Video is 3.0104 frames ahead of audio,
                        doubling video frame interval to slow down.
2009-03-18 22:43:05.573 NVP: interlaced frame seen after 31 progressive frames
2009-03-18 22:43:05.573 Set video sync frame interval to 33366
2009-03-18 22:43:05.573 Enabled deinterlacing
2009-03-18 22:43:05.656 NVP: progressive frame seen after 4 interlaced  frames
2009-03-18 22:43:05.723 Set video sync frame interval to 33366
2009-03-18 22:43:05.723 Disabled deinterlacing
2009-03-18 22:43:05.873 NVP: interlaced frame seen after 7 progressive frames
2009-03-18 22:43:05.873 Set video sync frame interval to 33366
2009-03-18 22:43:05.873 Enabled deinterlacing
2009-03-18 22:43:05.956 NVP: progressive frame seen after 4 interlaced  frames
2009-03-18 22:43:06.023 Set video sync frame interval to 33366
2009-03-18 22:43:06.023 Disabled deinterlacing
2009-03-18 22:43:06.040 NVP: interlaced frame seen after 3 progressive frames
2009-03-18 22:43:06.040 Set video sync frame interval to 33366
2009-03-18 22:43:06.040 Enabled deinterlacing
2009-03-18 22:43:06.123 NVP: progressive frame seen after 4 interlaced  frames
2009-03-18 22:43:06.189 Set video sync frame interval to 33366
2009-03-18 22:43:06.190 Disabled deinterlacing
'video_output' mean = '37167.11', std. dev. = '12472.73', fps = '26.91'
2009-03-18 22:43:09.551 NVP: Changing speed to 0
2009-03-18 22:43:09.551 rate: 29.97 speed: 1 skip: 1 = interval 33366
2009-03-18 22:43:09.551 Set video sync frame interval to 33366
2009-03-18 22:43:09.606 VideoOutputXv: UpdatePauseFrame() AuLADuAU
2009-03-18 22:43:09.606 VideoOutputXv: UpdatePauseFrame -- XvMC
2009-03-18 22:43:09.607 VideoOutputXv: UpdatePauseFrame -- XvMC:
                        Found a pause frame in display
2009-03-18 22:43:09.742 DPMS Reactivated.
2009-03-18 22:43:12.556 TV: Attempting to change from WatchingPreRecorded to None
2009-03-18 22:43:12.570 TV: StopStuff() -- begin
2009-03-18 22:43:12.571 TV: StopStuff(): stopping ring buffer[s]
2009-03-18 22:43:12.571 TV: StopStuff(): stopping player[s] (1/2)
2009-03-18 22:43:12.571 TV: StopStuff(): stopping player[s] (2/2)
2009-03-18 22:43:12.571 NVP: Exited decoder loop.
2009-03-18 22:43:12.572 ~OpenGLVideoSync() -- begin
2009-03-18 22:43:12.572 ~OpenGLVideoSync() -- middle
2009-03-18 22:43:12.572 ~OpenGLVideoSync() -- end
2009-03-18 22:43:12.572 VideoOutputXv: dtor
2009-03-18 22:43:12.572 VideoOutputXv: DiscardFrames(1)
2009-03-18 22:43:12.572 VideoOutputXv: DiscardFrames() 1: AuLAPuAU
2009-03-18 22:43:12.572 VideoOutputXv: Frame F is in use by avlib and so is being held for later discarding.
2009-03-18 22:43:12.572 VideoOutputXv: DiscardFrames() 2: AdDAPdAA
2009-03-18 22:43:12.573 VideoOutputXv: Frame B is in use by avlib and so is being held for later discarding.
2009-03-18 22:43:12.573 VideoOutputXv: Frame F is in use by avlib and so is being held for later discarding.
2009-03-18 22:43:12.573 VideoOutputXv: Frame B is in use by avlib and so is being held for later discarding.
2009-03-18 22:43:12.573 VideoOutputXv: Frame F is in use by avlib and so is being held for later discarding.
2009-03-18 22:43:12.573 VideoOutputXv: DiscardFrames() 3: AdAAPdAA -- done()
2009-03-18 22:43:12.575 VideoOutputXv: DiscardFrames(1)
2009-03-18 22:43:12.575 VideoOutputXv: DiscardFrames() 1: AdAAPdAA
2009-03-18 22:43:12.575 VideoOutputXv: Frame B is in use by avlib and so is being held for later discarding.
2009-03-18 22:43:12.575 VideoOutputXv: Frame F is in use by avlib and so is being held for later discarding.
2009-03-18 22:43:12.575 VideoOutputXv: DiscardFrames() 2: AdAAPdAA
2009-03-18 22:43:12.575 VideoOutputXv: Frame B is in use by avlib and so is being held for later discarding.
2009-03-18 22:43:12.575 VideoOutputXv: Frame F is in use by avlib and so is being held for later discarding.
2009-03-18 22:43:12.575 VideoOutputXv: DiscardFrames() 3: AdAAPdAA -- done()
2009-03-18 22:43:12.577 VideoOutputXv: Closing XVideo port 325
2009-03-18 22:43:12.629 TV: StopStuff() -- end
2009-03-18 22:43:12.629 TV: Changing from WatchingPreRecorded to None

```

---

### Post by newlinux on 2009-03-19
you have probably already found this, but first thought is if "Use Video as Timebase" is set in the frontend playback settings make sure it is disabled...

---

### Post by newlinux on 2009-03-19
Also, do you still have this problem when you use the "timestretch" function during playback (change speed to .95 or 1.05)?

---

### Post by rmhurt on 2009-03-20
> **newlinux said:**
> you have probably already found this, but first thought is if "Use Video as Timebase" is set in the frontend playback settings make sure it is disabled...

spot on, newlinux!  i had that enabled and the problem went away when i simply disabled it; that was the only change i had to make.

your suggestion corresponds to this thread from earlier this month which i found by Googling for my slow-down error message, altho the problem is a bit different than mine: [http://www.gossamer-threads.com/lists/mythtv/users/373819]("http://www.gossamer-threads.com/lists/mythtv/users/373819")

again, thank you, thank you, thank you!

rock on, Mythbuntu!

---

### Post by rmhurt on 2009-03-20
> **newlinux said:**
> Also, do you still have this problem when you use the "timestretch" function during playback (change speed to .95 or 1.05)?

for posterity, i did try this early on using the "m" menu and it didn't help at all. the m menu let me change it to .9 and 1.1.

---

### Post by newlinux on 2009-03-20
> **rmhurt said:**
> for posterity, i did try this early on using the "m" menu and it didn't help at all. the m menu let me change it to .9 and 1.1.

I have a shortcut key that lets me adjust in .05 increments. This was just to check to see if your deinterlacer was causing the problem. When you timestretch I believe the deinterlacer is disabled. But you found your problem and it all good. 

happy mythbuntuing.

---

