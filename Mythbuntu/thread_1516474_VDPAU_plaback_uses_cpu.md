---
title: "VDPAU plaback uses cpu"
date: 2010-06-23
forum: Mythbuntu
---

### Post by My Name on 2010-06-23
Looking at the CPU usage when playing livetv I am getting a heavy load. I was under the impression the using vdpau would take the video playback load??
It certainly does when using PCLinuxOS. I was using it for a couple of days and the CPU was running at about 10-15%. now it's running at 80+%.
Any ideas why the CPU would be working so hard?
My playback settings are VDPAU High quality
hardware is an acer revo cheap single core one.

---

### Post by uncle hammy on 2010-06-23
I use VDPAU normal, and I have noticed that 720p and greater streams play using between 5% and 12% CPU usage.  However, less than 720p streams (think a digital sub channel like 8.3) play using 40% - 60% CPU usage.  Figure that one out, lower resolution, 5 to 10 times the CPU usage.

---

### Post by jyavenard on 2010-06-24
> **uncle hammy said:**
> I use VDPAU normal, and I have noticed that 720p and greater streams play using between 5% and 12% CPU usage.  However, less than 720p streams (think a digital sub channel like 8.3) play using 40% - 60% CPU usage.  Figure that one out, lower resolution, 5 to 10 times the CPU usage.

Probably not using VDPAU then..
Check the log with -v playback, you're likely going to see some errors that vdpau couldn't be used and as such is defaulting back to software playback.
Likely related to the deinterlacer configured

---

### Post by My Name on 2010-06-25
cool, i'll check that out. I have checked the de-interlacing settings on the mythtv website and configured mythtv to use the settings for my card, but i'll double check. my card is an on board ion 9400 BTW.

---

### Post by uncle hammy on 2010-06-25
> **jyavenard said:**
> Probably not using VDPAU then..
Check the log with -v playback, you're likely going to see some errors that vdpau couldn't be used and as such is defaulting back to software playback.
Likely related to the deinterlacer configured

Here is the log from a sample playing a SD stream, top indicated CPU usage between 40% - 60%.  Near as I can tell from it, VDPAU is being used.....

