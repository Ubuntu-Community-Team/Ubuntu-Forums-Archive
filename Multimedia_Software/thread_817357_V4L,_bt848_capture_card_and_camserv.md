---
title: "V4L, bt848 capture card and camserv"
date: 2008-06-03
forum: Multimedia Software
---

### Post by steph291 on 2008-06-03
Hi everyone,

I'm having problem with camserv and my pci capture card.

1. I have 2 webcam on my ubuntu system: a logitech quickcam express
and a pci capture card with bt848 chipset. (3com bigpicture)

2. tested with xawtv and vlc, those works fine and even at the same time.
(two instance of xawtv)

3. I can stream out the video with vlc (two instance of vlc) for both
webcam.

4. BUT... camserv return and V4L error when I try to stream my pci
capture card :mad: which works fine with my logitech quickcam.

here's the nessage :
(V4L) mmap: Invalid argument

I've been reading forums for months, no answer.
Please help 

Thanks
Edit : I switch from 6.06 to 8.04, will see the result in a couple of days ...
still looking for answers

Edit : I'm stuck at resolution 800x600 and xorg.conf is not containing any usefull
line that I can modify :(

Edit1: under debian etch, I have a wintv bt878, tested with xawtv it's working fine
camserv returned error :
(v4l) mmap: invalid argument

---

### Post by ddoxey on 2009-04-07
I had a similar problem running two webcams with camserv on my system.
I don't recall the exact error message.
But the problem turned out to be that two high speed devices couldn't be run simultaneously on the same USB bus.

The solution was to plug one of the cameras into a different port, on the back of the box. Of course there's no guarantee that the proximity of the physical ports assures you that they're on different buses internally. But in my case this solution worked.

I hope that helps.

---

