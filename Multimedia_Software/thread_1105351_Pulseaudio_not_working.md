---
title: "Pulseaudio not working"
date: 2009-03-24
forum: Multimedia Software
---

### Post by Qbeta on 2009-03-24
So I'm not getting any sound using pulse.  I'm running an AMD64 dual core machine and using Ubuntu 8.10 (Intrepid).  Yes, I've read the FAQ [http://ubuntuforums.org/showthread.php?t=789578]("http://ubuntuforums.org/showthread.php?t=789578") on pulse problems and done the things recommended there.  It still does not work.  I have used fuser to try to find if anything is using the audio devices and there does not seem to be anything hogging the audio devices.


E: alsa-util.c: Error opening PCM device plughw:0: Device or resource busy
E: module.c: Failed to load  module "module-alsa-sink" (argument: "device=plughw:0 rate=44100 sink_name=mysink"): initialization failed.
E: main.c: Module load failed.
E: main.c: Failed to initialize daemon.

There is also this earlier in the output

W: ltdl-bind-now.c: Failed to find original dlopen loader.
W: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted

---

### Post by Qbeta on 2009-03-25
I've now upgraded to Jaunty (9.04).  Still no lock with pulse.  I get the same errors:

E: alsa-util.c: Error opening PCM device plughw:0: Device or resource busy

Yet it does not seem that anything is using any of the things under /dev/snd

Does anyone have any ideas?

---

### Post by markbuntu on 2009-03-25
Set your system/preferences/sound to pulseaudio. You can go here to see how to set up pulseaudio to work properly.

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

---

### Post by Qbeta on 2009-03-26
> **markbuntu said:**
> Set your system/preferences/sound to pulseaudio. You can go here to see how to set up pulseaudio to work properly.

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

OK, problem (mostly) solved.  Pulse has to be run as sudo with the --system option.  This is in spite of the fact that I added myself to the pulse, pulse-rt and pulse-access groups.  It seems the audio devices are all owned by group audio.  The pulse group is supposedly a member of that group and I am a member of pulse.  Still pulse will only start when run as sudo.  Also the audio group does not appear in the System-->Administration-->Users and Groups applet.  Well, at least I have sound now. :P

---

### Post by redenex on 2009-03-26
You should be lucky to have sound in the first place, there are many others, like me, who do not have any sound since 64 bit 8.10 installation. We have tried almost everything but no luck yet.

---

### Post by markbuntu on 2009-03-26
Jaunty is still very much a work in progress, especially the sound part. I find that if something is broken it usually gets fixed one or two updates later. Patience is definitely necessary with Jaunty.

---

