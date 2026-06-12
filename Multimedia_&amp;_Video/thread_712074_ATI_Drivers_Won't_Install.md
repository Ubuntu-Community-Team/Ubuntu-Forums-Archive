---
title: "ATI Drivers Won't Install"
date: 2008-03-01
forum: Multimedia &amp; Video
---

### Post by kshane on 2008-03-01
I was wondering if others are having trouble installing the newer ATI drivers.  I have tried to install the January and February releases with no luck.  I end up putting the December driver back.  I've been using the built-in installer.

Edit:  I get black-green screen after rebooting to new drivers.  Using ATI Radeon X1650Pro w/512mb on board...

Hmmmm?

Kevin

---

### Post by Kivech on 2008-03-02
I'm having issues with the newer drivers from ATI for my Radeon X1900 as well. I had to revert to the proprietary drivers that came with Ubuntu to get my system to work properly again.

So no, you're not the only one. I have no clue what's going on. I was trying to get my direct rendering to work, but to no aval so far.

Kivech

---

### Post by kshane on 2008-03-02
> **Kivech said:**
> I'm having issues with the newer drivers from ATI for my Radeon X1900 as well. I had to revert to the proprietary drivers that came with Ubuntu to get my system to work properly again.

So no, you're not the only one. I have no clue what's going on. I was trying to get my direct rendering to work, but to no aval so far.

Kivech

So, it's not just me...    :)

I went back to "ati-driver-installer-7-11-x86.x86_64.run", from November, I believe.  Works...  Mostly

I wish they'd get it together...

Kevin

---

### Post by miciurin on 2008-03-03
I also have a X1650pro/512MB. With the ati drivers from ubuntu repositories worked, but since I had to use XGL, which proved buggy I decided to try the new drivers (february release). Inastalled by manually building package, also with envy, nothing worked. Kept getting the mesa thing and upon reboot a white screen.
After much googling and  looking at the errors from Xorg.0.log I changed the AGP aperture size in BIOS to 256MB. It worked immediatelly after that.

---

