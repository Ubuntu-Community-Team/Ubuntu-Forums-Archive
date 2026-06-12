---
title: "Jack  will not start in realtime"
date: 2010-11-01
forum: Multimedia Software
---

### Post by buddykoerner on 2010-11-01
Hello,

I am not able to start JACK in realtime mode. This is a bummer. here is the error message I get:

 p, li { white-space: pre-wrap; } [COLOR=#999999]12:10:02.080 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]12:10:02.081 Statistics reset.[/COLOR]
 [COLOR=#66CC99]12:10:02.117 ALSA connection graph change.[/COLOR]
 [COLOR=#CCCC99]12:10:02.313 ALSA connection change.[/COLOR]
 [COLOR=#999999]12:10:03.940 Startup script...[/COLOR]
 [COLOR=#990099]12:10:03.943 artsshell -q terminate[/COLOR]
 sh: artsshell: not found
 [COLOR=#999999]12:10:04.345 Startup script terminated with exit status=32512.[/COLOR]
 [COLOR=#999999]12:10:04.345 JACK is starting...[/COLOR]
 [COLOR=#990099]12:10:04.346 /usr/bin/jackd -dalsa -r44100 -p1024 -n2 -D -Chw:1 -Phw:1[/COLOR]
 [COLOR=#999999]12:10:04.349 JACK was started with PID=2624.[/COLOR]
 jackd 0.118.0
 Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
 jackd comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 JACK is running in realtime mode, but you are not allowed to use realtime scheduling.
 Your system has an audio group, but you are not a member of it.
 Please add yourself to the audio group by executing (as root):
   usermod -a -G audio (null)
 After applying these changes, please re-login in order for them to take effect.
 You don't appear to have a sane system configuration. It is very likely that you
 encounter xruns. Please apply all the above mentioned changes and start jack again!
 [COLOR=#999999]12:10:04.357 JACK was stopped with exit status=255.[/COLOR]
 [COLOR=#999999]12:10:04.358 Post-shutdown script...[/COLOR]
 [COLOR=#990099]12:10:04.358 killall jackd[/COLOR]
 jackd: no process found
 [COLOR=#999999]12:10:04.768 Post-shutdown script terminated with exit status=256.[/COLOR]
 [COLOR=#FF0000]12:10:06.535 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]


How do I add myself into the audio group?

thanks,
-buddy
[COLOR=#ff0000] [/COLOR]

---

### Post by cchhrriiss121212 on 2010-11-01
In terminal:
```
sudo adduser "yourusername" audio
```

---

