---
title: "Kernel update broke my network driver"
date: 2010-12-23
forum: Networking &amp; Wireless
---

### Post by stunet on 2010-12-23
hello,

I managed to get my Linksys AE1000 USB wireless adapter to work on Unbuntu 10.04 LTS.

but recently I updated the kernel to 2.6.32-26 and when i rebooted I logged on to see my wireless connection was not working.

even worse, I can't fn the links i had that showed me how to install it in the first place, arg!](*,)

I have looked about the forum for a solution, but the one i did find didn't work and was towards 10.10

from what i gather, its about the fact that the new kernel uses a different usb setup(probably incorrect, let me know it its incorrect).

its an issue that the hacked driver isnt compatible with the new kernel release, how can i revert to the older version that it did work on? if you need to know, i'm using a RALinkTech driver([http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2))

really hope you can help, this is my development server and its so painful when i have to test my things on IIS instead :P

much thanks :)

---

### Post by stunet on 2010-12-23
you can disregard this.

didn't fix it, just made the server a wired connection and added the wireless to my windows system. Next time, I'll just better plan my updates especially if i spent a whole day hacking a driver ;)

---

### Post by walt.smith1960 on 2010-12-24
One of the downsides to devices where you have to build the driver is that every time the kernel updates, you have to build the driver again.  If you know  which Ralink chipset you have, download the proper software from Ralink's site and there'll likely be a readme file as part of the  package download detailing build procedures.

Somewhat O.T., I have an Atheros ATH9K device and used Vagrale13's Ath9K_GUI installer found on sourceforge.  I wondered why using it was a two stage process (install the installer then run the installer) but my question was answered when I had a kernel update. I experienced the same thing as you, the wireless adapter died from the kernel update.  However, all I had to do was run the installer which is installed permanently and do something else for a couple minutes while the installer rebuilt the driver.  BRILLIANT!!

---

### Post by stunet on 2010-12-24
I've tried a few things, but it wasn't working so i just make the system wired.

I have a wireless card that works well on it, but i had to put it on another system of mine.

better off this way, now i can access the linux box faster now that i don't have to wait for my connection to be found :) next time I'll research it more before i buy hardware for my linux systems.

---

