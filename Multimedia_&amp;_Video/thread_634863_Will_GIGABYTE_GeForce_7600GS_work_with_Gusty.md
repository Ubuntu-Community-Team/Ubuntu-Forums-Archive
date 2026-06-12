---
title: "Will GIGABYTE GeForce 7600GS work with Gusty?"
date: 2007-12-08
forum: Multimedia &amp; Video
---

### Post by lambono on 2007-12-08
Hi Guys,
I was thinking of buying the GIGABYTE GeForce 7600GS card. 
I like the fact that is has no fan.

Does anyone know if this card will work in gusty?

I saw this report and was wondering if there is a fix for it.

[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.22/+bug/174632](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.22/+bug/174632)

Thanks for your help!

Lambono

---

### Post by lambono on 2007-12-08
Also...
If this isnt going to work can anyone recommend a good passive card that will work well??

Im using the xc cube small form factor PC so the car needs to me small.

Thanks

---

### Post by lambono on 2007-12-09
Any ideas?
I was thinking of buying this on ebay today...

Thanks

---

### Post by dontpannic on 2007-12-09
Should do as it will use nVidia restricted drivers... By the way, try ebuyer.co.uk rather than ebay,,,

---

### Post by Scorpuk on 2007-12-09
Don't see why you will have a problem as my MythTv frontend is using the XFX 7600GS card witht he restricted drivers. 

Although it is using Feisty rather than Gusty, but that shouldn't make a difference...


Edit: ebuyer.com is very good, as well as dabs.com. ;)

---

### Post by Varko on 2007-12-22
My GeForce 7600 GS works fine with Gutsy but took a few steps.  I just installed a PNY GeForce 7600 GS (AGP version; I don't have a PCI Express motherboard yet) this afternoon in place of a Radeon 9800XT.  Upon booting, the system failed to start X (no surprise) and gave me a dialog box that prompted me for the type of card.  After I selected GeForce 7 Series the system uninstalled the proprietary fglrx ATI driver, and prompted me to install the proprietary NVidia driver.  When I rebooted I was stuck in an ugly 640x480 mode and could not change the screen resolution.  It turned out that when installing the NVidia driver the system changed my monitor type in xorg.conf from "SDM-HS93" (my Sony 19 inch LCD monitor) which my initial installation of Gutsy had correctly detected, to some kine of "Failsafe Monitor" with no modes other than 640x480.  Because I (whew!) had previously saved a date stamped copy of the file (xorg.conf.20071204231854), sudo gedit /etc/X11/xorg.conf allowed me to copy and paste the old and correct "Monitor" section from the backup into the working xorg.conf file, and edit the "Screen" section to use the correct monitor title ("SDM-HS93" in my case).  One last reboot and now everything is great.  The reason for the new card is to improve the frame rate of Wow under Wine, and I'm happy to report that I now have a reasonable frame rate using OpenGL (and the apply-to-forehead addon) with all the sliders maxed.  If you're looking to do the same, look for the WoW-Wine howto at [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

Moral of this story: back up xorg.conf before you change video cards.  You might need part of it again.:)

---

