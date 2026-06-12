---
title: "Stuttering and skipping playback in Amarok, Rytnmbox"
date: 2009-05-02
forum: Multimedia Software
---

### Post by ubigT on 2009-05-02
Freakin annoying skipping, stuttering, jumping sound playback. It does not seem to correspond to me scrolling web pages or my use of other programs at all, as other posts have discussed. All music I listen too skips, not video though. My system is by no means bogged down or slow, so i have no idea what is causing this... any ideas?  I got nothing :(
Thanks in advance for any help.

lspci -v

00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
	Subsystem: ASUSTeK Computer Inc. Device 82fe
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at f9ff8000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

---

### Post by atngplusultra on 2009-05-02
i'm having this problem too, and it's clearly based in something new in the Jaunty release.
I have gotten some sound improvements, actually, ever since the upgrade (my headphones and speakers cooperate correctly now)
but I spent some time getting the old Amarok to work on 9.04, and now it's doing what Amarok 2 was doing.
It may be a xine thing? or some other library? i dunno. hhhheeelllppp

---

### Post by psycovic23 on 2009-05-02
I'm having the same problem. VERY annoying. Any soluions?

---

### Post by ubigT on 2009-05-04
I swear this is getting WORSE on my computer, to the point that I don't even listen to music anymore.... Anybody have an idea?


EDIT:
Just found this:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/345627](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/345627)

I'm working now but I'll give it a shot and let you know how it goes...

---

### Post by skotos on 2009-05-04
OK guys, this is one of the most if not simply the most spreaded /devastating problem after the Jaunty upgrade. You all have to start looking for remedies to your pulseaudio-alsa broken configurations. Currently all the threads devoted to multimedia howtos or sound problems propose solutions that do not heal completely but - at least - give us a way to survive...

Here follow a list of some threads you might start looking at

[LIST=1]
[*]howto pulseaudiofixes: [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)
[*]multiple sound solution: [http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)
[*]sound not working: [http://ubuntuforums.org/showthread.php?t=1136670](http://ubuntuforums.org/showthread.php?t=1136670)
[*]amarok 2: [http://ubuntuforums.org/showthread.php?t=1138252](http://ubuntuforums.org/showthread.php?t=1138252)
[/LIST]
This is not a comprehnsive list, just a starter kit to let you understand the kind of problem/solution that might better suite you and therefore seek

---

