---
title: "Jackd won't run causing Ardour not to work"
date: 2011-07-10
forum: Multimedia Software
---

### Post by ahayzen on 2011-07-10
Hi

Linux andy-desktop 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686 i686 i386 GNU/Linux

I am using Ubuntu 11.04 32Bit and I can't get Ardour to run, jackd seems to freeze, it was working on past releases but I have not managed to get it working with natty.

When I start ardour/jack jackd freezes in system monitor it states 'sys_rt_sigtimedwait' as the waiting channel. Note that this even happens with the Dummy driver!

This is the output from qjackctl:

```

 p, li { white-space: pre-wrap; }  [COLOR=#999999]18:13:16.634 JACK is starting...[/COLOR]
 [COLOR=#990099]18:13:16.634 /usr/bin/jackd -r -dalsa -dhw:0 -r44100 -p1024 -n3[/COLOR]
 Cannot connect to server socket err = Connection refused
 Cannot connect to server socket
 jack server is not running or cannot be started
 [COLOR=#999999]18:13:16.657 JACK was started with PID=9951.[/COLOR]
 no message buffer overruns
 no message buffer overruns
 jackdmp 1.9.7
 Copyright 2001-2005 Paul Davis and others.
 Copyright 2004-2010 Grame.
 jackdmp comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 JACK server starting in non-realtime mode
 control device hw:0
 control device hw:0
 audio_reservation_init
 Acquire audio card Audio0
 creating alsa driver ... hw:0|hw:0|1024|3|44100|0|0|nomon|swmeter|-|32bit
 control device hw:0
 Using ALSA driver HDA-Intel running on card 0 - HDA NVidia at 0xcfff4000 irq 22
 configuring for 44100Hz, period = 1024 frames (23.2 ms), buffer = 3 periods
 ALSA: final selected sample format for capture: 32bit integer little-endian
 ALSA: use 3 periods for capture
 ALSA: final selected sample format for playback: 32bit integer little-endian
 ALSA: use 3 periods for playback

```
Jack then freezes here, once i kill the process jackd the text below appears.



```

 [COLOR=#ff0000]18:13:31.309 Could not connect to JACK server as client. - Overall operation failed. - Server communication error. Please check the messages window for more info.[/COLOR]
 Cannot read socket fd = 28 err = Interrupted system call
 Could not read result type = 22
 Client name = qjackctl conflits with another running client
 Cannot connect to the server
 [COLOR=#999999]18:13:31.384 JACK was stopped successfully.[/COLOR]
 [COLOR=#cc3366]18:13:31.384 JACK has crashed.[/COLOR]


```Hope someone can help me out :)

Thanks in advance.

Andy

---

### Post by ahayzen on 2011-07-11
Hi

I have solved this issue by downloading the jack source from the website and compiling myself. It now appears to be working.

Andy

---

