---
title: "Sound dies after a random time of playback"
date: 2011-01-27
forum: Multimedia Software
---

### Post by eltomito on 2011-01-27
Hi!
Can anybody help me with a sound problem?
I checked the Comprehensive Sound Problem Guide but it didn't help.

This is what happens:

When I start Audacious and make it play music, after a random time the player
freezes up and the music stops playing. I have to make Audacious force quit and restart it, then it works for some time again.
When I play a youtube video (in Firefox), it plays fine for some time and then it loses sound and either continues playing silent or the video stops and doesn't start again until I reload the page.

I would be grateful for any help!

I use kernel 2.6.31-11-rt and the soundcard is...
             product: AC'97 Sound Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.7
             bus info: pci@0000:00:02.7
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=Intel ICH latency=32 maxlatency=11 mingnt=52
             resources: irq:18 ioport:9400(size=256) ioport:9000(size=128)

These are some logs I think could help figure this out (yes, the sound died
at about 13:25:05 :-)

-- user.log --

Jan 27 13:25:06 joo pulseaudio[6541]: pid.c: Stale PID file, overwriting.
Jan 27 13:25:07 joo pulseaudio[6549]: pid.c: Daemon already running.
Jan 27 13:25:07 joo pulseaudio[6551]: pid.c: Daemon already running.
Jan 27 13:25:08 joo pulseaudio[6552]: pid.c: Daemon already running.

-- syslog --

Jan 27 13:25:06 joo pulseaudio[6541]: pid.c: Stale PID file, overwriting.
Jan 27 13:25:07 joo pulseaudio[6549]: pid.c: Daemon already running.
Jan 27 13:25:07 joo pulseaudio[6551]: pid.c: Daemon already running.
Jan 27 13:25:08 joo pulseaudio[6552]: pid.c: Daemon already running.

-- daemon.log --

Jan 27 13:25:05 joo rtkit-daemon[4360]: Failed to make ourselves RT: Invalid argument
Jan 27 13:25:07 joo rtkit-daemon[4360]: last message repeated 24 times
Jan 27 13:25:07 joo rtkit-daemon[4360]: Warning: Reached burst limit for user '1000', denying request.
Jan 27 13:26:08 joo rtkit-daemon[4360]: last message repeated 18 times

Thank you very much for any help!

---

### Post by wooddealer on 2011-07-22
Bump.  Any progress on this, I am having the same problem.  A sample of my /var/log/messages

```
Jul 21 21:16:15 desktop pulseaudio[3153]: ratelimit.c: 20 events suppressed
Jul 21 21:17:08 desktop pulseaudio[3153]: ratelimit.c: 47 events suppressed
Jul 21 21:20:31 desktop pulseaudio[3318]: pid.c: Stale PID file, overwriting.

```

---

### Post by vangop on 2011-11-07
Same thing with pulseaudio in all the *ubuntus 11.10.
Anyone has a workaround?

---

### Post by vangop on 2011-11-09
Ok, finally comes THE solution.
I've just removed pulseaudio and that's all. With alsa all sound problems got fixed.
I've never had such bad issues with it before, so considered it a radical solution. You can disable it from autostart if you want and use alsa, but I've just removed it.

---

