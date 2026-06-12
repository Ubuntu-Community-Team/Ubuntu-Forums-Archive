---
title: "installing a modem"
date: 2005-12-31
forum: Networking &amp; Wireless
---

### Post by jnoreiko on 2005-12-31
I'm following [the instructions on the wiki]("https://wiki.ubuntu.com/DialupModemHowto") to set up a PCI modem.

scanModem reported it as supported by the Lucent driver, so I'm following that section.

I've taken note of the extra step for 5.04 users, but I've found the following problem: there is no /dev/ttyLTM0 device.
I have found however a /dev/ttLTM0 (without the y).
is there a typo?

Also, what do I do next?
I tried opening the Networking prefs applet, and setting /dev/ttLTM0 (without the y) as my modem device, but I just get a message that it can't find a modem there.

---

