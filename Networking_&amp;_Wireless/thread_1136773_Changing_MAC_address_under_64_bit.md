---
title: "Changing MAC address under 64 bit?"
date: 2009-04-25
forum: Networking &amp; Wireless
---

### Post by lurikeen on 2009-04-25
I've tried macchanger, but that only works under 32 bit. I've also tried manually editing config files, and changing the value in eth1 settings, but to no avail. I need to change my mac address before I can connect to my network, so any packages I install I must first put on my flash drive. Does anyone know how I can do this?

---

### Post by ibuclaw on 2009-04-25
Oddly enough, someone else asked this an hour ago too. I'll just direct you to the same site as I directed him.
[http://www.howtogeek.com/howto/ubuntu/change-your-network-card-mac-address-on-ubuntu/](http://www.howtogeek.com/howto/ubuntu/change-your-network-card-mac-address-on-ubuntu/)

Also, bare in mind that a reboot is required for the changes to take effect.

Regards
Iain

---

### Post by lurikeen on 2009-04-25
That method isn't working for me; I've tried it before. What else can I do?

---

### Post by lurikeen on 2009-04-25
Ok, this method worked:

```

sudo ifconfig down
sudo ifconfig hw ether xx:xx:xx:xx:xx
sudo ifconfig up

```

Thanks.

---

### Post by kevdog on 2009-04-25
I use the iw program since I found the use of hw ether to never work for me!

---

