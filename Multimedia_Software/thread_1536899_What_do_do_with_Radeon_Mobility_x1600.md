---
title: "What do do with Radeon Mobility x1600 ?"
date: 2010-07-22
forum: Multimedia Software
---

### Post by [censored] on 2010-07-22
Hi. I have an intel imac with the Radeon Mobility x1600, support for which seems to be broken in Lucid Lynx. I can't seem to get 3d graphics happening.

Has anybody found a way to fix that?

Or should I just go back to Karmic Koala?

I'm currently using 8.04 Hardy, which is ok, but a lot of hte stuff in its repos seem to be pretty outdated, which is annoying.

---

### Post by Mark Phelps on 2010-07-24
> **'[censored] said:**
> Hi. I have an intel imac with the Radeon Mobility x1600, support for which seems to be broken in Lucid Lynx. I can't seem to get 3d graphics happening.

Has anybody found a way to fix that?
There is no way to fix that -- and retain Lucid.  The new ATI drivers (that WILL work in Lucid) will not work with your card, and the old drivers (that WILL work with your card) will not work in recent Ubuntu versions.


> I'm currently using 8.04 Hardy, which is ok, but a lot of hte stuff in its repos seem to be pretty outdated, which is annoying.
8.10 is the last Ubuntu version for which 3D fglrx drivers were available.  So, of course it worked in 8.04.

---

### Post by [censored] on 2010-07-25
Thanks. Is there a distro that will work with my radeon x1600? 

I've noticed that Knoppix does-ish.

---

### Post by mcduck on 2010-07-25
My Mobility Radeon X1600 works just fine with the default, open source radeon driver. 3D, video playback and everything. :)

You really shouldn't even need to do a single thing to get it working, it works right out of the box.

Edit: if you try to upgrade from older Ubuntu version that has the old version of fglrx driver that still supports this card, you'll of course have to uninstall the driver to get Ubuntu to use the open source driver instead.

---

### Post by [censored] on 2010-07-25
mcduck how about catalyst control center? Can you get that working. 

Again this is an old intel imac, with a built in monitor that's gotten a bit dim over the years. I need colour controls to adjust it a bit.

---

### Post by Mark Phelps on 2010-07-25
> **'[censored] said:**
> mcduck how about catalyst control center? Can you get that working. 

NO -- CCC is bundled with the ATI proprietary drivers -- which I've already told you will NOT work with your card and recent versions of Ubuntu.

You'll have to live without CCC when you're limited to using the open source drivers.

---

### Post by lskau on 2010-07-25
I have had my notebook on hardy (8.04LTS) for a long time because I used it for playing WOW, and 9.XX + 10.XX does NOT support the GFX drivers.

I have tried everything but it just does not work.

It is just too lousy that ATI does not produce linux drivers :(

Now I am on 10.04LTS but needs to dual boot into *cough*windows*cough* in order to play any games relying on acceleration.


I am a professional Unix/Linux Admin so its a real drag

---

### Post by Yellow Pasque on 2010-07-25
Yeah, ATI should have updated their "legacy" Catalyst driver to support newer kernels/Xservers until the open-source Gallium3D driver was fast and stable "enough" for general use. It comes down to ATI not having enough resources to fully support proprietary and open drivers (or maybe trying to get you to buy a new card as a cynic might see it).

---

### Post by [censored] on 2010-07-26
Is there a way to adjust brightness, contrast, color, et al with the open source drivers?

---

