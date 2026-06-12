---
title: "Sound problems (poor 5.1 sound, low mic volume)"
date: 2013-03-03
forum: Multimedia Software
---

### Post by caracalsef on 2013-03-03
Hey there. I've installed Ubuntu 12.10 and I find that great! ( I'm a Windows user - if there will be DoTA 2 for linux, I'll say bye bye to windows :) )
But I have some problem with sound card. It may be because I don't know how to set it up right. The sound card is Xonar D1. I enabled 6 channels by editing that alsa config file (can't remember the right name, I'm on windows now - you know which file :P) and the test from the mixer is working (the one when you click on each speaker), except for the subwoofer. I hear a...thing, but that's not bass. If I'll have to, I'll record the sound which subwoofer makes when I hit his icon on the mixer :D I played with alsamixer, too, but no luck to get the subwoofer make the correct sound (low frequencies, just....rustling sound).
Also, I know from Windows that with WMP I can hear 5.1 effect in 5.1 .mkv movies. Didn't noticed that effect in Ubuntu.
Now with the microphone. I installed Skype for Ubuntu, but when I get a call, the other person can't hear me only if I shout on the microphone (so it is correctly installed - working good under Windows). What can I do in  this situation?
Thank you.

---

### Post by midfingr on 2013-03-03
Hi,
With Skype you may be able to fix the issue by open a terminal and typing:

gstreamer-properties

A window will open with output and input options. Under input, select Plugin: ALSA -- Advanced Linux Sound Architecture, then under Device, change it from default to whatever the system has picked up (there may be more than one, so experiment). Close the window.

In the terminal, type:

alsamixer

Try raising the microphone volume. In Skype, under preferences--audio select ALSA as the default input. Try a test call to see if it worked. You may get feedback, so turn your speaker output down just in case.

If that doesn't help, I'm sure others will be able to direct you to the proper solution. Good luck. :)

---

### Post by caracalsef on 2013-03-03
Thank you for your try midfingr :D

Unfortunately, that didn't helped :( I made the settings in gstreamer-properties.

In skype, at sound devices I have only "PulseAudio server (local)" at Microphone, Speakers and Ringing. There's nothing else to choose from.

In alsamixer I have set +12 dB Gain. I also have a square with a text under that says "<Mic Boost>", but I can't change anything and in the square I have "MM".

L.E.: I think I got it. That MM means it's muted so I must hit M key to unmute. Now Mic Boost is on and with +20dB Gain. I resolved this problem :D Now only remain the one with 5.1 sound effect and subwoofer "lack of bass" :)

---

### Post by midfingr on 2013-03-04
Hi,
It's good to see you've resolved the mic issue. Thank you for the update. :)

I have problems with 5.1 surround; using onboard audio. The only time I can get it working is when using Arch Linux and OSS (Open Sound System). When using ALSA and Pulse, I just leave it at stereo. I wish I could help you out.

