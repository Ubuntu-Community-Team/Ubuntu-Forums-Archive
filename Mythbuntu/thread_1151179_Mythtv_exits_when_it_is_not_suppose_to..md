---
title: "Mythtv exits when it is not suppose to."
date: 2009-05-06
forum: Mythbuntu
---

### Post by mtbdrew on 2009-05-06
Mythbuntu 9.04 exits to desktop when trying to delete previously watched show. I've tried disabling exit but it doesn't work.

---

### Post by andrewc6l on 2009-05-06
Is this happening with just one program, or with all programs? Do you see anything interesting in /var/log/mythtv/mythfrontend.log?

---

### Post by mtbdrew on 2009-05-07
So far this is only happening with MythTV, I will need to check the log file when I get home.

Thanks
Andrew

---

### Post by s_g_robertson on 2009-05-07
> **andrewc6l said:**
> Is this happening with just one program, or with all programs? Do you see anything interesting in /var/log/mythtv/mythfrontend.log?

> **mtbdrew said:**
> So far this is only happening with MythTV, I will need to check the log file when I get home.

Thanks
Andrew

I think he was meaning does it happen with all recorded programs within MythTV as opposed to other aplplications.

---

### Post by mtbdrew on 2009-05-08
> **s_g_robertson said:**
> I think he was meaning does it happen with all recorded programs within MythTV as opposed to other aplplications.

I've only noticed when finished watching a recording and I try to delete or go back to the list of recorded shows. If trying to delete the Frontend ends without deleting and I thrown back to the desktop. If trying to escape back to the list again I'm thrown back to the desktop.

---

### Post by andrewc6l on 2009-05-08
The next time this happens, please go to a command line and execute the following command:

tail -n 100 /var/log/mythtv/mythfrontend.log

and post the results here. Hopefully it will have something useful :-)

---

### Post by mtbdrew on 2009-05-09
> **andrewc6l said:**
> The next time this happens, please go to a command line and execute the following command:

tail -n 100 /var/log/mythtv/mythfrontend.log

and post the results here. Hopefully it will have something useful :-)

Here you go:

