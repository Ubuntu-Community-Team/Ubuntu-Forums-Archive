---
title: "Jack doesn't start after upgrade to Feisty"
date: 2007-05-18
forum: Multimedia &amp; Video
---

### Post by hansson_14 on 2007-05-18
I run Xubuntu 64
After upgrading to 7.04 Qjackctl refuses to start Jack, showing following message:

20:30:57.933 Patchbay activated.
20:30:57.957 Statistics reset.
20:30:58.021 Startup script...
20:30:58.021 artsshell -q terminate
20:30:58.049 MIDI connection graph change.
can't create mcop directory
Creating link /home/fredrik/.kde/socket-Fredrik.
20:30:58.683 Startup script terminated with exit status=256.
20:30:58.683 JACK is starting...
20:30:58.683 jackd -R -p128 -dalsa -dhw:0 -r44100 -p128 -n2 -S
20:30:58.686 JACK was started with PID=6271 (0x187f).
jackd 0.102.20
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
cannot use real-time scheduling (FIFO at priority 10) [for thread 473398480, from thread 473398480] (1: Operation not permitted)
cannot create engine
20:30:58.819 JACK was stopped successfully.
20:30:58.889 MIDI active patchbay scan...
20:30:58.889 MIDI connection change.
20:30:59.093 MIDI active patchbay scan...
20:31:00.930 Could not connect to JACK server as client. Please check the messages window for more info.

I tried to reinstall Jack and Qjackctl, but still the same problem.

However, if I login as root everything works fine.

Thanks for helping,
Fredrik

---

### Post by luctor on 2007-05-19
permission problem
take a look at [https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation)

> 
Real-Time Support

Now you need to set up real-time access for your applications.

All you have to do for this is give your audio group permissions to access the rtprio, nice, and memlock limits. To do this, you just need to run these commands:
```

 sudo su -c 'echo @audio - rtprio 99 >> /etc/security/limits.conf'
 sudo su -c 'echo @audio - memlock 250000 >> /etc/security/limits.conf'
 sudo su -c 'echo @audio - nice -10 >> /etc/security/limits.conf'

```
And that is it! You're all set for real-time acces!


---

### Post by hansson_14 on 2007-05-26
Yes, that was it ... after I made those permission changes and logged out an in again, all is well.

Thanks! :D

---

### Post by tomjennings on 2007-05-30
> **hansson_14 said:**
> Yes, that was it ... after I made those permission changes and logged out an in again, all is well.

Thanks! :D

Not here!

Just installed and upgraded ubuntustudio. Sony FE-590 laptop, dual core. I had jack running on ubuntu 6.10 but too many xruns, so I thought I'd try low-latency. It's worse now!

With qjackctl, and after having made the edits to /etc/security/limits.conf, and log out/log in, I still get jackd timeout/zombification then termination.


