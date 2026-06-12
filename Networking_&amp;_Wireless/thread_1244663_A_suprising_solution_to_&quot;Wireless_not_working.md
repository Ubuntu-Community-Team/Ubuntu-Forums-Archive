---
title: "A suprising solution to &quot;Wireless not working&quot; issue"
date: 2009-08-19
forum: Networking &amp; Wireless
---

### Post by Enos Shenk on 2009-08-19
Greets,

I just decided today to install Ubuntu on my laptop primarily for messing about with wireless. To my annoyance however, the wireless on the laptop would not work. 

The system offered to activate the proprietary drivers for my card (Broadcom STA drivers), so naturally I accepted. Except nothing worked still.

Frustrated, I paged through over 25 pages of threads on this board trying to figure out why the wireless wouldnt connect when A: The driver was installed, B: All the appropriate console commands showed the card as working fine and C: My router showed that the laptop was attempting to get an IP.

Wait...Hang on a moment. I took a closer look at the list of connected machines that my router (and 99% of other routers) will show you. And lo and behold, the laptop was on there THREE times. One for the wired connection, one for the wireless, and one wireless that oddly enough had the computer name from the previous windows installation.

A quick click revoked the "old" connection, and imagine that, everything connected right up.

So perhaps it should be added to the list of "Really easy things to check before you dig into the guts of the machine" for wireless issues. I imagine this would be very common, considering alot of folks will be having issues like this after overwriting an old windows installation.

In short, if your routers DHCP page shows your old windows machine name on wireless, revoke the DHCP lease, and if the hardware is working, it should open you up to connect.

---

### Post by sarfarazkazi on 2009-08-19
This is a great tip! Thanks!

---

### Post by Enos Shenk on 2009-08-19
Oh great...Disregard this. It "works" until I try to use anything that accesses the wireless, then it drops connection.

I dont even know what to search for to try and figure this out...Considering it does "work" according to all the diagnostics Ive looked at, then you try to use the connection and it poofs itself...Any ideas?

---

