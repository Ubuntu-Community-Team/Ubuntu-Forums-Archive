---
title: "linux routing tables"
date: 2011-04-03
forum: Networking &amp; Wireless
---

### Post by eng.bablo on 2011-04-03
where and how can edit linux routing table?
thanks

---

### Post by matt_symes on 2011-04-03
Hi

Have a look at the terminal command route. Open a terminal and type

```
route
```

to see the routing table.

```
man route
```

will give you more information. You can add, delete and view routes and a whole lot more.

Kind regards

---

### Post by SeijiSensei on 2011-04-03
If you're comfortable with "CIDR" addresses, you might find it easier to use the "ip" command that's part of iproute2.

For instance, the command

```
route add -net 192.168.12.0 netmask 255.255.255.0 gw 192.168.11.1
```

can also be written as 

```
ip route add 192.168.12.0/24 via 192.168.11.1
```

iproute2 includes a lot of [advanced routing features]("http://www.policyrouting.org/iproute2-toc.html") that are not in the older route command.

---

### Post by eng.bablo on 2011-04-03
> **matt_symes said:**
> Hi

Have a look at the terminal command route. Open a terminal and type

```
route
```

to see the routing table.

```
man route
```

will give you more information. You can add, delete and view routes and a whole lot more.

Kind regards
thanks alot . i'll try and reply

---

### Post by eng.bablo on 2011-04-03
done...thanks for your kindly help

---