```

2010-06-25 06:57:54.977 TV: StartTV() -- begin
2010-06-25 06:57:54.977 TV: ctor -- begin
2010-06-25 06:57:54.997 TV: ctor -- end
2010-06-25 06:57:54.997 TV: Init -- begin
2010-06-25 06:57:54.998 TV: Init -- end channel groups
2010-06-25 06:57:55.018 TV: DrawUnusedRects() -- begin
2010-06-25 06:57:55.018 TV: DrawUnusedRects() -- end
2010-06-25 06:57:55.019 TV: Init -- end
2010-06-25 06:57:55.039 TV: tv->LiveTV() -- begin
2010-06-25 06:57:55.062 TV: tv->LiveTV() -- end
2010-06-25 06:57:55.063 TV: StartTV -- process events begin
2010-06-25 06:57:55.213 TV: HandleStateChange(0) -- begin
2010-06-25 06:57:55.213 TV: Attempting to change from None to WatchingLiveTV
2010-06-25 06:57:55.213 MythContext: Connecting to backend server: 192.168.25.252:6543 (try 1 of 1)
2010-06-25 06:57:55.214 Using protocol version 56
2010-06-25 06:57:55.228 Spawning LiveTV Recorder -- begin
2010-06-25 06:57:55.286 Spawning LiveTV Recorder -- end
2010-06-25 06:57:55.288 LiveTVChain(live-myth-lr-2010-06-25T06:57:55): ReloadAll(): Added new recording
2010-06-25 06:57:55.291 ProgramInfo(): Updated pathname '':'' -> '1352_20100625065753.mpg'
2010-06-25 06:57:55.309 We have a playbackURL(myth://192.168.25.252:6543/1352_20100625065753.mpg) & cardtype(DUMMY)
2010-06-25 06:57:55.309 We have a RingBuffer
2010-06-25 06:57:55.369 TV: StartRecorder(): took 1 ms to start recorder.
2010-06-25 06:57:55.369 TV: StartPlayer(0, WatchingLiveTV, main) -- begin
2010-06-25 06:57:55.369 TV: Elapsed time since TV constructor was called: 392 ms
2010-06-25 06:57:55.413 detectInterlace(Ignore Scan, Interlaced Scan, 25, 576) ->Interlaced Scan
2010-06-25 06:57:55.418 NVP(0): Disabling Audio, params(-1,2,44100)
2010-06-25 06:57:55.421 VideoOutput: Allowed renderers: xv-blit,xshm,xlib,opengl,vdpau
2010-06-25 06:57:55.421 VideoOutput: Allowed renderers (filt: dummy): xlib,xshm,xv-blit,opengl,vdpau
2010-06-25 06:57:55.425 VDP: Accepting: cmp(>= 0 720) dec(vdpau) cpus(1) rend(vdpau) osd(vdpau) osdfade(enabled) deint(vdpaubasicdoublerate,vdpaubasic) filt(vdpaucolorspace=auto)
2010-06-25 06:57:55.426 VDP: Accepting: cmp(> 0 0) dec(vdpau) cpus(1) rend(vdpau) osd(vdpau) osdfade(enabled) deint(vdpauadvanceddoublerate,vdpauadvanced) filt(vdpaucolorspace=auto)
2010-06-25 06:57:55.426 VDP: LoadBestPreferences(2048x2048, 0)
2010-06-25 06:57:55.426 VDP: LoadBestPreferences(2048x2048, 60)
2010-06-25 06:57:55.426 VDP: LoadBestPreferences(720x576, 60)
2010-06-25 06:57:55.426 VideoOutput: Preferred renderer: vdpau
2010-06-25 06:57:55.426 VideoOutput: Trying video renderer: 'vdpau'
2010-06-25 06:57:55.443 VDP: Accepting: cmp(>= 0 720) dec(vdpau) cpus(1) rend(vdpau) osd(vdpau) osdfade(enabled) deint(vdpaubasicdoublerate,vdpaubasic) filt(vdpaucolorspace=auto)
2010-06-25 06:57:55.443 VDP: Accepting: cmp(> 0 0) dec(vdpau) cpus(1) rend(vdpau) osd(vdpau) osdfade(enabled) deint(vdpauadvanceddoublerate,vdpauadvanced) filt(vdpaucolorspace=auto)
2010-06-25 06:57:55.443 VDP: LoadBestPreferences(2048x2048, 0)
2010-06-25 06:57:55.443 VDP: LoadBestPreferences(2048x2048, 60)
2010-06-25 06:57:55.452 VideoOutWindow::SetPIPState. pip_state: 0]
2010-06-25 06:57:55.452 Snapping height to avoid scaling: height: 576, top: 96
2010-06-25 06:57:55.452 Display Rect  left: 0, top: 96, width: 1360, height: 576, aspect: 1.33333
2010-06-25 06:57:55.452 Video Rect    left: 0, top: 0, width: 720, height: 576, aspect: 1.77778
2010-06-25 06:57:55.452 VDP: LoadBestPreferences(720x576, 60)
2010-06-25 06:57:55.452 Snapping height to avoid scaling: height: 576, top: 96
2010-06-25 06:57:55.452 Display Rect  left: 0, top: 96, width: 1360, height: 576, aspect: 1.33333
2010-06-25 06:57:55.453 Video Rect    left: 0, top: 0, width: 720, height: 576, aspect: 1.77778
2010-06-25 06:57:55.453 VDP: SetVideoRenderer(vdpau)
2010-06-25 06:57:55.453 VDP: SetVideoRender(vdpau) == GetVideoRenderer()
2010-06-25 06:57:55.455 VideoOutput: Pixel dimensions: Screen 1360x768, window 1360x768
2010-06-25 06:57:55.455 VideoOutput: Actual display dimensions: 345x195 mm  Aspect: 1.76923
2010-06-25 06:57:55.455 VideoOutput: Estimated window dimensions: 345x195 mm  Aspect: 1.76923
2010-06-25 06:57:55.560 ProgramInfo(): Updated pathname '':'' -> '1352_20100625065753.mpg'
2010-06-25 06:57:55.601 VDPAU: Created 2 output surfaces.
2010-06-25 06:57:55.601 VDPAU: Set colorkey to 0x20202
2010-06-25 06:57:55.601 VDPAU: Version 1
2010-06-25 06:57:55.601 VDPAU: Information NVIDIA VDPAU Driver Shared Library  195.36.24  Thu Apr 22 19:52:55 PDT 2010
2010-06-25 06:57:55.601 VDPAU: HQ Scaling not supported.
2010-06-25 06:57:55.601 VDPAU: MPEG4 hardware acceleration not supported.
2010-06-25 06:57:55.601 VDPAU: Created VDPAU render device 1360x768
2010-06-25 06:57:55.603 VidOutVDPAU: Created VDPAU osd (1360x768)
2010-06-25 06:57:55.623 ProgramInfo(): Updated pathname '':'' -> '1352_20100625065753.mpg'
2010-06-25 06:57:55.632 VidOutVDPAU: PictureAttributes: Brightness, Contrast, Colour, Hue
2010-06-25 06:57:55.648 VidOutVDPAU: Using ITU BT.601 colorspace
2010-06-25 06:57:55.648 Display Rect  left: 0, top: 0, width: 1360, height: 768, aspect: 1.77778
2010-06-25 06:57:55.648 Video Rect    left: 0, top: 0, width: 720, height: 576, aspect: 1.77778
2010-06-25 06:57:55.648 VidOutVDPAU: Created VDPAU context (software decode)
2010-06-25 06:57:55.654 Over/underscan. V: 0, H: 0
2010-06-25 06:57:55.654 Display Rect  left: 0, top: 0, width: 1360, height: 768, aspect: 1.77778
2010-06-25 06:57:55.654 Video Rect    left: 0, top: 0, width: 720, height: 576, aspect: 1.77778
2010-06-25 06:57:55.654 VDP: LoadBestPreferences(720x576, 25)
2010-06-25 06:57:55.656 FilterManager: GetFilterInfo(convert) returning: 0x0
2010-06-25 06:57:55.657 NVP(0): LoadFilters('vdpaucolorspace=auto'..) -> 0x0
2010-06-25 06:57:55.659 OSD Theme Dimensions W: 1280 H: 720
2010-06-25 06:57:55.685 ProgramInfo(): Updated pathname '':'' -> '1352_20100625065753.mpg'
2010-06-25 06:57:55.744 LiveTVChain(live-myth-lr-2010-06-25T06:57:55): ReloadAll(): Added new recording
2010-06-25 06:57:55.748 ProgramInfo(): Updated pathname '':'' -> '1352_20100625065754.mpg'
2010-06-25 06:57:55.815 ProgramInfo(): Updated pathname '':'' -> '1352_20100625065754.mpg'
2010-06-25 06:57:55.873 ProgramInfo(): Updated pathname '':'' -> '1352_20100625065754.mpg'
2010-06-25 06:57:55.902 playCtx: StartDecoderThread(): took 483 ms to start player.
2010-06-25 06:57:55.902 TV: StartPlayer(0, WatchingLiveTV, main) -- end ok
2010-06-25 06:57:55.902 TV: Changing from None to WatchingLiveTV
2010-06-25 06:57:55.902 TV: State is LiveTV & mctx == ctx
2010-06-25 06:57:55.903 NVP(0): ClearAfterSeek(1)
2010-06-25 06:57:55.903 VidOutVDPAU: ClearAfterSeek()
2010-06-25 06:57:55.903 VidOutVDPAU: DiscardFrames(0)
2010-06-25 06:57:55.903 VideoBuffers::DiscardFrames(0): AAAAAAAAAAAAAAAAA
2010-06-25 06:57:55.903 VideoBuffers::DiscardFrames(0): AAAAAAAAAAAAAAAAA -- done
2010-06-25 06:57:55.903 VidOutVDPAU: DiscardFrames() 3: AAAAAAAAAAAAAAAAA -- done()
2010-06-25 06:57:55.904 New DB connection, total: 3
2010-06-25 06:57:55.904 TV: UpdateOSDInput done
2010-06-25 06:57:55.904 TV: UpdateLCD done
2010-06-25 06:57:55.906 Realtime priority would require SUID as root.
2010-06-25 06:57:55.906 Connected to database 'mythconverg' at host: 192.168.25.252
2010-06-25 06:57:55.907 VDP: GetFilteredDeint() : vdpau -> 'vdpauadvanceddoublerate'
2010-06-25 06:57:55.908 VidOutVDPAU: Enabled deinterlacing.
2010-06-25 06:57:55.909 NVP(0): DoPause() -- begin
2010-06-25 06:57:55.909 rate: 25 speed: 1 skip: 1 = interval 40000
2010-06-25 06:57:55.909 NVP(0): DoPause() -- setting paused
2010-06-25 06:57:55.909 LiveTVChain(live-myth-lr-2010-06-25T06:57:55): SwitchTo(1)
2010-06-25 06:57:55.909 LiveTVChain(live-myth-lr-2010-06-25T06:57:55): Entry@1: '1352_20100625065754'
2010-06-25 06:57:55.909 JumpToProgram(void)
2010-06-25 06:57:55.909 TV: ITVRestart done
2010-06-25 06:57:55.914 ProgramInfo(): Updated pathname '':'' -> '1352_20100625065754.mpg'
2010-06-25 06:57:55.914 TV: HandleStateChange(0) -- end
2010-06-25 06:57:55.915 DRMVideoSync: Could not open device /dev/dri/card0, No such file or directory
2010-06-25 06:57:55.915 OpenGLVideoSync()
2010-06-25 06:57:55.919 FilterManager: GetFilterInfo(convert) returning: 0x0
2010-06-25 06:57:55.919 NVP(0): LoadFilters('vdpaucolorspace=auto'..) -> 0x0
2010-06-25 06:57:55.927 RingBuf(myth://192.168.25.252:6543/1352_20100625065753.mpg): OpenFile(myth://192.168.25.252:6543/1352_20100625065754.mpg, 12)
2010-06-25 06:57:55.929 Forcing GLX version to 1.2 (orig 1.4)
2010-06-25 06:57:55.930 GLCtx: Created OpenGL window.
2010-06-25 06:57:55.930 GLCtx: Created GLX context.
2010-06-25 06:57:55.930 GLCtx: GLX Version: 1.2
2010-06-25 06:57:55.930 GLCtx: Direct rendering: Yes
2010-06-25 06:57:55.947 ScreenSaverX11Private: ResetTimer -- begin
2010-06-25 06:57:55.948 ScreenSaverX11Private: StopTimer
2010-06-25 06:57:55.949 ScreenSaverX11Private: StartTimer
2010-06-25 06:57:55.949 ScreenSaverX11Private: ResetTimer -- end
2010-06-25 06:57:55.968 GLCtx: OpenGL vendor  : NVIDIA Corporation
2010-06-25 06:57:55.968 GLCtx: OpenGL renderer: GeForce 8400 GS/PCI/SSE2
2010-06-25 06:57:55.968 GLCtx: OpenGL version : 3.2.0 NVIDIA 195.36.24
2010-06-25 06:57:55.968 GLCtx: Max texture size: 8192 x 8192
2010-06-25 06:57:55.968 GLCtx: Max texture units: 4
2010-06-25 06:57:55.969 Set video sync frame interval to 40000
2010-06-25 06:57:55.981 Video timing method: SGI OpenGL
2010-06-25 06:57:55.981 Refresh rate: 16662, frame interval: 40000
2010-06-25 06:57:55.990 RingBuf(myth://192.168.25.252:6543/1352_20100625065754.mpg): CalcReadAheadThresh(0 KB)
			 -> threshhold(64 KB) min read(0 KB) blk size(32 KB)
2010-06-25 06:57:56.069 VDPAU: Added 2 output surfaces (total 4, max 4)
2010-06-25 06:57:56.418 'nice /usr/share/mythtv/mythweather/scripts/us_nws/animaps.pl -u ENG -d /home/USER/.mythtv/MythWeather/Animated-Map-Download http://images.weather.com/looper/archive/us_mw_4regradar_plus_us' has exited
2010-06-25 06:57:56.418 Unable to save data to cachefile: /home/USER/.mythtv/MythWeather/Animated-Map-Download/cache_http://images.weather.com/looper/archive/us_mw_4regradar_plus_us
2010-06-25 06:57:57.208 AFD: Stream #0, has id 0x41 codec id MPEG2VIDEO, type Video, bitrate 10000000 at 0x7f6e280b2710
2010-06-25 06:57:57.212 VDP: Accepting: cmp(>= 0 720) dec(vdpau) cpus(1) rend(vdpau) osd(vdpau) osdfade(enabled) deint(vdpaubasicdoublerate,vdpaubasic) filt(vdpaucolorspace=auto)
2010-06-25 06:57:57.212 VDP: Accepting: cmp(> 0 0) dec(vdpau) cpus(1) rend(vdpau) osd(vdpau) osdfade(enabled) deint(vdpauadvanceddoublerate,vdpauadvanced) filt(vdpaucolorspace=auto)
2010-06-25 06:57:57.212 VDP: LoadBestPreferences(2048x2048, 0)
2010-06-25 06:57:57.212 VDP: LoadBestPreferences(2048x2048, 60)
2010-06-25 06:57:57.212 VDP: LoadBestPreferences(704x480, 60)
2010-06-25 06:57:57.215 VDP: Accepting: cmp(>= 0 720) dec(vdpau) cpus(1) rend(vdpau) osd(vdpau) osdfade(enabled) deint(vdpaubasicdoublerate,vdpaubasic) filt(vdpaucolorspace=auto)
2010-06-25 06:57:57.216 VDP: Accepting: cmp(> 0 0) dec(vdpau) cpus(1) rend(vdpau) osd(vdpau) osdfade(enabled) deint(vdpauadvanceddoublerate,vdpauadvanced) filt(vdpaucolorspace=auto)
2010-06-25 06:57:57.216 VDP: LoadBestPreferences(2048x2048, 0)
2010-06-25 06:57:57.216 VDP: LoadBestPreferences(2048x2048, 60)
2010-06-25 06:57:57.216 VDP: LoadBestPreferences(704x480, 60)
2010-06-25 06:57:57.219 VDP: Accepting: cmp(>= 0 720) dec(vdpau) cpus(1) rend(vdpau) osd(vdpau) osdfade(enabled) deint(vdpaubasicdoublerate,vdpaubasic) filt(vdpaucolorspace=auto)
2010-06-25 06:57:57.219 VDP: Accepting: cmp(> 0 0) dec(vdpau) cpus(1) rend(vdpau) osd(vdpau) osdfade(enabled) deint(vdpauadvanceddoublerate,vdpauadvanced) filt(vdpaucolorspace=auto)
2010-06-25 06:57:57.219 VDP: LoadBestPreferences(2048x2048, 0)
2010-06-25 06:57:57.220 VDP: LoadBestPreferences(2048x2048, 60)
2010-06-25 06:57:57.220 VDP: LoadBestPreferences(704x480, 60)
2010-06-25 06:57:57.222 Using 1 CPUs for decoding
2010-06-25 06:57:57.225 AFD: InitVideoCodec() 0x7f6e29018070 id(MPEG2VIDEO) type (Video).
2010-06-25 06:57:57.229 VDP: Accepting: cmp(>= 0 720) dec(vdpau) cpus(1) rend(vdpau) osd(vdpau) osdfade(enabled) deint(vdpaubasicdoublerate,vdpaubasic) filt(vdpaucolorspace=auto)
2010-06-25 06:57:57.230 VDP: Accepting: cmp(> 0 0) dec(vdpau) cpus(1) rend(vdpau) osd(vdpau) osdfade(enabled) deint(vdpauadvanceddoublerate,vdpauadvanced) filt(vdpaucolorspace=auto)
2010-06-25 06:57:57.230 VDP: LoadBestPreferences(2048x2048, 0)
2010-06-25 06:57:57.231 VDP: LoadBestPreferences(2048x2048, 60)
2010-06-25 06:57:57.231 VDP: LoadBestPreferences(704x480, 60)
2010-06-25 06:57:57.231 VidOutVDPAU: InputChanged(704,480,1.33333) 'None'->'MPEG2 VDPAU'
2010-06-25 06:57:57.233 VidOutVDPAU: DiscardFrames(1)
2010-06-25 06:57:57.233 VideoBuffers::DiscardFrames(1): AAAAAAAAAAAAAAAAA
2010-06-25 06:57:57.233 VideoBuffers::DiscardFrames(): AAAAAAAAAAAAAAAAA -- done()
2010-06-25 06:57:57.233 VideoBuffers::DiscardFrames(1): AAAAAAAAAAAAAAAAA -- done
2010-06-25 06:57:57.233 VidOutVDPAU: DiscardFrames() 3: AAAAAAAAAAAAAAAAA -- done()
2010-06-25 06:57:57.264 Display Rect  left: 0, top: 0, width: 1360, height: 768, aspect: 1.77778
2010-06-25 06:57:57.264 Video Rect    left: 0, top: 0, width: 704, height: 480, aspect: 1.77778
2010-06-25 06:57:57.265 VDP: LoadBestPreferences(704x480, 25)
2010-06-25 06:57:57.265 Display Rect  left: 0, top: 0, width: 1360, height: 768, aspect: 1.77778
2010-06-25 06:57:57.265 Video Rect    left: 0, top: 0, width: 704, height: 480, aspect: 1.77778
2010-06-25 06:57:57.265 VDP: SetVideoRenderer(vdpau)
2010-06-25 06:57:57.265 VDP: SetVideoRender(vdpau) == GetVideoRenderer()
2010-06-25 06:57:57.273 VideoOutput: Pixel dimensions: Screen 1360x768, window 1360x768
2010-06-25 06:57:57.273 VideoOutput: Actual display dimensions: 345x195 mm  Aspect: 1.76923
2010-06-25 06:57:57.273 VideoOutput: Estimated window dimensions: 345x195 mm  Aspect: 1.76923
2010-06-25 06:57:57.434 VDPAU: Created 2 output surfaces.
2010-06-25 06:57:57.435 VDPAU: Set colorkey to 0x20202
2010-06-25 06:57:57.435 VDPAU: Created VDPAU render device 1360x768
2010-06-25 06:57:57.436 VidOutVDPAU: Created VDPAU osd (1360x768)
2010-06-25 06:57:57.457 VidOutVDPAU: PictureAttributes: Brightness, Contrast, Colour, Hue
2010-06-25 06:57:57.468 VidOutVDPAU: Using ITU BT.601 colorspace
2010-06-25 06:57:57.468 Display Rect  left: 0, top: 0, width: 1360, height: 768, aspect: 1.77778
2010-06-25 06:57:57.468 Video Rect    left: 0, top: 0, width: 704, height: 480, aspect: 1.77778
2010-06-25 06:57:57.468 VidOutVDPAU: Created VDPAU context (GPU decode)
2010-06-25 06:57:57.468 VDP: GetFilteredDeint() : vdpau -> 'vdpauadvanceddoublerate'
2010-06-25 06:57:57.469 VidOutVDPAU: Enabled deinterlacing.
2010-06-25 06:57:57.469 VDP: LoadBestPreferences(704x480, 29.97)
2010-06-25 06:57:57.489 NVP(0): Forcing decode extra audio option on (Video method requires it).
2010-06-25 06:57:57.489 NVP(0): ClearAfterSeek(1)
2010-06-25 06:57:57.491 VidOutVDPAU: ClearAfterSeek()
2010-06-25 06:57:57.491 VidOutVDPAU: DiscardFrames(0)
2010-06-25 06:57:57.491 VideoBuffers::DiscardFrames(0): AAAAAAAAAAAAAAAAA
2010-06-25 06:57:57.491 VideoBuffers::DiscardFrames(0): AAAAAAAAAAAAAAAAA -- done
2010-06-25 06:57:57.491 VidOutVDPAU: DiscardFrames() 3: AAAAAAAAAAAAAAAAA -- done()
2010-06-25 06:57:57.492 FilterManager: GetFilterInfo(convert) returning: 0x0
2010-06-25 06:57:57.492 NVP(0): LoadFilters('vdpaucolorspace=auto'..) -> 0x0
2010-06-25 06:57:57.492 detectInterlace(Detect Scan, Interlaced Scan, 29.97, 480) ->Interlaced Scan
2010-06-25 06:57:57.492 Set video sync frame interval to 33366
2010-06-25 06:57:57.492 Enabled deinterlacing
2010-06-25 06:57:57.492 AFD: EIA-708 caption service #1 is in the English language.
2010-06-25 06:57:57.492 AFD: Using vdpau for video decoding
2010-06-25 06:57:57.492 AFD: Looking for decoder for MPEG2VIDEO
2010-06-25 06:57:57.492 AFD: Opened codec 0x7f6e29018070, id(MPEG2VIDEO) type(Video)
2010-06-25 06:57:57.492 AFD: Stream #1, has id 0x44 codec id AC3, type Audio, bitrate 192000 at 0x7f6e288dfc40
2010-06-25 06:57:57.492 AFD: codec AC3 has 2 channels
2010-06-25 06:57:57.492 AFD: Looking for decoder for AC3
2010-06-25 06:57:57.493 AFD: Opened codec 0x7f6e29001f70, id(AC3) type(Audio)
2010-06-25 06:57:57.493 AFD: Stream #2, has id 0x45 codec id AC3, type Audio, bitrate 128000 at 0x7f6e280429a0
2010-06-25 06:57:57.493 AFD: codec AC3 has 2 channels
2010-06-25 06:57:57.493 AFD: Looking for decoder for AC3
2010-06-25 06:57:57.494 AFD: Opened codec 0x7f6e28fe2980, id(AC3) type(Audio)
2010-06-25 06:57:57.573 RingBuf(myth://192.168.25.252:6543/1352_20100625065754.mpg): CalcReadAheadThresh(0 KB)
			 -> threshhold(64 KB) min read(0 KB) blk size(32 KB)
2010-06-25 06:57:57.619 Opening audio device 'default'. ch 2(2) sr 48000 (reenc 1)
2010-06-25 06:57:57.620 Opening ALSA audio device 'default'.
2010-06-25 06:57:57.633 NVP(0): Enabling Audio
2010-06-25 06:57:57.669 Opening audio device 'default'. ch 2(2) sr 48000 (reenc 1)
2010-06-25 06:57:57.670 Opening ALSA audio device 'default'.
2010-06-25 06:57:57.673 Dec: Trying to select track (w/lang)
2010-06-25 06:57:57.673 Dec: Selecting first track
2010-06-25 06:57:57.673 Dec: Selected track #1 in the Unknown language(0)
2010-06-25 06:57:57.673 Dec: Selected track #1 in the English language(6647399)
2010-06-25 06:57:57.673 Dec: Resyncing position map. posmapStarted = 0 livetv(1) watchingRec(1)
2010-06-25 06:57:57.675 Position map filled from DB to: 15
2010-06-25 06:57:57.675 Dec: SyncPositionMap watchingrecording, from DB: 2 entries
2010-06-25 06:57:57.675 NVP(0): Filling position map from 16 to end
2010-06-25 06:57:57.686 Dec: Position map filled from Encoder to: 45
2010-06-25 06:57:57.687 Dec: SyncPositionMap watchingrecording total: 4 entries
2010-06-25 06:57:57.687 Dec: SyncPositionMap, new totframes: 45, new length: 1, posMap size: 4
2010-06-25 06:57:57.687 AFD: Partial position map found
2010-06-25 06:57:57.687 AFD: Successfully opened decoder for file: "myth://192.168.25.252:6543/1352_20100625065754.mpg". novideo(0)
2010-06-25 06:57:57.690 NVP(0): DoPlay() -- begin
2010-06-25 06:57:57.690 NVP(0): DoPlay: rate: 29.97 speed: 1 skip: 1 => new interval 33366
2010-06-25 06:57:57.691 Set video sync frame interval to 33366
2010-06-25 06:57:57.691 NVP(0): Stretch Factor 1, allow passthru 
2010-06-25 06:57:57.691 NVP(0): DoPlay() -- setting unpaused
2010-06-25 06:57:57.713 NVP(0): Waiting for prebuffer..  0 AAAAAAAAAAAAAAAAA
2010-06-25 06:57:57.863 NVP(0): Waiting for prebuffer..  1 AAAAAAAAAAAAAAAAA
2010-06-25 06:57:57.869 RingBuf(myth://192.168.25.252:6543/1352_20100625065754.mpg): CalcReadAheadThresh(0 KB)
			 -> threshhold(64 KB) min read(0 KB) blk size(32 KB)
2010-06-25 06:57:57.869 Dec: Resyncing position map. posmapStarted = 0 livetv(1) watchingRec(1)
2010-06-25 06:57:57.870 Position map filled from DB to: 15
2010-06-25 06:57:57.870 Dec: SyncPositionMap watchingrecording, from DB: 2 entries
2010-06-25 06:57:57.871 NVP(0): Filling position map from 16 to end
2010-06-25 06:57:57.899 Dec: Position map filled from Encoder to: 45
2010-06-25 06:57:57.899 Dec: SyncPositionMap watchingrecording total: 4 entries
2010-06-25 06:57:57.912 VidOutVDPAU: Created VDPAU decoder (2 ref frames)
2010-06-25 06:57:57.967 VDPAU: Added 2 output surfaces (total 4, max 4)
'video_output' mean = '34827.37', std. dev. = '7091.72', fps = '28.71'
2010-06-25 06:58:04.319 TV: SetActive(0,w/o OSD) 0 -> 0 -- begin
2010-06-25 06:58:04.319 TV: SetActive(0,w/o OSD) 0 -> 0 -- end
2010-06-25 06:58:04.359 TV: HandleStateChange(0) -- begin
2010-06-25 06:58:04.360 TV: Attempting to change from WatchingLiveTV to None
2010-06-25 06:58:04.360 TV: StopStuff() for player ctx 0 -- begin
2010-06-25 06:58:04.360 TV: SetActive(0,w/o OSD) 0 -> 0 -- begin
2010-06-25 06:58:04.360 TV: SetActive(0,w/o OSD) 0 -> 0 -- end
2010-06-25 06:58:04.360 TV: StopStuff(): stopping ring buffer
2010-06-25 06:58:04.361 NVP(0): Exited decoder loop.
2010-06-25 06:58:04.378 ~OpenGLVideoSync() -- closing opengl vsync
2010-06-25 06:58:04.379 GLCtx: Deleting OpenGL Resources
2010-06-25 06:58:04.379 GLCtx: Unmapping gl window
2010-06-25 06:58:04.380 GLCtx: Destroying gl window
2010-06-25 06:58:04.380 GLCtx: Destroying glx context
2010-06-25 06:58:04.391 GLCtx: Closing display
2010-06-25 06:58:04.392 VidOutVDPAU: DiscardFrames(1)
2010-06-25 06:58:04.392 VideoBuffers::DiscardFrames(1): DUUUUUUUUUUuAALDD
2010-06-25 06:58:04.393 VideoBuffers::DiscardFrames(): DAAAAAAAAAAAAAADD -- done()
2010-06-25 06:58:04.393 VideoBuffers::DiscardFrames(1): DAAAAAAAAAAAAAADD -- done
2010-06-25 06:58:04.393 VidOutVDPAU: DiscardFrames() 3: DAAAAAAAAAAAAAADD -- done()
2010-06-25 06:58:04.609 TV: StopStuff(): stopping player
2010-06-25 06:58:04.609 TV: StopStuff(): stopping recorder
2010-06-25 06:58:04.733 TV: StopStuff() -- end
2010-06-25 06:58:04.733 TV: Changing from WatchingLiveTV to None
2010-06-25 06:58:04.734 TV: HandleStateChange(0) -- end
2010-06-25 06:58:04.734 TV: StartTV -- process events end
2010-06-25 06:58:04.734 TV: StartTV -- process events 2 begin
2010-06-25 06:58:04.734 ScreenSaverX11Private: StopTimer
2010-06-25 06:58:04.737 TV: StartTV -- process events 2 end
2010-06-25 06:58:04.739 TV::~TV() -- begin
2010-06-25 06:58:04.800 TV::~TV() -- lock
2010-06-25 06:58:04.822 TV::~TV() -- end
2010-06-25 06:58:04.823 TV: StartTV -- end
2010-06-25 06:58:07.457 Deleting UPnP client...

```

