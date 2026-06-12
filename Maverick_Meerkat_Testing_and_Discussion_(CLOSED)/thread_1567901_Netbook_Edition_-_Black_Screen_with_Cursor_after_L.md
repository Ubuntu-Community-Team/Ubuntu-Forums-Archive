---
title: "Netbook Edition - Black Screen with Cursor after Login"
date: 2010-09-04
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by PricklyPete on 2010-09-04
I upgraded from 10.04 (netbook) to Maverick Beta (netbook) yesterday, and things didn't go so smoothly.

The login screen displays fine.  After I enter my password, the screen goes black.  The screen isn't totally dead though: the cursor is displayed and I can move it around, notifications will appear in the top right corner (e.g., "WIFI Radio On"), and I can get System Monitor to appear by pressing its keyboard shortcut.  This same phenomenon occurs when I boot with an older kernel.

The above situation occurs when I login using the "Ubuntu Netbook Edition" option, which is the default.  If I login under "Ubuntu Netbook Edition 2D" option, everything seems to work pretty normal with one big exception.  The interface looks like some hybrid of 10.04 Netbook and 10.04 Desktop.  Definitely not Unity.

I've been reading this forum and others for 2 days now, to no avail.  I've removed and reinstalled X and the kernel headers, among other things.  I'm stuck.

Oh, and I'm using an Intel video card, not an NVIDIA one.  3D appears to be working (when I run glxinfo), though I suspect the reason why Unity doesn't work, but logging in using "Ubuntu Netbook Edition 2D" does work, involves a 3D issue.

---

### Post by dino99 on 2010-09-04
few ideas, try:

booting without "splash"

or/and add i965.modeset=0

or/and remove vga=xxx if it exist on the boot line

when booted, check your video driver activation (system admin additional drivers)

---

