---
title: "MythTV &quot;Error was encountered while displaying video&quot;"
date: 2008-04-01
forum: Multimedia &amp; Video
---

### Post by Mohonri on 2008-04-01
I'm slogging through setting up MythTV.  My latest problem is this:  When attempting to watch live TV in the frontend, nothing happens for a few seconds, and then I get an error:

"Error was encountered while displaying video"

No other details.  I dug around a bit, found the log, and here is what looks like the pertinent part:
```
2008-04-01 20:33:27.983 TV: Attempting to change from None to WatchingLiveTV
2008-04-01 20:33:27.984 Using protocol version 31
2008-04-01 20:33:28.106 DPMS Deactivated 
2008-04-01 20:33:28.139 NVP: Disabling Audio, params(-1,2,44100)
2008-04-01 20:33:28.169 VideoOutputXv: XvMCTex: Init failed
2008-04-01 20:33:28.170 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  141
  Minor opcode:  14
  Resource id:  0x1eb
2008-04-01 20:33:28.663 TV: Changing from None to WatchingLiveTV
2008-04-01 20:33:28.683 Realtime priority would require SUID as root.
2008-04-01 20:33:28.781 Video timing method: USleep with busy wait
2008-04-01 20:33:31.530 NVP: Prebuffer wait timed out 10 times.
2008-04-01 20:33:31.839 RingBuf(/media/disk/recordings/1903_20080401203329.mpg): Waited 2.0 seconds for data to become available...
2008-04-01 20:33:31.840 Checking to see if there's a new livetv program to switch to..
2008-04-01 20:33:32.848 RingBuf(/media/disk/recordings/1903_20080401203329.mpg): Timing out wait due to impending livetv switch.
mpegts_read_header: unable to read first 1024 bytes
2008-04-01 20:33:32.848 AFD Error: avformat err(-1) on av_open_input_file call.
2008-04-01 20:33:32.848 Couldn't open decoder for: /media/disk/recordings/1903_20080401203329.mpg
2008-04-01 20:33:32.849 NVP, Error: JumpToProgram failed.
2008-04-01 20:33:32.851 TV: Attempting to change from WatchingLiveTV to None
2008-04-01 20:33:33.503 NVP: Prebuffer wait timed out 10 times.
2008-04-01 20:33:33.544 Opening ALSA audio device 'default'.
2008-04-01 20:33:33.558 mixer set channel 0 err -22: Invalid argument
2008-04-01 20:33:33.558 mixer unable to find control Master 1
2008-04-01 20:33:33.561 NVP: Enabling Audio
2008-04-01 20:33:33.761 NVP, Error: JumpToProgram failed.
2008-04-01 20:33:33.761 NVP, Error: Unknown error, exiting decoder
2008-04-01 20:36:50.430 TV: Changing from WatchingLiveTV to None
```

At one point, I was able to pick up and watch TV, but that was over a week ago, and I've made countless changes since then, so I can't pin it to one thing.  As far as hardware goes, I have a Dvico Fusion HDTV 5 RT Lite and a GeForce 6200 using the proprietary nvidia driver.  My first inclination is to blame it on my xorg.conf, which I've modified to get TV Out.  Here is the section I have modified:
```
Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       30.0 - 65.0
    VertRefresh     60
#    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "nVidia Corporation NV44A [GeForce 6200]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation NV44A [GeForce 6200]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "TwinView"
#    Option	   "TwinViewOrientation" "Clone"
    Option         "TVOutFormat" "SVIDEO"
    Option         "TVStandard" "NTSC-M"
    Option         "MetaModes" "1024x768,640x480; 800x600,640x480; 640x480,640x480"
    Option         "AddARGBVisuals" "True"
    Option         "AddARGBGLXVisuals" "True"
    Option         "NoLogo" "True"
    SubSection     "Display"
        Depth       24
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
EndSection
```I'm a bit of a novice at hacking xorg.conf, so chances are pretty good I've loused something up.  Can anyone help me out?

---

### Post by the[V]oid on 2008-04-28
Hi, I'm having a comparable problem. Have you solved this or come any further?

---

