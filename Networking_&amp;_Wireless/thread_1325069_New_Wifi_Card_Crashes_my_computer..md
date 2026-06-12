---
title: "New Wifi Card Crashes my computer."
date: 2009-11-13
forum: Networking &amp; Wireless
---

### Post by leona on 2009-11-13
Hi there.

I have been trying to get wifi working on my computer, I have tried some usb and pci cards, some worked some didn't.  

I bought a wifi which I thought would be compatible with Linux. (as the add said it was).

But once installed my system just halts after a few minutes, I have never had since since I last used Windows!

What is going on?

The only thing I can pull from the logs is
```

Nov 13 09:14:26 leona-ubuntu kernel: [  108.913910] phy0 -> rt61pci_bbp_read: Error - PHY_CSR3 register busy. Read failed.
Nov 13 09:14:26 leona-ubuntu kernel: [  108.914416] phy0 -> rt61pci_bbp_write: Error - PHY_CSR3 register busy. Write failed.

```

I can not give you details from the card as it will not stay alive long enough for me to get to a terminal to perform any commands! 

The supplier points me to a link to [drivers]("http://www.faculty-x.net/linux/RT61_Linux_STA_Drv1.1.0.0.tar.gz")
which seems to be a archive of source files, eeek! I don't do 'make' anything!  As this is a dark area which I do not understand.

So can anyone suggest what I can do?  How I can get this card working and keep my system stable?

If it helps, I got the same problem with a USB Wifi stick.

Leona.

---

### Post by leona on 2009-11-13
Really? does no one have any idea what could be wrong?

---

### Post by leona on 2009-11-15
I solved the problem by putting the card in a different slot, must have been a connection issue.

---

