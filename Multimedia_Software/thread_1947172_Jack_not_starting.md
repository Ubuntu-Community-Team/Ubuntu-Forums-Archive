---
title: "Jack not starting"
date: 2012-03-26
forum: Multimedia Software
---

### Post by LCWyche on 2012-03-26
Unable to start Jack
Hi!
Have just clean installed Ubuntu studio 64 11.10. When I start Ardour this message appears:

'Ardour could not start JACK
There are several possible reasons:
1) You requested audio parameters that are not supported..
2) JACK is running as another user.
Please consider the possibilities, and perhaps try different parameters.'

This is what happens when I run qjackctl:
Wed Mar 21 16:43:47 2012: Saving settings to "/home/laurence/.config/jack/conf.xml" ...
Wed Mar 21 16:43:47 2012: Saving settings to "/home/laurence/.config/jack/conf.xml" ...
Wed Mar 21 16:43:47 2012: Starting jack server...
Wed Mar 21 16:43:47 2012: JACK server starting in realtime mode with priority 10
Wed Mar 21 16:43:47 2012: [1m[31mERROR: Cannot lock down memory area (Cannot allocate memory)[0m
Wed Mar 21 16:43:47 2012: control device hw:0
Wed Mar 21 16:43:47 2012: control device hw:0
Wed Mar 21 16:43:47 2012: Acquired audio card Audio0
Wed Mar 21 16:43:47 2012: creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit
Wed Mar 21 16:43:47 2012: con [sorry my bad]
Wed Mar 21 16:43:47 2012: configuring for 44100Hz, period = 1024 frames (23.2 ms), buffer = 2 periods
Wed Mar 21 16:43:47 2012: ALSA: final selected sample format for capture: 32bit integer little-endian
Wed Mar 21 16:43:47 2012: ALSA: use 2 periods for capture
Wed Mar 21 16:43:47 2012: ALSA: final selected sample format for playback: 32bit integer little-endian
Wed Mar 21 16:43:47 2012: ALSA: use 2 periods for playback
Wed Mar 21 16:43:47 2012: [1m[31mERROR: Cannot use real-time scheduling (RR/10)(1: Operation not permitted)[0m
Wed Mar 21 16:43:47 2012: [1m[31mERROR: AcquireSelfRealTime error[0m
Wed Mar 21 16:43:52 2012: [1m[31mERROR: JackProcessSync::LockedTimedWait error usec = 5000000 err = Connection timed out[0m
Wed Mar 21 16:43:52 2012: [1m[31mERROR: Driver is not running[0m
Wed Mar 21 16:43:52 2012: [1m[31mERROR: Cannot open client name = dbusapi[0m
Wed Mar 21 16:43:52 2012: [1m[31mERROR: failed to create dbusapi jack client[0m
Cannot connect to server socket err = Connection refused
Cannot connect to server socket
jack server is not running or cannot be started

Then I am informed that "Jack will continue to run in the system 
tray".


Help!

---

