---
title: "ati problem! - i'm getting so weary."
date: 2007-12-13
forum: Multimedia &amp; Video
---

### Post by Sobiquet on 2007-12-13
in this guide; it states: "Make sure fglrx is not disabled in the DISABLED_MODULES part: kdesu kate /etc/default/linux-restricted-modules-common."

so i went there, turns out fgrlx is disabled, but how do i enable it? thanks.

p.s the restricted drivers thing: enabling it causes me to run in low graphics mode every time.

Thanks alot.

---

### Post by elliotjreed on 2007-12-13
sudo dpkg-reconfigure xserver-xorg

is uaually a good place to start...

it will come up with a list, just check fglrx!

However, if it does not work, you may start up with a blank screen, just go into safe mode and type in the command again - selecting the previous driver, and you'll be back to normal!!

Good luck!

---

### Post by acoustibop on 2007-12-13
> **Sobiquet said:**
> in this guide; it states: "Make sure fglrx is not disabled in the DISABLED_MODULES part: kdesu kate /etc/default/linux-restricted-modules-common."

so i went there, turns out fgrlx is disabled, but how do i enable it? thanks.

Delete fglrx from the uncommented  DISABLED_MODULES="" line, Sobiquet.

---

