---
title: "Headphones output suddenly stopped working. Audio muted with headphones."
date: 2011-10-24
forum: Multimedia Software
---

### Post by vangop on 2011-10-24
Hi,
I've been surprised that when I plugged the headphones the sound LED went red (as with muted) and there was no sound out of the headphones.
It used to work just 5 mins before, and suddenly this.
When I plug them off (regular jack, not USB), the sound is working. Nothing is muted in sound applet, it changes the output from speekers to headphones and back on plug in/off. Tried reboot, didnt help.
Any ideas??

---

### Post by vangop on 2011-10-24
Update: like I said when I plug the H.Ph. in, the sound applet changes the output connector from "Analog Speakers" to "Analog Headphones". 
If I change it back the sound is back to headphones.
WTF and how to fix it??

---

### Post by short4lif2 on 2011-10-25
I'm having a problem with my headphones as well.  The difference is that I don't get analog headphones in my list of output connectors, i only get analog speakers.

---

### Post by vangop on 2011-10-25
Anyone with bright ideas? I tried gksudo gedit /etc/pulse/default.pa and play with some *-restore modules but it didn't seem to have any effect.
BTW I notice that the sound is muted with headphones even before I log in into the desktop session. Since pulseaudio is a per session config, this must be related to smth els?

---

### Post by vangop on 2011-10-26
I've installed some updates and the issue is gone. Not sure if that's related to update though.
Weeeird....

---

