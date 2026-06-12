---
title: "Upgrade to 12.04, no video on Revo Ion frontend"
date: 2013-01-06
forum: Mythbuntu
---

### Post by vagster on 2013-01-06
Hi there,

This weekend, I updated my mythtv combined frontend/backend to 12.04 running MythTV 0.25 fixes. The combined frontned/backend went like a dream so I also upgraded my separate Revo frontend. 

Now, whenever I try to play any video, I just get a blank screen with the audio playing. I have tried the following:

[LIST]
[*]Completely removed the Nvidia drivers (295.40 family) and re-installed them using instructions from [here]("http://askubuntu.com/questions/206283/how-can-i-uninstall-a-nvidia-driver-completely").

[*]Changed the desktop back to XFCE.

[*]Updated vdpau-vc-drivers.

[*]Swapped between Slim, VDPAU Normal and Slim, and OpenGL playback profiles

[*]Tried playing an SD video in VLC - this works okay. Tried playing a HD video in VLC and this was very chopp with V high CPU usage. Swapping hardware acceleration on and off in VLC made no difference.

[*] Ran vdpauinfo which gives alot of information and seems to be functioning.
[/LIST]

It doesn't seem to matter what I do, I just always get no video but audio plays fine.

WAF and CAF are at an all time low and am sure this is something simple I am missing. 

Any advice on what to do next would be much appreciated.

Cheers

Stephen

---

### Post by nickrout on 2013-01-06
Check your playback profiles and make sure that they do not have any extraneous vdpau settings.

