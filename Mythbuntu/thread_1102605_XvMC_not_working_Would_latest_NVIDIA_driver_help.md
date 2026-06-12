---
title: "XvMC not working Would latest NVIDIA driver help ?"
date: 2009-03-21
forum: Mythbuntu
---

### Post by stevecartermo on 2009-03-21
I am having a tough time getting XvMC working on a 2 ghz celeron with an NVIDIA 5200 and Mythbuntu 8.1. I have been through alot of postings and I still get a black screen when I try to watch HD ATSC recordings on this box. These recordings work fine on another machine I have a P4 2.0 ghz machine with an FX5200 and Mythbuntu 8.04

The celeron displays SD recordings well. If I change the myth setup so that it doesn't use XvMC then the HD recordings are choppy.

I tried 0, 1, 2, and 3 for the NVAGP section of xorg.conf they all produced a black Screen and a locked frontend.

I see that NVIDIA has released an updated driver 173.14.18 that has some AGPGART fix. Any thoughts on whether this might help my problem, and how would I upgrade the driver on my system.

Thanks

Steve

---

### Post by stevecartermo on 2009-03-22
Ihave the frontendlog its a little long 


celeron@celeron-desktop:~$ cat /var/log/Xorg.0.log | grep Motion
(II) Loading extension XVideo-MotionCompensation
celeron@celeron-desktop:~$ cat /etc/X11/XvMCConfig
libXvMCNVIDIA_dynamic.so.1
celeron@celeron-desktop:~$ cat /proc/driver/nvidia/agp/status
Status: 	 Enabled
Driver: 	 AGPGART
AGP Rate: 	 8x
Fast Writes: 	 Disabled
SBA: 		 Enabled
celeron@celeron-desktop:~$ mythfrontend --verbose playback

