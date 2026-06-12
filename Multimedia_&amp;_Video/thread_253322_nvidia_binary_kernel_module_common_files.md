---
title: "nvidia binary kernel module common files"
date: 2006-09-08
forum: Multimedia &amp; Video
---

### Post by missmoondog on 2006-09-08
what exactly are the nvidia binary kernel module common files used for, if anything, on a machine that has nothing nvidia related on it? Are they necessary on this particular machine?

i've been disabling it with bootup-manager and hadn't had any problems. now, when i start up, i get a multi colered screen for a little bit, then it pops up normal.

thank you

---

### Post by tseliot on 2006-09-08
Maybe you refer to nvidia-kernel-common.

It's a dependency of the restricted modules but it does not affect your computer unless you use the nvidia driver.

There's no need to disable it.

---

### Post by missmoondog on 2006-09-08
no, that's the exact name as listed in bum startup items. it's listed in every install i've done of k/ubuntu.

so, there's no need to have it enabled then either? :-k

---

### Post by tseliot on 2006-09-08
> **missmoondog said:**
> no, that's the exact name as listed in bum startup items. it's listed in every install i've done of k/ubuntu.

so, there's no need to have it enabled then either? :-k

I used the name of the package (not the one of the service).

And no, there's no need to keep it enabled. The choice is down to you.

---

### Post by missmoondog on 2006-09-08
which probably means it has nothing to do with my original theorizing of it having something to do with the multi colored screen when first starting up. not that big of a deal anyway as everything does load/start correctly anyway and even stays at the refresh rate i want, which it didn't used to do.

confused now? LOL

thanks for the insight.

---

