---
title: "pulseaudio and alc888 digital in Jaunty"
date: 2009-05-01
forum: Multimedia Software
---

### Post by alkis on 2009-05-01
Hi all,
I am using Jaunty and an SPDIF cable to connect the digital output of my ALC888 card to an external decoder-amplifier, but I experience various sound problems.
After a fresh boot sound seems to be working correctly, but if I play some movies using direct AC3/DTS passthrough, then I get no sound from normal applications (amarok, etc.).
The strange thing is that in the PA volume control applet, in the output devices tab ther is no entry for the alc888 digital, only for the alc888 analog. When something is playing i can see the bar moving but hear nothing.
I have tried various ideas i found around, with no success, but not one was referring exactly to my problem, that is mixing pulseaudio with digital output, so any input would be appreciated.

---

### Post by neu2buntu on 2009-05-01
have you tried [[SIZE=4][COLOR=Red]this[/COLOR][/SIZE]]("http://ubuntuforums.org/showthread.php?t=776958") post?

---

### Post by alkis on 2009-05-01
wow!!!!! worked like a charm!!!!!
thanks a lot!!!
I now have the digital device listed in the output devices, and I can select the one the applications use...sweet!

BUT, I can now hear some strange scratches when music is playing, which did not happen before....any ideas??

---

### Post by neu2buntu on 2009-05-01
have a look at your mic settings , it maybe is feedback....try muting it or changing to nonexisting ext mic?

---

### Post by alkis on 2009-05-02
also, AC3/DTS passthrough for mplayer and vlc stopped working after this fix...:confused:

---