2009-03-22 11:33:35.182 Using runtime prefix = /usr
QServerSocket: failed to bind or listen to the socket
2009-03-22 11:33:35.187 MediaRenderer::HttpServer Create Error
2009-03-22 11:33:35.250 XScreenSaver support enabled
2009-03-22 11:33:35.261 DPMS is active.
2009-03-22 11:33:35.269 Empty LocalHostName.
2009-03-22 11:33:35.269 Using localhost value of celeron-desktop
2009-03-22 11:33:35.271 Testing network connectivity to 192.168.0.143
2009-03-22 11:33:35.347 New DB connection, total: 1
2009-03-22 11:33:35.379 Connected to database 'mythconverg' at host: 192.168.0.143
2009-03-22 11:33:35.384 Closing DB connection named 'DBManager0'
2009-03-22 11:33:35.501 Primary screen 0.
2009-03-22 11:33:35.515 Connected to database 'mythconverg' at host: 192.168.0.143
2009-03-22 11:33:35.524 Running in a window
2009-03-22 11:33:35.525 Using screen 0, 1280x1000 at 0,24
2009-03-22 11:33:35.559 user: 1000 effective user: 1000 before privileged thread
2009-03-22 11:33:35.560 user: 1000 effective user: 1000 run_priv_thread
2009-03-22 11:33:35.560 user: 1000 effective user: 1000 after privileged thread
2009-03-22 11:33:35.576 New DB connection, total: 2
2009-03-22 11:33:35.588 Connected to database 'mythconverg' at host: 192.168.0.143
2009-03-22 11:33:35.596 mythfrontend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2009-03-22 11:33:35.596 Enabled verbose msgs:  important general playback
2009-03-22 11:33:36.448 max_width: 1280 max_height: 1024
2009-03-22 11:33:36.750 No theme dir: /home/celeron/.mythtv/themes/G.A.N.T
2009-03-22 11:33:36.758 Primary screen 0.
2009-03-22 11:33:36.760 Running in a window
2009-03-22 11:33:36.772 Using screen 0, 1280x1000 at 0,24
2009-03-22 11:33:36.774 No theme dir: /home/celeron/.mythtv/themes/G.A.N.T
2009-03-22 11:33:36.775 Switching to square mode (G.A.N.T)
2009-03-22 11:33:36.924 Using the Qt painter
2009-03-22 11:33:36.928 lirc init success using configuration file: /home/celeron/.mythtv/lircrc
2009-03-22 11:33:36.931 JoystickMenuClient Error: Joystick disabled - Failed to read /home/celeron/.mythtv/joystickmenurc
2009-03-22 11:33:39.312 Loading from: /usr/share/mythtv/themes/G.A.N.T/base.xml
2009-03-22 11:33:39.559 Loading from: /usr/share/mythtv/themes/default/base.xml
2009-03-22 11:33:39.788 Registering Internal as a media playback plugin.
2009-03-22 11:33:40.017 MonitorRegisterExtensions(0x100, gif,jpg,png)
2009-03-22 11:33:40.189 Failed to run 'cdrecord --scanbus'
2009-03-22 11:33:40.197 Failed to run 'cdrecord --scanbus -dev=ATA'
2009-03-22 11:33:40.213 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2009-03-22 11:33:40.351 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
Failed to bind for SIP connection 192.168.0.125
SIP listening on IP Address :5060 NAT address 
SIP: Cannot register; proxy, username or password not set
Destroying SipFsm object 
2009-03-22 11:33:40.782 No theme dir: /home/celeron/.mythtv/themes/G.A.N.T
2009-03-22 11:33:47.367 XMLParse::LoadTheme using /usr/share/mythtv/themes/G.A.N.T/ui.xml
2009-03-22 11:33:47.791 Connecting to backend server: 192.168.0.143:6543 (try 1 of 5)
2009-03-22 11:33:47.794 Using protocol version 40
2009-03-22 11:33:50.954 RingBuf(myth://192.168.0.143:6543/2231_20090322073000.mpg): OpenFile(myth://192.168.0.143:6543/2231_20090322073000.mpg, 1)
2009-03-22 11:33:50.998 RingBuf(myth://192.168.0.143:6543/2231_20090322073000.mpg): CalcReadAheadThresh(3049797969 KB)
			 -> threshhold(64 KB) min read(0 KB) blk size(32 KB)
2009-03-22 11:33:51.983 AFD: Stream #0, has id 0x49 codec id MPEG2VIDEO, type Video, bitrate 65000000 at 0x0xa52cb50
2009-03-22 11:33:51.992 VDP: Accepting: cmp(<= 719 576,> 0 0) dec(ffmpeg) cpus(1) skiploop(enabled) rend(xv-blit) osd(softblend) osdfade(enabled) deint(kerneldeint,linearblend) filt()
2009-03-22 11:33:51.993 VDP: Accepting: cmp(<= 1920 1088,> 0 0) dec(xvmc) cpus(1) skiploop(enabled) rend(xvmc-blit) osd(chromakey) osdfade(disabled) deint(bobdeint,onefield) filt()
2009-03-22 11:33:51.993 VDP: LoadBestPreferences(2048x2048, 0)
2009-03-22 11:33:52.001 VDP: LoadBestPreferences(2048x2048, 60)
2009-03-22 11:33:52.002 VDP: LoadBestPreferences(1920x1080, 60)
2009-03-22 11:33:52.002 Using 1 CPUs for decoding
2009-03-22 11:33:52.003 AFD: InitVideoCodec() 0xa29da40 id(MPEG2VIDEO) type (Video).
2009-03-22 11:33:52.003 detectInterlace(Detect Scan, Interlaced Scan, 29.97, 1080) ->Interlaced Scan
2009-03-22 11:33:52.004 AFD: EIA-608 caption 1 is in the English language.
2009-03-22 11:33:52.004 AFD: EIA-708 caption service #1 is in the English language.
2009-03-22 11:33:52.005 AFD: Using ffmpeg for video decoding
2009-03-22 11:33:52.005 AFD: Looking for decoder for MPEG2VIDEO
2009-03-22 11:33:52.006 AFD: Opened codec 0xa29da40, id(MPEG2VIDEO) type(Video)
2009-03-22 11:33:52.006 AFD: Stream #1, has id 0x52 codec id AC3, type Audio, bitrate 384000 at 0x0xa481070
2009-03-22 11:33:52.007 AFD: codec AC3 has 6 channels
2009-03-22 11:33:52.007 AFD: Looking for decoder for AC3
2009-03-22 11:33:52.008 AFD: Opened codec 0xa6223b0, id(AC3) type(Audio)
2009-03-22 11:33:52.022 RingBuf(myth://192.168.0.143:6543/2231_20090322073000.mpg): CalcReadAheadThresh(3049798285 KB)
			 -> threshhold(64 KB) min read(0 KB) blk size(32 KB)
2009-03-22 11:33:52.022 Dec: Selected track #1 in the English language(6647399)
2009-03-22 11:33:52.023 Dec: Selected track #1 in the English language(6647399)
2009-03-22 11:33:52.023 AFD: Recording has no position -- using libavformat seeking.
2009-03-22 11:33:52.023 AFD: Successfully opened decoder for file: "myth://192.168.0.143:6543/2231_20090322073000.mpg". novideo(0)
2009-03-22 11:33:52.040 VDP: Accepting: cmp(<= 719 576,> 0 0) dec(ffmpeg) cpus(1) skiploop(enabled) rend(xv-blit) osd(softblend) osdfade(enabled) deint(kerneldeint,linearblend) filt()
2009-03-22 11:33:52.040 VDP: Accepting: cmp(<= 1920 1088,> 0 0) dec(xvmc) cpus(1) skiploop(enabled) rend(xvmc-blit) osd(chromakey) osdfade(disabled) deint(bobdeint,onefield) filt()
2009-03-22 11:33:52.041 VDP: LoadBestPreferences(2048x2048, 0)
2009-03-22 11:33:52.041 VDP: LoadBestPreferences(2048x2048, 60)
2009-03-22 11:33:52.109 VideoOutputNull()
2009-03-22 11:33:52.109 VDP: LoadBestPreferences(1920x1088, 60)
2009-03-22 11:33:52.110 Display Rect  left: 0, top: 0, width: 0, height: 0, aspect: 1.33333
2009-03-22 11:33:52.110 Video Rect    left: 0, top: 0, width: 1920, height: 1080, aspect: 1.77778
2009-03-22 11:33:52.111 Created data @0xadda8020->0xae0a5022
2009-03-22 11:33:52.112 Created data @0xadaaa020->0xadda7022
2009-03-22 11:33:52.112 Created data @0xad7ac020->0xadaa9022
2009-03-22 11:33:52.112 Created data @0xad4ae020->0xad7ab022
2009-03-22 11:33:52.113 Created data @0xad1b0020->0xad4ad022
2009-03-22 11:33:52.113 Created data @0xaceb2020->0xad1af022
2009-03-22 11:33:52.114 Created data @0xacbb4020->0xaceb1022
2009-03-22 11:33:52.114 Created data @0xac8b6020->0xacbb3022
2009-03-22 11:33:52.115 Created data @0xac5b8020->0xac8b5022
2009-03-22 11:33:52.115 Created data @0xac2ba020->0xac5b7022
2009-03-22 11:33:52.115 Created data @0xabfbc020->0xac2b9022
2009-03-22 11:33:52.116 Created data @0xabcbe020->0xabfbb022
2009-03-22 11:33:52.116 Created data @0xab9c0020->0xabcbd022
2009-03-22 11:33:52.117 Created data @0xab6c2020->0xab9bf022
2009-03-22 11:33:52.117 Created data @0xab3c4020->0xab6c1022
2009-03-22 11:33:52.117 Created data @0xab0c6020->0xab3c3022
2009-03-22 11:33:52.118 Created data @0xaadc8020->0xab0c5022
2009-03-22 11:33:52.123 Created data @0xaaaca020->0xaadc7022
2009-03-22 11:33:52.124 Created data @0xaa7cc020->0xaaac9022
2009-03-22 11:33:52.126 Created data @0xaa4ce020->0xaa7cb022
2009-03-22 11:33:52.126 Created data @0xaa1d0020->0xaa4cd022
2009-03-22 11:33:52.126 Created data @0xa9ed2020->0xaa1cf022
2009-03-22 11:33:52.127 Created data @0xa9bd4020->0xa9ed1022
2009-03-22 11:33:52.127 Created data @0xa98d6020->0xa9bd3022
2009-03-22 11:33:52.130 Created data @0xa95d8020->0xa98d5022
2009-03-22 11:33:52.130 Created data @0xa92da020->0xa95d7022
2009-03-22 11:33:52.131 Created data @0xa8fdc020->0xa92d9022
2009-03-22 11:33:52.131 Created data @0xa8cde020->0xa8fdb022
2009-03-22 11:33:52.131 Created data @0xa89e0020->0xa8cdd022
2009-03-22 11:33:52.132 Created data @0xa86e2020->0xa89df022
2009-03-22 11:33:52.132 Created data @0xa83e4020->0xa86e1022
2009-03-22 11:33:52.142 Created data @0xa80e6020->0xa83e3022
2009-03-22 11:33:52.553 VDP: SetVideoRenderer(null)
2009-03-22 11:33:52.554 VDP: Old preferences: rend(xvmc-blit) osd(chromakey) deint(bobdeint,onefield) filt()
2009-03-22 11:33:52.554 VDP: New preferences: rend(null) osd(softblend) deint(linearblend,linearblend) filt()
2009-03-22 11:33:52.555 Display Rect  left: 0, top: 0, width: 0, height: 0, aspect: 1.33333
2009-03-22 11:33:52.555 Video Rect    left: 0, top: 0, width: 1920, height: 1080, aspect: 1.77778
2009-03-22 11:33:52.558 NVP: LoadFilters(''..) -> 0
2009-03-22 11:33:52.558 NVP: ClearAfterSeek(1)
2009-03-22 11:33:52.564 NVP: Waiting for prebuffer.. 0 AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
2009-03-22 11:33:52.706 NVP: Waiting for prebuffer.. 1 LLAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
2009-03-22 11:33:52.839 NVP: Waiting for prebuffer.. 2 uLULAAAAAAAAAAAAAAAAAAAAAAAAAAA
2009-03-22 11:33:52.973 NVP: Waiting for prebuffer.. 3 UuUULLAAAAAAAAAAAAAAAAAAAAAAAAA
2009-03-22 11:33:53.107 NVP: Waiting for prebuffer.. 4 UUUULUULAAAAAAAAAAAAAAAAAAAAAAA
2009-03-22 11:33:53.241 NVP: Waiting for prebuffer.. 5 UUUUuUULuAAAAAAAAAAAAAAAAAAAAAA
2009-03-22 11:33:53.376 NVP: Waiting for prebuffer.. 6 UUUUUUULUULAAAAAAAAAAAAAAAAAAAA
2009-03-22 11:33:53.565 AFD: HandleGopStart: gopset not set, syncing positionMap
2009-03-22 11:33:53.566 Resyncing position map. posmapStarted = 0 livetv(0) watchingRec(0)
2009-03-22 11:33:53.566 AFD: HandleGopStart: Initial key frame distance: 15.
2009-03-22 11:33:54.043 NVP: prebuffering pause
2009-03-22 11:33:54.043 NVP: Waiting for prebuffer.. 0 AAAAAAAAAAAAAAAALAULAAAAAAAAAAA
2009-03-22 11:33:54.177 NVP: Waiting for prebuffer.. 1 AAAAAAAAAAAAAAAAuAULULAAAAAAAAA
2009-03-22 11:33:54.311 NVP: Waiting for prebuffer.. 2 AAAAAAAAAAAAAAAAUAULUULAAAAAAAA
2009-03-22 11:33:54.401 TV: Attempting to change from None to WatchingPreRecorded
2009-03-22 11:33:54.412 RingBuf(myth://192.168.0.143:6543/2231_20090322073000.mpg): OpenFile(myth://192.168.0.143:6543/2231_20090322073000.mpg, 12)
2009-03-22 11:33:54.432 RingBuf(myth://192.168.0.143:6543/2231_20090322073000.mpg): CalcReadAheadThresh(3049797969 KB)
			 -> threshhold(64 KB) min read(0 KB) blk size(32 KB)
2009-03-22 11:33:54.444 NVP: Waiting for prebuffer.. 3 AAAAAAAAAAAAAAAAUAUuUULLAAAAAAA
2009-03-22 11:33:54.453 DPMS Deactivated 
2009-03-22 11:33:54.455 New DB connection, total: 3
2009-03-22 11:33:54.475 Connected to database 'mythconverg' at host: 192.168.0.143
2009-03-22 11:33:54.482 NVP: Exited decoder loop.
2009-03-22 11:33:54.578 ~VideoOutputNull()
2009-03-22 11:33:55.751 AFD: Stream #0, has id 0x49 codec id MPEG2VIDEO, type Video, bitrate 65000000 at 0x0xa4deb50
2009-03-22 11:33:55.757 VDP: Accepting: cmp(<= 719 576,> 0 0) dec(ffmpeg) cpus(1) skiploop(enabled) rend(xv-blit) osd(softblend) osdfade(enabled) deint(kerneldeint,linearblend) filt()
2009-03-22 11:33:55.757 VDP: Accepting: cmp(<= 1920 1088,> 0 0) dec(xvmc) cpus(1) skiploop(enabled) rend(xvmc-blit) osd(chromakey) osdfade(disabled) deint(bobdeint,onefield) filt()
2009-03-22 11:33:55.758 VDP: LoadBestPreferences(2048x2048, 0)
2009-03-22 11:33:55.758 VDP: LoadBestPreferences(2048x2048, 60)
2009-03-22 11:33:55.759 VDP: LoadBestPreferences(1920x1080, 60)
2009-03-22 11:33:55.759 Using 1 CPUs for decoding
2009-03-22 11:33:55.764 VDP: Accepting: cmp(<= 719 576,> 0 0) dec(ffmpeg) cpus(1) skiploop(enabled) rend(xv-blit) osd(softblend) osdfade(enabled) deint(kerneldeint,linearblend) filt()
2009-03-22 11:33:55.773 VDP: Accepting: cmp(<= 1920 1088,> 0 0) dec(xvmc) cpus(1) skiploop(enabled) rend(xvmc-blit) osd(chromakey) osdfade(disabled) deint(bobdeint,onefield) filt()
2009-03-22 11:33:55.773 VDP: LoadBestPreferences(2048x2048, 0)
2009-03-22 11:33:55.774 VDP: LoadBestPreferences(2048x2048, 60)
2009-03-22 11:33:55.774 VDP: LoadBestPreferences(1920x1080, 60)
2009-03-22 11:33:55.780 VideoOutputXv: XvMC version: 1.1
2009-03-22 11:33:55.901 XvMCSurfaceTypes::find(w 1920, h 1080, chroma 1, vld 0, idct 1, mpeg2, sub-width 0, sub-height 0, disp, p<= 356, 3250 <=p, port, surfNum)
2009-03-22 11:33:55.902 Trying XvMC port 325
2009-03-22 11:33:55.914 Found a suitable XvMC surface 0
2009-03-22 11:33:55.939 VDP: Accepting: cmp(<= 719 576,> 0 0) dec(ffmpeg) cpus(1) skiploop(enabled) rend(xv-blit) osd(softblend) osdfade(enabled) deint(kerneldeint,linearblend) filt()
2009-03-22 11:33:55.940 VDP: Accepting: cmp(<= 1920 1088,> 0 0) dec(xvmc) cpus(1) skiploop(enabled) rend(xvmc-blit) osd(chromakey) osdfade(disabled) deint(bobdeint,onefield) filt()
2009-03-22 11:33:55.943 VDP: LoadBestPreferences(2048x2048, 0)
2009-03-22 11:33:55.953 VDP: LoadBestPreferences(2048x2048, 60)
2009-03-22 11:33:55.956 VDP: LoadBestPreferences(1920x1080, 60)
2009-03-22 11:33:55.967 VideoOutputXv: @ j=0 Looking for flag[s]: XvInputMask  1d
2009-03-22 11:33:55.973 VideoOutputXv: Adaptor#0: NV17 Video Texture has flag[s]: XvInputMask XvImageMask 
2009-03-22 11:33:55.973 VideoOutputXv: Has XVideo flags...
2009-03-22 11:33:55.975 VideoOutputXv: Missing XV_BRIGHTNESS, rejecting.
2009-03-22 11:33:55.975 VideoOutputXv: Adaptor#1: NV05 Video Blitter has flag[s]: XvInputMask XvImageMask 
2009-03-22 11:33:55.975 VideoOutputXv: Has XVideo flags...
2009-03-22 11:33:55.976 VideoOutputXv: Missing XV_BRIGHTNESS, rejecting.
2009-03-22 11:33:55.977 VideoOutputXv: @ j=1 Looking for flag[s]: XvInputMask  d
2009-03-22 11:33:55.977 VideoOutputXv: Adaptor#0: NV17 Video Texture has flag[s]: XvInputMask XvImageMask 
2009-03-22 11:33:55.979 VideoOutputXv: Has XVideo flags...
2009-03-22 11:33:56.030 VideoOutputXv: Missing XV_COLORKEY, rejecting.
2009-03-22 11:33:56.030 VideoOutputXv: Adaptor#1: NV05 Video Blitter has flag[s]: XvInputMask XvImageMask 
2009-03-22 11:33:56.030 VideoOutputXv: Has XVideo flags...
2009-03-22 11:33:56.035 VideoOutputXv: Missing XV_COLORKEY, rejecting.
2009-03-22 11:33:56.035 VideoOutputXv: @ j=2 Looking for flag[s]: XvInputMask  15
2009-03-22 11:33:56.036 VideoOutputXv: Adaptor#0: NV17 Video Texture has flag[s]: XvInputMask XvImageMask 
2009-03-22 11:33:56.036 VideoOutputXv: Has XVideo flags...
2009-03-22 11:33:56.043 VideoOutputXv: Missing XV_BRIGHTNESS, rejecting.
2009-03-22 11:33:56.043 VideoOutputXv: Adaptor#1: NV05 Video Blitter has flag[s]: XvInputMask XvImageMask 
2009-03-22 11:33:56.043 VideoOutputXv: Has XVideo flags...
2009-03-22 11:33:56.046 VideoOutputXv: Missing XV_BRIGHTNESS, rejecting.
2009-03-22 11:33:56.046 VideoOutputXv: @ j=3 Looking for flag[s]: XvInputMask  5
2009-03-22 11:33:56.047 VideoOutputXv: Adaptor#0: NV17 Video Texture has flag[s]: XvInputMask XvImageMask 
2009-03-22 11:33:56.047 VideoOutputXv: Has XVideo flags...
2009-03-22 11:33:56.047 VideoOutputXv: Here...
2009-03-22 11:33:56.047 XvMCSurfaceTypes::find(w 1920, h 1080, chroma 1, vld 0, idct 1, mpeg2, sub-width 0, sub-height 0, disp, p<= 356, 3250 <=p, port, surfNum)
2009-03-22 11:33:56.047 Trying XvMC port 325
2009-03-22 11:33:56.050 Found a suitable XvMC surface 0
2009-03-22 11:33:56.052 VideoOutputXv: Grabbed xv port 325
2009-03-22 11:33:56.052 VideoOutputXv: XvMC surface found with IDCT support on port 325
2009-03-22 11:33:56.258 VideoOutputXv: Closing XVideo port 325
2009-03-22 11:33:56.259 AFD: InitVideoCodec() 0xa660910 id(MPEG2VIDEO_XVMC) type (Video).
2009-03-22 11:33:56.260 detectInterlace(Detect Scan, Interlaced Scan, 29.97, 1080) ->Interlaced Scan
2009-03-22 11:33:56.261 AFD: EIA-608 caption 1 is in the English language.
2009-03-22 11:33:56.261 AFD: EIA-708 caption service #1 is in the English language.
2009-03-22 11:33:56.262 AFD: Using xvmc for video decoding
2009-03-22 11:33:56.262 AFD: Looking for decoder for MPEG2VIDEO_XVMC
2009-03-22 11:33:56.263 AFD: Opened codec 0xa660910, id(MPEG2VIDEO_XVMC) type(Video)
2009-03-22 11:33:56.263 AFD: Stream #1, has id 0x52 codec id AC3, type Audio, bitrate 384000 at 0x0xa576330
2009-03-22 11:33:56.264 AFD: codec AC3 has 6 channels
2009-03-22 11:33:56.265 AFD: Looking for decoder for AC3
2009-03-22 11:33:56.269 AFD: Opened codec 0xa681890, id(AC3) type(Audio)
2009-03-22 11:33:56.278 RingBuf(myth://192.168.0.143:6543/2231_20090322073000.mpg): CalcReadAheadThresh(3049798285 KB)
			 -> threshhold(64 KB) min read(0 KB) blk size(32 KB)
2009-03-22 11:33:56.300 Opening audio device 'default'. ch 2(2) sr 48000
2009-03-22 11:33:56.302 Opening ALSA audio device 'default'.
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL /dev/mixer
2009-03-22 11:33:56.472 AudioOutput Warning: Mixer attach error -2: No such file or directory
			Check Mixer Name in Setup: '/dev/mixer'
2009-03-22 11:33:56.480 Dec: Selected track #1 in the English language(6647399)
2009-03-22 11:33:56.481 Dec: Selected track #1 in the English language(6647399)
2009-03-22 11:33:56.483 Resyncing position map. posmapStarted = 0 livetv(0) watchingRec(0)
2009-03-22 11:33:57.100 Position map filled from DB to: 53817
2009-03-22 11:33:57.106 SyncPositionMap prerecorded, from DB: 3626 entries
2009-03-22 11:33:57.117 SyncPositionMap, new totframes: 53817, new length: 1795, posMap size: 3626
2009-03-22 11:33:57.117 AFD: Position map found
2009-03-22 11:33:57.118 AFD: Successfully opened decoder for file: "myth://192.168.0.143:6543/2231_20090322073000.mpg". novideo(0)
2009-03-22 11:33:57.196 VideoOutputXv: XvMC version: 1.1
2009-03-22 11:33:57.197 VideoOutput: Allowed renderers: xvmc-blit
2009-03-22 11:33:57.198 VideoOutput: Allowed renderers (filt: xvmc): xvmc-blit
2009-03-22 11:33:57.198 VideoOutput: Trying video renderer: xvmc-blit
2009-03-22 11:33:57.203 VDP: Accepting: cmp(<= 719 576,> 0 0) dec(ffmpeg) cpus(1) skiploop(enabled) rend(xv-blit) osd(softblend) osdfade(enabled) deint(kerneldeint,linearblend) filt()
2009-03-22 11:33:57.203 VDP: Accepting: cmp(<= 1920 1088,> 0 0) dec(xvmc) cpus(1) skiploop(enabled) rend(xvmc-blit) osd(chromakey) osdfade(disabled) deint(bobdeint,onefield) filt()
2009-03-22 11:33:57.203 VDP: LoadBestPreferences(2048x2048, 0)
2009-03-22 11:33:57.204 VDP: LoadBestPreferences(2048x2048, 60)
2009-03-22 11:33:57.270 VideoOutputXv: ctor
2009-03-22 11:33:57.304 XOff: 0, YOff: 0
2009-03-22 11:33:57.305 VDP: LoadBestPreferences(1920x1088, 60)
2009-03-22 11:33:57.306 Display Rect  left: 0, top: 125, width: 1280, height: 750, aspect: 1.33333
2009-03-22 11:33:57.306 Video Rect    left: 0, top: 0, width: 1920, height: 1080, aspect: 1.77778
2009-03-22 11:33:57.307 VideoOutputXv: Pixel dimensions: Screen 1280x1000, window 1280x1000
2009-03-22 11:33:57.337 VideoOutputXv: Estimated display dimensions: 325x260 mm  Aspect: 1.25
2009-03-22 11:33:57.337 VideoOutputXv: Estimated window dimensions: 325x260 mm  Aspect: 1.25
2009-03-22 11:33:57.339 VideoOutputXv: XvMC version: 1.1
2009-03-22 11:33:57.339 VideoOutputXv: InitSetupBuffers() render: xvmc-blit, allowed: xvmc-blit
2009-03-22 11:33:57.347 VDP: Accepting: cmp(<= 719 576,> 0 0) dec(ffmpeg) cpus(1) skiploop(enabled) rend(xv-blit) osd(softblend) osdfade(enabled) deint(kerneldeint,linearblend) filt()
2009-03-22 11:33:57.348 VDP: Accepting: cmp(<= 1920 1088,> 0 0) dec(xvmc) cpus(1) skiploop(enabled) rend(xvmc-blit) osd(chromakey) osdfade(disabled) deint(bobdeint,onefield) filt()
2009-03-22 11:33:57.348 VDP: LoadBestPreferences(2048x2048, 0)
2009-03-22 11:33:57.349 VDP: LoadBestPreferences(2048x2048, 60)
2009-03-22 11:33:57.350 VDP: LoadBestPreferences(1920x1088, 60)
2009-03-22 11:33:57.365 VideoOutputXv: @ j=0 Looking for flag[s]: XvInputMask  1d
2009-03-22 11:33:57.365 VideoOutputXv: Adaptor#0: NV17 Video Texture has flag[s]: XvInputMask XvImageMask 
2009-03-22 11:33:57.366 VideoOutputXv: Has XVideo flags...
2009-03-22 11:33:57.367 VideoOutputXv: Missing XV_BRIGHTNESS, rejecting.
2009-03-22 11:33:57.368 VideoOutputXv: Adaptor#1: NV05 Video Blitter has flag[s]: XvInputMask XvImageMask 
2009-03-22 11:33:57.368 VideoOutputXv: Has XVideo flags...
2009-03-22 11:33:57.369 VideoOutputXv: Missing XV_BRIGHTNESS, rejecting.
2009-03-22 11:33:57.370 VideoOutputXv: @ j=1 Looking for flag[s]: XvInputMask  d
2009-03-22 11:33:57.370 VideoOutputXv: Adaptor#0: NV17 Video Texture has flag[s]: XvInputMask XvImageMask 
2009-03-22 11:33:57.370 VideoOutputXv: Has XVideo flags...
2009-03-22 11:33:57.371 VideoOutputXv: Missing XV_COLORKEY, rejecting.
2009-03-22 11:33:57.372 VideoOutputXv: Adaptor#1: NV05 Video Blitter has flag[s]: XvInputMask XvImageMask 
2009-03-22 11:33:57.372 VideoOutputXv: Has XVideo flags...
2009-03-22 11:33:57.373 VideoOutputXv: Missing XV_COLORKEY, rejecting.
2009-03-22 11:33:57.374 VideoOutputXv: @ j=2 Looking for flag[s]: XvInputMask  15
2009-03-22 11:33:57.374 VideoOutputXv: Adaptor#0: NV17 Video Texture has flag[s]: XvInputMask XvImageMask 
2009-03-22 11:33:57.374 VideoOutputXv: Has XVideo flags...
2009-03-22 11:33:57.375 VideoOutputXv: Missing XV_BRIGHTNESS, rejecting.
2009-03-22 11:33:57.376 VideoOutputXv: Adaptor#1: NV05 Video Blitter has flag[s]: XvInputMask XvImageMask 
2009-03-22 11:33:57.376 VideoOutputXv: Has XVideo flags...
2009-03-22 11:33:57.377 VideoOutputXv: Missing XV_BRIGHTNESS, rejecting.
2009-03-22 11:33:57.378 VideoOutputXv: @ j=3 Looking for flag[s]: XvInputMask  5
2009-03-22 11:33:57.378 VideoOutputXv: Adaptor#0: NV17 Video Texture has flag[s]: XvInputMask XvImageMask 
2009-03-22 11:33:57.379 VideoOutputXv: Has XVideo flags...
2009-03-22 11:33:57.379 VideoOutputXv: Here...
2009-03-22 11:33:57.460 XvMCSurfaceTypes::find(w 1920, h 1088, chroma 1, vld 0, idct 1, mpeg2, sub-width 0, sub-height 0, disp, p<= 356, 3250 <=p, port, surfNum)
2009-03-22 11:33:57.460 Trying XvMC port 325
2009-03-22 11:33:57.468 Found a suitable XvMC surface 0
2009-03-22 11:33:57.470 VideoOutputXv: Grabbed xv port 325
2009-03-22 11:33:57.470 VideoOutputXv: XvMC surface found with IDCT support on port 325
2009-03-22 11:33:57.470 VideoOutputXv: XvMC Adaptor Name: 'NV17 Video Texture'
2009-03-22 11:33:57.601 VDP: SetVideoRenderer(xvmc-blit)
2009-03-22 11:33:57.601 VDP: SetVideoRender(xvmc-blit) == GetVideoRenderer()
2009-03-22 11:33:57.603 VideoOutputXv: Chromakeying not possible with this XVideo port.
2009-03-22 11:33:57.603 VideoOutputXv: Ack! Disabling ChromaKey OSD
			We can't use ChromaKey OSD if chromakeying is not supported!
2009-03-22 11:33:57.604 VideoOutputXv: DiscardFrames(1)
2009-03-22 11:33:57.604 VideoOutputXv: DiscardFrames() 1: AAAAAAAA
2009-03-22 11:33:57.605 VideoOutputXv: DiscardFrames() 2: AAAAAAAA
2009-03-22 11:33:57.605 VideoOutputXv: DiscardFrames() 3: AAAAAAAA -- done()
2009-03-22 11:33:57.607 VideoOutputXv: DiscardFrames(1)
2009-03-22 11:33:57.607 VideoOutputXv: DiscardFrames() 1: AAAAAAAA
2009-03-22 11:33:57.608 VideoOutputXv: DiscardFrames() 2: AAAAAAAA
2009-03-22 11:33:57.608 VideoOutputXv: DiscardFrames() 3: AAAAAAAA -- done()
2009-03-22 11:34:14.537 TV: StartPlayer(): took 20000 ms to start player.
2009-03-22 11:34:14.537 TV Error: StartPlayer(): NVP is not playing after 20000 msec
2009-03-22 11:34:14.538 TV: Changing from None to WatchingPreRecorded
2009-03-22 11:34:14.544 TV Error: nvp->IsPlaying() timed out
2009-03-22 11:34:14.544 TV: Attempting to change from WatchingPreRecorded to None
2009-03-22 11:34:14.545 TV: StopStuff() -- begin
2009-03-22 11:34:14.545 TV: StopStuff(): stopping ring buffer[s]
2009-03-22 11:34:14.555 TV: StopStuff(): stopping player[s] (1/2)
2009-03-22 11:34:14.555 TV: StopStuff(): stopping player[s] (2/2)
^CSignal: Interrupt
Ungrabbing XVideo port: 325
Mutex destroy failure: Device or resource busy
celeron@celeron-desktop:~$ 


A Little long but still a black screen

---

