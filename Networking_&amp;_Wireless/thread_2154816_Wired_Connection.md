---
title: "Wired Connection"
date: 2013-06-16
forum: Networking &amp; Wireless
---

### Post by skhozema on 2013-06-16
How to set Wired connection as default for PC desktop. During boot it searches for wifi connection for sometime and then gets connected to the wired one. I want to set it for wired connection as default.


khozema.

---

### Post by hansdown on 2013-06-16
Hi skhozema.

Which version are you running?

---

### Post by praseodym on 2013-06-16
Please show
```

cat /etc/network/interfaces
```

---

### Post by Iowan on 2013-06-16
One option (maybe not the best) would be to uncheck the "Connect automatically" box for your wireless interface.

---

### Post by skhozema on 2013-06-19
i got this 

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

---

### Post by skhozema on 2013-06-19
> **praseodym said:**
> Please show
```

cat /etc/network/interfaces
```

> **hansdown said:**
> Hi skhozema.

Which version are you running?

I am using Ubuntu 13.04, 64 bit

---

### Post by praseodym on 2013-06-19
Remove the tick at "connect automatically" in your wireless profiles and tick it in "wired"

---

