---
title: "JMicron JMC250 Wired NIC Not Connecting"
date: 2011-12-18
forum: Networking &amp; Wireless
---

### Post by giggaflop on 2011-12-18
Clevo w251hu Laptop
Wired And Wireless Networking
Wireless Works, Wired Doesn't
Wired Card is a JMC250 Gigabit Ethernet (rev 05)

Please Ask For What Info Is Required, Never had to Troubleshoot a Wired NIC before, normally just works D:

Network Info (Wired Cable Unplugged At This Point): [http://paste.ubuntu.com/774281/](http://paste.ubuntu.com/774281/)

Tried this "fix":
Power off machine, unplug power cable and battery if any.
Press power button to empty memory.
Restart

Tried Linux Mint Live USB, still nothing :(

---

### Post by praseodym on 2011-12-18
Hi,

router firmware is up-to-date? MAC address filter is turned off? Try also to take _anything_ from the current for about 20 minutes and try it again

---

### Post by giggaflop on 2011-12-18
Router is Working Fine, No Mac Address Filter, already tested and no go.
Ubuntu Live CD connects for 1 seconds, then the link dies as reported by dmesg

---

### Post by praseodym on 2011-12-18
Checked the cable?

---

### Post by giggaflop on 2011-12-18
yes, i have checked the cable, its definitely the Laptop

---

### Post by giggaflop on 2011-12-18
really not working :(

---

### Post by praseodym on 2011-12-18
Please show:

```
sudo apt-get install ethtool
sudo ethtool eth0
```

---

