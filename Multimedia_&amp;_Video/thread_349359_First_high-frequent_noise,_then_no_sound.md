---
title: "First high-frequent noise, then no sound"
date: 2007-01-30
forum: Multimedia &amp; Video
---

### Post by knahrvorn on 2007-01-30
I've just installed Edgy on a new computer. It has an Asus P5LD2 SE main board with an on-board Intel sound card (with both analogue and digital outputs). However, sound doesn't work very well. After booting the system, when logging in, the default log-in sound is played, although with a loud, very high-frequent tone in over it. Later, there's no sound from any program, yet the programs don't complain about a missing sound card or similar; they just keep playing with nothing coming from the speakers. If I try to log out and back in, even the log-in sound isn't played any more (until I reboot, after which the same thing happens again). What might be wrong, and how do I solve it?

Unfortunately, the [Comprehensive Sound Problem Solutions Guide](http://www.ubuntuforums.org/showthread.php?t=205449) didn't help much; the first question asked yields success, although there isn't...

$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by deadgobby on 2007-01-30
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)
 This may work.
Gobby

---

### Post by knahrvorn on 2007-01-30
> **deadgobby said:**
> [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)
 This may work.
Gobby

Great, thanks! This worked, indeed! Just manually upgraded to the newest RC of alsa.  Too bad that it doesn't just work out of the box like it did with my old machine. I hope the next Ubuntu release will include this newer alsa version.

---

