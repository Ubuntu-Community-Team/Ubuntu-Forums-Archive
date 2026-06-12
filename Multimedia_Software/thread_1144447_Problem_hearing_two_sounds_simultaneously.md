---
title: "Problem hearing two sounds simultaneously"
date: 2009-04-30
forum: Multimedia Software
---

### Post by bo01 on 2009-04-30
Hello,
this is might be a common problem but I still can't figure it out.

I am using Debian, but I know some Ubuntu users have this problem too.

The laptop I am using is a DELL XPS M1530 and the exact distribution is Debian 5.0 (Lenny).
$uname -ar
```
Linux laptop 2.6.26-2-686 #1 SMP Thu Mar 26 01:08:11 UTC 2009 i686 GNU/Linux
```

The problem, as I write in the title, is that if for example I am listening a sound file in vlc then I cannot hear any flash (eg YouTube). Same with Amarok and other players and also the sound systems too.

I think there is a conflict with the drivers (OSS, ALSA, pulseaudio) and the applications using them.

I am going to write some outputs while the programs are running, in case they are useful to you in order to help me.

If I am watching a flash video with sound and I am trying to hear the same time a song in vlc (although I have manually set vlc to use ALSA), I get this in the console:
```
oss audio output error: cannot open audio device (/dev/dsp)
```

With Amarok, I get this message
```
xine was unable to initialize any audio drivers.
```

When I type $pulseaudio while listening to something, I get
```
W: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
W: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
E: alsa-util.c: Error opening PCM device hw:0: Device or resource busy
E: module.c: Failed to load  module "module-alsa-sink" (argument: "device_id=0 sink_name=alsa_output.pci_8086_284b_alsa_playback_0"): initialization failed.
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
```

Finally if I am not listening anything and I type $pulseaudio, I get
```
E: pid.c: Daemon already running.
E: main.c: pa_pid_file_create() failed.
```

Thanks in advance for any help!

---

### Post by markbuntu on 2009-05-01
You can try this guide, it should work for Lenny if you are using gnome or xfce desktop.

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

To fix the Operation not permitted problem you need to make your user and root members of the following groups
pulse
pulse-rt
pulse-access

Make sure that pulse is loaded at login

---

### Post by bo01 on 2009-05-01
Thanks for the answer! 

It seems that every application using pulseaudio has no problem with sound mixing. So the problem is setting vlc to use pulseaudio. In the preferences menu of vlc, all it has is setting for every module the correct device, not choosing the module you want. Some help here?

Thanks again! (I also posted in the thread you gave me).

---

### Post by bo01 on 2009-05-01
I think I found it. I had to check advanced options in the output modules. Although it doesn't say anything about pulseaudio, I clicked ESD and it worked. 

Thanks again!:)

---

