---
title: "Audio problems with 8.10 and PVR-250"
date: 2008-12-29
forum: Mythbuntu
---

### Post by siersmak on 2008-12-29
I'm new to mythbuntu, and everything seems to be working very well except that I've been fighting with getting the audio to work on my PVR-250.  The sound card works fine- I hear the Ubuntu drums when my X server restarts.  And, mythtv plays the audio from online streams.  But it does not properly record the audio or play audio when I'm watching live tv.  Actually, perhaps 1 out of 20 times the audio works fine. The other 19 times it either has no audio or all I hear is a high pitched buzzing sound.

Here are some logs and outputs:

mythbackend.log:
```
2008-12-29 23:42:59.454 MainServer::HandleAnnounce Monitor
2008-12-29 23:42:59.457 adding: vcrkiller as a client (events: 0)
2008-12-29 23:42:59.459 MainServer::HandleAnnounce Monitor
2008-12-29 23:42:59.460 adding: vcrkiller as a client (events: 1)
2008-12-29 23:42:59.471 MainServer::HandleAnnounce Playback
2008-12-29 23:42:59.477 adding: vcrkiller as a client (events: 0)
2008-12-29 23:42:59.481 TVRec(1): Changing from None to WatchingLiveTV
2008-12-29 23:42:59.487 TVRec(1): HW Tuner: 1->1
2008-12-29 23:43:00.579 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2008-12-29 23:43:00.584 MPEGRec(/dev/video0) Warning: Audio sample rate 32000 Hz
			is not supported by ivtv driver, using 48000 Hz instead.
2008-12-29 23:43:07.833 TVRec(1): Changing from WatchingLiveTV to None
2008-12-29 23:43:08.013 Finished recording Unknown: channel 2002
2008-12-29 23:44:05.937 Expiring 5 MBytes for 2002 @ Mon Dec 29 23:42:15 2008 => Unknown
2008-12-29 23:44:05.943 Expiring 4 MBytes for 2002 @ Mon Dec 29 23:42:59 2008 => Unknown
2008-12-29 23:45:18.257 MainServer::HandleAnnounce Monitor
2008-12-29 23:45:18.261 adding: vcrkiller as a client (events: 0)
2008-12-29 23:45:18.263 MainServer::HandleAnnounce Monitor
2008-12-29 23:45:18.264 adding: vcrkiller as a client (events: 1)
```

mythfrontend.log:
```
Starting mythfrontend.real..
2008-12-29 23:42:54.015 New DB connection, total: 2
2008-12-29 23:42:54.016 Connected to database 'mythconverg' at host: localhost
2008-12-29 23:42:54.019 mythfrontend version: 0.21.20080304-1 www.mythtv.org
2008-12-29 23:42:54.019 Enabled verbose msgs:  important general
2008-12-29 23:42:54.492 No theme dir: /home/siersmak/.mythtv/themes/Mythbuntu-8.04
2008-12-29 23:42:54.494 Primary screen 0.
2008-12-29 23:42:54.495 Using screen 0, 1024x768 at 0,0
2008-12-29 23:42:54.495 No theme dir: /home/siersmak/.mythtv/themes/Mythbuntu-8.04
2008-12-29 23:42:54.496 Switching to square mode (Mythbuntu-8.04)
2008-12-29 23:42:54.514 Using the Qt painter
2008-12-29 23:42:54.514 JoystickMenuClient Error: Joystick disabled - Failed to read /home/siersmak/.mythtv/joystickmenurc
2008-12-29 23:42:54.517 lirc init success using configuration file: /home/siersmak/.mythtv/lircrc
2008-12-29 23:42:55.728 Specified base font 'medium' does not exist for font clock
2008-12-29 23:42:55.728 Specified base font 'medium' does not exist for font small
2008-12-29 23:42:55.729 Specified base font 'medium' does not exist for font medium
2008-12-29 23:42:55.729 Specified base font 'medium' does not exist for font large
2008-12-29 23:42:55.730 Loading from: /usr/share/mythtv/themes/Mythbuntu-8.04/base.xml
2008-12-29 23:42:55.899 Loading from: /usr/share/mythtv/themes/default/base.xml
2008-12-29 23:42:55.956 Registering Internal as a media playback plugin.
2008-12-29 23:42:56.050 MonitorRegisterExtensions(0x100, gif,jpg,png)
2008-12-29 23:42:56.096 Failed to run 'cdrecord --scanbus'
2008-12-29 23:42:56.101 Failed to run 'cdrecord --scanbus -dev=ATA'
2008-12-29 23:42:56.105 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2008-12-29 23:42:56.146 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
Failed to find network interface eth0
SIP listening on IP Address :5060 NAT address 
SIP: Cannot register; proxy, username or password not set
Destroying SipFsm object 
2008-12-29 23:42:56.277 No theme dir: /home/siersmak/.mythtv/themes/Mythbuntu-8.04
2008-12-29 23:42:59.453 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-12-29 23:42:59.454 Using protocol version 40
2008-12-29 23:42:59.470 TV: Attempting to change from None to WatchingLiveTV
2008-12-29 23:42:59.471 Using protocol version 40
2008-12-29 23:43:01.259 New DB connection, total: 3
2008-12-29 23:43:01.260 Connected to database 'mythconverg' at host: localhost
2008-12-29 23:43:01.277 DPMS Deactivated 
2008-12-29 23:43:02.143 AFD: Opened codec 0x8bbf030, id(MPEG2VIDEO) type(Video)
2008-12-29 23:43:02.144 AFD: codec MP2 has 2 channels
2008-12-29 23:43:02.144 AFD: Opened codec 0x8bbe480, id(MP2) type(Audio)
2008-12-29 23:43:02.205 Opening audio device '/dev/dsp'. ch 2(2) sr 48000
2008-12-29 23:43:02.205 Opening OSS audio device '/dev/dsp'.
2008-12-29 23:43:02.248 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2008-12-29 23:43:02.306 OSD Theme Dimensions W: 640 H: 480
2008-12-29 23:43:02.639 TV: Changing from None to WatchingLiveTV
2008-12-29 23:43:02.645 Realtime priority would require SUID as root.
2008-12-29 23:43:02.748 OpenGLVideoSync()
2008-12-29 23:43:02.793 Video timing method: SGI OpenGL
2008-12-29 23:43:07.788 TV: Attempting to change from WatchingLiveTV to None
2008-12-29 23:43:07.864 ~OpenGLVideoSync() -- begin
2008-12-29 23:43:07.864 ~OpenGLVideoSync() -- middle
2008-12-29 23:43:07.864 ~OpenGLVideoSync() -- end
2008-12-29 23:43:08.263 TV: Changing from WatchingLiveTV to None
2008-12-29 23:43:08.288 DPMS Reactivated.
2008-12-29 23:43:11.703 Deleting UPnP client...
```

