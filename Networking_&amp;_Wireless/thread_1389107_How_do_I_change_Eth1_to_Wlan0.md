---
title: "How do I change Eth1 to Wlan0?"
date: 2010-01-24
forum: Networking &amp; Wireless
---

### Post by Floppyjoe on 2010-01-24
I used to be able to change eth1 to wlan0 in etc/iftab but that is deprecated now I think.

How do I go about doing this?

---

### Post by tgeer43 on 2010-01-24
> **Floppyjoe said:**
> I used to be able to change eth1 to wlan0 in etc/iftab but that is deprecated now I think.

How do I go about doing this?
What is it that you are trying to accomplish, exactly?
Perhaps then I can help.

tgeer

---

### Post by d3v1150m471c on 2010-01-24
you can't. you mean how do you setup wireless?

---

### Post by Floppyjoe on 2010-01-24
ok I searched hi and lo and found this after a few hours.

```
sudo gedit /etc/udev/rules.d/70-persistent-net.rules
```

you will see:
> # This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.

# PCI device 0x1969:0x1062 (atl1c)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:26:22:4c:XX:XX", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x14e4:0x4315 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="0c:60:76:XX:XX:XX", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

I just changed the eth1 here to wlan0

Thanks for your help guys...some programs will not work properly if it thinks a wireless connection is an ethernet connection...

then reboot...or restart networking...

---

### Post by d3v1150m471c on 2010-01-24
interesting. what applications will not work if it recognizes it as eth0?

---

### Post by Floppyjoe on 2010-01-24
> **d3v1150m471c said:**
> interesting. what applications will not work if it recognizes it as eth0?


Well SWscanner does not work...still doesn't even after the change...maybe network manager is interfering with it...

---

### Post by Floppyjoe on 2010-01-25
Don't do this cause the interface gets renamed for some reason after rebooting a few times.  Then I had to remove bcmwl-kernel-sources and reintall it to get Ubuntu to stop that behaviour.

---

### Post by kovo1533 on 2011-09-15
for me, remowing "bcmwl-kernel-sources" and "bcmwl-modaliases" helped and I am able to use the conky feature that shows wireless link quality now.

---

