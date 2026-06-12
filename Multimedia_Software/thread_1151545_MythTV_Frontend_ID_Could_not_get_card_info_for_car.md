---
title: "MythTV: Frontend ID: Could not get card info for card #0 (udev?)"
date: 2009-05-07
forum: Multimedia Software
---

### Post by particleMan86 on 2009-05-07
I have a DVICO dual tuner (HDTV Fusion) that usually works well with MythTV but every once in a while it just doesn't. I try to click "Watch TV" and the screen blinks and stays on the menu. I did some digging and noticed that when this happens, mythtv-setup also fails to recognize the card. The message is:

"Frontend ID: Could not get card info for card #0 Subtype: Unknown error"

It also seems that when this happens, the /dev/dvb nodes don't exist (normally the tuners live there as adapter0 and adapter1). I think that udev is responsible for creating those nodes, so it may be a problem there. It's very strange, though, that it is so intermittent. Up til now I have just been restarting until the problem goes away, because I didn't know which subsystem to restart, or how (is there a way to restart udev?).

Anyone else have experience with this issue? I have searched on the mythtv forums and here but haven't found any solutions.

Thanks!

---

### Post by adamclinch on 2009-08-08
make sure there are appropriate permissions on your /dev/dvb stuff

---

