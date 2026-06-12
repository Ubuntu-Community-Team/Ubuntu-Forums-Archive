---
title: "JACK not working with USB audio interface"
date: 2017-04-06
forum: Multimedia Software
---

### Post by jabrilm on 2017-04-06
I have a Steinberg USB audio interface (model: UR12), and am using Ubuntu 16.04 on an HP laptop. When I try to start JACK, using qjackctl, I get the popup message "D-BUS: Jack Server could not be started" followed by "Could not connect to Jack server as client."

The qjackctl messages window gives much more detailed info, shown below at bottom.

On my desktop machine, it all works, with nearly the same setup (same UR12 interface, same version of Ubuntu, also using qjackctl). 

Other threads from the past suggest that it could be a pulseaudio problem, but I've tried the various solutions and it has not made a difference. For example, killing pulseaudio and forcing it not to spawn, and using pasuspender -- before the JACK server in qjackctl setup.

Any other suggestions? Do the error messages indicate that it's likely a pulseaudio problem, or something else?

You can see that the first two error messages have to do with ALSA configuring playback. 

Detailed error messages:

 
```
09:32:31.681 Statistics reset.
09:32:31.753 ALSA connection change.
09:32:32.307 D-BUS: Service is available (org.jackaudio.service aka jackdbus).
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for -1, skipping unlock
JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for -1, skipping unlock
09:32:32.351 ALSA connection graph change.
09:33:04.315 D-BUS: JACK server could not be started. Sorry
Thu Apr  6 09:33:04 2017: Starting jack server...
Thu Apr  6 09:33:04 2017: JACK server starting in realtime mode with priority 10
Thu Apr  6 09:33:04 2017: self-connect-mode is "Don't restrict self connect requests"
Thu Apr  6 09:33:04 2017: Acquired audio card Audio3
Thu Apr  6 09:33:04 2017: creating alsa driver ... hw:UR12|hw:UR12|1024|2|44100|0|0|nomon|swmeter|-|32bit
Thu Apr  6 09:33:04 2017: Using ALSA driver USB-Audio running on card 3 - Yamaha Corporation Steinberg UR12 at usb-0000:00:10.0-2.1, high speed
Thu Apr  6 09:33:04 2017: configuring for 44100Hz, period = 1024 frames (23.2 ms), buffer = 2 periods
Thu Apr  6 09:33:04 2017: ALSA: final selected sample format for capture: 32bit integer little-endian
Thu Apr  6 09:33:04 2017: ALSA: use 2 periods for capture
Thu Apr  6 09:33:04 2017: ALSA: final selected sample format for playback: 32bit integer little-endian
Thu Apr  6 09:33:04 2017: ALSA: use 2 periods for playback
Thu Apr  6 09:33:04 2017: ERROR: ALSA: cannot set hardware parameters for playback
Thu Apr  6 09:33:04 2017: ERROR: ALSA: cannot configure playback channel
Thu Apr  6 09:33:04 2017: Released audio card Audio3
Thu Apr  6 09:33:04 2017: ERROR: Cannot initialize driver
Thu Apr  6 09:33:04 2017: ERROR: JackServer::Open failed with -1
Thu Apr  6 09:33:04 2017: ERROR: Failed to open server
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for -1, skipping unlock
JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for -1, skipping unlock
Thu Apr  6 09:33:05 2017: Saving settings to "/home/gabrielm/.config/jack/conf.xml" ...
09:33:26.257 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for -1, skipping unlock
JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for -1, skipping unlock
09:39:45.955 D-BUS: JACK server could not be started. Sorry
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for -1, skipping unlock
JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for -1, skipping unlock
Thu Apr  6 09:39:45 2017: Starting jack server...
Thu Apr  6 09:39:45 2017: JACK server starting in realtime mode with priority 10
Thu Apr  6 09:39:45 2017: self-connect-mode is "Don't restrict self connect requests"
Thu Apr  6 09:39:45 2017: Acquired audio card Audio3
Thu Apr  6 09:39:45 2017: creating alsa driver ... hw:UR12|hw:UR12|1024|2|44100|0|0|nomon|swmeter|-|32bit
Thu Apr  6 09:39:45 2017: Using ALSA driver USB-Audio running on card 3 - Yamaha Corporation Steinberg UR12 at usb-0000:00:10.0-2.1, high speed
Thu Apr  6 09:39:45 2017: configuring for 44100Hz, period = 1024 frames (23.2 ms), buffer = 2 periods
Thu Apr  6 09:39:45 2017: ALSA: final selected sample format for capture: 32bit integer little-endian
Thu Apr  6 09:39:45 2017: ALSA: use 2 periods for capture
Thu Apr  6 09:39:45 2017: ALSA: final selected sample format for playback: 32bit integer little-endian
Thu Apr  6 09:39:45 2017: ALSA: use 2 periods for playback
Thu Apr  6 09:39:45 2017: ERROR: ALSA: cannot set hardware parameters for playback
Thu Apr  6 09:39:45 2017: ERROR: ALSA: cannot configure playback channel
Thu Apr  6 09:39:45 2017: Released audio card Audio3
Thu Apr  6 09:39:45 2017: ERROR: Cannot initialize driver
Thu Apr  6 09:39:45 2017: ERROR: JackServer::Open failed with -1
Thu Apr  6 09:39:45 2017: ERROR: Failed to open server
Thu Apr  6 09:39:47 2017: Saving settings to "/home/gabrielm/.config/jack/conf.xml" ...
09:40:24.814 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for -1, skipping unlock
JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for -1, skipping unlock
```


