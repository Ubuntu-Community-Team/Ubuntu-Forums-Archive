---
title: "Ubuntu for Android"
date: 2013-06-05
forum: Mobile Technology Discussions (CLOSED)
---

### Post by LinuxUser666 on 2013-06-05
Basically I have one question:
What does Ubuntu for Android do?
Does it remove Android from my device or does it replace my Android and with what? Orr it runs Ubuntu in JVM?
Thank you for your attention. ):P

---

### Post by Clifweb on 2013-06-05
Ubuntu for android, is like an application of Ubuntu on top of android that when docked to a larger screen with keyboard and mouse you get the full Ubuntu desktop. I don't know the progress on this as I think their priority is the Ubuntu phone a full replacement of android.
[http://www.ubuntu.com/phone/ubuntu-for-android]("http://www.ubuntu.com/phone/ubuntu-for-android")

---

### Post by LinuxUser666 on 2013-06-06
Thank you for that information Clifweb, much obliged.

---

### Post by Nr90 on 2013-07-19
Not really.
The focus seems to be on Ubuntu Touch. Ubuntu for Android and Ubuntu TV seem to be on the backburner.

---

### Post by ykyong on 2013-08-01
> **Nr90 said:**
> Not really.
The focus seems to be on Ubuntu Touch. Ubuntu for Android and Ubuntu TV seem to be on the backburner.
Hi, I am new and I am a bit confused, hope you can enlightened me. Is Ubuntu touch and Ubuntu edge the same?):P

---

### Post by Copper Bezel on 2013-08-01
Ubuntu Touch is (one of the) operating system(s) set to run on the Ubuntu Edge. So the Ubuntu Edge would be an Ubuntu Touch device in the way that the Samsung Galaxy S4 is an Android 4.x device. Ubuntu Touch is an OS that can run on a variety of existing phones and that Canonical wants OEMs and carriers to pick up to ship on commercially sold phones, and the Ubuntu Edge is sort of a demonstration of what it's capable of. 

Ubuntu Edge also includes Android, and with the Edge, or any other phone that's powerful enough, either Android and Ubuntu Touch can run a desktop-style interface over the underlying OS on a regular computer monitor.

[Ubuntu Touch]("https://wiki.ubuntu.com/Touch/FAQ") uses an Android kernel and drivers, most of the Ubuntu desktop runlevels (just compiled to run on ARM instead of x86), and a different blend of the Unity interface designed for touch devices. It doesn't run X11, the desktop server used in Ubuntu desktop, so it's (presently) restricted to running webapps and the core apps being developed by Canonical, despite having most of the Ubuntu OS running under the surface. Presumably, Mir (the new display server) will be implemented on Ubuntu Touch as it replaces X11 on the desktop, allowing desktop apps to be run there; I know that Mir is slightly closer to compatibility with Ubuntu Touch than X11 is at the moment, but I'm not certain what the long-term plan is. The core apps from Ubuntu Touch will be offered [in some implementation]("http://www.omgubuntu.co.uk/2013/05/mark-shuttleworth-on-mir-unity8-future") on the desktop, possibly as part of Ubuntu moving away from its [Gnome desktop]("http://en.wikipedia.org/wiki/Gnome_desktop") base.

---

