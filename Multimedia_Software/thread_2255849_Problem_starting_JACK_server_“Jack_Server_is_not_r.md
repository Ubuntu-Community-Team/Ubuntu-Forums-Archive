---
title: "Problem starting JACK server “Jack Server is not running or cannot be started”"
date: 2014-12-08
forum: Multimedia Software
---

### Post by rythem-pianoguy on 2014-12-08
Hello everyone! I am a professional pianist from New Delhi, India. I  had always been a fan of Linux over Windows. Since I'm a musician, I  downloaded some DAWs to try them out. I had read about JACK and that it  helps achieving low latency. But the problem is, I haven't been able to  get it to work despite googling and reading on forums. That's the only  reason I'm not satisfied and not able to fully adopt Linux.
 I  request all the experienced users and technicians, to please consider my  problem and help me getting JACK to work, because otherwise, it is  terrible to have high latency which makes recordings not feasible.
 I have also attached the message log of JACK Control here.
 I would really appreciate the help from you guys.

```
 [COLOR=#999999]12:33:48.414 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]12:33:48.418 Statistics reset.[/COLOR]
 [COLOR=#cccc99]12:33:48.431 ALSA connection change.[/COLOR]
 [COLOR=#999999]12:33:48.449 D-BUS: Service is available (org.jackaudio.service aka jackdbus).[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server request channel
 jack server is not running or cannot be started
 [COLOR=#66cc99]12:33:48.467 ALSA connection graph change.[/COLOR]
 [COLOR=#ff0000]12:33:56.858 D-BUS: JACK server could not be started. Sorry[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server request channel
 jack server is not running or cannot be started
 Mon Dec  8 12:33:56 2014: Starting jack server...
 Mon Dec  8 12:33:56 2014: JACK server starting in realtime mode with priority 10
 Mon Dec  8 12:33:56 2014: ERROR: Cannot lock down 82274202 byte memory area (Cannot allocate memory)
 Mon Dec  8 12:33:56 2014: Acquired audio card Audio0
 Mon Dec  8 12:33:56 2014: creating alsa driver ... hw:0|hw:0|256|2|44100|0|0|nomon|swmeter|-|32bit
 Mon Dec  8 12:33:56 2014: ERROR: ALSA: Cannot open PCM device alsa_pcm for playback. Falling back to capture-only mode
 Mon Dec  8 12:33:56 2014: ERROR: Cannot initialize driver
 Mon Dec  8 12:33:56 2014: ERROR: JackServer::Open failed with -1
 Mon Dec  8 12:33:56 2014: ERROR: Failed to open server
 Mon Dec  8 12:33:58 2014: Saving settings to "/home/rythem/.config/jack/conf.xml" ...
 [COLOR=#ff0000]12:34:00.147 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server request channel
 jack server is not running or cannot be started
 Mon Dec  8 12:40:53 2014: Starting jack server...
 Mon Dec  8 12:40:53 2014: JACK server starting in realtime mode with priority 10
 Mon Dec  8 12:40:53 2014: ERROR: Cannot lock down 82274202 byte memory area (Cannot allocate memory)
 Mon Dec  8 12:40:53 2014: ERROR: cannot register object path "/org/freedesktop/ReserveDevice1/Audio0": A handler is already registered for /org/freedesktop/ReserveDevice1/Audio0
 Mon Dec  8 12:40:53 2014: ERROR: Failed to acquire device name : Audio0 error : A handler is already registered for /org/freedesktop/ReserveDevice1/Audio0
 Mon Dec  8 12:40:53 2014: ERROR: Audio device hw:0 cannot be acquired...
 Mon Dec  8 12:40:53 2014: ERROR: Cannot initialize driver
 Mon Dec  8 12:40:53 2014: ERROR: JackServer::Open failed with -1
 Mon Dec  8 12:40:53 2014: ERROR: Failed to open server
 [COLOR=#ff0000]12:49:37.936 D-BUS: JACK server could not be started. Sorry[/COLOR]
 [COLOR=#ff0000]Cannot connect to server socket err = No such file or directory[/COLOR]
 [COLOR=#ff0000]Cannot connect to server request channel[/COLOR]
 [COLOR=#ff0000]jack server is not running or cannot be started[/COLOR]
 [COLOR=#ff0000]Mon Dec  8 12:49:37 2014: Starting jack server...[/COLOR]
 [COLOR=#ff0000]Mon Dec  8 12:49:37 2014: JACK server starting in realtime mode with priority 10[/COLOR]
 [COLOR=#ff0000]Mon Dec  8 12:49:37 2014: ERROR: Cannot lock down 82274202 byte memory area (Cannot allocate memory)[/COLOR]
 [COLOR=#ff0000]Mon Dec  8 12:49:37 2014: ERROR: cannot register object path "/org/freedesktop/ReserveDevice1/Audio0": A handler is already registered for /org/freedesktop/ReserveDevice1/Audio0[/COLOR]
 [COLOR=#ff0000]Mon Dec  8 12:49:37 2014: ERROR: Failed to acquire device name : Audio0 error : A handler is already registered for /org/freedesktop/ReserveDevice1/Audio0[/COLOR]
 [COLOR=#ff0000]Mon Dec  8 12:49:37 2014: ERROR: Audio device hw:0 cannot be acquired...[/COLOR]
 [COLOR=#ff0000]Mon Dec  8 12:49:37 2014: ERROR: Cannot initialize driver[/COLOR]
 [COLOR=#ff0000]Mon Dec  8 12:49:37 2014: ERROR: JackServer::Open failed with -1[/COLOR]
 [COLOR=#ff0000]Mon Dec  8 12:49:37 2014: ERROR: Failed to open server[/COLOR]
 [COLOR=#ff0000]Mon Dec  8 12:49:39 2014: Saving settings to "/home/rythem/.config/jack/conf.xml" ...[/COLOR]
 [COLOR=#ff0000]12:49:41.563 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]
 [COLOR=#ff0000]Cannot connect to server socket err = No such file or directory[/COLOR]
 [COLOR=#ff0000]Cannot connect to server request channel[/COLOR]
 [COLOR=#ff0000]jack server is not running or cannot be started[/COLOR]


```

---

