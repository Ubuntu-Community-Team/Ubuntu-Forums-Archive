---
title: "Reception Redux"
date: 2008-11-09
forum: Mythbuntu
---

### Post by dsbw on 2008-11-09
It's beginning to look to me like not all receivers are equal.

Which is to say, if I plug my antenna into the TV, I get a couple dozen channels that mostly come in clear. If I plug my antenna into the KWorld ATSC 115, I get a half-dozen channels that are flaky.

Is that the receiver, or is that Myth? I don't know why it would be the latter, but I've heard some suggestions that MythTV is somewhat finicky signal-wise.

If it is the card, what are some better options? HD Homerun seems to be one, but what else?

---

### Post by novellahub on 2008-11-10
I guess the first question is what antenna you are using?  I use a amplified antenna to pull in stations that are 27 miles from my location.  

[http://ubuntuforums.org/showpost.php?p=5886923&postcount=6](http://ubuntuforums.org/showpost.php?p=5886923&postcount=6)

I have four Kworld 115 cards in my Master box and it has been working flawlessly. I even use a cable TV splitter to share the signal between all four.  Thursdays are my biggest night for recording with all 4 recording at once.

---

### Post by newlinux on 2008-11-10
Is it tuning problems you are having or is it display problems (or both).
If display problems, are you comparing digital stations or analog stations? Analog station quality does vary with capture hardware, but digital stations shouldn't (just what stations you get clearly might vary based on tuning sensitivity). You may need to play with playback profiles. 

I've got my 3 kworld's  digital and analog reception looking as good as my TV's digital and analog reception (and the cards are located on different backends), using multiple splitters as well. But there definitely can be a difference in tuning sensitivity - you may need to change antennas or play with the location, etc.

---

### Post by dsbw on 2008-11-11
Hmmm. I'm just talking about digital here.

What I do is take my antenna that's working on my TV, then plug it (without moving anything) into the computer. Much poorer results.

How do you tell, on a myth system, when you're adjusting correctly?

---

### Post by novellahub on 2008-11-12
Bring up live tv and press F7 for the signal strength meter.  Then adjust from there.

---

### Post by dsbw on 2008-11-13
Thanks, I'll give that a try.

---

### Post by tradewinds on 2008-11-25
Hi,
For those that have multiple Kworld 115 on a recent kernel version, is there anything or special settings you needed to use? I have two cards, but only one is showing. For the one that is not, here is what I get with MPlayer. Any help is very much appreciated:

```
mplayer dvb://
MPlayer dev-SVN-r27637-4.3-openSUSE Linux 11.0 (x86_64)-Packman (C) 2000-2008 MPlayer Team
CPU: AMD Athlon(tm) Dual Core Processor 4850e (Family: 15, Model: 107, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing dvb://.
dvb_tune Freq: 473028615
Not able to lock to the signal on the given frequency, timeout: 30
dvb_tune, TUNING FAILED
ERROR, COULDN'T SET CHANNEL  0: Failed to open dvb://.
Select error: Bad file descriptor


Exiting... (End of file)
```

---

### Post by agamotto on 2008-11-27
Also, bear in mind that some stations in your area may not be broadcasting at full power until February.

---

