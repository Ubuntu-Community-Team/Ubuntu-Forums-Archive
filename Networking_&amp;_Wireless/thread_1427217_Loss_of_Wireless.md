---
title: "Loss of Wireless"
date: 2010-03-11
forum: Networking &amp; Wireless
---

### Post by biomedtek on 2010-03-11
I am using Ubuntu 9.1.0 64 bit on a dual boot HP DM3 laptop.
It has a wireless card from Atheros Communications, model AR928X.
In Windows 7 the wireless works without any issues, but under Ubuntu I lose my wireless connectivity after some amount of time, could be minutes, or hours. When the connection is lost the list of wireless networks can not be refreshed, the adapter is basically turned off, even though the laptop switch indicats that the hardware wireless is on. The only way to reaquire wireless signals is to then reboot. I'm thinking this could be a driver issue, but don't know how to proceed.

---

### Post by bkratz on 2010-03-11
> **biomedtek said:**
> I am using Ubuntu 9.1.0 64 bit on a dual boot HP DM3 laptop.
It has a wireless card from Atheros Communications, model AR928X.
In Windows 7 the wireless works without any issues, but under Ubuntu I lose my wireless connectivity after some amount of time, could be minutes, or hours. When the connection is lost the list of wireless networks can not be refreshed, the adapter is basically turned off, even though the laptop switch indicats that the hardware wireless is on. The only way to reaquire wireless signals is to then reboot. I'm thinking this could be a driver issue, but don't know how to proceed.

Have you tried this yet?

[http://ubuntuforums.org/showpost.php?p=8599246&postcount=5](http://ubuntuforums.org/showpost.php?p=8599246&postcount=5)

---

### Post by biomedtek on 2010-03-11
when I try to install the backports I get this error:

E: Invalid operation linux-backports-modules-karmic-generic

Am I not supposed to be using apt-get?

---

### Post by bkratz on 2010-03-11
> **biomedtek said:**
> when I try to install the backports I get this error:

E: Invalid operation linux-backports-modules-karmic-generic

Am I not supposed to be using apt-get?

Yes, here is the full commands

[http://ubuntuforums.org/showpost.php?p=8613831&postcount=26](http://ubuntuforums.org/showpost.php?p=8613831&postcount=26)

---

### Post by biomedtek on 2010-03-11
oops, yes, forgot the install command.
Wireless has been connected for over an hour now, I think this fix worked.
Thank you for your efforts.

---

### Post by bkratz on 2010-03-11
> **biomedtek said:**
> oops, yes, forgot the install command.
Wireless has been connected for over an hour now, I think this fix worked.
Thank you for your efforts.

Glad to hear it helped. Please mark the thread solved with the thread tools so that other may benefit.

---

