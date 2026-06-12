---
title: "JACK on a Soundblaster live! 24-bit?"
date: 2010-06-28
forum: Multimedia Software
---

### Post by miguelpinheiro on 2010-06-28
Hi, do you know how can i make JACK work on a Soundblaster live! 24-bit? when i start jack on qjackctl, i get this:
```
  p, li { white-space: pre-wrap; }  [COLOR=#999999]00:36:51.442 Startup script...[/COLOR]
 [COLOR=#990099]00:36:51.443 artsshell -q terminate[/COLOR]
 sh: artsshell: not found
 [COLOR=#999999]00:36:51.845 Startup script terminated with exit status=32512.[/COLOR]
 [COLOR=#999999]00:36:51.846 JACK is starting...[/COLOR]
 [COLOR=#990099]00:36:51.846 /usr/bin/jackd -dalsa -dhw:0 -r44100 -p1024 -n2[/COLOR]
 [COLOR=#999999]00:36:51.851 JACK was started with PID=12529.[/COLOR]
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
 [COLOR=#999999]00:36:51.915 JACK was stopped with exit status=255.[/COLOR]
 [COLOR=#999999]00:36:51.924 Post-shutdown script...[/COLOR]
 [COLOR=#990099]00:36:51.925 killall jackd[/COLOR]
 jackd: processo nÃ£o achado (translation: process not found)
 [COLOR=#999999]00:36:52.367 Post-shutdown script terminated with exit status=256.[/COLOR]
 [COLOR=#ff0000]00:36:54.236 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]

```the driver used is PulseAudio, and the only things on connections are:

[IMG]http://img267.imageshack.us/img267/3914/semttuloha.png[/IMG]
but if i connect the two CA0106 (wich btw, i don't know if are tue soundblaster), nothing happens

thanks

---

### Post by miguelpinheiro on 2010-06-29
oh, and i've tried to do what the guides to get JACK to work with PulseAudio say, but it didn't work

---

