---
title: "Can't launch PulseAudio"
date: 2009-09-30
forum: Multimedia Software
---

### Post by Rhapsody on 2009-09-30
Recently I've got a webcam and started wanting to use it with Skype. It may be closed source, but they have an x64 build and it works very nicely with my desktop.

The only problem with this is sound. Skype gives me two choices, ALSA (not an option, I'm using OSSv4 here) or PulseAudio. I've found that PulseAudio does not start by default with KDE, which is why I couldn't access it. I tried launching it manually with 'pulseaudio -D' to see how it works, only to be confronted with this:

```
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
N: main.c: Called SUID root and real-time and/or high-priority scheduling was requested in the configuration. However, we lack the necessary privileges:
N: main.c: We are not in group 'pulse-rt', PolicyKit refuse to grant us the requested privileges and we have no increase RLIMIT_NICE/RLIMIT_RTPRIO resource limits.
N: main.c: For enabling real-time/high-priority scheduling please acquire the appropriate PolicyKit privileges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limits for this user.
E: main.c: **[COLOR="Red"]Daemon startup failed.[/COLOR]**
```

These problems seemed mostly related with permissions, so I went to PolicyKit Authorization, and added myself under both entries in "The PulseAudio Project". This changed the error, but then left my stumped:

```
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
E: main.c: **[COLOR="Red"]Daemon startup failed.[/COLOR]**
```

Is this related to my use of OSSv4 in anyway? If so, how do I fix it and start using Skype? I'm on Kubuntu Jaunty, using KDE 4.2.4.

---

