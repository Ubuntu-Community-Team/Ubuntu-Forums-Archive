---
title: "OBS Studio crashed with SIGSEGV in avcodec_find_best_pix_fmt_of_list ( segmentation f"
date: 2020-09-24
forum: Multimedia Software
---

### Post by sosabz on 2020-09-24
My Obs Studio, after pressing record button, crash and close automatically and show this problem:


[ATTACH=CONFIG]287015[/ATTACH]

```
```
osb crashed with [sigsegv][2] in avcodec find best pix fmt of list

``````


And its log file is :

```

```
09:44:41 AM.440: CPU Name: Intel(R) Core(TM) i7-7500U CPU @ 2.70GHz
09:44:41 AM.440: CPU Speed: 800.040MHz
09:44:41 AM.441: Physical Cores: 2, Logical Cores: 4
09:44:41 AM.441: Physical Memory: 11882MB Total, 222MB Free
09:44:41 AM.441: Kernel Version: Linux 5.4.0-26-generic
09:44:41 AM.486: Distribution: "Ubuntu" "20.10"
09:44:41 AM.487: Window System: X11.0, Vendor: The X.Org Foundation, Version: 1.20.8
09:44:41 AM.535: Portable mode: false
09:44:43 AM.112: OBS 25.0.8+dfsg1-3 (linux)
09:44:43 AM.112: ---------------------------------
09:44:43 AM.118: ---------------------------------
09:44:43 AM.118: audio settings reset:
09:44:43 AM.118:     samples per sec: 44100
09:44:43 AM.118:     speakers:        2
09:44:43 AM.205: ---------------------------------
09:44:43 AM.205: Initializing OpenGL...
09:44:44 AM.174: Loading up OpenGL on adapter NVIDIA Corporation GeForce 920MX/PCIe/SSE2
09:44:44 AM.174: OpenGL loaded successfully, version 3.3.0 NVIDIA 450.51.06, shading language 3.30 NVIDIA via Cg compiler
09:44:44 AM.332: ---------------------------------
09:44:44 AM.332: video settings reset:
09:44:44 AM.332:     base resolution:   1680x1050
09:44:44 AM.332:     output resolution: 1680x1050
09:44:44 AM.332:     downscale filter:  Bicubic
09:44:44 AM.332:     fps:               30/1
09:44:44 AM.332:     format:            NV12
09:44:44 AM.332:     YUV mode:          601/Partial
09:44:44 AM.333: NV12 texture support not available
09:44:44 AM.370: Audio monitoring device:
09:44:44 AM.370:     name: Default
09:44:44 AM.370:     id: default
09:44:44 AM.376: ---------------------------------
09:44:44 AM.415: Failed to load 'en-US' text for module: 'decklink-ouput-ui.so'
09:44:45 AM.251: A DeckLink iterator could not be created.  The DeckLink drivers may not be installed
09:44:45 AM.251: No blackmagic support
09:44:46 AM.525: NVENC supported
09:44:46 AM.525: FFMPEG VAAPI supported
09:44:47 AM.096: VLC found, VLC video source enabled
09:44:47 AM.097: ---------------------------------
09:44:47 AM.097:   Loaded Modules:
09:44:47 AM.097:     vlc-video.so
09:44:47 AM.097:     text-freetype2.so
09:44:47 AM.097:     rtmp-services.so
09:44:47 AM.097:     obs-x264.so
09:44:47 AM.097:     obs-transitions.so
09:44:47 AM.097:     obs-outputs.so
09:44:47 AM.097:     obs-filters.so
09:44:47 AM.097:     obs-ffmpeg.so
09:44:47 AM.097:     linux-v4l2.so
09:44:47 AM.097:     linux-pulseaudio.so
09:44:47 AM.097:     linux-jack.so
09:44:47 AM.097:     linux-decklink.so
09:44:47 AM.097:     linux-capture.so
09:44:47 AM.097:     linux-alsa.so
09:44:47 AM.097:     image-source.so
09:44:47 AM.097:     frontend-tools.so
09:44:47 AM.097:     decklink-ouput-ui.so
09:44:47 AM.097: ---------------------------------
09:44:47 AM.163: ==== Startup complete ===============================================
09:44:47 AM.189: Service '' not found
09:44:47 AM.245: All scene data cleared
09:44:47 AM.245: ------------------------------------------------
09:44:47 AM.257: pulse-input: Server name: 'pulseaudio 13.99.1'
09:44:47 AM.259: pulse-input: Audio format: s16le, 44100 Hz, 2 channels
09:44:47 AM.259: pulse-input: Started recording from 'alsa_output.pci-0000_00_1f.3.analog-stereo.monitor'
09:44:47 AM.259: [Loaded global audio device]: 'Desktop Audio'
09:44:47 AM.363: pulse-input: Server name: 'pulseaudio 13.99.1'
09:44:47 AM.366: pulse-input: Audio format: s16le, 44100 Hz, 2 channels
09:44:47 AM.366: pulse-input: Started recording from 'alsa_input.pci-0000_00_1f.3.analog-stereo'
09:44:47 AM.366: [Loaded global audio device]: 'Mic/Aux'
09:44:47 AM.372: xshm-input: Geometry 1680x1050 @ 1920,0
09:44:47 AM.374: Switched to scene 'Scene'
09:44:47 AM.375: ------------------------------------------------
09:44:47 AM.375: Loaded scenes:
09:44:47 AM.375: - scene 'Scene':
09:44:47 AM.375:     - source: 'Screen Capture (XSHM)' (xshm_input)
09:44:47 AM.375: ------------------------------------------------
09:44:47 AM.938: adding 69 milliseconds of audio buffering, total audio buffering is now 69 milliseconds (source: Desktop Audio)
09:44:47 AM.938: 
```
```
also my OS version is :

```

```
so@sosa:/var/www/html$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu Groovy Gorilla (development branch)
Release:    20.10
Codename:    groovy


```
```
I have googled the `osb crashed with sigsegv in avcodec find best pix fmt of list
` and don't find any related solution, also i have asked about this problem here:

[https://askubuntu.com/questions/1276765/obs-studio-crash-when-start-recording-after-install-avatarify](https://askubuntu.com/questions/1276765/obs-studio-crash-when-start-recording-after-install-avatarify)

Which don't find any answer and today i have tried to reinstall OBS Studio by **Synaptic Package Manager** in Ubuntu which don't solved my problem, so i asked here.


Thanks for your attention.

---

### Post by QIII on 2020-09-24
Hello.

Please do not post large images.  Some users have slow connections or data limits ... or both.

Please use the paperclip button to attach files.  The will the thumbnailed and other users can choose to view them full sized or not.

Thanks.

---

### Post by Yellow Pasque on 2020-09-24
[https://github.com/obsproject/obs-studio/issues/3254#issuecomment-677781204](https://github.com/obsproject/obs-studio/issues/3254#issuecomment-677781204)

---

