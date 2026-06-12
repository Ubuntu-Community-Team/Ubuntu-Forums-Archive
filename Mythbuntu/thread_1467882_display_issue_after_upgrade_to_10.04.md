---
title: "display issue after upgrade to 10.04"
date: 2010-05-01
forum: Mythbuntu
---

### Post by ZedThou on 2010-05-01
I have just upgraded from 9.10 to 10.04. Along the way there was a problem with grub which I seem to have finally solved, but now when booting up into 10.04 there is a dialog informing me the display is not configured properly. I was running the proprietary nvidia drivers before, version 195.36 I believe. There are three options in the dialog:

- Use default (generic) configuration

- Create new configuration for this hardware

- Use your backed-up configuration

It doesn't matter which option I choose, the dialog comes right back up. Please let me know what other information would be helpful to solve this.

It seems that mythweb is running and the backend is still up, so that's something, and my wife may not leave me as long as this is fixed before the next episode of House airs.

---

### Post by cby52894 on 2010-05-01
I am also having the exact same issue.

---

### Post by ZedThou on 2010-05-01
Finally this is fixed. Examination of the X server logs showed there was a mismatch in the nvidia kernel module and X server nvidia build, and after some frustration I ended up just purging every nvidia-related thing I could find on the system with dpkg and building the latest nvidia driver from scratch (luckily the old xorg.conf had not been completely removed by that silly dialog thingie, and a backup was found in /etc/X11). Probably not the best way to solve this but the nvidia packages have always been a bit of a pain, at least to me.

---

### Post by paoleary on 2010-05-01
I've found that occasionally when the kernel and driver are updated simultaneously, DKMS gets confused and builds the new driver for the old kernel.  Removing and reinstalling the nvidia driver packages after booting the new kernel does the trick; you don't have to build the driver from scratch.

---

