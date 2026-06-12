---
title: "Integrated Webcam recognized but Not working with Ubuntu  10.10"
date: 2011-04-16
forum: Multimedia Software
---

### Post by tachka on 2011-04-16
Hello everybody,

I recently rebooted my computer, switching from Vista to Ubuntu 10.10, 32 bit.
I've had troubles with my webcam ever since. I've tried every single suggestion from the Ubuntu Forums and nothing works, and I am now quite desperate..

I'm installed Cheese but nothing else than a green dotted screen appears, I've also tried gucview which tells me that my webcam is recognized under the name of USB 2.0 Camera.

When I enter lsusb in the terminal, here is what appears:

natacha@natacha-EasyNote-MX36:~$ lsusb
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0402:5602 ALi Corp. M5602 Video Camera Controller
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

The webcam doesn't work with any program, but since it does partially work with Cheese, I would think that I either have to install an additional driver or that my camera is not compatible with Ubuntu, which would really suck.

The closest similar case I've found on the net was this one : [https://bugzilla.kernel.org/show_bug.cgi?id=16575](https://bugzilla.kernel.org/show_bug.cgi?id=16575) . Apparently it's about a Bug 16575 but the problem doesn't seem to have been resolved either.

If you have ANY suggestion, they are really welcome because I'm quite out of ideas.

---

### Post by no2498 on 2011-04-16
i put this in google  see a few solved

0402:5602 ALi Corp. M5602 Video Camera Controller

---

### Post by BicyclerBoy on 2011-04-16
Looks like you build it yourself..

[http://m560x-driver.svn.sourceforge.net/](http://m560x-driver.svn.sourceforge.net/)

This code may have been integrated into dvb v4l project but you would have to check..

Best advice is: buy a uvc supported webcam..forget the Ali Corp device..

[http://www.linuxlaptopwiki.net/wiki/ALi_Corp_M5602](http://www.linuxlaptopwiki.net/wiki/ALi_Corp_M5602)

This link has a useful test for uvc compatible webcams..

---

### Post by no2498 on 2011-04-16
i have a non uvc cam and it works in/on ubuntu linux 10.04 lucid

---

