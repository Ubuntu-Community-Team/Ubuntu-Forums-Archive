---
title: "xorg.conf ??"
date: 2009-12-07
forum: Multimedia Software
---

### Post by Pasdar on 2009-12-07
It seems there is no xorg.conf in 9.10... ??

I'm trying to remove my ati drivers... I can remove them, but upon reboot it gives error that it cant find the ati drivers... so apparently it stays in the config file... so i was forced to install it again.... :-/

---

### Post by lavinog on 2009-12-07
Xorg does not require a config file for normal use.  The proprietary drivers will require the config file though.

I am assuming you are trying to remove the proprietary drivers.
have you tried:
```

sudo bash /usr/share/ati/fglrx-uninstall.sh

```

---

### Post by Yellow Pasque on 2009-12-08
[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)

---

