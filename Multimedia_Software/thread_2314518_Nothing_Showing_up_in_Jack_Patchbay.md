---
title: "Nothing Showing up in Jack Patchbay"
date: 2016-02-21
forum: Multimedia Software
---

### Post by big-t-gor on 2016-02-21
I've used Ubuntu before and I have had Jack working without any problem but with these computer I can't seem to get it working right. Nothing shows up in the QJackCTL patchbay at all. I have no idea what I could be doing wrong the last time I used it it worked straight away.

 ```
16:51:38.977 Patchbay deactivated.
 16:51:38.978 Statistics reset.
 16:51:38.982 ALSA connection change.
 16:51:38.988 D-BUS: Service is available (org.jackaudio.service aka jackdbus).
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server request channel
 jack server is not running or cannot be started
 16:51:38.996 ALSA connection graph change.
 16:51:43.969 D-BUS: JACK server is starting...
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server request channel
 jack server is not running or cannot be started
 16:51:43.987 D-BUS: JACK server was started (org.jackaudio.service aka jackdbus).
 Sun Feb 21 16:51:43 2016: Starting jack server...
 Sun Feb 21 16:51:43 2016: JACK server starting in realtime mode with priority 10
 Sun Feb 21 16:51:43 2016: Acquired audio card Audio0
 Sun Feb 21 16:51:43 2016: creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit
 Sun Feb 21 16:51:43 2016: configuring for 44100Hz, period = 1024 frames (23.2 ms), buffer = 2 periods
 Sun Feb 21 16:51:43 2016: ALSA: final selected sample format for capture: 32bit integer little-endian
 Sun Feb 21 16:51:43 2016: ALSA: use 2 periods for capture
 Sun Feb 21 16:51:43 2016: ALSA: final selected sample format for playback: 32bit integer little-endian
 Sun Feb 21 16:51:43 2016: ALSA: use 2 periods for playback
 Sun Feb 21 16:51:43 2016: graph reorder: new port 'system:capture_1'
 Sun Feb 21 16:51:43 2016: New client 'system' with PID 0
 Sun Feb 21 16:51:43 2016: graph reorder: new port 'system:capture_2'
 Sun Feb 21 16:51:43 2016: graph reorder: new port 'system:playback_1'
 Sun Feb 21 16:51:43 2016: graph reorder: new port 'system:playback_2'
 Sun Feb 21 16:51:43 2016: graph reorder: new port 'system:playback_3'
 Sun Feb 21 16:51:43 2016: graph reorder: new port 'system:playback_4'
 Sun Feb 21 16:51:45 2016: Saving settings to "/home/tyrone/.config/jack/conf.xml" ...
 16:51:46.240 JACK connection change.
 16:51:46.242 Server configuration saved to "/home/tyrone/.jackdrc".
 16:51:46.243 Statistics reset.
 16:51:46.269 Client activated.
 16:51:46.300 JACK connection graph change.
 Sun Feb 21 16:51:46 2016: New client 'qjackctl' with PID 3557
```

This is the message out log is when I start it up.

---

### Post by Bucky Ball on 2016-02-22
*Thread moved to **Multimedia Software**.*

Welcome. Although you are new to the forums, you are not new to Ubuntu so you will have a much better chance of getting help with JACK here. If there's anything you don't understand, as always round here, just ask. 

Probably going to need a lot more info about your system and setup. What hardware do you have connected and what are you expecting to see in JACK? 

Generally, you launch JACK first, launch what you are going to use with it, say Ardour, then start and check the Jack setup if it starts OK. 

Good luck. :)

---

