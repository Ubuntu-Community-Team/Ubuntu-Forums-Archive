---
title: "Problems with Jack"
date: 2018-12-27
forum: Multimedia Software
---

### Post by eufex1 on 2018-12-27
Hi
Fresh install of Ubuntu Studio 18.1 and cannot get Jack to run - I've done a test build on my laptop (different hardware natch) and it's OK.
However, on the desktop it just will not work.
Internal audio is working with PulseAudio but internal audio won't work with Jack. what also won't work with Jack is my firewire interface which does work fine with the laptop.

Looking at the logs from QJack CTL I get:

```
17:59:01.799 Statistics reset.
17:59:01.811 ALSA connection change.
17:59:01.813 D-BUS: Service is available (org.jackaudio.service aka jackdbus).
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server request channel
 jack server is not running or cannot be started
 JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for -1, skipping unlock
 JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for -1, skipping unlock
17:59:01.850 ALSA connection graph change.
17:59:09.031 D-BUS: JACK server could not be started. Sorry
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server request channel
 jack server is not running or cannot be started
 JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for -1, skipping unlock
 JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for -1, skipping unlock
 Thu Dec 27 17:59:08 2018: Starting jack server...
 Thu Dec 27 17:59:08 2018: JACK server starting in realtime mode with priority 10
 Thu Dec 27 17:59:08 2018: self-connect-mode is "Don't restrict self connect requests"
 Thu Dec 27 17:59:09 2018: Acquired audio card Audio0
 Thu Dec 27 17:59:09 2018: creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit
 Thu Dec 27 17:59:09 2018: Using ALSA driver HDA-Intel running on card 0 - HDA NVidia at 0xf7080000 irq 79
 Thu Dec 27 17:59:09 2018: ERROR: ALSA: Cannot open PCM device alsa_pcm for playback. Falling back to capture-only mode
 Thu Dec 27 17:59:09 2018: Released audio card Audio0
 Thu Dec 27 17:59:09 2018: ERROR: Cannot initialize driver
 Thu Dec 27 17:59:09 2018: ERROR: JackServer::Open failed with -1
 Thu Dec 27 17:59:09 2018: ERROR: Failed to open server
 Thu Dec 27 17:59:11 2018: Saving settings to "/home/ppp/.config/jack/conf.xml" ...

17:59:13.266 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server request channel
 jack server is not running or cannot be started
 JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for -1, skipping unlock
 JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for -1, skipping unlock
```




I've done the whole browsing through forums bit, stopping pulse audio, entering scripts in qjackctl, tried Catia etc, deleting config files and starting from scratch and it just refuses to run.

From terminal running jack_control start
results in DBus exception: org.jackaudio.Error.Generic: Failed to open server

Help :)

---

### Post by eufex1 on 2018-12-28
Well, after spending about 8 hours on this have managed to get it working. It seems that for the internal audio hardware, jack server will not start and connect the driver unless a combination of sample rate, frame rate etc it likes is set beforehand. Getting the correct combination was just guesswork and hit miss. Still has a lot of xruns mind. 
Ive also got the FireWire running which seems to be more reliable, more so on very low latencies, I get xruns on higher latencies for some reason but glad things are moving in the right direction.

---

### Post by slickymaster on 2018-12-28
Thread moved to **Multimedia Software** for a better fit

---

