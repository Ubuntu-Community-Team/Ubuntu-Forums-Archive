---
title: "[SOLVED] Can't get CD's to play"
date: 2008-10-29
forum: Multimedia Software
---

### Post by Tony Flury on 2008-10-29
I have followed all the instructions in the Sticky thread, and I am still unable to play CDs on my laptop (Audio CDs play fine under Windows) so it is not my CD Drive mechanics, and CD-ROMS work in the drive (i have installed windows games under Wine). I also know that my sound card is fine, as sound works in games, and other applications.

I have Hardy Heron - with all the latest updates.
Laptop is a HP Pavillion dv6512eu - 1GB Ram.

I have tried : 
Rhythmbox - CD is detected and the tracks are listed, but it does not advance the track - and nothing plays.

Amarok - it will detect and list the tracks on the CD - wont advance the tracks, nothing plays, and Amarok seens to freeze when you try to go to the next track.

Audacious - It detects the CD, lists the tracks, wont advance through the track, and forwarding to the next track freezes the application.

The fact that all 3 applications refuse to advance through the tracks suggests something low level about the way Ubuntu plays Audio CDs.

Some assistance would be greatly appreciated :-)

---

### Post by xc3RnbFO8P on 2008-10-29
In Terminal:
> rhythmbox
and try to play CD.
See if there in some errors.

---

### Post by Tony Flury on 2008-10-29
```

tony@laptop:~$ rhythmbox

** (rhythmbox:14117): WARNING **: No property volume.disc.capacity on device with id /org/freedesktop/Hal/devices/volume_part_1_size_705941504


```

So what does that mean ?

---

### Post by xc3RnbFO8P on 2008-10-29
Bug?
Rhythmbox thinks CD is a blank writable CD.
Something to do with HAL.

---

### Post by Tony Flury on 2008-10-29
That is very odd, because it lists the tracks on the CD, and it does the same thing whether it it is faced with a burnt CDRW, or a commercial Audio CD.

Edit : Actual Audio CDs don't give the same error - but don't play either.

All the other players also detect all the tracks (but wont play them), and the tracks show up on the Desktop flder too.

Anyone any ideas how to fix it ?

---

### Post by Tony Flury on 2008-10-30
This is still very very puzzling ... i would be interested in any ideas.

---

### Post by Tony Flury on 2008-10-31
Any assistance on this would be greatly appreciated :-)

---

