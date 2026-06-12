---
title: "new motherboard; old 8.10; no eth0"
date: 2009-04-01
forum: Networking &amp; Wireless
---

### Post by CharmyBee on 2009-04-01
Hello
I have a new computer (with totally different onboard LAN chipset) with an old hard drive and old Kubuntu 8.10 setup which was configured for the previous computer (that had a completely different motherboard with onboard LAN)
So far using the same Kubuntu setup on my new machine leads to my ethernet being permanently 'disconnected' no matter how many connections i've tried to make. The IPs, subnet mask, gateway and DNS server settings are all correctly configured.

Any way to reconfigure the eth0 to actually work on the new computer with the old Kubuntu? I really DON'T want to reinstall fresh from nothing and reconfigure absolutely everything.

p.s. I'm posting this from Windows.
The NIC is RTL8168C(P)/8111C(P)

---

### Post by chili555 on 2009-04-01
Please check here: [https://www.linuxquestions.org/questions/fedora-35/sata-wont-detect-on-fedora-7-572868/](https://www.linuxquestions.org/questions/fedora-35/sata-wont-detect-on-fedora-7-572868/)

Especially this:> As of 27 May 2007, in kernel 2.6.21.3, you may experience the issues with the r8169 driver if you dual boot Windows on some systems. Windows by defaults disables the NIC at Windows shutdown time in order to disable Wake-On-Lan, and this NIC will remain disabled until the next time Windows turns it on. The r8169 driver in the kernel does not know how to turn the NIC on from this disabled state; therefore, the device will not respond, even if the driver loads and reports that the device is up. To work around this problem, simply enable the feature "Wake-on-lan after shutdown." You can set this options through Windows' device manager.

Edit: Problem with dual-booting with Windows exist also in 2.6.19.5 and 2.6.20.8 kernel, so it is safe to assume that it will concern all 2.6 kernels until the kernel developers update the drivers for RTL8168 to the version that will be able to turn on the NIC from disabled state. (Corey)

---

### Post by CharmyBee on 2009-04-01
Just tried that (including the unplug-for-15-secs method), still no luck although the connection shows up as 'unmanaged' but there's barely anything to configure beyond ip addresses, which are all correct.

I've also tried switching the driver module from another old suggestion and still no luck.
There is also no network in using gOS also.

---

### Post by freonchill on 2009-04-01
know its not the best option, but if you want to try a "power failure" while in windows then boot directly to ubuntu and see if it shows-up there...

and by "power failure" i do mean pull the power while in windows.

---

