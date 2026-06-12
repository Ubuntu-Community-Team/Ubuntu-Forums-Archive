---
title: "Can't connect to pulseaudio server on Ubuntu server Meerkat"
date: 2010-10-24
forum: Multimedia Software
---

### Post by PureW on 2010-10-24
Hello,

I'm trying to run Pulseaudio on my server connected to my stereo so that I can stream wonderful music from everywhere. :)

The problem is that I can play sound from inside the pulseaudio command-line but not from anywhere else. It is as if no one can find the pulseaudio-server. This is all locally on the server, I haven't started streaming over the network yet.

This works fine:
> anders@Sparrow:~$ pulseaudio -C
Welcome to PulseAudio! Use "help" for usage information.
>>> play-file /home/anders/Strings.wav 0
>>> 

Nothing else works:
> anders@Sparrow:~$ aplay -Dpulse 
ALSA lib pulse.c:229:(pulse_connect) PulseAudio: Unable to connect: Connection refused

aplay: main:654: audio open error: Connection refused
anders@Sparrow:~$ pactl stat
Connection failure: Connection refused
pa_context_connect() failed: Connection refused
anders@Sparrow:~$ 

The behavior is the same regardless on if pulseaudio is running or not.

The log from starting and killing pulseaudio ( **pulseaudio -v 2> log-pulse** ). Trying to connect to pulseaudio gives no response in the log.
[http://pastebin.com/TwRDsQ79](http://pastebin.com/TwRDsQ79)

My config-files should be pretty default:
daemon.conf: [http://pastebin.com/iLun8Fpa](http://pastebin.com/iLun8Fpa)
default.pa: [http://pastebin.com/5yBkZ03R](http://pastebin.com/5yBkZ03R)

---

### Post by PureW on 2010-10-24
How should I continue trouble-shooting this? I have no idea where to begin. When I google I don't really see anyone with a similar problem.

---

### Post by Don Geddis on 2011-06-29
Don't know if this has anything to do with your problem.  But I had a possibly similar sound issue with Ubuntu.  <https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/162399/+index> and <https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/162266>.

The two relevant things turned out to be: (1) reconfigure pulse-audio to run at startup, instead of at user login; and (2) add my username to the "audio" group in /etc/group.

---

### Post by benjabean1 on 2012-03-04
How do you set up something to run at startup, but not user login?

---

