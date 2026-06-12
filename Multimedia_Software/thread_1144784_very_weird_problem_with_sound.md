---
title: "very weird problem with sound"
date: 2009-05-01
forum: Multimedia Software
---

### Post by joeabiraad on 2009-05-01
Hi

lately i've been facing this weird problem with sound.
When i start up my pc no sound is played, only a "kheshhh" sound is heard.

If i kill pulse audio using 
```
sudo killall pulseaudio
```

and the reload my alsa drivers using
```
sudo alsa force-reload
```

sound seem to work perfectly in ONLY amarok. If i try to play music in totem, the problem is back again and i have to rekill pulseaudio and reload the alsa drivers.
If i play flash videos in firefox its the same thing.

Anyone can help ? 

Thanks
Joe

---

### Post by joeabiraad on 2009-05-01
I was just trying to follow this guide
[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578) (PART A) I have ubuntu 9.04

and it seems i cant do step 5.

I cant run 
```
pulseaudio
```

reason:
```
jo@jo-desktop:~$ pulseaudio
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
N: main.c: Called SUID root and real-time and/or high-priority scheduling was requested in the configuration. However, we lack the necessary privileges:
N: main.c: We are not in group 'pulse-rt', PolicyKit refuse to grant us the requested privileges and we have no increase RLIMIT_NICE/RLIMIT_RTPRIO resource limits.
N: main.c: For enabling real-time/high-priority scheduling please acquire the appropriate PolicyKit privileges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limits for this user.
E: socket-server.c: bind(): Address already in use
E: module.c: Failed to load  module "module-esound-protocol-unix" (argument: ""): initialization failed.
E: main.c: Module load failed.
E: main.c: Failed to initialize daemon.
jo@jo-desktop:~$ 

```

---

### Post by dentaku65 on 2009-05-01
> **joeabiraad said:**
> I was just trying to follow this guide
[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578) (PART A) I have ubuntu 9.04

and it seems i cant do step 5.

I cant run 
```
pulseaudio
```

reason:
```
jo@jo-desktop:~$ pulseaudio
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
N: main.c: Called SUID root and real-time and/or high-priority scheduling was requested in the configuration. However, we lack the necessary privileges:
N: main.c: We are not in group 'pulse-rt', PolicyKit refuse to grant us the requested privileges and we have no increase RLIMIT_NICE/RLIMIT_RTPRIO resource limits.
N: main.c: For enabling real-time/high-priority scheduling please acquire the appropriate PolicyKit privileges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limits for this user.
E: socket-server.c: bind(): Address already in use
E: module.c: Failed to load  module "module-esound-protocol-unix" (argument: ""): initialization failed.
E: main.c: Module load failed.
E: main.c: Failed to initialize daemon.
jo@jo-desktop:~$ 

```

Are you logged as root?

---

### Post by osarusan on 2009-05-01
I had that problem too. Try killing pulseaudio before you run pulseaudio. That worked for me. There's a command a few lines down from there if you want something to copy and paste.

---

### Post by joeabiraad on 2009-05-01
i tried to to do it.

the thing is that it is working when i issue this command
```
sudo alsa force-reload
```

but it is working only in AMAROK... not in firefox flash and not in TOTEM.

evenmore if i try to play an mp3 in totem player.... then sound stop working again :S

---

### Post by WatchingThePain on 2009-05-01
Hi,

You need to be added to the group.
Look here : [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/265010](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/265010)
Maybe this can help.

---

### Post by joeabiraad on 2009-05-01
Ok ... thanks

that fixed the pulseaudio running problem.
i needed to add my username to the pulse-rt group using
```

sudo usermod -G pulse-rt jo

```

but still i cannot hear sounds using totem.

here is the output:
```

jo@jo-desktop:~$ totem Desktop/s.wmv
/var/lib/python-support/python2.6/gdata/tlslite/utils/cryptomath.py:9: DeprecationWarning: the sha module is deprecated; use the hashlib module instead
  import sha

```

All i hear is a shushing sound... !

Thanks

---

### Post by WatchingThePain on 2009-05-01
Sounds like Totem is using a wrong module, hopefully someone knows how to make it use the hashlib module (as I don't).

---

