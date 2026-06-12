---
title: "Ubuntu freezes when trying to remove a wireless driver"
date: 2009-01-02
forum: Networking &amp; Wireless
---

### Post by spartan_87 on 2009-01-02
Hey, I am having a problem with removing/unloading my wireless driver (iwl3945) for my Intel 3945ABG wireless card. I have been messing around with aircrack-ng and need to load the drivers from compat-wireless which I successfully did the day before, but since Iv rebooted I think it loaded the original driver I was using before. Now today every time I try to unload or run modprobe -r on my current driver my system locks up and I have to do a hard boot.
Maybe I am wrong and the compat-wireless driver is still loaded, but how do I see what driver is currently loaded?

---

### Post by Kobalt on 2009-01-02
Hello,

You can prevent your driver from being loaded at boot time by adding it to */etc/modprobe.d/blacklist*

---

### Post by spartan_87 on 2009-01-03
Yeah I had to do that to load the driver I needed. I am able to load any driver I want but whenever I try to unload drivers my system freezes up and also the caps lock and num lock LEDs flash, then I have to do a hard boot.

---

### Post by shelleycat on 2009-01-03
I have something similar, (Asus A9Rp, with a USB wireless device zd1211rw driver).  I think that to avoid it, you could try
sudo service NetworkManager stop
before doing the rmmod.  Then restart the NetworkManager.  I have not tried this a lot, because I only have to remove a driver sometimes.

---

