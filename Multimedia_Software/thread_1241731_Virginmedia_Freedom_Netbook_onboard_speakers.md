---
title: "Virginmedia Freedom Netbook onboard speakers"
date: 2009-08-16
forum: Multimedia Software
---

### Post by macstevejb on 2009-08-16
No matter what I try, I cant seem to get the speakers to work on this little netbook. Sound works elsewhere...output via jack and inputs etc.

I have compiled and installed the latest Alsa drivers v1.20.0.

Anyone experienced similar problems and came up with a fix?

Thanks :)

---

### Post by leeagt on 2009-08-17
/etc/modprobe.d/alsa-base
 
Add options snd-hda-intel model=  <Still trying to work out what should be here>
 
 
to the bottom of that configuration file.
 
I'll report back if i get it to work

---

