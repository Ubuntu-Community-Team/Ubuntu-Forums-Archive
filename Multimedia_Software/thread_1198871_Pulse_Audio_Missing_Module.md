---
title: "Pulse Audio Missing Module"
date: 2009-06-28
forum: Multimedia Software
---

### Post by illbashu on 2009-06-28
```
bash@bash-desktop:~$ pulseaudio
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
N: main.c: Called SUID root and real-time and/or high-priority scheduling was requested in the configuration. However, we lack the necessary privileges:
N: main.c: We are not in group 'pulse-rt', PolicyKit refuse to grant us the requested privileges and we have no increase RLIMIT_NICE/RLIMIT_RTPRIO resource limits.
N: main.c: For enabling real-time/high-priority scheduling please acquire the appropriate PolicyKit privileges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limits for this user.
W: pid.c: Stale PID file, overwriting.
E: module.c: Failed to open module "module-rtp-recv": file not found
E: module-gconf.c: pa_module_load() failed
E: module-rtp-send.c: Source does not exist.
E: module.c: Failed to load  module "module-rtp-send" (argument: "source=@DEFAULT_MONITOR@ loop=0"): initialization failed.
E: module-gconf.c: pa_module_load() failed
```

Everytime I try to play anything with sound all i get is static. Is there a known fix for this?

---

### Post by illbashu on 2009-06-28
I took a look and the module is there in /usr/lib/pulse-0.9/modules

---

### Post by dano1 on 2009-06-28
make yourself a member of pulse under users and groups.

hth, danny

---

### Post by illbashu on 2009-06-29
i did that, but it didn't work, then i removed it and installed 0.9.15 and it still doesn't have sound but it doesn't out put any sound. so I checked sound and both the Default Pulse Mixers are gone. So I think i am going to just reinstalls 9.04 or install the 9.10 Alpha version.

---

