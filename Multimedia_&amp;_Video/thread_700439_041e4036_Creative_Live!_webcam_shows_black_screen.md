---
title: "041e:4036 Creative Live! webcam shows black screen"
date: 2008-02-18
forum: Multimedia &amp; Video
---

### Post by popcornisgood on 2008-02-18
I have a Creative Live! webcam, which I have read is supported, but whenever I try to use it in anything other than Ekiga, it just shows a black screen.  I also have a Pinnacle TV Tuner, and I know that the TV tuner is considered the /dev/video0 device, and my webcam is /dev/video1.  Ekiga is the only thing I've used so far that actually asked me which video device to use.  Camorama doesn't seem to let you change video devices, and in Camorama, it shows a black screen.  I did notice that in Camorama, the black screen is a wider aspect ratio than my camera outputs, which makes me think it might be looking at the TV tuner instead of the webcam.

Is there any way to make the Creative Webcam my default video device, or is this really just a driver problem?  Or did I completely miss it and is this problem something else entirely?  I'm lost, so any help would be appreciated!

---

### Post by ArchangHell on 2008-02-19
Not the same problem, but the same hardware, so i kinda "parasite" your thread :)

First trying to answer: stupid solution occurred me, rename the filles video0 to video1.

Second, if someone can help, I also have a creative live and a pinnacle PCTV, but only have /dev/video0 (pinnacle), so in Ekiga I cannot choose the webcam.

It is connected:
Bus 001 Device 002: ID 041e:4038 Creative Technology, Ltd

Any ideas?

---

### Post by YannickDefais on 2008-02-20
Hi,

[https://help.ubuntu.com/community/Ekiga#head-3274890d77ff130ffdf41a390af294cc6769b8e7](https://help.ubuntu.com/community/Ekiga#head-3274890d77ff130ffdf41a390af294cc6769b8e7)

Did you try this?

From the Edit menu, choose Preferences &#8594; Devices &#8594; Video device. Change the channel number until you find the right one.

Regards,
Yannick

---

