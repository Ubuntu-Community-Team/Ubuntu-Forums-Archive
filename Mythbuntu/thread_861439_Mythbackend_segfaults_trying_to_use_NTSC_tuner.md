---
title: "Mythbackend segfaults trying to use NTSC tuner"
date: 2008-07-16
forum: Mythbuntu
---

### Post by theophile on 2008-07-16
I have a pchdtv hd-3000 card and I'm trying to configure it to receive standard definition channels from the cable box over s-video, in addition to the firewire source I am using for HD content. I have made the connections and I can watch TV flawlessly using tvtime and VLC. Problem is, I can't get it to capture in Myth.

I set up the tuner as an analog tuner using V4L and default settings. I created a source for analog channels and assigned it to the s-video input. I added a channel for it. 

I can watch and record the firewire source just fine. But whenever I try to watch or record from the s-video input, the backend unceremoniously segfaults. Here are the relevant sections from the logs.

Keep in mind that while the frontend logs have errors about the display, the backend segfaults even if I try merely to record the channel and not watch it.

This is what appears on the console where mythbackend was running, immediately after the successful exit of the channel-changer script:

```
2008-07-12 11:23:25.627 ret_pid(11528) child(11528) status(0x0)
2008-07-12 11:23:25.627 External Tuning program exited with no error
2008-07-12 11:23:26.841 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
Segmentation fault
```

This is what is shown by the frontend as run in terminal:

