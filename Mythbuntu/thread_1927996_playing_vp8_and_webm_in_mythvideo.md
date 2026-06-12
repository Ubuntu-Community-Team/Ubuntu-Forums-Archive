---
title: "playing vp8 and webm in mythvideo"
date: 2012-02-19
forum: Mythbuntu
---

### Post by weiser on 2012-02-19
Hi,
I have tried to get trailers playback to work under mythvideo, but I can't get my client to play webm files, vlc and mplayer is playing them fine. It complains about decoder as shown in the log, anybody have any ideas?


I have mythbuntu 10.04 but with upgraded mythtv as server:

MythTV Version   : v0.24.2-14-g9743d9c
MythTV Branch    : fixes/0.24
Network Protocol : 63
Library API      : 0.24.20110505-1
QT Version       : 4.6.2
Options compiled in:
 linux profile using_alsa using_oss using_pulse using_pulseoutput using_backend using_bindings_perl using_bindings_python using_crystalhd using_directfb using_dvb using_firewire using_frontend using_hdhomerun using_hdpvr using_iptv using_ivtv using_joystick_menu using_lirc using_mheg using_opengl_video using_opengl_vsync using_qtdbus using_qtwebkit using_v4l using_x11 using_xrandr using_xv using_bindings_perl using_bindings_python using_mythtranscode using_opengl using_vdpau using_ffmpeg_threads using_live using_mheg


and a client on kubuntu 11.10 with:

MythTV Version   : v0.24.1-80-g1de0431
MythTV Branch    : fixes/0.24
Network Protocol : 63
Library API      : 0.24.20110505-1
QT Version       : 4.7.3
Options compiled in:
 linux profile using_alsa using_oss using_pulse using_pulseoutput using_backend using_bindings_perl using_bindings_python using_dvb using_firewire using_frontend using_hdhomerun using_hdpvr using_iptv using_ivtv using_joystick_menu using_lirc using_mheg using_opengl_video using_opengl_vsync using_qtdbus using_qtwebkit using_v4l using_x11 using_xrandr using_xv using_bindings_perl using_bindings_python using_mythtranscode using_opengl using_vdpau using_ffmpeg_threads using_live using_mheg
 

And here is the log from mythfrontend:

2012-02-19 13:39:49.570 TV: StartTV() -- begin
2012-02-19 13:39:49.571 TV: ctor -- begin
2012-02-19 13:39:49.585 TV: ctor -- end
2012-02-19 13:39:49.585 TV: Init -- begin
2012-02-19 13:39:49.616 TV: DrawUnusedRects() -- begin
2012-02-19 13:39:49.616 TV: DrawUnusedRects() -- end
2012-02-19 13:39:49.618 TV: DrawUnusedRects() -- begin
2012-02-19 13:39:49.618 TV: DrawUnusedRects() -- end
2012-02-19 13:39:49.634 TV: DrawUnusedRects() -- begin
2012-02-19 13:39:49.634 TV: DrawUnusedRects() -- end
2012-02-19 13:39:49.637 TV: Init -- end
2012-02-19 13:39:49.639 TV: tv->Playback() -- begin
2012-02-19 13:39:49.658 TV: HandleStateChange(0) -- begin
2012-02-19 13:39:49.658 TV: Attempting to change from None to WatchingVideo
2012-02-19 13:39:49.658 RingBuf(myth://Videos@mythtv:6543/film/459ajX4zn_E.webm): OpenFile(myth://Videos@mythtv:6543/film/459ajX4zn_E.webm, 2000 ms)
2012-02-19 13:39:49.733 TV: StartPlayer(0, WatchingVideo, main) -- begin
2012-02-19 13:39:49.733 TV: Elapsed time since TV constructor was called: 162 ms
2012-02-19 13:39:51.125 RingBuf(myth://Videos@mythtv:6543/film/459ajX4zn_E.webm) Warning: Taking too long to be allowed to read..
2012-02-19 13:39:52.126 RingBuf(myth://Videos@mythtv:6543/film/459ajX4zn_E.webm) Warning: Taking too long to be allowed to read..
2012-02-19 13:39:52.609 RingBuf(myth://Videos@mythtv:6543/film/459ajX4zn_E.webm) Warning: Taking too long to be allowed to read..
2012-02-19 13:39:52.651 AFD: Stream #0, has id 0x0 codec id VP8, type Video, bitrate 0 at 0x7f37006c5cf0
2012-02-19 13:39:52.694 VDP: Ignoring profile item 113 (decoder xvmc is not supported (supported: ffmpeg,vdpau,libmpeg2))
2012-02-19 13:39:52.695 VDP: Ignoring profile item 115 (decoder xvmc is not supported (supported: ffmpeg,vdpau,libmpeg2))
2012-02-19 13:39:52.695 VDP: Accepting: cmp(<= 720 576,> 0 0) dec(ffmpeg) cpus(1) skiploop(enabled) rend(xv-blit) osd(softblend) osdfade(enabled) deint(bobdeint,linearblend) filt()
2012-02-19 13:39:52.695 VDP: Accepting: cmp(<= 1280 720,> 720 576) dec(libmpeg2) cpus(1) skiploop(enabled) rend(xv-blit) osd(softblend) osdfade(enabled) deint(bobdeint,onefield) filt()
2012-02-19 13:39:52.695 VDP: Accepting: cmp(> 0 0) dec(libmpeg2) cpus(1) skiploop(enabled) rend(xv-blit) osd(chromakey) osdfade(disabled) deint(bobdeint,onefield) filt()
2012-02-19 13:39:52.695 VDP: LoadBestPreferences(2048x2048, 0)
2012-02-19 13:39:52.695 VDP: LoadBestPreferences(2048x2048, 60)
2012-02-19 13:39:52.696 VDP: LoadBestPreferences(640x356, 60)
2012-02-19 13:39:52.696 AFD: Using 1 CPUs for decoding
2012-02-19 13:39:52.696 AFD: InitVideoCodec() 0x7f37006c5f10 id(VP8) type (Video).
2012-02-19 13:39:52.696 AFD: Selected FPS is 25 (avg 25 stream 25 container 1000 estimated 25)
2012-02-19 13:39:52.696 Player(0): detectInterlace(Detect Scan, Interlaced Scan, 25, 356) ->Interlaced Scan
2012-02-19 13:39:52.696 AFD Warning: ScanATSCCaptionStreams() called with no PMT
2012-02-19 13:39:52.696 AFD: Using ffmpeg for video decoding
2012-02-19 13:39:52.696 AFD: Looking for decoder for VP8
2012-02-19 13:39:52.697 [vp8 @ 0x7f37206ea700]Edge emulation not supported
2012-02-19 13:39:52.697 AFD Error: Could not open codec 0x7f37006c5f10, id(VP8) type(Video) aborting. reason -1163346256
2012-02-19 13:39:52.697 Couldn't open decoder for: myth://Videos@mythtv:6543/film/459ajX4zn_E.webm
2012-02-19 13:39:52.697 Unable to open video file.
2012-02-19 13:40:12.744 playCtx, Error: StartPlaying() Failed to start player
2012-02-19 13:40:12.744 Player(0): StopPlaying - begin
2012-02-19 13:40:12.744 Player(0): Exited decoder loop.
2012-02-19 13:40:12.745 Player(0): StopPlaying - end
2012-02-19 13:40:12.745 TV: StartPlayer(0, WatchingVideo, main) -- end error

Thanks.

---

