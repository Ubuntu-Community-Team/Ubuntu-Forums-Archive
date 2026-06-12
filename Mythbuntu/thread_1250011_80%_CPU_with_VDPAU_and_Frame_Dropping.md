---
title: "80% CPU with VDPAU and Frame Dropping"
date: 2009-08-26
forum: Mythbuntu
---

### Post by zobcat on 2009-08-26
I'm using Avenard's repos for VDAUP support. However, mythfrontend.real is still above 80% cpu when playing video content. I have created my playing profiles accordingly. 

I'm using the M3N78-VM motherboard with GF8200. Others have gotten it to work with this board with no problem. I'm posting this new thread, because it seems the old one has been dead for a month. 

I also have a problem with video frames being dropped (too slow). I've made sure that "Aggressive sound card buffering" is unchecked and that "Extra audio buffering" is checked. Here is my output:

```
fal@fel:~$ mythfrontend.real -v playback
2009-08-26 00:43:53.294 Using runtime prefix = /usr
2009-08-26 00:43:53.305 XScreenSaver support enabled
2009-08-26 00:43:53.305 DPMS is active.
2009-08-26 00:43:53.306 Empty LocalHostName.
2009-08-26 00:43:53.306 Using localhost value of fel
2009-08-26 00:43:53.310 New DB connection, total: 1
2009-08-26 00:43:53.313 Connected to database 'mythconverg' at host: localhost
2009-08-26 00:43:53.313 Closing DB connection named 'DBManager0'
2009-08-26 00:43:53.314 Primary screen 0.
2009-08-26 00:43:53.315 Connected to database 'mythconverg' at host: localhost
2009-08-26 00:43:53.316 Using screen 0, 1680x1050 at 0,0
2009-08-26 00:43:53.335 user: 1000 effective user: 1000 before privileged thread
2009-08-26 00:43:53.335 user: 1000 effective user: 1000 run_priv_thread
2009-08-26 00:43:53.335 user: 1000 effective user: 1000 after privileged thread
2009-08-26 00:43:53.337 New DB connection, total: 2
2009-08-26 00:43:53.337 Connected to database 'mythconverg' at host: localhost
2009-08-26 00:43:53.339 mythfrontend version: 0.21.20080304-1 www.mythtv.org
2009-08-26 00:43:53.339 Enabled verbose msgs:  important general playback
2009-08-26 00:43:53.750 max_width: 1680 max_height: 1050
2009-08-26 00:43:53.785 No theme dir: /home/fal/.mythtv/themes/blootubelite-wide
2009-08-26 00:43:53.786 Primary screen 0.
2009-08-26 00:43:53.786 Using screen 0, 1680x1050 at 0,0
2009-08-26 00:43:53.787 No theme dir: /home/fal/.mythtv/themes/blootubelite-wide
2009-08-26 00:43:53.787 Switching to wide mode (blootubelite-wide)
2009-08-26 00:43:53.796 Using the Qt painter
2009-08-26 00:43:53.796 JoystickMenuClient Error: Joystick disabled - Failed to read /home/fal/.mythtv/joystickmenurc
2009-08-26 00:43:53.798 lirc init success using configuration file: /home/fal/.mythtv/lircrc
2009-08-26 00:43:54.554 Specified base font 'medium' does not exist for font small
2009-08-26 00:43:54.554 Specified base font 'medium' does not exist for font medium
2009-08-26 00:43:54.554 Specified base font 'medium' does not exist for font large
2009-08-26 00:43:54.554 Specified base font 'medium' does not exist for font clock
2009-08-26 00:43:54.555 Loading from: /usr/share/mythtv/themes/blootubelite-wide/base.xml
2009-08-26 00:43:54.611 Loading from: /usr/share/mythtv/themes/default/base.xml
2009-08-26 00:43:54.667 Registering Internal as a media playback plugin.
2009-08-26 00:43:54.755 MonitorRegisterExtensions(0x100, gif,jpg,png)
2009-08-26 00:43:54.776 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
2009-08-26 00:43:54.796 No theme dir: /home/fal/.mythtv/themes/blootubelite-wide
2009-08-26 00:43:58.342 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-08-26 00:43:58.344 Using protocol version 40
2009-08-26 00:43:58.363 TV: Attempting to change from None to WatchingLiveTV
2009-08-26 00:43:58.364 Using protocol version 40
2009-08-26 00:43:59.929 LiveTVChain(live-fel-2009-08-26T00:43:58): ReloadAll(): Added new recording
2009-08-26 00:43:59.969 TV: StartRecorder(): took 28 ms to start recorder.
2009-08-26 00:43:59.976 DPMS Deactivated 
2009-08-26 00:43:59.994 New DB connection, total: 3
2009-08-26 00:43:59.994 Connected to database 'mythconverg' at host: localhost
2009-08-26 00:44:00.009 detectInterlace(Ignore Scan, Interlaced Scan, 25, 576) ->Interlaced Scan
2009-08-26 00:44:00.012 NVP: Disabling Audio, params(-1,2,44100)
2009-08-26 00:44:00.124 VDPAU: Version 0
2009-08-26 00:44:00.124 VDPAU: Information NVIDIA VDPAU Driver Shared Library  190.25  Thu Aug 20 18:31:10 PDT 2009
2009-08-26 00:44:00.824 VideoOutput: Allowed renderers: directfb,xv-blit,xshm,opengl,vdpau,xlib
2009-08-26 00:44:00.825 VideoOutput: Allowed renderers (filt: dummy): xlib,xshm,directfb,xv-blit,opengl
2009-08-26 00:44:00.831 VDP: Accepting: cmp(< 1920 720) dec(vdpau) cpus(0) skiploop(enabled) rend(vdpau) osd(vdpau) osdfade(enabled) deint(vdpauadvanceddoublerate,none) filt()
2009-08-26 00:44:00.832 VDP: Accepting: cmp(>= 0 720) dec(ffmpeg) cpus(0) skiploop(enabled) rend(vdpau) osd(vdpau) osdfade(enabled) deint(vdpaubasicdoublerate,none) filt()
2009-08-26 00:44:00.832 VDP: LoadBestPreferences(2048x2048, 0)
2009-08-26 00:44:00.832 VDP: LoadBestPreferences(2048x2048, 60)
2009-08-26 00:44:00.833 VDP: LoadBestPreferences(720x576, 60)
2009-08-26 00:44:00.833 VideoOutput: Trying video renderer: xv-blit
2009-08-26 00:44:00.840 VDP: Accepting: cmp(< 1920 720) dec(vdpau) cpus(0) skiploop(enabled) rend(vdpau) osd(vdpau) osdfade(enabled) deint(vdpauadvanceddoublerate,none) filt()
2009-08-26 00:44:00.840 VDP: Accepting: cmp(>= 0 720) dec(ffmpeg) cpus(0) skiploop(enabled) rend(vdpau) osd(vdpau) osdfade(enabled) deint(vdpaubasicdoublerate,none) filt()
2009-08-26 00:44:00.840 VDP: LoadBestPreferences(2048x2048, 0)
2009-08-26 00:44:00.840 VDP: LoadBestPreferences(2048x2048, 60)
2009-08-26 00:44:00.854 VideoOutputXv: ctor
2009-08-26 00:44:00.878 XOff: 0, YOff: 0
2009-08-26 00:44:00.878 VDP: LoadBestPreferences(720x576, 60)
2009-08-26 00:44:00.878 Display Rect  left: 0, top: 0, width: 1680, height: 1050, aspect: 1.33333
2009-08-26 00:44:00.878 Video Rect    left: 0, top: 0, width: 720, height: 576, aspect: 1.33333
2009-08-26 00:44:00.880 VideoOutputXv: Pixel dimensions: Screen 1680x1050, window 1680x1050
2009-08-26 00:44:00.881 VideoOutputXv: Estimated display dimensions: 427x267 mm  Aspect: 1.59925
2009-08-26 00:44:00.881 VideoOutputXv: Estimated window dimensions: 427x267 mm  Aspect: 1.59925
2009-08-26 00:44:00.950 VideoOutputXv: InitSetupBuffers() render: vdpau, allowed: xv-blit,xshm,opengl,vdpau,xlib
2009-08-26 00:44:01.027 Created data @0xab718020->0xab7afe22
2009-08-26 00:44:01.028 Created data @0xab680020->0xab717e22
2009-08-26 00:44:01.028 Created data @0xab5e8020->0xab67fe22
2009-08-26 00:44:01.028 Created data @0xab550020->0xab5e7e22
2009-08-26 00:44:01.028 Created data @0xab4b8020->0xab54fe22
2009-08-26 00:44:01.028 Created data @0xab420020->0xab4b7e22
2009-08-26 00:44:01.028 Created data @0xab388020->0xab41fe22
2009-08-26 00:44:01.029 Created data @0xab2f0020->0xab387e22
2009-08-26 00:44:01.029 Created data @0xab258020->0xab2efe22
2009-08-26 00:44:01.029 Created data @0xab1c0020->0xab257e22
2009-08-26 00:44:01.029 Created data @0xab128020->0xab1bfe22
2009-08-26 00:44:01.029 Created data @0xab090020->0xab127e22
2009-08-26 00:44:01.029 Created data @0xaaff8020->0xab08fe22
2009-08-26 00:44:01.029 Created data @0xaaf60020->0xaaff7e22
2009-08-26 00:44:01.029 Created data @0xaaec8020->0xaaf5fe22
2009-08-26 00:44:01.030 Created data @0xaae30020->0xaaec7e22
2009-08-26 00:44:01.030 Created data @0xaad98020->0xaae2fe22
2009-08-26 00:44:01.062 VideoOutputXv: Created VDPAU context (software decode)
2009-08-26 00:44:01.062 VDP: SetVideoRenderer(vdpau)
2009-08-26 00:44:01.062 VDP: SetVideoRender(vdpau) == GetVideoRenderer()
2009-08-26 00:44:01.107 VDPAU: Created OSD (1680x1050)
2009-08-26 00:44:01.107 VideoOutputXv: VDPAU Colorkey: 0x20202 (depth 24)
2009-08-26 00:44:01.108 Display Rect  left: 139, top: 0, width: 1401, height: 1050, aspect: 1.59925
2009-08-26 00:44:01.108 Video Rect    left: 0, top: 0, width: 720, height: 576, aspect: 1.33333
2009-08-26 00:44:01.111 Over/underscan. V: 0, H: 0
2009-08-26 00:44:01.111 Display Rect  left: 139, top: 0, width: 1401, height: 1050, aspect: 1.59925
2009-08-26 00:44:01.112 Video Rect    left: 0, top: 0, width: 720, height: 576, aspect: 1.33333
2009-08-26 00:44:01.112 VDP: LoadBestPreferences(720x576, 25)
2009-08-26 00:44:01.114 NVP: LoadFilters(''..) -> 0
2009-08-26 00:44:01.117 OSD Theme Dimensions W: 640 H: 480
2009-08-26 00:44:01.478 TV: StartPlayer(): took 1470 ms to start player.
2009-08-26 00:44:01.478 TV: Changing from None to WatchingLiveTV
2009-08-26 00:44:01.478 NVP: ClearAfterSeek(1)
2009-08-26 00:44:01.478 VideoOutputXv: ClearAfterSeek()
2009-08-26 00:44:01.478 VideoOutputXv: DiscardFrames(0)
2009-08-26 00:44:01.478 VideoBuffers::DiscardFrames(0): AAAAAAAAAAAAAAAAA
2009-08-26 00:44:01.479 VideoBuffers::DiscardFrames(0): AAAAAAAAAAAAAAAAA -- done
2009-08-26 00:44:01.479 VideoOutputXv: DiscardFrames() 3: AAAAAAAAAAAAAAAAA -- done()
2009-08-26 00:44:01.479 Realtime priority would require SUID as root.
2009-08-26 00:44:01.480 VDP: GetFilteredDeint() : vdpau -> 'vdpauadvanceddoublerate'
2009-08-26 00:44:01.480 rate: 25 speed: 1 skip: 1 = interval 40000
2009-08-26 00:44:01.596 nVidiaVideoSync: VBlank ioctl did not work, unimplemented in this driver?
2009-08-26 00:44:01.597 DRMVideoSync: Could not open device /dev/dri/card0, No such file or directory
2009-08-26 00:44:01.597 RTCVideoSync: Could not open /dev/rtc, Permission denied.
2009-08-26 00:44:01.597 Set video sync frame interval to 40000
2009-08-26 00:44:01.597 Using audio as timebase
2009-08-26 00:44:01.597 Video timing method: USleep with busy wait
2009-08-26 00:44:01.597 Refresh rate: 16699, frame interval: 40000
2009-08-26 00:44:01.638 VideoOutputXv: UpdatePauseFrame() AAAAAAAAAAAAAAAAA
2009-08-26 00:44:01.802 LiveTVChain(live-fel-2009-08-26T00:43:58): ReloadAll(): Added new recording
2009-08-26 00:44:01.803 LiveTVChain(live-fel-2009-08-26T00:43:58): SwitchTo(1)
2009-08-26 00:44:01.803 LiveTVChain(live-fel-2009-08-26T00:43:58): Entry@1: '1201_20090826004400'
2009-08-26 00:44:01.803 JumpToProgram(void)
2009-08-26 00:44:01.816 RingBuf(/var/lib/mythtv/recordings/1201_20090826004358.mpg): OpenFile(/var/lib/mythtv/recordings/1201_20090826004400.mpg, 12)
2009-08-26 00:44:01.820 RingBuf(/var/lib/mythtv/recordings/1201_20090826004400.mpg): CalcReadAheadThresh(3086199216 KB)
			 -> threshhold(64 KB) min read(0 KB) blk size(32 KB)
2009-08-26 00:44:01.934 NVP: Waiting for prebuffer..  0 AAAAAAAAAAAAAAAAA
2009-08-26 00:44:02.134 VideoOutputXv: UpdatePauseFrame() AAAAAAAAAAAAAAAAA
2009-08-26 00:44:02.137 NVP: Waiting for prebuffer..  1 AAAAAAAAAAAAAAAAA
2009-08-26 00:44:02.337 VideoOutputXv: UpdatePauseFrame() AAAAAAAAAAAAAAAAA
2009-08-26 00:44:02.340 NVP: Waiting for prebuffer..  2 AAAAAAAAAAAAAAAAA
2009-08-26 00:44:02.541 VideoOutputXv: UpdatePauseFrame() AAAAAAAAAAAAAAAAA
2009-08-26 00:44:02.549 VDPAU: Using 4 output surfaces (max 4)
2009-08-26 00:44:02.549 NVP: Waiting for prebuffer..  3 AAAAAAAAAAAAAAAAA
2009-08-26 00:44:02.740 AFD: Stream #0, has id 0x49 codec id MPEG2VIDEO, type Video, bitrate 14950000 at 0x0xaf59dc50
2009-08-26 00:44:02.743 VDP: Accepting: cmp(< 1920 720) dec(vdpau) cpus(0) skiploop(enabled) rend(vdpau) osd(vdpau) osdfade(enabled) deint(vdpauadvanceddoublerate,none) filt()
2009-08-26 00:44:02.743 VDP: Accepting: cmp(>= 0 720) dec(ffmpeg) cpus(0) skiploop(enabled) rend(vdpau) osd(vdpau) osdfade(enabled) deint(vdpaubasicdoublerate,none) filt()
2009-08-26 00:44:02.743 VDP: LoadBestPreferences(2048x2048, 0)
2009-08-26 00:44:02.743 VDP: LoadBestPreferences(2048x2048, 60)
2009-08-26 00:44:02.744 VDP: LoadBestPreferences(1280x720, 60)
2009-08-26 00:44:02.745 VDP: Accepting: cmp(< 1920 720) dec(vdpau) cpus(0) skiploop(enabled) rend(vdpau) osd(vdpau) osdfade(enabled) deint(vdpauadvanceddoublerate,none) filt()
2009-08-26 00:44:02.746 VDP: Accepting: cmp(>= 0 720) dec(ffmpeg) cpus(0) skiploop(enabled) rend(vdpau) osd(vdpau) osdfade(enabled) deint(vdpaubasicdoublerate,none) filt()
2009-08-26 00:44:02.746 VDP: LoadBestPreferences(2048x2048, 0)
2009-08-26 00:44:02.746 VDP: LoadBestPreferences(2048x2048, 60)
2009-08-26 00:44:02.746 VDP: LoadBestPreferences(1280x720, 60)
2009-08-26 00:44:02.746 Using 0 CPUs for decoding
2009-08-26 00:44:02.747 AFD: InitVideoCodec() 0xb1ba11d0 id(MPEG2VIDEO) type (Video).
2009-08-26 00:44:02.747 VideoOutputXv: InputChanged(1280,720,1.77778) 'None'->'MPEG2'
2009-08-26 00:44:02.747 VDP: LoadBestPreferences(1280x720, 25)
2009-08-26 00:44:02.747 VDP: GetFilteredDeint() : vdpau -> 'vdpaubasicdoublerate'
2009-08-26 00:44:02.784 VDP: GetFilteredDeint() : vdpau -> 'vdpaubasicdoublerate'
2009-08-26 00:44:02.820 VideoOutputXv: DiscardFrames(1)
2009-08-26 00:44:02.820 VideoBuffers::DiscardFrames(1): AAAAAAAAAAAAAAAAA
2009-08-26 00:44:02.821 VideoBuffers::DiscardFrames(): AAAAAAAAAAAAAAAAA -- done()
2009-08-26 00:44:02.821 VideoBuffers::DiscardFrames(1): AAAAAAAAAAAAAAAAA -- done
2009-08-26 00:44:02.821 VideoOutputXv: DiscardFrames() 3: AAAAAAAAAAAAAAAAA -- done()
2009-08-26 00:44:02.821 VideoOutputXv: DiscardFrames(1)
2009-08-26 00:44:02.821 VideoBuffers::DiscardFrames(1): AAAAAAAAAAAAAAAAA
2009-08-26 00:44:02.822 VideoBuffers::DiscardFrames(): AAAAAAAAAAAAAAAAA -- done()
2009-08-26 00:44:02.822 VideoBuffers::DiscardFrames(1): AAAAAAAAAAAAAAAAA -- done
2009-08-26 00:44:02.822 VideoOutputXv: DiscardFrames() 3: AAAAAAAAAAAAAAAAA -- done()
2009-08-26 00:44:02.899 VideoOutputXv: DiscardFrames(1)
2009-08-26 00:44:02.899 VideoBuffers::DiscardFrames(1): AAAAAAAAAAAAAAAAA
2009-08-26 00:44:02.899 VideoBuffers::DiscardFrames(): AAAAAAAAAAAAAAAAA -- done()
2009-08-26 00:44:02.899 VideoBuffers::DiscardFrames(1): AAAAAAAAAAAAAAAAA -- done
2009-08-26 00:44:02.899 VideoOutputXv: DiscardFrames() 3: AAAAAAAAAAAAAAAAA -- done()
2009-08-26 00:44:02.930 VideoOutputXv: InitSetupBuffers() render: vdpau, allowed: xv-blit,xshm,opengl,vdpau,xlib
2009-08-26 00:44:02.972 Created data @0xab65e020->0xab7af822
2009-08-26 00:44:02.972 Created data @0xab50c020->0xab65d822
2009-08-26 00:44:02.972 Created data @0xab3ba020->0xab50b822
2009-08-26 00:44:02.972 Created data @0xab268020->0xab3b9822
2009-08-26 00:44:02.972 Created data @0xab116020->0xab267822
2009-08-26 00:44:02.972 Created data @0xaafc4020->0xab115822
2009-08-26 00:44:02.972 Created data @0xaae72020->0xaafc3822
2009-08-26 00:44:02.972 Created data @0xa7dae020->0xa7eff822
2009-08-26 00:44:02.972 Created data @0xa7c5c020->0xa7dad822
2009-08-26 00:44:02.972 Created data @0xa7b0a020->0xa7c5b822
2009-08-26 00:44:02.972 Created data @0xa79b8020->0xa7b09822
2009-08-26 00:44:02.972 Created data @0xa7866020->0xa79b7822
2009-08-26 00:44:02.973 Created data @0xa7714020->0xa7865822
2009-08-26 00:44:02.973 Created data @0xa75c2020->0xa7713822
2009-08-26 00:44:02.973 Created data @0xa7470020->0xa75c1822
2009-08-26 00:44:02.973 Created data @0xa731e020->0xa746f822
2009-08-26 00:44:02.973 Created data @0xa71cc020->0xa731d822
2009-08-26 00:44:02.994 VideoOutputXv: Created VDPAU context (software decode)
2009-08-26 00:44:02.994 VDP: SetVideoRenderer(vdpau)
2009-08-26 00:44:02.994 VDP: SetVideoRender(vdpau) == GetVideoRenderer()
2009-08-26 00:44:03.013 VDPAU: Created OSD (1680x1050)
2009-08-26 00:44:03.016 VideoOutputXv: VDPAU Colorkey: 0x20202 (depth 24)
2009-08-26 00:44:03.016 Display Rect  left: 0, top: 52, width: 1680, height: 945, aspect: 1.59925
2009-08-26 00:44:03.016 Video Rect    left: 0, top: 0, width: 1280, height: 720, aspect: 1.77778
2009-08-26 00:44:03.016 VDP: GetFilteredDeint() : vdpau -> 'vdpaubasicdoublerate'
2009-08-26 00:44:03.017 VDP: GetFilteredDeint() : vdpau -> 'vdpaubasicdoublerate'
2009-08-26 00:44:03.032 VideoOutputXv: UpdatePauseFrame() AAAAAAAAAAAAAAAAA
2009-08-26 00:44:03.032 VDP: LoadBestPreferences(1280x720, 59.9401)
2009-08-26 00:44:03.131 NVP: ClearAfterSeek(1)
2009-08-26 00:44:03.132 VideoOutputXv: ClearAfterSeek()
2009-08-26 00:44:03.132 VideoOutputXv: DiscardFrames(0)
2009-08-26 00:44:03.132 VideoBuffers::DiscardFrames(0): AAAAAAAAAAAAAAAAA
2009-08-26 00:44:03.132 VideoBuffers::DiscardFrames(0): AAAAAAAAAAAAAAAAA -- done
2009-08-26 00:44:03.132 VideoOutputXv: DiscardFrames() 3: AAAAAAAAAAAAAAAAA -- done()
2009-08-26 00:44:03.132 NVP: LoadFilters(''..) -> 0
2009-08-26 00:44:03.132 detectInterlace(Detect Scan, Interlaced Scan, 59.9401, 720) ->Progressive Scan
2009-08-26 00:44:03.132 Set video sync frame interval to 16683
2009-08-26 00:44:03.134 NVP: Waiting for prebuffer..  4 AAAAAAAAAAAAAAAAA
2009-08-26 00:44:03.153 Disabled deinterlacing
2009-08-26 00:44:03.154 AFD: Using ffmpeg for video decoding
2009-08-26 00:44:03.154 AFD: Looking for decoder for MPEG2VIDEO
2009-08-26 00:44:03.154 AFD: Opened codec 0xb1ba11d0, id(MPEG2VIDEO) type(Video)
2009-08-26 00:44:03.154 AFD: Stream #1, has id 0x52 codec id AC3, type Audio, bitrate 384000 at 0x0xb1b3a2a0
2009-08-26 00:44:03.154 AFD: codec AC3 has 2 channels
2009-08-26 00:44:03.154 AFD: Looking for decoder for AC3
2009-08-26 00:44:03.154 AFD: Opened codec 0xb1b50aa0, id(AC3) type(Audio)
2009-08-26 00:44:03.154 AFD: Stream #2, has id 0x53 codec id AC3, type Audio, bitrate 192000 at 0x0xaeedb020
2009-08-26 00:44:03.155 AFD: codec AC3 has 1 channels
2009-08-26 00:44:03.155 AFD: Looking for decoder for AC3
2009-08-26 00:44:03.155 AFD: Opened codec 0xb1bbdde0, id(AC3) type(Audio)
2009-08-26 00:44:03.217 VideoOutputXv: UpdatePauseFrame() AAAAAAAAAAAAAAAAA
2009-08-26 00:44:03.223 RingBuf(/var/lib/mythtv/recordings/1201_20090826004400.mpg): CalcReadAheadThresh(3086175867 KB)
			 -> threshhold(64 KB) min read(0 KB) blk size(32 KB)
2009-08-26 00:44:03.235 Opening audio device 'default'. ch 2(2) sr 48000
2009-08-26 00:44:03.236 Opening ALSA audio device 'default'.
2009-08-26 00:44:03.271 NVP: Waiting for prebuffer..  5 AAAAAAAAAAAAAAAAA
2009-08-26 00:44:03.343 Mixer unable to find control Master
2009-08-26 00:44:03.343 Mixer unable to find control Master
2009-08-26 00:44:03.344 NVP: Enabling Audio
2009-08-26 00:44:03.344 Dec: Trying to select track (w/lang)
2009-08-26 00:44:03.344 Dec: Selecting first track
2009-08-26 00:44:03.344 Dec: Selected track #1 in the Unknown language(0)
2009-08-26 00:44:03.344 Resyncing position map. posmapStarted = 0 livetv(1) watchingRec(1)
2009-08-26 00:44:03.345 SyncPositionMap watchingrecording, from DB: 0 entries
2009-08-26 00:44:03.345 Filling position map from 0 to 77
2009-08-26 00:44:03.346 Position map filled from Encoder to: 72
2009-08-26 00:44:03.346 SyncPositionMap watchingrecording total: 7 entries
2009-08-26 00:44:03.346 SyncPositionMap, new totframes: 72, new length: 1, posMap size: 7
2009-08-26 00:44:03.346 AFD: Partial position map found
2009-08-26 00:44:03.346 AFD: Successfully opened decoder for file: "/var/lib/mythtv/recordings/1201_20090826004400.mpg". novideo(0)
2009-08-26 00:44:03.347 NVP: DoPlay: rate: 59.9401 speed: 1 skip: 1 => new interval 16683
2009-08-26 00:44:03.347 Set video sync frame interval to 16683
2009-08-26 00:44:03.348 NVP: Stretch Factor 1, allow passthru 
2009-08-26 00:44:03.349 RingBuf(/var/lib/mythtv/recordings/1201_20090826004400.mpg): CalcReadAheadThresh(3086175867 KB)
			 -> threshhold(64 KB) min read(0 KB) blk size(32 KB)
2009-08-26 00:44:03.349 Resyncing position map. posmapStarted = 0 livetv(1) watchingRec(1)
2009-08-26 00:44:03.349 SyncPositionMap watchingrecording, from DB: 7 entries
2009-08-26 00:44:03.350 Filling position map from 73 to 77
2009-08-26 00:44:03.350 Position map filled from Encoder to: 72
2009-08-26 00:44:03.350 SyncPositionMap watchingrecording total: 7 entries
2009-08-26 00:44:03.355 VideoOutputXv: UpdatePauseFrame() LAAAAAAAAAAAAAAAA
2009-08-26 00:44:03.362 NVP: Waiting for prebuffer..  6 LAAAAAAAAAAAAAAAA
2009-08-26 00:44:03.428 NVP: Waiting for prebuffer..  7 uLAAAAAAAAAAAAAAA
2009-08-26 00:44:03.439 NVP: prebuffering pause
2009-08-26 00:44:03.439 NVP: Waiting for prebuffer..  0 aLLAAAAAAAAAAAAAA
2009-08-26 00:44:03.517 VDPAU: Using 4 output surfaces (max 4)
2009-08-26 00:44:03.565 Dec: Selected track #1 in the Unknown language(0)
2009-08-26 00:44:03.666 NVP: prebuffering pause
2009-08-26 00:44:03.666 NVP: Waiting for prebuffer..  0 AAAAAAAAAAaAALLAA
2009-08-26 00:44:03.685 NVP: prebuffering pause
2009-08-26 00:44:03.685 NVP: Waiting for prebuffer..  0 AAAAAAAAAAaAALALA
2009-08-26 00:44:03.703 NVP: prebuffering pause
2009-08-26 00:44:03.703 NVP: Waiting for prebuffer..  0 AAAAAAAAAAAAALAAL
2009-08-26 00:44:03.712 NVP: prebuffering pause
2009-08-26 00:44:03.712 NVP: Waiting for prebuffer..  0 LAAAAAAAAAAAAaAAL
2009-08-26 00:44:03.721 NVP: prebuffering pause
2009-08-26 00:44:03.733 NVP: Waiting for prebuffer..  0 AAULAAAAAAAAAAAAL
'video_output' mean = '17033.75', std. dev. = '3147.19', fps = '58.71'
2009-08-26 00:44:06.384 NVP: Video is 5.21381 frames behind audio (too slow), dropping frame to catch up.
2009-08-26 00:44:06.421 NVP: Video is 7.38692 frames behind audio (too slow), dropping frame to catch up.
2009-08-26 00:44:06.458 NVP: Video is 9.3015 frames behind audio (too slow), dropping frame to catch up.
2009-08-26 00:44:06.495 NVP: Video is 11.0371 frames behind audio (too slow), dropping frame to catch up.
2009-08-26 00:44:06.532 NVP: Video is 12.6535 frames behind audio (too slow), dropping frame to catch up.
2009-08-26 00:44:06.534 WriteAudio: buffer underrun
2009-08-26 00:44:06.569 NVP: Video is 13.686 frames behind audio (too slow), dropping frame to catch up.
2009-08-26 00:44:06.607 NVP: Video is 14.7152 frames behind audio (too slow), dropping frame to catch up.
2009-08-26 00:44:06.615 WriteAudio: buffer underrun
2009-08-26 00:44:06.646 NVP: Video is 15.2172 frames behind audio (too slow), dropping frame to catch up.
2009-08-26 00:44:06.676 WriteAudio: buffer underrun
2009-08-26 00:44:06.691 NVP: Video is 15.8036 frames behind audio (too slow), dropping frame to catch up.
2009-08-26 00:44:06.734 NVP: Video is 16.2134 frames behind audio (too slow), dropping frame to catch up.
2009-08-26 00:44:06.762 WriteAudio: buffer underrun
2009-08-26 00:44:06.777 NVP: Video is 16.5657 frames behind audio (too slow), dropping frame to catch up.
2009-08-26 00:44:06.813 NVP: Video is 16.785 frames behind audio (too slow), dropping frame to catch up.
2009-08-26 00:44:06.849 NVP: Video is 16.9645 frames behind audio (too slow), dropping frame to catch up.
2009-08-26 00:44:06.852 WriteAudio: buffer underrun
2009-08-26 00:44:06.886 NVP: Video is 16.8593 frames behind audio (too slow), dropping frame to catch up.
2009-08-26 00:44:06.920 WriteAudio: buffer underrun
2009-08-26 00:44:06.923 NVP: Video is 17.0052 frames behind audio (too slow), dropping frame to catch up.
2009-08-26 00:44:06.960 NVP: Video is 16.8898 frames behind audio (too slow), dropping frame to catch up.
2009-08-26 00:44:06.993 WriteAudio: buffer underrun
2009-08-26 00:44:06.996 NVP: Video is 17.0131 frames behind audio (too slow), dropping frame to catch up.
2009-08-26 00:44:07.032 NVP: Video is 16.8807 frames behind audio (too slow), dropping frame to catch up.
2009-08-26 00:44:07.068 NVP: Video is 16.9912 frames behind audio (too slow), dropping frame to catch up.
2009-08-26 00:44:07.077 WriteAudio: buffer underrun
2009-08-26 00:44:07.107 NVP: Video is 16.8194 frames behind audio (too slow), dropping frame to catch up.
2009-08-26 00:44:07.123 WriteAudio: buffer underrun
2009-08-26 00:44:07.144 NVP: Video is 16.8703 frames behind audio (too slow), dropping frame to catch up.
2009-08-26 00:44:07.181 NVP: Video is 17.0584 frames behind audio (too slow), dropping frame to catch up.
2009-08-26 00:44:07.190 WriteAudio: buffer underrun
2009-08-26 00:44:07.219 NVP: Video is 17.0646 frames behind audio (too slow), dropping frame to catch up.
2009-08-26 00:44:07.254 NVP: Video is 17.2491 frames behind audio (too slow), dropping frame to catch up.
2009-08-26 00:44:07.275 WriteAudio: buffer underrun
2009-08-26 00:44:07.287 NVP: Video is 17.1776 frames behind audio (too slow), dropping frame to catch up.
2009-08-26 00:44:07.321 NVP: Video is 17.0491 frames behind audio (too slow), dropping frame to catch up.
2009-08-26 00:44:07.355 NVP: Video is 17.2224 frames behind audio (too slow), dropping frame to catch up.
2009-08-26 00:44:07.375 WriteAudio: buffer underrun
2009-08-26 00:44:07.394 NVP: Video is 17.3674 frames behind audio (too slow), dropping frame to catch up.
2009-08-26 00:44:07.428 NVP: Video is 17.5061 frames behind audio (too slow), dropping frame to catch up.
2009-08-26 00:44:07.448 WriteAudio: buffer underrun
2009-08-26 00:44:07.462 NVP: Video is 17.5802 frames behind audio (too slow), dropping frame to catch up.
2009-08-26 00:44:07.496 NVP: Video is 17.5759 frames behind audio (too slow), dropping frame to catch up.
2009-08-26 00:44:07.515 WriteAudio: buffer underrun
2009-08-26 00:44:07.530 NVP: Video is 17.6175 frames behind audio (too slow), dropping frame to catch up.
2009-08-26 00:44:07.569 NVP: Video is 17.5888 frames behind audio (too slow), dropping frame to catch up.
2009-08-26 00:44:07.586 WriteAudio: buffer underrun
2009-08-26 00:44:07.603 NVP: Video is 17.5973 frames behind audio (too slow), dropping frame to catch up.
2009-08-26 00:44:07.636 NVP: Video is 17.5736 frames behind audio (too slow), dropping frame to catch up.
2009-08-26 00:44:07.655 WriteAudio: buffer underrun
2009-08-26 00:44:07.670 NVP: Video is 17.5559 frames behind audio (too slow), dropping frame to catch up.
2009-08-26 00:44:07.705 NVP: Video is 17.5276 frames behind audio (too slow), dropping frame to catch up.
2009-08-26 00:44:07.725 WriteAudio: buffer underrun
2009-08-26 00:44:07.743 NVP: Video is 17.5064 frames behind audio (too slow), dropping frame to catch up.
2009-08-26 00:44:07.777 NVP: Video is 17.5055 frames behind audio (too slow), dropping frame to catch up.
2009-08-26 00:44:07.798 WriteAudio: buffer underrun
2009-08-26 00:44:07.811 NVP: Video is 17.4599 frames behind audio (too slow), dropping frame to catch up.
2009-08-26 00:44:07.845 NVP: Video is 17.3807 frames behind audio (too slow), dropping frame to catch up.
'video_output' mean = '27028.62', std. dev. = '15701.83', fps = '37.00'
2009-08-26 00:44:07.863 WriteAudio: buffer underrun
2009-08-26 00:44:07.879 NVP: Video is 17.3513 frames behind audio (too slow), dropping frame to catch up.
2009-08-26 00:44:07.913 NVP: Video is 17.3142 frames behind audio (too slow), dropping frame to catch up.
2009-08-26 00:44:07.931 WriteAudio: buffer underrun
2009-08-26 00:44:07.951 NVP: Video is 17.2714 frames behind audio (too slow), dropping frame to catch up.
2009-08-26 00:44:07.985 NVP: Video is 17.2843 frames behind audio (too slow), dropping frame to catch up.
2009-08-26 00:44:08.004 WriteAudio: buffer underrun
2009-08-26 00:44:08.020 NVP: Video is 17.234 frames behind audio (too slow), dropping frame to catch up.
2009-08-26 00:44:08.054 NVP: Video is 17.1813 frames behind audio (too slow), dropping frame to catch up.
2009-08-26 00:44:08.073 WriteAudio: buffer underrun
2009-08-26 00:44:08.087 NVP: Video is 17.1418 frames behind audio (too slow), dropping frame to catch up.
2009-08-26 00:44:08.109 WriteAudio: buffer underrun
2009-08-26 00:44:08.122 NVP: Video is 17.0672 frames behind audio (too slow), dropping frame to catch up.
2009-08-26 00:44:08.156 NVP: Video is 17.2061 frames behind audio (too slow), dropping frame to catch up.
2009-08-26 00:44:08.174 WriteAudio: buffer underrun
2009-08-26 00:44:08.195 NVP: Video is 17.3552 frames behind audio (too slow), dropping frame to catch up.
2009-08-26 00:44:08.229 NVP: Video is 17.5419 frames behind audio (too slow), dropping frame to catch up.
2009-08-26 00:44:08.249 WriteAudio: buffer underrun
2009-08-26 00:44:08.263 NVP: Video is 17.6071 frames behind audio (too slow), dropping frame to catch up.
2009-08-26 00:44:08.297 NVP: Video is 17.611 frames behind audio (too slow), dropping frame to catch up.
2009-08-26 00:44:08.316 WriteAudio: buffer underrun
2009-08-26 00:44:08.359 NVP: Video is 17.6439 frames behind audio (too slow), dropping frame to catch up.
2009-08-26 00:44:08.411 NVP: Video is 17.8783 frames behind audio (too slow), dropping frame to catch up.
2009-08-26 00:44:08.440 WriteAudio: buffer underrun
2009-08-26 00:44:08.449 NVP: Video is 17.7994 frames behind audio (too slow), dropping frame to catch up.
2009-08-26 00:44:08.484 NVP: Video is 17.6354 frames behind audio (too slow), dropping frame to catch up.
2009-08-26 00:44:08.514 WriteAudio: buffer underrun
2009-08-26 00:44:08.520 NVP: Video is 17.6172 frames behind audio (too slow), dropping frame to catch up.
2009-08-26 00:44:08.555 NVP: Video is 17.4088 frames behind audio (too slow), dropping frame to catch up.
2009-08-26 00:44:08.591 WriteAudio: buffer underrun
2009-08-26 00:44:08.591 NVP: Video is 17.4173 frames behind audio (too slow), dropping frame to catch up.
2009-08-26 00:44:08.627 NVP: Video is 17.1689 frames behind audio (too slow), dropping frame to catch up.
2009-08-26 00:44:08.655 WriteAudio: buffer underrun
2009-08-26 00:44:08.663 NVP: Video is 17.2224 frames behind audio (too slow), dropping frame to catch up.
2009-08-26 00:44:08.698 NVP: Video is 17.0976 frames behind audio (too slow), dropping frame to catch up.
2009-08-26 00:44:08.731 WriteAudio: buffer underrun
2009-08-26 00:44:08.734 NVP: Video is 17.154 frames behind audio (too slow), dropping frame to catch up.
2009-08-26 00:44:08.769 NVP: Video is 16.9715 frames behind audio (too slow), dropping frame to catch up.
2009-08-26 00:44:08.771 NVP: Video is 17.0444 frames behind audio (too slow), dropping frame to catch up.
2009-08-26 00:44:08.771 NVP: Video is 16.8443 frames behind audio (too slow), dropping frame to catch up.
2009-08-26 00:44:08.771 NVP: Video is 16.4394 frames behind audio (too slow), dropping frame to catch up.
2009-08-26 00:44:08.771 NVP: Video is 15.8811 frames behind audio (too slow), dropping frame to catch up.
2009-08-26 00:44:08.771 NVP: Video is 15.2226 frames behind audio (too slow), dropping frame to catch up.
2009-08-26 00:44:08.771 NVP: Video is 14.4739 frames behind audio (too slow), dropping frame to catch up.
2009-08-26 00:44:08.771 NVP: Video is 13.6577 frames behind audio (too slow), dropping frame to catch up.
2009-08-26 00:44:08.771 NVP: Video is 12.8057 frames behind audio (too slow), dropping frame to catch up.
2009-08-26 00:44:08.771 NVP: Video is 11.912 frames behind audio (too slow), dropping frame to catch up.
2009-08-26 00:44:08.771 NVP: Video is 10.987 frames behind audio (too slow), dropping frame to catch up.
2009-08-26 00:44:08.771 NVP: Video is 10.0535 frames behind audio (too slow), dropping frame to catch up.
2009-08-26 00:44:08.772 NVP: prebuffering pause
2009-08-26 00:44:08.772 NVP: Waiting for prebuffer..  0 AALAAAAAAAAAAAALA
2009-08-26 00:44:08.772 WriteAudio: buffer underrun
2009-08-26 00:44:08.812 NVP: Video is 9.09854 frames behind audio (too slow), dropping frame to catch up.
2009-08-26 00:44:08.812 NVP: prebuffering pause
2009-08-26 00:44:08.812 NVP: Waiting for prebuffer..  0 AALAAAAAAAAAAAAaA
2009-08-26 00:44:08.845 NVP: prebuffering pause
2009-08-26 00:44:08.850 NVP: Waiting for prebuffer..  0 ALLAAAAAAAAAAAAaA
2009-08-26 00:44:08.872 NVP: prebuffering pause
2009-08-26 00:44:08.872 NVP: Waiting for prebuffer..  0 AALAALAAAAAAAAAAA
2009-08-26 00:44:08.893 NVP: prebuffering pause
2009-08-26 00:44:08.894 NVP: Waiting for prebuffer..  0 AAaLALAAAAAAAAAAA
2009-08-26 00:44:08.917 NVP: prebuffering pause
2009-08-26 00:44:08.917 NVP: Waiting for prebuffer..  0 AAAAALAALAAAAAAAA
2009-08-26 00:44:09.714 TV: Attempting to change from WatchingLiveTV to None
2009-08-26 00:44:09.714 TV: StopStuff() -- begin
2009-08-26 00:44:09.714 TV: StopStuff(): stopping ring buffer[s]
2009-08-26 00:44:09.747 TV: StopStuff(): stopping player[s] (1/2)
2009-08-26 00:44:09.747 TV: StopStuff(): stopping recorder[s]
2009-08-26 00:44:09.760 NVP: Exited decoder loop.
2009-08-26 00:44:09.780 VideoOutputXv: dtor
2009-08-26 00:44:09.781 VideoOutputXv: DiscardFrames(1)
2009-08-26 00:44:09.781 VideoBuffers::DiscardFrames(1): LAAAAAAUUUUUUUuUu
2009-08-26 00:44:09.782 VideoBuffers::DiscardFrames(): AAAAAAAAAAAAAAAAA -- done()
2009-08-26 00:44:09.782 VideoBuffers::DiscardFrames(1): AAAAAAAAAAAAAAAAA -- done
2009-08-26 00:44:09.782 VideoOutputXv: DiscardFrames() 3: AAAAAAAAAAAAAAAAA -- done()
2009-08-26 00:44:09.886 VideoOutputXv: DiscardFrames(1)
2009-08-26 00:44:09.886 VideoBuffers::DiscardFrames(1): AAAAAAAAAAAAAAAAA
2009-08-26 00:44:09.886 VideoBuffers::DiscardFrames(): AAAAAAAAAAAAAAAAA -- done()
2009-08-26 00:44:09.886 VideoBuffers::DiscardFrames(1): AAAAAAAAAAAAAAAAA -- done
2009-08-26 00:44:09.886 VideoOutputXv: DiscardFrames() 3: AAAAAAAAAAAAAAAAA -- done()
2009-08-26 00:44:10.152 TV: StopStuff(): stopping player[s] (2/2)
2009-08-26 00:44:10.190 TV: StopStuff() -- end
2009-08-26 00:44:10.190 TV: Changing from WatchingLiveTV to None
2009-08-26 00:44:10.217 DPMS Reactivated.
2009-08-26 00:44:16.827 Deleting UPnP client...

```

