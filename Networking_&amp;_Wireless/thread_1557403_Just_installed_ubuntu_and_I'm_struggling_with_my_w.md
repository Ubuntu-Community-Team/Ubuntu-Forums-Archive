---
title: "Just installed ubuntu and I'm struggling with my wireless."
date: 2010-08-20
forum: Networking &amp; Wireless
---

### Post by dangleitis on 2010-08-20
I've searched and looked around for some solutions but nothing so far.  Any help is very much appreciated, thanks.

---

### Post by Naitsirhc Hsem on 2010-08-20
what is your wireless card, can you post the output of this command here so we can better help you.

```
lspci
```
and
```
lsusb
```

these list all of the possible devices on your computer

---

### Post by dangleitis on 2010-08-20
Ok thanks very much.  I think it's a Broadcom bcm4318

---

### Post by Naitsirhc Hsem on 2010-08-20
Have you checked System > Administration > Hardware Drivers,
if it does not appear in there search for bcm4318 on this forum

---

### Post by dangleitis on 2010-08-20
I've done that and it says no proprietary drivers are in use on the system, I'll search for the broadcom on here as you've advised, thank you for the help.

---

### Post by Naitsirhc Hsem on 2010-08-20
anytime!

---

### Post by JBAlaska on 2010-08-20
Put the LiveCD in your drive and go to: System, Administration, Software sources and check the box below "Installable from CDROM". Then open a term and do:

```
sudo apt-get update
```

Then:

```
sudo apt-get install bcmwl-kernel-source
```

Now reboot and select the BroadcomSTA driver. in System, Administration, Hardware Drivers.

---

