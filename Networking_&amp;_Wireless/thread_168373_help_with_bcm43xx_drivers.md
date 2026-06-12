---
title: "help with bcm43xx drivers"
date: 2006-04-30
forum: Networking &amp; Wireless
---

### Post by sal on 2006-04-30
I have an emachines m6810 with onboard (intergrated) broadcom 4306 but i am using an pcmcia Buffalo AirForce One 54g with the broadcom4318 chipset and the bcm43xx fwcutter drivers.

the problem is that the laptop is turning on the intergratyed 4306 broadcom as well and i would like to know how to disable it so only the pcmcia card is inabled at boot.

thanks for any help.

---

### Post by sal on 2006-05-04
anyone?

---

### Post by the_tiger on 2006-05-05
Try going into your computer bios and disabling it.

---

### Post by sal on 2006-05-05
there is no way in the bios to disable it.
that was the first thing i tried.

---

### Post by the_tiger on 2006-05-05
How about a command in the statup scrips like

```
sudo ifconfig eth0 down
```

where eth0 is the your unrequired interface.

---

### Post by sal on 2006-05-06
thanks i'm going to try that.

---

