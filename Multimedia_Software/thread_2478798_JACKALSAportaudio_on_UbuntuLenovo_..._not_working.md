---
title: "JACK/ALSA/portaudio on Ubuntu/Lenovo ... not working"
date: 2022-09-05
forum: Multimedia Software
---

### Post by m-g4 on 2022-09-05
I'm trying to set up portaudio (needs to be the latest release) on a Lenovo Thinkpad with Ubuntu 20.04. I have an external USB sound card with 7 channels. That sound card needs to be available to portaudio via MATLAB. At the moment, portaudio and MATLAB cannot see the sound card.

I think I need to use JACK and ALSA to do this. However, they are not getting on at all well. I've spend a couple of days on this so far. I have Ubuntu Studio Controls, and that appears to show I have Real Time Permissions Enabled. However, I cannot start JACK. If I try to start up QjackCtl, I get the following:

```
[COLOR=#999999]22:53:41.930 Statistics reset.[/COLOR]
 [COLOR=#ff0000]22:53:41.935 Could not open ALSA sequencer as a client. ALSA MIDI patchbay will be not available.[/COLOR]
 ALSA lib conf.c:1228:(parse_value) default is not a string
 ALSA lib conf.c:1967:(_snd_config_load_with_include) _toplevel_:364:0:Invalid argument
 ALSA lib conf.c:4180:(snd_config_update_r) /usr/share/alsa/alsa.conf may be old or corrupted: consider to remove or fix it
 [COLOR=#999999]22:53:44.678 D-BUS: Service is available (org.jackaudio.service aka jackdbus).[/COLOR]
 [COLOR=#ff0000]22:53:44.763 D-BUS: JACK server could not be started. Sorry[/COLOR]
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
 Mon Sep  5 22:53:44 2022: Starting jack server...
 Mon Sep  5 22:53:44 2022: JACK server starting in realtime mode with priority 10
 Mon Sep  5 22:53:44 2022: self-connect-mode is "Don't restrict self connect requests"
 Mon Sep  5 22:53:44 2022: ERROR: control open "hw:0" (Invalid argument)
 Mon Sep  5 22:53:44 2022: ERROR: control open "hw:0" (Invalid argument)
 Mon Sep  5 22:53:44 2022: creating alsa driver ... hw:0|-|1024|2|44100|0|0|nomon|swmeter|-|32bit
 Mon Sep  5 22:53:44 2022: ERROR: control open "hw:0" (Invalid argument)
 Mon Sep  5 22:53:44 2022: ERROR: ALSA: Cannot open PCM device alsa_pcm for playback. Falling back to capture-only mode
 Mon Sep  5 22:53:44 2022: ERROR: control open "hw:0" (Invalid argument)
 Mon Sep  5 22:53:44 2022: ERROR: control open "hw:0" (Invalid argument)
 Mon Sep  5 22:53:44 2022: ERROR: Cannot initialize driver
 Mon Sep  5 22:53:44 2022: ERROR: JackServer::Open failed with -1
 Mon Sep  5 22:53:44 2022: ERROR: Failed to open server
 Mon Sep  5 22:53:45 2022: Saving settings to "/home/mlibxmg4/.config/jack/conf.xml" ...
 [COLOR=#ff0000]22:53:48.167 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server request channel
 jack server is not running or cannot be started
 JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for -1, skipping unlock
 JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for -1, skipping unlock


```

Here is the window from Ubuntu Studio Controls:

[IMG]http://www.stammertime.com/Articles/Screenshot.png[/IMG]

When I click on "Start or Restart Jack" there is no response. Not even an error message.

I've tried everything I can think of to troubleshoot this. Any suggestions would be gratefully received.

For example, if I uninstall everything and then reinstall in a particular order, will it make a difference? If so, what order? Alternatively, do I need to track down and adjust a setting somewhere, and if so where?

Is there anything I can do which is guaranteed to work, even if it is time consuming?

(One clue: this might be limited to the USB bus. I managed to get JACK to run one time with the internal two channel sound card. However JACK will not work with a USB sound card. I have tried a two channel USB sound card as well as the seven channel USB sound card.)

---

### Post by m-g4 on 2022-09-08
I have some updates for this. I think I have traced the problem to McAfee antivirus software. The system I am working on was provided by my IT department, and I didn't realise that the antivirus software was included by default. 

Unfortunately, I think trying to troubleshoot with McAfee antivirus running in the background has corrupted some part of the installation. At this point, I can see little option other than to reinstall Ubuntu and start again.

---

