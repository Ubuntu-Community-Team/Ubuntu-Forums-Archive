---
title: "DHCP restarts often."
date: 2009-09-03
forum: Networking &amp; Wireless
---

### Post by MechaMechanism on 2009-09-03
My DHCP is restarting far too often.  In the past it would restart about once a day and now every 1400 to 1700 seconds.  So what caused DHCP to start restart so often?  I have cable internet.

These lines below completely fill up the daemon log.

```
dhclient: DHCPREQUEST of 0.0.0.0 on eth0 to 172.18.166.6 port 67
dhclient: DHCPACK of 0.0.0.0 from 172.18.166.6
dhclient: bound to 0.0.0.0 -- renewal in 1766 seconds.
```

---

### Post by DGortze380 on 2009-09-03
> **MechaMechanism said:**
> My DHCP is restarting far too often.  In the past it would restart about once a day and now every 1400 to 1700 seconds.  So what caused DHCP to start restart so often?  I have cable internet.

These lines below completely fill up the daemon log.

```
dhclient: DHCPREQUEST of 0.0.0.0 on eth0 to 172.18.166.6 port 67
dhclient: DHCPACK of 0.0.0.0 from 172.18.166.6
dhclient: bound to 0.0.0.0 -- renewal in 1766 seconds.
```

Do you have a router? Or are you connected directly to your cable modem?

---

### Post by MechaMechanism on 2009-09-03
> **DGortze380 said:**
> Do you have a router? Or are you connected directly to your cable modem?Directly to the cable modem.

---

### Post by DGortze380 on 2009-09-03
> **MechaMechanism said:**
> Directly to the cable modem.

Then I doubt there's much you can do. Your ISP controls your lease time.

---

### Post by MechaMechanism on 2009-09-03
> **DGortze380 said:**
> Then I doubt there's much you can do. Your ISP controls your lease time.Well thanks anyway then.

---

