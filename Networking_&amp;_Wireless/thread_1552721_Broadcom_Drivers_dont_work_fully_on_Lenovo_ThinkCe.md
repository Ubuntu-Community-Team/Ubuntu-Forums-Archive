---
title: "Broadcom Drivers dont work fully on Lenovo ThinkCentre"
date: 2010-08-14
forum: Networking &amp; Wireless
---

### Post by adarshik on 2010-08-14
Hi All,

I just bought a brand new Lenovo ThinkCentre A70z (All in One). Today I  installed Ubuntu 10.4 32bit version, Here are the problems I  encountered.

1) Ubuntu didn't recognize my Broadcom Wifi Card by default, all though  the drivers are there on the DVD, it seems to be blacklisted.

my hardware details are :

02:00.0 Network controller [0280]: Broadcom Corporation Device [14e4:4357] (rev 01)
Subsystem: Broadcom Corporation Device [14e4:04da]

after reading this forum (thanks all) , I managed to activate the drivers.

the drivers I am using are :

a) Package              : bcmwl-kernel-source
    Installed Version  : 5.60.48.36+bdcom-0ubuntu3

b) Package              : bcmwl-modaliases
    Installed Version  : 5.60.48.36+bdcom-0ubuntu3

for this to work, (make sure) you have installed the below:

c) Package               : dkms
    Installed Version     : 2.1.1.2-2fakesync1

d) Package                : fakeroot
     Installed Version    : 1.14.4-1ubuntu1
 
e) Package                : patch
      Installed Version    : 2.6-2ubuntu1

BUT I HAVE A PROBLEM, EVERY TIME I REBOOT, "THE DRIVERS ARE ACTIVATED,  BUT NOT IN USE) I HAVE TO REMOVE AND REINSTALL THEM FOR THE WIFI TO  WORK.

Can anyone please help me

Thanks in Advance

2) Setting Boot Sequence:
 Unlike my Older Dell Inspirion Laptop, I wasn't able to Install Ubuntu  through USB drive, it doesn't simply recognize the USB (I think the BIOS  needs to be upgraded), I finally managed to install Ubuntu 10.4 32 bit  vesrion via DVD.

---

### Post by mikewhatever on 2010-08-14
Can you explain how you know that the activated driver is not in use. Usually, after bcmwl-kernel-source and the other packages are install and the computer is rebooted, the driver should autoload and make the card functional.

---