BTW, I've tried using the "release" packages to no avail, and am now using the most current "testing" packages and I'm getting the same results.

I must be doing something wrong. But what is it?

---

### Post by jyavenard on 2009-08-26
> **zobcat said:**
> 
I must be doing something wrong. But what is it?

MythTV isn't using VDPAU for playback, but ffmpeg for decoding due to your video profile
```
2009-08-26 00:44:03.154 AFD: Using ffmpeg for video decoding
2009-08-26 00:44:03.154 AFD: Looking for decoder for MPEG2VIDEO
2009-08-26 00:44:03.154 AFD: Opened codec 0xb1ba11d0, id(MPEG2VIDEO) type(Video)
2009-08-26 00:44:03.154 AFD: Stream #1, has id 0x52 codec id AC3, type Audio, bitrate 384000 at 0x0xb1b3a2a0

```

Your playback profile shows that if playing a HD video (w > 0 ; h >= 720)
, you will use software decoding which is definitely *not* what you want if you don't have a fast enough processor

---

### Post by zobcat on 2009-08-26
I'm running a AMD Athlon II X2 250 3.0GHz CPU.

---

### Post by jyavenard on 2009-08-27
that doesn't change the fact the the video profile you've defined and that is being used doesn't use vdpau :)

---

### Post by zobcat on 2009-08-27
Here are screenshots of my vdpau playback profile.

