---
title: "Trouble With Wireless Card and Drivers"
date: 2010-11-28
forum: Networking &amp; Wireless
---

### Post by theBackup on 2010-11-28
Recently after an installation upgrade my wireless card started sending my computer into a kernal panic shortly after boot up. To fix this I decided to try and install the factory windows drivers using the driver installation program found in Synaptic. However, these drivers did not appear to do anything and even worse they seemed to override the Ubuntu default driver and the wireless card is constantly set off and I know of no way to turn it back on. I have an Atheros Ar298x card. Could anyone help me get my wireless back?
-Thanks

---

### Post by uncaspi on 2010-11-28
Put in your live CD and select safe mode. Do the changes to the drivers there.

---

### Post by MooPi on 2010-11-28
Have you tried to get the Linux drivers working,I think ath9k will work for your chip.Can you give us the results from these commands in terminal```
lsmod
lspci
iwconfig
```

---

### Post by theBackup on 2010-11-30
Thanks for the hint, I managed to set it back to the default drivers that ubuntu shipped with!

---

### Post by uncaspi on 2010-11-30
Remember to put solved in the thread. Tab to thread tools.

---

