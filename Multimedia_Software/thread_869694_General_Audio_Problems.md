---
title: "General Audio Problems"
date: 2008-07-25
forum: Multimedia Software
---

### Post by Myiasia on 2008-07-25
Okay, now I know this path has likely been beaten before, but it's overgrown enough I can't seem to find what I'm looking for - so, here we go. Oh, and feel free to skip the following big chunk to the numbered questions. I've posted results of lspci and alay at the bottom. :p

 First off, I've been using Ubuntu for a few years now, and every trip down this bumpy road I call "Linux Woes" (no offense, of course. I love Linux, especially Ubuntu - but let's face it. It doesn't like change!) has been a pretty good learning experience. But one thing has always bothered me: Its audio support, even today, seems to be 5 to 10 years behind everyone else, depending on the situation. What're my questions?

 1: How on Earth do I get a single sound system (JUST Pulse/Alsa, or JUST ESD/Alsa) so they're not fighting?

 2: Is it even possible to get rid of OSS without busting something? I tried once, following a more experienced user's instructions, and my sound disappeared completely.

 3: Once I got PulseAudio installed, I noticed a horrible latency problem in most of my applications (although, Gnome's system sounds had no delay) - up to a second in most cases. Is there a way to get rid of this?

 4: I have disabled my onboard audio and placed a SoundBlaster Audigy LS/SE in its place, and it didn't correct my latency problems in Pulse (some threads mentioned the latency being hardware-based). In fact, the only thing it did is confuse my speakers - it thinks my rear speakers are my front speakers. How to fix this? (EDIT: I've fixed the reversed speaker output problem. Simply put, this one was user error. One of my solder jobs was sloppy from when I replaced a popped capacitor)

 Any help is greatly appreciated. And just a note, I've been using Windows most of my life (I still prefer it for general gaming) - so if I seem somewhat incompetent, point it out so I can learn s'more! :p

aplay -l results:
**** List of PLAYBACK Hardware Devices ****
card 0: CA0106 [CA0106], device 0: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 1: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 2: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 3: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

lspci -v relevant results:
03:03.0 Multimedia audio controller: Creative Labs SB Audigy LS
	Subsystem: Creative Labs Unknown device 100a
	Flags: bus master, medium devsel, latency 64, IRQ 22
	I/O ports at e400 [size=32]
	Capabilities: [dc] Power Management version 2

Further info about my machine: [http://valid.x86-secret.com/show_oc.php?id=382995](http://valid.x86-secret.com/show_oc.php?id=382995)
(As taken from Windows - it was just easier to use CPU-Z on it. :p)

---

### Post by Myiasia on 2008-07-26
Anyone at all got any info to help out with this?

---

### Post by Myiasia on 2008-07-26
Still having issues, here, and running out of time. Worst comes to worse, I may just give up on Linux 'til it catches up with Windows or even MacOS in sound capabilities. :p

I've found how to remove things, but it's not helping me decide what to use! Need some pointers and (possibly) opinions on what seems to work best for multiple streams/sounds (for example, playing a game while listening to music through XMMS, or just general audio editing between a few programs, nix that nasty 1-second latency problem).

---

### Post by markbuntu on 2008-07-26
Try this, It is fairly longwinded but you don't really have to do too much messing around with stuff and you can easily put it back the way it was if it does not work out. I wrote it after being continually frustrated by all the other guides not working. You can probably figure out which sound card to choose which is the only really tricky part.

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by Myiasia on 2008-07-27
> **markbuntu said:**
> Try this, It is fairly longwinded but you don't really have to do too much messing around with stuff and you can easily put it back the way it was if it does not work out. I wrote it after being continually frustrated by all the other guides not working. You can probably figure out which sound card to choose which is the only really tricky part.

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

Thanks! I'll have a look at this tomorrow when I've the time to do so. :)

---

