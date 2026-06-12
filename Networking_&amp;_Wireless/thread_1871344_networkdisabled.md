---
title: "network:disabled"
date: 2011-10-28
forum: Networking &amp; Wireless
---

### Post by gulmer on 2011-10-28
I installed ubuntu on a friends dell laptop inspiron 5150 last year and everything worked.Just recently she called and said she could not connect with her router wireless. I checked her wireless network using command lshw and it came up w/network DISABLED, description: Wireless interface. Shows a driver, rt2800usb, version=2.6.38-12-generic firmware=0.12
On the top panel info it has Wireless Network device not ready (firmware missing). What happened, worked before now not? I've got Natty Narwhal installed. The problem started about a week ago.

---

### Post by fdrake on 2011-10-28
try to see if there is a phisical switcher that turms on/off the wifi. also you may need to enable it in the bios in some laptops.
can you post the results of the command

```
rfkill list all
```

---

### Post by gulmer on 2011-10-28
> **fdrake said:**
> try to see if there is a phisical switcher that turms on/off the wifi. also you may need to enable it in the bios in some laptops.
can you post the results of the command

```
rfkill list all
```

1:phy1: Wireless LAN
soft blocked: no
hard blocked: no

---

### Post by gulmer on 2011-10-28
Thanks to chili555

---

