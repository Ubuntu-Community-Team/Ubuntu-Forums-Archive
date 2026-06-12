---
title: "Video weirdness again"
date: 2010-06-16
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by cariboo on 2010-06-16
I removed a couple of old kernels this morning, and one of the things removed was the broadcom wl driver.I still had the wireless icon in the top panel, but there where no access points showing up.

I opened a terminal and ran **sudo lshw -C network** to see if the proper driver was being loaded, as the command was running, the screen went rainbow colors, the only way to fix it was to log out then back in again.

The screenshot I took shows normal so there is no sense in attaching it. This same thing happened early in Lucid testing, and now it's showing up in Maverick.

System is a Compaq Mini-110 with Intel i946 graphics chip set.

Has anyone run else run into the same problem?

---

### Post by timosha on 2010-06-17
When I run that command on a Thinkpad R51 - 2887 with Intel 855GM graphics chip the whole system freezes. A power cycle is then required.

---