---

### Post by jyavenard on 2010-06-25
First ...
> **uncle hammy said:**
> 
2010-06-25 06:57:55.648 VidOutVDPAU: Created VDPAU context (software decode)


then:

> 
2010-06-25 06:57:57.468 VidOutVDPAU: Created VDPAU context (GPU decode)


so it's using VDPAU for video decode in the 2nd instance...

You have a 8400M however, the decoding is mainly done in software by the drivers...
The 8400M didn't have full offloaded mpeg2 decoding: h264 only

---

### Post by My Name on 2010-06-25
> **jyavenard said:**
> First ...


then:



so it's using VDPAU for video decode in the 2nd instance...

You have a 8400M however, the decoding is mainly done in software by the drivers...
The 8400M didn't have full offloaded mpeg2 decoding: h264 only

You seem to be a bit of an expert at this so keep an eye on this thread please and I'll post my log later on this evening (GMT)):P

---

### Post by uncle hammy on 2010-06-25
> **jyavenard said:**
> First ...


then:



so it's using VDPAU for video decode in the 2nd instance...

You have a 8400M however, the decoding is mainly done in software by the drivers...
The 8400M didn't have full offloaded mpeg2 decoding: h264 only
I see.  So when I view an HD stream, say Chuck on NBC at 1080i, it is able to do full offload?  Because with those streams, I have very low CPU usage.

