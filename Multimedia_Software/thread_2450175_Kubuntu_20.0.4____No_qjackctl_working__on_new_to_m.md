---
title: "Kubuntu 20.0.4    No qjackctl working  on new to me lenovo t440s"
date: 2020-09-08
forum: Multimedia Software
---

### Post by Dirk_Ouellette on 2020-09-08
Now I admit that I took this hdd out of another lenovo laptop and stuck it in this new to me laptop; runs fine, just no jack.

```
18:48:21.114 Statistics reset.

 18:48:21.205 ALSA connection change.

 18:48:21.946 D-BUS: Service is available (org.jackaudio.service aka jackdbus).
 18:48:21.959 Startup script...
 18:48:21.959 a2jmidid -e &
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server request channel
 jack server is not running or cannot be started
 JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for -1, skipping unlock
 JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for -1, skipping unlock
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server request channel
 jack server is not running or cannot be started
 JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for -1, skipping unlock
 JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for -1, skipping unlock
 18:48:22.127 ALSA connection graph change.
 JACK MIDI <-> ALSA sequencer MIDI bridge, version 9 built on Wed Dec 31 16:00:00 1969
 Copyright 2006,2007 Dmitry S. Baikov
 Copyright 2007,2008,2009,2011,2012 Nedko Arnaudov
 Bridge starting...
 Using JACK server 'default'
 Hardware ports will be exported.
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server request channel
 jack server is not running or cannot be started
 JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for -1, skipping unlock
 JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for -1, skipping unlock
 [31mERROR: [0ma2j_jack_client_create: Cannot create jack client
 [31mERROR: [0ma2j_start: a2j_new() failed.
 18:48:22.359 Startup script terminated successfully.
 18:48:22.397 D-BUS: JACK server could not be started. Sorry
 18:48:22.599 ALSA active patchbay scan...
 Tue Sep  8 18:48:22 2020: Starting jack server...
 Tue Sep  8 18:48:22 2020: JACK server starting in realtime mode with priority 10
 Tue Sep  8 18:48:22 2020: self-connect-mode is "Don't restrict self connect requests"
 Tue Sep  8 18:48:22 2020: ERROR: Cannot lock down 82280346 byte memory area (Cannot allocate memory)
 Tue Sep  8 18:48:22 2020: ERROR: control open "hw:USB" (No such device)
 Tue Sep  8 18:48:22 2020: ERROR: control open "hw:USB" (No such device)
 Tue Sep  8 18:48:22 2020: creating alsa driver ... hw:USB|hw:USB|1024|2|44100|4|4|hwmon|hwmeter|-|32bit
 Tue Sep  8 18:48:22 2020: ERROR: control open "hw:USB" (No such device)
 Tue Sep  8 18:48:22 2020: ERROR: ALSA: Cannot open PCM device alsa_pcm for playback. Falling back to capture-only mode
 Tue Sep  8 18:48:22 2020: ERROR: control open "hw:USB" (No such device)
 Tue Sep  8 18:48:22 2020: ERROR: control open "hw:USB" (No such device)
 Tue Sep  8 18:48:22 2020: ERROR: Cannot initialize driver
 Tue Sep  8 18:48:22 2020: ERROR: JackServer::Open failed with -1
 Tue Sep  8 18:48:22 2020: ERROR: Failed to open server
 Tue Sep  8 18:48:23 2020: Saving settings to "/home/dirk/.config/jack/conf.xml" ...
 18:48:24.610 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server request channel
 jack server is not running or cannot be started
 JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for -1, skipping unlock
 JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for -1, skipping unlock
 18:50:17.385 Startup script...
 18:50:17.385 a2jmidid -e &
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server request channel
 jack server is not running or cannot be started
 JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for -1, skipping unlock
 JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for -1, skipping unlock
 JACK MIDI <-> ALSA sequencer MIDI bridge, version 9 built on Wed Dec 31 16:00:00 1969
 Copyright 2006,2007 Dmitry S. Baikov
 Copyright 2007,2008,2009,2011,2012 Nedko Arnaudov
 Bridge starting...
 Using JACK server 'default'
 Hardware ports will be exported.
 18:50:17.594 ALSA connection graph change.
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server request channel
 jack server is not running or cannot be started
 JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for -1, skipping unlock
 JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for -1, skipping unlock
 [31mERROR: [0ma2j_jack_client_create: Cannot create jack client
 [31mERROR: [0ma2j_start: a2j_new() failed.
 18:50:17.670 ALSA active patchbay scan...
 18:50:17.786 Startup script terminated successfully.
 18:50:17.824 D-BUS: JACK server could not be started. Sorry
 Tue Sep  8 18:50:17 2020: Starting jack server...
 Tue Sep  8 18:50:17 2020: JACK server starting in realtime mode with priority 10
 Tue Sep  8 18:50:17 2020: self-connect-mode is "Don't restrict self connect requests"
 Tue Sep  8 18:50:17 2020: ERROR: Cannot lock down 82280346 byte memory area (Cannot allocate memory)
 Tue Sep  8 18:50:17 2020: ERROR: control open "hw:USB" (No such device)
 Tue Sep  8 18:50:17 2020: ERROR: control open "hw:USB" (No such device)
 Tue Sep  8 18:50:17 2020: creating alsa driver ... hw:USB|hw:USB|1024|2|44100|4|4|hwmon|hwmeter|-|32bit
 Tue Sep  8 18:50:17 2020: ERROR: control open "hw:USB" (No such device)
 Tue Sep  8 18:50:17 2020: ERROR: ALSA: Cannot open PCM device alsa_pcm for playback. Falling back to capture-only mode
 Tue Sep  8 18:50:17 2020: ERROR: control open "hw:USB" (No such device)
 Tue Sep  8 18:50:17 2020: ERROR: control open "hw:USB" (No such device)
 Tue Sep  8 18:50:17 2020: ERROR: Cannot initialize driver
 Tue Sep  8 18:50:17 2020: ERROR: JackServer::Open failed with -1
 Tue Sep  8 18:50:17 2020: ERROR: Failed to open server
 18:50:19.884 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server request channel
 jack server is not running or cannot be started
 JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for -1, skipping unlock
 JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for -1, skipping unlock
 Tue Sep  8 18:50:19 2020: Saving settings to "/home/dirk/.config/jack/conf.xml" ...
 18:52:12.962 Startup script...
 18:52:12.963 a2jmidid -e &
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server request channel
 jack server is not running or cannot be started
 JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for -1, skipping unlock
 JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for -1, skipping unlock
 JACK MIDI <-> ALSA sequencer MIDI bridge, version 9 built on Wed Dec 31 16:00:00 1969
 Copyright 2006,2007 Dmitry S. Baikov
 Copyright 2007,2008,2009,2011,2012 Nedko Arnaudov
 Bridge starting...
 Using JACK server 'default'
 Hardware ports will be exported.
 18:52:13.170 ALSA connection graph change.
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server request channel
 jack server is not running or cannot be started
 JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for -1, skipping unlock
 JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for -1, skipping unlock
 [31mERROR: [0ma2j_jack_client_create: Cannot create jack client
 [31mERROR: [0ma2j_start: a2j_new() failed.
 18:52:13.258 ALSA active patchbay scan...
 18:52:13.363 Startup script terminated successfully.
 18:52:13.398 D-BUS: JACK server could not be started. Sorry
 Tue Sep  8 18:52:13 2020: Starting jack server...
 Tue Sep  8 18:52:13 2020: JACK server starting in realtime mode with priority 10
 Tue Sep  8 18:52:13 2020: self-connect-mode is "Don't restrict self connect requests"
 Tue Sep  8 18:52:13 2020: ERROR: Cannot lock down 82280346 byte memory area (Cannot allocate memory)
 Tue Sep  8 18:52:13 2020: ERROR: control open "hw:USB" (No such device)
 Tue Sep  8 18:52:13 2020: ERROR: control open "hw:USB" (No such device)
 Tue Sep  8 18:52:13 2020: creating alsa driver ... hw:USB|hw:USB|1024|2|44100|4|4|hwmon|hwmeter|-|32bit
 Tue Sep  8 18:52:13 2020: ERROR: control open "hw:USB" (No such device)
 Tue Sep  8 18:52:13 2020: ERROR: ALSA: Cannot open PCM device alsa_pcm for playback. Falling back to capture-only mode
 Tue Sep  8 18:52:13 2020: ERROR: control open "hw:USB" (No such device)
 Tue Sep  8 18:52:13 2020: ERROR: control open "hw:USB" (No such device)
 Tue Sep  8 18:52:13 2020: ERROR: Cannot initialize driver
 Tue Sep  8 18:52:13 2020: ERROR: JackServer::Open failed with -1
 Tue Sep  8 18:52:13 2020: ERROR: Failed to open server
 Tue Sep  8 18:52:14 2020: Saving settings to "/home/dirk/.config/jack/conf.xml" ...
 18:52:15.470 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server request channel
 jack server is not running or cannot be started
 JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for -1, skipping unlock
 JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for -1, skipping unlock
 18:54:41.536 Startup script...
 18:54:41.537 a2jmidid -e &
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server request channel
 jack server is not running or cannot be started
 JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for -1, skipping unlock
 JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for -1, skipping unlock
 JACK MIDI <-> ALSA sequencer MIDI bridge, version 9 built on Wed Dec 31 16:00:00 1969
 Copyright 2006,2007 Dmitry S. Baikov
 Copyright 2007,2008,2009,2011,2012 Nedko Arnaudov
 Bridge starting...
 Using JACK server 'default'
 Hardware ports will be exported.
 18:54:41.745 ALSA connection graph change.
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server request channel
 jack server is not running or cannot be started
 JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for -1, skipping unlock
 JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for -1, skipping unlock
 [31mERROR: [0ma2j_jack_client_create: Cannot create jack client
 [31mERROR: [0ma2j_start: a2j_new() failed.
 18:54:41.894 ALSA active patchbay scan...
 18:54:41.938 Startup script terminated successfully.
 18:54:41.974 D-BUS: JACK server could not be started. Sorry
 Tue Sep  8 18:54:41 2020: Starting jack server...
 Tue Sep  8 18:54:41 2020: JACK server starting in realtime mode with priority 10
 Tue Sep  8 18:54:41 2020: self-connect-mode is "Don't restrict self connect requests"
 Tue Sep  8 18:54:41 2020: ERROR: Cannot lock down 82280346 byte memory area (Cannot allocate memory)
 Tue Sep  8 18:54:41 2020: ERROR: control open "hw:USB" (No such device)
 Tue Sep  8 18:54:41 2020: ERROR: control open "hw:USB" (No such device)
 Tue Sep  8 18:54:41 2020: creating alsa driver ... hw:USB|hw:USB|1024|2|44100|4|4|hwmon|hwmeter|-|32bit
 Tue Sep  8 18:54:41 2020: ERROR: control open "hw:USB" (No such device)
 Tue Sep  8 18:54:41 2020: ERROR: ALSA: Cannot open PCM device alsa_pcm for playback. Falling back to capture-only mode
 Tue Sep  8 18:54:41 2020: ERROR: control open "hw:USB" (No such device)
 Tue Sep  8 18:54:41 2020: ERROR: control open "hw:USB" (No such device)
 Tue Sep  8 18:54:41 2020: ERROR: Cannot initialize driver
 Tue Sep  8 18:54:41 2020: ERROR: JackServer::Open failed with -1
 Tue Sep  8 18:54:41 2020: ERROR: Failed to open server
 Tue Sep  8 18:54:43 2020: Saving settings to "/home/dirk/.config/jack/conf.xml" ...
 18:54:44.108 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server request channel
 jack server is not running or cannot be started
 JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for -1, skipping unlock
 JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for -1, skipping unlock
```

---

### Post by Autodave on 2020-09-11
Since no one else has jumped in, let me give you my idea.  I would uninstall it and then reinstall.  If possible, I would use the old laptop to uninstall.  My guess is that the sound card is different from one machine to the other and that is why it is not working: it is either looking for the wrong card or looking in the wrong place.

---

