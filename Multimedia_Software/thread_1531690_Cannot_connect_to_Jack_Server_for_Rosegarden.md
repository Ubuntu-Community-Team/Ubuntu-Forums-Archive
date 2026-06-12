---
title: "Cannot connect to Jack Server for Rosegarden"
date: 2010-07-15
forum: Multimedia Software
---

### Post by graphixfx on 2010-07-15
I am trying to use rosegarden, but it says "midi fine, no audio". I found a thread with this same issue and that said to instal jackd and a synth. So I installed qsynth and tried to start jackd. When starting jackd i get this error:

10:16:50.399 Patchbay deactivated.
10:16:50.546 Statistics reset.
10:16:51.021 ALSA connection graph change.
10:16:51.287 ALSA connection change.
10:16:57.507 Startup script...
10:16:57.507 artsshell -q terminate
sh: artsshell: not found
10:16:57.909 Startup script terminated with exit status=32512.
10:16:57.909 JACK is starting...
10:16:57.909 /usr/bin/jackd -dalsa -dhw:0 -r44100 -p1024 -n2
10:16:57.912 JACK was started with PID=10399.
jackd 0.118.0
Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK is running in realtime mode, but you are not allowed to use realtime scheduling.
Please check your /etc/security/limits.conf for the following lines
and correct/add them:
  @audio          -       rtprio          100
  @audio          -       nice            -10
After applying these changes, please re-login in order for them to take effect.
You don't appear to have a sane system configuration. It is very likely that you
encounter xruns. Please apply all the above mentioned changes and start jack again!
10:16:57.956 JACK was stopped with exit status=255.
10:16:57.957 Post-shutdown script...
10:16:57.957 killall jackd
jackd: no process found
10:16:58.385 Post-shutdown script terminated with exit status=256.
10:16:59.957 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.

Does any one have any thought or is having the same issue?

Thanks for any help

---

### Post by cchhrriiss121212 on 2010-07-15
> JACK is running in realtime mode, but you are not allowed to use realtime scheduling.
Please check your /etc/security/limits.conf for the following lines
and correct/add them:
  @audio          -       rtprio          100
  @audio          -       nice            -10
Here is your solution, either:
a) uncheck the realtime box from jack setup window (which gives you worse performance)
b) open a terminal and paste this:
```
sudo gedit /etc/security/limits.conf
```
Then paste these lines:
@audio - rtprio 99
@audio - memlock unlimited
(the nice value is not necessary)
You should also add yourself to the audio group (System>Users & Groups), then reboot.

---

