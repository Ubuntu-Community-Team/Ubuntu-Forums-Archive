---
title: "out of range  46.5khz/43hz"
date: 2008-07-11
forum: Multimedia Software
---

### Post by kushal.7 on 2008-07-11
hi frnds,

i recently installed ubuntu 8.04. while booting up,  the screen gets hang up with an error " out of range 46.4khz / 43hz " for 5-6 secs & then everything is all right. 

this prob doesn't occur in case of windows xp booting.

plz tell me why this happens & solution.

---

### Post by Lostincyberspace on 2008-07-11
it mean that the monitor is receiving video with that refresh rate and it is out of range for it.

---

### Post by VitaLiNux on 2008-07-11
You need to boot ubuntu in recovery mode in order to fix that problem. After booting, try loading ¨screen resolution¨ @ System > Preferences. You might try different monitor settings. Choose those which approach your monitor size and resolution, also the refreshing rate.

Edit:
Should you have solved your problem, come back and tell us!

---

### Post by klange on 2008-07-11
> **VitaLiNux said:**
> You need to boot ubuntu in recovery mode in order to fix that problem. After booting, try loading ¨screen resolution¨ @ System > Preferences. You might try different monitor settings. Choose those which approach your monitor size and resolution, also the refreshing rate.

Edit:
Should you have solved your problem, come back and tell us!

He said it happens for 5-6 seconds and then it stops. I'd say bad framebuffer configuration, not a screen resolution / refresh rate problem in X.

---

### Post by VitaLiNux on 2008-07-11
> **WindowsSucks said:**
> He said it happens for 5-6 seconds and then it stops. I'd say bad framebuffer configuration, not a screen resolution / refresh rate problem in X.
Any idea of how he can solve his problem?

---

### Post by kushal.7 on 2008-07-12
> **kushal.7 said:**
> hi frnds,

i recently installed ubuntu 8.04. while booting up,  the screen gets hang up with an error " out of range 46.5khz / 43hz " for 5-6 secs & then everything is all right. 

this prob doesn't occur in case of windows xp booting.

plz tell me why this happens & solution.


when i tried to change the screen resolution @ System > Preferences, then i got the following error.

"The X server does not support the xRandR extansion. Runtime resolutiuon changes to the display size are not available."

I am using 17incd LCD.

---

### Post by kushal.7 on 2008-07-13
> **kushal.7 said:**
> when i tried to change the screen resolution @ System > Preferences, then i got the following error.

"The X server does not support the xRandR extansion. Runtime resolutiuon changes to the display size are not available."

I am using 17incd LCD.

plz solve my problem .

---

### Post by p_quarles on 2008-07-13
Moved to Multimedia & Video.

---