Thanks for your help.

[ATTACH]126488[/ATTACH]

[ATTACH]126489[/ATTACH]

[ATTACH]126490[/ATTACH]

[ATTACH]126491[/ATTACH]

[ATTACH]126492[/ATTACH]

---

### Post by jyavenard on 2009-08-27
[QUOTE=zobcat;7856192]Here are screenshots of my vdpau playback profile.

Thanks for your help.

I don't see much the point of answering when you obviously don't read any of my previous answers.

Look at your screen capture !!!
You've defined it to use ffmpeg for decoding HD video..

Can't you even look at your own screen capture ?

---

### Post by zobcat on 2009-08-27
Sorry about that. I've been changing settings back and forth so much I didn't even realize I had left it that way. 

I've changed it back to VDPAU now. I'm still getting very high CPU ~100%.

Here's my output:
```
fal@fel:~$ mythfrontend.real -v playback
2009-08-27 18:37:42.336 Using runtime prefix = /usr
2009-08-27 18:37:42.347 XScreenSaver support enabled
2009-08-27 18:37:42.350 DPMS is active.
2009-08-27 18:37:42.351 Empty LocalHostName.
2009-08-27 18:37:42.351 Using localhost value of fel
2009-08-27 18:37:42.367 New DB connection, total: 1
2009-08-27 18:37:42.371 Connected to database 'mythconverg' at host: localhost
2009-08-27 18:37:42.372 Closing DB connection named 'DBManager0'
2009-08-27 18:37:42.372 Primary screen 0.
2009-08-27 18:37:42.373 Connected to database 'mythconverg' at host: localhost
2009-08-27 18:37:42.373 Using screen 0, 1680x1050 at 0,0
2009-08-27 18:37:42.404 user: 1000 effective user: 1000 before privileged thread
2009-08-27 18:37:42.404 user: 1000 effective user: 1000 run_priv_thread
2009-08-27 18:37:42.404 user: 1000 effective user: 1000 after privileged thread
2009-08-27 18:37:42.406 New DB connection, total: 2
2009-08-27 18:37:42.407 Connected to database 'mythconverg' at host: localhost
2009-08-27 18:37:42.408 mythfrontend version: 0.21.20080304-1 www.mythtv.org
2009-08-27 18:37:42.408 Enabled verbose msgs:  important general playback
2009-08-27 18:37:42.712 max_width: 1680 max_height: 1050
2009-08-27 18:37:42.750 No theme dir: /home/fal/.mythtv/themes/blootubelite-wide
2009-08-27 18:37:42.751 Primary screen 0.
2009-08-27 18:37:42.751 Using screen 0, 1680x1050 at 0,0
2009-08-27 18:37:42.751 No theme dir: /home/fal/.mythtv/themes/blootubelite-wide
2009-08-27 18:37:42.751 Switching to wide mode (blootubelite-wide)
2009-08-27 18:37:42.761 Using the Qt painter
2009-08-27 18:37:42.762 lirc init success using configuration file: /home/fal/.mythtv/lircrc
2009-08-27 18:37:42.762 JoystickMenuClient Error: Joystick disabled - Failed to read /home/fal/.mythtv/joystickmenurc
2009-08-27 18:37:43.721 Specified base font 'medium' does not exist for font small
2009-08-27 18:37:43.722 Specified base font 'medium' does not exist for font medium
2009-08-27 18:37:43.722 Specified base font 'medium' does not exist for font large
2009-08-27 18:37:43.722 Specified base font 'medium' does not exist for font clock
2009-08-27 18:37:43.724 Loading from: /usr/share/mythtv/themes/blootubelite-wide/base.xml
2009-08-27 18:37:43.808 Loading from: /usr/share/mythtv/themes/default/base.xml
2009-08-27 18:37:43.833 Registering Internal as a media playback plugin.
2009-08-27 18:37:43.876 MonitorRegisterExtensions(0x100, gif,jpg,png)
2009-08-27 18:37:43.896 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
2009-08-27 18:37:43.917 No theme dir: /home/fal/.mythtv/themes/blootubelite-wide
2009-08-27 18:37:55.358 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-08-27 18:37:55.359 Using protocol version 40
2009-08-27 18:37:55.377 TV: Attempting to change from None to WatchingLiveTV
2009-08-27 18:37:55.378 Using protocol version 40
2009-08-27 18:37:56.857 LiveTVChain(live-fel-2009-08-27T18:37:55): ReloadAll(): Added new recording
2009-08-27 18:37:56.876 TV: StartRecorder(): took 0 ms to start recorder.
2009-08-27 18:37:56.898 New DB connection, total: 3
2009-08-27 18:37:56.898 Connected to database 'mythconverg' at host: localhost
2009-08-27 18:37:56.900 DPMS Deactivated 
2009-08-27 18:37:56.914 detectInterlace(Ignore Scan, Interlaced Scan, 25, 576) ->Interlaced Scan
2009-08-27 18:37:56.919 NVP: Disabling Audio, params(-1,2,44100)
2009-08-27 18:37:56.970 VDPAU: Version 0
2009-08-27 18:37:56.970 VDPAU: Information NVIDIA VDPAU Driver Shared Library  190.25  Thu Aug 20 18:31:10 PDT 2009
2009-08-27 18:37:57.423 VideoOutput: Allowed renderers: directfb,xv-blit,xshm,opengl,vdpau,xlib
2009-08-27 18:37:57.424 VideoOutput: Allowed renderers (filt: dummy): xlib,xshm,directfb,xv-blit,opengl
2009-08-27 18:37:57.427 VDP: Accepting: cmp(< 1920 720) dec(vdpau) cpus(0) skiploop(enabled) rend(vdpau) osd(vdpau) osdfade(enabled) deint(vdpauadvanceddoublerate,none) filt()
2009-08-27 18:37:57.427 VDP: Accepting: cmp(>= 0 720) dec(vdpau) cpus(0) skiploop(enabled) rend(vdpau) osd(vdpau) osdfade(enabled) deint(vdpaubasicdoublerate,none) filt()
2009-08-27 18:37:57.427 VDP: LoadBestPreferences(2048x2048, 0)
2009-08-27 18:37:57.427 VDP: LoadBestPreferences(2048x2048, 60)
2009-08-27 18:37:57.428 VDP: LoadBestPreferences(720x576, 60)
2009-08-27 18:37:57.428 VideoOutput: Trying video renderer: xv-blit
2009-08-27 18:37:57.429 VDP: Accepting: cmp(< 1920 720) dec(vdpau) cpus(0) skiploop(enabled) rend(vdpau) osd(vdpau) osdfade(enabled) deint(vdpauadvanceddoublerate,none) filt()
2009-08-27 18:37:57.430 VDP: Accepting: cmp(>= 0 720) dec(vdpau) cpus(0) skiploop(enabled) rend(vdpau) osd(vdpau) osdfade(enabled) deint(vdpaubasicdoublerate,none) filt()
2009-08-27 18:37:57.430 VDP: LoadBestPreferences(2048x2048, 0)
2009-08-27 18:37:57.430 VDP: LoadBestPreferences(2048x2048, 60)
2009-08-27 18:37:57.441 VideoOutputXv: ctor
2009-08-27 18:37:57.444 XOff: 0, YOff: 0
2009-08-27 18:37:57.444 VDP: LoadBestPreferences(720x576, 60)
2009-08-27 18:37:57.444 Display Rect  left: -280, top: 0, width: 2240, height: 1050, aspect: 1.33333
2009-08-27 18:37:57.444 Video Rect    left: 0, top: 0, width: 720, height: 576, aspect: 1.33333
2009-08-27 18:37:57.445 VideoOutputXv: Pixel dimensions: Screen 1680x1050, window 1680x1050
2009-08-27 18:37:57.445 VideoOutputXv: Estimated display dimensions: 427x267 mm  Aspect: 1.59925
2009-08-27 18:37:57.445 VideoOutputXv: Estimated window dimensions: 427x267 mm  Aspect: 1.59925
2009-08-27 18:38:05.508 VideoOutputXv: InitSetupBuffers() render: vdpau, allowed: xv-blit,xshm,opengl,vdpau,xlib
2009-08-27 18:38:05.573 Created data @0xabb27020->0xabbbee22
2009-08-27 18:38:05.573 Created data @0xaba8f020->0xabb26e22
2009-08-27 18:38:05.573 Created data @0xab9f7020->0xaba8ee22
2009-08-27 18:38:05.573 Created data @0xab95f020->0xab9f6e22
2009-08-27 18:38:05.573 Created data @0xab8c7020->0xab95ee22
2009-08-27 18:38:05.573 Created data @0xab82f020->0xab8c6e22
2009-08-27 18:38:05.573 Created data @0xab797020->0xab82ee22
2009-08-27 18:38:05.573 Created data @0xab6ff020->0xab796e22
2009-08-27 18:38:05.573 Created data @0xab667020->0xab6fee22
2009-08-27 18:38:05.573 Created data @0xab5cf020->0xab666e22
2009-08-27 18:38:05.573 Created data @0xab537020->0xab5cee22
2009-08-27 18:38:05.573 Created data @0xab49f020->0xab536e22
2009-08-27 18:38:05.573 Created data @0xab407020->0xab49ee22
2009-08-27 18:38:05.573 Created data @0xab36f020->0xab406e22
2009-08-27 18:38:05.573 Created data @0xab2d7020->0xab36ee22
2009-08-27 18:38:05.574 Created data @0xab23f020->0xab2d6e22
2009-08-27 18:38:05.574 Created data @0xab1a7020->0xab23ee22
2009-08-27 18:38:05.588 VideoOutputXv: Created VDPAU context (software decode)
2009-08-27 18:38:05.589 VDP: SetVideoRenderer(vdpau)
2009-08-27 18:38:05.589 VDP: SetVideoRender(vdpau) == GetVideoRenderer()
2009-08-27 18:38:05.615 VDPAU: Created OSD (1680x1050)
2009-08-27 18:38:05.616 VideoOutputXv: VDPAU Colorkey: 0x20202 (depth 24)
2009-08-27 18:38:05.616 Display Rect  left: -280, top: -104, width: 2240, height: 1259, aspect: 1.59925
2009-08-27 18:38:05.616 Video Rect    left: 0, top: 0, width: 720, height: 576, aspect: 1.33333
2009-08-27 18:38:05.618 Over/underscan. V: 0, H: 0
2009-08-27 18:38:05.619 Display Rect  left: -280, top: -104, width: 2240, height: 1259, aspect: 1.59925
2009-08-27 18:38:05.619 Video Rect    left: 0, top: 0, width: 720, height: 576, aspect: 1.33333
2009-08-27 18:38:05.619 VDP: LoadBestPreferences(720x576, 25)
2009-08-27 18:38:05.620 NVP: LoadFilters(''..) -> 0
2009-08-27 18:38:05.621 OSD Theme Dimensions W: 640 H: 480
2009-08-27 18:38:05.821 NVP: ClearAfterSeek(1)
2009-08-27 18:38:05.821 VideoOutputXv: ClearAfterSeek()
2009-08-27 18:38:05.821 TV: StartPlayer(): took 8898 ms to start player.
2009-08-27 18:38:05.821 VideoOutputXv: DiscardFrames(0)
2009-08-27 18:38:05.821 VideoBuffers::DiscardFrames(0): AAAAAAAAAAAAAAAAA
2009-08-27 18:38:05.821 VideoBuffers::DiscardFrames(0): AAAAAAAAAAAAAAAAA -- done
2009-08-27 18:38:05.821 VideoOutputXv: DiscardFrames() 3: AAAAAAAAAAAAAAAAA -- done()
2009-08-27 18:38:05.821 TV: Changing from None to WatchingLiveTV
2009-08-27 18:38:05.823 New DB connection, total: 4
2009-08-27 18:38:05.823 VDP: GetFilteredDeint() : vdpau -> 'vdpauadvanceddoublerate'
2009-08-27 18:38:05.833 rate: 25 speed: 1 skip: 1 = interval 40000
2009-08-27 18:38:05.834 Connected to database 'mythconverg' at host: localhost
2009-08-27 18:38:05.835 The realtime priority setting is not enabled.
2009-08-27 18:38:05.933 nVidiaVideoSync: VBlank ioctl did not work, unimplemented in this driver?
2009-08-27 18:38:05.933 DRMVideoSync: Could not open device /dev/dri/card0, No such file or directory
2009-08-27 18:38:05.933 OpenGLVideoSync()
2009-08-27 18:38:05.935 OpenGLVideoSync: x,y -> 840, 525
2009-08-27 18:38:05.990 Using OpenGLVideoSync
2009-08-27 18:38:05.990 Set video sync frame interval to 40000
2009-08-27 18:38:05.996 Using audio as timebase
2009-08-27 18:38:05.997 Video timing method: SGI OpenGL
2009-08-27 18:38:05.997 Refresh rate: 16699, frame interval: 40000
2009-08-27 18:38:06.053 VideoOutputXv: UpdatePauseFrame() AAAAAAAAAAAAAAAAA
2009-08-27 18:38:06.445 VDPAU: Using 4 output surfaces (max 4)
2009-08-27 18:38:06.568 LiveTVChain(live-fel-2009-08-27T18:37:55): ReloadAll(): Added new recording
2009-08-27 18:38:06.569 LiveTVChain(live-fel-2009-08-27T18:37:55): SwitchTo(1)
2009-08-27 18:38:06.569 LiveTVChain(live-fel-2009-08-27T18:37:55): Entry@1: '1261_20090827183805'
2009-08-27 18:38:06.569 JumpToProgram(void)
2009-08-27 18:38:06.608 RingBuf(/var/lib/mythtv/recordings/1261_20090827183755.mpg): OpenFile(/var/lib/mythtv/recordings/1261_20090827183805.mpg, 12)
2009-08-27 18:38:06.631 RingBuf(/var/lib/mythtv/recordings/1261_20090827183805.mpg): CalcReadAheadThresh(3086473648 KB)
			 -> threshhold(64 KB) min read(0 KB) blk size(32 KB)
2009-08-27 18:38:06.681 NVP: Waiting for prebuffer..  0 AAAAAAAAAAAAAAAAA
2009-08-27 18:38:06.888 VideoOutputXv: UpdatePauseFrame() AAAAAAAAAAAAAAAAA
2009-08-27 18:38:06.898 NVP: Waiting for prebuffer..  1 AAAAAAAAAAAAAAAAA
2009-08-27 18:38:07.105 VideoOutputXv: UpdatePauseFrame() AAAAAAAAAAAAAAAAA
2009-08-27 18:38:07.115 NVP: Waiting for prebuffer..  2 AAAAAAAAAAAAAAAAA
2009-08-27 18:38:07.225 AFD: Stream #0, has id 0x49 codec id MPEG2VIDEO, type Video, bitrate 19000000 at 0x0xb1b103a0
2009-08-27 18:38:07.227 VDP: Accepting: cmp(< 1920 720) dec(vdpau) cpus(0) skiploop(enabled) rend(vdpau) osd(vdpau) osdfade(enabled) deint(vdpauadvanceddoublerate,none) filt()
2009-08-27 18:38:07.227 VDP: Accepting: cmp(>= 0 720) dec(vdpau) cpus(0) skiploop(enabled) rend(vdpau) osd(vdpau) osdfade(enabled) deint(vdpaubasicdoublerate,none) filt()
2009-08-27 18:38:07.228 VDP: LoadBestPreferences(2048x2048, 0)
2009-08-27 18:38:07.228 VDP: LoadBestPreferences(2048x2048, 60)
2009-08-27 18:38:07.228 VDP: LoadBestPreferences(1280x720, 60)
2009-08-27 18:38:07.323 VideoOutputXv: UpdatePauseFrame() AAAAAAAAAAAAAAAAA
2009-08-27 18:38:07.336 VDPAU Error: Error at util-vdpau.cpp:870 (#23, The system does not have enough resources to complete the requested operation at this time.)
2009-08-27 18:38:07.336 VDPAU Error: Failed to create output surface.
2009-08-27 18:38:07.349 NVP: Waiting for prebuffer..  3 AAAAAAAAAAAAAAAAA
2009-08-27 18:38:07.365 VDP: Accepting: cmp(< 1920 720) dec(vdpau) cpus(0) skiploop(enabled) rend(vdpau) osd(vdpau) osdfade(enabled) deint(vdpauadvanceddoublerate,none) filt()
2009-08-27 18:38:07.365 VDP: Accepting: cmp(>= 0 720) dec(vdpau) cpus(0) skiploop(enabled) rend(vdpau) osd(vdpau) osdfade(enabled) deint(vdpaubasicdoublerate,none) filt()
2009-08-27 18:38:07.365 VDP: LoadBestPreferences(2048x2048, 0)
2009-08-27 18:38:07.366 VDP: LoadBestPreferences(2048x2048, 60)
2009-08-27 18:38:07.366 VDP: LoadBestPreferences(1280x720, 60)
2009-08-27 18:38:07.366 Using 0 CPUs for decoding
2009-08-27 18:38:07.366 AFD: InitVideoCodec() 0xb1b0f1f0 id(MPEG2VIDEO) type (Video).
2009-08-27 18:38:07.366 VideoOutputXv: InputChanged(1280,720,1.77778) 'None'->'MPEG2'
2009-08-27 18:38:07.367 VDP: LoadBestPreferences(1280x720, 25)
2009-08-27 18:38:07.367 VDP: GetFilteredDeint() : vdpau -> 'vdpaubasicdoublerate'
2009-08-27 18:38:07.399 VDP: GetFilteredDeint() : vdpau -> 'vdpaubasicdoublerate'
2009-08-27 18:38:07.417 VideoOutputXv: DiscardFrames(1)
2009-08-27 18:38:07.417 VideoBuffers::DiscardFrames(1): AAAAAAAAAAAAAAAAA
2009-08-27 18:38:07.417 VideoBuffers::DiscardFrames(): AAAAAAAAAAAAAAAAA -- done()
2009-08-27 18:38:07.417 VideoBuffers::DiscardFrames(1): AAAAAAAAAAAAAAAAA -- done
2009-08-27 18:38:07.417 VideoOutputXv: DiscardFrames() 3: AAAAAAAAAAAAAAAAA -- done()
2009-08-27 18:38:07.417 VideoOutputXv: DiscardFrames(1)
2009-08-27 18:38:07.417 VideoBuffers::DiscardFrames(1): AAAAAAAAAAAAAAAAA
2009-08-27 18:38:07.417 VideoBuffers::DiscardFrames(): AAAAAAAAAAAAAAAAA -- done()
2009-08-27 18:38:07.417 VideoBuffers::DiscardFrames(1): AAAAAAAAAAAAAAAAA -- done
2009-08-27 18:38:07.417 VideoOutputXv: DiscardFrames() 3: AAAAAAAAAAAAAAAAA -- done()
2009-08-27 18:38:07.477 VideoOutputXv: DiscardFrames(1)
2009-08-27 18:38:07.477 VideoBuffers::DiscardFrames(1): AAAAAAAAAAAAAAAAA
2009-08-27 18:38:07.477 VideoBuffers::DiscardFrames(): AAAAAAAAAAAAAAAAA -- done()
2009-08-27 18:38:07.477 VideoBuffers::DiscardFrames(1): AAAAAAAAAAAAAAAAA -- done
2009-08-27 18:38:07.477 VideoOutputXv: DiscardFrames() 3: AAAAAAAAAAAAAAAAA -- done()
2009-08-27 18:38:07.513 VideoOutputXv: InitSetupBuffers() render: vdpau, allowed: xv-blit,xshm,opengl,vdpau,xlib
2009-08-27 18:38:07.563 Created data @0xaba6d020->0xabbbe822
2009-08-27 18:38:07.564 Created data @0xab91b020->0xaba6c822
2009-08-27 18:38:07.564 Created data @0xab7c9020->0xab91a822
2009-08-27 18:38:07.564 Created data @0xab677020->0xab7c8822
2009-08-27 18:38:07.564 Created data @0xab525020->0xab676822
2009-08-27 18:38:07.564 Created data @0xab3d3020->0xab524822
2009-08-27 18:38:07.564 Created data @0xab281020->0xab3d2822
2009-08-27 18:38:07.564 Created data @0xa7eae020->0xa7fff822
2009-08-27 18:38:07.564 Created data @0xa7d5c020->0xa7ead822
2009-08-27 18:38:07.564 Created data @0xa7c0a020->0xa7d5b822
2009-08-27 18:38:07.564 Created data @0xa7ab8020->0xa7c09822
2009-08-27 18:38:07.564 Created data @0xa7966020->0xa7ab7822
2009-08-27 18:38:07.564 Created data @0xa7814020->0xa7965822
2009-08-27 18:38:07.564 Created data @0xa76c2020->0xa7813822
2009-08-27 18:38:07.564 Created data @0xa7570020->0xa76c1822
2009-08-27 18:38:07.564 Created data @0xa741e020->0xa756f822
2009-08-27 18:38:07.564 Created data @0xa72cc020->0xa741d822
2009-08-27 18:38:07.594 VideoOutputXv: Created VDPAU context (software decode)
2009-08-27 18:38:07.594 VDP: SetVideoRenderer(vdpau)
2009-08-27 18:38:07.594 VDP: SetVideoRender(vdpau) == GetVideoRenderer()
2009-08-27 18:38:07.615 VDPAU: Created OSD (1680x1050)
2009-08-27 18:38:07.615 VideoOutputXv: VDPAU Colorkey: 0x20202 (depth 24)
2009-08-27 18:38:07.615 Display Rect  left: -280, top: -104, width: 2240, height: 1259, aspect: 1.59925
2009-08-27 18:38:07.615 Video Rect    left: 0, top: 0, width: 1280, height: 720, aspect: 1.33333
2009-08-27 18:38:07.615 VDP: GetFilteredDeint() : vdpau -> 'vdpaubasicdoublerate'
2009-08-27 18:38:07.615 VDP: GetFilteredDeint() : vdpau -> 'vdpaubasicdoublerate'
2009-08-27 18:38:07.634 VideoOutputXv: UpdatePauseFrame() AAAAAAAAAAAAAAAAA
2009-08-27 18:38:07.634 VDP: LoadBestPreferences(1280x720, 59.9401)
2009-08-27 18:38:07.724 NVP: ClearAfterSeek(1)
2009-08-27 18:38:07.724 VideoOutputXv: ClearAfterSeek()
2009-08-27 18:38:07.724 VideoOutputXv: DiscardFrames(0)
2009-08-27 18:38:07.724 VideoBuffers::DiscardFrames(0): AAAAAAAAAAAAAAAAA
2009-08-27 18:38:07.724 VideoBuffers::DiscardFrames(0): AAAAAAAAAAAAAAAAA -- done
2009-08-27 18:38:07.724 VideoOutputXv: DiscardFrames() 3: AAAAAAAAAAAAAAAAA -- done()
2009-08-27 18:38:07.724 NVP: LoadFilters(''..) -> 0
2009-08-27 18:38:07.724 detectInterlace(Detect Scan, Interlaced Scan, 59.9401, 720) ->Progressive Scan
2009-08-27 18:38:07.724 Set video sync frame interval to 16683
2009-08-27 18:38:07.736 NVP: Waiting for prebuffer..  4 AAAAAAAAAAAAAAAAA
2009-08-27 18:38:07.746 Disabled deinterlacing
2009-08-27 18:38:07.746 AFD: Using ffmpeg for video decoding
2009-08-27 18:38:07.746 AFD: Looking for decoder for MPEG2VIDEO
2009-08-27 18:38:07.746 AFD: Opened codec 0xb1b0f1f0, id(MPEG2VIDEO) type(Video)
2009-08-27 18:38:07.746 AFD: Stream #1, has id 0x52 codec id AC3, type Audio, bitrate 448000 at 0x0xb1b0f860
2009-08-27 18:38:07.746 AFD: codec AC3 has 2 channels
2009-08-27 18:38:07.746 AFD: Looking for decoder for AC3
2009-08-27 18:38:07.747 AFD: Opened codec 0xb1b0fbc0, id(AC3) type(Audio)
2009-08-27 18:38:07.747 AFD: Stream #2, has id 0x53 codec id AC3, type Audio, bitrate 192000 at 0x0xb1b0ff50
2009-08-27 18:38:07.747 AFD: codec AC3 has 2 channels
2009-08-27 18:38:07.747 AFD: Looking for decoder for AC3
2009-08-27 18:38:07.747 AFD: Opened codec 0xb1b23c50, id(AC3) type(Audio)
2009-08-27 18:38:07.773 RingBuf(/var/lib/mythtv/recordings/1261_20090827183805.mpg): CalcReadAheadThresh(3086450299 KB)
			 -> threshhold(64 KB) min read(0 KB) blk size(32 KB)
2009-08-27 18:38:07.777 Opening audio device 'default'. ch 2(2) sr 48000
2009-08-27 18:38:07.777 Opening ALSA audio device 'default'.
2009-08-27 18:38:07.791 Mixer unable to find control Master
2009-08-27 18:38:07.791 Mixer unable to find control Master
2009-08-27 18:38:07.791 NVP: Enabling Audio
2009-08-27 18:38:07.791 Dec: Trying to select track (w/lang)
2009-08-27 18:38:07.791 Dec: Selecting first track
2009-08-27 18:38:07.791 Dec: Selected track #1 in the Unknown language(0)
2009-08-27 18:38:07.791 Resyncing position map. posmapStarted = 0 livetv(1) watchingRec(1)
2009-08-27 18:38:07.793 SyncPositionMap watchingrecording, from DB: 0 entries
2009-08-27 18:38:07.793 Filling position map from 0 to 59
2009-08-27 18:38:07.794 Position map filled from Encoder to: 48
2009-08-27 18:38:07.794 SyncPositionMap watchingrecording total: 5 entries
2009-08-27 18:38:07.794 SyncPositionMap, new totframes: 48, new length: 0, posMap size: 5
2009-08-27 18:38:07.794 AFD: Partial position map found
2009-08-27 18:38:07.794 AFD: Successfully opened decoder for file: "/var/lib/mythtv/recordings/1261_20090827183805.mpg". novideo(0)
2009-08-27 18:38:07.795 NVP: DoPlay: rate: 59.9401 speed: 1 skip: 1 => new interval 16683
2009-08-27 18:38:07.795 Set video sync frame interval to 16683
2009-08-27 18:38:07.795 NVP: Stretch Factor 1, allow passthru 
2009-08-27 18:38:07.816 NVP: Waiting for prebuffer..  5 AAAAAAAAAAAAAAAAA
2009-08-27 18:38:07.836 RingBuf(/var/lib/mythtv/recordings/1261_20090827183805.mpg): CalcReadAheadThresh(3086450299 KB)
			 -> threshhold(64 KB) min read(0 KB) blk size(32 KB)
2009-08-27 18:38:07.836 Resyncing position map. posmapStarted = 0 livetv(1) watchingRec(1)
2009-08-27 18:38:07.836 SyncPositionMap watchingrecording, from DB: 5 entries
2009-08-27 18:38:07.836 Filling position map from 49 to 61
2009-08-27 18:38:07.837 Position map filled from Encoder to: 60
2009-08-27 18:38:07.837 SyncPositionMap watchingrecording total: 6 entries
2009-08-27 18:38:07.837 SyncPositionMap, new totframes: 60, new length: 1, posMap size: 6
2009-08-27 18:38:08.052 [ac3 @ 0xb6f6d850]frame CRC mismatch
2009-08-27 18:38:08.086 [ac3 @ 0xb6f6d850]incomplete frame
2009-08-27 18:38:08.086 [ac3 @ 0xb6f6d850]invalid frame size
2009-08-27 18:38:08.093 VDPAU: Using 4 output surfaces (max 4)
2009-08-27 18:38:08.169 [mpeg2video @ 0xb6f6d850]ac-tex damaged at 7 35
2009-08-27 18:38:08.172 [mpeg2video @ 0xb6f6d850]Warning MVs not available
2009-08-27 18:38:08.244 [mpeg2video @ 0xb6f6d850]ac-tex damaged at 67 20
2009-08-27 18:38:08.245 [mpeg2video @ 0xb6f6d850]invalid cbp at 18 23
2009-08-27 18:38:08.245 [mpeg2video @ 0xb6f6d850]mb incr damaged
2009-08-27 18:38:08.248 [mpeg2video @ 0xb6f6d850]Warning MVs not available
2009-08-27 18:38:08.491 [mpeg2video @ 0xb6f6d850]invalid mb type in P Frame at 79 17
2009-08-27 18:38:08.594 [mpeg2video @ 0xb6f6d850]invalid mb type in I Frame at 36 1
2009-08-27 18:38:08.594 [mpeg2video @ 0xb6f6d850]invalid mb type in I Frame at 13 2
2009-08-27 18:38:08.595 [mpeg2video @ 0xb6f6d850]ac-tex damaged at 33 4
2009-08-27 18:38:08.894 [mpeg2video @ 0xb6f6d850]ac-tex damaged at 72 37
2009-08-27 18:38:08.894 [mpeg2video @ 0xb6f6d850]slice mismatch
2009-08-27 18:38:08.894 [mpeg2video @ 0xb6f6d850]ac-tex damaged at 24 10
2009-08-27 18:38:08.894 [mpeg2video @ 0xb6f6d850]invalid mb type in P Frame at 4 11
2009-08-27 18:38:08.894 [mpeg2video @ 0xb6f6d850]mb incr damaged
2009-08-27 18:38:08.894 [mpeg2video @ 0xb6f6d850]ac-tex damaged at 20 14
2009-08-27 18:38:08.894 [mpeg2video @ 0xb6f6d850]ac-tex damaged at 11 15
2009-08-27 18:38:08.895 [mpeg2video @ 0xb6f6d850]ac-tex damaged at 1 16
2009-08-27 18:38:08.895 [mpeg2video @ 0xb6f6d850]mb incr damaged
2009-08-27 18:38:08.895 [mpeg2video @ 0xb6f6d850]ac-tex damaged at 13 18
2009-08-27 18:38:08.895 [mpeg2video @ 0xb6f6d850]ac-tex damaged at 5 19
2009-08-27 18:38:08.895 [mpeg2video @ 0xb6f6d850]mb incr damaged
2009-08-27 18:38:08.895 [mpeg2video @ 0xb6f6d850]mb incr damaged
2009-08-27 18:38:08.895 [mpeg2video @ 0xb6f6d850]ac-tex damaged at 59 22
2009-08-27 18:38:08.895 [mpeg2video @ 0xb6f6d850]invalid mb type in P Frame at 1 23
2009-08-27 18:38:08.895 [mpeg2video @ 0xb6f6d850]mb incr damaged
2009-08-27 18:38:08.895 [mpeg2video @ 0xb6f6d850]ac-tex damaged at 6 25
2009-08-27 18:38:08.895 [mpeg2video @ 0xb6f6d850]invalid mb type in P Frame at 9 26
2009-08-27 18:38:08.895 [mpeg2video @ 0xb6f6d850]ac-tex damaged at 12 27
2009-08-27 18:38:08.895 [mpeg2video @ 0xb6f6d850]ac-tex damaged at 13 28
2009-08-27 18:38:08.896 [mpeg2video @ 0xb6f6d850]invalid cbp at 2 29
2009-08-27 18:38:08.896 [mpeg2video @ 0xb6f6d850]ac-tex damaged at 8 30
2009-08-27 18:38:08.896 [mpeg2video @ 0xb6f6d850]ac-tex damaged at 0 31
2009-08-27 18:38:08.896 [mpeg2video @ 0xb6f6d850]invalid mb type in P Frame at 32 32
2009-08-27 18:38:08.896 [mpeg2video @ 0xb6f6d850]ac-tex damaged at 3 33
2009-08-27 18:38:08.896 [mpeg2video @ 0xb6f6d850]mb incr damaged
2009-08-27 18:38:08.896 [mpeg2video @ 0xb6f6d850]invalid cbp at 7 35
2009-08-27 18:38:08.896 [mpeg2video @ 0xb6f6d850]mb incr damaged
2009-08-27 18:38:08.896 [mpeg2video @ 0xb6f6d850]ac-tex damaged at 65 37
2009-08-27 18:38:08.896 [mpeg2video @ 0xb6f6d850]ac-tex damaged at 20 38
2009-08-27 18:38:08.896 [mpeg2video @ 0xb6f6d850]ac-tex damaged at 49 39
2009-08-27 18:38:08.896 [mpeg2video @ 0xb6f6d850]ac-tex damaged at 1 40
2009-08-27 18:38:08.897 [mpeg2video @ 0xb6f6d850]ac-tex damaged at 7 41
2009-08-27 18:38:08.897 [mpeg2video @ 0xb6f6d850]slice mismatch
2009-08-27 18:38:08.897 [mpeg2video @ 0xb6f6d850]ac-tex damaged at 43 43
2009-08-27 18:38:08.897 [mpeg2video @ 0xb6f6d850]invalid mb type in P Frame at 32 44
2009-08-27 18:38:08.897 [mpeg2video @ 0xb6f6d850]Warning MVs not available
'video_output' mean = '16829.02', std. dev. = '3229.29', fps = '59.42'
2009-08-27 18:38:10.348 [mpeg2video @ 0xb6f6d850]ac-tex damaged at 78 20
2009-08-27 18:38:10.348 [mpeg2video @ 0xb6f6d850]ac-tex damaged at 1 22
2009-08-27 18:38:10.349 [mpeg2video @ 0xb6f6d850]skipped MB in I frame at 6 24
'video_output' mean = '16687.60', std. dev. = '2158.79', fps = '59.92'
2009-08-27 18:38:11.688 [ac3 @ 0xb6f6d850]frame CRC mismatch
2009-08-27 18:38:11.720 [ac3 @ 0xb6f6d850]incomplete frame
2009-08-27 18:38:11.721 [ac3 @ 0xb6f6d850]invalid frame size
2009-08-27 18:38:11.766 TV: Attempting to change from WatchingLiveTV to None
2009-08-27 18:38:11.766 TV: StopStuff() -- begin
2009-08-27 18:38:11.766 TV: StopStuff(): stopping ring buffer[s]
2009-08-27 18:38:11.782 TV: StopStuff(): stopping player[s] (1/2)
2009-08-27 18:38:11.782 TV: StopStuff(): stopping recorder[s]
2009-08-27 18:38:11.799 NVP: Exited decoder loop.
2009-08-27 18:38:11.813 ~OpenGLVideoSync() -- begin
2009-08-27 18:38:11.813 ~OpenGLVideoSync() -- middle
2009-08-27 18:38:11.814 ~OpenGLVideoSync() -- end
2009-08-27 18:38:11.814 VideoOutputXv: dtor
2009-08-27 18:38:11.814 VideoOutputXv: DiscardFrames(1)
2009-08-27 18:38:11.814 VideoBuffers::DiscardFrames(1): LAAuAAAUUAUUUUuUU
2009-08-27 18:38:11.814 VideoBuffers::DiscardFrames(): AAAAAAAAAAAAAAAAA -- done()
2009-08-27 18:38:11.814 VideoBuffers::DiscardFrames(1): AAAAAAAAAAAAAAAAA -- done
2009-08-27 18:38:11.814 VideoOutputXv: DiscardFrames() 3: AAAAAAAAAAAAAAAAA -- done()
2009-08-27 18:38:11.883 VideoOutputXv: DiscardFrames(1)
2009-08-27 18:38:11.884 VideoBuffers::DiscardFrames(1): AAAAAAAAAAAAAAAAA
2009-08-27 18:38:11.884 VideoBuffers::DiscardFrames(): AAAAAAAAAAAAAAAAA -- done()
2009-08-27 18:38:11.884 VideoBuffers::DiscardFrames(1): AAAAAAAAAAAAAAAAA -- done
2009-08-27 18:38:11.884 VideoOutputXv: DiscardFrames() 3: AAAAAAAAAAAAAAAAA -- done()
2009-08-27 18:38:12.178 TV: StopStuff(): stopping player[s] (2/2)
2009-08-27 18:38:12.221 TV: StopStuff() -- end
2009-08-27 18:38:12.221 TV: Changing from WatchingLiveTV to None
2009-08-27 18:38:12.273 DPMS Reactivated.
```