[http://www.mythtv.org/wiki/Release_Notes_-_0.25](http://www.mythtv.org/wiki/Release_Notes_-_0.25)

Also what version are you on? (EXACTLY). Have you used the mythbuntu repo to update to latest -fixes?

Lastly your frontend log would help.

---

### Post by vagster on 2013-01-07
Hi Nick,

Thanks for your response.

I have removed all the extraneous profile settings so they have default values only.

The exact version of mythtv is 0.25 [v0.25.3-29-g010e576]. I do have the 0.25 repos setup and it is upto date AFAIK (the 0.25 repository is set in mythbuntu control centre).

The output from mythfrontend --verbose is:

```
Jan  7 06:29:01 bigtv mythfrontend[2918]: N CoreContext mythmainwindow.cpp:1862 (RegisterMediaPlugin) Registering Internal as a media playback plugin.
Jan  7 06:29:02 bigtv mythfrontend[2918]: I CoreContext mythtranslation.cpp:66 (load) Loading en_gb translation for module mythgallery
Jan  7 06:29:02 bigtv mythfrontend[2918]: I CoreContext serverpool.cpp:395 (listen) Listening on TCP 127.0.0.1:6546
Jan  7 06:29:02 bigtv mythfrontend[2918]: I CoreContext serverpool.cpp:395 (listen) Listening on TCP 192.168.32.102:6546
Jan  7 06:29:02 bigtv mythfrontend[2918]: I CoreContext serverpool.cpp:395 (listen) Listening on TCP [::1]:6546
Jan  7 06:29:02 bigtv mythfrontend[2918]: I CoreContext serverpool.cpp:395 (listen) Listening on TCP [fe80::92fb:a6ff:fe30:98fc%eth0]:6546
Jan  7 06:29:02 bigtv mythfrontend[2918]: N CoreContext main.cpp:1074 (RunMenu) Found mainmenu.xml for theme 'Mythbuntu'
Jan  7 06:29:02 bigtv mythfrontend[2918]: I Reconnect mythcorecontext.cpp:371 (ConnectCommandSocket) MythCoreContext: Connecting to backend server: 192.168.32.100:6543 (try 1 of 1)
Jan  7 06:29:02 bigtv mythfrontend[2918]: I Reconnect mythcorecontext.cpp:1178 (CheckProtoVersion) Using protocol version 72
Jan  7 06:29:02 bigtv mythfrontend[2918]: I CoreContext bonjourregister.cpp:103 (BonjourCallback) Bonjour: Service registration complete: name 'Mythfrontend on bigtv' type '_mythfrontend._tcp.' domain: 'local.'
Jan  7 06:29:13 bigtv mythfrontend[2918]: I CoreContext tv_play.cpp:987 (TV) TV: Creating TV object
Jan  7 06:29:13 bigtv mythfrontend[2918]: N CoreContext mythmainwindow.cpp:2586 (PauseIdleTimer) Suspending idle timer
Jan  7 06:29:13 bigtv mythfrontend[2918]: I CoreContext tv_play.cpp:1206 (Init) TV: Created TvPlayWindow.
Jan  7 06:29:13 bigtv mythfrontend[2918]: I CoreContext tv_play.cpp:2121 (HandleStateChange) TV: Attempting to change from None to WatchingPreRecorded
Jan  7 06:29:13 bigtv mythfrontend[2918]: I CoreContext mythcorecontext.cpp:1178 (CheckProtoVersion) Using protocol version 72
Jan  7 06:29:13 bigtv mythfrontend[2918]: I CoreContext mythcorecontext.cpp:1178 (CheckProtoVersion) Using protocol version 72
Jan  7 06:29:14 bigtv mythfrontend[2918]: I CoreContext audio/audiopulsehandler.cpp:320 (SuspendInternal) Pulse: PulseAudio suspend OK
Jan  7 06:29:14 bigtv mythfrontend[2918]: N CoreContext audioplayer.cpp:167 (ReinitAudio) AudioPlayer: Enabling Audio
Jan  7 06:29:17 bigtv mythfrontend[2918]: I CoreContext avformatdecoder.cpp:2104 (ScanStreams) AFD: Opened codec 0xae0eb30, id(MPEG2VIDEO) type(Video)
Jan  7 06:29:17 bigtv mythfrontend[2918]: I CoreContext avformatdecoder.cpp:1962 (ScanStreams) AFD: codec MP2 has 2 channels
Jan  7 06:29:17 bigtv mythfrontend[2918]: I CoreContext avformatdecoder.cpp:2104 (ScanStreams) AFD: Opened codec 0xae58a80, id(MP2) type(Audio)
Jan  7 06:29:17 bigtv mythfrontend[2918]: I CoreContext avformatdecoder.cpp:1962 (ScanStreams) AFD: codec MP3 has 0 channels
Jan  7 06:29:17 bigtv mythfrontend[2918]: I CoreContext avformatdecoder.cpp:2104 (ScanStreams) AFD: Opened codec 0xae59090, id(MP3) type(Audio)
Jan  7 06:29:17 bigtv mythfrontend[2918]: I CoreContext avformatdecoder.cpp:2104 (ScanStreams) AFD: Opened codec 0xae5e2e0, id(DVB_SUBTITLE) type(Subtitle)
Jan  7 06:29:17 bigtv mythfrontend[2918]: I CoreContext audio/audiooutputbase.cpp:791 (Reconfigure) AO: Opening audio device 'hdmi' ch 2(2) sr 48000 sf signed 16 bit reenc 0
Jan  7 06:29:18 bigtv mythfrontend[2918]: E CoreContext audio/audiooutputalsa.cpp:195 (SetPreallocBufferSize) ALSA: Setting hardware audio buffer size to 128
Jan  7 06:29:18 bigtv mythfrontend[2918]: E CoreContext audio/audiooutputalsa.cpp:211 (SetPreallocBufferSize) ALSA: Error opening /proc/asound/card0/pcm3p/sub0/prealloc: Permission denied. 
Jan  7 06:29:18 bigtv mythfrontend[2918]: E CoreContext audio/audiooutputalsa.cpp:213 (SetPreallocBufferSize) ALSA: Try to manually increase audio buffer with: echo 128 | sudo tee /proc/asound/card0/pcm3p/sub0/prealloc
Jan  7 06:29:18 bigtv mythfrontend[2918]: E CoreContext audio/audiooutputalsa.cpp:545 (OpenDevice) ALSA: Unable to sufficiently increase ALSA hardware buffer size - underruns are likely
Jan  7 06:29:18 bigtv mythfrontend[2918]: E CoreContext audio/audiooutputalsa.cpp:937 (OpenMixer) ALSA: failed to register mixer device /dev/mixer: No such file or directory
Jan  7 06:29:18 bigtv mythfrontend[2918]: E CoreContext audio/audiooutputalsa.cpp:550 (OpenDevice) ALSA: Unable to open audio mixer. Volume control disabled
Jan  7 06:29:23 bigtv mythfrontend[2918]: I CoreContext mythrender_vdpau.cpp:1675 (CreatePresentationSurfaces) VDPAU: Created 2 output surfaces.
Jan  7 06:29:23 bigtv mythfrontend[2918]: I CoreContext mythrender_vdpau.cpp:1709 (CheckHardwareSupport) VDPAU: Version 1
Jan  7 06:29:23 bigtv mythfrontend[2918]: I CoreContext mythrender_vdpau.cpp:1716 (CheckHardwareSupport) VDPAU: Information NVIDIA VDPAU Driver Shared Library  295.40  Thu Apr  5 21:54:31 PDT 2012
Jan  7 06:29:23 bigtv mythfrontend[2918]: I CoreContext mythrender_vdpau.cpp:401 (Create) VDPAU: Created VDPAU render device 1920x1080
Jan  7 06:29:23 bigtv mythfrontend[2918]: N CoreContext mythplayer.cpp:506 (CheckExtraAudioDecode) Player(0): Forcing decode extra audio option on (Video method requires it).
Jan  7 06:29:24 bigtv mythfrontend[2918]: I CoreContext mythplayer.cpp:1737 (InitAVSync) Player(0): Video timing method: USleep with busy wait
Jan  7 06:29:24 bigtv mythfrontend[2918]: I CoreContext tv_play.cpp:5169 (StartPlayer) TV: Created player.
Jan  7 06:29:24 bigtv mythfrontend[2918]: I CoreContext tv_play.cpp:2360 (HandleStateChange) TV: Changing from None to WatchingPreRecorded
Jan  7 06:29:24 bigtv mythfrontend[2918]: I CoreContext tv_play.cpp:2451 (HandleStateChange) TV: Main UI disabled.
Jan  7 06:29:24 bigtv mythfrontend[2918]: I CoreContext tv_play.cpp:378 (StartTV) TV: Entering main playback loop.
Jan  7 06:29:25 bigtv mythfrontend[2918]: I CoreContext screensaver-x11.cpp:149 (DisableDPMS) ScreenSaverX11Private: DPMS Deactivated 1
Jan  7 06:29:25 bigtv mythfrontend[2918]: I CoreContext mythrender_vdpau.cpp:587 (CheckOutputSurfaces) VDPAU: Added 2 output surfaces (total 4, max 4)
Jan  7 06:29:32 bigtv mythfrontend[2918]: I CoreContext tv_play.cpp:2121 (HandleStateChange) TV: Attempting to change from WatchingPreRecorded to None
Jan  7 06:29:32 bigtv mythfrontend[2918]: I CoreContext mythpainter_vdpau.cpp:111 (ClearCache) VDPAU Painter: Clearing VDPAU painter cache.
Jan  7 06:29:32 bigtv mythfrontend[2918]: W CoreContext mythpainter.cpp:32 (~MythPainter) MythPainter: 25 images not yet de-allocated.
Jan  7 06:29:32 bigtv mythfrontend[2918]: I CoreContext audio/audiopulsehandler.cpp:320 (SuspendInternal) Pulse: PulseAudio resume OK
Jan  7 06:29:32 bigtv mythfrontend[2918]: I CoreContext tv_play.cpp:2360 (HandleStateChange) TV: Changing from WatchingPreRecorded to None
Jan  7 06:29:32 bigtv mythfrontend[2918]: I CoreContext tv_play.cpp:380 (StartTV) TV: Exiting main playback loop.
Jan  7 06:29:32 bigtv mythfrontend[2918]: I CoreContext screensaver-x11.cpp:161 (RestoreDPMS) ScreenSaverX11Private: DPMS Reactivated 1
Jan  7 06:29:32 bigtv mythfrontend[2918]: N CoreContext mythmainwindow.cpp:2591 (PauseIdleTimer) Resuming idle timer
```

Cheers

Stephen

---

### Post by BicyclerBoy on 2013-01-07
Alsa does not set the correct group for proc/asound..
This helps make the alsa buffer size nonsense go away:
```

# file /etc/rc.local ( before the exit 0)
# set audio as group for /proc/asound/
/bin/chown -hR root:audio /proc/asound
/bin/chmod 774 /proc/asound
/bin/chmod 774 /proc/asound/card0
/bin/chmod 774 /proc/asound/card0/pcm3p
/bin/chmod 774 /proc/asound/card0/pcm3p/sub0
/bin/chmod 774 /proc/asound/card0/pcm3p/sub0/prealloc
/bin/echo 1536 | tee /proc/asound/card0/pcm3p/sub0/prealloc

```

The above could be wrapped up more in a more compact fashion but I choose not to.

Check you do not have any custom filters added to vpdau profiles.

---

### Post by vagster on 2013-01-09
Confirmed that I had no custom filters enabled in any VDPAU profile.

Made the audio change as suggested and audio works fine.

Still no video on playback.

Frontend log:

```
Jan  9 21:07:20 bigtv mythfrontend[1807]: I Socket mythcorecontext.cpp:1103 (readyRead) Received remote 'Clear Cache' request
Jan  9 21:07:35 bigtv mythfrontend[1807]: I CoreContext tv_play.cpp:987 (TV) TV: Creating TV object
Jan  9 21:07:35 bigtv mythfrontend[1807]: N CoreContext mythmainwindow.cpp:2586 (PauseIdleTimer) Suspending idle timer
Jan  9 21:07:35 bigtv mythfrontend[1807]: I CoreContext tv_play.cpp:1206 (Init) TV: Created TvPlayWindow.
Jan  9 21:07:35 bigtv mythfrontend[1807]: I CoreContext tv_play.cpp:2121 (HandleStateChange) TV: Attempting to change from None to WatchingPreRecorded
Jan  9 21:07:35 bigtv mythfrontend[1807]: I CoreContext mythcorecontext.cpp:1178 (CheckProtoVersion) Using protocol version 72
Jan  9 21:07:35 bigtv mythfrontend[1807]: I CoreContext mythcorecontext.cpp:1178 (CheckProtoVersion) Using protocol version 72
Jan  9 21:07:36 bigtv mythfrontend[1807]: I CoreContext audio/audiopulsehandler.cpp:320 (SuspendInternal) Pulse: PulseAudio suspend OK
Jan  9 21:07:36 bigtv mythfrontend[1807]: N CoreContext audioplayer.cpp:167 (ReinitAudio) AudioPlayer: Enabling Audio
Jan  9 21:07:41 bigtv mythfrontend[1807]: I CoreContext avformatdecoder.cpp:2104 (ScanStreams) AFD: Opened codec 0xb0d6e00, id(MPEG2VIDEO) type(Video)
Jan  9 21:07:41 bigtv mythfrontend[1807]: I CoreContext avformatdecoder.cpp:1962 (ScanStreams) AFD: codec MP2 has 2 channels
Jan  9 21:07:41 bigtv mythfrontend[1807]: I CoreContext avformatdecoder.cpp:2104 (ScanStreams) AFD: Opened codec 0xb0d2440, id(MP2) type(Audio)
Jan  9 21:07:41 bigtv mythfrontend[1807]: I CoreContext avformatdecoder.cpp:1962 (ScanStreams) AFD: codec MP3 has 0 channels
Jan  9 21:07:41 bigtv mythfrontend[1807]: I CoreContext avformatdecoder.cpp:2104 (ScanStreams) AFD: Opened codec 0xb0d2a20, id(MP3) type(Audio)
Jan  9 21:07:41 bigtv mythfrontend[1807]: I CoreContext avformatdecoder.cpp:2104 (ScanStreams) AFD: Opened codec 0xb0d3000, id(DVB_SUBTITLE) type(Subtitle)
Jan  9 21:07:41 bigtv mythfrontend[1807]: I CoreContext audio/audiooutputbase.cpp:791 (Reconfigure) AO: Opening audio device 'hdmi' ch 2(2) sr 48000 sf signed 16 bit reenc 0
Jan  9 21:07:42 bigtv mythfrontend[1807]: E CoreContext audio/audiooutputalsa.cpp:937 (OpenMixer) ALSA: failed to register mixer device /dev/mixer: No such file or directory
Jan  9 21:07:42 bigtv mythfrontend[1807]: E CoreContext audio/audiooutputalsa.cpp:550 (OpenDevice) ALSA: Unable to open audio mixer. Volume control disabled
Jan  9 21:07:47 bigtv mythfrontend[1807]: I CoreContext mythrender_vdpau.cpp:1675 (CreatePresentationSurfaces) VDPAU: Created 2 output surfaces.
Jan  9 21:07:47 bigtv mythfrontend[1807]: I CoreContext mythrender_vdpau.cpp:1709 (CheckHardwareSupport) VDPAU: Version 1
Jan  9 21:07:47 bigtv mythfrontend[1807]: I CoreContext mythrender_vdpau.cpp:1716 (CheckHardwareSupport) VDPAU: Information NVIDIA VDPAU Driver Shared Library  295.40  Thu Apr  5 21:54:31 PDT 2012
Jan  9 21:07:47 bigtv mythfrontend[1807]: I CoreContext mythrender_vdpau.cpp:401 (Create) VDPAU: Created VDPAU render device 1920x1080
Jan  9 21:07:47 bigtv mythfrontend[1807]: N CoreContext mythplayer.cpp:506 (CheckExtraAudioDecode) Player(0): Forcing decode extra audio option on (Video method requires it).
Jan  9 21:07:48 bigtv mythfrontend[1807]: I CoreContext mythplayer.cpp:1737 (InitAVSync) Player(0): Video timing method: USleep with busy wait
Jan  9 21:07:48 bigtv mythfrontend[1807]: I CoreContext tv_play.cpp:5169 (StartPlayer) TV: Created player.
Jan  9 21:07:48 bigtv mythfrontend[1807]: I CoreContext tv_play.cpp:2360 (HandleStateChange) TV: Changing from None to WatchingPreRecorded
Jan  9 21:07:49 bigtv mythfrontend[1807]: I CoreContext tv_play.cpp:2451 (HandleStateChange) TV: Main UI disabled.
Jan  9 21:07:49 bigtv mythfrontend[1807]: I CoreContext tv_play.cpp:378 (StartTV) TV: Entering main playback loop.
Jan  9 21:07:50 bigtv mythfrontend[1807]: I CoreContext screensaver-x11.cpp:149 (DisableDPMS) ScreenSaverX11Private: DPMS Deactivated 1
Jan  9 21:07:50 bigtv mythfrontend[1807]: I CoreContext mythrender_vdpau.cpp:587 (CheckOutputSurfaces) VDPAU: Added 2 output surfaces (total 4, max 4)
Jan  9 21:07:53 bigtv mythfrontend[1807]: I CoreContext tv_play.cpp:2121 (HandleStateChange) TV: Attempting to change from WatchingPreRecorded to None
Jan  9 21:07:54 bigtv mythfrontend[1807]: I CoreContext mythpainter_vdpau.cpp:111 (ClearCache) VDPAU Painter: Clearing VDPAU painter cache.
Jan  9 21:07:54 bigtv mythfrontend[1807]: W CoreContext mythpainter.cpp:32 (~MythPainter) MythPainter: 25 images not yet de-allocated.
Jan  9 21:07:54 bigtv mythfrontend[1807]: I CoreContext audio/audiopulsehandler.cpp:320 (SuspendInternal) Pulse: PulseAudio resume OK
Jan  9 21:07:54 bigtv mythfrontend[1807]: I CoreContext tv_play.cpp:2360 (HandleStateChange) TV: Changing from WatchingPreRecorded to None
Jan  9 21:07:54 bigtv mythfrontend[1807]: I CoreContext tv_play.cpp:380 (StartTV) TV: Exiting main playback loop.
Jan  9 21:07:54 bigtv mythfrontend[1807]: I CoreContext screensaver-x11.cpp:161 (RestoreDPMS) ScreenSaverX11Private: DPMS Reactivated 1
Jan  9 21:07:54 bigtv mythfrontend[1807]: N CoreContext mythmainwindow.cpp:2591 (PauseIdleTimer) Resuming idle timer
Jan  9 21:08:09 bigtv mythfrontend[1807]: I CoreContext bonjourregister.cpp:27 (~BonjourRegister) Bonjour: De-registering service '_mythfrontend._tcp.' on 'Mythfrontend on bigtv'
Jan  9 21:08:09 bigtv mythfrontend[1807]: I CoreContext mythraopdevice.cpp:82 (Cleanup) RAOP Device: Cleaning up.
Jan  9 21:08:09 bigtv mythfrontend[1807]: I CoreContext mythairplayserver.cpp:260 (Cleanup) AirPay: Cleaning up.
Jan  9 21:08:09 bigtv mythfrontend[1807]: I CoreContext audio/audiopulsehandler.cpp:46 (Suspend) Pulse: Cleaning up PulseHandler
Jan  9 21:08:09 bigtv mythfrontend[1807]: I CoreContext main.cpp:244 (cleanup) Deleting UPnP client...
Jan  9 21:08:10 bigtv mythfrontend[1807]: I CoreContext mythcontext.cpp:1115 (~MythContext) Waiting for threads to exit.
```

From vdpauinfo

```
display: :0.0   screen: 0
API version: 1
Information string: NVIDIA VDPAU Driver Shared Library  295.40  Thu Apr  5 21:54:31 PDT 2012

Video surface:

name   width height types
-------------------------------------------
420     4096  4096  NV12 YV12 
422     4096  4096  UYVY YUYV 

Decoder capabilities:

name               level macbs width height
-------------------------------------------
MPEG1                 0  8192  2048  2048
MPEG2_SIMPLE          3  8192  2048  2048
MPEG2_MAIN            3  8192  2048  2048
H264_MAIN            41  8190  2032  2048
H264_HIGH            41  8190  2032  2048
VC1_SIMPLE            1  8190  2048  2048
VC1_MAIN              2  8190  2048  2048
VC1_ADVANCED          4  8190  2048  2048

Output surface:

name              width height nat types
----------------------------------------------------
B8G8R8A8          8192  8192    y  Y8U8V8A8 V8U8Y8A8 
R10G10B10A2       8192  8192    y  Y8U8V8A8 V8U8Y8A8 

Bitmap surface:

name              width height
------------------------------
B8G8R8A8          8192  8192
R8G8B8A8          8192  8192
R10G10B10A2       8192  8192
B10G10R10A2       8192  8192
A8                8192  8192

Video mixer:

feature name                    sup
------------------------------------
DEINTERLACE_TEMPORAL             y
DEINTERLACE_TEMPORAL_SPATIAL     y
INVERSE_TELECINE                 y
NOISE_REDUCTION                  y
SHARPNESS                        y
LUMA_KEY                         y
HIGH QUALITY SCALING - L1        -
HIGH QUALITY SCALING - L2        -
HIGH QUALITY SCALING - L3        -
HIGH QUALITY SCALING - L4        -
HIGH QUALITY SCALING - L5        -
HIGH QUALITY SCALING - L6        -
HIGH QUALITY SCALING - L7        -
HIGH QUALITY SCALING - L8        -
HIGH QUALITY SCALING - L9        -

parameter name                  sup      min      max
-----------------------------------------------------
VIDEO_SURFACE_WIDTH              y         1     4096
VIDEO_SURFACE_HEIGHT             y         1     4096
CHROMA_TYPE                      y  
LAYERS                           y         0        4

attribute name                  sup      min      max
-----------------------------------------------------
BACKGROUND_COLOR                 y  
CSC_MATRIX                       y  
NOISE_REDUCTION_LEVEL            y      0.00     1.00
SHARPNESS_LEVEL                  y     -1.00     1.00
LUMA_KEY_MIN_LUMA                y  
LUMA_KEY_MAX_LUMA                y  

```

Anybody else got an Acer Revo 3610 working with 12.04 and Ubuntu? Anything special you had to do?

Thanks

Stephen

---

### Post by BicyclerBoy on 2013-01-09
There was a similar problem couple months back...
Here's a link to the saga..
[http://ubuntuforums.org/showthread.php?t=2059325](http://ubuntuforums.org/showthread.php?t=2059325)

The only thing that worked was to change the frontend to a fresh/unused hostname..
This forced creation of new DB tables in the master BE database..

We couldn't find any incorrect video playback db settings..

---

### Post by diesel48 on 2013-01-11
Running a Revo 1600 with out troubles. One of my frontends was getting really laggy for some reason. Changed the hostname and it was good again. Switched from Mythdora to Mythbuntu with 4 frontends and one backend/frontend. Went pretty smooth. Something funky must have carried over from the database with one.

---

### Post by vagster on 2013-01-11
Wow. Changing the custom identifier for the frontend resolved the issue.

I had spotted that black screen thread in my searches but thought it was only to do with screens turning off.

Thanks very much everyone!

Stephen

---

### Post by BicyclerBoy on 2013-01-13
Thanks for reporting back..
You are the 3rd poster that has had this problem..

---

