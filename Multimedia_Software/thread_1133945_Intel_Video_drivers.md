---
title: "Intel Video drivers?"
date: 2009-04-23
forum: Multimedia Software
---

### Post by Zoquara on 2009-04-23
I'm trying to figure out how to get video drivers on a second computer in my house. The graphics are integrated on an Intel 946GZ Express board. I've found a few sites about Linux drivers for the Intel chipsets, but I have to admit total confusion at this point. Everything is either outdated (2006!), or I just don't understand what to do. On my computer (also integrated graphics) all I needed was EnvyNG, but that doesn't work on the other one. The OS on the second computer is Ubuntu 8.10. 

I've tried installing an old nVidia card I have on the other computer, and it won't load... It freezes before the OS even fully loads, so that's not an option :(

---

### Post by psyke83 on 2009-04-23
> **Zoquara said:**
> I'm trying to figure out how to get video drivers on a second computer in my house. The graphics are integrated on an Intel 946GZ Express board. I've found a few sites about Linux drivers for the Intel chipsets, but I have to admit total confusion at this point. Everything is either outdated (2006!), or I just don't understand what to do. On my computer (also integrated graphics) all I needed was EnvyNG, but that doesn't work on the other one. The OS on the second computer is Ubuntu 8.10. 

I've tried installing an old nVidia card I have on the other computer, and it won't load... It freezes before the OS even fully loads, so that's not an option :(

The intel drivers are integrated into Ubuntu, in the package "xserver-xorg-video-intel". You don't need to install or configure anything to make them work, and they're already the latest version (provided you keep your system up-to-date).

EnvyNG is/was intended only to install the ATI (fglrx) or NVIDIA proprietary driver, nothing else. Newer versions of Ubuntu also come with a "Restricted Drivers" manager called Jocky, which notify a user if they need any restricted drivers (NVIDIA, fglrx, or certain wireless card drivers).

In short, your Intel card will work automatically without the need to install extra drivers.

---

### Post by Zoquara on 2009-04-23
Thank you! I've been beating my head against the wall for a couple days now trying to fix a problem, and was trying from the wrong angle.

---

