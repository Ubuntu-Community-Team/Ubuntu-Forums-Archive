---
title: "Adobe Flash no sound"
date: 2008-12-08
forum: Multimedia Software
---

### Post by yingun on 2008-12-08
Hello I have just upgraded from Hardy Heron to the Interpid Ibex. At first everything was working fine (in mplayer, FF Flash and etc), I could hear the sound. But after when I installed Skype and did a few tweakings, my Skype works fine and now I can only watch Youtube video without sound.

I had removed and re-installed my pulseaudio previously.
I had made sure that I have not muted my sound. (I still can play the music using VLC)

I tried this but not working too,
> # Flash also looks for /usr/lib/libesd.so.1
sudo ln -s /usr/lib/libesd.so.0 /usr/lib/libesd.so.1

# Flash expects /tmp/.esd/socket to exist.
sudo mkdir -p /tmp/.esd/
sudo touch /tmp/.esd/socket

I have installed libflashsupport package and not working also.

When I started my FF from the terminal I have these errors

> ALSA lib pcm_pulse.c:625: (pulse_prepare) PulseAudio: Unable to create stream: Invalid argument

> $ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

When I ran this command as stated by this thread [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

> 
 $ pkill pulseaudio; sleep 2; pulseaudio -vv


I got these excerpt which point out the errors

> W: ltdl-bind-now.c: Failed to find original dlopen loader.
E: pid.c: Daemon already running.
E: main.c: pa_pid_file_create() failed.

........

W: ltdl-bind-now.c: Failed to find original dlopen loader.
W: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
W: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted



Here I attached my AlsaMixer setting,
What else should I do to make it work ? Thank you very much.

---

### Post by yingun on 2008-12-08
It's weird, I don't know somehow it's working now. Thanks to all people who have thought of the possible solutions.:lolflag:

---

### Post by zordon on 2008-12-09
got the same problem and don't know what to do; flash is silent; youtube silent :-( not happy after upgrade to interpid

---

### Post by gandaran on 2008-12-09
> **zordon said:**
> got the same problem and don't know what to do; flash is silent; youtube silent :-( not happy after upgrade to interpid
and you still flash 9 installed? get flash 10, it'll fix the problem

---

### Post by zordon on 2008-12-09
thanx, now it works! simple solutions are the best!

---

### Post by yingun on 2008-12-10
I don't know why, mine is not working again. Sometimes it works, but most of the time don't. I already have the flash 10.

---

### Post by yingun on 2008-12-11
If anyone has got the same problem, try complete removal of the flash using synaptic package manager and install it again. This time it really works for me, I hope it will always.

---

