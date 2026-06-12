---
title: "Sound only works well when pavucontrol is open/running..."
date: 2014-07-06
forum: Multimedia Software
---

### Post by neu5eeCh on 2014-07-06
My sound comes through a jack in the back of a Samsung HDMI monitor. If pavucontrol (Pulse Audio Volume Control) is running (as in the window/dialog box is open) then the sound is flawless. As soon as I close it, the sound is badly distorted. Open it? Perfect. Close it? Distorted. Any ideas? All my Google searches are dead ends. Seems like there must be a line that needs to be tweaked somewhere?

---

### Post by neu5eeCh on 2014-07-06
Okay, the solution is incredibly obscure (took me hours of Googling) but here it is (and comes from [here]("https://forums.virtualbox.org/viewtopic.php?f=7&t=23982&sid=9e7c182553a4b99535fe943cea20632f&start=30")):

The gist of it is this:

In the /etc/pulse directory are the following files:

> client.conf daemon.conf default.pa system.pa
[B]
Step 1[/B]: sudo nano default.pa

Look for the following lines:

> Automatically load driver modules depending on the hardware available
Ugly hack for Nexus 10
.ifexists /system/lib/hw/audio.primary.manta.so
load-module module-udev-detect tsched=0
.else
load-module module-udev-detect
.endif

**Step 2**: Hash them all out, and put in the line:

> load-module module-udev-detect tsched=0

So, we're eliminating the if/then statement and invoking the "ugly hack" that worked for the NEXUS 10, which just happens to work for my armhf Cubox-i (and might work in other systems).

---