EDIT with further information:

If I go into alsamixer and select my UR12 sound card, I get the message "this sound device does not have any controls." However, I get the same message from alsamixer on my desktop machine, where it does work.

For comparison, here is the qjackctl messages output when using the UR12 device on my desktop machine, where it does work:

  ```
10:04:30.145 Statistics reset.
10:04:30.219 ALSA connection change.
10:04:30.642 D-BUS: Service is available (org.jackaudio.service aka jackdbus).
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for 4294967295, skipping unlock
JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for 4294967295, skipping unlock
10:04:30.734 ALSA connection graph change.
10:04:30.872 ALSA active patchbay scan...
10:04:38.486 D-BUS: JACK server is starting...
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for 4294967295, skipping unlock
JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for 4294967295, skipping unlock
10:04:38.543 D-BUS: JACK server was started (org.jackaudio.service aka jackdbus).
Thu Apr  6 10:04:38 2017: Starting jack server...
Thu Apr  6 10:04:38 2017: JACK server starting in realtime mode with priority 10
Thu Apr  6 10:04:38 2017: self-connect-mode is "Don't restrict self connect requests"
Thu Apr  6 10:04:38 2017: Acquired audio card Audio2
Thu Apr  6 10:04:38 2017: creating alsa driver ... hw:UR12|hw:UR12|1024|2|44100|0|0|nomon|swmeter|-|32bit
Thu Apr  6 10:04:38 2017: configuring for 44100Hz, period = 1024 frames (23.2 ms), buffer = 2 periods
Thu Apr  6 10:04:38 2017: ALSA: final selected sample format for capture: 32bit integer little-endian
Thu Apr  6 10:04:38 2017: ALSA: use 2 periods for capture
Thu Apr  6 10:04:38 2017: ALSA: final selected sample format for playback: 32bit integer little-endian
Thu Apr  6 10:04:38 2017: ALSA: use 2 periods for playback
Thu Apr  6 10:04:38 2017: graph reorder: new port 'system:capture_1'
Thu Apr  6 10:04:38 2017: New client 'system' with PID 0
Thu Apr  6 10:04:38 2017: graph reorder: new port 'system:capture_2'
Thu Apr  6 10:04:38 2017: graph reorder: new port 'system:playback_1'
Thu Apr  6 10:04:38 2017: graph reorder: new port 'system:playback_2'
10:04:40.610 JACK connection change.
10:04:40.611 Server configuration saved to "/home/gabrielm/.jackdrc".
10:04:40.612 Statistics reset.
10:04:40.622 Client activated.
10:04:40.622 Patchbay activated.
10:04:40.624 JACK active patchbay scan...
10:04:40.625 ALSA active patchbay scan...
10:04:40.708 JACK connection graph change.
Thu Apr  6 10:04:39 2017: Saving settings to "/home/gabrielm/.config/jack/conf.xml" ...
Thu Apr  6 10:04:40 2017: New client 'qjackctl' with PID 7324
10:04:40.853 JACK active patchbay scan...
```

I see this difference in the outputs. 

On my laptop, where JACK does not work with the UR12 device:

 ```
Thu Apr 6 09:33:04 2017: creating alsa driver ... hw:UR12|hw:UR12|1024|2|44100|0|0|nomon|swmeter|-|32bit
Thu Apr 6 09:33:04 2017: Using ALSA driver USB-Audio running on card 3 - Yamaha Corporation Steinberg UR12 at usb-0000:00:10.0-2.1, high speed
Thu Apr 6 09:33:04 2017: configuring for 44100Hz, period = 1024 frames (23.2 ms), buffer = 2 periods
```

On my desktop, where JACK does work with the UR12 device:

```
Thu Apr 6 10:04:38 2017: Acquired audio card Audio2
Thu Apr 6 10:04:38 2017: creating alsa driver ... hw:UR12|hw:UR12|1024|2|44100|0|0|nomon|swmeter|-|32bit
Thu Apr 6 10:04:38 2017: configuring for 44100Hz, period = 1024 frames (23.2 ms), buffer = 2 periods

```

It looks like my on my laptop, ALSA is using a driver from the Steinberg UR12, and on the desktop it is not. If I am interpreting that correctly, a) could that be the source of the problem, and b) if so, how do I tell ALSA not to use that driver in the first case?

It was an easy solution. My laptop has both USB 2.0 and USB 3.0 ports. I had to switch to 3.0 and it works fine. Hope this saves somebody else hours of time!

---