It seems it's still using ffmpeg. 

```
2009-08-27 18:38:07.746 AFD: Using ffmpeg for video decoding
2009-08-27 18:38:07.746 AFD: Looking for decoder for MPEG2VIDEO
2009-08-27 18:38:07.746 AFD: Opened codec 0xb1b0f1f0, id(MPEG2VIDEO) type(Video)
```

What do you think?

---

### Post by jyavenard on 2009-08-28
Why can't people read the log they provide ...

```
2009-08-27 18:38:07.336 VDPAU Error: Error at util-vdpau.cpp:870 (#23, The system does not have enough resources to complete the requested operation at this time.)
2009-08-27 18:38:07.336 VDPAU Error: Failed to create output surface.

```

not enough resources: you need to increase the memory dedicated to the GPU, 256MB is the bare minimum

---

### Post by mihaicj on 2009-10-04
> **jyavenard said:**
> not enough resources: you need to increase the memory dedicated to the GPU, 256MB is the bare minimum

How do you increase this memory?

---

### Post by jyavenard on 2009-10-04
In the BIOS .

---

### Post by mihaicj on 2009-10-05
I have an nvidia quadro nvs 140M GPU with 512MB memory. Even some 720p movies don't show due to this error. What could be the cause?

---

### Post by jyavenard on 2009-10-06
> **mihaicj said:**
> I have an nvidia quadro nvs 140M GPU with 512MB memory. Even some 720p movies don't show due to this error. What could be the cause?