23:25:43.649 Patchbay deactivated.
23:25:43.676 Statistics reset.
23:25:43.754 MIDI connection graph change.
23:25:43.883 MIDI connection change.
23:25:56.772 Startup script...
23:25:56.772 artsshell -q terminate
can't create mcop directory
Creating link /root/.kde/socket-qx.
23:25:57.316 Startup script terminated with exit status=256.
23:25:57.316 JACK is starting...
23:25:57.316 /usr/bin/jackd -v -R -dalsa -dhw:0 -r48000 -p1024 -n2
23:25:57.323 JACK was started with PID=13012 (0x32d4).
getting driver descriptor from /usr/lib/libjack0.100.0/jack_alsa.so
getting driver descriptor from /usr/lib/libjack0.100.0/jack_oss.so
getting driver descriptor from /usr/lib/libjack0.100.0/jack_dummy.so
getting driver descriptor from /usr/lib/libjack0.100.0/jack_freebob.so
jackd 0.102.20
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
server `default' registered
loading driver ..
apparent rate = 48000
creating alsa driver ... hw:0|hw:0|1024|2|48000|0|0|nomon|swmeter|-|32bit
control device hw:0
configuring for 48000Hz, period = 1024 frames, buffer = 2 periods
ALSA: final selected sample format for capture: 32bit little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 32bit little-endian
ALSA: use 2 periods for playback
registered builtin port type 32 bit float mono audio
registered builtin port type 8 bit raw midi
clock source = system clock via gettimeofday
running with uid=0 and euid=0, will not try to use capabilites
new client: alsa_pcm, id = 1 type 1 @ 0x8069f58 fd = -1
new buffer size 1024
registered port alsa_pcm:capture_1, offset = 4096
registered port alsa_pcm:capture_2, offset = 8192
registered port alsa_pcm:playback_1, offset = 0
registered port alsa_pcm:playback_2, offset = 0
++ jack_rechain_graph():
client alsa_pcm: internal client, execution_order=0.
-- jack_rechain_graph()
13012 waiting for signals
23:25:59.344 Server configuration saved to "/home/tomic/.jackdrc".
23:25:59.347 Statistics reset.
23:25:59.361 Client activated.
23:25:59.364 Audio connection change.
23:25:59.377 Audio connection graph change.
new client: qjackctl-13003, id = 2 type 2 @ 0xb7fac000 fd = 15
++ jack_rechain_graph():
client alsa_pcm: internal client, execution_order=0.
client qjackctl-13003: start_fd=5, execution_order=0.
client qjackctl-13003: wait_fd=10, execution_order=1 (last client).
-- jack_rechain_graph()
23:25:59.414 XRUN callback (1).
23:26:01.375 XRUN callback (38 skipped).
jackd watchdog: timeout - killing jackd
zombified - calling shutdown handler
23:26:02.570 Shutdown notification.
23:26:02.574 Client deactivated.
23:26:02.581 JACK was stopped successfully.
23:26:02.582 Post-shutdown script...
23:26:02.582 killall jackd
cannot read result for request type 7 from server (Connection reset by peer)
cannot send request type 7 to server
cannot read result for request type 7 from server (Broken pipe)
jackd: no process killed
23:26:02.812 Post-shutdown script terminated with exit status=256.

Running without -R (realtime) avoids this, but jack won't play audio, not even with bad gapping/dropouts as in 6.04.

Running as user or root makes no difference. Priority settings make no difference. A quick ps ax show it does get invoked OK.

ALSA works (xmms, mixxx with ALSA as output instead of Jack).

Any hints anyone?

---

### Post by tomjennings on 2007-05-30
Sorry, more info:

$ uname -a

Linux qx 2.6.20-16-lowlatency #2 SMP PREEMPT Wed May 23 01:49:41 UTC 2007 i686 GNU/Linux

I've tried dozens of combinations of priority, frames, period, etc. I'm a good techie and sysadmin but there seems to be no way to intelligently choose a path; there's no docs on what these settings actually do and why I'd choose one over the other. I get the relationship in general between blocksize, blocks per unit time, switchin latencies etc but who knows how Jack is wired.

Confounding symptoms are, if I uncheck Realtime (no -R) then Jack stays running, but with lots of xruns

00:08:07.321 XRUN callback (31 skipped).
00:08:09.331 XRUN callback (29 skipped).
00:08:11.342 XRUN callback (33 skipped).
00:08:13.353 XRUN callback (33 skipped).
00:08:15.366 XRUN callback (33 skipped).
00:08:17.387 XRUN callback (27 skipped).
00:08:19.398 XRUN callback (31 skipped).


But if I start mixxx, it behaves very strangely (I load a track to A, but it doesn't even attempt to play, clicking PLAY/PAUSE changes the icon nothing more) and the track waveform display doesn't load. It all works fine if jack isnt running and I choose ALSA as output.

(On earlier non-rt kernels jack would run, but get xruns and audio was gapping, hence the upgrade to ubuntustudio.)

Does there exist anywhere but the source information on what the various parameters to jack are? The source won't help me, I'm not an audio/kernel geek, and to be honest that seems a bit of a stretch.

Does anyone have jack running under ubuntustudio?

---

### Post by tomjennings on 2007-05-30
Egad, I'm embarrassed! Three in a row! 

But here's new data. I ran jackd as root and it revealed a segfault:

root@qx:~# jackd -R -d alsa
jackd 0.102.20
Copyright [blah blah]
JACK compiled with System V SHM support.
loading driver ..
creating alsa driver ... hw:0|hw:0|1024|2|48000|0|0|nomon|swmeter|-|32bit
control device hw:0
configuring for 48000Hz, period = 1024 frames, buffer = 2 periods
ALSA: final selected sample format for capture: 32bit little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 32bit little-endian
ALSA: use 2 periods for playback
jackd watchdog: timeout - killing jackd
Segmentation fault (core dumped)
root@qx:~# 

Umm, segfault?

---

### Post by tomjennings on 2007-05-30
OK, now you know I'm crazy, answering my own questions... :-)


* my soundcard cannot do fullduplex and requires jackd option --playback to work; this stopped the segfaults. (that's qjackctl's Audio: playback only option)

* _ had to use n=3 to stop the xruns (that's qjackctl's Periods/Buffer option)

/usr/bin/jackd -v -R -dalsa -dhw:0 -r48000 -p1024 -n3 -i2 --playback


Jack is a great thing, but man it's not easy to puzzle out. 

[http://www.jackaudio.org/faq](http://www.jackaudio.org/faq) was a big help (duh :-)

---

### Post by burnman99 on 2007-05-31
Getting Jack error as well

01:54:14.663 Patchbay deactivated.
01:54:14.711 Statistics reset.
01:54:14.720 Startup script...
01:54:14.721 artsshell -q terminate
01:54:14.761 MIDI connection graph change.
01:54:14.992 Startup script terminated with exit status=256.
01:54:14.992 JACK is starting...
01:54:14.993 /usr/bin/jackd -dalsa -dhw:0 -r44100 -p1024 -n2
01:54:15.008 JACK was started with PID=12072 (0x2f28).
jackd 0.102.20
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
apparent rate = 44100
creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit
control device hw:0
configuring for 44100Hz, period = 1024 frames, buffer = 2 periods
ALSA: final selected sample format for capture: 16bit little-endian
ALSA: cannot set period size to 1024 frames for capture
ALSA: cannot configure capture channel
cannot load driver module alsa
no message buffer overruns
01:54:15.023 JACK was stopped successfully.
01:54:15.024 Post-shutdown script...
01:54:15.024 killall jackd
jackd: no process killed
01:54:15.209 MIDI connection change.
01:54:15.234 Post-shutdown script terminated with exit status=256.
01:54:17.222 Could not connect to JACK server as client. Please check the messages window for more info.
01:55:00.516 Startup script...
01:55:00.518 artsshell -q terminate
01:55:00.770 Startup script terminated with exit status=256.
01:55:00.772 JACK is starting...
01:55:00.774 /usr/bin/jackd -dalsa -dhw:0 -r44100 -p1024 -n2
01:55:00.791 JACK was started with PID=12098 (0x2f42).
jackd 0.102.20
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
apparent rate = 44100
creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit
control device hw:0
configuring for 44100Hz, period = 1024 frames, buffer = 2 periods
ALSA: final selected sample format for capture: 16bit little-endian
ALSA: cannot set period size to 1024 frames for capture
ALSA: cannot configure capture channel
cannot load driver module alsa
no message buffer overruns
01:55:00.886 JACK was stopped successfully.
01:55:00.889 Post-shutdown script...
01:55:00.891 killall jackd
jackd: no process killed
01:55:01.107 Post-shutdown script terminated with exit status=256.
01:55:02.820 Could not connect to JACK server as client. Please check the messages window for more info

Any Ideas?

TIA

Roger

---

### Post by burnman99 on 2007-05-31
n/m it works great now thanks!

Rog

---

