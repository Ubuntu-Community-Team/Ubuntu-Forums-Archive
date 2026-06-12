---
title: "Jack, PulseAudio, and rtprio"
date: 2011-03-23
forum: Multimedia Software
---

### Post by balkce on 2011-03-23
Hi,

I've been dabbling in using Jack and PulseAudio over each other. I'm using 10.10, with jack2 and pulseaudio from repository.

As of now, I've been able to "connect" the two via:

```
pactl load-module module-jack-sink
pactl load-module module-jack-source
```after JACK has started.

Everything was well until some days ago I noticed that the data from the microphones connected to my external sound card started giving out crackling and severe artefacts some time (2-3 minutes) after JACK was started. I noticed that the following error appeared in the system logs around the time the crackling started:

```
Mar 22 22:48:40 Aliquis pulseaudio[2205]: module-jack-source.c: JACK error >JackActivationCount::Signal value = 0 ref = 4<
```Afters some search in the interwebs ( [http://www.linuxmusicians.com/viewtopic.php?f=27&t=3076](http://www.linuxmusicians.com/viewtopic.php?f=27&t=3076) ) , I found that the error means:

> your jack client take to long to get ready, try to set a higher priory to jack or / and use a higher frame buffer.The way that I'm doing things, PulseAudio is acting as a JACK client, so that makes sense.

Right now, I'm trying out if a higher frame buffer does the trick (10 minutes and no crackling; good sign). However, I also wanted to see if increasing the priority of JACK could also help.

JACK's priority was set to (default), which defaults to an rtprio of 10. I understand that, by default, the priorities of JACK's clients (which should include PulseAudio: [http://linux.die.net/man/5/pulse-daemon.conf](http://linux.die.net/man/5/pulse-daemon.conf) ) are set to 9.

Before I even attempted anything I noticed that every time I conjured up the pactl lines above, the following error on the system logs would appear:

```
Mar 22 23:01:23 Aliquis pulseaudio[2213]: module-jack-sink.c: JACK error >Cannot use real-time scheduling (RR/5)(1: Operation not permitted)<
Mar 22 23:01:23 Aliquis pulseaudio[2213]: module-jack-sink.c: JACK error >AcquireRealTime error<
Mar 22 23:01:23 Aliquis pulseaudio[2213]: module-jack-source.c: JACK error >Cannot use real-time scheduling (RR/5)(1: Operation not permitted)<
Mar 22 23:01:23 Aliquis pulseaudio[2213]: module-jack-source.c: JACK error >AcquireRealTime error<
```I changed the realtime-priority in /etc/pulse/daemon.conf to 9, and the above error disappeared, which is good.

However, when I changed JACK's priority to something other than default (which is what I need to do to see if a higher priority takes away the microphone crackling), the above error returned. I understand that the number in (RR/#) in the above error lines is the priority that pactl attempted to set itself on, so I've changed the realtime-priority setting (as well as the rlimit-rtprio setting to let it grow) in /etc/pulse/daemon.conf to be the same as that number, and doing

```
ps -Leo rtprio,cmd,pid | grep audio 
```I can see that PulseAudio had acquired the priority setting that I set in daemon.conf, but the error still came back.

Basically, my first question here is: has anybody else tried to change JACK's priority while maintaining an error-free communication with PulseAudio?

And, when changing the default JACK's priority, to what rtprio setting should I change PulseAudio priority so that the above error doesn't occur?

Thanks,

Caleb

PS. I have added myself to the audio group, and the audio group has its security/limits set adequately. In fact, JACK is running in realtime mode by itself without much problems. When doing 
```
ps -Leo rtprio,cmd,pid | grep jack
```I can see that JACK has the priority setting I gave it.

The problem here is that pactl is not letting the connection between PulseAudio and JACK be realtime (am I understanding this correctly?).

---

