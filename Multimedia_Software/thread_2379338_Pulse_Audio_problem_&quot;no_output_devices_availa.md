---
title: "Pulse Audio problem: &quot;no output devices available&quot;"
date: 2017-12-04
forum: Multimedia Software
---

### Post by mire on 2017-12-04
Let me be clear from the on set sounds are playing on my machine. However I can not control the volume in KDE's audio app due to it claiming that no audio devices are found. Please do not mark this as solved until the error message is addressed. Inability to control volume is the problem in view not lack of sound.

---

### Post by mire on 2017-12-04
Found out this is known issue in kubuntu 17.10
[https://bugs.freedesktop.org/show_bug.cgi?id=95104](https://bugs.freedesktop.org/show_bug.cgi?id=95104)
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/1720519](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/1720519)
Basically a configuration error that PulseAudio deems fatal. I have not evaluated the any of the solutions just yet.

---

### Post by Yellow Pasque on 2017-12-04
> * The KCM module for audio configuration has an option under "Advanced" to "Automatically switch all running streams when a new output becomes available". This checkbox updates the PulseAudio gconf configuration /system/pulseaudio/modules/switch-on-connect/enabled and sets it to "true". What that is set, when the PA gconf module gets loaded, it tries to load the switch-on-connect module again - cause PA to crash.

^It would be easiest to uncheck the box.

---

### Post by nedrige2 on 2018-01-03
I had the same problem. 
I have the ubuntu-desktop as well as the kubuntu-desktop installed. 
That caused some problems, until I removed the ~/.gconf folder (  I initially renamed it to gconf.org).

---

### Post by Yellow Pasque on 2018-01-03
> **nedrige2 said:**
> I had the same problem. 
I have the ubuntu-desktop as well as the kubuntu-desktop installed. 
That caused some problems, until I removed the ~/.gconf folder (  I initially renamed it to gconf.org).

Why would you remove the whole folder for one setting?

---

### Post by franzbischoff on 2018-01-10
Solved removing ~/.gconf/system/pulse and ~/.config/pulse and rebooting.

Maybe just the first folder is needed to fix the problem.

---

