---
title: "pulse audio latest update problem"
date: 2009-01-04
forum: Multimedia Software
---

### Post by cezdeville on 2009-01-04
today i've installed few updates (i'm not sure the date, but they were latest), there were some pulse audio fixes among them.
now - after update - i've got breaks in music aand video playback. every few minutes (2-3 sometimes more often haven't noticed any rule) there is few seconds (about 3-5) gap in playback.
it happens in totem as well as in banshee, so it seems to be wide system problem.
console shows no output, but i've found out that system monitor shows drastic jump of pulse audio CPU usage (up to 85%) and process has futex_wait status.

someone has crossed this bug? it's quite annoying. is there any way to undo that update?

---

### Post by cezdeville on 2009-01-04
bump!

is that really only mine problem?

---

### Post by gettinoriginal on 2009-01-04
These are some sites that my help:


[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by cezdeville on 2009-01-04
thanks for suggestion. i've seen these topics couple of times.
i've installed and kept Interpid mainly because PulseAudio is much improved in 8.10, compared to Hardy. At least until today it worked without any problems 'out of a box'. i had sound in ET and EVE Voice working.

todays update screw the thing for me. i have problems with playback and - it seems - also with mic. these problems are erratic, that is hard for me to find any solution or even to pinpoint its nature. yet its impossible to f.e. watch film if you are loosing sound every couple of minutes. 

i just wish i hadn't made that upgrade today, or just turn it back now. once again i'm starting to be afraid of updates

i know that it was mentioned many times earlier but i have to say, that Ubuntu Developers should slow down and focus more on quality, than frequency of new releases. i decided to stick with Interpid to have a sound for a price of working Bluetooth. last two releases are horrific for me! 
now i'm considering to go back to Gutsy. yet i'd like to use the newest versions of some programs (Firefox, GIMP, etc). what choice do i have? i don't want to reinstall my system every few months or with every problem i run into.

please don't take me as a troll. i'm with Ubuntu since Dapper and i've used Suse for few years earlier. you can easyly check that usually i don't complain. but this time i'm loosing my nerve.

---

### Post by gettinoriginal on 2009-01-04
May I suggest that you uninstall pulse audio, then reinstall it, some have mentioned that it helps after updates.

---

### Post by cezdeville on 2009-01-05
thank you very much for your will to help.

i've reinstalled PulseAudio as you suggested. unfortunately it didn't help.
sound works without any problems in Enemy Territory and EVE.
while playing music, films, or using Skype still i've got random gaps.
always the same scenario: pulseaudio's CPU usage drastically grows, it shows futex_wait status in System Monitor (usually it's do_poll) and we have few seconds gap. then it all goes back to normal work. it happens once in few minutes (typically 3-5, as it seems to happen at least once per music track).

anyone have other ideas?? or should i wait for another update?

---

### Post by markbuntu on 2009-01-05
Are you getting any messages in your logs?

---

### Post by cezdeville on 2009-01-06
where should i look for them?

---

### Post by markbuntu on 2009-01-06
In System/Administration/System Log. there will be a few logs there and if you want to view more you can use file/open. 

Look in messages and the syslog first.

---

### Post by ExemplarUbuntu on 2009-01-08
I had skype working last weekend. Did some updates today and now I get no sound output and no input.

In user log:

Jan  8 19:15:11 Toshiba-ubuntu pulseaudio[5276]: ltdl-bind-now.c: Failed to find original dlopen loader.
Jan  8 19:15:11 Toshiba-ubuntu pulseaudio[5278]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Jan  8 19:15:11 Toshiba-ubuntu pulseaudio[5278]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Jan  8 19:15:31 Toshiba-ubuntu pulseaudio[5278]: module-x11-xsmp.c: X11 session manager not running.
Jan  8 19:15:31 Toshiba-ubuntu pulseaudio[5278]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.

---

### Post by cezdeville on 2009-01-09
here are my logs:
pulseaudio[5282]: ltdl-bind-now.c: Failed to find original dlopen loader.
pulseaudio[5285]: main.c setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
pulseaudio[5285]: main.c setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
pulseaudio[5285]: module-x11-xsmp.c: X11 session manager not running.
pulseaudio[5285]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.

---

### Post by gettinoriginal on 2009-01-09
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

---

### Post by ExemplarUbuntu on 2009-01-10
System sounds work ok.

Sound recording works.

It is just Skype that has been broken by the latest set of updates so that page isn't very relevant.

---

### Post by gettinoriginal on 2009-01-10
Try this one:
[https://help.ubuntu.com/community/Skype](https://help.ubuntu.com/community/Skype)

---

