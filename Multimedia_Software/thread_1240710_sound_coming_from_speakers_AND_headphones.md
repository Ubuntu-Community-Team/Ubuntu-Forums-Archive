---
title: "sound coming from speakers AND headphones"
date: 2009-08-15
forum: Multimedia Software
---

### Post by Topher88 on 2009-08-15
Before, my sound wasn't working at all, either through my laptop speakers or through the headphones.  I finally got it fixed by fudging around with settings, except now when I put headphones into the headphone jack, the sound continues playing through the laptop speakers AND plays through the headphones.  I have a brand new HP DV6 1230us, I believe.  Just wondering if there is some quick setting tweak for this.  Now that I at least have the sound working, I'm not too extremely worried about it, but I would like to fix it as soon as I can.  Thanks!

---

### Post by Topher88 on 2009-08-17
any ideas?

---

### Post by rykel on 2009-08-17
Have you tried Right-Clicking on the Volume Control icon at the top right corner of your Ubuntu desktop, select "Open Volume Control" and muting/unmuting the relevant bars?

Just a suggestion... hope that helps!

---

### Post by Topher88 on 2009-08-17
> **rykel said:**
> Have you tried Right-Clicking on the Volume Control icon at the top right corner of your Ubuntu desktop, select "Open Volume Control" and muting/unmuting the relevant bars?

Just a suggestion... hope that helps!

The relevant bars do not seem to correspond with the correct speakers.  The headphones basically act ilke an extension of the laptop speakers; whatever the laptop speakers do, the headphones do, seemingly no matter what.

---

### Post by Topher88 on 2009-09-21
So, does any one have any ideas what might be causing this?  I've done a lot of tweaking in volume control, but to no avail - whatever the computer speakers do, anything plugged into the headphone jack does the same, if available.

Thanks.

---

### Post by rasmukri on 2009-09-25
i have the same prob i haven't thought about changing the individual ones in the volume manager ill try that

---

### Post by rasmukri on 2009-10-04
so what worked for me was this:
click the volume icon and select volume control
then switches uncheck the box that says speaker
then close it out
you should be good to go but you will need to recheck the box to make the speakers work again

---

### Post by SLKHDP on 2009-12-06
Hi All

i also having that Problem, problem is you cant find "headphone sense jack" in ubuntu 9.10 easily like ubuntu 9.04. therefore i have installed ALSA mixer and in ALSA mixer you can find "headphone sense jack" then you can change sound as you like head phone or local speaker or both.

Try this work for me

Thanks
SLKHDP

---

### Post by markoper on 2009-12-07
didn't work for me alsamixer doesn't have that option (Karmic and aspire 5735, Realtek ALC268 )

---

### Post by littlemisscrazy on 2009-12-08
same here i have no headphone jack option 
here's a shot of my alsamixer

and with this alsa mixer i can only change preferences of the right speaker

---

### Post by markbuntu on 2009-12-08
These problems are very hardware specific, especially for laptops. There is a listing here of fixes for this sort of problem.

[http://ubuntuforums.org/showthread.php?t=1043568](http://ubuntuforums.org/showthread.php?t=1043568)

---