Also, I am not sure what you mean about the "2nd" instance, because this is from watching one show.  I hit "Live TV", and it was already tuned to the station.

---

### Post by My Name on 2010-06-25
wel  here is a chunk of my frontend log, let's see what you can meke of it
```

2010-06-25 20:23:29.018 [h264 @ 0x1088960]mmco: unref short failure
2010-06-25 20:23:29.415 VDPAU: Created 2 output surfaces.
2010-06-25 20:23:29.415 VDPAU: Created VDPAU render device 1360x768
2010-06-25 20:23:32.190 NVP(2): Forcing decode extra audio option on (Video method requires it).
2010-06-25 20:23:32.198 AFD: Opened codec 0xa7327260, id(H264) type(Video)
2010-06-25 20:23:32.198 AFD: codec MP2 has 2 channels
2010-06-25 20:23:32.199 AFD: Opened codec 0xa91f7600, id(MP2) type(Audio)
2010-06-25 20:23:32.251 Opening audio device 'default'. ch 2(2) sr 48000 (reenc 0)
2010-06-25 20:23:32.258 Opening ALSA audio device 'default'.
2010-06-25 20:23:32.358 NVP(2): Enabling Audio
2010-06-25 20:23:32.424 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.424 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.424 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.425 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.425 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.425 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.426 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.429 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.429 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.430 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.430 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.430 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.431 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.431 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.431 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.431 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.432 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.432 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.432 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.433 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.433 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.433 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.434 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.434 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.434 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.435 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.435 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.435 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.435 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.435 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.436 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.436 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.436 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.437 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.437 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.437 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.437 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.438 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.438 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.438 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.439 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.439 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.439 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.440 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.440 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.440 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.440 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.441 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.441 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.441 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.442 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.442 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.442 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.456 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.456 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.456 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.456 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.461 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.461 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.462 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.462 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.462 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.463 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.463 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.465 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.466 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.466 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.466 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.467 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.467 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.467 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.467 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.469 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.469 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.470 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.470 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.471 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.472 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.472 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.472 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.473 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.473 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.473 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.474 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.474 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.474 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.475 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.475 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.475 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.476 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.476 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.476 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.477 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.477 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.477 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.478 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.478 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.478 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.479 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.479 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.479 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.480 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.480 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.481 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.481 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.482 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.482 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.482 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.483 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.483 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.483 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.484 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.484 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.484 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.484 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.485 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.485 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.485 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.485 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.486 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.486 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.486 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.486 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.487 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.487 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.487 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.490 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.490 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.491 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.491 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.491 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.492 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.493 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.494 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.494 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.494 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.495 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.495 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.495 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.495 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.496 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.500 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.501 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.501 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.501 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.501 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.502 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.502 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.508 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.508 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.509 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.509 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.509 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.510 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.510 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.511 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.511 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.512 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.513 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.514 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.514 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.514 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.515 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.515 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.515 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.515 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.516 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.516 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.516 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.517 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.517 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.517 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.518 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.518 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.518 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.518 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.519 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.519 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.519 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.519 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.520 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.520 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.520 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.521 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.523 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.523 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.524 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.524 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.524 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.525 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.525 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.527 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.528 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.528 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.528 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.528 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.529 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.529 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.530 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.531 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.531 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.532 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.532 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.532 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.532 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.533 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.533 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.533 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.534 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.534 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.534 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.535 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.535 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.535 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.535 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.536 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.536 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.536 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.537 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.537 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.537 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.538 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.538 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.538 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.539 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.539 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.539 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.540 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.540 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.540 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.555 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.555 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.556 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.556 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.556 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.556 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.557 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.566 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.566 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.566 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.567 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.567 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.567 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.570 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.570 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.571 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.571 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.571 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.574 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.574 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.575 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.577 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.577 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.577 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.578 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.578 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.579 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.580 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.580 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.580 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.581 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.581 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.581 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.581 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.582 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.582 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.582 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.583 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.585 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.586 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.586 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.586 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.586 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.587 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.587 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.587 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.588 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.588 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.588 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.589 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.589 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.589 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.589 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.590 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.604 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.604 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.605 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.605 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.611 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.612 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.612 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.612 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.612 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.613 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.618 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.621 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.621 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.622 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.622 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.622 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.622 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.623 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.624 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.624 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.624 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.625 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.627 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.629 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.629 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.630 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.630 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.630 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.631 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.632 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.632 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.633 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.633 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.633 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.634 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.634 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.634 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.634 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.635 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.635 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.635 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.636 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.636 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.636 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.637 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.637 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.637 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.637 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.638 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.638 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.639 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.639 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.639 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.639 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.640 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.640 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.641 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.641 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.641 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.642 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.654 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.654 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.654 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.655 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.660 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.660 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.660 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.660 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.661 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.661 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.661 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.664 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.665 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.665 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.666 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.666 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.667 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.667 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.667 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.667 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.668 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.670 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.671 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.671 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.671 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.672 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.672 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.672 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.672 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.673 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.673 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.673 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.674 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.674 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.674 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.675 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.675 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.675 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.676 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.676 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.676 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.676 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.677 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.677 [h264_vdpau @ 0x1088960]number of reference frames exceeds max (probably corrupt input), discarding one
2010-06-25 20:23:32.677 [h264_vdpau @ 0x1088960]mmco: unref short failure
2010-06-25 20:23:33.479 [h264_vdpau @ 0x1088960]mmco: unref short failure
2010-06-25 20:23:33.497 VDPAU: Added 2 output surfaces (total 4, max 4)
2010-06-25 20:23:33.518 NVP(2): prebuffering pause
2010-06-25 20:23:33.521 [h264_vdpau @ 0x1088960]mmco: unref short failure
2010-06-25 20:23:33.617 NVP(2): prebuffering pause
2010-06-25 20:24:13.840 [h264_vdpau @ 0x1088960]illegal short term buffer state detected

```

sorry it's big i know...

---

### Post by jyavenard on 2010-06-26
The logs are rather obvious. 

Too many reference frames. VDPAU only support some h264 profiles. Re-encode the video with different providers

---

### Post by My Name on 2010-06-26
Could you put that in layman's terms...

---

