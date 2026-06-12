---
title: "Wake on LAN - Prevent NIC from powering off"
date: 2012-06-06
forum: Networking &amp; Wireless
---

### Post by cheflo on 2012-06-06
Hello,
I'm looking for some help on how to get my network card to stay powered on and ready to receive those magical packages even after issuing the "shutdown"-command. I'm using Ubuntu Server 12.04 32-bit and I have been able to wake my Asus EeeBox 1012 from both hibernate and sleep, but not from a complete shutdown.

I followed this: [https://calomel.org/wakeonlan.html](https://calomel.org/wakeonlan.html) (scroll down to "Setting the target's..."), but it didn't help. I have enabled WoL in BIOS and "ethtool eth0" tells me that my WoL-setting is "g".

Can anyone help me out here?

---

### Post by cheflo on 2012-06-07
Ok I solved this. Turns out there was an extra setting in the BIOS apart from Wake on LAN. Enabling "Wake from PME" or something like that solved my problems.

---

### Post by maiky137 on 2012-09-20
Thank you,

this little Post saved my day!

I've tried everything else but this...

---

