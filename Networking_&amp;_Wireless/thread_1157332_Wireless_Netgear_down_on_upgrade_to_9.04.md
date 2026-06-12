---
title: "Wireless Netgear down on upgrade to 9.04"
date: 2009-05-12
forum: Networking &amp; Wireless
---

### Post by EricBelcastro on 2009-05-12
Hi,
     I had no problems using this specific wireless adapter for some time now on 8.10. I initially installed the driver via ndiswrapper and it is still present.  When the adapter is plugged in the icon that displays a pending connection just keeps rotating in the upper right corner and never connects (if I click on it, the computer often starts to freeze).

I have just upgraded to Ubuntu 9.04 (Studio) from 8.10.
PC Pentium 4
The computer is not on a physical (wired) network.

It is a Netgear Wireless-N WN111 adapter using driver netmw245.inf, mrvw245.sys. 

lsusb - shows that it is indeed present
ndiswrapper -l - shows that the driver is installed and hardware is present.

I don't know what about the upgrade caused it to not work, because everything -looks- fine. But, nope. No wireless internet.

Thank you very much for any help,
Eric

---

### Post by EricBelcastro on 2009-05-13
Well, on top of this the sound wouldn't work, and the MySQL wouldn't load on startup, etc. so I just went back to 8.10. I would rather have stability. Honestly, maybe ever 8.04 wouldn't be a bad idea, but it's back to 8.10 for now. So, indirectly, I suppose this can be considered resolved - I uninstalled it and said goodbye (for now).

---

### Post by mreh.Eh on 2009-05-13
This is the same thing that is happening to me, though admittedly not the same model.

---

### Post by mreh.Eh on 2009-05-13
You might try using "sudo dhclient wlan0"

---

