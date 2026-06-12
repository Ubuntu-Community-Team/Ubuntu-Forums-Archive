---
title: "Have pulseaudio lock the sound device"
date: 2008-10-19
forum: Multimedia Software
---

### Post by msundman on 2008-10-19
Every once in a while some application manages to aquire an exclusive lock on the sound device and then no application can play sounds using pulseaudio. So how can I make pulseaudio **keep** the sound device locked for its use?

---

### Post by markbuntu on 2008-10-20
You need to get all your applications using pulseaudio, then you won't be having these problems. I have laid out how to do this in my guide here:


[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

Just skip down to the Multiple Application Sound Sharing section and go from there.

---

### Post by msundman on 2008-10-21
> **markbuntu said:**
> You need to get all your applications using pulseaudio, then you won't be having these problems. I have laid out how to do this in my guide here: [...]

That will never, ever work. Of course I have configured alsa to use pulse by default, but there is no way I can stop every oss/jack/whathaveyou-program from accessing the sound device directly.
Therefore I need to make sure that pulseaudio gets a lock on the sound device first, and **keeps** the lock once it gets it.
(Or at the very least I would need some way to detect which non-pulse-application is keeping the sound device locked. However, that would just fix the symptoms, and I'd rather fix the problem, which is that pulse shouldn't let others get exclusive locks on the sound device.)

---

### Post by markbuntu on 2008-10-21
There is no way you can do that with jack but you can do that with all alsa and oss applications.

If you are using jack, you can use the pulse-audio-module-jack which will create a jack sink and source which you can use to route alsa oss and pulseaudio applications through pulseaudio to jack. In my guide linked above I have an explanation how to set this up. There is currently no other way to use jack and pulseaudio at the same time.

Everything in my guide has been tried by myself and many other people and it works on Hardy 8.04 i386 and amd64 generic installs and on 8.04 UbuntuStudio i386 and UbuntuStudio amd64 on all kernels from 2.6.24-16 to 2.6.24-21 both generic and rt.

---

### Post by msundman on 2008-10-21
> **markbuntu said:**
> There is no way you can do that with jack but you can do that with all alsa and oss applications.
No, I can't. I can't force any application to lock the sound device.

> **markbuntu said:**
> Everything in my guide has been tried by myself and many other people and it works on [...]
I'm sure it works, but your solution is for another problem than what I've presented.
I don't want to go through all apps and check what sound system they use and prefix all launchers with padsp or somesuch. That's just fixing the symptoms.
I want to start by making sure **pulseaudio gets and keeps its lock on the sound device** so that no other app -- whether using oss, alsa, jack or something else -- can get an exclusive lock on the sound device.
*After that* if some app can't play sound, *and* I want it to, *only then* will I do whatever configuration-changes that's needed to make it play sound through pulseaudio.

Let me once more state what I want:
**I need there to be *no way what so ever* for any application to lock out pulseaudio from accessing the sound device.**

---

### Post by markbuntu on 2008-10-21
> **msundman said:**
> No, I can't. I can't force any application to lock the sound device.


I'm sure it works, but your solution is for another problem than what I've presented.
I don't want to go through all apps and check what sound system they use and prefix all launchers with padsp or somesuch. That's just fixing the symptoms.
I want to start by making sure **pulseaudio gets and keeps its lock on the sound device** so that no other app -- whether using oss, alsa, jack or something else -- can get an exclusive lock on the sound device.
*After that* if some app can't play sound, *and* I want it to, *only then* will I do whatever configuration-changes that's needed to make it play sound through pulseaudio.

Let me once more state what I want:
**I need there to be *no way what so ever* for any application to lock out pulseaudio from accessing the sound device.**


Pulseaudio provides on demand services, if no application is asking for a device pulseaudio will not try to control it. Pulseaudio can make use of many system resource and it makes no sense to tie them all up if no application is using them. 

If you want pulseaudio to lock the sound hardware, just start some applications that uses pulseaudio and leave it running with the volume turned all the way down.

You can go to pulseaudio.org and ask Lennart if he will change this for you.

---

### Post by msundman on 2008-10-21
> **markbuntu said:**
> If you want pulseaudio to lock the sound hardware, just start some applications that uses pulseaudio and leave it running with the volume turned all the way down.
Now we're talking, that is precisely what I need! The problem is that apps using pulseaudio only use the device when actually playing sound (or maybe also when adjusting levels or somesuch), so I need an app that doesn't let pulseaudio let go of the sound device. I don't know which actions hold the sound device for how long, but it would be nice if the app could either do something else than actually play sound (which could be e.g. a wav of nothing but silence) or mute its own volume (or adjust it to 0).

---

### Post by markbuntu on 2008-10-21
Just start Rythmbox and play an internet radio station. Pulseaudio will own the hardware as long as the radio plays.

If you want to actually control pulseaudio you need to use pavucontrol which is the pulseaudio volume control. You can set the volume of individual applications with it, change devices etc, etc. Multiple applications can run at the same time, each with its own volume control.

You really should look through my guide, starting at the Packages section.

---

### Post by msundman on 2008-10-21
> **markbuntu said:**
> Just start Rythmbox and play an internet radio station. Pulseaudio will own the hardware as long as the radio plays.
That's way, way worse than my "unless I can find come up with something better"-scenario of having a small audio app loop a wav of just silence.

> **markbuntu said:**
> If you want to actually control pulseaudio you need to use pavucontrol which is the pulseaudio volume control. You can set the volume of individual applications with it, change devices etc, etc. Multiple applications can run at the same time, each with its own volume control.
I know that you can adjust the volume per app, which I also wrote in the message you're replying to, so I don't understand why you just keep telling me things that you know I already know.

Now, what I don't know is if there is some app that uses pulseaudio in a less resource-"intensive" way but yet manages to have pulseaudio keep its hold on the sound device. I also don't know if there is some small audio-player that can adjust its volume in such a way that no other app's volume is affected. (Not that I've even tried, because the whole audio-player-playing-silence is, as I said, an "if all else fails"-scenario.)

> **markbuntu said:**
> You really should look through my guide, starting at the Packages section.
I've skimmed through it and found nothing I didn't already know.

---

### Post by markbuntu on 2008-10-22
Pulseaudio is just not designed to do what you want it to. You can ask Lennart at pulseaudio.org if he will change that for you.

---

### Post by msundman on 2008-10-25
> **msundman said:**
> how can I make pulseaudio **keep** the sound device locked for its use?
According to some helpful guys on the #pulseaudio IRC channel the only thing needed is to uncomment the line "load-module module-suspend-on-idle" in /etc/pulse/default.pa and then either rebooting or unloading the module using pacmd.
I'm going to try this for a while and if it seems to work as expected without any side-effects then I'll mark this thread as solved.

---

### Post by rtg on 2009-11-06
In order not to leave the thread as "I will try and respond if it works" and no answer afterwards...

My audio chip produced clicking sounds when pulseaudio was closing the device. Since I don't have sound coming out permanently these clicks were pretty scary when multiplied by a decent external audio amplifier :).

So by commenting out the following lines in /etc/pulse/default.pa
```
### Automatically suspend sinks/sources that become idle for too long
load-module module-suspend-on-idle
```
I now have a click-free experience :)

---

