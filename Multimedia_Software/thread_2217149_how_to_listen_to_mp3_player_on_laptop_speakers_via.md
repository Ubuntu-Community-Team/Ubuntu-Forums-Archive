---
title: "how to listen to mp3 player on laptop speakers via microphone jack"
date: 2014-04-15
forum: Multimedia Software
---

### Post by poikiloid on 2014-04-15
I have already tried jackd.
It did not find anything in the "audio" tab of the connections dialog...

Got these error in the messages window:
```
18:32:24.040 Patchbay deactivated.
18:32:24.043 Statistics reset.
18:32:24.162 ALSA connection change.
18:32:26.353 D-BUS: Service is available (org.jackaudio.service aka jackdbus).
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
18:32:26.360 ALSA connection graph change.
18:34:22.985 D-BUS: JACK server could not be started. Sorry
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
Tue Apr 15 18:34:22 2014: Starting jack server...
Tue Apr 15 18:34:22 2014: JACK server starting in non-realtime mode
Tue Apr 15 18:34:22 2014: ERROR: Cannot lock down 82274202 byte memory area (Cannot allocate memory)
Tue Apr 15 18:34:22 2014: Acquired audio card Audio0
Tue Apr 15 18:34:22 2014: creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit
Tue Apr 15 18:34:22 2014: ERROR: ALSA: Cannot open PCM device alsa_pcm for playback. Falling back to capture-only mode
Tue Apr 15 18:34:22 2014: ERROR: Cannot initialize driver
Tue Apr 15 18:34:22 2014: ERROR: JackServer::Open failed with -1
Tue Apr 15 18:34:22 2014: ERROR: Failed to open server
Tue Apr 15 18:34:24 2014: Saving settings to "/home/erik/.config/jack/conf.xml" ...
18:34:31.804 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
```

Any ideas, or alternative to JACKD??

---

