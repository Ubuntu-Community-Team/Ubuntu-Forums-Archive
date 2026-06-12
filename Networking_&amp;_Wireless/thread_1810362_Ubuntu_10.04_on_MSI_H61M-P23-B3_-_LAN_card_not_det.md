---
title: "Ubuntu 10.04 on MSI H61M-P23-B3 - LAN card not detected"
date: 2011-07-22
forum: Networking &amp; Wireless
---

### Post by iNerdSure on 2011-07-22
Installation of ubuntu 10.04 on new PC with motherboard MSI H61M-P23-B3 was ok. However, the on-board LAN card could not be detected/recognized. USB Wi-Fi adapter could be used.

But I need to get this PC running on wired LAN, as the intended location of the PC in the office is not suited for Wi-Fi LAN access.

I read another post in another forum that ubuntu 11.04 could solve the network card detetction problem.

But this office has all its PCs on ubuntu 10.04 LTS.  And it's not practical nor desirable to have one PC running on another version.

Can anyone suggest how I can solve the LAN card detection problem?

Thank you.

---

### Post by iNerdSure on 2011-07-25
Problem solved.  On-board LAN card is now detected.

The solution was posted in:

[http://ubuntuforums.org/showthread.php?t=1806056&page=2](http://ubuntuforums.org/showthread.php?t=1806056&page=2)

and the Atheros AR8151 drivers can be found at:

[http://wireless.kernel.org/en/users/Download#Directly_downloading_the_tarball](http://wireless.kernel.org/en/users/Download#Directly_downloading_the_tarball)

---