A long shot. Maybe take a look at this article? -- [http://drona.csa.iisc.ernet.in/~uday/surround-pulse.shtml](http://drona.csa.iisc.ernet.in/~uday/surround-pulse.shtml) It's probably outdated however.

---

### Post by caracalsef on 2013-03-04
I solved the 5.1 audio, too. A guy in romanian Ubuntu forums posted a daemon.conf and I just replaced it with mine :D Now everything is OK!

Thank you for support. Here's the config file

```

# This file is part of PulseAudio.
#
# PulseAudio is free software; you can redistribute it and/or modify
# it under the terms of the GNU Lesser General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.
#
# PulseAudio is distributed in the hope that it will be useful, but
# WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU
# General Public License for more details.
#
# You should have received a copy of the GNU Lesser General Public License
# along with PulseAudio; if not, write to the Free Software
# Foundation, Inc., 59 Temple Place, Suite 330, Boston, MA 02111-1307
# USA.

## Configuration file for the PulseAudio daemon. See pulse-daemon.conf(5) for
## more information. Default values are commented out.  Use either ; or # for
## commenting.

; daemonize = no
; fail = yes
; allow-module-loading = yes
; allow-exit = yes
; use-pid-file = yes
; system-instance = no
; local-server-type = user
; enable-shm = yes
; shm-size-bytes = 0 # setting this 0 will use the system-default, usually 64 MiB
; lock-memory = no
; cpu-limit = no

high-priority = yes
nice-level = -11

realtime-scheduling = yes
; realtime-priority = 5

; exit-idle-time = 20
; scache-idle-time = 20

; dl-search-path = (depends on architecture)

; load-default-script-file = yes
; default-script-file = /etc/pulse/default.pa

; log-target = auto
; log-level = notice
; log-meta = no
; log-time = no
; log-backtrace = 0

# resample-method = speex-float-7
resample-method =  src-sinc-medium-quality
# resample-method = src-sinc-best-quality
enable-remixing = yes
enable-lfe-remixing = yes

flat-volumes = no

; rlimit-fsize = -1
; rlimit-data = -1
; rlimit-stack = -1
; rlimit-core = -1
; rlimit-as = -1
; rlimit-rss = -1
; rlimit-nproc = -1
; rlimit-nofile = 256
; rlimit-memlock = -1
; rlimit-locks = -1
; rlimit-sigpending = -1
; rlimit-msgqueue = -1
; rlimit-nice = 31
; rlimit-rtprio = 9
; rlimit-rttime = 1000000

default-sample-format = s24le
default-sample-rate = 48000
default-sample-channels = 6
default-channel-map = front-left,front-right,rear-left,rear-right,front-center,lfe

default-fragments = 2
default-fragment-size-msec = 5

; enable-deferred-volume = yes
deferred-volume-safety-margin-usec = 1
; deferred-volume-extra-delay-usec = 0

```

---

### Post by midfingr on 2013-03-05
Awesome!! :biggrin: Thank you for letting me know.

I made some progress too. Turns out the connections at the back were incorrect; took hours to figure them out.

Also. The script. Is that the default.pa or the other system script? In any case, I was messing around with something similar, but I completely broke pulseaudio -- lol! Good thing I made a backup so alls well.

Here's something to type in the console for a speaker test:

```
speaker-test  -c6 -l1 -twav
```

---

### Post by caracalsef on 2013-03-06
```

Also. The script. Is that the default.pa or the other system script? 

```
I didn't understood the question...sorry. :-s
Now I have other thig that bug me. I can get a clear sound when watching youtube clips, but when I play a movie, sometimes the sound goes to high. And overall volume is to low. I mean, if I set speakers to a volume to hear good in youtube, in movies I can't hear almost anything (except for high volume on some parts of the movie). If I set the proper volume for movies, if I play a youtube clip, the volume is WAY to high! :D

---

### Post by midfingr on 2013-03-07
No worries about the question. I saw that it was a daemon config file.

That sounds like a common problem everyone has. It has to do with going from stereo to a surround mix and other variations. To be sure however, are voices in movies hard to hear? You turn up the volume. a loud part happens and you're blasted out of the room? That's not just computers, but on legacy equipment as well.

What player(s) do you use to watch movies? i.e. VLC, Totem, other? VLC offers a lot of sound customization for example.

EDIT: Here's one example for adjusting volume in VLC Player: [http://www.instantfundas.com/2012/06/dialogues-too-quiet-action-too-loud-use.html](http://www.instantfundas.com/2012/06/dialogues-too-quiet-action-too-loud-use.html)

---

### Post by caracalsef on 2013-03-07
I use smplayer to watch movies and I think all of them are 6 channels.

Yes, that was the problem. Low voices and then...BOOM, some loud scene from the movie :D

I kinda solved this by checking normalize volume box in smplayer options. It was ticked by default, but I unchecked it :D

Well, so far I like Ubuntu and I'm 3 days without windows :))

---

### Post by midfingr on 2013-03-08
Smplayer, excellent media software. I use that as well.

One movie notorious for that is Matrix. If you have a copy, try getting that balanced out.

Congrats on your days with Ubuntu/Linux! So, did you completely trash Windows? ;)

---

### Post by caracalsef on 2013-03-09
Until now, no. I still have dual boot with Ubuntu 12.10 and Windows 8, but I think of getting more disk space to Ubuntu from Windows :D I don't know if I'll remove Windows for good. I'm still waiting to see what apps I miss on Ubuntu and can't run them.

It's a good thing anyway, as my thought, when I installed Ubuntu, was just to develop some kernel for my android device, but I liked it very much :))

---

### Post by midfingr on 2013-03-09
Wow. Ubuntu 12.10 and you still like Ubuntu? :D -- lol! I had problems with that release, crashes, horrible video driver installation. Wait until Ubuntu 13.04 is released. I'm using the alpha version, it's more stable and reliable than most of the past releases.

I use Win8 too and think it's really good for a Windows release. Although, I don't dual-boot and pointed grub to the hard drive Ubuntu is installed; easy if you have multiple hard drives of course.

I find that Windows is still the best platform for gaming; wait and see on Steam... A decent blogging client is hard to find in Linux. i.e. a  Windows Live Writer alternative. Other than that, most is either as good as or better in Ubuntu/Linux.

---

