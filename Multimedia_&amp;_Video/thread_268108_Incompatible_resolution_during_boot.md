---
title: "Incompatible resolution during boot"
date: 2006-09-29
forum: Multimedia &amp; Video
---

### Post by mjpatey on 2006-09-29
I've been messing around with xorg.conf due to the recent kernel update and problems that caused with my ATI card.

Everything's working fine now, except that during boot, Ubuntu switches into a video mode that my monitor doesn't support.  So I get a blank screen (with the monitor's error message overlaid) up to and including the login screen.  I hear the login bongos, and type my username and password "blind".  Then the Nautilus splash appears at the proper resolution, and we happily boot the rest of the way into Ubuntu.

I'm sure it's a single tweak to a single file, but which one?

Thanks for any help you may have.

-Mark

---

### Post by geezerone on 2006-09-29
Hi

Did you try installing xorg-driver-fglrx? I had problem with Nvidia driver from Automatix which didn't show a login screen and after restoring xorg.conf and installing fglrx all is ok including screensaver.

---