```
2008-07-12 11:23:21.386 TV: CommitQueuedInput() livetv(1) qchannum(54) qchanid(1054)
2008-07-12 11:23:21.386 TV: ChangeChannel(1054, '54') 
2008-07-12 11:23:21.395 TV: SwitchCards(1054,'54',0)
2008-07-12 11:23:21.399 NVP: Changing speed to 0
2008-07-12 11:23:21.399 rate: 29.97 speed: 1 skip: 1 = interval 33366
2008-07-12 11:23:21.400 Set video sync frame interval to 33366
2008-07-12 11:23:21.434 NVP: Exited decoder loop.
2008-07-12 11:23:21.526 VideoOutputXv: dtor
2008-07-12 11:23:21.527 VideoOutputXv: DiscardFrames(1)
2008-07-12 11:23:21.527 VideoBuffers::DiscardFrames(1): UUUUUUUUUUUUUuUULUUUAUUUUUUUUUU
2008-07-12 11:23:21.527 VideoBuffers::DiscardFrames(): AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA -- done()
2008-07-12 11:23:21.527 VideoBuffers::DiscardFrames(1): AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA -- done
2008-07-12 11:23:21.527 VideoOutputXv: DiscardFrames() 3: AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA -- done()
2008-07-12 11:23:21.528 VideoOutputXv: DiscardFrames(1)
2008-07-12 11:23:21.528 VideoBuffers::DiscardFrames(1): AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
2008-07-12 11:23:21.528 VideoBuffers::DiscardFrames(): AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA -- done()
2008-07-12 11:23:21.528 VideoBuffers::DiscardFrames(1): AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA -- done
2008-07-12 11:23:21.528 VideoOutputXv: DiscardFrames() 3: AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA -- done()
2008-07-12 11:23:21.536 VideoOutputXv: Closing XVideo port 245
2008-07-12 11:23:21.594 Using protocol version 40
2008-07-12 11:23:26.837 LiveTVChain(live-farmer-2008-07-12T11:23:06): ReloadAll(): Added new recording
2008-07-12 11:23:26.854 RingBuf(/mnt/store/1054_20080712112325.nuv): OpenFile(/mnt/store/1054_20080712112325.nuv, 12)
2008-07-12 11:23:26.855 RingBuf(/mnt/store/1054_20080712112325.nuv): CalcReadAheadThresh(3061159504 KB)
			 -> threshhold(64 KB) min read(0 KB) blk size(32 KB)
2008-07-12 11:23:26.901 TV: StartRecorder(): took 46 ms to start recorder.
2008-07-12 11:23:27.067 detectInterlace(Ignore Scan, Interlaced Scan, 29.97, 1088) ->Interlaced Scan
2008-07-12 11:23:27.073 Opening audio device 'NULL'. ch 6(2) sr 48000
2008-07-12 11:23:27.073 Opening NULL audio device.
2008-07-12 11:23:27.081 Opening audio device 'NULL'. ch 6(2) sr 48000
2008-07-12 11:23:27.081 Opening NULL audio device.
2008-07-12 11:23:27.091 Event socket closed. No connection to the backend.
2008-07-12 11:23:46.947 TV: StartPlayer(): took 20000 ms to start player.
2008-07-12 11:23:46.947 TV Error: StartPlayer(): NVP is not playing after 20000 msec
2008-07-12 11:23:46.947 TV: StopStuff() -- begin
2008-07-12 11:23:46.947 TV: StopStuff(): stopping ring buffer[s]
2008-07-12 11:23:46.947 RingBuf(/mnt/store/1054_20080712112325.nuv): CalcReadAheadThresh(3085926740 KB)
			 -> threshhold(64 KB) min read(0 KB) blk size(32 KB)
2008-07-12 11:23:46.948 Resyncing position map. posmapStarted = 0 livetv(1) watchingRec(0)
2008-07-12 11:23:46.949 SyncPositionMap watchingrecording, from DB: 0 entries
2008-07-12 11:23:46.950 TV: StopStuff(): stopping player[s] (1/2)
2008-07-12 11:23:46.950 TV: StopStuff(): stopping recorder[s]
2008-07-12 11:23:46.951 MythSocket(af0a9220:-1): writeStringList: Error, socket went unconnected.
2008-07-12 11:23:46.951 MythSocket(af0a9220:-1): readStringList: Error, called with unconnected socket.
2008-07-12 11:23:46.951 RemoteEncoder::SendReceiveStringList(): No response.
2008-07-12 11:23:46.951 decodeLongLong() called with offset >= list size.
2008-07-12 11:23:46.951 PosMapFromEnc: Warning, tried to fetch PositionMap from Encoder but encoder returned framesWritten == 0
2008-07-12 11:23:46.951 SyncPositionMap watchingrecording no entries from encoder, try DB
2008-07-12 11:23:46.952 SyncPositionMap watchingrecording total: 0 entries
2008-07-12 11:23:46.953 MythSocket(af0a9220:-1): writeStringList: Error, called with unconnected socket.
2008-07-12 11:23:46.954 MythSocket(af0a9220:-1): readStringList: Error, called with unconnected socket.
2008-07-12 11:23:46.954 RemoteEncoder::SendReceiveStringList(): No response.
2008-07-12 11:23:46.954 TV: StopStuff(): stopping player[s] (2/2)
2008-07-12 11:23:46.955 Opening audio device 'NULL'. ch 6(2) sr 48000
2008-07-12 11:23:46.955 Opening NULL audio device.
2008-07-12 11:23:46.960 VideoOutput: Allowed renderers: xv-blit,xshm,opengl,xlib
2008-07-12 11:23:46.961 VideoOutput: Allowed renderers (filt: nuppel): xlib,xshm,xv-blit,opengl
2008-07-12 11:23:46.965 VDP: Accepting: cmp(>= 1280 720) dec(ffmpeg) cpus(1) rend(xv-blit) osd(softblend) osdfade(disabled) deint(linearblend,linearblend) filt()
2008-07-12 11:23:46.965 VDP: Accepting: cmp(> 0 0) dec(ffmpeg) cpus(1) rend(xv-blit) osd(softblend) osdfade(enabled) deint(greedyhdoubleprocessdeint,kerneldeint) filt()
2008-07-12 11:23:46.965 VDP: Accepting: cmp(>= 1280 720) dec(ffmpeg) cpus(1) rend(quartz-blit) osd(softblend) osdfade(disabled) deint(linearblend,linearblend) filt()
2008-07-12 11:23:46.966 VDP: Accepting: cmp(> 0 0) dec(ffmpeg) cpus(1) rend(quartz-blit) osd(softblend) osdfade(enabled) deint(greedyhdoubleprocessdeint,kerneldeint) filt()
2008-07-12 11:23:46.966 VDP: LoadBestPreferences(2048x2048, 0)
2008-07-12 11:23:46.966 VDP: LoadBestPreferences(2048x2048, 60)
2008-07-12 11:23:46.966 VDP: LoadBestPreferences(1920x1088, 60)
2008-07-12 11:23:46.966 VideoOutput: Preferred renderer: xv-blit
2008-07-12 11:23:46.967 VideoOutput: Trying video renderer: xv-blit
2008-07-12 11:23:46.969 VDP: Accepting: cmp(>= 1280 720) dec(ffmpeg) cpus(1) rend(xv-blit) osd(softblend) osdfade(disabled) deint(linearblend,linearblend) filt()
2008-07-12 11:23:46.970 VDP: Accepting: cmp(> 0 0) dec(ffmpeg) cpus(1) rend(xv-blit) osd(softblend) osdfade(enabled) deint(greedyhdoubleprocessdeint,kerneldeint) filt()
2008-07-12 11:23:46.970 VDP: Accepting: cmp(>= 1280 720) dec(ffmpeg) cpus(1) rend(quartz-blit) osd(softblend) osdfade(disabled) deint(linearblend,linearblend) filt()
2008-07-12 11:23:46.970 VDP: Accepting: cmp(> 0 0) dec(ffmpeg) cpus(1) rend(quartz-blit) osd(softblend) osdfade(enabled) deint(greedyhdoubleprocessdeint,kerneldeint) filt()
2008-07-12 11:23:46.971 VDP: LoadBestPreferences(2048x2048, 0)
2008-07-12 11:23:46.971 VDP: LoadBestPreferences(2048x2048, 60)
2008-07-12 11:23:46.996 VideoOutputXv: ctor
2008-07-12 11:23:46.999 XOff: 0, YOff: 0
2008-07-12 11:23:46.999 VDP: LoadBestPreferences(1920x1088, 60)
2008-07-12 11:23:46.999 Display Rect  left: 0, top: 0, width: 1360, height: 768, aspect: 1.33333
2008-07-12 11:23:46.999 Video Rect    left: 0, top: 0, width: 1920, height: 1080, aspect: 1.33333
2008-07-12 11:23:47.007 VideoOutputXv: Pixel dimensions: Screen 1360x768, window 1360x768
2008-07-12 11:23:47.008 VideoOutputXv: Estimated display dimensions: 345x195 mm  Aspect: 1.76923
2008-07-12 11:23:47.008 VideoOutputXv: Estimated window dimensions: 345x195 mm  Aspect: 1.76923
2008-07-12 11:23:47.009 VideoOutputXv: InitSetupBuffers() render: xv-blit, allowed: xv-blit,xshm,opengl,xlib
2008-07-12 11:23:47.012 VDP: Accepting: cmp(>= 1280 720) dec(ffmpeg) cpus(1) rend(xv-blit) osd(softblend) osdfade(disabled) deint(linearblend,linearblend) filt()
2008-07-12 11:23:47.013 VDP: Accepting: cmp(> 0 0) dec(ffmpeg) cpus(1) rend(xv-blit) osd(softblend) osdfade(enabled) deint(greedyhdoubleprocessdeint,kerneldeint) filt()
2008-07-12 11:23:47.013 VDP: Accepting: cmp(>= 1280 720) dec(ffmpeg) cpus(1) rend(quartz-blit) osd(softblend) osdfade(disabled) deint(linearblend,linearblend) filt()
2008-07-12 11:23:47.013 VDP: Accepting: cmp(> 0 0) dec(ffmpeg) cpus(1) rend(quartz-blit) osd(softblend) osdfade(enabled) deint(greedyhdoubleprocessdeint,kerneldeint) filt()
2008-07-12 11:23:47.013 VDP: LoadBestPreferences(2048x2048, 0)
2008-07-12 11:23:47.013 VDP: LoadBestPreferences(2048x2048, 60)
2008-07-12 11:23:47.014 VDP: LoadBestPreferences(1920x1088, 60)
2008-07-12 11:23:47.014 VideoOutputXv: @ j=0 Looking for flag[s]: XvInputMask XvImageMask  10
2008-07-12 11:23:47.014 VideoOutputXv: Adaptor#0: NV17 Video Overlay has flag[s]: XvInputMask XvImageMask 
2008-07-12 11:23:47.014 VideoOutputXv: Has XVideo flags...
2008-07-12 11:23:47.015 VideoOutputXv: Has XV_BRIGHTNESS...
2008-07-12 11:23:47.015 VideoOutputXv: Here...
2008-07-12 11:23:47.015 VideoOutputXv: Grabbed xv port 245
2008-07-12 11:23:47.015 VideoOutputXv: XVideo surface found on port 245
2008-07-12 11:23:47.015 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Overlay'
2008-07-12 11:23:47.016 VideoOutputXv: XVideo Format #0 is 'YUY2'
2008-07-12 11:23:47.016 VideoOutputXv: XVideo Format #1 is 'YV12'
2008-07-12 11:23:47.016 VideoOutputXv: XVideo Format #2 is 'UYVY'
2008-07-12 11:23:47.016 VideoOutputXv: XVideo Format #3 is 'I420'
2008-07-12 11:23:47.016 VideoOutputXv: Using XVideo Format 'YV12'
2008-07-12 11:23:47.016 VideoOutputXv: CreateShmImages(32): video_dim: 1920x1088
2008-07-12 11:23:47.244 VDP: SetVideoRenderer(xv-blit)
2008-07-12 11:23:47.245 VDP: SetVideoRender(xv-blit) == GetVideoRenderer()
2008-07-12 11:23:47.246 Display Rect  left: 170, top: 0, width: 1020, height: 768, aspect: 1.77778
2008-07-12 11:23:47.246 Video Rect    left: 0, top: 0, width: 1920, height: 1080, aspect: 1.33333
2008-07-12 11:23:47.250 Over/underscan. V: 0.02, H: 0.02
2008-07-12 11:23:47.251 Display Rect  left: 170, top: 0, width: 1020, height: 768, aspect: 1.77778
2008-07-12 11:23:47.251 Video Rect    left: 38, top: 22, width: 1843, height: 1037, aspect: 1.33333
2008-07-12 11:23:47.251 VDP: LoadBestPreferences(1920x1088, 29.97)
2008-07-12 11:23:47.254 NVP: LoadFilters(''..) -> 0
2008-07-12 11:23:47.258 OSD Theme Dimensions W: 640 H: 480
2008-07-12 11:23:47.733 NVP: ClearAfterSeek(1)
2008-07-12 11:23:47.733 VideoOutputXv: ClearAfterSeek()
2008-07-12 11:23:47.734 VideoOutputXv: DiscardFrames(0)
2008-07-12 11:23:47.734 VideoBuffers::DiscardFrames(0): AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
2008-07-12 11:23:47.734 VideoBuffers::DiscardFrames(0): AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA -- done
2008-07-12 11:23:47.734 VideoOutputXv: DiscardFrames() 3: AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA -- done()
2008-07-12 11:23:47.736 VDP: GetFilteredDeint() : xv-blit -> 'linearblend'
2008-07-12 11:23:47.738 Using deinterlace method linearblend
2008-07-12 11:23:47.741 The realtime priority setting is not enabled.
2008-07-12 11:23:47.743 NVP: Exited decoder loop.
2008-07-12 11:23:47.836 nVidiaVideoSync: VBlank ioctl did not work, unimplemented in this driver?
2008-07-12 11:23:47.836 DRMVideoSync: Could not open device /dev/dri/card0, No such file or directory
2008-07-12 11:23:47.836 Using audio as timebase
2008-07-12 11:23:47.836 Video timing method: RTC
2008-07-12 11:23:47.837 Refresh rate: 16683, frame interval: 33366
2008-07-12 11:23:47.837 VideoOutputXv: dtor
2008-07-12 11:23:47.837 VideoOutputXv: DiscardFrames(1)
2008-07-12 11:23:47.837 VideoBuffers::DiscardFrames(1): AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
2008-07-12 11:23:47.837 VideoBuffers::DiscardFrames(): AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA -- done()
2008-07-12 11:23:47.837 VideoBuffers::DiscardFrames(1): AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA -- done
2008-07-12 11:23:47.837 VideoOutputXv: DiscardFrames() 3: AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA -- done()
2008-07-12 11:23:47.838 VideoOutputXv: DiscardFrames(1)
2008-07-12 11:23:47.838 VideoBuffers::DiscardFrames(1): AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
2008-07-12 11:23:47.838 VideoBuffers::DiscardFrames(): AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA -- done()
2008-07-12 11:23:47.838 VideoBuffers::DiscardFrames(1): AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA -- done
2008-07-12 11:23:47.838 VideoOutputXv: DiscardFrames() 3: AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA -- done()
2008-07-12 11:23:47.843 VideoOutputXv: Closing XVideo port 245
2008-07-12 11:23:47.868 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-07-12 11:23:47.869 Connection timed out.          
			You probably should modify the Master Server 
			settings in the setup program and set the    
			proper IP address.
```

