---
title: "Sound only works after sudo alsa force-reload"
date: 2013-11-07
forum: Multimedia Software
---

### Post by lucacerone on 2013-11-07
Dear all,
after experiencing a few issues with my sound card (due to a mistake of mine), I finally seem to have almost everything
working fine on my Ubuntu 12.04 64 bit.

The only problem is that the sound doesn't work immediately at startup, but only after I open a terminal and use the command 

sudo alsa force-reload

After that everything works fine till the next time I reboot.
It is not extremely annoying, but how can I fix this issue?

Thanks a lot for the help,
Cheers!

---

### Post by tgalati4 on 2013-11-08
Look in the log files to see why alsa is dumping out.  Boot up logs are /var/log/syslog and /var/log/syslog.1.  Could be a simple permissions issue with an audio device.  Post anything alsa-related.

---

### Post by lucacerone on 2013-11-08
Hi tgalati4,
thanks a lot for the help.

The files contain quite a lot of stuff, I have tried:

> cat /var/log/syslog | grep -i alsa
Nov  8 01:21:02 np350v roard: (roard: driver_alsa.c:179): Error: driver_alsa_open_vio(*): Unable to open PCM device: Connection refused
Nov  8 01:21:02 np350v roard: (roard: output.c:454): Error: add_output(drv='alsa', dev='(null)', opts='sync'): can not open output driver.

while syslog.1 shows nothing.

While this is it the output checking for pulseaudio:
> Nov  8 01:03:04 np350v pulseaudio[2559]: [pulseaudio] pid.c: Daemon already running.
Nov  8 01:05:02 np350v pulseaudio[10903]: [pulseaudio] pid.c: Daemon already running.
Nov  8 01:20:56 np350v pulseaudio[1275]: [pulseaudio] main.c: Running in system mode, forcibly disabling SHM mode!
Nov  8 01:20:56 np350v pulseaudio[1275]: [pulseaudio] main.c: Running in system mode, forcibly disabling exit idle time!
Nov  8 01:20:56 np350v pulseaudio[1326]: [pulseaudio] main.c: OK, so you are running PA in system mode. Please note that you most likely shouldn't be doing that.
Nov  8 01:20:56 np350v pulseaudio[1326]: [pulseaudio] main.c: If you do it nonetheless then it's your own fault if things don't work as expected.
Nov  8 01:20:56 np350v pulseaudio[1326]: [pulseaudio] main.c: Please read [http://pulseaudio.org/wiki/WhatIsWrongWithSystemMode](http://pulseaudio.org/wiki/WhatIsWrongWithSystemMode) for an explanation why system mode is usually a bad idea.
Nov  8 01:21:02 np350v pulseaudio[1326]: [pulseaudio] protocol-native.c: Denied access to client with invalid authorization data.
Nov  8 01:21:03 np350v pulseaudio[1326]: [pulseaudio] protocol-native.c: Denied access to client with invalid authorization data.
Nov  8 01:21:03 np350v pulseaudio[1326]: [pulseaudio] protocol-native.c: Denied access to client with invalid authorization data.
Nov  8 01:21:03  pulseaudio[1326]: last message repeated 3 times
Nov  8 01:21:21 np350v pulseaudio[1326]: [pulseaudio] protocol-native.c: Denied access to client with invalid authorization data.
Nov  8 01:21:35  pulseaudio[1326]: last message repeated 2 times
Nov  8 01:21:36 np350v pulseaudio[1326]: [pulseaudio] protocol-native.c: Denied access to client with invalid authorization data.
Nov  8 01:21:42 np350v pulseaudio[1326]: [pulseaudio] protocol-native.c: Denied access to client with invalid authorization data.
Nov  8 01:21:55  pulseaudio[1326]: last message repeated 3 times
Nov  8 01:21:57 np350v pulseaudio[1326]: [pulseaudio] protocol-native.c: Denied access to client with invalid authorization data.
Nov  8 01:22:30  pulseaudio[1326]: last message repeated 16 times
Nov  8 01:23:05  pulseaudio[1326]: last message repeated 7 times
Nov  8 01:23:07 np350v pulseaudio[1326]: [pulseaudio] protocol-native.c: Denied access to client with invalid authorization data.
Nov  8 01:23:09 np350v pulseaudio[1326]: [pulseaudio] protocol-native.c: Denied access to client with invalid authorization data.
Nov  8 01:23:12 np350v pulseaudio[1326]: [pulseaudio] protocol-native.c: Denied access to client with invalid authorization data.
Nov  8 01:23:16 np350v pulseaudio[1326]: [pulseaudio] protocol-native.c: Denied access to client with invalid authorization data.
Nov  8 01:23:16 np350v pulseaudio[1326]: [pulseaudio] protocol-native.c: Denied access to client with invalid authorization data.
Nov  8 01:23:17 np350v pulseaudio[1326]: [pulseaudio] protocol-native.c: Denied access to client with invalid authorization data.
Nov  8 01:23:54  pulseaudio[1326]: last message repeated 7 times
Nov  8 01:23:57 np350v pulseaudio[1326]: [pulseaudio] protocol-native.c: Denied access to client with invalid authorization data.
Nov  8 01:24:24  pulseaudio[1326]: last message repeated 6 times
Nov  8 01:24:26 np350v pulseaudio[1326]: [pulseaudio] protocol-native.c: Denied access to client with invalid authorization data.
Nov  8 01:24:33  pulseaudio[1326]: last message repeated 2 times
Nov  8 01:25:44 np350v pulseaudio[2557]: [pulseaudio] pid.c: Daemon already running.
Nov  8 01:32:17 np350v pulseaudio[2617]: [pulseaudio] pid.c: Daemon already running.
Nov  8 01:35:13 np350v pulseaudio[3429]: [pulseaudio] pid.c: Failed to open PID file '/tmp/pulse-TUeJkSiYiDaz/pid': No such file or directory
Nov  8 01:35:13 np350v pulseaudio[3429]: [pulseaudio] pid.c: Failed to open PID file '/tmp/pulse-TUeJkSiYiDaz/pid': No such file or directory
Nov  8 01:35:19 np350v pulseaudio[11251]: [pulseaudio] pid.c: Daemon already running.
Nov  8 01:35:19 np350v pulseaudio[11253]: [pulseaudio] pid.c: Daemon already running.
Nov  8 09:26:42 np350v pulseaudio[2411]: [pulseaudio] pid.c: Daemon already running.
Nov  8 09:28:52 np350v pulseaudio[10825]: [pulseaudio] pid.c: Daemon already running.

the output for syslog1 contains error prior to when I fixed so I am not posting them.

I see there are issues, but I have no idea what issues and how to solve them.

Any help would be really appreciated, thanks a lot in advance for the help :)

