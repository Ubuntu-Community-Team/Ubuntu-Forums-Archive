---
title: "Problems ripping DVD with Arista"
date: 2010-12-29
forum: Multimedia Software
---

### Post by bennettg on 2010-12-29
hi noob here.

i had some success with handrake to rip dvd's in older versions of ubuntu.  i now have a clean install of 10.10 and know that handbrake is not compatible (even tried the ppa of the nighly builds without success).  In looking for alternatives, i cam across arista transcoder....which seems perfect for my needs (simple), but whenever i put a dvd in the queue its gives me an error that says conversion failed....no valid dvd title found.   this happens no matter what dvd i use and no matter what preset i choose.  can someone help?

---

### Post by coffeecat on 2010-12-29
Do you have libdvdcss2 installed?

---

### Post by JohnAStebbins on 2010-12-29
> **bennettg said:**
> hi noob here.

i had some success with handrake to rip dvd's in older versions of ubuntu.  i now have a clean install of 10.10 and know that handbrake is not compatible (even tried the ppa of the nighly builds without success).  In looking for alternatives, i cam across arista transcoder....which seems perfect for my needs (simple), but whenever i put a dvd in the queue its gives me an error that says conversion failed....no valid dvd title found.   this happens no matter what dvd i use and no matter what preset i choose.  can someone help?

The HandBrake nightly builds work perfectly fine on Ubuntu 10.10.  You are probably missing libdvdcss like the last poster said.  HandBrake's activity log will indicate this if this is what is happening.

---

