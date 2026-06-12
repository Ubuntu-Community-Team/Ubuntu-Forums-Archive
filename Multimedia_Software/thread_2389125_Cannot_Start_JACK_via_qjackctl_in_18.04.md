---
title: "Cannot Start JACK via qjackctl in 18.04"
date: 2018-04-11
forum: Multimedia Software
---

### Post by SlidingHorn on 2018-04-11
I'm running Ubuntu Studio 18.04, and when I attempt to start JACK using qjackctl, I get the following error (this is the same with or without using "pasuspend -- " before the server prefix setting)

```
17:28:53.166 Statistics reset.
17:28:53.180 ALSA connection change.
17:28:53.182 D-BUS: Service is available (org.jackaudio.service aka jackdbus).
Cannot connect to server socket err = Connection refused
Cannot connect to server request channel
jack server is not running or cannot be started
JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for -1, skipping unlock
JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for -1, skipping unlock
17:28:53.280 ALSA connection graph change.
qt.svg: /usr/share/icons/Faba/16x16/actions/dialog-ok.svg:112: Could not resolve property: linearGradient4205
qt.svg: /usr/share/icons/Faba/16x16/actions/dialog-ok.svg:112: Could not resolve property: linearGradient4205
qt.svg: /usr/share/icons/Faba/16x16/actions/dialog-ok.svg:112: Could not resolve property: linearGradient4205
qt.svg: /usr/share/icons/Faba/16x16/actions/dialog-ok.svg:112: Could not resolve property: linearGradient4205
qt.svg: /usr/share/icons/Faba/16x16/actions/dialog-ok.svg:112: Could not resolve property: linearGradient4205
17:30:58.751 D-BUS: JACK server could not be started. Sorry
Wed Apr 11 17:30:33 2018: Starting jack server...
Wed Apr 11 17:30:33 2018: JACK server starting in realtime mode with priority 10
Wed Apr 11 17:30:33 2018: self-connect-mode is "Don't restrict self connect requests"
Wed Apr 11 17:30:34 2018: Acquired audio card Audio3
Wed Apr 11 17:30:34 2018: creating alsa driver ... hw:Hea|hw:Hea|64|2|48000|0|0|nomon|swmeter|-|32bit
Wed Apr 11 17:30:34 2018: configuring for 48000Hz, period = 64 frames (1.3 ms), buffer = 2 periods
Wed Apr 11 17:30:34 2018: ALSA: final selected sample format for capture: 16bit little-endian
Wed Apr 11 17:30:34 2018: ALSA: use 2 periods for capture
Wed Apr 11 17:30:34 2018: ALSA: final selected sample format for playback: 16bit little-endian
Wed Apr 11 17:30:34 2018: ALSA: use 2 periods for playback
Wed Apr 11 17:30:39 2018: ERROR: JackPosixProcessSync::LockedTimedWait error usec = 5000000 err = Connection timed out
Wed Apr 11 17:30:39 2018: ERROR: Driver is not running
Wed Apr 11 17:30:39 2018: ERROR: Cannot open client name = dbusapi
Wed Apr 11 17:30:39 2018: ERROR: failed to create dbusapi jack client
Wed Apr 11 17:30:39 2018: ERROR: Unknown request 4294967295
Wed Apr 11 17:30:39 2018: ERROR: CheckSize error size = 0 Size() = 12
Wed Apr 11 17:30:39 2018: ERROR: CheckRead error
Cannot connect to server socket err = Connection refused
Cannot connect to server request channel
jack server is not running or cannot be started
JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for -1, skipping unlock
JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for -1, skipping unlock
17:31:23.702 Could not connect to JACK server as client. - Overall operation failed. - Server communication error. Please check the messages window for more info.
Cannot read socket fd = 30 err = Success
CheckRes error
JackSocketClientChannel read fail
Cannot open qjackctl client
JackShmReadWritePtr1::~JackShmReadWritePtr1 - Init not done for -1, skipping unlock
JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for -1, skipping unlock
JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for -1, skipping unlock
Wed Apr 11 17:31:23 2018: ERROR: JackPosixProcessSync::LockedTimedWait error usec = 5000000 err = Connection timed out
Wed Apr 11 17:31:23 2018: ERROR: Driver is not running
Wed Apr 11 17:31:23 2018: ERROR: Cannot create new client
Wed Apr 11 17:31:23 2018: ERROR: Unknown request 4294967295
Wed Apr 11 17:31:23 2018: ERROR: CheckSize error size = 0 Size() = 12
Wed Apr 11 17:31:23 2018: ERROR: CheckRead error
```

Any help in getting this running is greatly appreciated!  TIA


**EDIT:**  OvenWerks was able to help me figure this out in the #ubuntustudio IRC channel.  It appears that the USB driver/card combination I was using couldn't handle the 64 frame buffer I had set.  Changed it to 128, and everything started up.

---

