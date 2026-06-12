---
title: "I dont know jack"
date: 2013-11-26
forum: Multimedia Software
---

### Post by leeper69 on 2013-11-26
Hi I am trying to get jack to run in ubuntu studio 13.10 I looked a a few posts and have installed ubuntustudio-audio which gets QjackCtl installed only to get the following message when trying to start it.```
12:01:19.544 Patchbay deactivated.
12:01:19.713 Statistics reset.
12:01:19.802 ALSA connection change.
12:01:19.903 D-BUS: Service is available (org.jackaudio.service aka jackdbus).
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
12:01:19.918 ALSA connection graph change.
12:01:50.927 D-BUS: JACK server could not be started. Sorry
Tue Nov 26 12:01:50 2013: Starting jack server...
Tue Nov 26 12:01:50 2013: JACK server starting in realtime mode with priority 10
Tue Nov 26 12:01:50 2013: Acquired audio card Audio0
Tue Nov 26 12:01:50 2013: creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit
Tue Nov 26 12:01:50 2013: ERROR: ALSA: Cannot open PCM device alsa_pcm for playback. Falling back to capture-only mode
Tue Nov 26 12:01:50 2013: ERROR: Cannot initialize driver
Tue Nov 26 12:01:50 2013: ERROR: JackServer::Open failed with -1
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
Tue Nov 26 12:01:50 2013: ERROR: Failed to open server
Tue Nov 26 12:01:52 2013: Saving settings to "/home/us/.config/jack/conf.xml" ...
12:02:03.069 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
```

---

### Post by leeper69 on 2013-11-26
from the output above I can see that the driver for jack is not working, but what to do from there.
I found a good url that explains why jack wont start in ubuntu it seems jack and pulseaudio dont play well together.
[http://www.jackaudio.org/pulseaudio_and_jack](http://www.jackaudio.org/pulseaudio_and_jack)
I have another sound card and the next time I shut down my system I will give it a shot.
has anyone got jack working in ubuntu studio?

---

### Post by leeper69 on 2013-12-09
Hi everyone I enabled my onboard sound card and installed ubuntu studio 13.10 and now i have two sound cards enabled the sound blaster card is tyed to pulse audio and the intel built in card is tyed to alsa and i now have jack.

---

