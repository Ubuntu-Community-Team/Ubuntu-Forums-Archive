---
title: "Gusty won't work on my ati 200m"
date: 2007-09-29
forum: Multimedia &amp; Video
---

### Post by dhruv_1884 on 2007-09-29
Hi,
I'm writing this from Feisty. I have an ati 200m graphics card on my acer aspire 5100 laptop.
AMD turion 64 bit
I am running beryl on Feisty, everything works just fine, not so on gusty though
When i boot from the gusty beta cd, everything works fine till the login page.
The login page says "logging ubuntu in 10 secs"
I wait for 10 seconds,
The login box dissapears,
All i see is the brown background and the mouse pointer
nothing happens for a few seconds
my display restarts and i am back to the login page again.
and this happens even if i try Failsafe Gnome

The cd has no errors

---

### Post by dhruv_1884 on 2007-09-29
Ok Got the fix,
Thanks to launcpad

Use the "Start in safe graphics mode" option instead of  "Start and Install";

it would start with a 1024*768 resolution.
Install it and then get the restricted drivers "fglrx", restart , it should do 1280*800

---

