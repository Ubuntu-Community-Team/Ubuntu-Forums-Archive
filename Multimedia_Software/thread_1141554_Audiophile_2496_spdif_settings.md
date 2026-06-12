---
title: "Audiophile 2496 spdif settings"
date: 2009-04-28
forum: Multimedia Software
---

### Post by mag1 on 2009-04-28
Hi, i've searched and played around with them for a while and just can't work out what the right combo of drivers and volume settings are to get audio over spdif, i suspect its fairly simple but there's so many and none are really that descriptive, it works fine under xp as i use it for both analogue and digital pass through, all i want is analogue here though, really appreciate the help thanks! :)

---

### Post by mag1 on 2009-04-29
Please i still need help with this, it sucks to not have sound when you need it! :(

---

### Post by mag1 on 2009-04-29
I've played around a bit more and after using gstreamer-properties i managed to at least get a test tone on the second pulse audio unknown device, still not getting sound elsewhere, any ideas? :confused:

---

### Post by mag1 on 2009-04-29
Well i managed to fix it myself, a shame the forum wasn't so helpful to someone who had just signed up, oh well...

To anyone else looking for help with this, i fixed it by setting up pulse audio using [this guide]("http://ubuntuforums.org/showthread.php?t=866965"), make sure to have all the multi's to max under the alsa mixer in the standard volume control, add them and anything else under preferences if need be, set both iec958 to digital mixer under the options tab, i kept the master volume to around 80%.

---

