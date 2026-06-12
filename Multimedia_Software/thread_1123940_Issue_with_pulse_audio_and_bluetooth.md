---
title: "Issue with pulse audio and bluetooth"
date: 2009-04-12
forum: Multimedia Software
---

### Post by blah19 on 2009-04-12
Alright, with a lot of messing around I got my bluetooth headset to work for a little bit. While messing around with it (just trying to record and play), it suddenly stopped and aplay yielded the following:
[PHP] ALSA lib pcm_bluetooth.c:381:(bluetooth_prepare) BT_START failed : Input/output error(5)[/PHP]
So I went back through the instructions and was unable to discover the issue. I made sure that it was synced. I relogged and used the following commend to sync with pulseaudio:
[PHP]pactl load-module module-alsa-source device=bluetooth [/PHP]
yielding: Failure: Module initalization failed (in the log:)
[PHP]Apr 12 20:39:43 PCNAME pulseaudio[8945]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted[/PHP]

I've retraced my steps with no avail, and being a novice I'm kinda lost :|
I'd appreciate and help anyone could provide!

---

### Post by markbuntu on 2009-04-12
The Bt has to be successfully paired before running the pactl command or it will fail to load the module. Logging out will remove pairing so you need to establish that again before running pactl

The setlimit(RLIMIT_RTPRIO) problem occurs when you are not a member of one or all of these groups

pulse
pulse-rt
pulse-access

pulse-bluetooth is not especially stable in the pulseaudio version available in hardy and intrepid but it does work for a lot of people.

---

### Post by blah19 on 2009-04-12
> **markbuntu said:**
> The Bt has to be successfully paired before running the pactl command or it will fail to load the module. Logging out will remove pairing so you need to establish that again before running pactl

The setlimit(RLIMIT_RTPRIO) problem occurs when you are not a member of one or all of these groups

pulse
pulse-rt
pulse-access

pulse-bluetooth is not especially stable in the pulseaudio version available in hardy and intrepid but it does work for a lot of people.

I actually did set those permissions already, it is with those set I get the error.

Being synced with the device made no difference  as well.

---

### Post by markbuntu on 2009-04-13
You also need a recent version of bluez from bluez.org. I have been trying off and on for weeks to get my bluetooth headest to work with pulseaudio, once in a while it will work for a little while. 

Supposedly this is all fixed in pulse0.9.15 which will be in Koala. Hmmm, maybe I will try again with Mandriva....

---

