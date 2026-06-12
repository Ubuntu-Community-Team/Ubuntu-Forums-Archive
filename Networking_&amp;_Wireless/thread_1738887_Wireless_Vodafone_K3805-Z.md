---
title: "Wireless Vodafone K3805-Z"
date: 2011-04-25
forum: Networking &amp; Wireless
---

### Post by Tom 6 on 2011-04-25
Hi :)
My usb-dongle seems to have a driver installed already but says it is not enabled.  How do i enable it?

I tried posting in Launchpad but apart from getting a lot of info about my system it didn't seem to help.
[https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/153889](https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/153889)

I tried compiling the ath9k driver but it wouldn't compile and the MadWifi wouldn't work.  I tried following instructions for using ndis-wrapper to allow the Windows drivers but i couldn't find the .inf and .bin for the K3805-Z

I did find another thread in UbuntuForums and it was solved but it's 9 or 10 pages of false-starts and reinstalls and i wondered if anyone could let me know how to fix internet connection
[http://ubuntuforums.org/showthread.php?t=1669429&page=7](http://ubuntuforums.org/showthread.php?t=1669429&page=7)

Regards from
Tom :)

---

### Post by mick222 on 2011-04-25
Have you tried using network connections to set up a mobile connection I have a mobile broadband connection with a vodaphone phone which was quite easy to setup.

---

### Post by Tom 6 on 2011-04-25
Hi :)

The easy answer of just un-mounting the storage part of the device didn't work.  Using Network Manager to create a new connection also didn't work.

The 10 page thread seems to suggest that installing
python-messaging_0.5.9-1_all.deb
wader-core_0.5.5-1_all.deb
bcm_2.99.12-1_all.deb
is worth trying but even then people were having a LOT of trouble with this device.

Regards from
Tom :)

---

### Post by Tom 6 on 2011-04-26
Hi :)
The answer seems to be to upgrade or install Ubuntu 10.10 or 11.04 (or newer if this thread is being read after early 2011) as the kernel now has the drivers in the kernel.  I think i will try it next time i am on the boat.
Many thanks and regards from
Tom :)

---