---

### Post by Yellow Pasque on 2013-11-09
When you start the system, get alsa info (before running alsa force-reload), then get it again after force-reload: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by tgalati4 on 2013-11-10
Sometimes adding yourself to group *audio* helps:

tgalati4@tpad-Gloria7 ~ $ groups
tgalati4 adm dialout cdrom** audio** video plugdev fuse lpadmin netdev pulse-rt admin sambashare phcusers


```
sudo adduser lucacerone audio
```

---

### Post by Yellow Pasque on 2013-11-10
> **tgalati4 said:**
> Sometimes adding yourself to group *audio* helps

That's not a good idea for most people, especially for multi-user systems: [https://wiki.ubuntu.com/Audio/TheAudioGroup](https://wiki.ubuntu.com/Audio/TheAudioGroup)
Only 'pulse' should be in the audio group.

---

### Post by tgalati4 on 2013-11-10
My experience with older versions of Ubuntu and using Jack, adding the primary user to group audio solves a lot of problems, but you are correct, on a multiuser system this is not recommended.

---

### Post by lucacerone on 2013-11-11
Hi everybody,
first of all thanks for the help.

My user was already in the audio group (I think I found this solution online) and now I have removed it since it doesn't seem to help.

As for the ALSAINFO, thanks for the advice, I can't do it right now, but tonight I will do as you suggested and post the results in the thread :)

Cheers,
Luca

---

### Post by lucacerone on 2013-11-11
Hi everybody,
as Temüjin suggested here is the link provided by AlsaInfo before running `sudo alsa force-reload`:  [http://www.alsa-project.org/db/?f=9b191a9b48e8fcab57a4a86007ceb63fef3c456f](http://www.alsa-project.org/db/?f=9b191a9b48e8fcab57a4a86007ceb63fef3c456f)

and here is the link provided by AlsaInfo after forcing the reload: [http://www.alsa-project.org/db/?f=8f700e202f9663e89fc9e79cf180b9098c01bbdd](http://www.alsa-project.org/db/?f=8f700e202f9663e89fc9e79cf180b9098c01bbdd)
and having checked that the sound works.

Thanks a lot in advance for the help,
Cheers,
Luca

---

### Post by Yellow Pasque on 2013-11-11
Before:
```
RoarAudio:
      Installed - Yes (/usr/bin/roard)
      Running - Yes
```
After:
```
RoarAudio:
      Installed - Yes (/usr/bin/roard)
      Running - No
```
I don't know too much about roaraudio, but it's possibly grabbing the hardware device and blocking pulseaudio until you run force-reload.

---

### Post by lucacerone on 2013-11-11
I have no idea what is roaraudio... thanks for noticing it :)

---

### Post by Yellow Pasque on 2013-11-11
Well, then you probably want to remove roaraudio package. If you installed mpd or followed a tutorial to do so, it may have been installed at that point.

---

### Post by lucacerone on 2013-11-11
And that fixed the issue :) 
Thanks a lot for the help it's almost three weeks that I was playing around to get the sound back :)

---