if the log shows:
```
2009-08-27 18:38:07.336 VDPAU Error: Error at util-vdpau.cpp:870 (#23, The system does not have enough resources to complete the requested operation at this time.)

```

Then you don't have enough memory, plain and simple.

Either your GPU doesn't have enough memory allocated (you need at least 256MB with VDPAU).
Or there aren't enough buffers allocated.

The default buffer is is 17, there are some videos with a high number of reference frame (like 16) for which you must increase that value of that buffer, maximum is 32.

If you use MythTV trunk, there's a way to modify that value without editing the source code. Otherwise, you have to edit the code and recompile yourself

---

### Post by mihaicj on 2009-10-06
The error is
```

[vdpau] Error when calling vdp_output_surface_create: The system does not have enough resources to complete the requested operation at this time.

```
I'm using MPlayer, not MythTV. The video card has 512MB of memory, so that should be enough.

Should I try to modify the buffer size? I have no idea how much is it.

---

### Post by jyavenard on 2009-10-06
> **mihaicj said:**
> The error is
```

[vdpau] Error when calling vdp_output_surface_create: The system does not have enough resources to complete the requested operation at this time.

```
I'm using MPlayer, not MythTV. The video card has 512MB of memory, so that should be enough.

Should I try to modify the buffer size? I have no idea how much is it.

This has nothing to do with mythtv then, and I can't help

Ask on the mplayer distribution list how to increase the number of VDPAU buffers.

---

