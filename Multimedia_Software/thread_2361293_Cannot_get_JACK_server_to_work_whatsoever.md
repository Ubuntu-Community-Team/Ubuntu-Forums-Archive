---
title: "Cannot get JACK server to work whatsoever"
date: 2017-05-14
forum: Multimedia Software
---

### Post by abadpena1 on 2017-05-14
Hello all,

Its been a while since I have been on a forum. Anyway, I have been trying to get JACK server to work for the longest time for my system (ASUS ROG G751JL). I have tried a lot of threads dealing with my issue to no avail. What I am trying to do is plug in my guitar to my system so I can use the application "guitarix" which depends on JACK Server. The application that I use to control my JACK settings is "QjackCTL". When I plug in my guitar I get the following message in QjackCTL:

```
[COLOR=#999999]22:07:36.626 Statistics reset.[/COLOR]
[COLOR=#cccc99]22:07:36.632 ALSA connection change.[/COLOR]
[COLOR=#999999]22:07:36.635 D-BUS: Service is available (org.jackaudio.service aka jackdbus).[/COLOR]
[COLOR=#ff0000]22:07:36.725 D-BUS: JACK server could not be started. Sorry[/COLOR]
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
[COLOR=#66cc99]22:07:36.765 ALSA connection graph change.[/COLOR]
Sun May 14 22:07:36 2017: Starting jack server...
Sun May 14 22:07:36 2017: JACK server starting in realtime mode with priority 10
Sun May 14 22:07:36 2017: self-connect-mode is "Don't restrict self connect requests"
Sun May 14 22:07:36 2017: Acquired audio card Audio3
Sun May 14 22:07:36 2017: Acquired audio card Audio1
Sun May 14 22:07:36 2017: creating alsa driver ... hw:PCH|hw:Jam,0|16|3|48000|0|0|nomon|swmeter|-|16bit
Sun May 14 22:07:36 2017: Using ALSA driver HDA-Intel running on card 1 - HDA Intel PCH at 0xed310000 irq 30
Sun May 14 22:07:36 2017: configuring for 48000Hz, period = 16 frames (0.3 ms), buffer = 3 periods
Sun May 14 22:07:36 2017: ALSA: final selected sample format for capture: 32bit integer little-endian
Sun May 14 22:07:36 2017: ERROR: ALSA: cannot set period size to 16 frames for capture
Sun May 14 22:07:36 2017: ERROR: ALSA: cannot configure capture channel
Sun May 14 22:07:36 2017: Released audio card Audio3
Sun May 14 22:07:36 2017: Released audio card Audio1
Sun May 14 22:07:36 2017: ERROR: Cannot initialize driver
Sun May 14 22:07:36 2017: ERROR: JackServer::Open failed with -1
Sun May 14 22:07:36 2017: ERROR: Failed to open server
Sun May 14 22:07:37 2017: Saving settings to "/home/abad/.config/jack/conf.xml" ...
[COLOR=#ff0000]22:07:38.968 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for -1, skipping unlock
JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for -1, skipping unlock
```

I usually don't ask for help when it comes to troubleshooting software, but it has now been 8 months since I have been trying to get this to work. I have finally given up trying to do this on my own. I was wondering if anyone could assist me in doing this?

---

### Post by Bucky Ball on 2017-05-15
Welcome. It would help a lot if you could tell us where you're up to with it after eight months. 

[LIST]
[*]What are you trying to do with jack? Just run it? 
[*]Have you got qjackctl installed? If not, install that and we can check the settings more easily.
[*]Are you running this with an outboard device? If there are conflicting settings in jack it can prevent jack from starting.
[*]Do you have AV apps open while you are trying to start jack?
[/LIST]

Always helps if you give us an idea of the hardware you are using to do what you're doing and the release and flavour of Ubuntu you are using (Ubuntu-studio 16.04 LTS?) ... and anything else of use you can think of. ;)

---

