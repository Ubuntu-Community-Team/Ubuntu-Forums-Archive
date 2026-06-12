---
title: "Yet another wireless issue, but interesting."
date: 2009-09-21
forum: Networking &amp; Wireless
---

### Post by fakinbacon on 2009-09-21
I've had an outstanding issue with most linux flavors in that my wireless doesn't work. Contributors to the issue have been Fedora, openSUSE, Mandriva, Debian, and now ubuntu, but I've made a discovery that may assist in determining the issue. I recently had installed ubuntu 8.04 in its 32 bit state. it worked famously and was my favorite distro yet except that I wished it were 64-bit. Well I was messing with options in the bootloader and royally messed it up, so I figured "hey, why not use this moment to switch to the x86_64 version."

My wireless card mysteriously no longer works. I thought back and now I realize that on all the distros on which I tried the 64-bit version (except sabayon which notouriously has all drivers in existence) I've had the same issue (slightly different on debian which also didn't have a driver for my ethernet card). Also a usb card that worked by default in the x86 version doesn't work.... 

My computer type is a HP dv3000. Intel centrino dual core processor @ 2.00 Ghz each. 4Gb RAM 

I don't have access to ethernet right now or I would post lspci and all that usefull information but I plan to a little later. I seem to remember that my network controller is listed in both the x86 and x86_64 version as "unknown intel device 4[then other numbers]"

---

