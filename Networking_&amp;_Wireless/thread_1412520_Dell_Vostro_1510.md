---
title: "Dell Vostro 1510"
date: 2010-02-21
forum: Networking &amp; Wireless
---

### Post by ojve on 2010-02-21
Hi!

Just upgraded from Intrepid to karmic on my girlfriends Dell Vostro 1510 and the wireless stopped working.  The drivers are installed and worked fine under intrepid. When I enter the hardware drivers utility it says that the driver is active but currently not being used.

Any suggestions on how to fix this?

iwconfif output:
```

lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

```

Thx
//Thomas

---

### Post by northd_tech on 2010-02-21
Can you post the results of the following terminal commands:

```
lspci 

lsmod

uname -a

sudo lshw -C network

ifconfig
```

---

### Post by chili555 on 2010-02-21
I don't want to step on my esteemed colleague northd_tech, but I think we'd also love to see:```
rfkill list
```

---

### Post by ojve on 2010-02-22
Hi,

Sorry for the troube. After rebooting another time, everything works again.

//T

---

