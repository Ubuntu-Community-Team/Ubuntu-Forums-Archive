---
title: "Can't get monitor to use all its real estate."
date: 2010-01-11
forum: Multimedia Software
---

### Post by tvaughan77 on 2010-01-11
Hi,

I have a brand new Dell w/ Ubuntu 9.10 installed and a new Dell ST2410 monitor. The graphics card in my box is an ATI Radeon HD4350.

Unfortunately, I can't get the monitor to "use all the screen space" (see attached picture).
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=143312&d=1263233235[/IMG]

In Preferences->Display, the monitor is maxed out at 1920x1080, and I can't use the physical controls on the side of the monitor to stretch out the display (the "Auto Adjust" menu is greyed out).

I also tried System->Administration->Hardware Drivers and I see that the "ATI/AMD proprietary FGLRX graphics driver" is not activated.  When I try to activate it, it says "driver cannot be activate; see /var/log/jockey.log for details."

Here's the tail of the jockey.log. . . can anyone help me?

```

2010-01-11 13:03:29,914 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x99755cc> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-01-11 13:03:29,914 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x99755cc> about HardwareID('modalias', 'acpi:PNP0C02:')
2010-01-11 13:03:29,996 DEBUG: XorgDriverHandler(fglrx, xorg-driver-fglrx, fglrx): xorg.conf driver matches
2010-01-11 13:03:30,064 DEBUG: XorgDriverHandler(fglrx, xorg-driver-fglrx, fglrx): xorg.conf driver matches
2010-01-11 13:03:30,083 DEBUG: XorgDriverHandler(fglrx, xorg-driver-fglrx, fglrx): xorg.conf driver matches
2010-01-11 13:04:06,805 DEBUG: XorgDriverHandler(fglrx, xorg-driver-fglrx, fglrx): xorg.conf driver matches
2010-01-11 13:04:15,824 DEBUG: Installing package: linux-headers-2.6.28-11-generic
2010-01-11 13:04:16,015 DEBUG: Package linux-headers-2.6.28-11-generic does not exist, aborting
2010-01-11 13:04:16,357 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2010-01-11 13:04:16,357 WARNING: /sys/module/fglrx/drivers does not exist, cannot rebind fglrx driver
2010-01-11 13:04:16,357 ERROR: XorgDriverHandler.enable(): package or module not installed, aborting
2010-01-11 13:04:16,386 DEBUG: XorgDriverHandler(fglrx, xorg-driver-fglrx, fglrx): xorg.conf driver matches

```

---

### Post by HappyFeet on 2010-01-11
There should be a way to manually adjust the screen to stretch it.

---

### Post by tvaughan77 on 2010-01-11
Well, like I said, >  I can't use the physical controls on the side of the monitor to stretch out the display (the "Auto Adjust" menu is greyed out).

I feel as though there's a driver problem going on here because everything on the screen is kind of choppy.

I think this may be at the root of my problems:
[https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/496225](https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/496225)

---

### Post by tvaughan77 on 2010-01-18
Finally got my own problem fixed . . . 

I totally screwed up my entire installation by trying to upgrade to all the latest drivers.  It got so bad that I couldn't even log in to my machine unless I used gnome-failsafe.

I re-installed (this was a brand new system so I "only" lost about 8 hours).  From the baseline installation of Ubuntu 9.04 I ran in to this problem:
[http://ubuntuforums.org/showthread.php?p=7953477#post7953477](http://ubuntuforums.org/showthread.php?p=7953477#post7953477)

But changing the menu item to "gksu amdcccle" didn't work for me - it just kind of thought about opening something for a second and then didn't do anything.

So on the command prompt, I typed "sudo gksu amdcccle", which popped open the ATI control center.  In the Display Manager, the 4th tab is about "Adjustments" If you overscale all the way out to the max, then the problem is fixed. (See screenshot)
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=144055&stc=1&d=1263832481[/IMG]

---

