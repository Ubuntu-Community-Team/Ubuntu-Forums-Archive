---
title: "Flash 10 starts jumping/forwarding video playback"
date: 2009-05-10
forum: Multimedia Software
---

### Post by James78 on 2009-05-10
Hi,

I use Kubuntu Jaunty Jackalope, I installed Gnome a bit ago and started having sound problems due to Pulseaudio overloading CPU, then it'd shutdown. So I made a attempt to fix this for awhile, and eventually after doing something, flash (latest version) on Firefox 3.0.10 jumps. Basically, I go to any video, I let it play, and it'll be fine for about a minute or 2, then the video will automatically get jumpy, the sound still works, but it sounds like the video is forwarding, and it almost appears to go 2 seconds at a time. Really odd behaviour. Another noticed thing is that when this happens, Firefox jumps from a regular 30% CPU usage to over 80%. If I stop the video and press play again, it plays like it's forwarding, but if I move the video slider, it goes away until about a minute later. I've tried Reinstalling Firefox, and Flash many times, the problem still occurs.

Note: I tried to uninstall all traces of Pulseaudio since it was being a pain, and now my hardware is falling back to my ALSA driver configuration, although in my System Settings -> Multimedia panel, it still says "Pulse Audio" in there for some reason; I put it at the bottom of the list. Libstd pulse won't uninstall without removing the core of KDE for some reason, and Libstd alsa isn't installed at this moment. Video playback in VLC, and music playback in Songbird is flawless (except for small jumps and bumps in the audio, I assume normal? Perhaps not. Pulseaudio didn't bump like that..)

I played a flash video in Songbird, and it does the exact same thing, which leads me to believe it's not flash or the browser that's causing the issue. It almost seems like when I play music, and get these little skips and gaps, actually it seems more like the sound repeats itself, that it's around the same time that the flash video would start doing this annoying problem. For all it seems, I'm still having major sound issues on my system, and that may be the cause. :(

Update: Now, I reinstalled all Pulseaudio related packages, and the whenever sound is played Pulseaudio eats up the cpu after 15 seconds and terminates due to CPU overload. Really, this whole thing is related to something wrong with my sound system, no idea what, but it's frustrating.

Anyone have any ideas? I would like to get this fixed asap!

If anyone wants to see a closer look at it, I can record a video of it.

**^^ Above information INCORRECT. Please see this [post](http://ubuntuforums.org/showpost.php?p=7329402&postcount=8).**

---

### Post by James78 on 2009-05-10
Eh, bump.

---

### Post by James78 on 2009-05-11
Bump..

---

### Post by psyke83 on 2009-05-11
Try to enable the proposed repository and install kernel 2.6.28-12-generic. It provides fixes for intel-hda and intel8x0 sound cards that were causing problems with PulseAudio such as what you describe.

---

### Post by James78 on 2009-05-11
Already had that installed, still had the exact same issues. Downloaded 0.9.15 test 8, compiled and installed. Pulseaudio version information says it's still 0.9.14, it won't start up in the command line, but I have a sh script that automatically starts it up at system startup, and that works great. There appear to be no CPU overloads, and sound quality is far superior to anything I've ever used!

---

### Post by psyke83 on 2009-05-11
> **James78 said:**
> Already had that installed, still had the exact same issues. Downloaded 0.9.15 test 8, compiled and installed. Pulseaudio version information says it's still 0.9.14, it won't start up in the command line, but I have a sh script that automatically starts it up at system startup, and that works great. There appear to be no CPU overloads, and sound quality is far superior to anything I've ever used!

Ok. Note that Luke Yelavich has PA 0.9.15 packages in his [PPA]("https://launchpad.net/~themuso/+archive/ppa").

---

### Post by James78 on 2009-05-11
Added, but new version doesn't seem to be appearing in my package managers..

Edit: Nevermind, Synaptic saw that these packages needed upgraded. Perfect. :) No more issues. Except for the fact that when my system starts up sound won't work at all. If I play a song in Songbird, then kill pulseaudio, it works. Ehh. >.<

---

### Post by James78 on 2009-05-22
It's funny, because it's so extremely hard to find the cause of this issue. Apparently it's NOT solved. Flash still starts jumping around after a few minutes of playing, and apparently it's not only flash related, it happens in other programs that play video as well! When it happens, the audio becomes cracks (like the video is forwarding), and it starts going super fast. Really annoying.. I'm using ALSA drivers right now. Oh, might I mention that when it does this now, it seems the sound repeats the last 1 or 2 seconds and forwards the video. It's really weird.

I'm tired of this and would like it fixed already. Please anyone, have ANY ideas? My filesystem is ext4, but it had this issue with ext3 also, so that can't be an issue.

Related issue: [http://ubuntuforums.org/showthread.php?p=7144994](http://ubuntuforums.org/showthread.php?p=7144994)

---

### Post by szim90 on 2009-05-23
Same exact issue on ubuntu (Jaunty), I think it might have something to do with pulse audio ([http://ubuntuforums.org/showthread.php?t=1135269](http://ubuntuforums.org/showthread.php?t=1135269))

-Sean

---

### Post by James78 on 2009-05-24
It would seem to be extremely closely related, however I do have pulseaudio uninstalled right now, and it's still happening. Haven't tested without having pulseaudio ever being installed. Have original Ubuntu-Desktop components installed (including Gnome).

---

### Post by James78 on 2009-05-24
Set tsched to 1. Haven't noticed any further crashes since. Edited config files: /etc/pulse/default.pa & /usr/local/etc/pulse/default.pa

I still notice messages like "alsa-sink.c: Increasing wakeup watermark to ...ms", but it still seems to work I guess.

No problems with video at all since audio started working. System startup and system logout audio plays fast however, other than that it's good. If you can't get pulseaudio sound to work on startup (system startup sound), and you're using KDE4, try adding pulse-session.sh* to pre-KDE startup.

*Note that pulse-session is originally named pulse-session, without sh extension. Use this command.
```
cp /usr/bin/pulse-session /home/user/.kde/env/pulse-session.sh
```

---

