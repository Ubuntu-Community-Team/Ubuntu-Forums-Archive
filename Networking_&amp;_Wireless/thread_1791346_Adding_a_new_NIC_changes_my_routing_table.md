---
title: "Adding a new NIC changes my routing table"
date: 2011-06-26
forum: Networking &amp; Wireless
---

### Post by tprizler on 2011-06-26
Hi!


I have a problem on my Ubuntu machine.
This machine is a virtual machine.

I have added a new nic using the VM console.

I have restarted the network service, an dI got a new ip address from the DHCP.

The thing is, this interface is "taking over " the old one.
It completely changed my routing table.

from this:
```

Destination   Gateway             Genmask            Flags      MSS Window   irtt  Iface
10.10.10.0          0.0.0.0        255.255.255.0      U           0  0           0  eth4
169.254.0.0         0.0.0.0        255.255.0.0        U           0  0           0  eth4
0.0.0.0             10.10.10.1     0.0.0.0            UG          0  0           0  eth4


to this:
10.10.56.0          0.0.0.0        255.255.255.0      U           0  0           0  eth5
10.10.10.0          0.0.0.0        255.255.255.0      U           0  0           0  eth4
169.254.0.0         0.0.0.0        255.255.0.0        U           0  0           0  eth4
0.0.0.0             10.10.56.1     0.0.0.0            UG          0  0           0  eth5

```

I don't understand why it's happening!!
Any idea?

Thanks!

---

