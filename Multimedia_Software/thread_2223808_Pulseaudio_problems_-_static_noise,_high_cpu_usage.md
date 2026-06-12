---
title: "Pulseaudio problems - static noise, high cpu usage"
date: 2014-05-13
forum: Multimedia Software
---

### Post by David_Abergel on 2014-05-13
Hi all.

This problem has been bugging me for a few weeks and despite spending a load of time searching I haven't found an answer.

I'm running xubuntu 14.04 on a standard Dell laptop. Running lspci gives the following information on my audio card:
00:1b.0 Audio device: Inter Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04).

In general, sound works fine. But randomly (usually within the first two hours of using the machine) I will hear a loud crackling or static kind of noise from the speakers. Running top shows that pulseaudio is using 25-30% CPU when this happens. Killing the pulseaudio process stops the noise, and the respawned pulseaudio will allow programs such as VLC to function normally, but the multimedia keys on the keyboard no longer work.

Does anyone else have this bug? Or can you give me some hints for how to fix this?

I've tried reinstalling pulseaudio but that seemed to have no effect.

Thanks.

---

### Post by David_Abergel on 2014-05-15
Anyone?
All help would be very gratefully received.

---

### Post by T.J. on 2014-05-15
Pulseaudio has had a long history of being poorly handling certain audio chipset drivers, I'm afraid. You may be able to solve your problem by adjusting the the driver parameters in the file: /etc/pulse/default.pa.  You will need to have administrator permission to do this.  Be sure to make a backup copy of the file before you make changes, just in case.


Edit the line:
load-module module-udev-detect

and add "tsched=0" so it will be:

load-module module-udev-detect tsched=0

Save it, and then preferably reboot, just to be on the safe side.   Don't worry, this parameter should be perfectly safe to use.  It will force  PulseAudio try to not bulldoze over the sound driver's timing by forcing the scheduler to 0.

Hopefully, that will do it.  Let me know if it persists.

---

### Post by T.J. on 2014-05-15
Save this as a last resort.

Many consider it heresy, but the second solution that would work for certain is to remove PulseAudio entirely. PA is nice to have, but it is hardly an absolute necessity on a personal workstation.  It's just a mixer and audio routing software.  It has known problems, and can be a hindrance if PA does not play nice with the sound driver.  By removing it, you may lose some mixer controls, but you should see your CPU usage drop.

---

### Post by T.J. on 2014-05-15
Sorry, I just realized you may not know how to do the above.  Please let me know if you want me to walk you through it - which I'll be happy to do.

---

### Post by uk.matt.jones on 2014-07-16
I was experiencing exactly the same symptoms on a Dell Latitude e6420 with Ubuntu 14.04. In addition to the problems described by David, pulseaudio was using 10-15% of my i7 processor all of the time, even when there was no audio output.

The edit to /etc/pulse/default.pa suggested by T.J. so far seems to work. I've had no problems after several hours use. Thanks T.J.!

---

