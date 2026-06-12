---
title: "Wireless support on Dell Inspiron 1440."
date: 2010-09-04
forum: Networking &amp; Wireless
---

### Post by Vinu Raj V on 2010-09-04
Hi, 
      I've installed Ubuntu 9.10 on my Dell Inspiron 1440 laptop. How can I install the necessary wifi drivers for my machine.

Thanks in advance.

---

### Post by Scallyph on 2010-09-04
You might wanna start finding out what kind of chipset you're wireless card uses.

---

### Post by JBAlaska on 2010-09-04
Your laptop uses the Broadcom Corporation BCM4312 802.11b/g.

To get your wireless working:
Put the LiveCD in your drive and go to: **System, Administration, Software sources** and check the box below "Installable from CDROM". Then open a term and do:
```
sudo apt-get update
```

Then:
```
sudo apt-get install bcmwl-kernel-source

```

Now reboot and select the **BroadcomSTA driver**. in **System, Administration, Hardware Drivers** You may have to reboot again to get the driver working.

---