2009-05-09 20:41:09.634 Loading from: /usr/share/mythtv/themes/Mythbuntu-8.04-wide/base.xml
2009-05-09 20:41:09.668 Loading from: /usr/share/mythtv/themes/default/base.xml
2009-05-09 20:41:09.772 Registering Internal as a media playback plugin.
2009-05-09 20:41:09.960 MonitorRegisterExtensions(0x100, gif,jpg,png)
2009-05-09 20:41:10.127 Failed to run 'cdrecord --scanbus'
2009-05-09 20:41:10.134 Failed to run 'cdrecord --scanbus -dev=ATA'
2009-05-09 20:41:10.137 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2009-05-09 20:41:10.180 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
2009-05-09 20:41:10.288 No theme dir: /home/mythbox/.mythtv/themes/Mythbuntu-8.04-wide
2009-05-09 20:41:10.865 Using NV NPOT texture extension
2009-05-09 20:42:18.851 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-05-09 20:42:18.855 Using protocol version 40
2009-05-09 20:42:21.086 Deleting UPnP client...
Starting mythfrontend.real..
2009-05-09 21:02:12.384 New DB connection, total: 2
2009-05-09 21:02:12.384 Connected to database 'mythconverg' at host: localhost
2009-05-09 21:02:12.387 mythfrontend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2009-05-09 21:02:12.387 Enabled verbose msgs:  important general
2009-05-09 21:02:12.409 Connecting to lcd server: localhost:6545 (try 1 of 10)
2009-05-09 21:02:13.457 No theme dir: /home/mythbox/.mythtv/themes/Mythbuntu-8.04-wide
2009-05-09 21:02:13.458 Primary screen 0.
2009-05-09 21:02:13.459 Using screen 0, 1366x768 at 0,0
2009-05-09 21:02:13.459 No theme dir: /home/mythbox/.mythtv/themes/Mythbuntu-8.04-wide
2009-05-09 21:02:13.460 Switching to wide mode (Mythbuntu-8.04-wide)
2009-05-09 21:02:13.479 Using the OpenGL painter
2009-05-09 21:02:13.479 JoystickMenuClient Error: Joystick disabled - Failed to read /home/mythbox/.mythtv/joystickmenurc
2009-05-09 21:02:13.481 lirc init success using configuration file: /home/mythbox/.mythtv/lircrc
2009-05-09 21:02:14.327 Specified base font 'medium' does not exist for font clock
2009-05-09 21:02:14.327 Specified base font 'medium' does not exist for font small
2009-05-09 21:02:14.327 Specified base font 'medium' does not exist for font medium
2009-05-09 21:02:14.327 Specified base font 'medium' does not exist for font large
2009-05-09 21:02:14.329 Loading from: /usr/share/mythtv/themes/Mythbuntu-8.04-wide/base.xml
2009-05-09 21:02:14.356 Loading from: /usr/share/mythtv/themes/default/base.xml
2009-05-09 21:02:14.405 Registering Internal as a media playback plugin.
2009-05-09 21:02:14.495 MonitorRegisterExtensions(0x100, gif,jpg,png)
2009-05-09 21:02:14.518 Failed to run 'cdrecord --scanbus'
2009-05-09 21:02:14.523 Failed to run 'cdrecord --scanbus -dev=ATA'
2009-05-09 21:02:14.530 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2009-05-09 21:02:14.573 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
2009-05-09 21:02:14.642 No theme dir: /home/mythbox/.mythtv/themes/Mythbuntu-8.04-wide
2009-05-09 21:02:15.168 Using NV NPOT texture extension
2009-05-09 21:02:22.400 XMLParse::LoadTheme using /usr/share/mythtv/themes/Mythbuntu-8.04-wide/ui.xml
2009-05-09 21:02:22.759 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-05-09 21:02:22.760 Using protocol version 40
2009-05-09 21:02:24.160 AFD: Opened codec 0x8544770, id(MPEG2VIDEO) type(Video)
2009-05-09 21:02:24.161 AFD: codec AC3 has 2 channels
2009-05-09 21:02:24.163 AFD: Opened codec 0x8544e90, id(AC3) type(Audio)
2009-05-09 21:02:24.163 AFD: codec AC3 has 2 channels
2009-05-09 21:02:24.164 AFD: Opened codec 0x852d170, id(AC3) type(Audio)
2009-05-09 21:02:24.164 AFD: codec AC3 has 2 channels
2009-05-09 21:02:24.166 AFD: Opened codec 0x8557990, id(AC3) type(Audio)
2009-05-09 21:02:25.388 AFD: Opened codec 0x85670c0, id(MPEG2VIDEO) type(Video)
2009-05-09 21:02:25.389 AFD: codec AC3 has 2 channels
2009-05-09 21:02:25.390 AFD: Opened codec 0x85659b0, id(AC3) type(Audio)
2009-05-09 21:02:25.390 AFD: codec AC3 has 2 channels
2009-05-09 21:02:25.391 AFD: Opened codec 0x8557d10, id(AC3) type(Audio)
2009-05-09 21:02:25.391 AFD: codec AC3 has 2 channels
2009-05-09 21:02:25.392 AFD: Opened codec 0x8565ea0, id(AC3) type(Audio)
2009-05-09 21:02:26.406 AFD: Opened codec 0x85670c0, id(MPEG2VIDEO) type(Video)
2009-05-09 21:02:26.406 AFD: codec AC3 has 6 channels
2009-05-09 21:02:26.407 AFD: Opened codec 0x852bc60, id(AC3) type(Audio)
2009-05-09 21:02:26.407 AFD: codec AC3 has 1 channels
2009-05-09 21:02:26.408 AFD: Opened codec 0x8557d10, id(AC3) type(Audio)
2009-05-09 21:02:26.791 TV: Attempting to change from None to WatchingPreRecorded
2009-05-09 21:02:26.811 DPMS Deactivated 
2009-05-09 21:02:27.005 AFD: Opened codec 0x8644e10, id(MPEG2VIDEO) type(Video)
2009-05-09 21:02:27.006 AFD: codec AC3 has 6 channels
2009-05-09 21:02:27.007 AFD: Opened codec 0x8569cd0, id(AC3) type(Audio)
2009-05-09 21:02:27.007 AFD: codec AC3 has 1 channels
2009-05-09 21:02:27.008 AFD: Opened codec 0x856a050, id(AC3) type(Audio)
2009-05-09 21:02:27.013 Opening audio device 'default'. ch 2(2) sr 48000
2009-05-09 21:02:27.013 Opening ALSA audio device 'default'.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
2009-05-09 21:02:27.667 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2009-05-09 21:02:27.866 OSD Theme Dimensions W: 640 H: 480
2009-05-09 21:02:28.336 TV: Changing from None to WatchingPreRecorded
2009-05-09 21:02:28.341 Realtime priority would require SUID as root.
2009-05-09 21:02:28.440 OpenGLVideoSync()
2009-05-09 21:02:28.488 Video sync method can't support double framerate (refresh rate too low for bob deint)
2009-05-09 21:02:28.493 Video timing method: SGI OpenGL
2009-05-09 21:02:28.540 AO: dropping back audio_buffer_unused
2009-05-09 21:02:28.582 AO: dropping back audio_buffer_unused
2009-05-09 21:02:28.639 AO: dropping back audio_buffer_unused
2009-05-09 21:02:28.696 AO: dropping back audio_buffer_unused
2009-05-09 21:02:28.727 AO: dropping back audio_buffer_unused
2009-05-09 21:02:28.759 AO: dropping back audio_buffer_unused
2009-05-09 21:02:28.790 AO: dropping back audio_buffer_unused
2009-05-09 21:02:28.821 AO: dropping back audio_buffer_unused
2009-05-09 21:02:28.852 AO: dropping back audio_buffer_unused
2009-05-09 21:02:28.883 AO: dropping back audio_buffer_unused
2009-05-09 21:02:28.914 AO: dropping back audio_buffer_unused
2009-05-09 21:02:28.945 AO: dropping back audio_buffer_unused
2009-05-09 21:02:28.951 AO: dropping back audio_buffer_unused
2009-05-09 21:02:28.982 AO: dropping back audio_buffer_unused
2009-05-09 21:02:30.828 TV: Attempting to change from WatchingPreRecorded to None
2009-05-09 21:02:30.835 ~OpenGLVideoSync() -- begin
2009-05-09 21:02:30.836 ~OpenGLVideoSync() -- middle
2009-05-09 21:02:30.836 ~OpenGLVideoSync() -- end

---

### Post by mtbdrew on 2009-05-10
bump

---

### Post by andrewc6l on 2009-05-11
Nothing too horrible in there, I'm afraid. You might want to try disabling "Enable OpenGL vertical sync for timing" (under Setup -> TV Settings -> Playback) and make sure you're using Qt as the paint engine (under Setup -> Appearance) just because the last thing that happened looked like an OpenGL thing... other than that, the log doesn't have much to go on.

---

### Post by mtbdrew on 2009-05-11
> **andrewc6l said:**
> Nothing too horrible in there, I'm afraid. You might want to try disabling "Enable OpenGL vertical sync for timing" (under Setup -> TV Settings -> Playback) and make sure you're using Qt as the paint engine (under Setup -> Appearance) just because the last thing that happened looked like an OpenGL thing... other than that, the log doesn't have much to go on.

I'll give that a try, though I had those settings with 8.10 and didn't have the early exit issue.

---

### Post by mtbdrew on 2009-05-13
Made those changes but still exits out to desktop early.

Any other things I can check?

---

### Post by mtbdrew on 2009-05-14
bump

---

