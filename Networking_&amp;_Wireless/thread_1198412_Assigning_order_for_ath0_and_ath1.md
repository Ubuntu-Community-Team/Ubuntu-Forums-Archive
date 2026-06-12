---
title: "Assigning order for ath0 and ath1"
date: 2009-06-27
forum: Networking &amp; Wireless
---

### Post by VAsnowman on 2009-06-27
I have a need to have the ubiquiti pccard be assigned ath0 (currently being assigned ath1) instead of my internal wireless atheros card.  How do i change the order of how the kernel looks at the card and assigns the ath0 or 1.  Is there a way to switch the two?

---

### Post by jhannah on 2009-06-28
The device names are assigned by udev on boot and you should be able to swap them in /etc/udev/rules.d/70-persistent-net.rules. After changing the device names to suit your needs, try to reboot and the cards should come up with the correct names.

---

