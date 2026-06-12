---
title: "Cant adjust brightness with new Kernel 2.6.38-1 update. Screen remains dim."
date: 2011-01-29
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by tjeremiah on 2011-01-29
I received an update for a new kernel yesterday, installed it and now my monitor remains dim, 50% brightness. Although this has been an issue since 10.04, I once again cant adjust the brightness via the FN keys. Also, in power management, the brightness option has disappeared. How can I correct this issue?

---

### Post by jfernyhough on 2011-01-29
Wait for a new kernel release candidate, or go back to .37 for the moment. This thing tends to happen with the early kernel RCs as drivers are updated etc.

---

### Post by tjeremiah on 2011-01-29
> **jfernyhough said:**
> Wait for a new kernel release candidate, or go back to .37 for the moment. This thing tends to happen with the early kernel RCs as drivers are updated etc.

oh ok, didnt know that. Thanks.

---

### Post by pressureman on 2011-01-29
Yep, 2.6.38-1 seems a bit unstable. On my first reboot after installing it on my Thinkpad, I had a kernel panic. Second attempt, screen was dim, even though running on AC. I pulled the power and reconnected, and the screen then went to full brightness.

However I've had two gnome desktop crashes, going back to GDM - once just completely out of the blue, and once when switching to full screen video playback in VLC.

I'm glad I always keep at least one prior kernel installed...

---

### Post by coffeecat on 2011-01-29
Just to observe  that the ymmv principle is alive and well (particularly with Sony Vaios which seem to have a multitude of different ways of implementing screen brightness), the 2.6.38-1 kernel has cured the screen brightness issue on my Vaio VGN-NS20S.

Screen brightness with the Fn keys was fine with Karmic and Lucid, broke (i.e. became completely non-functional) in Maverick, worked again briefly with the 2.6.36-0 kernel in early Natty testing and then broke again with all the 2.6.37 kernels. Now it's working again with the 2.6.38-1 kernel.

Actually in Maverick it was broken only with the Maverick 2.6.35 kernels. If I ran Maverick with Lucid's 2.6.32 or the 2.6.36-0, it was OK.

@tjeremiah, I presume your experience is with the Vaio NR160E listed in your sig?

---

### Post by tjeremiah on 2011-01-29
> **coffeecat said:**
> 

@tjeremiah, I presume your experience is with the Vaio NR160E listed in your sig?

yeah it is.

---

### Post by tjeremiah on 2011-01-29
I just went back to Kernel 2.6.37-12 and noticed that the brightness finally works alone with the FN keys with this kernel.:guitar: I guess im going to have to keep this one forever.

---

