---
title: "Soundcard Troubles"
date: 2006-12-19
forum: Multimedia &amp; Video
---

### Post by StormGuy on 2006-12-19
I seem to be having trouble getting sound on my Ubuntu-d Gateway laptop.  I've been following the Sound Problems Solutions guide, but I can't seem to locate the problem.  

aplay -l returns this:
```

**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

...which, according to the guide (and I could be misunderstanding it...I'm a total newb) should mean that all I need to do is check to see if alsamixer has my sound muted.  But alsamixer has the sound unmuted and at full blast.  I don't know what the problem could be :confused:

---

### Post by StormGuy on 2006-12-19
I still haven't managed to find the problem.   It's odd since it looks like the card is detected under aplay -l.  I am also able to adjust the volume settings on the laptop itself via function keys...I just can't hear anything :confused:

---

