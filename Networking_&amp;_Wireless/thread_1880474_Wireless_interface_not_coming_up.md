---
title: "Wireless interface not coming up"
date: 2011-11-13
forum: Networking &amp; Wireless
---

### Post by halfpower on 2011-11-13
I can see the interface when I run lspci, but when I type iwlist, I get the following

```

$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

```

I have the RT3090 wifi chipset.  I added the following to the end of /etc/modprobe.d/blacklist.conf because it improves performance
```

blacklist rt2800pci
blacklist rt2800lib
blacklist rt2x00usb
blacklist rt2x00pci
blacklist rt2x00lib

```

Does anyone know why I can't use my wireless interface?

---

### Post by halfpower on 2011-11-13
I un-blacklisted the items in blacklist.conf and everything works reasonably well now.

---