This is what appears in dmesg:

```
[ 1254.122742] mythbackend[11575]: segfault at ad704000 eip b7c2a036 esp aca03a80 error 4
```

According to this

[http://www.mythtv.org/wiki/index.php/PcHDTV_HD-3000](http://www.mythtv.org/wiki/index.php/PcHDTV_HD-3000)

I should be able to add this card as a DVB card and there will be an option to set up the analog features. Is this true in 0.21? Because I can't find it anywhere. 

I've also been able to watch the s-video input from VLC so I know the hardware and drivers are OK.

Also, I set a program on the s-video sourced channel to record and fan the backend a few times, each time it segfaulted at startup when beginning the recording. THis process created severl smal .nuv files:

```
-rw-r--r-- 1 root   root   17040 2008-07-12 18:27 1054_20080712182700.nuv
-rw-r--r-- 1 mythtv mythtv  8824 2008-07-12 18:30 1054_20080712183000.nuv
-rw-r--r-- 1 root   root   12932 2008-07-12 18:30 1054_20080712183001.nuv
-rw-r--r-- 1 mythtv mythtv  8824 2008-07-12 18:32 1054_20080712183300.nuv
-rw-r--r-- 1 root   root    8824 2008-07-12 18:32 1054_20080712183301.nuv
-rw-r--r-- 1 root   root     608 2008-07-12 18:36 1054_20080712183700.nuv
-rw-r--r-- 1 root   root     608 2008-07-12 18:37 1054_20080712183800.nuv
```

Again, I don't know what this means.

On the hunch that maybe there was a sound capture problem, I set the audio device to /dev/null. It still segfaulted.

I am baffled here.

---

### Post by theophile on 2008-07-16
Sorry, this is on Mythbuntu 8.04, and:
```
mythtv-common:
  Installed: 0.21.0+fixes16838-0ubuntu3.1
  Candidate: 0.21.0+fixes17490-0ubuntu0+mythbuntu2
  Version table:
     0.21.0+fixes17490-0ubuntu0+mythbuntu2 0
        500 http://weeklybuilds.mythbuntu.org hardy/main Packages
 *** 0.21.0+fixes16838-0ubuntu3.1 0
        500 http://archive.ubuntu.com hardy-updates/multiverse Packages
        100 /var/lib/dpkg/status
     0.21.0+fixes16838-0ubuntu3 0
        500 http://archive.ubuntu.com hardy/multiverse Packages

```

---

