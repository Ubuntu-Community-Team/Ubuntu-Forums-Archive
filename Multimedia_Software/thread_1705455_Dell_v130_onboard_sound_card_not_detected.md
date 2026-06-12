---
title: "Dell v130 onboard sound card not detected"
date: 2011-03-12
forum: Multimedia Software
---

### Post by mg620 on 2011-03-12
I received my shiny new v130 with 10.04 last week.  (Sold my iPad and finally got what I really wanted!)  10.04 was pretty buggy, so I went through the upgrade process for 10.10, but the system hung for 12 hours halfway through.  When restarted, the system was broken.  I did a fresh install of 10.10.

The onboard sound is no longer detected.  It is an IDT 92HD79.

I have tried to follow the steps at [http://ubuntuforums.org/showthread.php?t=205449&highlight=auto-detect+sound+card&#65279;](http://ubuntuforums.org/showthread.php?t=205449&highlight=auto-detect+sound+card&#65279;)

When I type **aplay -l**, the output is **aplay: device_list:221: no soundcard found...**

When I type **lspci -v** there is no audio or sound shown.

I have checked the BIOS and the audio is detected and listed there.

Any way to get the system to detect the onboard sound or should I just freshly reinstall the original 10.04 from the CD that came with the system?

Thanks

---

### Post by mg620 on 2011-03-15
Anyone?

---

### Post by bnawals on 2011-04-28
Did u try updating the alsa drivers???

---

