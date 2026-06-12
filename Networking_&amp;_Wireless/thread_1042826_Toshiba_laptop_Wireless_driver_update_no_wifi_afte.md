---
title: "Toshiba laptop Wireless driver update no wifi after reboot"
date: 2009-01-17
forum: Networking &amp; Wireless
---

### Post by ubuntubrian on 2009-01-17
Brand new cheapy Toshiba satellite and no network connection so I downloaded compat-wireless-2.6.tar.bz2 and ran the how-to:
[http://wireless.kernel.org/en/users/Download](http://wireless.kernel.org/en/users/Download)

After rebooting NetworkManager works and I was able to connect to my network. After suspending and waking, no network connection so I ran the driver update again, rebooted, and it's back up. How do I get the update to "stick"?

---

### Post by ubuntubrian on 2009-01-20
Fixed-
I installed the linux-backports-modules and then blacklisted "ath-pci" in  /etc/modprobe.d/blacklist. Now NetworkManager finds networks all by itself!

---

### Post by ANew on 2009-01-20
> **ubuntubrian said:**
> Fixed-
I installed the linux-backports-modules and then blacklisted "ath-pci" in  /etc/modprobe.d/blacklist. Now NetworkManager finds networks all by itself!

What module i had installed from backports? there are many of them. i have similar problem.

---

### Post by kevdog on 2009-01-20
You dont need to blacklist ath_pci.  Just remove its entry for the /etc/modules file

---

