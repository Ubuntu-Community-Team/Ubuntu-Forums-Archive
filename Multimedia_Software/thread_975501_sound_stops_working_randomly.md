---
title: "sound stops working randomly"
date: 2008-11-08
forum: Multimedia Software
---

### Post by zamrg on 2008-11-08
This problem recently started happening where by the sound randomly stops working.
I was just playing an mp3, went away for 10 minutes, and when I unpaused the track, the sound was dead. This happens with anything; system sounds, vlc, music, etc.

I looked at all log files and noticed a few errors in my user.log; not sure if they related to the problem but I've pasted everything.

```

Nov  8 03:52:01 zephyr bonobo-activation-server (mrg-27236): could not associate with desktop session: Failed to connect to socket /tmp/dbus-rqvwrUUKDd: Connection refused
Nov  8 03:52:11 zephyr pulseaudio[27494]: ltdl-bind-now.c: Failed to find original dlopen loader.
Nov  8 03:52:11 zephyr pulseaudio[27496]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Nov  8 03:52:11 zephyr pulseaudio[27496]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Nov  8 03:52:11 zephyr pulseaudio[27496]: alsa-util.c: Device hw:1 doesn't support 8 channels, changed to 2.
Nov  8 03:52:34 zephyr pulseaudio[27496]: module-x11-xsmp.c: X11 session manager not running.
Nov  8 03:52:34 zephyr pulseaudio[27496]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.
Nov  8 03:53:41 zephyr hp: io/hpmud/pp.c 627: unable to read device-id ret=-1 
Nov  8 03:53:43 zephyr python: io/hpmud/pp.c 627: unable to read device-id ret=-1 
Nov  8 14:41:54 zephyr mrg: Shorewall restarted
Nov  8 20:02:37 zephyr bonobo-activation-server (mrg-19906): could not associate with desktop session: Failed to connect to socket /tmp/dbus-3NPfoWVVGU: Connection refused
Nov  8 20:02:42 zephyr pulseaudio[20060]: ltdl-bind-now.c: Failed to find original dlopen loader.
Nov  8 20:02:42 zephyr pulseaudio[20062]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Nov  8 20:02:42 zephyr pulseaudio[20062]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Nov  8 20:02:43 zephyr pulseaudio[20062]: alsa-util.c: Device hw:1 doesn't support 8 channels, changed to 2.
Nov  8 20:03:05 zephyr pulseaudio[20062]: module-x11-xsmp.c: X11 session manager not running.
Nov  8 20:03:05 zephyr pulseaudio[20062]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.
Nov  8 20:04:12 zephyr hp: io/hpmud/pp.c 627: unable to read device-id ret=-1 
Nov  8 20:04:13 zephyr python: io/hpmud/pp.c 627: unable to read device-id ret=-1

```

I was wondering if anyone else has experienced this problem or knows of a possible solution.

I'm using Ubuntu Intrepid 8.10 with a Audigy 4 soundcard and 7.1 surround sound.

---

### Post by fearlsgroove on 2008-11-25
I'm seeing the same issue including all the same error messages in user.log .. sound works after a reboot, then stops eventually. Sound preferences > testing any device displays an error:

```
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Failed to connect: Connection refused
```

After the issue occurs, opening an app that would like to use the sound like totem or banshee cause that program to freeze. 

[I've seen the issue mentioned around the tubes]("http://mybroadband.co.za/vb/showthread.php?t=144567"), but haven't seen anyone with a solution.

restarting pulseaudio with pulseaudio -k produces an error:
```
W: ltdl-bind-now.c: Failed to find original dlopen loader.
E: main.c: Failed to kill daemon.
```

Dis is drivin me crazy mon!

My sound card is "NVIDIA CK804 with ALC850" I'll be happy to provide any other info if it'll help anyone, but I'm clueless

---

### Post by SlaughterDog on 2008-11-25
I find that if I put my computer into standby, the sound doesn't work when I resume, unless I log out then log back in. Perhaps the issues are related?

---

### Post by fearlsgroove on 2008-11-26
I've found that it's connected to flash. It works until I view a flash movie in firefox. Installing libflashsupport fixes the issue, but i've read that it causes browser crashes, and should also be unnecessary with flash 10. So far it seems stable.

```
sudo apt-get install libflashsupport
```

I don't use standby on this machine (it's a desktop) so I dunno whether that's an issue for me.

---

### Post by psyke83 on 2008-11-26
> **fearlsgroove said:**
> I've found that it's connected to flash. It works until I view a flash movie in firefox. Installing libflashsupport fixes the issue, but i've read that it causes browser crashes, and should also be unnecessary with flash 10. So far it seems stable.

```
sudo apt-get install libflashsupport
```

I don't use standby on this machine (it's a desktop) so I dunno whether that's an issue for me.

No, no no... please, **do not** install this library! It causes serious instability in Firefox. This library was necessary to get Flash 9 to work with PulseAudio, but Flash 10 works perfectly with PulseAudio's ALSA plugins.

Follow the [PuleAudio Fixes]("http://ubuntuforums.org/showthread.php?t=789578") guide to ensure you have the latest Flash 10 package and a proper PulseAudio configuration.

Explanation for instability: [bug #192888]("https://bugs.launchpad.net/bugs/192888")

---

### Post by hamzah2096 on 2009-01-19
try turn off the **visual assistance** in System>preference>session

---

### Post by hamzah2096 on 2009-01-19
check for visual assistance in System>preference>session. turn it off if it is on the list. hope this help

---

### Post by Feanor93 on 2009-08-30
I have the same problem, but it doesn't seen to be linked to youTube. I tried to find visual assistance but there was no session tab under preferences. I'm running Jaunty, would that make a difference?

---

### Post by teodora on 2010-02-10
Same problem appears working with Ubuntu 9.10. There is no 'session' in the menus.

---

### Post by CadetD on 2010-05-12
Same here. Started since upgrading to  Ubuntu 10.04 LTS Lucid Lynx

---

### Post by Gen. Lee poor on 2010-05-16
Snap. Same problem here in 10.04. Restarting firefox seems to work, but it breaks after a few minutes.

Any ideas?

---

### Post by wasabishot on 2010-05-28
Having the same problem sincce upgrading to Lucid 10.04

really irritating..... it is a bug since 2008 and still no fix?? shame on you!!!!!!!!
if i'm not wrong 2 new versions of ubuntu went out since then....

I guess listening to music or watching videos is not that important

We should care about world peace or the economy crisis instead...

help us!!!!!!!!!!

---

### Post by cnewswanger on 2010-08-27
I've got the same behavior,  Run ANY sound application including VST, Flash(HuLu, YouTube etc.) Audacious, Skype.  After 5 to 10 minutes there is a stutter in the audio then it quits.  If I have the pulse audio or QAMix window open the audio source vanishes.  Closing the app and reopening, restores the audio.  If I open Audacious while running a flash video in Firefox, Audacious will hang when the audio quits and requires Audacious to be killed before audio will work again.  I believe this started when I upgraded to 10.04.
My system:
Dell inspiron 1420
Core duo T7500 2.2GHz
Release 10.04
Gnome 2.30.2

Audio hardware: Intel 82801H
Kernel module: snd-hda-intel

---

