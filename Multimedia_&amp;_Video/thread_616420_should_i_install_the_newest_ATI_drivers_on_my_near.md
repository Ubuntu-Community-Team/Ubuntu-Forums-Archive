---
title: "should i install the newest ATI drivers on my nearly fully working gutsy? i'm scared!"
date: 2007-11-18
forum: Multimedia &amp; Video
---

### Post by ijason on 2007-11-18
hey all. i've got my laptop running a fresh install of gutsy, and things are almost 99% working - graphics wise. i don't get direct rendering for my ati m300 card. i've been looking through all the guides, and they're all including adding compiz and flgx drivers as part of the steps... but my distro of gutsy already HAD compiz with it. and my compiz is working fine (as long as i'm on the ubuntu approved drivers).

so, basically i'm afraid of making things worse by messing with flgx / compiz when i may not need to. do i just fetch the new drivers from here ([http://ati.amd.com/support/drivers/linux/linux-radeon.html](http://ati.amd.com/support/drivers/linux/linux-radeon.html)) and install JUST the drivers to get direct rendering? or do i need to do more steps. 

i'd rather not break compiz, which happens when i enable the restricted drivers, and also when i tried upgrading fiesty to different drivers.

---

### Post by aoanla on 2007-11-18
In any case, I'd wait a week for the next iteration of the fglrx driver, which is due out before the end of the month. Bug fixes are expected to be included, so it's worth waiting - rather than doing the upgrade twice...

---

### Post by rondamato on 2007-11-18
I agree.  I did NOT have good luck with Fawn and the ATI drivers with a 2900 on a friends PC (though this may have been due to a faulty keyboard/chair interface...)  I must have dicked around with xconf and the ATI driver for days.  Finally switched him to a NVidia 7600--near PnP install and good drivers (it seems).  It runs his shading/blending applications crazy fast.

Wait for the new fglrx.  Remember: THIS IS A N00Bs RECOMMENDATION!  Aoanla seems to know what's going on in my experience!

Peace and good luck to you.

DoctorRon
Chicago, IL
<rondamato@gmail.com>
------------
v7.10 Gutsy Gibbon 32-bit/Gnome
HP Pavillion (something)
AMD Sempron 3100 w/2GB DDR 533

---

