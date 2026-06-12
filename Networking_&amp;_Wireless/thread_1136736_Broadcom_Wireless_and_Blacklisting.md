---
title: "Broadcom Wireless and Blacklisting"
date: 2009-04-25
forum: Networking &amp; Wireless
---

### Post by Rhemat on 2009-04-25
Heya all,

I recently got a laptop from a friend, and installed Xubuntu Linux on it.  At first, I was unable to get the Broadcom Wireless NIC in it to work, but I was able to fix the problem yesterday.
When I first looked for reasons why the NIC wouldn't work, everybody was saying that the restricted drivers don't work and you have to use ndiswrapper, and blacklist the Broadcom restricted drivers.  I tried three different tutorials, and never got it to work with ndiswrapper.  So I uninstalled ndiswrapper, and went to the blacklist file (/etc/modprobe.d/blacklist), and found that the drivers had been blacklisted **out of the box**.  After I deleted the blacklist drivers that were relevant, the restricted Broadcom driver just worked.
I just wanted to post this because I think a lot of people had to putz around with ndiswrapper for no reason, and ask why the driver would be blacklisted on a fresh install?
Hopefully this helps.

---

