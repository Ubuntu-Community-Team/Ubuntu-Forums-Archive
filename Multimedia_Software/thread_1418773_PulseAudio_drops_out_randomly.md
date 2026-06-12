---
title: "PulseAudio drops out randomly"
date: 2010-03-01
forum: Multimedia Software
---

### Post by insert_name_here on 2010-03-01
I'm running Karmic on a Lenovo T60 with a Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02) audio device. I use PulseAudio.

Whenever I'm listening to music, using VLC or Amarok, the sound drops out randomly. I have not found out a way to dependably reproduce the error, though it's been taking place over the course of weeks/months and occurs between one and twenty times an hour, roughly.

The following info is in the user.log for each time the error occurs. (This is the only info and it is repeated in the log many times)

> Feb 28 22:06:16 <computer name> pulseaudio[16124]: pid.c: Stale PID file, overwriting.
Feb 28 22:06:16 <computer name> pulseaudio[16128]: pid.c: Daemon already running.

I've also got this segfault in messages.log -- the specific address changes for each instance of the error.
> Feb 28 22:10:09 <computer name> kernel: [925883.628021] pulseaudio[16124]: segfault at 7 ip 00ecd5b3 sp bfc4982c error 6 in libc-2.10.1.so[e60000+13e000]

The only way to fix the problem is to restart the music program (vlc or amarok). After restarting the program, the sound works, for some period of time, whether minutes or hours. Restarting the computer helps, again temporarily. The problem begins again.

Anyone else have this error? Any ideas how to solve it? Should I file a bug report? (And with whom?)

---