v4l2-ctl --log-status:
```
[ 1163.315060] ivtv0: =================  START STATUS CARD #0  =================
   [ 1163.315080] ivtv0: Version: 1.4.0 Card: Hauppauge WinTV PVR-250
   [ 1163.367635] tveeprom 0-0050: Hauppauge model 32032, rev B310, serial# 7043629
   [ 1163.367644] tveeprom 0-0050: tuner model is Philips FI1236 MK2 (idx 10, type 2)
   [ 1163.367648] tveeprom 0-0050: TV standards NTSC(M) (eeprom 0x08)
   [ 1163.367656] tveeprom 0-0050: audio processor is MSP4448 (idx 27)
   [ 1163.367660] tveeprom 0-0050: decoder processor is SAA7115 (idx 19)
   [ 1163.367663] tveeprom 0-0050: has no radio, has IR receiver, has no IR transmitter
   [ 1163.367670] saa7115 0-0021: Audio frequency: 48000 Hz
   [ 1163.369420] saa7115 0-0021: Input:           Composite 4
   [ 1163.369424] saa7115 0-0021: Video signal:    broadcast/DVD
   [ 1163.369428] saa7115 0-0021: Frequency:       60 Hz
   [ 1163.369431] saa7115 0-0021: Detected format: NTSC
   [ 1163.369434] saa7115 0-0021: Width, Height:   720, 480
   [ 1163.370919] msp3400 0-0040: msp3400 rev1 = 0x0117 rev2 = 0x3042
   [ 1163.370925] msp3400 0-0040: Audio:    volume 58981
   [ 1163.370930] msp3400 0-0040: Standard: 4.5  M BTSC-Stereo (stereo)
   [ 1163.370934] msp3400 0-0040: Audmode:  0x0003
   [ 1163.370937] msp3400 0-0040: Routing:  0x00000000 (input) 0x00000044 (output)
   [ 1163.370947] msp3400 0-0040: ACB:      0x0c00
   [ 1163.370952] tuner 0-0061: Tuner mode:      analog TV
   [ 1163.370955] tuner 0-0061: Frequency:       55.25 MHz
   [ 1163.370958] tuner 0-0061: Standard:        0x0000b000
   [ 1163.370964] ivtv0: Video Input:  Tuner 1
   [ 1163.370967] ivtv0: Audio Input:  Tuner 1
   [ 1163.370969] ivtv0: Tuner:  TV
   [ 1163.370973] ivtv0: Stream: MPEG-2 Program Stream
   [ 1163.370978] ivtv0: VBI Format: No VBI
   [ 1163.370981] ivtv0: Video:  720x480, 30 fps
   [ 1163.370985] ivtv0: Video:  MPEG-2, 4x3, Variable Bitrate, 4500000, Peak 6000000
   [ 1163.370991] ivtv0: Video:  GOP Size 15, 2 B-Frames, GOP Closure
   [ 1163.370998] ivtv0: Audio:  48 kHz, Layer II, 384 kbps, Stereo, No Emphasis, No CRC
   [ 1163.371004] ivtv0: Spatial Filter:  Manual, Luma 1D Horizontal, Chroma 1D Horizontal, 0
   [ 1163.371008] ivtv0: Temporal Filter: Manual, 8
   [ 1163.371013] ivtv0: Median Filter:   Off, Luma [0, 255], Chroma [0, 255]
   [ 1163.371017] ivtv0: Status flags:    0x00200000
   [ 1163.371020] ivtv0: Stream encoder MPG: status 0x0000, 0% of 4096 KiB (128 buffers) in use
   [ 1163.371024] ivtv0: Stream encoder YUV: status 0x0000, 0% of 2048 KiB (64 buffers) in use
   [ 1163.371029] ivtv0: Stream encoder VBI: status 0x0000, 0% of 1040 KiB (61 buffers) in use
   [ 1163.371032] ivtv0: Stream encoder PCM: status 0x0000, 0% of 324 KiB (72 buffers) in use
   [ 1163.371036] ivtv0: Read MPG/VBI: 6875072/0 bytes
   [ 1163.371039] ivtv0: ==================  END STATUS CARD #0  ==================
```

Any help that anyone can offer would be appreciated.  I have searched this forum up and down for someone experiencing the same problem, and can't seem to work it out.  Also, I'm unsure why it tells me to set the sampling rate to 48kHz, because I have already done that it in the transcoders section of my recording profiles.

---

