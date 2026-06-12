---
title: "XvMC, &quot;Failed To Reinit Video&quot;"
date: 2009-01-20
forum: Mythbuntu
---

### Post by GCFreak on 2009-01-20
Hi,

Yeah, the title says it all pretty much this time. No error code, kinda stuck. I want to use the CPU-- profile for the TV so I can get better HD framerates, but it doesn't work when XvMC is used.

Thanks.

---

### Post by GCFreak on 2009-01-22
Bump. Upgrading the video card drivers didn't seem to help... I've run out of ideas.

---

### Post by GCFreak on 2009-01-22
Ok, I have a log for you guys to sift through:

```
2009-01-23 15:39:29.172 Using runtime prefix = /usr
2009-01-23 15:39:29.353 XScreenSaver support enabled
2009-01-23 15:39:29.353 DPMS is active.
2009-01-23 15:39:29.354 Empty LocalHostName.
2009-01-23 15:39:29.354 Using localhost value of mediacentre
2009-01-23 15:39:29.363 New DB connection, total: 1
2009-01-23 15:39:29.368 Connected to database 'mythconverg' at host: localhost
2009-01-23 15:39:29.369 Closing DB connection named 'DBManager0'
2009-01-23 15:39:29.371 Primary screen 0.
2009-01-23 15:39:29.371 Connected to database 'mythconverg' at host: localhost
2009-01-23 15:39:29.373 Using screen 0, 1024x768 at 0,0
2009-01-23 15:39:29.382 New DB connection, total: 2
2009-01-23 15:39:29.382 Connected to database 'mythconverg' at host: localhost
2009-01-23 15:39:29.386 mythfrontend version: 0.21.20080304-1 www.mythtv.org
2009-01-23 15:39:29.386 Enabled verbose msgs:  important general
2009-01-23 15:39:29.860 No theme dir: /home/media/.mythtv/themes/Mythbuntu-8.04
2009-01-23 15:39:29.867 Primary screen 0.
2009-01-23 15:39:29.868 Using screen 0, 1024x768 at 0,0
2009-01-23 15:39:29.869 No theme dir: /home/media/.mythtv/themes/Mythbuntu-8.04
2009-01-23 15:39:29.870 Switching to square mode (Mythbuntu-8.04)
2009-01-23 15:39:29.906 Using the OpenGL painter
2009-01-23 15:39:29.907 lirc init success using configuration file: /home/media/.mythtv/lircrc
2009-01-23 15:39:29.908 JoystickMenuClient Error: Joystick disabled - Failed to read /home/media/.mythtv/joystickmenurc
2009-01-23 15:39:31.167 Specified base font 'medium' does not exist for font clock
2009-01-23 15:39:31.167 Specified base font 'medium' does not exist for font small
2009-01-23 15:39:31.167 Specified base font 'medium' does not exist for font medium
2009-01-23 15:39:31.167 Specified base font 'medium' does not exist for font large
2009-01-23 15:39:31.168 Loading from: /usr/share/mythtv/themes/Mythbuntu-8.04/base.xml
2009-01-23 15:39:31.205 Loading from: /usr/share/mythtv/themes/default/base.xml
2009-01-23 15:39:31.257 Registering Internal as a media playback plugin.
2009-01-23 15:39:31.347 MonitorRegisterExtensions(0x100, gif,jpg,png)
2009-01-23 15:39:31.401 Failed to run 'cdrecord --scanbus'
2009-01-23 15:39:31.405 Failed to run 'cdrecord --scanbus -dev=ATA'
2009-01-23 15:39:31.410 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2009-01-23 15:39:31.449 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
SIP listening on IP Address 10.1.1.6:5060 NAT address 10.1.1.6
SIP: Cannot register; proxy, username or password not set
2009-01-23 15:39:31.578 No theme dir: /home/media/.mythtv/themes/Mythbuntu-8.04
2009-01-23 15:39:32.188 Using NV NPOT texture extension
2009-01-23 15:39:33.596 Connecting to backend server: 10.1.1.6:6543 (try 1 of 5)
2009-01-23 15:39:33.597 Using protocol version 40
2009-01-23 15:39:33.626 TV: Attempting to change from None to WatchingLiveTV
2009-01-23 15:39:33.639 Using protocol version 40
2009-01-23 15:39:35.242 DPMS Deactivated 
2009-01-23 15:39:35.247 New DB connection, total: 3
2009-01-23 15:39:35.248 Connected to database 'mythconverg' at host: localhost
2009-01-23 15:39:35.266 NVP: Disabling Audio, params(-1,2,44100)
DisplaResX: Desired Resolution and FrameRate not found.
2009-01-23 15:39:35.312 SwitchToVideo: Video size 720 x 576: xrandr failed for 720 x 576
2009-01-23 15:39:35.314 VideoOutputXv: Desired video renderer 'ivtv' not available.
			codec 'None' makes 'xv-blit,xshm,opengl,xlib,' available, using 'xv-blit' instead.
2009-01-23 15:39:35.317 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2009-01-23 15:39:35.385 OSD Theme Dimensions W: 640 H: 480
2009-01-23 15:39:35.803 TV: Changing from None to WatchingLiveTV
2009-01-23 15:39:35.806 New DB connection, total: 4
2009-01-23 15:39:35.806 Realtime priority would require SUID as root.
2009-01-23 15:39:35.807 Connected to database 'mythconverg' at host: localhost
2009-01-23 15:39:35.808 FilterManager: failed to load filter 'none', no such filter exists
2009-01-23 15:39:35.808 Couldn't load deinterlace filter none
2009-01-23 15:39:35.912 OpenGLVideoSync()
2009-01-23 15:39:35.977 Video timing method: SGI OpenGL
2009-01-23 15:39:37.555 RingBuf(/var/lib/mythtv/recordings/1001_20090123153935.mpg): Waited 1.0 seconds for data to become available...
2009-01-23 15:39:37.555 Checking to see if there's a new livetv program to switch to..
2009-01-23 15:39:38.146 [h264 @ 0xb722fb70]number of reference frames exceeds max (probably corrupt input), discarding one
2009-01-23 15:39:38.146 [h264 @ 0xb722fb70]number of reference frames exceeds max (probably corrupt input), discarding one
2009-01-23 15:39:38.146 [h264 @ 0xb722fb70]number of reference frames exceeds max (probably corrupt input), discarding one
2009-01-23 15:39:38.146 [h264 @ 0xb722fb70]number of reference frames exceeds max (probably corrupt input), discarding one
2009-01-23 15:39:38.146 [h264 @ 0xb722fb70]number of reference frames exceeds max (probably corrupt input), discarding one
2009-01-23 15:39:38.146 [h264 @ 0xb722fb70]number of reference frames exceeds max (probably corrupt input), discarding one
2009-01-23 15:39:38.147 [h264 @ 0xb722fb70]number of reference frames exceeds max (probably corrupt input), discarding one
2009-01-23 15:39:38.147 [h264 @ 0xb722fb70]number of reference frames exceeds max (probably corrupt input), discarding one
2009-01-23 15:39:38.147 [h264 @ 0xb722fb70]number of reference frames exceeds max (probably corrupt input), discarding one
2009-01-23 15:39:38.147 [h264 @ 0xb722fb70]number of reference frames exceeds max (probably corrupt input), discarding one
2009-01-23 15:39:38.147 [h264 @ 0xb722fb70]number of reference frames exceeds max (probably corrupt input), discarding one
2009-01-23 15:39:38.147 [h264 @ 0xb722fb70]number of reference frames exceeds max (probably corrupt input), discarding one
2009-01-23 15:39:38.147 [h264 @ 0xb722fb70]number of reference frames exceeds max (probably corrupt input), discarding one
2009-01-23 15:39:38.147 [h264 @ 0xb722fb70]number of reference frames exceeds max (probably corrupt input), discarding one
2009-01-23 15:39:38.147 [h264 @ 0xb722fb70]number of reference frames exceeds max (probably corrupt input), discarding one
2009-01-23 15:39:38.147 [h264 @ 0xb722fb70]number of reference frames exceeds max (probably corrupt input), discarding one
2009-01-23 15:39:38.147 [h264 @ 0xb722fb70]number of reference frames exceeds max (probably corrupt input), discarding one
2009-01-23 15:39:38.147 [h264 @ 0xb722fb70]number of reference frames exceeds max (probably corrupt input), discarding one
2009-01-23 15:39:38.148 [h264 @ 0xb722fb70]number of reference frames exceeds max (probably corrupt input), discarding one
2009-01-23 15:39:38.148 [h264 @ 0xb722fb70]number of reference frames exceeds max (probably corrupt input), discarding one
2009-01-23 15:39:38.148 [h264 @ 0xb722fb70]number of reference frames exceeds max (probably corrupt input), discarding one
2009-01-23 15:39:38.148 [h264 @ 0xb722fb70]number of reference frames exceeds max (probably corrupt input), discarding one
2009-01-23 15:39:38.148 [h264 @ 0xb722fb70]number of reference frames exceeds max (probably corrupt input), discarding one
2009-01-23 15:39:38.148 [h264 @ 0xb722fb70]number of reference frames exceeds max (probably corrupt input), discarding one
2009-01-23 15:39:38.148 [h264 @ 0xb722fb70]number of reference frames exceeds max (probably corrupt input), discarding one
2009-01-23 15:39:38.148 [h264 @ 0xb722fb70]number of reference frames exceeds max (probably corrupt input), discarding one
2009-01-23 15:39:38.148 [h264 @ 0xb722fb70]number of reference frames exceeds max (probably corrupt input), discarding one
2009-01-23 15:39:38.148 [h264 @ 0xb722fb70]number of reference frames exceeds max (probably corrupt input), discarding one
2009-01-23 15:39:38.148 [h264 @ 0xb722fb70]number of reference frames exceeds max (probably corrupt input), discarding one
2009-01-23 15:39:38.148 [h264 @ 0xb722fb70]number of reference frames exceeds max (probably corrupt input), discarding one
2009-01-23 15:39:38.148 [h264 @ 0xb722fb70]number of reference frames exceeds max (probably corrupt input), discarding one
2009-01-23 15:39:38.149 [h264 @ 0xb722fb70]number of reference frames exceeds max (probably corrupt input), discarding one
2009-01-23 15:39:38.149 [h264 @ 0xb722fb70]number of reference frames exceeds max (probably corrupt input), discarding one
2009-01-23 15:39:38.149 [h264 @ 0xb722fb70]number of reference frames exceeds max (probably corrupt input), discarding one
2009-01-23 15:39:38.149 [h264 @ 0xb722fb70]number of reference frames exceeds max (probably corrupt input), discarding one
2009-01-23 15:39:38.149 [h264 @ 0xb722fb70]number of reference frames exceeds max (probably corrupt input), discarding one
2009-01-23 15:39:38.149 [h264 @ 0xb722fb70]number of reference frames exceeds max (probably corrupt input), discarding one
2009-01-23 15:39:38.149 [h264 @ 0xb722fb70]number of reference frames exceeds max (probably corrupt input), discarding one
2009-01-23 15:39:38.149 [h264 @ 0xb722fb70]number of reference frames exceeds max (probably corrupt input), discarding one
2009-01-23 15:39:38.149 [h264 @ 0xb722fb70]number of reference frames exceeds max (probably corrupt input), discarding one
2009-01-23 15:39:38.149 [h264 @ 0xb722fb70]number of reference frames exceeds max (probably corrupt input), discarding one
2009-01-23 15:39:38.149 [h264 @ 0xb722fb70]number of reference frames exceeds max (probably corrupt input), discarding one
2009-01-23 15:39:38.149 [h264 @ 0xb722fb70]number of reference frames exceeds max (probably corrupt input), discarding one
2009-01-23 15:39:38.149 [h264 @ 0xb722fb70]number of reference frames exceeds max (probably corrupt input), discarding one
2009-01-23 15:39:38.149 [h264 @ 0xb722fb70]number of reference frames exceeds max (probably corrupt input), discarding one
2009-01-23 15:39:38.149 [h264 @ 0xb722fb70]number of reference frames exceeds max (probably corrupt input), discarding one
2009-01-23 15:39:38.149 [h264 @ 0xb722fb70]number of reference frames exceeds max (probably corrupt input), discarding one
2009-01-23 15:39:38.150 [h264 @ 0xb722fb70]number of reference frames exceeds max (probably corrupt input), discarding one
2009-01-23 15:39:38.150 [h264 @ 0xb722fb70]number of reference frames exceeds max (probably corrupt input), discarding one
2009-01-23 15:39:38.150 [h264 @ 0xb722fb70]number of reference frames exceeds max (probably corrupt input), discarding one
2009-01-23 15:39:38.150 [h264 @ 0xb722fb70]number of reference frames exceeds max (probably corrupt input), discarding one
2009-01-23 15:39:38.150 [h264 @ 0xb722fb70]number of reference frames exceeds max (probably corrupt input), discarding one
2009-01-23 15:39:38.150 [h264 @ 0xb722fb70]number of reference frames exceeds max (probably corrupt input), discarding one
2009-01-23 15:39:38.150 [h264 @ 0xb722fb70]number of reference frames exceeds max (probably corrupt input), discarding one
2009-01-23 15:39:38.150 [h264 @ 0xb722fb70]number of reference frames exceeds max (probably corrupt input), discarding one
2009-01-23 15:39:38.150 [h264 @ 0xb722fb70]number of reference frames exceeds max (probably corrupt input), discarding one
2009-01-23 15:39:38.150 [h264 @ 0xb722fb70]number of reference frames exceeds max (probably corrupt input), discarding one
2009-01-23 15:39:38.150 [h264 @ 0xb722fb70]number of reference frames exceeds max (probably corrupt input), discarding one
2009-01-23 15:39:38.150 [h264 @ 0xb722fb70]number of reference frames exceeds max (probably corrupt input), discarding one
2009-01-23 15:39:38.150 [h264 @ 0xb722fb70]number of reference frames exceeds max (probably corrupt input), discarding one
2009-01-23 15:39:38.150 [h264 @ 0xb722fb70]number of reference frames exceeds max (probably corrupt input), discarding one
2009-01-23 15:39:38.151 [h264 @ 0xb722fb70]number of reference frames exceeds max (probably corrupt input), discarding one
2009-01-23 15:39:38.151 [h264 @ 0xb722fb70]number of reference frames exceeds max (probably corrupt input), discarding one
2009-01-23 15:39:38.151 [h264 @ 0xb722fb70]number of reference frames exceeds max (probably corrupt input), discarding one
2009-01-23 15:39:38.151 [h264 @ 0xb722fb70]number of reference frames exceeds max (probably corrupt input), discarding one
2009-01-23 15:39:38.151 [h264 @ 0xb722fb70]number of reference frames exceeds max (probably corrupt input), discarding one
2009-01-23 15:39:38.151 [h264 @ 0xb722fb70]number of reference frames exceeds max (probably corrupt input), discarding one
2009-01-23 15:39:38.151 [h264 @ 0xb722fb70]number of reference frames exceeds max (probably corrupt input), discarding one
2009-01-23 15:39:38.160 [h264 @ 0xb722fb70]number of reference frames exceeds max (probably corrupt input), discarding one
2009-01-23 15:39:38.160 [h264 @ 0xb722fb70]number of reference frames exceeds max (probably corrupt input), discarding one
2009-01-23 15:39:38.160 [h264 @ 0xb722fb70]number of reference frames exceeds max (probably corrupt input), discarding one
2009-01-23 15:39:38.160 [h264 @ 0xb722fb70]number of reference frames exceeds max (probably corrupt input), discarding one
2009-01-23 15:39:38.160 [h264 @ 0xb722fb70]number of reference frames exceeds max (probably corrupt input), discarding one
2009-01-23 15:39:38.161 [h264 @ 0xb722fb70]number of reference frames exceeds max (probably corrupt input), discarding one
2009-01-23 15:39:38.161 [h264 @ 0xb722fb70]number of reference frames exceeds max (probably corrupt input), discarding one
2009-01-23 15:39:38.161 [h264 @ 0xb722fb70]number of reference frames exceeds max (probably corrupt input), discarding one
2009-01-23 15:39:38.161 [h264 @ 0xb722fb70]number of reference frames exceeds max (probably corrupt input), discarding one
2009-01-23 15:39:38.161 [h264 @ 0xb722fb70]number of reference frames exceeds max (probably corrupt input), discarding one
2009-01-23 15:39:38.161 [h264 @ 0xb722fb70]number of reference frames exceeds max (probably corrupt input), discarding one
2009-01-23 15:39:38.161 [h264 @ 0xb722fb70]number of reference frames exceeds max (probably corrupt input), discarding one
2009-01-23 15:39:38.161 [h264 @ 0xb722fb70]number of reference frames exceeds max (probably corrupt input), discarding one
2009-01-23 15:39:38.161 [h264 @ 0xb722fb70]number of reference frames exceeds max (probably corrupt input), discarding one
2009-01-23 15:39:38.161 [h264 @ 0xb722fb70]number of reference frames exceeds max (probably corrupt input), discarding one
2009-01-23 15:39:38.161 [h264 @ 0xb722fb70]number of reference frames exceeds max (probably corrupt input), discarding one
2009-01-23 15:39:38.162 [h264 @ 0xb722fb70]number of reference frames exceeds max (probably corrupt input), discarding one
2009-01-23 15:39:38.162 [h264 @ 0xb722fb70]number of reference frames exceeds max (probably corrupt input), discarding one
2009-01-23 15:39:38.162 [h264 @ 0xb722fb70]number of reference frames exceeds max (probably corrupt input), discarding one
2009-01-23 15:39:38.162 [h264 @ 0xb722fb70]number of reference frames exceeds max (probably corrupt input), discarding one
2009-01-23 15:39:38.162 [h264 @ 0xb722fb70]number of reference frames exceeds max (probably corrupt input), discarding one
2009-01-23 15:39:38.162 [h264 @ 0xb722fb70]number of reference frames exceeds max (probably corrupt input), discarding one
2009-01-23 15:39:38.162 [h264 @ 0xb722fb70]number of reference frames exceeds max (probably corrupt input), discarding one
2009-01-23 15:39:38.162 [h264 @ 0xb722fb70]number of reference frames exceeds max (probably corrupt input), discarding one
2009-01-23 15:39:38.162 [h264 @ 0xb722fb70]number of reference frames exceeds max (probably corrupt input), discarding one
2009-01-23 15:39:38.162 [h264 @ 0xb722fb70]number of reference frames exceeds max (probably corrupt input), discarding one
2009-01-23 15:39:38.162 [h264 @ 0xb722fb70]number of reference frames exceeds max (probably corrupt input), discarding one
2009-01-23 15:39:38.162 [h264 @ 0xb722fb70]number of reference frames exceeds max (probably corrupt input), discarding one
2009-01-23 15:39:38.163 [h264 @ 0xb722fb70]number of reference frames exceeds max (probably corrupt input), discarding one
2009-01-23 15:39:38.163 [h264 @ 0xb722fb70]number of reference frames exceeds max (probably corrupt input), discarding one
2009-01-23 15:39:38.163 [h264 @ 0xb722fb70]number of reference frames exceeds max (probably corrupt input), discarding one
2009-01-23 15:39:38.163 [h264 @ 0xb722fb70]number of reference frames exceeds max (probably corrupt input), discarding one
2009-01-23 15:39:38.166 [h264 @ 0xb722fb70]number of reference frames exceeds max (probably corrupt input), discarding one
2009-01-23 15:39:38.166 [h264 @ 0xb722fb70]number of reference frames exceeds max (probably corrupt input), discarding one
2009-01-23 15:39:38.166 [h264 @ 0xb722fb70]number of reference frames exceeds max (probably corrupt input), discarding one
2009-01-23 15:39:38.166 [h264 @ 0xb722fb70]number of reference frames exceeds max (probably corrupt input), discarding one
2009-01-23 15:39:38.166 [h264 @ 0xb722fb70]number of reference frames exceeds max (probably corrupt input), discarding one
2009-01-23 15:39:38.166 [h264 @ 0xb722fb70]number of reference frames exceeds max (probably corrupt input), discarding one
2009-01-23 15:39:38.166 [h264 @ 0xb722fb70]number of reference frames exceeds max (probably corrupt input), discarding one
2009-01-23 15:39:38.166 [h264 @ 0xb722fb70]number of reference frames exceeds max (probably corrupt input), discarding one
2009-01-23 15:39:38.166 [h264 @ 0xb722fb70]number of reference frames exceeds max (probably corrupt input), discarding one
2009-01-23 15:39:38.166 [h264 @ 0xb722fb70]number of reference frames exceeds max (probably corrupt input), discarding one
2009-01-23 15:39:38.167 [h264 @ 0xb722fb70]number of reference frames exceeds max (probably corrupt input), discarding one
2009-01-23 15:39:38.167 [h264 @ 0xb722fb70]number of reference frames exceeds max (probably corrupt input), discarding one
2009-01-23 15:39:38.217 [h264 @ 0xb722fb70]mmco: unref short failure
2009-01-23 15:39:38.217 [h264 @ 0xb722fb70]number of reference frames exceeds max (probably corrupt input), discarding one
2009-01-23 15:39:38.672 NVP: Prebuffer wait timed out 10 times.
2009-01-23 15:39:40.841 NVP: Prebuffer wait timed out 10 times.
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  142
  Minor opcode:  2
  Resource id:  0x1a6
2009-01-23 15:39:41.442 VideoOutputXv Error: Unable to create XvMC Context, status(11): BadAlloc
X Error: BadContext 154
  Major opcode:  142
  Minor opcode:  3
  Resource id:  0x1a6
2009-01-23 15:39:41.442 Error: XvMC-IDCT H.264 not supported by ffmpeg
DisplaResX: Desired Resolution and FrameRate not found.
2009-01-23 15:39:41.446 SwitchToVideo: Video size 1280 x 720: xrandr failed for 720 x 576
2009-01-23 15:39:41.446 Error: XvMC-IDCT H.264 not supported by ffmpeg
2009-01-23 15:39:41.453 Error: XvMC-IDCT H.264 not supported by ffmpeg
2009-01-23 15:39:41.458 VideoOutputXv: XvMC Adaptor Name: 'NV17 Video Texture'
2009-01-23 15:39:41.458 VideoOutputXv Error: Unable to create XvMC Context, status(11): BadAlloc
2009-01-23 15:39:41.458 
XError type: 0
    display: 0x9fed440
  serial no: 380
   err code: \ufffd (BadContext)
   req code: 
 minor code: 
resource id: 422
2009-01-23 15:39:41.459 
XError type: 0
    display: 0x9fed440
  serial no: 379
   err code: (BadMatch (invalid parameter attributes))
   req code: 
 minor code: 
resource id: 422
2009-01-23 15:39:41.459 
XError type: 0
    display: 0x9fed440
  serial no: 380
   err code: \ufffd (BadContext)
   req code: 
 minor code: 
resource id: 422
2009-01-23 15:39:41.459 
XError type: 0
    display: 0x9fed440
  serial no: 379
   err code: (BadMatch (invalid parameter attributes))
   req code: 
 minor code: 
resource id: 422
2009-01-23 15:39:41.459 VideoOutputXv Error: Failed to create XvMC Buffers.
2009-01-23 15:39:41.459 VideoOutputXv: Falling back to X11 video output over a network socket.
			      *** May be very slow ***
2009-01-23 15:39:41.459 VideoOutputXv Error: XCreateImage failed: XJ_disp(0x9fed440) visual(0x9fee598) 
                        XJ_depth(24) WxH(1024x768) bpl(3072)
2009-01-23 15:39:41.460 VideoOutputXv Error: Failed to create X buffers.
2009-01-23 15:39:41.460 Error: XvMC-IDCT H.264 not supported by ffmpeg
2009-01-23 15:39:41.463 VideoOutputXv: XvMC Adaptor Name: 'NV17 Video Texture'
2009-01-23 15:39:41.463 VideoOutputXv Error: Unable to create XvMC Context, status(11): BadAlloc
2009-01-23 15:39:41.463 
XError type: 0
    display: 0x9fed440
  serial no: 391
   err code: \ufffd (BadContext)
   req code: 
 minor code: 
resource id: 422
2009-01-23 15:39:41.463 
XError type: 0
    display: 0x9fed440
  serial no: 390
   err code: (BadMatch (invalid parameter attributes))
   req code: 
 minor code: 
resource id: 422
2009-01-23 15:39:41.463 
XError type: 0
    display: 0x9fed440
  serial no: 391
   err code: \ufffd (BadContext)
   req code: 
 minor code: 
resource id: 422
2009-01-23 15:39:41.463 
XError type: 0
    display: 0x9fed440
  serial no: 390
   err code: (BadMatch (invalid parameter attributes))
   req code: 
 minor code: 
resource id: 422
2009-01-23 15:39:41.464 VideoOutputXv Error: Failed to create XvMC Buffers.
2009-01-23 15:39:41.464 VideoOutputXv: Falling back to X11 video output over a network socket.
			      *** May be very slow ***
2009-01-23 15:39:41.464 VideoOutputXv Error: XCreateImage failed: XJ_disp(0x9fed440) visual(0x9fee598) 
                        XJ_depth(24) WxH(1024x768) bpl(3072)
2009-01-23 15:39:41.464 VideoOutputXv Error: Failed to create X buffers.
2009-01-23 15:39:41.464 VideoOutputXv Error: Failed to get any video output Exiting playback.
2009-01-23 15:39:41.464 VideoOutputXv Error: InputChanged(): Failed to recreate buffers
2009-01-23 15:39:41.464 ReinitVideo(): videoOutput->IsErrored()
2009-01-23 15:39:41.519 TV: Attempting to change from WatchingLiveTV to None
2009-01-23 15:39:42.299 NVP: Prebuffer wait timed out 10 times.
2009-01-23 15:39:43.186 AFD Error: Could not find decoder for codec (NONE), ignoring.
2009-01-23 15:39:43.186 AFD: codec AAC_LATM has 2 channels
2009-01-23 15:39:43.187 AFD: Opened codec 0xabcbac50, id(AAC_LATM) type(Audio)
2009-01-23 15:39:43.187 AFD: Opened codec 0xa626f7e0, id(DVB_SUBTITLE) type(Subtitle)
2009-01-23 15:39:43.187 Couldn't open decoder for: /var/lib/mythtv/recordings/1001_20090123153935.mpg
2009-01-23 15:39:43.187 NVP, Error: JumpToProgram failed.
2009-01-23 15:39:43.187 NVP, Error: Unknown error, exiting decoder
2009-01-23 15:39:43.250 ~OpenGLVideoSync() -- begin
2009-01-23 15:39:43.251 ~OpenGLVideoSync() -- middle
2009-01-23 15:39:43.251 ~OpenGLVideoSync() -- end
2009-01-23 15:39:44.096 TV: Changing from WatchingLiveTV to None
2009-01-23 15:39:44.171 DPMS Reactivated.
Destroying SipFsm object 
2009-01-23 15:39:48.807 Deleting UPnP client...

```

I simply start the frontend, tried to start TV ONE, a 720p channel, and exited it.

---

### Post by GCFreak on 2009-01-23
Ok nevermind, Freeview|HD here in New Zealand uses MPEG-4 H.264/AVC, and as far as I know XvMC only supports MPEG-2. That's a shame. I hope it does soon...

---

