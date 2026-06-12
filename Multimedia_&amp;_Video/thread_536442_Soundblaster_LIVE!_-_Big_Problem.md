---
title: "Soundblaster LIVE! - Big Problem"
date: 2007-08-27
forum: Multimedia &amp; Video
---

### Post by hooplah on 2007-08-27
Okay. I just re-installed ubuntu after everything getting screwed up with WUBI on windows, and now ... I'm suffering a large problem. The sound doesn't work, at all. The weird thing is, the only sound that does work, is when the login screen appears after boot. With the drum roll or whatever. 

I have already searched for various tutorials, help and whatnot throughout the internet. I've tried several different methods, but none want to work. Below, I will specify the commands I have inputed to the terminal, to help better diagnose my problem.

```

max@max-desktop:~$ gksudo asoundconf list
Names of available sound cards:
I82801BAICH2
Live

```

```

max@max-desktop:~$ gksudo asoundconf set-default-card Live

```

```

max@max-desktop:~$ gksudo asoundconf list
Names of available sound cards:
I82801BAICH2
Live

```

Other attempts at fixing this issue were going into Applications > Sound & Video > Volume Control. I tried switching devices, and enabling everything. However,  once I restarted the X server, logged out, or even rebooted my computer, the issue had not fixed itself, at all.

Cheers,
Max

---

### Post by hooplah on 2007-08-27
Sorry to bump, but this is really a issue that I'd like to be fixed soon if possible.

---

