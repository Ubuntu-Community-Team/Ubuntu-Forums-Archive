---
title: "Myth Frontend is crashing after watching tv or recordings"
date: 2009-08-12
forum: Mythbuntu
---

### Post by tshannon on 2009-08-12
Every time after stopping watching a recording, or live tv, the frontend crashes.  This just started happening after my upgrade to Jaunty.

From what I can gather online, the error basically means, something crashed, and that's about it.  Any ideas?



```
Aug 12 19:56:56 CaldazarMyth lircd-0.8.4a[1552]: accepted new client on /dev/lircd
Aug 12 19:57:16 CaldazarMyth pulseaudio[2654]: main.c: Called SUID root and real-time and/or high-priority scheduling was requested in the configuration. However, we lack the necessary privileges:
Aug 12 19:57:16 CaldazarMyth pulseaudio[2654]: main.c: We are not in group 'pulse-rt', PolicyKit refuse to grant us the requested privileges and we have no increase RLIMIT_NICE/RLIMIT_RTPRIO resource limits.
Aug 12 19:57:16 CaldazarMyth pulseaudio[2654]: main.c: For enabling real-time/high-priority scheduling please acquire the appropriate PolicyKit privileges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limits for this user.
Aug 12 19:57:16 CaldazarMyth pulseaudio[2657]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
Aug 12 19:57:16 CaldazarMyth pulseaudio[2657]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
Aug 12 19:57:16 CaldazarMyth pulseaudio[2657]: module.c: Failed to open module "module-console-kit": file not found
Aug 12 19:57:16 CaldazarMyth pulseaudio[2657]: main.c: Module load failed.
Aug 12 19:57:16 CaldazarMyth pulseaudio[2657]: main.c: Failed to initialize daemon.
Aug 12 19:57:16 CaldazarMyth pulseaudio[2654]: main.c: Daemon startup failed.
Aug 12 19:57:24 CaldazarMyth kernel: [75730.245556] **mythfrontend.re[2643]: segfault at a7992650 ip a7992650 sp a953e36c error 4 in FreeMono.ttf[a79ca000+40000]**
Aug 12 19:57:24 CaldazarMyth lircd-0.8.4a[1552]: removed client
```

---

### Post by dano1 on 2009-08-13
try making yourself a member of pulse, pulse access, and pulse-rt in system/admn/users and groups.

---

### Post by tshannon on 2009-08-19
That didn't help, it just got rid of the pulse audio errors (although they weren't giving me any noticeable problems.

I'm still getting the segfault.

---

### Post by roundhay on 2009-08-20
There quite a few threads which already discuss this, try:

[http://ubuntuforums.org/showthread.php?t=1145048](http://ubuntuforums.org/showthread.php?t=1145048)

---

### Post by tshannon on 2009-09-06
Thanks a lot for the link.  Uninstalling pulse audio fixed it for me.

---

### Post by MonsterMaxx on 2009-09-07
I had the same problem. Here's the fix
[http://ubuntuforums.org/showthread.php?t=1209139](http://ubuntuforums.org/showthread.php?t=1209139)

---

