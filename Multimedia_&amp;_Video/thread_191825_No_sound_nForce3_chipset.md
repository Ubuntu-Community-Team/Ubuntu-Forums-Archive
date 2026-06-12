---
title: "No sound nForce3 chipset"
date: 2006-06-08
forum: Multimedia &amp; Video
---

### Post by meesterblack on 2006-06-08
](*,) 

Getting just a little frustrated with my new Ubuntu install.  Been surfing for the last few hours looking for a solution regarding my lack of sound, but alas I am here begging for help.

I'd consider myself an intermediate linux user and I have several Ubuntu installs under my belt now.

I have a Gigabyte AMD64 motherboard with an nVidia nForce3 chipset.  Everything else seems to work fine, however I get no sound output whatsoever.  I am willing to gamble that most likely the issue is related to the jack-sensing crap that is built into the mo-board as the other Dapper installs I've done on other systems have all detected and configured the onboard audio correctly.

In a futile attempt, I went to the nVidia site and downloaded their proprietary driver for my chipset and installed it (after downloading the kernel source, yadda, yadda).  I added a line in my /etc/modprobe.d/alsa-base to include the nvsound driver.  I could be way off -- not a linux hardware expert -- but it was worth a shot.

So far, no dice.  Anyone else encountered issues with jack-sensing??  How about nForce onboard audio issues??

Any help would be appreciated -- let me know if I need to post something...

-m-

---

