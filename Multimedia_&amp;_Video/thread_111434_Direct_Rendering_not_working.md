---
title: "Direct Rendering not working"
date: 2006-01-02
forum: Multimedia &amp; Video
---

### Post by Zill on 2006-01-02
Just installed PPRacer on my new Breezy system.  Runs horrendously slowly with a mouse movement about once a second.  Also no sound!  glxinfo advises "direct rendering: No", which I think is likely to be the main problem.  glxgears also runs very slowly.

Both TuxRacer (now PPRacer) and glxgears ran fine on this PC when it had various Mandrake versions installed, so the hardware is OK.

PC uses an Intel 82810E DC-133 integrated graphics chipset.

Any ideas what I need to do to get Breezy to use Direct Rendering and get Tux moving again?

Many thanks,

Zill

---

### Post by shof2k on 2006-01-06
Which module does xorg use for your card?  You can find out by looking in xorg.conf.

If it's i180 or i915, try looking at the freedesktop.org for updated modules.

Hope that helps.

---

### Post by Zill on 2006-01-11
Many thanks for the info shof2k - I will check that out.
Sorry about the delay in replying :-(
All the best,

Zill

---

