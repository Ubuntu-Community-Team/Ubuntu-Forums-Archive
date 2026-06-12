---
title: "how do you watch and record on mutliple tuners"
date: 2010-07-12
forum: Mythbuntu
---

### Post by blkbx on 2010-07-12
I have a win nova t500 which has two usb tuners. I have installed and configured them but I don't know how to use the secound tuner while watching live tv with the first. I figured that I could watch and record on tuner0 and record on tuner1 which was why I bought the card but I have no idea how to use it with mythtv. I'm running mythbuntu 10.04 on a reasonably capable pc.
Thanks for any help given in advance.
Brian

---

### Post by laffinet on 2010-07-12
While watching liveTV bring up the context menu ('m' on a keyboard, whatever corresponding button on a remote, on mine it's the one with the windows logo).

Select "switch input", select the other tuner.

Couple of other things:
1. avoid conflicts with liveTV - there's a check box somewhere in the frontend settings. Forgot where exactly, I think it's under TV settings somewhere. Check "avoid conflicts with liveTV". This should open the tuner that isn't recording when you open liveTV

2. virtual tuners - mythtv can record more than one channel with one (supported) tuner if the channels are on the same multiplex. To enable this, go to mythbackend setup, capture cards. Select your tuner, go to "recording options". Set the number of tuners to more then one.

---

### Post by blkbx on 2010-07-13
Thanks for the help. I think I have it so it can record on the same multiplex. Not sure if it's using the secound tuner though.

---

### Post by itlarson on 2010-07-14
If the first channel number (2 in 2.1 for example) is different from the one being recorded, you have to be using a different tuner.  If the first channel number is the same, but the second one is different, the two channels are on the same multiplex, and you can watch one and record the other (or record both) without using a second tuner.  Note that you can record on both tuners at once as well, and watch one of the recordings as it is being recorded.

---

