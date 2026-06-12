---
title: "can't get usb sound in wolfenstein ET"
date: 2007-04-28
forum: Multimedia &amp; Video
---

### Post by eobard on 2007-04-28
I installed ET, no problem with the install but had no sound. So after searching these and other forums I added the two following lines:
> echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
echo "et.x86 0 0 disable" > /proc/asound/card0/pcm0c/oss
to /etc/init.d/bootmisc.h which gave me sound through my sound card but I need to get it out through my USB headset. I looked around but have found no solution that gets me USB output. Can anyone give me a nudge in the right direction?

---

### Post by eobard on 2007-05-02
Anyone?

---

