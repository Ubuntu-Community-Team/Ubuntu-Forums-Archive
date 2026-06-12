---
title: "Intel Pro/Wireless 2915 Broken (aka I am an idiot)"
date: 2009-10-18
forum: Networking &amp; Wireless
---

### Post by noob555 on 2009-10-18
So here is the problem.  I tried going beyond my comfort level yesterday.  I don't really know very much about the terminal as I have only been using Ubuntu for about 7 or 8 months now.  Nevertheless, I tried to patch my Wireless driver to allow packet injection.  I'm not certain what happened, but the moment I reinstalled the wireless no longer functioned *at all*.  

If I enter "lspci", the computer clearly recognizes that the card is there because it spits out the following:

          04:02.0 Network controller: Intel Corporation PRO/Wireless 2915ABG [Calexico2] Network Connection (rev 05)

However, if I enter "iwconfig", I get the following:

          lo        no wireless extensions.
          eth0      no wireless extensions.
          irda0     no wireless extensions.
          pan0      no wireless extensions.

I tried reinstalling the driver from debian.org, but no joy.  I really don't know what to do at this point.

Any help would be greatly appreciated.

---

### Post by lswb on 2009-10-18
If you reinstall your current kernel version it should bring along the stock drivers.

---

### Post by melodybrat124 on 2009-10-18
> **lswb said:**
> If you reinstall your current kernel version it should bring along the stock drivers.

how do i istall wireless internet with xumbuntu

---

### Post by noob555 on 2009-10-18
Thank you.  How do I do that?

---

### Post by lswb on 2009-10-18
You can do it from synaptic

Main Menu/System/Administration/Synaptic

Then click on search and enter "linux-image"

Scroll through the resulting list and look for lines where the checkbox at the left is green. This indicates the package is currently installed. Right click on those lines and select "Mark for Reinstallation" then click "Apply" from the Synaptic menu.

---

