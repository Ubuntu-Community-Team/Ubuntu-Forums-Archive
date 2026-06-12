---
title: "Remove hisax and isdn modules"
date: 2009-06-07
forum: Networking &amp; Wireless
---

### Post by megacrypto on 2009-06-07
Im currently trying to install and setup an OpenVox telephony card, but in order to do so, i need to remove the isdn and hisax modules from loading.

How can i uninstall / remove them? Im on 8.10 server

```

02:04.0 Communication controller: Tiger Jet Network Inc. Tiger3XX Modem/ISDN interface
        Subsystem: Device 9100:0003
        Flags: bus master, medium devsel, latency 32, IRQ 9
        I/O ports at a400 [size=256]
        Memory at e2001000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>
        Kernel modules: hisax


```

---

### Post by puppywhacker on 2009-06-07
```
rmmod hisax
rmmod isdn4linux
depmod -a

```
if rebuilding the module list doesn't help, you can add and remove modules in these files (it goes to show that I never got the hang of the module list, still I get my modules loaded or blacklisted)
```
/etc/modules
/etc/modprobe.d/blacklist.conf
```

---

### Post by megacrypto on 2009-06-10
thanks puppywhacker

i also managed to do it this way:
```

sudo modprobe -r hisax
sudo modprobe -r isdn
sudo nano /etc/modprobe.d/blacklist

```

and in the blacklist file i added:
```

# Stop ISDN modules
blacklist hisax
blacklist isdn

```

---

