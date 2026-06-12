---
title: "Mythbuntu 11.10 - LIRC - MCE Remote - resume problem"
date: 2011-10-17
forum: Mythbuntu
---

### Post by kismitt on 2011-10-17
My MCE remote work perfectly using Mythubuntu 10.10 then I decided to upgrade to 11.04 and starting to have this problem.  I couldn't figure out how to fix it, so I live without the remote until 11.10.

Hoping this problem will be fix with a new install. I did a clean Install of Mythbuntu 11.10, but keeping old mythtv database from 11.04.  The mce remote works out of box using 11.10 without having to do anything.  But when I suspend the computer and do a resume (wake-up from sleep) the mce remote won't respond.  IRW won't respond even after a restart of lirc.  Same problem from 11.04. 

Looking at the log file, I think this is where the problem but I don't see any error message:

usb 7-2: reset full speed USB device number 3 using uhci_hcd
Oct 17 13:20:36 tv kernel: [  206.172849] mceusb 7-2:1.0: resume
Oct 17 13:20:36 tv kernel: [  206.172865] PM: resume of drv: dev:ep_00 complete after 488.315 msecs
Oct 17 13:20:36 tv kernel: [  206.172871] PM: resume of drv:mceusb dev:7-2:1.0 complete after 488.390 msecs

---

