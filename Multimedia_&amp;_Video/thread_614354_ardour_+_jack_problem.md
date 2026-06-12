---
title: "ardour + jack problem"
date: 2007-11-15
forum: Multimedia &amp; Video
---

### Post by NotimePro on 2007-11-15
so i get a jack server not running error when i try to start ardour. then when i try to run qJackctl it says that it could not connect to the jack server either.

this is what it gives me

21:58:49.642 Startup script...
21:58:49.642 artsshell -q terminate
JACK tmpdir identified as [/dev/shm]
sh: artsshell: not found
21:58:49.846 Startup script terminated with exit status=32512.
21:58:49.846 JACK is starting...
21:58:49.846 /usr/bin/jackd -R -dalsa -dhw:0 -r44100 -p1024 -n2
21:58:49.847 JACK was started with PID=12759 (0x31d7).
jackd 0.103.0
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
cannot use real-time scheduling (FIFO at priority 10) [for thread -1210770752, from thread -1210770752] (1: Operation not permitted)
cannot create engine
21:58:49.853 JACK was stopped successfully.
21:58:49.853 Post-shutdown script...
21:58:49.853 killall jackd
jackd: no process killed
21:58:50.057 Post-shutdown script terminated with exit status=256.
21:58:51.953 Could not connect to JACK server as client. Please check the messages window for more info.
JACK tmpdir identified as [/dev/shm]

oh yea im running ubuntu 7.10

---

### Post by MrFSL on 2007-11-15
start jackctrl with a sudo before it:

```
sudo qJackctl
```

---

### Post by NotimePro on 2007-11-15
well it works now. thank you

however when i try to start ardour i still get an error saying that it could not find the jack server

also when i use sudo qjackctl i get this 

Warning: no locale found: /usr/share/locale/qjackctl_en_US.UTF-8.qm

---

### Post by NotimePro on 2007-11-16
bump, still wont work

---

