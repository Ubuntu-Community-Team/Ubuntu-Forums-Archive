---
title: "Jack just wont start"
date: 2006-07-07
forum: Multimedia &amp; Video
---

### Post by x1zer0 on 2006-07-07
No matter what ive tried i just cant get Jack to start i am a bit of a linux newbie so i maybe missing something stupid, but i followed the instructions to a tee, please help me :)

02:35:57.393 Startup script...
02:35:57.393 artsshell -q terminate
can't create mcop directory
Creating link /home/darryl/.kde/socket-ukronix.
02:35:57.709 Startup script terminated with exit status=256.
02:35:57.709 JACK is starting...
02:35:57.709 /usr/bin/jackd -R -t5000 -dalsa -r44100 -p1024 -n2 -D -Chw:0 -Phw:0 -S
02:35:57.715 JACK was started with PID=6262 (0x1876).
02:35:57.740 Could not connect to JACK server as client. Please check the messages window for more info.
jackd 0.100.0
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
apparent rate = 44100
creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|16bit
control device hw:0
configuring for 44100Hz, period = 1024 frames, buffer = 2 periods
nperiods = 2 for capture
nperiods = 2 for playback
02:35:58.386 JACK was stopped successfully.

AMD1800+, Creative Live! EMU10k1 750MB

Maybe I just need a new Sound Card?

---

### Post by Sheik Yerbouti on 2006-07-07
Just a guess really but try 48000 for your sample rate I know the Audigy uses 48k I believe the live does as well.

---

### Post by x1zer0 on 2006-07-08
Thanks for the reply :)

Unfortunately it makes no difference though, i either get a zombified state error or request type7 (broken pipe) can anyone tell me what this means?

Thanks for the help.

---

### Post by Sheik Yerbouti on 2006-07-09
try this bare minimum command to start jackd from a terminal. To see if it has anything to do with your settings in qjackctl.

 jackd -R -d alsa -d hw

---

### Post by x1zer0 on 2006-07-09
Fantastic, thanks for the reply, it works!!!, I got it to run from Jack control aswell after your help :)

---

### Post by x1zer0 on 2006-07-17
Hi, since the latest kernel update Jack wont run again :) UI dont understan why since I have not changed any other settings.

22:49:31.450 Patchbay deactivated.
22:49:31.679 Statistics reset.
22:49:31.893 Startup script...
22:49:31.893 artsshell -q terminate
22:49:31.943 MIDI connection graph change.
sound server terminated
22:49:32.242 Startup script terminated successfully.
22:49:32.242 JACK is starting...
22:49:32.243 /usr/bin/jackd -R -t5000 -dalsa -r48000 -p1024 -n2 -D -Chw:0 -Phw:0
22:49:32.256 JACK was started with PID=5891 (0x1703).
jackd 0.100.0
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
apparent rate = 48000
creating alsa driver ... hw:0|hw:0|1024|2|48000|0|0|nomon|swmeter|-|32bit
control device hw:0
configuring for 48000Hz, period = 1024 frames, buffer = 2 periods
Note: audio device hw:0 doesn't support a 32bit sample format so JACK will try a 24bit format instead
Note: audio device hw:0 doesn't support a 24bit sample format so JACK will try a 16bit format instead
nperiods = 2 for capture
Note: audio device hw:0 doesn't support a 32bit sample format so JACK will try a 24bit format instead
Note: audio device hw:0 doesn't support a 24bit sample format so JACK will try a 16bit format instead
22:49:32.506 Server configuration saved to "/home/darryl/.jackdrc".
22:49:32.508 Statistics reset.
22:49:32.585 Client activated.
22:49:32.586 Audio connection change.
22:49:32.587 MIDI connection change.
22:49:32.605 Audio connection graph change.
nperiods = 2 for playback
zombified - calling shutdown handler
22:49:32.692 Shutdown notification.
22:49:32.693 Client deactivated.
22:49:32.694 JACK is stopping...
cannot read result for request type 7 from server (Connection reset by peer)
cannot send request type 7 to server
cannot read result for request type 7 from server (Broken pipe)
22:49:32.848 JACK was stopped successfully.

Any help please :)

---

### Post by alamet on 2006-10-28
Hi, I have the same problem!
In Dapper I had no problem with jack (except for some xruns but it worked).
Since I upgraded to Edgy (did it when it was still Beta) I get this message in qjackctrl:

18:32:27.516 Patchbay deactivated.
18:32:27.603 Statistics reset.
18:32:27.799 MIDI connection graph change.
18:32:27.905 MIDI connection change.
18:32:31.509 Startup script...
18:32:31.510 artsshell -q terminate
sound server terminated
18:32:31.892 Startup script terminated successfully.
18:32:31.907 JACK is starting...
18:32:31.912 jackd -R -dalsa -dhw:0 -r48000 -p128 -n2
18:32:31.934 JACK was started with PID=5179 (0x143b).
jackd 0.101.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
apparent rate = 48000
creating alsa driver ... hw:0|hw:0|128|2|48000|0|0|nomon|swmeter|-|32bit
control device hw:0
configuring for 48000Hz, period = 128 frames, buffer = 2 periods
Note: audio device hw:0 doesn't support a 32bit sample format so JACK will try a 24bit format instead
Note: audio device hw:0 doesn't support a 24bit sample format so JACK will try a 16bit format instead
nperiods = 2 for capture
Note: audio device hw:0 doesn't support a 32bit sample format so JACK will try a 24bit format instead
Note: audio device hw:0 doesn't support a 24bit sample format so JACK will try a 16bit format instead
nperiods = 2 for playback
18:32:34.020 Server configuration saved to "/home/samuele/.jackdrc".
18:32:34.025 Statistics reset.
18:32:34.139 Client activated.
18:32:34.145 Audio connection change.
18:32:34.156 Audio connection graph change.
18:32:34.167 XRUN callback (1).
18:32:36.181 XRUN callback (381 skipped).
jackd watchdog: timeout - killing jackd
18:32:37.164 Shutdown notification.
18:32:37.171 Client deactivated.
18:32:37.179 JACK was stopped successfully.
zombified - calling shutdown handler
cannot send request type 7 to server
cannot read result for request type 7 from server (Pipe interrotta)
cannot send request type 7 to server
cannot read result for request type 7 from server (Pipe interrotta)

Any ideas? thanks!

---

