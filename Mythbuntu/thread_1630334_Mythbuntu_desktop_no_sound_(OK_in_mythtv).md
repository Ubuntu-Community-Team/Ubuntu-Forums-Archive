---
title: "Mythbuntu desktop no sound (OK in mythtv)"
date: 2010-11-25
forum: Mythbuntu
---

### Post by iitywygms on 2010-11-25
Hi All:
Been a while since I have tried but I noticed I no longer get sound out of any aps or flash.  Mplayer for example and no sound on Youtube.
Sound works great in mythtv.
I tried searching but all that comes up is sound problems with mythtv.
I have a acer revo outputting thru the spdif.
Any idea where I can start? Running 10.04 with .24 autobuilds.
Thanks

---

### Post by managementboy on 2010-11-26
> **iitywygms said:**
> Hi All:
Been a while since I have tried but I noticed I no longer get sound out of any aps or flash.  Mplayer for example and no sound on Youtube.
Sound works great in mythtv.
I tried searching but all that comes up is sound problems with mythtv.
I have a acer revo outputting thru the spdif.
Any idea where I can start? Running 10.04 with .24 autobuilds.
Thanks
do you have mythfrontend open at the same time? mythfrontend will block the alsa device for itself. Close mythfrontend and try again.

---

### Post by iitywygms on 2010-11-26
No. I have mythfrontend closed.  I have been able to get partial success by adding a asound.conf file with this inside.

pcm.!default {
  type plug
  slave.pcm iec958
}

Just not sure why it use to work and now it needs a special asound.conf.

---

