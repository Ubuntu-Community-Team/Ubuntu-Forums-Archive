---
title: "Jack Control not working"
date: 2010-09-05
forum: Multimedia Software
---

### Post by higashi on 2010-09-05
I have a few programs that require Jack audio output but, when running Jack Control and pressing Start, all i get is a pop up saying
> Could not connect to JACK server as client.
- Overall operation failed.
- Unable to connect to server.
Please check the messages window for more info.
and another (the JACK messages pop up) saying
> 12:14:10.484 Patchbay deactivated.
12:14:10.508 Statistics reset.
12:14:10.640 ALSA connection graph change.
12:14:10.835 ALSA connection change.
12:15:53.324 Startup script...
12:15:53.324 artsshell -q terminate
sh: artsshell: not found
12:15:53.728 Startup script terminated with exit status=32512.
12:15:53.728 JACK is starting...
12:15:53.729 /usr/bin/jackd -dalsa -dhw:0 -r44100 -p1024 -n2
12:15:53.731 JACK was started with PID=3289.
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
12:15:53.755 JACK was stopped with exit status=255.
12:15:53.755 Post-shutdown script...
12:15:53.756 killall jackd
jackd: no process found
12:15:54.189 Post-shutdown script terminated with exit status=256.
12:15:55.876 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
How can i get Jack to run properly?

---

### Post by higashi on 2010-09-08
bump

---

### Post by cchhrriiss121212 on 2010-09-08
> JACK is running in realtime mode, but you are not allowed to use realtime scheduling.
Your system has an audio group, but you are not a member of it.
Please add yourself to the audio group by executing (as root):
  usermod -a -G audio (null)
These are the two things you need to check, for some reason they are not performed during installation of jack on Ubuntu, but they are on other distros. 
[B]
To use realtime:[/B]
```
sudo gedit /etc/security/limits.conf
```
then paste these lines:
@audio - rtprio 99
@audio - memlock unlimited
[B]
To join the audio group:[/B]
```
sudo adduser "yourusername" audio
```

---

### Post by higashi on 2010-09-08
I tried both of these and neither of them worked ):

---

### Post by cchhrriiss121212 on 2010-09-08
Oops, forgot to mention that they need a reboot to take effect (as will any other alteration to a system file).

---

### Post by higashi on 2010-09-08
oh ok, it works now, thanks! :D

---

