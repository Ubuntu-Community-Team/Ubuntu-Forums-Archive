---
title: "Cannot get legacy ATI drivers to install on Ubuntu 8.10 (Ibex)"
date: 2009-11-03
forum: Multimedia Software
---

### Post by MonoMatt304 on 2009-11-03
I've been trying to install Ubuntu 8.10 on my older laptop, since it's the latest Ubuntu release that will work with ATI's legacy Ubuntu drivers, and I need full 3D acceleration.  The card is a Radeon Mobility 9600.

The problem is, I can't get them to install.

No option shows up in "Restricted Drivers" at first, even after enabling all repositories and doing a full system update.  It's just blank and says "No Restricted Drivers are in use on this system."

I've both installed the driver directly from ATI's website, and followed the directions [here]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI") and it seems to work (I can load Catalyst Control Center, enable desktop effects, etc) but after that, Ubuntu forces me to "enable" the restricted drivers (it will find them at this point, nagging me to enable them, when it wouldn't show anything before), effectively installing them on top of the drivers I installed, causing the Xserver to either outright crash and not reload, or causing the system to hang when trying to do anything with 3D graphics.

Any ideas?

---

